### Repository
subsystems access and modify a single data structure called the central repository.  
![[Pasted image 20241113102420.png]]
### Model-View-Controller (MVC)
Subsystems are classified into three different types:  
	Model subsystems: maintain domain knowledge,  
	View subsystems: display it to the user  
	Controller subsystems: manage the sequence of interactions with the user.
![[Pasted image 20241113102529.png|200]]
### Client/Server
The server subsystem provides services to instances of other subsystems called the clients, which are responsible for interacting with the user.
### Peer-to-Peer
### Multi-Tier
Subsystems are organized hierarchically based on the dependency  
The bottom layer/tier is the most independent  
Every layer/tier can access the tier(s) below them  
Closed architecture: only one layer below is accessible.  
Open architecture: a layer can access services of any of the layers below it
### Pipe and filter
  
Subsystems process data received from a set of inputs and send results to other subsystems via a set of outputs.  
The subsystems are called “filters,” and the associations between the subsystems are called “pipes.”  
Each filter knows only the content and the format of the data received on the input pipes, not the filters that produced them