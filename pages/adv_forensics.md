## Week 2 - Advanced Forensics              

This week's post will focus on discussing on Malware. I'll try to summarize what malware is, why is it created, and how its operates. 
After that, I'll briefly show how to analyze malware and share some useful analysis tools as well.

### What is Malware
Malware is a shortened name for ***MAL***icious soft***WARE***. It is usually transmitted by clicking a link in email/web page or inserting a malicious USB stick. **The most common way to infect a PC is through the user.**

Example of XP malware:

![Malware example](malware_example.png "Malware example")


There are many types of malware. I've listed some major ones below.
* Viruses: program written to enter to your computer and damage/alter your files/data
* Trojans: a destructive program that looks as a genuine application. Ex: fake antiviruses.
* Types: Backdoor, downloader, password stealer, keylogger, bot
* Potentially Unwanted Programs: adware, spyware, tools
* Ransom-ware: program that encrypts user's files on PC until he/she send money to unlock them
* POS malware: records and transmits credit card numbers processed by POS terminals
* Targeted malware

### Why Does Malware Exist?
Malware exists for many reasons. Usually the motives for malware creation are: money, revenge, ideology, excitement.
Common targets of Malware are: large companies, governments, contractors, etc.

### Analyzing Malware
#### Replication of Malware
Replication of malware's behavior allows us to study how malware behaves and design countermeasures against it and possibly the family of malware it belongs to.
To successfully replicate malware behavior while not damaging your test setup, follow 3 simple steps:
* Create an isolated environment. Ex: standalone PC with insecure internet access
* Use a hardened Virtual Machine(VM). Some viruses check for VMs but there are workarounds for that.
* Add Bait. Ex: If it's keylogger for credit card numbers, enter fake numbers in PC.

#### Useful Software Tools
While replicating malware's behavior, use some of these tools to record malware's actions on the test PC.
* FileInsight (static analysis) - program that analyzes binary files for useful malware info, has many plugins
* FakeNet - creates a fake network to allow analyzing malware in closed local network environment
* AntiSpy
* Process Explorer - more detailed version of Task Manager
* Process Monitor - records all events made by processes in a specified time duration
* FlyPaper - blocks network traffic and prevents malware from exiting. Great for step-by-step analysis of malware execution

#### Analyzing Data From Replication
After replicating malware's behavior,  now comes the hardest part: analyzing the data gathered. Usually, analysis
becomes easier as one becomes experienced. 

For Lab 1, this week I analyzed malware evil.exe. According to research, it was used by Chinese criminals to infiltrate Korean banks. [Article Link](https://blog.avast.com/2013/03/19/analysis-of-chinese-attack-against-korean-banks/). The malware schedules a series of daily tasks that runs svchest.exe malware file. Then, that harmlessly-named file communicates with a website to coordinate activities. See screenshot of this malware file's contents below, extracted by FileInsight.

![alt text](Lab1_malware_code.jpg "Snapshot of malware")

It's fairly complicated malware program. The other files like tonji2.exe and pao.exe also run in the background depending if the scheduled program is running at the time. This malware seems to be a backdoor program with keylogger features as well. The backdoor part explains the downloading by svchest.exe of additional files like funbots.txt and system.yf (as seen in screenshot). The keylogger/datalogger portion exlains why the malware runs multiple times every day, sending newly gathered data back to the malicious sites.


[Go Home](../index.md) 
