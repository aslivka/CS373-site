## Week 3 - Malware Defense              
### Introduction
After covering many types of malware and how forensically investigate them, next topic is on
Malware Defense. 

### Attack Graph
An attack graph describes how malware operates. The real graph is fairly big and hard to follow. I'll just summarize the 4 steps of attack:
* First Contact
* Local Execution
* Establish Presence
* Malicious Activity

### Ways to Defend Against Malware
Below is a list of ways to defend against Malware. I won't go into much detail in the list.
Much of this post will focus on last Lab, analyzing 4 samples and reporting results.

***First Contact***

*	Spam: Anti-spam
*	Network: Firewall, Network IPS (intrusion prevention software)
*	Web: IP, Domain, & URL reputation
*	Physical access: Disk encryption, also blocking physical access to USB ports using epoxy, or strict company policy

***Local Execution***
*	Spam: Client-side content filtering
*	Network: Network IPS
*	Web: Content filtering/scanning
*	Host: Host IPS, Anti-virus, Whitelisting

***Establish Presence***
*	Host: Anti-virus, Whitelisting, HIPS
*	Network: Firewall, Network IPS
*	Web: IP, Domain, & URL reputation 

***Malicious Activity*** 
*	Host: Anti-virus
*	Network: NIPS, Firewall
*	Web: IP, Domain, URL rep & content filtering
*	Data Loss Prevention

### Week 3 Lab - Malware Report
From the 4 given samples, 3 were judged malware

***Malicious:*** 
* 068D5B62254DC582F3697847C16710B7
* ***00670f2B9631D0F97C7CFC6C764DD9D9 (Analyzed malware)***
* A1874F714F7A15399B9FAE968180B303

***Not malicious:***
* 4844FD851088A11E240CFE5B54096209 

It’s a freeware program, LADS, that lists alternate data streams of an NTFS directory. 
It uses powerful system calls similar to malware to perform its harmless functions. 
It’s also written in Delphi, commonly used malware language, but that’s a false clue.

Name: Artem Slivka

Date/Time of your “posting”: 19/01/27

Malware hash: 00670f2B9631D0F97C7CFC6C764DD9D9

***Yara signature:*** 

```
rule malware{
	strings:
		$a="hau"
	condition:
		all of them
}
```
#### Malware Behavior
Malware tries to download some files after going to some web site links using Internet Explorer. 
After that it executes Dx.bat and qusla.exe. Those programs add Chinese language and font support 
to current computer to view them correctly. Next, the program modifies the sets up qusla.exe to 
run on every startup of Windows OS. Finally, it modifies starting page for Internet Explorer to 
http://www.3392.cn, a Chinese site. The last step explains why this malware was classified as 
StartPage malware by McAfee. For more detailed analysis see static and dynamic analysis sections
below:

#### Static Analysis
First, the hash for the files was entered into VirusTotal database. It was confirmed as malware type Trojan:Win32/Startpage, with original filename hau.exe. This malware has Chinese origin.
[Link](https://www.virustotal.com/#/file/dad270e45be77716062e0890bee6e31e9d498dddbe828563d8ffb58faca51e3c/details)
Next, file was statically analyzed with FileInsight. This particular malware file wasn’t compressed or encrypted so a large amount of useful data can be retrieved from it. After taking strings dump from the file here’s a summary of what the malware does:
*	It executes some hidden Internet Explorer sessions going to following web pages:
*	http://www.9435.cn
*	http://www.dxcpm.com/sogou.htm
*	http://www.s12580.com
*	http://www.ifengw.com/ete.htm
*	Tries executing msns.exe , a file it probably downloaded
*	Modifies Quick Launch shortcul link for Internet Explorer to open up http://www.3392.cn
*	Downloads files:  ***c:\qusla.exe, Dx.bat ***
*	Program assigns all possible permissions to ***c:\qusla.exe***:	attrib +r +s +h c:\qusla.exe
Then, it adds qusla.exe to Windows startup by creating the appropriate registry key at HKLM\Software\Microsoft\Windows\CurrentVersion\Run
*	Finally, it changes start page for Internet explorer to http://www.3392.cn.
See FileInsight screenshot for condensed string dump of program’s contents
![alt text](w3_finsight_shot.jpg "FileInsight screenshot of malware")




[Go Home](../index.md) 
