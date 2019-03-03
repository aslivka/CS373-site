## Week 10 - HackTheBox Final Report           
### Introduction
This post focuses on the Final assignment in the class. It discusses the various
HackTheBox site challenges I did to meet the requirements.

### Getting Invite
Signing up for a HackTheBox invite was an interesting challenge. 
1.  On the invite page, I found an obfuscated javascript code snippet, seen below:
```javascript
eval(function(p,a,c,k,e,d){e=function(c){return c.toString(36)};if(!''.replace(/^/,String)){while(c--){d[c.toString(a)]=k[c]||c.toString(a)}k=[function(e){return d[e]}];e=function(){return'\\w+'};c=1};while(c--){if(k[c])...e|error|data|var|verifyInviteCode|makeInviteCode|how|to|generate|verify'.split('|'),0,{}))
```
2. Using this code as reference, I called function makeInviteCode() in browser console. 
 This gave me a HTTP response with data:
``` javascript
0: 200
data: "SW4gb3JkZXIgdG8gZ2VuZXJhdGUgdGhlIGludml0ZSBjb2RlLCBtYWtlIGEgUE9TVCByZXF1ZXN0IHRvIC9hcGkvaW52aXRlL2dlbmVyYXRl"
enctype: "BASE64"
```
3. I then decoded the data property using https://www.base64decode.org/ and got the following message:
In order to generate the invite code, make a POST request to /api/invite/generate
4. Finally, I made this POST request to suggested link and received another encoded string:
```
SFZFUkYtVlJIRVAtWExWUVktSVlSUEYtR0lSRUg=  
```
I decoded it using BASE64 and got the invite KEY: HVERF-VRHEP-XLVQY-IYRPF-GIREH

### Challenge 1: 



 ![alt text](../images/w8_smtp_messages.jpg "SMTP message examples")



[Go Home](../index.md) 
