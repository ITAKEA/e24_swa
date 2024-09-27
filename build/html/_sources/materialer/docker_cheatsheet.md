# Docker Cheatsheet

**Start en Container fra et Image**
    
> `docker run ubuntu` (Ubuntu er Image navnet)    

**Adgang til container gennem terminalen**

> `docker run -it ubuntu`    
>  -i : interactive    
>  -t : Teletypewriter (terminalen) 

**Adgang til container gennem http protokollen (browseren, Postman etc.)**

>  `docker run -p [host_port]:[container_port] IMAGE`    
>  `docker run -p 8080:80 nginx`    
>  -p : port mapping    


**Delete en container når den slukkes**

> `docker run --rm  Ubuntu`    
> --rm : remove (after close)

**Se en liste over Images**

> `docker images`

**Slet et image**

> `docker rmi <id_til_image>`    

**Se en liste over Containers**

> `docker ps`     

og ikke kørende containers     

> `docker ps -a`    
> -a : all    

**Download et image**    

> `docker pull ubuntu`    

**Tilføj miljøvariabler**

> `docker run -env GITHUB_TOKEN=xyz123dkajh`    
> -env : environement


**Ekstra**    
---

**Kør container så den ikke blokerer terminalen**

> `docker run -d nginx`    
> -d : detached

**Del en mappe fra host til container**    

> `docker run -v /host/path:/container/path`
> `docker run -v /user/clbo/flaskapp:/app`


**Push et image til docker hub**    

> `docker login`    
> `docker push IMAGE`

**Giv din container et navn**        

> `docker run --name min_container ubuntu`    
> --name : containernavn




