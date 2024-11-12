Troubleshooting with Docker:
docker run -it -v $(pwd)/.gradle:/home/gradle/.gradle -v $(pwd):/home/gradle/project -w /home/gradle/project/XXXXXXXXXXXXXXX -p XXXX:XXXX --link mysql:mysql --link redis:redis --name gradle-widget gradle:7.0.2 bash

Given this command line, "--link" is depreciated.
Alternatively use network: 
	"docker network create networkname"
	"docker network ls" to confirm creation
	"docker network connect containername" do for any containers needing to connect
	"docker network inspect networkname" to confirm containers are connected container sections should display the two containers
	"docker exec mysql ping gradle-widget -c2" to check if the two containers can communicate

useful commands: 
	cd directory: used to change command line location
	cd ~: resets command line location to defualt
	
