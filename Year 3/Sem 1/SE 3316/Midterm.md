# Week 1 and 2 (Intro)
### The Origins of the WWW
▪ WWW was invented by Tim Berners-Lee at CERN (1989)
▪ Hypertext across the Internet (replacing FTP)
▪ Three constituents: HTML + URL + HTTP
	• HTML is an SGML language for hypertext
	• URL is a notation for locating files on servers
	• HTTP is a high-level protocol for file transfers

### Uniform Resource Locator - URL
scheme (http), server (example.com) and path (/ex/one)
• http://example.com/ex/one/
http is most common scheme

### Internationalized Resource Identifier - URI
▪ scheme:scheme-specific-part
▪ Conventions about use of /, #, and ?
	• “/” for separating hierarchical structure
	• “?” for separating a query from a resource that can respond to a query
	• “#” for separating URI from “fragment identifier”
***This is the stuff that makes up the URL***

Syntax of URI is restricted to US-ASCII
Makes it Vulnerable to IDN homograph attacks
	Meaning replacing letters in the link that look identical but are not US-ASCII characters

### Data Flow Models in WWW
![[Pasted image 20241017014922.png]]

Understand HTML, CSS, JavaScript
In HTML always use linking files in tags using src, its good practice
Note that HTML does have a formal syntax specification, always check for HTML validity 
### Issues with JavaScript
Browsers interpret differently
	• Many workarounds to make things work
	• JQuery has arisen as a “quasi standard”
Lack of features
	• Evolving to address some concerns
Competition
	• Dart from Google
	• TypeScript from Microsoft
	• CoffeeScript from Ruby community

### Unicode
Unicode aims to cover all characters in all past or present written languages
Uses 32 bit namespace
	• Theoretical size of ~4 billion
	• Only 1,114,112 are allowed
	• As of May, 2020, has 143,859 characters
		o V15.1 (Sep. 12, 2023) has 149,813 characters
	• Covers 161 modern and historic scripts
Assigns a unique number to each character
	• Called a “code point” and depicted with U+xxxx in hexadecimal notation
	• E.g. Egyptian hieroglyph A036 is U+1302 with the glyph

### Unicode Principles
Unicode Characters
	• A character is a symbol that appears in a text
	• Mapping characters to numbers
	• Numbers are called “code points”
Glyphs
	• Pictorial representation of each code point
	• Handled by fonts
Encoding/Decoding
	• Convention for mapping “code points” to a serial bit stream (“code units”)
	and vice versa
	• UTF-8 (8-bit code units), UTF-16 (16 bits) 

### Unicode Code Points
▪ A code point is a unique number assigned to every Unicode character
▪ Code points are between 0 and 1,114,112
▪ Current standard (15.1, Sep. 12, 2023) has 149,813 characters
▪ The character HIRAGANA LETTER SA is assigned the code point 12,373
▪ Written as U+3055 (4+ digit hex of code point)
▪ Code point 0 through 127 coincide with ASCII
▪ Some code points are never assigned

# Week 3 (JavaScript)
• JavaScript runs right inside the browser
• JavaScript is dynamically typed
• JavaScript is object oriented in that almost everything in the language is an object
	‒ Objects in JavaScript are prototype-based
	‒ Objects in C++, Java etc are class-based
	‒ Makes JavaScript objects quite different
![[Pasted image 20241017015944.png]]

### Client Side Scripting
Pros:
	Offloads computation to user's computer
	Can allow for faster responses
Cons:
	JavaScript may not be enabled in client's browser
	Browser differences may result in inconsistencies in script execution
	JS heavy web applications may be complicated to debug and maintain

### History
• Introduced by Netscape in their Navigator browser in 1996.
• An implementation of ECMAScript
• JavaScript was only slightly useful, and quite often, very annoying to many users
• JavaScript became a much more important part of web development in the mid 2000s with the ability to interact with Document Object Model and AJAX.
• As an acronym it means Asynchronous JavaScript And XML.
	‒ The most important feature of AJAX sites is the asynchronous data requests.
• ECMAScript is the name of JavaScript standard developed by ECMA
	‒ Latest is ECMASript-262 (15th edition) released in June 2024

### Data Requests
Old way with no JavaScript:
	Get form
	User interacts and makes changes
	send changes
	get updated form
	reload form to display to user\
	repeat until finished
New way with JS:
	Get form
	User interacts and makes changes
	request data to correspond to the changes
	no need to reload entire page, browser updates with recieved data to put in list or something

### JS libraries. frameworks
if you dont know then damn

### Where does JavaScript go?
Inline
	<\a href="JavaScript:OpenWindow();">more info<\/a>
	<\input type="button" onClick="alert('Hi!');" />
Embedded
	<\script type="text/javascript">
	/* A JavaScript Comment \*/
	alert("Hello World!");
	<\/script>
	Nightmare to maintain above styles
External (Best)
	Just the way you do it normally

### The <\noscript> tag
Runs when user does not have the ability to run JS
Usually just notifies user to enable it

### Strict Mode
"use strict";
turns "silent errors" to "throw errors"
easier to optimize code this way

### Operators
== is equal to type
=== is equal to value and type
vice versa for not equals
<,>,=<,=>
### Conditionals
```js
if (){

} else if (){

} else {

}

switch () {
case "":
output = "";
break;
default:
output = "";
}

x = (y==4) ? "y is 4" : "y is not 4"
//y==4 is the condition, ? "output if true" : "output if false"
```
A value is said to be truthy if it evaluates to true, while a value is said to be falsy if it evaluates to false.
false, null, "", '', 0, NaN, and undefined are falsy
# Week 4
Its networking stuff for HTTPS, short slides just read again its stuff repeated from networking with additional details about the protocol

# Week 5
Server Side Scripting
Kinda self explanatory? 
Its just back-end
Explains how servers and databases if needing to connect to client side stuff (front-end) they have frameworks and script languages to process the data
***REST*** (Prob need to read into this)
HTTP GET POST stuff like that
Talks about SQL
Async interactions and implementation
AJAX
JavaScript Promises functions
Input sanitation (Defending stuff like SQL injections but javascript you know this)
