# Docker Cheatsheet

#### Start en ny Container fra et Image

`docker run IMAGE`     
`docker run Ubuntu`    

#### Adgang til container gennem terminalen

`docker run -it Ubuntu`    
* -i = interactive
* -t = Teletypewriter (terminalen) 

#### Adgang til container gennem http protokollen (browseren, Postman etc.)

`docker run -p [host_port]:[container_port] IMAGE`    
`docker run -p 8080:80 nginx`    
* -p = port mapping
