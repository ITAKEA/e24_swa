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
    
>    Authorization: Bearer <din_adgangstoken>
>    Content-Type: application/json

* Tilføj Body: I afsnittet 'Body' skal du vælge 'raw' og 'JSON (application/json)'. Derefter skal du indtaste følgende JSON-objekt:

```
    {    "path": "",    "recursive": false,    "include_media_info": false,    "include_deleted": false,    "include_has_explicit_shared_members": false,    "include_mounted_folders": true,    "include_non_downloadable_files": true} 
```

Hvis alt er indstillet korrekt, vil du modtage en respons fra Dropbox API, der indeholder en liste over filer og mapper i den angivne mappe. og en statuskode 200 (OK)

Du skal i det følgende bruge Dropbox Api Dokumentationen.

Den finder du her: https://www.dropbox.com/developers/documentation/http/documentation

 

Øvelse 2: Opret en mappe

I Dropbox API-dokumentationen, find det endpoint, der giver dig mulighed for at oprette en ny mappe.
Brug Postman til at sende den passende forespørgsel for at oprette en ny mappe med navnet "TestMappe".
Tjek din Dropbox for at se din nye mappe.
Dokumentation: I din README-fil, angiv det anvendte endpoint (url) og HTTP-verb du har brugt. Beskriv desuden hvad du evt. har skrevet i body i dit request og det svar du har fået tilbage fra API'en. Beskriv desuden kort om dette flow er i overenstemmelse med princippet om "uniform interface" i REST principperne, og hvis ikke hvad der så kunne gøres bedre.
Øvelse 3: Hent mappe detaljer

Find det endpoint i dokumentationen, der giver detaljer om en specifik mappe.
Vælg en mappe fra din Dropbox, noter dens sti, og brug Postman til at hente dens detaljer.
Undersøg detaljerne i den returnerede JSON.
Dokumentation: I din README, noter endpointet, HTTP-verbet, request body (vis nogen) og det response du har fået tilbage inkl. status kode. Beskriv desuden kort om dette flow er i overenstemmelse med princippet om "uniform interface" i REST principperne, og hvis ikke hvad der så kunne gøres bedre.
Øvelse 4: Upload en fil

Find det endpoint i dokumentationen, der giver dig mulighed for at uploade en fil.
Brug Postman til at sende den passende forespørgsel for at uploade en fil til "TestMappe".
Tjek din "TestMappe" på Dropbox for at sikre, at filen er blevet uploadet.
Dokumentation: I din README, beskriv endpointet, HTTP-verbet, og hvordan du uploadede filen.
Øvelse 5: Slet en fil

I dokumentationen skal du finde det endpoint, der giver dig mulighed for at slette en fil.
Vælg en fil fra din "TestMappe", noter dens sti, og brug Postman til at slette den.
Tjek din "TestMappe" på Dropbox for at sikre, at filen er blevet slettet.
Dokumentation: I din README, beskriv endpointet, HTTP-verbet, og stien på den fil, du slettede. Beskriv desuden kort om dette flow er i overenstemmelse med princippet om "uniform interface" i REST principperne, og hvis ikke hvad der så kunne gøres bedre.
Øvelse 7: Søg efter filer

Naviger til Dropbox API-dokumentationen og find endpointet for at søge efter filer.
Brug Postman til at sende en forespørgsel for at søge efter filer, der indeholder ordet "test". (hvis du ikke har nogle filer kan du oprette et par stykker først)
Undersøg de returnerede filer, og se om søgningen gik godt (er der “test” i filen)
Dokumentation: I din README, noter endpointet, HTTP-verbet, request body, response body og status kode. Beskriv desuden kort om dette flow er i overenstemmelse med princippet om "uniform interface" i REST principperne, og hvis ikke hvad der så kunne gøres bedre.
Øvelse 8: Flyt en fil

I dokumentationen skal du finde det endpoint, der giver dig mulighed for at flytte en fil.
Vælg en fil, noter dens nuværende sti og den nye sti, og brug Postman til at flytte den.
Tjek din Dropbox for at se, om filen er blevet flyttet til den nye placering.
Dokumentation: Dokumenter endpointet, HTTP-verbet, request body, response body og status kode. Beskriv desuden kort om dette flow er i overenstemmelse med princippet om "uniform interface" i REST principperne, og hvis ikke hvad der så kunne gøres bedre.
Øvelse 9: Kopier en fil

Find det endpoint i dokumentationen, der giver dig mulighed for at kopiere en fil.
Brug filen fra den forrige øvelse og brug Postman til at kopiere filen til en ny placering.
Tjek din Dropbox for at sikre, at en kopi af filen er blevet oprettet på den nye placering.
Dokumentation: I din README, beskriv endpointet, HTTP-verbet, request body, response body og status kode. Beskriv desuden kort om dette flow er i overenstemmelse med princippet om "uniform interface" i REST principperne, og hvis ikke hvad der så kunne gøres bedre.
Øvelse 10: Brug JavaScript's Fetch med Dropbox API

Opret en simpel HTML-side med en knap.
Når knappen klikkes, skal du bruge JavaScript's fetch til at sende en GET-forespørgsel for at hente alle filer og mapper i din "TestMappe".
Vis filerne og mapperne på siden.
Dokumentation: I dit repository inkluder den JavaScript-kode og html, du har skrevet.
HUSK: du må ikke ligge din “Access Token” på github, så slet den inden du pusher din kode.
Øvelse 11: Er https://api.dropboxapi.com/2/ Restfull or not?

Beskriv til sidst kort hvad du tænker om API´et i forhold til REST “constraints”. Hvordan er det i feks. i forhold til “Uniform Interface” og hvad gør det for din oplevelse af at bruge API´et?
