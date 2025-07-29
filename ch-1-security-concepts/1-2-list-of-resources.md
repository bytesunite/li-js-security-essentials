# Chapter 1 - Overview of Security Concepts
## Lesson 2 - List of available resources

Before looking at common threats in JavaScript, let's explore tools and resources used to research and analyze threats. You will use these tools to get more information and analyze your code for potential threats.

The Open Web Application Security Project or "OWASP", is a cybersecuriy community with with many resources available. You will need to create an account to gain access to all available resources. If you scroll down on the homepage you can view a calendar with dates and locations of OWASP conferences available to you. If you continue to scroll down the homepage you will find a list of flagship resources where there is a link to display a list of resources. In this list you will see things like "cheatsheets", "dependency checks", and much more. The homepage also shows the platforms they subscribe to such as GitHub, Facebook, Linkedin, Twitter, etc. 

1. Synk<br>
If you use Node.js or any NPM package, [Snyk](https://www.snyk.io) is a tool to help identify potential issues in your dependencies. It does it automatically as you make updates to your repository. It provides a lot more details on vulnerable dependencies than you get with npm audit and the specific exploit that could occur.

2. RetireJS<br>
[RetireJS](https://github.com/RetireJS/retire.js) is another scanning tool you can use to scan your application for known issues and get some ideas as to what is the security issue in your code.

3. NPM Audit<br>
[npm-audit](https://docs.npmjs.com/cli/v7/commands/npm-audit) is a good free way to do search of your own dependencies.

It is important to remember dependencies auditing is cruicial, as you are relying on other people. Some are paying attention to security, and others not so much. It is your responsibility to make sure your code is as safe as possible.
