# Dropbox api exercise 

## Øvelse 1: Opsætning

* Opret en konto på Dropbox.
* Gå derefter til https://www.dropbox.com/developers/apps og opret en App
* Generer en “Access Token” og skriv den ned.
* Åbn Postman
* Klik på '+' ikonet for at oprette en ny anmodning.
* Indstil anmodningsmetoden til POST
* Indtast https://api.dropboxapi.com/2/files/list_folder
* Tilføj Headers: I afsnittet 'Headers' skal du tilføje følgende nøgle-værdi-par:

```    
    Authorization: Bearer <din_adgangstoken>
    Content-Type: application/json
```

* Tilføj Body: I afsnittet 'Body' skal du vælge 'raw' og 'JSON (application/json)'. Derefter skal du indtaste følgende JSON-objekt:

```
    {    
        "path": "",    
        "recursive": false,    
        "include_media_info": false,    
        "include_deleted": false,    
        "include_has_explicit_shared_members": false,    
        "include_mounted_folders": true,    
        "include_non_downloadable_files": true
    } 
```

Hvis alt er indstillet korrekt, vil du modtage en respons fra Dropbox API, der indeholder en liste over filer og mapper i den angivne mappe. og en statuskode 200 (OK)

Du skal i det følgende bruge Dropbox Api Dokumentationen.

Den finder du her: [https://www.dropbox.com/developers/documentation/http/documentation](https://www.dropbox.com/developers/documentation/http/documentation)

Lav nu et Python program der gemmer, sletter, redigerer i filer på din Dropbox konto.
