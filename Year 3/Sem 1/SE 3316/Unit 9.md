# Semantic Web
▪ coined by Tim Berners-Lee (1997)
"The Semantic Web is an extension of the current web in which information is given well-defined meaning, better enabling computers and people to work in cooperation.”

Embed meaning in a way so that programs can read it

XML allows "meaningful" tags to be added, but this is only sensible to humans, and not machines.
Schemas allow machines to somewhat understand each tag meaning if the same schema is used, different schemas will not work with each other to increase machine understanding.

Goal is to connect different schemas and link their meanings.
![[Pasted image 20241206230346.png]]
### Resource Description Framework (RDF)
RDF is to representing the world around us, is in XML.
It is a language for representing metadata about Web resources
	Title, author, and modification date of a web page,
	Copyright and licensing information about a Web document,
	Availability to schedule for a shared resource
Used to representing "things" that aren't directly retrievable (e.g. person, house) 

RDF Concept:
"John Smith created a particular web page"
"website" has a ***Creator*** whose value is ***John Smith***
Important parts:
	"thing" being described (webpage)
	property of "thing" (creator)
	value of property (John Smith)

Graph Structure:
Written using XML, suitable for tree structures
![[Pasted image 20241206231506.png]]
Resources are identified by various URIs
Literals are identified by names
Properties are the arrows
![[Pasted image 20241206232318.png]]
Property URIs
	Pick a base URI for your RDF vocabulary:
	• http://amk.ca/xml/review/1.0#
	▪ The base URI is assigned to a prefix, such as "rev".
	▪ Properties are then referenced as 'rev:subject', 'rev:topic', etc.
	▪ The RDF parser will concatenate the base URI (from the prefix) and the
	name:
	• rev:subject → http://amk.ca/xml/review/1.0#subject

RDF Vocabularies
	▪ DC (Dublin Core)
		• Namespace: http://purl.org/dc/elements/1.1/
		• Properties: title, creator, publisher, subject, identifier, …
	▪ FOAF (Friend-of-a-friend)
		• Describes people
		• Classes: Person
		• Properties: name, interest, mbox, schoolHomepage, workplaceHomepage
		• Namespace: http://xmlns.com/foaf/0.1/
	▪ DOAP (Description of a Project)
		• Describes open source projects
		• Classes: Project, Repository
		• Properties: name, homepage, mailing-list, license, maintainer
		• Namespace: http://usefulinc.com/ns/doap#
	▪ RSS (RDF Site Summary)

Pros and Cons
Pros:
	RDF exists and is strictly specified
	RDF is decentralized. allowing anyone to create their own vocabulary, giving it many implementations
Cons:
	Tedious to write by hand
	Requires a decent amount of knowledge

### RDFa – RDF in Attributes
Set of attribute-level extentions to XHTML/XML
Allows embedding RDF triplets 
Compliant user agents can extract these triplets
Benefits
	• Publisher independence - each site can use its own standards
	• Data reuse - data is not duplicated.
	• Self containment - HTML and the RDF are contained in the same document
	• Schema modularity - attributes are reusable
	• Evolvability - additional fields can be added in future

Attributes
	▪ **about** - a URI specifying the resource the metadata is about
	▪ **rel** and **rev** – relationship and reverse-relationship with another resource
	▪ **src**, **href** and **resource** – partner resource
	▪ **property** – property for the content of an element or the partner
	resource
	▪ Optional: **content**, **datatype**, **typeof**

![[Pasted image 20241206233201.png]]
