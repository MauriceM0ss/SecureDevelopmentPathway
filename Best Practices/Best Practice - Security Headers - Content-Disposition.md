# Content-Disposition

## Wat is het?

De '**Content-Disposition**' header zorgt er voor dat de browser de inhoud van de pagina correct kan weergeven, bijvoorbeeld een inline document in je pagina, of voor het afdwingen van een download. Denk aan bijvoorbeeld een PDF document waarvan je wil dat de gebruiker deze in de pagina zelf moet kunnen zien (Content-Disposition: inline) of dat het een ZIP bestand betreft die gedownload moet worden (Content-Disposition: attachment; filename="voorbeeld.zip").

## Best Practice

Hieronder volgen een aantal best practices die je kan volgen omtrent de 'Content-Disposition' header.

* Zorg dat de header 'Content-Type' aan aanwezig is die aangeeft om welk type document het gaat en welke encoding je gebruikt
* Kies de juiste disposition voor wat je zoekt: 'Inline' voor het inline weergeven van een document, 'Attachment' voor het forceren van een download
* Denk ook aan de CSP Header om te beveiliging van welke bronnen bestanden geladen mogen worden (bijvoorbeeld de directive *default-src 'self'*)

### Voorbeelden

Een 'Save As' dialoog triggeren:

```text
200 OK
Content-Type: text/html; charset=utf-8
Content-Disposition: attachment; filename="cool.html"
Content-Length: 21

<HTML>Save me!</HTML>
```

Een multipart formulier:

```text
POST /test.html HTTP/1.1
Host: example.org
Content-Type: multipart/form-data;boundary="boundary"

--boundary
Content-Disposition: form-data; name="field1"

value1
--boundary
Content-Disposition: form-data; name="field2"; filename="example.txt"

value2
--boundary--
```

## Testen

Open een terminal en voer het volgende commando uit:

```bash
curl -s -D- https://vws-example.nl | grep -i Content-Disposition
```

## FAQ

### Vraagje?

Op dit moment zijn er nog geen vragen over dit onderwerp.

## Sources

<https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Disposition>
<https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types>
