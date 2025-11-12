# Cross-Origin Resource Sharing (CORS)

## Wat is het?

Deze header zorgt ervoor dat scripts die via de browser worden uitgevoerd, kunnen communiceren met bronnen van een andere oorsprong (domain, schema of port).

## Best Practice

> [!NOTE]
> Als het framework of webserver die wordt gebruikt CORS-functionaliteit ondersteunt, maak daar dan altijd gebruik van in plaats van het handmatig te implementeren.

## Publiek zonder authenticatie

### Context

De endpoints zijn openbaar toegankelijk. e.g. Iedereen kan er rechtstreeks met een browser bij, zonder te hoeven inloggen of van een specifieke website te komen.

### Configuratie

```text
Access-Control-Allow-Origin: *
Access-Control-Max-Age: 3600
Access-Control-Allow-Credentials: false
```

## Restrictief zonder authenticatie

### Context

De endpoints zijn alleen toegankelijk voor browsers van een beperkte groep websites (origins) en vereisen geen inloggegevens.

### Configuratie

```text
Access-Control-Allow-Origin: [Value_Taken_From_The_List_Of_Allowed_Origins]
Access-Control-Max-Age: 10
Access-Control-Allow-Credentials: false
```

## Restrictief met authenticatie

### Context

De applicatie is ontworpen voor het gebruikt vanuit een browser en staat alleen toegang toe van geautoriseerde websites/applicaties met correcte inloggegevens.

### Configuratie

```text
Access-Control-Allow-Origin: [Value_Taken_From_The_List_Of_Allowed_Origins]
Access-Control-Max-Age: 10
Access-Control-Allow-Credentials: true
```

## Testen

In onderzoek

## FAQ

### Hoe zit het in het geval "Publiek met authenticatie"

*Context: Iedereen kan met een webbrowser bij de endpoints en inloggegevens zijn vereist.*

Dit is niet toegestaan. Ook wordt dit actief geblokkeerd door een browser met bijvoorbeeld de melding:

```text
"The value of the 'Access-Control-Allow-Origin' header in the response must not be the wildcard '*' when the request's credentials mode is 'include'."
```

Maak gebruik van "Restrictief met authenticatie". Indien dit niet kan bespreken met security om te zoeken naar een oplossing. Ga niet de origin kopiëren in de "Access-Control-Allow-Origin" header. Dit kan worden misbruikt, zie [Portswigger](https://portswigger.net/web-security/cors#server-generated-acao-header-from-client-specified-origin-header) voor een voorbeeld.

## Sources

* [Developer.Mozzila.org - CORS Header](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS)
* [OWASP Prevent CORS Misconfigurations](https://owasp.org/www-project-secure-headers/index.html#prevent-cors-misconfiguration-issues)
