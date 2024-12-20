# Azure Deployment 1
I dag og næste gang skal i lære at deploey jeres microservices til Azure.

## Læringsmål
* Kunne deploye microservices til Azure webapp services
* Kunne opsætte en CI/CD pipline med Github, Github action, Dockerhub og Azure Webapps

## Forberedelse
* Opret en Students account på **[Azure](https://azure.microsoft.com/en-us/free/students/)**
* Opret en account på **[DockerHub](https://hub.docker.com/)**
* Kør kommandoen: `docker run -it --rm -p 5001:80 clbo/joke-service:latest`      
    (vi skal arbejde med dette image i timerne).


## Dagen i dag
* Gennemgang af Azure Portal
    * Azure Web App
    * forbind til dockerhub 
        * [Tip 12: Deploying a container image to Azure App Service from Docker Hub](https://www.youtube.com/watch?v=_LNOg8kU4CE)
* DockeHub
    * push image til docker hub
        * docker build -t clbo/jokes-service:0.0.1 --push
        * (el. docker push clbo/jokes-service:0.0.1)

* Github Actions

## Materialer
* [https://jokes-service.azurewebsites.net/](https://jokes-service.azurewebsites.net/)
* [https://github.com/ITAKEA/jokes_service](https://github.com/ITAKEA/jokes_service)
* [DockerHub - joke-service](https://hub.docker.com/r/clbo/joke-service)
* [Tip 12: Deploying a container image to Azure App Service from Docker Hub](https://www.youtube.com/watch?v=_LNOg8kU4CE)
* [YAML | In One Video](https://www.youtube.com/watch?v=cdLNKUoMc6c)
