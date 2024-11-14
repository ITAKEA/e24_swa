# Dokumentation af endpoints
Dokumentation er jeres endpoints er altafgørende for om andre kan bruge jeres kode. 
Vi kigger på 3 metoder til at dokumentere endpoints på:

* Readmefiler
    * Dette er ofte indgangen for en bruger af jeres microservices, og her skal der være en fyldestgørende beskrivelse af hvordan man opsætter og konfigurere jeres service. Readmefilen skal være skrevet til den bruger der skal bruge den, hvilket gør det vigtigt at den rette information er med og at det der ikke er vigtigt undlades.   
* Et /api/ endpoint med en liste over alle endpoints i jeres microservice.
    * Et eksempel på dette kan være: [https://api.github.com/](https://api.github.com/)
* Et /docs/ endpoint med openAPI (swagger) documentation.
    * Et eksempel på dette kan være: [https://petstore.swagger.io/](https://petstore.swagger.io/)

Vi kommer til at bruge ChatGpt fuldt ud til denne diciplin. Altså at skrive dokumentation vha den. Men i skal selvfølgelig vide hvad der foregår, kunne forklare det hele, og kunne sætte det op på den rigtige måde. Hvilket ikke er nogen triviel opgave. 

## Læringsmål
* Kunne skrive dokumentation til Microservice endpoints i form af 
    * Readmefiler
    * json api dokumentation
    * Swagger (OpenApi) dokumentation

## Forberedelse
**Brug alt i alt en halv times tid på denne forberedelse.**

* Vi kommer til at arbejde med [Flasgger](https://github.com/flasgger/flasgger/blob/master/README.md) modulet. I skal derfor skimme denne readmefil igennem.
Slut målet for de næste 2 undervisningsgange er at i kan dokumenterer jeres endpoints. Det er gjort i vores demo app herunder. Skim derfor disse links igennem inden vi mødes.    

* [Swagger til Api Gateway](https://githubapigateway-h4hrfpe0fgg5dphq.northeurope-01.azurewebsites.net/docs)
* [Swagger til Github Microservice](https://github-microservice-gygahdabdwbjbbhj.northeurope-01.azurewebsites.net/docs)
* [JSON docs i root til Api Gateway](https://githubapigateway-h4hrfpe0fgg5dphq.northeurope-01.azurewebsites.net/)
* [JSON docs i root til Github Microservice](https://github-microservice-gygahdabdwbjbbhj.northeurope-01.azurewebsites.net/)
* [Readme til Api Gateway](https://github.com/ITAKEA/api_gateway/blob/master/README.md)
* [Readme til Github Microservice](https://github.com/ITAKEA/github_microservice/blob/master/README.md)

I skal desuden kigge på kildekode til dette repository

* [Api Gateway - Github](https://github.com/ITAKEA/api_gateway)

Der er lavet en ny mappe **[swagger](https://github.com/ITAKEA/api_gateway/tree/master/swagger)** og nogle ændringer i app.py filen. Skim også det igennem.


## Dagen i dag

**Demo**     
* [SwaggerUI](https://swagger.io/tools/swagger-ui/)
* [OpenAI - openapi.yaml](https://github.com/openai/openai-openapi/blob/master/openapi.yaml)



## Materialer
* [Swagger til Api Gateway](https://githubapigateway-h4hrfpe0fgg5dphq.northeurope-01.azurewebsites.net/docs)
* [Swagger til Github Microservice](https://github-microservice-gygahdabdwbjbbhj.northeurope-01.azurewebsites.net/docs)
* [JSON docs i root til Api Gateway](https://githubapigateway-h4hrfpe0fgg5dphq.northeurope-01.azurewebsites.net/)
* [JSON docs i root til Github Microservice](https://github-microservice-gygahdabdwbjbbhj.northeurope-01.azurewebsites.net/)

* [Readme til Api Gateway](https://github.com/ITAKEA/api_gateway/blob/master/README.md)
* [Readme til Github Microservice](https://github.com/ITAKEA/github_microservice/blob/master/README.md)

* [Flasgger dokumentation](https://github.com/flasgger/flasgger/blob/master/README.md)
