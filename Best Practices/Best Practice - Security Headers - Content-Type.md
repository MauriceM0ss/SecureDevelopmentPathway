# Content-Type

## Wat is het?

Deze header instrueert de browser hoe deze moet omgaan met de content van je pagina's. Door dit zo in te stellen dat de browser weet om wat voor content het gaat en welke tekenset wordt gebruikt , wordt voorkomen dat XSS aanvallen eenvoudig uitgevoerd kunnen worden.

## Best Practice

In responses, zorgt een 'Content-Type' header ervoor dat de client de actuele content type krijgt van de teruggegeven content. Het kan zijn dat deze header genegeerd wordt als de browser MIME sniffing doet; hiervoor zou je ook de 'X-Content-Type-Options' header op 'nosniff' moeten zetten (Dit is beschreven in hoofdstuk v14.4.4).

*Let op*: onderstaand is een voorbeeld.

```text
Content-Type: text/html; charset=utf-8
Content-Type: multipart/form-data; boundary=something
```

### Directives

* media-type: de MIME-Type van de resource of de data
* charset: Character encoding standard (voorkeur = UTF-8)
* boundary: Voor entiteiten die uit meerdere delen bestaan, is de boundary directive vereist. De directive bestaat uit 1 tot 70 tekens uit een reeks tekens (en eindigt niet met witruimte). Het wordt gebruikt om de grenzen van de verschillende delen van het bericht in te kapselen. Vaak wordt de header boundary voorafgegaan door twee dashes en aan de laatste boundary twee streepjes aan het einde.

### MIME-Types

* Application
* Audio
* Example
* Font
* Image
* Model
* Text
* Video

## Testen

Via een terminal verstuur het volgende commando:

```bash
curl -s -D- https://vws-example.nl | grep -i Content-Type
```

De verwachte response is bijvoorbeeld: `content-type: text/html; charset=UTF-8`

## FAQ

### Vraagje?

Op dit moment zijn er nog geen vragen over dit onderwerp.

## Sources

* <https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Type>
* <https://developer.mozilla.org/en-US/docs/Glossary/MIME_type>
* <https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types>
* <https://www.iana.org/assignments/media-types/media-types.xhtml>
