# XML
### Introduction
XML: Extensible Markup Language
A framework for defining markup languages (IT IS NOT A MARKUP LANGUAGE DISPITE GOOGLE AND THE NAME)
Inherently internationalized and platform independent (Unicode)

### Recipes in XML
You can name your own tags in anything
This defines the recipe of the XML file
![[Pasted image 20241111143726.png|500]]
### XML Notation
Defining the syntax of our recipe language
	• DTD, XML Schema, ...
	• What do we gain by formally defining our language?
Showing recipe documents in browsers
	• XPath, XSLT (XML Stylesheet Language Transformation)
	• What are the roles of XPath and XSLT?
Building a recipe editor
	• DOM, SAX (Simple API for XML), XML libraries

### XML Trees
![[Pasted image 20241111144455.png]]
This is the same with file systems and file paths
Wildcards: * matches any group of characters; ? matches a single character; [] match a single
character within the given range. E.g. [3e-h] Matches any character in the set [3, e, f, g, h].
What does File path: /home/\*/\*/Hello.* map to?

![[Pasted image 20241111144633.png]]

### Nodes in XML Trees
▪ Text nodes: carry the actual contents, leaf nodes
	written as the text they carry
▪ Element nodes: define hierarchical logical groupings of contents, each have a name
	start-end tags: \<foo> <\/foo>
▪ Attribute nodes: unordered, each associated with an element node, has a name and a value
	name="value" in start tags
▪ Comment nodes: ignorable meta-information
	<\!--baz-->
▪ Processing instructions: instructions to specific processors, each have a target and a value
	<\?target-value?>
▪ Root node: Starting node that represents the entire tree

### Structure
![[Pasted image 20241111145031.png]]

### XML Namespaces
When combining languages, there may be element names that are the same, this causes confusion
Solution:
	Add the XML language before the element
	![[Pasted image 20241111145152.png|500]]
▪ Prefix xmlns is reserved for namespace declarations
▪ Prefixes starting with xml are reserved for future use

### XML Languages
XML language:
	• a set of XML documents with some semantics
Schema:
	• a formal definition of the syntax of an XML language
	while formal, it is used because of human-readable descriptions
	allows to define rulesets and structure
	data validation can be preformed
Schema language:
	• a notation for writing schemas
Validation:
![[Pasted image 20241111145349.png|500]]

### XML Stylesheet Language
**XML** separates content and presentation format
**XSL** defines the presentation format
XSL consists of
	• XSLT – a language for transforming XML
	• XSL-FO – an XML vocabulary for specifying formatting semantics
	• XPath to access or refer parts of XML documents
Why XSL?
	De-coupling the presentation (XSL) from data (XML)
		• An XML document can be made to look different depending on what stylesheet is applied to it
		• “XSL is to XML as CSS is to HTML”
	Existing XML document can also be repurposed for another using XSL stylesheets
![[Pasted image 20241111145744.png|500]]
![[Pasted image 20241111145756.png|500]]
