Client-Side Vs Server-Side
	Client handles UI
	Server handles db operations and other processing tasks
	REST API used to provide stable interface for server side operations
	Use Fetch() to interact with server API

Applications with Client-Side JavaScript
	Packaged with HTML
	Access DOM with JavaScript
	Lot of code needed to keep server and client in sync

Angular
	Front-end JS framework
		Written in TypeScript
	Compose HTML templates with Angular markup,
	Write component classes to manage templates
	Write application logic in services
	Package components and services in modules.
	Launch the app by bootstrapping the root module

Angular Architecture
![[Pasted image 20241106101052.png]]

Angular Structure
	Components:
		defines ***views***, which are sets of screen elements you can choose and modify
		uses ***services***, which provide functionality (Similar to imports?)
	Metadata:
		TypeScript decorators provide metadata for Angular
		component class treats it as a ***Template*** that defines a view
			Template:
				Combines HTML with Angular ***directives*** and ***binding markup*** that allow Angular to modify the HTML before it displays
			Service:
				Provides info for Angular to make available to components through ***Dependency Injection***

JavaScript Decorators
	Similar result as inheritance, allows changing a class/object
	Executes at run-time
	Wraps an object/class with another "decorator" class/function
		• Allows dynamic modification
		• Allows common functionality to be applied to many classes – not easy with inheritance

Combining Front and Back
	Front-end requires server end-point to update view, called "dev server"
	Back-end API also requires a server end-point
	Two servers on same host different port required
		Issue with cross-origin requests begin, which requires Cross Origin Resource Sharing mechanism
	Two ways to solve this:
		One server (back-end) with static route
		![[Pasted image 20241106125416.png|300]]
		Two servers (front and back) with a proxy
		![[Pasted image 20241106123427.png|300]]

Advanced TypeScript:
Arrays
	forEach(), map(), reduce(), filter()
Function expression with arrow notation (=>)

Further slides explain what each function does (READ)

JSON Web Tokens (JWT)
Need to separate authentication from access control
	Distributed authentication – separate servers for auth.
	Federated authentication – 3rd party auth.
Open standard for tamper-proof info transmission (Does not mean SECURE)
Transmitted as JSON object
Digitally signed and can be verified
	Password: HMAC
	Public Key: RSA or ECDSA

Explains JWT formatting and stuff (READ)