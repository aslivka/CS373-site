## Week 10 - HackTheBox Final Report           
### Introduction
This post focuses on the Final assignment in the class. It discusses the various
HackTheBox site challenges I did to meet the requirements.

### Getting Invite
Signing up for a HackTheBox invite was an interesting challenge. 
1.  On the invite page, I found an obfuscated javascript code snippet, seen below:
```javascript
eval(function(p,a,c,k,e,d){e=function(c){return c.toString(36)};if(!''.replace(/^/,String)){while(c--){d[c.toString(a)]=k[c]||c.toString(a)}k=[function(e){return d[e]}];e=function(){return'\\w+'};c=1};while(c--){if(k[c]){p=p.replace(new RegExp('\\b'+e(c)+'\\b','g'),k[c])}}return p}('1 i(4){h 8={"4":4};$.9({a:"7",5:"6",g:8,b:\'/d/e/n\',c:1(0){3.2(0)},f:1(0){3.2(0)}})}1 j(){$.9({a:"7",5:"6",b:\'/d/e/k/l/m\',c:1(0){3.2(0)},f:1(0){3.2(0)}})}',24,24,'response|function|log|console|code|dataType|json|POST|formData|ajax|type|url|success|api|invite|error|data|var|verifyInviteCode|makeInviteCode|how|to|generate|verify'.split('|'),0,{}))
```

2. Using this code as reference, I called function makeInviteCode() in browser console. 
 This gave me a HTTP response with data:
``` javascript
0: 200
data: "SW4gb3JkZXIgdG8gZ2VuZXJhdGUgdGhlIGludml0ZSBjb2RlLCBtYWtlIGEgUE9TVCByZXF1ZXN0IHRvIC9hcGkvaW52aXRlL2dlbmVyYXRl"
enctype: "BASE64"
```
3. I then decoded the data property using https://www.base64decode.org/ and got the following message:

```In order to generate the invite code, make a POST request to /api/invite/generate```

4. Finally, I made the POST request to suggested link and received another encoded string:
```SFZFUkYtVlJIRVAtWExWUVktSVlSUEYtR0lSRUg= ```
I decoded it using BASE64 and got the invite KEY: 
```HVERF-VRHEP-XLVQY-IYRPF-GIREH```

### Challenge Summary
I completed 3 challenges:
*   Misc - Art  (20 pts)
*   Steganography - Hackerman (30 pts)
*   Steganograph - Widescreen (20 pts)
Total = 70 pts
 ![alt text](../images/final_summary.jpg "Challenge summary")


### Challenge 1: Misc - Art [ 20 pts, Total = 20 pts]
For this challenge, I received a colorful image and had to find the required HTB{flag} inside of it.
Since this challenge wasn't classified in Steganography category, the flag information wasn't embedded in a secret way directly in the provided image. That is the flag string wasn't hidden using
image manipulation techniques like contrast, hue, brightness adjustments. 
Therefore, I had to look for another way to extract this info. After some research and hint from HackTheBox forums, I found an obscure computer language, Piet, that interpets image colors as specific computer instructions. With certain color combinations, it can easily print "Hello World". 
[Link](https://en.wikipedia.org/wiki/Esoteric_programming_language#Piet)

Finally, I found a Piet interpreter/compiler online and uploaded the challenge image to it. After brief compilation, I found the HTB flag by looking at Piet program's output. See screenshot below for details. 
```HackTheBox flag = HTB{p137_m0ndr14n}```

 ![alt text](../images/final_ch1.jpg "Challenge 1 screenshot")


[Go Home](../index.md) 