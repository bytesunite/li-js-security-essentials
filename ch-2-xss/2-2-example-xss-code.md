# Chapter 2 - Security Applied: XSS
## Lesson 2 - Example of XSS in Code

The instructor explains XSS through execise code. It shows a Vite project with JSX components. ReactJS and other frameworks will try to protect you by escaping bad code. The example creates a script to insert code into the innerHTML of an element. But React catches this and will not allow it.

<pre><code>
const createMarkup = () => {
  return { __html: 'I am so dangerous you can feel it! }
}

...

&lt;div className="footer">
  &lt;p>&amp;copy; {this.state.name} Inc.&lt;/p>
  &lt;div innerHTML={createMarkup()} />
&lt;/div>
</code></pre>

React protects you and instead all you see is the copyright symbol and the name but you do NOT see the "I am so dangerous.." message. React escaped it.

Browsers such a Chrome are using something called a "content security policy", which basically protects you from cross-site scripting (XSS). It sanitizes and escapes bad code. So not only will Frameworks help protect you but browsers are also starting to defend against this activity.
