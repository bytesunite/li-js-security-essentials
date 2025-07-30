# Chapter 2 - Security Applied: XSS
## Lesson 4 - Best Practices for XSS Threats

### Rules to follow
- Never pass unsafe data to your code. Always escape it or sanitize it.<br>
  Uses tools or use your own sanitize functions.
- Use JavaScript's `element.textContent` to populate DOM with safe content
- Use popular frameworks such as React or Angular to build your sites.<br>
  These frameworks help protect your from inserting unsafe data and escaping unsafe functions from running
- Review all the rules at the links explored in this video


Make sure to ready through the [OWASP Cross Site Scripting Prevention Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Cross_Site_Scripting_Prevention_Cheat_Sheet.html)

(Not part of course, OWASP XSS Cheat Sheet)
Cross Site Scripting (XSS) was originally known as from early versions of the attack used to steal data. XSS has now widened to include injection of basically any content. XSS attackes are serious.
- account impersonation
- observing user behavior
- loading external content
- stealing sensitive data

The cheat sheet contains techniques to prevent or limit the impact of XSS. Since no single technique will solve XSS, using the right combination of defensive techniques will be necessary to prevent XSS.
- Framework Security<br>
  Discusses unsafe data insertions to html DOM
- XSS Defense Philosophy<br>
  Ensure all variables go through validation & sanitized. Known as "perfect injection resistance"
- Output Encoding<br>
  This is broken into multiple parts to illustrate you should NOT put variables in HTML element, HTML attributes, inline script tags
- When using JSON, use *Content-Type* of *application/json* instead of text/html.
- CSS Contexts<br>
  This refers to when variables are placed in inline CSS. If you want to change CSS with JS then look into *style.property = x* styntax. a Safe Sink and will automatically CSS encode data in it.<br>
  When inserting variables into CSS properties, ensure the data is properly encoded and sanitized to prevent injection attacks. Avoid placing variables directly into selectors or other CSS contexts.
- URL Contexts<br>
  This is when variables are placed in the url. Use url encoding in these cases. See *urlencode()* and *window.encodeURIComponent()*
- Dangerous Contexts
  Don't place variables directly inside inline `<script>` tags, `<style>` tags, custom element attribute values (&lt;div someAttr=test />), (&lt;ToDefineATag href='/test' />)
- Other places to be careful<br>
  Don't place variables into dangerous contexts as even with output encoding, it will not prevent an XSS attack fully.
  - callback functions
  - code where urls are used in CSS {background-url: "javascript:alert(xss)";}
  - event handlers (onclick(), onerror(), onmouseover())
  - Unsafe JS functions like eval(), setInterval(), setTimeout()
- HTML Sanitization<br>
  When creating a WYSIWYG that takes user code, you can't use output encoding, so use HTML sanitization.
  OWASP suggests using [DOMPurify](https://github.com/cure53/DOMPurify) for HTML sanitization. But make sure to update it as new issues get discovered regularly.<br>

  `let clean = DOMPurify.sanitize(dirty);`

- Safe Sinks<br>
  The term "sink", used by security professionals, is the idea of a polluted river flows downstream. A XSS "sink" are places where variables are placed in your webpage.<br>
  Thankfully, many sinks where variables can be placed are safe. This is because these sinks treat the variable as text and will never execute it. Try to refactor your code to remove references to unsafe sinks like <span style="color:red">innerHTML</span>, and instead use <span style="color:green">textContent</span> or value.<br>

  Safe HTML Attributes include: align, alink, alt, bgcolor, border, cellpadding, cellspacing, class, color, cols, colspan, coords, dir, face, height, hspace, ismap, lang, marginheight, marginwidth, multiple, nohref, noresize, noshade, nowrap, ref, rel, rev, rows, rowspan, scrolling, shape, span, summary, tabindex, title, usemap, valign, value, vlink, vspace, width.
