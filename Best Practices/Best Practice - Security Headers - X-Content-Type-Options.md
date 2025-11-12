# Guide - X-Content-Type-Options

## Wat is het?

De HTTP response header '**X-Content-Type-Options**' vertelt de browser dat de aangegeven MIME types in de Content-Type headers correct zijn en niet aangepast moeten worden. Deze header voorkomt MIME type sniffing, waarbij de browser zelf probeert te achterhalen wat voor soort bestand het is.

## Best Practice

```html
X-Content-Type-Options: nosniff
```

## Testen

1. Via een terminal verstuur het volgende commando:

    ```bash
    curl -s -D- https://vws-example.nl | grep -i content-type
    ```

2. De verwachte response is:

    ```bash
    X-Content-Type-Options: nosniff
    ```

## FAQ

Geen opmerkingen voor deze header.

## Sources

<https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Content-Type-Options>
