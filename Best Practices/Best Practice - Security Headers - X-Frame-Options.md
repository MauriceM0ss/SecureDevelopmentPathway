# X-Frame-Options

## Optional

> [!CAUTION]
> De Content-Security-Policy (CSP) HTTP-header bevat een "frame-ancestors" directive, waardoor deze header voor ondersteunende browsers overbodig wordt.

## Wat is het?

De '**X-Frame-Options**' HTTP-responseheader kan worden gebruikt om aan te geven of een browser een pagina mag weergeven in een ```<frame>, <iframe>, <embed> of <object>```. Websites kunnen dit gebruiken om clickjacking-aanvallen te voorkomen door ervoor te zorgen dat hun content niet wordt ingebed in andere websites.

## Best Practice

X-Frame-Options: DENY

Met bovenstaande HTTP-header word voorkomen dat de content van de website via een frame op een andere website kan worden weergegeven.

## Testen

1. Via een terminal verstuur het volgende commando:

    ```bash
    curl -s -D- https://vws-example.nl | grep -i X-Frame
    ```

2. De verwachte response is:

    ```bash
    X-Frame-Options DENY
    ```

## FAQ

### Wat als de website ontworpen is om embedded te worden?

Op Stack Exchange kun je hier een interessante discussie over vinden, <https://security.stackexchange.com/questions/266520/csp-and-x-frame-options-for-site-that-is-designed-to-be-embedded>. In dit geval is het advies om gebruik van de CSP header frame-ancestor attribuut gebruik te maken en deze zo restrictief mogelijk af te stellen.

### Wat zijn de belangrijke opties voor deze header?

* DENY: Dit is de meest restrictieve optie en verbiedt het inladen van de content in frames van andere websites.
* ALLOW-FROM uri: Staat het inladen van de content toe in frames van alle websites die overeenkomen met de opgegeven uri.
* SAMEORIGIN: Staat het inladen van de content toe in frames van dezelfde oorsprong (hetzelfde domein en poortnummer) als de website met de header.

## Sources

* <https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options>
