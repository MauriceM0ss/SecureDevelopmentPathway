# Cache-Control

## Wat is het?

Deze header instrueert de browser hoe deze moet omgaan met caching voor zowel requests als responses. Door dit zo in te stellen dat er geen caching plaatsvindt, wordt voorkomen dat gevoelige informatie via de cache kan worden vrijgegeven.

## Best Practice

```text
Cache-Control: no-store, max-age=0
```

Deze header verbiedt webcaches om de response op te slaan en forceert browsers om de content altijd opnieuw van de server te halen.

## Testen

Verstuur het volgende commando via een terminal:

```bash
curl -s -D- https://vws-example.nl | grep -i cache
```

De verwachte response is: `Cache-Control: no-store, max-age=0`

## FAQ

### Online zie ik ook pragma: no-cache, wat is dit?

Pragma is optioneel en wordt gebruikt voor "backwards compatibility" maar is in essentie deprecated.

### Wat als ik caching nodig heb?

Indien caching nodig is voor de werking van de applicatie is het aanbevolen om de `must-revalidate` optie te gebruiken.

### Wat zijn de belangrijke opties voor deze header?

- **no-store** verbiedt webcaches om de response op te slaan.
- **max-age** bepaalt hoelang een response mag worden gecached voordat deze verouderd is.
- **must-revalidate** dwingt webcaches om de response te valideren met de server voordat deze wordt gebruikt.

## Sources

- <https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Cache-Control>
- <https://owasp.org/www-project-secure-headers/>
