title: Stanford CS142 - Web Applications
date: 2017-01-02
updated: 2017-03-17
categories:
- [technology]
tags: 
- Web
- Stanford
---

[Stanford CS142](http://cs142.stanford.edu) 学习笔记<!--more-->

> History :
2017-01-02 基于 SWinter 2017 的 课件 所做的笔记

在2000年的时候，就学习过HTML，JS，但很快就放下了，因为那时认为Web/UI开发很繁琐，没什么技术含量，个人也因此错过了PC Web时代。惟技术思维使得人一叶障目，产生偏见。如果从商业和产品角度开看，WEB开发速度快，能快速出原型；响应快，能快速处理需求变更和BUG；功能升级快，无须重新下载，对用户友好；唯一的缺点是表现力，也就是UI的性能问题。但Web开发在UI上的确是Native要比方便，简单的多(HTML + CSS + JS)，随着移动应用开发的成熟，跨平台的方案是大势所趋。在Cordova, Xamarin, React-Native等跨平台的移动应用开发方案中，个人最看好[React-Native](http://facebook.github.io/react-native/)，Oculus甚至提供了React-VR来开发WebVR应用。

在[Stanford CS的课程表](http://cs.stanford.edu/academics/courses)里查找了下Web开发相关的课程，发现了[CS142: Web Applications](http://cs142.stanford.edu)，花了3天时间学习，主要是对Web Applications开发的方方面面有了全局的认知，然后重点放在React-Native的学习和应用上。 泛泛的了解。

> Web-based applications offer numerous advantages, such as instant access, automatic upgrades, and opportunities for collaboration on a massive scale.  In the process you will learn about markup languages, scripting languages, network protocols, interactive graphics, event-driven programming, and databases, and see how they all work together to deliver exciting applications.

One good online source for reference documentation on HTML, CSS, and the DOM is [Mozilla Developer Network](https://developer.mozilla.org/en-US/). 

本课程采用MEAN Stack来做项目的练习，主要的好处是可以只用Javascript来Browser和Server的开发，但我个人更倾向于采用React + Go + MongoDB的技术栈。 

The web application we build in the course's projects will use what is known as the MEAN stack. The MEAN stack uses the JavaScript language in both the browser and the server-side. 
MongoDB - An object database
Express.js
AngularJS - JavaScript-based browser framework for apps
Node.js - JavaScript-based server engine

**prerequisites : CS107 and CS108**
**Reading:**
- JavaScript : The Definitive Guide
- HTTP : The Definitive Guide

# 01 Introduction
课程的目标：Learn how a web application is built

Web Application Architecture : WebBrowser <--HTTP--> Web server/Application server  <--LAN->  Database System

HTML/CSS/JavaScript/DOM - Markup, separation of content & style, reuse
Document object Model(DOM) - Document structure
Angular.js - Model View Controller, Single Page Applications

HTTP/AJAX/REST - API design
Cookies/Sessions

DBMS - Schema, Objects, CRUD, indexes, transactions
End-to-End - Scale and Security

# 02 HyperText Markup Language (HTML)
Web browsers display Documents described in HTML
Concept: Markup Language - Include directives with content
Directives can dictate presentation or describe content
Idea from the 1960s: RUNOFF 

# 03 Cascading Style Sheets (CSS)
Key concept: Separate style from content
Content (what to display) is in HTML files
Formatting information (how to display it) is in separate style sheets (.css files).
Use an element attribute named class to link (e.g. <span class=”test”>)
Result: define style information once, use in many places


CSS Selector    | CSS                       | HTML
----------------|---------------------------|-------------------------
Tag name        | h1 {color: red;}          | <h1>Today’s Specials</h1>
Class attribute | .large {font-size: 16pt;} | <p class="large">...
Tag and Class   | p.large {...}             | <p class="large">...
Element id      | #p20 {font-weight: bold;} | <p id="p20">...

Control many style properties of an element:
- Coloring
- Size
- Position
- Visibility
- Many more: (e.g. p: { text-decoration: line-through; })
- Also used in animation

Total element width =
width +
left padding +
right padding +
left border +
right border +
left margin +
right margin

Margin & Padding Transparent

# 04 Universal Resource Locator(URL)
Parts of an URL : http://host.company.com:80/a/b/c.html?user=Alice&year=2008#p2
Scheme (http:): identifies protocol used to fetch the content.
Host name (//host.company.com): name of a machine to connect to.
Server's port number (80): allows multiple servers to run on the same machine.
Hierarchical portion (/a/b/c.html): used by server to find content.
Query parameters (?user=Alice&year=2008): provides additional parameters
Fragment (#p2): Have browser scroll page to fragment (html: p2 is anchor tag)

# 05 JavaScript Basics
From Wikipedia:
... high-level, dynamic, untyped, and interpreted programming language
... is prototype-based with first-class functions, …
... supporting object-oriented, imperative, and functional programming

Variables have the type of the last thing assigned to it
Primitive types: undefined, number, string, boolean, function, object

Object is an unordered collection of name-value pairs called properties

# 06 JavaScript Programming
... supporting object-oriented, imperative, and functional programming

Mostly programming conventions (i.e. patterns) rather than language features
更多的是一种编程约定，而不是语言层面的特性

A property of an object can be a function 

Functions are classes in JavaScript: Name the function after the class

JavaScript Object Notation (JSON) :  is the standard format for sending data to and from a browser

# 07 Document Object Model(DOM)
HTML document exposed as a collection of JavaScript objects and methods
**The Document Object Model (DOM)**
- JavaScript can query or modify the HTML document
- Accessible via the JavaScript global scope, aliases: window

**DOM hierarchy**
- Rooted at window.document
- Follows HTML document structure
window.document.head
window.document.body
- DOM objects have tons (~250) of properties, most private Objects (representing elements, raw text, etc.) have a common set of properties and methods called a DOM "Node"

**DOM Node properties and methods**
- Identification
nodeName property is element type (uppercase: P, DIV, etc.) or #text
- Encode document's hierarchical structure
parentNode, nextSibling, prevSibling, firstChild, lastChild.
- Provide accessor and mutator methods
E.g. getAttribute, setAttribute methods, etc..

# 08 Events
**DOM communicates to JavaScript with Events**
Event types:
- Mouse-related: mouse movement, button click, enter/leave element
- Keyboard-related: down, up, press
- Focus-related: focus in, focus out (blur)
- Input field changed, Form submitted
- Timer events
- Miscellaneous:
- Content of an element has changed
- Page loaded/unloaded
- Image loaded
- Uncaught exception

**Event handling**
Creating an event handler: must specify 3 things:
- What happened: the event of interest.
- Where it happened: an element of interest.
- What to do: JavaScript to invoke when the event occurs on the element

**Event Concurrency**
- Events are serialized and processed one-at-a-time
- Event handling does not interleave with other Javascript execution.
- Handlers run to completion
- No multi-threading.
- Make reasoning about concurrency easier
- Rarely need locks.
- Background processing is harder than with threads

# 09 Front End Programming
Brief history of Web Applications : 
- Initially: static HTML files only.
- Common Gateway Interface (CGI)
- Certain URLs map to executable programs that generate web page
- Program exits after Web page complete
- Introduced the notion of stateless servers: each request independent, no state
carried over from previous requests. (Made scale-out architectures easier)
- Perl typically used for writing CGI programs

First-generation web app frameworks
Examples: (PHP, ASP.net, Java servlets)
- Incorporate language runtime system directly into Web server
- Templates: mix code and HTML
- Web-specific library packages:
- URL handling
- HTML generation
- Sessions
- Interfacing to databases

Second-generation frameworks
Examples: (Ruby on Rails, Django):
- Model-view-controller: stylized decomposition of applications
- Object-relational mapping (ORM): simplify the use of databases (make
database tables and rows appear as classes and objects)

Third-generation frameworks
Examples: (AngularJS, ReactJS, …)
- JavaScript frameworks running in browser - More app-like web apps
- Interactive, responsive applications
- Frameworks not dependent on particular server-side capabilities
- Node.js - Server side JavaScript
- No-SQL database (e.g. MongoDB)
- Many of the concepts of previous generations carry forward
- Model-view-controllers
- Templates

Model-View-Controller (MVC) Pattern
- Model: manages the application's data
JavaScript objects
- View: what the web page looks like
HTML/CSS
- Controller: fetch models and control view, handle user interactions,
JavaScript code
MVC pattern been around since the late 1970's
- Originally conceived in the Smalltalk project at Xerox PARC

View Generation
- Web App: Ultimately need to generate HTML and CSS
Templates are commonly used technique. Basic ideas:
- Write HTML document containing parts of the page that are always the same.
- Add bits of code that generate the parts that are computed for each page.
- The template is expanded by executing code snippets, substituting the results into the document.

Benefits of templates (Compare with direct JavaScript to DOM programming)
- Easy to visualize HTML structure
- Easy to see how dynamic data fits in
- Can do either on server or browser

Controllers
- Third-generation: JavaScript running in browser
Responsibilities:
- Connect models and views
Server communication: Fetch models, push updates
- Control view templates
Manage the view templates being shown
- Handle user interactions
Buttons, menus, and other interactive widgets

Model Data
- All non-static information needed by the view templates or controllers
- Traditionally tied to application's database schema
Object Relational Mapping (ORM) - A model is a table row
- Web application's model data needs are specified by the view designers But need to be persisted by the database
- Conflict: Database Schemas don't like changing frequently but web application model data might (e.g. user will like this view better if we add … and lose ...)


> 2016.12.15 正在看的时候，突然发现网页不可访问了，有可能正在更新，要开始新的课程，这种应用类的知识，很容易就过时了。
# 10 Introduction to AngularJS
个人更倾向于学习React，React-Native是很重要的原因。而且Angular 2对Angular1重写，

- JavaScript framework for writing web applications
Handles: DOM manipulation, input validation, server communication, URL mangement, etc.

- Uses Model-View-Controller pattern
HTML Templating approach with two-way binding

- Minimal server-side support dictated
- Focus on supporting for programming in the large and single page applications
Modules, reusable components, testing, etc.


# 11 Single Page Applications
在一个页面加载不同的URL

**没有看懂**
Deep linking
- Concept: the URL should capture the web app's context so that directing the
browser to the URL will result the app's execution to that context
1. Bookmarks
2. Sharing

- Context is defined by the user interface designer!
Consider: Viewing information of entity and have an edit dialog open
Should the link point to the entity view or to the entity & dialog?
Does it matter if I'm bookmarking for self or sharing with others?
How about navigating away and back or browser refresh?


# 12 Responsive Web Design
Web App Challenges : Screen real estate
> 屏幕适配和本地化是所有应用都要面对的问题

Responsive Web Design : 
- Context is like water!
The web app should flow into and fill whatever device you have.

- Possible with recent CSS extensions:
1. Add grid layout system with relative (e.g. 50%) rather than absolute (e.g. 50pt) measures
Specify element packing into columns and rows
2. Add @media rules based on screen sizes
Switch layout based on screen size
3. Made images support relative sizes
Autoscale image and videos to fix in screen region
img { width: 100%; height: auto; }
video { width: 100%; height: auto; }

**Responsive implementation**
- Build components to operate at different screen sizes and densities
Use relative rather than absolute
Specify sizes in device independent units
- Use CSS breakpoints to control layout and functionality
Layout alternatives
App functionality conditional on available screen real estate
- Mobile first popular
Expand a good mobile design to use more real estate

# 13 Building Web Applications
## Some Design Goals:
- Intuitive to use
Don't need to take a course or read a user manual
- Accomplish task accurately and rapidly
Provide needed information and functionality
- Users like the experience
Joy rather than pain when using the app

The hardest part of good web applications is the **design**.

Some guiding design principles for Web Apps
- Be consistent
Cognitive load less for the user
- Provide context
User shouldn't get lost in the app
- Be fast
Don't make the user wait

Consistency: Style guides & design templates
- Web apps should have a style guide - Covers the look and feel of the app
Style - Color schemes, animation, icons, images, typography, writing
User interactions - Menu, buttons, pickers, dialog boxes, tables, lists, ...
Layout - Structure, toolbars, content, responsiveness

- Patterns - If you do something multiple places do it the same way
Aided by reusable implementation components
Error handling, navigation, notifications, etc.

- Design templates - Follow a familiar structure
Example: Master-detail template

 
**Front-end web frameworks**
Popular example: Bootstrap
- CSS style sheets
Design templates
Grid layout system with responsive support (breakpoints, etc.)
Element styling
- HTML components
Buttons, menus, toolbars, lists, table, forms, etc.
- JavaScript
Modals, transitions, dropdowns, etc.
Originally jquery based
- Angular Material
CSS style sheets and Angular directives for implementing Material design spec

# 14 Browser/Server Communication
Controller's role in Model, View, Controller : 
- Controller's job to fetch model for the view
May have other server communication needs as well (e.g. authentication services)
- Browser is already talking to a web server, ask it for the model
- Early approach: have the browser do a HTTP request for the model
First people at Microsoft liked XML so the DOM extension got called: XMLHttpRequest
- Allowed JavaScript to do a HTTP request without switching page
- Widely used and called AJAX - Asynchronous JavaScript and XML
- Since it is using an HTTP request it can carry XML or anything else
More often used with JSON

Traditional AJAX uses patterns : 
- Response is HTML
elem.innerHTML = xhr.responseText;

- Response is JavaScript
eval(xhr.responseText);
Neither of the above are the AngularJS way

- Response is model data (JSON frequently uses here)
JSON.parse(xhr.responseText);

REST APIs : 
- REST - representational state transfer
- Guidelines for web app to server communications
- 2000 PhD dissertation that was highly impactful
Trend at the time was complex RPCs system
Became a must have thing: Do you have a REST API?
- Some good ideas, some not so good
Doesn't work for everything

Some RESTful API attributes : 
- Server should export resources to clients using unique names (URIs)
Example: http://www.example.com/photo/ is a collection
Example: http://www.example.com/photo/78237489 is a resource

- Keep servers "stateless"
Support easy load balancing across web servers

- Allow caching of resources
- Server supports a set of HTTP methods mapping to CRUD
GET method - Read resource (list on collection)
PUT method - Update resource
POST method - Create resource
DELETE method - Delete resource

RESTapi design : 
- Define the resources of the service and give them unique names (URIs)
- Have clients use a CRUD operations using HTTP methods
- Extend when needed (e.g. transaction across multiple resources)

Going forward: HTML5 WebSockets : 
- Rather than running over HTTP, HTML5 brings sockets to the browser
- Event-based interface like XMLHttpRequest


# 15 Web Servers
Web Application Architecture : 
Web Browser(Chrome/Firefox/Safari/Internet Explorer) <-- http -->  HTTP Server(Apache, NodeJS)  <-- LAN -->  Storage Server(MySQL, MongoDB)

Web Servers :
- Browsers speak HTTP and Web Servers speak HTTP
Browsers: send HTTP request and get HTTP responses
Web Server: get HTTP requests and send HTTP responses

- HTTP is layered on TCP/IP so a web server:
loop forever doing:
  accept TCP connection from browser
  read HTTP request from TCP connection
  process HTTP request
  write HTTP response to TCP connection
  shutdown TCP connection (except if Connection: keep-alive)

2nd Generation Web App Frameworks :
Web server runs a program per request - the **controller**:
1. Parse URL and/or HTTP request body to get parameters to view
2. Use parameters to fetch model data from DBMS (typically a SQL relational DBMS)
3. Run HTML view template with model data to generate the HTML
4. Send a HTTP response with the HTML back to the browser

Web servers for JavaScript frameworks :
- Most of the web app is simple static files - any web server speaking HTTP
View templates (HTML, CSS)
JavaScript files

- Remaining browser⇔ server communication around model data
CRUD (Create Read Update Delete) of model data
Session info (e.g. login, etc.) (Later...)

- Low requirements on web request processing
HTTP GET static files
Model data operation - mostly doing DBMS operations

# 16 Node.js
**Node.js**
- Take a JavaScript engine from a browser (Chrome's V8 JavaScript Engine)
Get same JavaScript on both browser and server
Don't need the DOM on the server
- Add events and an event queue
Everything runs as a call from the event loop
- Make event interface to all OS operations
Wrap all the OS blocking calls (file and socket/network io)
Add some data handle support
- Add a proper module system
Each module gets its own scope (not everything in window)

**Node modules**
- Many standard Node modules
File system, process access, networking, timers, devices, crypto, etc.
- Huge library of modules (npm)
Do pretty much anything you want
- We use:
Express - Fast, unopinionated, minimalist web framework (speak HTTP)
Mongoose - Elegant mongodb object modeling (speak to the database)

# 17 ExpressJS
Express.js - A web framework for Node.js
Fast, unopinionated, minimalist web framework
Relatively thin layer on top of the base Node.js functionality
What does a web server implementor need?
- Speak HTTP: Accept TCP connections, process HTTP request, send HTTP replies
Node's HTTP module does this
- Routing: Map URLs to the web server function for that URL
Need to support a routing table (like ngRoute in AngularJS)
- Middleware support: Allow request processing layers to be added in
Make it easy to add custom support for sessions, cookies, security, compression, etc.

# 18 Storage Tier
Web App Storage System Properties
- Always available - Fetch correct app data, store updates
Even if many request come in concurrently - Scalable
From all over the world
Even if pieces fail - Reliable / fault tolerant
- Provide a good organization of storing an application data
Quickly generate the model data of a view
Handle app evolving over time
- Good software engineering: Easy to use and reason about

**Relational Database System**
- Early on many different structures file system, objects, networks, etc.
- The database community decided the answer was the relational model
Many in the community still think it is.
Data is organized as a series of **tables** (also called called relations)
A table is made of up of **rows** (also called tuples or records)
A row is made of a fixed (per table) set of typed **columns**
String: VARCHAR(20)
Integer: INTEGER
Floating-point: FLOAT, DOUBLE
Date/time: DATE, TIME, DATETIME
Others

**NoSQL - MongoDB** 
- Using SQL databases provided reliable storage for early web applications
- Led to new databases that matched web application object model
Known collectively as NoSQL databases
- MongoDB - Most prominent NoSQL database
Data model: Stores collections containing documents (JSON objects)
Has expressive query language
Can use indexes for fast lookups
Tries to handle scalability, reliability, etc.

# 19 Cookies and Session
How do we know what user sent request?
- Would like to authenticate user and have that information available each time we process a request.
- More generally web apps would like to keep state per active browser
Called **session state**

Session state lookup problem : 
- HTTP request just come into a web server
Not a lot information to uniquely identify "session"
- Solution: Include something in the request to tells us the session
Care must taken to avoid forgeries
- Early HTTP solution: Cookies
State set by web server that browser attaches to every request
Useful but with a checkered history
- Modern browser support local storage API

Cookie contents : 
- Cookie: name and data
Domain for this cookie: server, port (optional), URL prefix (optional).
The cookie is only included in requests matching its domain.
Expiration date: browser can delete old cookies
- Limits:
Data size limited by browsers (typically < 4 KB).
Browsers limit the number of cookies per server (around 50).

Options for storing session state : 
- Web server's memory
Fastest access
May be too large (many active users)
Makes load balancing across web servers hard
- Storage system
Easily shared across all the web servers
May be overkill: Don't need the super reliability of storage system
May be too much load for the storage system
- Specialized storage system
Support fast fetching of small, short-lived data
Example: memcache, redis - in memory key-value stores

Cookie replacement: Web Storage API : 
- sessionStorage - Per origin storage available when page is open
- localStorage - Per origin storage with longer lifetime
- Standard key-value interface:
localStorage.appSetting = 'Anything';
localStorage.setItem('appSetting', 'Anything');
sessionStorage['app2Setting'] = 2;
- Limited space (~10MB) and similar reliability issues to cookies

# 20 Input and Validation
Early web app input: HTTP form tag
Server-side validation: 
- Regardless of validation in browser server needs to check everything
Easy to directly access server API bypassing all browser validation checks

# 21 Full stack state management
Session state ：
- Must be kept in sync between the browser app and the server
Who, if anyone, is logged in?
- Server will need to reject any requests from users not logged in
Model fetching done only at view/controller startup might not work
- Consider transitions of your photo app
Login - Not logged in to logged in
 At app startup most models are not available (e.g. sidenav user list) but become available after login is completed.
Logout - Logged in to not logged in
 Requests to web server that worked before will now fail

Dealing with other model changes
What happens if another user adds a photo or comment? Options:
- Do nothing: Easy!
User won't see new material until they do something that caused the model to be refreshed
Very disconcerting if they don't see their own changes
- Poll: Periodically check for changes or just refetch the model
Can provide a UI widget to trigger model refresh
- Server push: Have the server push model changes as soon as they occur
User sees updates as soon as possible
Might conflict with user changes or be disconcerting for the user
Implementation is easier with Web Sockets

# 22 Web App Security - Browser Isolation
Security is an hard problem :
- Many opportunities for attackers
Full stack means there are many interface that an attacker can use
- Hard to identify all the vulnerabilities
Complexity of system make it impossible guarantee no vulnerabilities
- Even a small mistake can compromise entire application
Only as strongest as the weakest link

Modes of attacks on web applications :
- Attack the connection between browser and web server
Steal password
Hijack existing connection
- Attack the server
Inject code that does bad things
- Attack the browser
Inject code that does bad things
- Breach the browser, attack the client machine
- Fool the user (phishing)

Security Defences :
- Isolation in browsers
Web app run in isolated sandbox
- Cryptography
Protect information from unauthorized viewing
Detect changes
Determine origin of information
- Web development frameworks
Use patterns that help, avoid dangerous ones

# 23 Network Attacks
Network Attacks :
- "man in the middle" attacks
- Attacker has access to network communication between browser and server.
- Passive attacks:
Eavesdrop on network traffic
- Active attacks:
Inject network packets
Modify packets
Reorder, replay packets
Block packets

Secure Sockets Layer (SSL) & Transport Layer Security (TLS) - HTTPS
- Protocol used for secure communication between browsers and servers
- Browser uses certificate to verify server's identity.
- Only one way: SSL/TLS does not allow the server to verify browser identity.
- Uses certificates and public-key encryption to pass a secret session-specific key from browser to server

# 24 Other Attacks
## Session Attacks
Cross-Site Request Forgery (CSRF)
- Attackers can potentially hijack sessions without even knowing session ids:
- Scenario:
Visit your bank's site, start up web app, log in.
Then visit the attacker's site (e.g. discussion forum with links, forms, etc.)
Attacker's page includes JavaScript that submits form to your bank.
When form gets submitted, browser includes bank's web app cookies, including thesession id.
Bank transfers money to attacker's account.
The form can be in an iframe that is invisible, so you never know the attack occurred.
This is called Cross-Site Request Forgery (CSRF) : Untrusted site uses trust that was given to user's browser(Sea-surf)

## Code Injection Attacks
Stored Cross Site Scripting Attack(XSS) :
- Attacker stores attacking code in a victim Web server, where it gets accessed by victim clients. Call a Stored Cross Site Scripting Attack
- On previous generations of web frameworks was a major attack loophole
Lots of stuffing things into innerHTML, bad escape processing
- Less so on JavaScript frameworks
Care is taken before stuffing things into the DOM

SQL Injection : 
Injection can also be used to extract sensitive information
- Modify existing query to retrieve different information
- Stolen information appears in "normal" Web output

Solutions : 
- Don't write SQL
- Use a framework that knows how to safely build sql commands:

## Phishing Attacks
Phishing(钓鱼网站)
- Basic idea:
Get unsuspecting users to visit an evil Web site
Convince them that the evil Web site is actually a legitimate site (such as a bank or PayPal)
Trick the user into disclosing personal information (password, credit card number, etc.)
Use the personal information for evil purposes such as identity theft.
 
## Denial of Service Attacks
**Denial of Service Attacks (DOS Attacks)**
- An attack that causes a service to fail by using up resources
Could be an accident (e.g. upload too big of a file) or on purpose
- Example from our Photo App:
User uploads photos, comments, user registration until our storage fills.
Establish so many connections our web server falls over
- Resource could be at networking layer
Use all the bandwidth of the network coming into our website
Use all the network sockets

**Distributed Denial of Service (DDoS) Attacks**
- DOS attack that uses many attacking machines
Example: Get control of a million machines and point them at someone's web server
- Botnets - Collection of compromised machines under control
- Has become an extortion business

**Web App DOS mitigation**
- None perfect - really hard problem
Do want to take steps to avoid accidental DOS and make purpose-driven DOS harder
- Resource quotas
Track resource consumption per user and provide way of cutting off users
Good for catching accidents, less so for malicious attacks
- Make resources cost money
Raises the cost or hassle for an attacker
Not always possible under business model
- Network layer: Need to push back on attack stream
Do things like cut off traffic coming from some part of the internet

# 25 Large-Scale Web Applications
**Scale-out architecture**
- Expand capacity by adding more instances
- Contrast: Scale-up architecture - Switch to a bigger instance
Quickly hit limits on how big of single instances you can build
- Benefits of scale-out
Can scale to fit needs: Just add or remove instances
Natural redundancy make tolerating failures easier: One instance dies others keep working
- Challenge: Need to manage multiple instances and distribute work to them

**Scale out web servers: Which server do you use?**
- Browsers want to speak HTTP to a web server
- Use load balancing to distribute incoming HTTP requests across many front-end web servers
- HTTP redirection (HotMail, now LiveMail):
Front-end machine accepts initial connections
Redirects them among an array of back-end machines
- DNS (Domain Name System) load balancing:
Specify multiple targets for a given name
Handles geographically distributed system
DNS servers rotate among those targets

**Load-balancing switch ("Layer 4-7 Switch")**
- Special load balancer network switch
Incoming packets pass through load balancer switch between Internet and web servers
Load balancer directs TCP connection request to one of the many web servers
Load balancer will send all packets for that connection to the same server.
- In some cases the switches are smart enough to inspect session cookies, so that the same session always goes to the same server.
- Stateless servers make load balancing easier (different requests from the same user can be handled by different servers).
- Can select web server based on random or on load estimates

**nginx ("Engine X")**
- Super efficient web server (i.e. speaks HTTP)
Handles 10s of thousands of HTTP connections
- Uses:
Load balancing - Forward requests to collection of front-end web servers
Handles front-end web servers coming and going (dynamic pools of server)
  Fault tolerant - web server dies the load balance just quits using it
Handles some simple request - static files, etc.
DOS mitigation - request rate limits
- Popular approach to shielding Node.js web servers

**Scale-out assumption: any web server will do**
- Stateless servers make load balancing easier
Different requests from the same user can be handled by different servers
Requires database to be shared across web servers
- What about session state?
Accessed on every request so needs to be fast (memcache?)
- WebSockets bind browsers and web server
Can not load balance each request

**Scale-out storage system**
- Traditionally Web applications have started off using relational databases
- A single database instance doesn't scale very far.
- Data sharding - Spread database over scale-out instances
Each piece is called data shard
Can tolerate failures by replication - place more than one copy of data (3 is common)
- Applications must partition data among multiple independent databases, which adds complexity.
Facebook initial model: One database instance per university
In 2009: Facebook had 4000 MySQL servers - Use hash function to select data shard

**Memcache: main-memory caching system**
- Key-value store (both keys and values are arbitrary blobs)
- Used to cache results of recent database queries
- Much faster than databases:
500-microsecond access time, vs. 10's of milliseconds Example: Facebook had 2000 memcache servers by 2009
Writes must still go to the DBMS, so no performance improvement for them
Cache misses still hurt performance
Must manage consistency in software (e.g., flush relevant memcache data when database gets modified)

Scale-out web architecture : 
Internet -> Load Balancer -> Web Server(....) -> Database Server(...)
                                              -> Memcache(...)

**Scaling issues were hard for early web app**
- Startup: Initially, can't afford expensive systems for managing large scale.
- But, application can suddenly become very popular ("flash crowd"); can be disastrous if application can not scale quickly.
- Many of the early web apps either lived or died by the ability to scale
Friendster vs. Facebook

**Cloud Computing**
- Idea: Use servers housed and managed by someone else
Use Internet to access them
- Virtualization is a key enabler
Specify your compute, storage, communication needs: Load balancer : 1, Web Server : 100, Database : 50, Memcache : 20
Cloud provider does the rest
- Examples:
Amazon EC2
Microsoft Azure
Google Cloud
Many others

**Cloud Computing Advantages**
- Key: Pay for the resources you use
No up front capital cost
Need 1000s machines right now? Possible
Perfect fit for startups:
1998 software startup: First purchase: server machines
2012 software startup: No server machines
- Typically billing is on resources:
CPU core time, memory bytes, storage bytes, network bytes
- Runs extremely efficiently
Buy equipment in large quantities, get volume discounts
Hirer a few experts to manage large numbers of machines
Place servers where space, electricity, and labor is cheap

**Content Distribution Network (CDN)**
- Consider a read-only part of our web app (e.g. image, html template, etc.)
Browser needs to fetch but doesn't care where it comes from
- Content distribution network
Has many servers positions all over the world
You give them some content (e.g. image) and they give you an URL
You put that URL in your app (e.g. <img src="...)
When user's browsers access that URL they are sent to the closest server (DNS trick)
- Benefits:
Faster serving of app contents
Reduce load on web app backend
- Only works on content that doesn't need to change often

# 26 Data Centers
**Evolution of data centers**
- 1960's, 1970's: a few very large time-shared computers
- 1980's, 1990's: heterogeneous collection of lots of smaller machines.
- Today and into the future:
Data centers contain large numbers of nearly identical machines
Individual applications can use thousands of machines simultaneously
- Companies consider data center technology a trade-secret
Limited public discussion of the state of the art from industry leaders

**Typical specs for a data center today**
- 15-40 megawatts power (Limiting factor)
- 50,000-200,000 servers
- $1B construction cost
- Onsite staff (security, administration): 15

# 27 Future directions
**MEAN software stack**
- Stack works but not the final say in web app technologies
- Angular.js
Browser-side JavaScript framework
HTML Templates with two-way binding
Directives and services for modular design
Much single page application support - routing, model fetching, etc.
- Node.js / Express.js web server code
Server side JavaScript
High "concurrency" with event-based programming
- MongoDB "document" storage
Storage system support scale out (sharing and replication), queries, indexes

**Front-end alternative - ReactJS from Facebook**
- JavaScript framework - Does view component only
- View declared in JavaScript (more accurately a lang translated to JavaScript)
Angular: HTML with JavaScript embedded
React: JavaScript with HTML embedded
- Basic building block: Components
Have a function render() that returns HTML-like structure
Accepts inputs (this.props)
Have an internal state (this.state)
- Components are reusable pieces composed to form view

**React benefits**
- High performance for rapidly changing views
Less time calling into Browser's DOM
- Server-side rendering
Can run React either on server or browser
Faster startup by pushing HTML from server
- React Native
Have native mobile apps for iOS and Android that speak React

**Go Language**
- System programming language released in 2007 by Google
Done by original Unix authors (Reacting to complexity of C++ and Java)
From Wikipedia:
A compiled, statically typed language ..., with garbage collection,
memory safety features and CSP-style concurrent programming ...
- Cross C & scripting languages
Productive and readable programs
C-like but got rid of unnecessary punctuations

**Full stack engineering**
- Tall order to fill
Make pretty web pages by mastering HTML and CSS
Architecture scalable web service
Layout storage system system sharding, schema, and indexes
- Typically people specialize
The expert in CSS is different than expert in database schema is different from the ops team

**Looking to the future**
- Systems likely one of the cloud providers will offer a platform that most web applications can just build off
LIke people don't write their own operating system anymore.
Technologies and app demands have been changing so much we still in the roll your ownphase.
- Pieces are coming together
World-wide scalable, reliability, available storage systems (e.g. Google's spanner)

**Web Apps versus Native Apps**
- Web Apps advantages:
Available on all platforms - Smaller, faster development
Easy "update" of application
Customize application per user
- Native apps
Native look and feel user interface
Integrate with host platform
- Hybrid approach: Embed browser in native app
- Backend can be largely the same for both - (e.g. REST APIs)
