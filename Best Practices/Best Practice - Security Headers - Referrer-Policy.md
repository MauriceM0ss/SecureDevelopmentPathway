# Referrer-Policy

## Wat is het?

Deze header is een beveiligingsmaatregel die websites kunnen gebruiken om te voorkomen dat hun browser informatie over de herkomst van een gebruiker naar andere websites verzendt. Dit voorkomt dat er (privacy) gevoelige data wordt gelekt naar externe partijen over bijv. welke website en/of webpagina's  de gebruiker zojuist heeft bezocht.

## Best Practice

```html
Referrer-Policy: no-referrer
```

Deze header zorgt er voor dat er geen referrer informatie wordt verstuurd indien een externe link wordt geopend.

## Testen

Via een terminal verstuur het volgende commando:

```bash
curl -s -D- https://exampe.nl | grep -i referrer
```

De verwachte response is: `Referrer-Policy: no-referrer`

## FAQ

### Waarom heb je het over de referer  header, zou het niet de referrer  header moeten zijn?

Dit is inderdaad een typefout die iemand ooit heeft gemaakt waardoor het onderdeel is geworden van de officiële specificaties.

Deze typefout is niet over genomen voor de security policy.

### Wat zijn de belangrijke opties voor deze header?

- **no-referrer** De Referer header wordt weggelaten: verzonden verzoeken bevatten geen referrer informatie. (Aanbevolen. Beste keuze als er geen referrer nodig is.)
- **strict-origin-when-cross-origin** Verstuur de oorsprong, het pad en de querystring bij verzoeken binnen je website (same-origin). Verstuur voor verzoeken naar andere websites (cross-origin) alleen de oorsprong (indien) het beveiligingsniveau van het protocol hetzelfde blijft (HTTPS → HTTPS). Verstuur de Referer-header niet naar minder veilige bestemmingen (HTTPS → HTTP). (Default en aanbevolen voor meeste use cases.)
- **no-referrer-when-downgrade** De Referer header wordt niet verzonden wanneer je van een HTTPS website naar een HTTP website navigeert. De referer-informatie wordt echter wel verzonden bij het navigeren binnen dezelfde website of van een HTTP(S)-website naar een andere HTTP(S)-website. (Niet aanbevolen. Toegestaan bij gebruik zoals beschreven in: "Wat als strict-origin-when-cross-origin (of strikter) niet aan je use cases voldoet?".)
- **origin** Verstuur in de Referer-header alleen de oorsprong. Bijvoorbeeld, een document op <https://example.com/pagina.html> zal enkel de referrer <https://example.com/> meesturen. (Gebruik strict-origin)
- **origin-when-cross-origin** Bij verzoeken binnen je website (same-origin) en met hetzelfde beveiligingsniveau (HTTP naar HTTP, HTTPS naar HTTPS), stuur je de oorsprong, het pad en de querystring mee. Voor verzoeken naar andere websites (cross-origin) en verzoeken naar minder beveiligde bestemmingen (HTTPS naar HTTP), stuur je alleen de oorsprong mee in de Referer-header. (Gebruik strict-origin-when-cross-origin.)
- **same-origin** Verstuur de oorsprong, het pad en de querystring voor verzoeken binnen je website (same-origin). Verstuur de Referer-header niet voor verzoeken naar andere websites (cross-origin). (Toegestaan)
- **strict-origin** Verstuur alleen de oorsprong in de Referer-header wanneer het beveiligingsniveau van het protocol hetzelfde blijft (HTTPS naar HTTPS). Verstuur de Referer-header niet naar websites met een lager beveiligingsniveau (HTTPS naar HTTP). (Toegestaan)
- **unsafe-url** Verstuur de oorsprong, het pad en de querystring in de Referer-header bij elk verzoek, ongeacht het beveiligingsniveau. (Niet aanbevolen)

### Wat als strict-origin-when-cross-origin (of strikter) niet aan je use case voldoet?

In dit geval kun je een progressieve aanpak hanteren: stel een beveiligingsgericht beleid in, zoals strict-origin-when-cross-origin voor je website. Als dat nodig is, kun je een iets minder strikt beleid gebruiken voor specifieke verzoeken of HTML-elementen.

Bijvoorbeeld:

```html
<head>
  <!-- document-level policy: strict-origin-when-cross-origin -->
  <meta name="referrer" content="strict-origin-when-cross-origin" />
  <head>
    <body>
      <!-- policy on this <a> element: no-referrer-when-downgrade -->
      <a src="…" href="…" referrerpolicy="no-referrer-when-downgrade"></a>
      <body></body>
    </body>
  </head>
</head>
```

## Sources

- <https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Referrer-Policy>
- <https://owasp.org/www-project-secure-headers/>
