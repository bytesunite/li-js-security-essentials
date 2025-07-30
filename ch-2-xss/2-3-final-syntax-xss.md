# Chapter 2 - Security Applied: XSS
## Lesson 3 - Final Syntax Applied XSS

So let's take a look at XSS on OWASP's website. Go the [OWASP website](https://owasp.org) and type in "cross site scripting". Click on the first result that comes up. It should provide a description and if you scroll down you should see a few links.
- XSS (Cross Site Scripting) Prevention Cheatsheet
- DOM based XSS Prevention Cheat Sheet

When you go the DOM XSS cheatsheet the number 1 rule is HTML escape then JavaScript Escape before inserting untrusted data into HTML Subcontext within the Execution Context.

Go to the [DOM based XSS Prevention Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/DOM_based_XSS_Prevention_Cheat_Sheet.html)
It shows examples of what NOT to do and techniques to use to help sanitize data to before inserting untrusted data. It talks about methods such as "innerHTML" and "outerHTML", as well as "document.write" & "document.writeln", warning you of untrusted data. Instead it suggests more secure ways to insert content into the DOM using packages such a "node-esapi" that encodes HTML and JavaScript.

<pre>
Dangerous HTML
<code>element.innerHTML = "&lt;HTML> Tags and markup";
element.outerHTML = "&lt;HTML> Tags and markup";
</code>

Guideline
<code>var ESAPI = require('node-esapi');
element.innerHTML = "&lt;%=ESAPI.encoder().encodeForJavaScript(ESAPI.encoder().encodeForHTML(untrustedData))%>";
element.outerHTML = "&lt;%=ESAPI.encoder().encodeForJavaScript(ESAPI.encoder().encodeForHTML(untrustedData))%>";
</code></pre>

You can also learn about what Frameworks are doing to sanitize data.<br>
Go to the [XSS (Cross Site Scripting) Prevention Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Cross_Site_Scripting_Prevention_Cheat_Sheet.html) and scroll down to "Framework Security". OWASP warns you to learn how your specific JavaScript framework works to prevent XSS to help prevent security issues.

### JavaScript textContent
JavaScript has a `textContent` property of an element object. You can use this to return the text content of an element or set the text content. For example you could get the content of `<ul id="myList">` with `document.getElementById("myList").textContent`.

The instructor shows an exercise file named "escapeHTML" that will take a single argument of untrusted text and sanitize it. It basically removes any kind of scripting from text.<br>

<pre><code>function escapeHTML(text) {
  return text
    .replace(/&/g, "&amp;amp;")
    .replace(/&lt;/g, "&amp;lt;")
    .replace(/>/g, "&amp;gt;")
    .replace(/"/g, "&amp;quot;")
    .replace(/'/g, "&amp;#039;");
}
</code></pre>
