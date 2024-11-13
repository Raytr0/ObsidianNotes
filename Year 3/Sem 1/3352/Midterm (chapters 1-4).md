# Chapter 1:
SOFTWARE DEVELOPMENT LIFE CYCLE (SDLC):
![[Pasted image 20241009004123.png]]
Waterfall model:
	Hard to change anything after starting
Incremental model:
	Basically different versions
		Throw-away prototyping
		Evolutionary prototyping

Agile:
![[Pasted image 20241008224816.png]]
The twelve agile principles:
	Satisfy the customer:
		Highest priority
		Through early and continuous delivery of valuable software.  
	Welcome changing requirements:
		Anytime in the development
	Deliver frequently
	Cross-functional and cross-divisional collaboration:
		Business and programming people collab
	Provide support and trust
	Personal communication
	Working Software
	Sustainable pace:
		The sponsors, developers, and users should be able to maintain a constant pace indefinitely.
	Pursuit of technical excellence
	Simplicity is essential
	Acting self-organized
	Inspection and adaption:
		At regular intervals, the team reflects on how to become more effective, then tunes and adjusts its behavior accordingly.

Agile framework: SCRUM
![[Pasted image 20241008225046.png]]
# Chapter 2:
Types of Requirements:
	Business Requirements:  
		High-level needs, goals, and objectives of the organization.  
		• They should be measurable and timebound.  
		• Example: Increase revenue by accepting credit-card  
		payments before the new year (by Dec. 31st )
	Stakeholder Requirements:
		Express the needs of a specific stakeholder or group of stakeholders, which may include customers, users, or suppliers.  
		• communicate the material interest of the stakeholders in the outcome of the product, service, or result.  
		• provide a basis for identifying the solution requirements
	Solution Requirement:
		Describe the characteristics of a solution in enough detail to design a solution.  
		Functional requirements (FRs): 
			describe the required behaviors of the solution. These are often expressed from the perspective of the system.  
		Nonfunctional requirements (NFRs): 
			Describes how well the system must perform in its intended environment and how it should respond to constraints on its behavior. NFRs are also called service-level requirements (SLRs), supplementary requirements, and quality requirements.
			![[Pasted image 20241008230227.png]]
	Transition Requirements:
		Describe the temporary capabilities that are essential to migrate  
		from the current state to a future state environment  
		• Include conversion of data from current system and training needed  
		to address skill gaps  
		• May also describe how the solution will be deployed and released into  
		production—such as migration and training requirements.  
		• E.g. The system must be deployed as a Docker container

Requirements Elicitation:
Discovery process used to bring forward or produce information relevant to the project or program by drawing out information from stakeholders and other sources.
Used to identify problems.
Concepts:
	Interviews:
	Facilitated Workshops:  
		Convene stakeholders or multidisciplinary teams in a focused and structured session to identify requirements, reconcile differences, and reach consensus among the participants. These interactive workshops enable discovery of requirements while resolving conflicts early in the project life cycle.
	Focus Groups:
		Focus groups assemble prequalified participants, such as subject matter experts, in a group setting to share their attitudes and expectations about a particular product, service, or result. The group members voice their opinions and provide clarity on specific topics. This technique provides qualitative feedback that can be further examined as requirements are analyzed.
	Brainstorming:
	Questionaries and Surveys:
	Document Analysis:
		Document analysis inspects a wide range of materials, such as a glossary of terms, strategic and business plans, process flows, problem/issue logs, regulations, policies, and procedures to discover and/or verify requirements. 
		• This technique provides a good starting point for eliciting relevant product details. 
		• Using up-to-date and accurate documentation is important to safeguard against erroneous information.
	Interface Analysis:
		Used to define requirements by examining system interactions between users, processes, and other system components. 
		• It helps to establish relationships and boundaries by determining the input and output needs of each interfacing system. 
		• This method is useful for identifying additional stakeholders who may be impacted by changes to the system interfaces, as well as potential interoperability issues.
	Prototypes:
	Mock-ups/Wireframes (design thinking):
		• Creating Mockups or wireframes either on paper or using tools like Visio to facilitate the communication. 
		• Can be seen as an overlap between Elicitation, analysis and interface design. Mock-ups / Wireframes (Design Thinking) 
	Observation:
		Also known as “job shadowing,” provides a direct way of viewing people in their environment to see how they perform their jobs or tasks and carry out processes within their environment. 
		• This technique is particularly helpful for eliciting tacit requirements that are difficult to verbalize.
	Analyzing existing systems:
	Analyzing other similar systems:

# Chapter 3
Requirements Analysis:
	Specifying and modeling:
		Domain Model:
			The domain model is a conceptual model that summarizes what we collected in the elicitation stage.  
			Mind Maps are popular tool to create conceptual models
		Workflow Model:
			Basically UML Diagrams
			Shows the Execution flow
			![[Pasted image 20241009003412.png]]
		Data Model:
			Simplified ER Diagram
			Represents the nouns and their basic relationships with each other  
			The adjectives are the attributes in the underlying tables, representing properties or states.
			![[Pasted image 20241009003400.png]]
		Business Rules:
			Examples:
				Loans of $100,000 or more must be approved by a senior officer
				Customers with deposits of less than $10,000 cannot be offered fixed interest rates
				Customers who pay back their loan in less than half the agreed loan period must pay a fee of 1.5% of the original loan amount
				A loan below $2,000,000 will be automatically decisioned
				An Olympic athlete can only play a sport for one country
		User Interface Design:
			What the product looks like from a user's persepective
	Traceability:
		Forward Traceability: 
			Starting from an artifact (e.g. document, model, requirement, test cases, ... etc.) we should be able to find all artifacts that were dependent on it. 
		Backward Traceability: 
			Starting from an artifact (e.g. document, model, requirement, test cases, ... etc.) we should be able to find all artifacts that it depended on (the sources) 
		Bidirectional Traceability: 
			Starting from an artifact we should be able to find all artifacts lead to it and those that built on it.

# Chapter 4
Work items in an Agile Project
Epics:
	is a large body of work that can be broken down into a number of smaller stories. Can be seen as:  
	- A logical grouping of related user stories  
	- A big user story that needs to be broken down
Features:
	A feature is an actionable aspect of an epic that can include multiple user stories (not always included)
User Stories:
	A User Story is a feature or requirement from the user’s perspective
	As simple as possible  
	• Template:  
	• As a <\type of user>, I want <\goal> so that <\reason >.
	![[Pasted image 20241009193425.png]]

![[Pasted image 20241009003700.png]]

INVEST
![[Pasted image 20241009003850.png]]