# Chapter 2 - Security Applied: XSS
## Lesson 1 - What is Cross-Site-Scripting?

Cross-Site Scripting (XSS) attacks are when a malicious script is injected into a trusted site. For example, add JavaScript code into an unsuspecting input of a form, and then use this to do all kinds of no good. Example of of attacks have been pulling data from cookies, session tokens, and all kinds of sensitive information.

For a demonstration of cross-scripting security issue, go to [synk lesson xss](https://learn.snyk.io/lesson/xss). Then scroll down and select your ecosystem "JavaScript". Then you can read through details about what XSS is. Following the description is a lesson to demonstrate how an XSS attack can play out in a chat application. 

The first demonstration provided by Synk shows how to insert CSS styles into a chat app to change the color of the background. Continue to scroll down to where you see "Say hi to Emily". Grab the `<style> * {background-color: #FFFF00 } </style>` that the instructions ask you to copy, and insert that code into the message text box. What you should see is the chat app now has a yellow background.

The second demonstration provided by Synk shows how to steal cookies, called "Hack 2: stealing cookies". You will be asked to copy a script tag `<script>document.getElementById("messageText").innerHTML=document.cookie;document.getElementById("sendMessage").click();</script>` and then insert this into the chat message box. This script should be pretty straight forward if you know JavaScript. 
- it grabs the document cookies & inserts them into an element with an id of "messageText"
- it forces a click event on the element with an id of "sendMessage"

This means any sites, Facebook etc., are open to this attack if they do not take steps to validate the data.

It is important for you to make sure you validate/sanitize data on both the client and the server. JavaScript libraries such as React will help you do this by putting parameters in place.

Also make sure you output encoding, so like HTTP cookie flag and CSP in your application. The instructor does not explain this or point you to specific example. Instead the instructor says there are many examples of how to do this in OWASP and the NodeGoat project, which you can find on Google.

<pre>
NOT PART OF COURSE:

OWASP Cheatsheet: Content Security Policy (CSP)
Content Security Policy (CSP) is a security feature that is used to specify the origin of content that is allowed to be loaded on a website or in a web applications. It is an added layer of security that helps to detect and mitigate certain types of attacks, including Cross-Site Scripting (XSS) and data injection attacks. These attacks are used for everything from data theft to site defacement to distribution of malware.

OWASP Cheatsheet: Secure Cookie Attribute
The Secure cookie attribute instructs web browsers to only send the cookie through an encrypted HTTPS (SSL/TLS) connection. This session protection mechanism is mandatory to prevent the disclosure of the session ID through MitM (Man-in-the-Middle) attacks. It ensures that an attacker cannot simply capture the session ID from web browser traffic.

Forcing the web application to only use HTTPS for its communication (even when port TCP/80, HTTP, is closed in the web application host) does not protect against session ID disclosure if the Secure cookie has not been set - the web browser can be deceived to disclose the session ID over an unencrypted HTTP connection. The attacker can intercept and manipulate the victim user traffic and inject an HTTP unencrypted reference to the web application that will force the web browser to submit the session ID in the clear.

NOTE: This header is relevant to be applied in pages which can load and interpret scripts and code, but might be meaningless in the response of a REST API that returns content that is not going to be rendered.

REFERENCES:
OWASP: HTTP headers cheatsheet, CSP
https://cheatsheetseries.owasp.org/cheatsheets/HTTP_Headers_Cheat_Sheet.html

OWASP: Session Cookies
https://cheatsheetseries.owasp.org/cheatsheets/Session_Management_Cheat_Sheet.html#cookies

NodeGoat
https://owasp.org/www-project-node.js-goat/
https://github.com/OWASP/NodeGoat
</pre>
