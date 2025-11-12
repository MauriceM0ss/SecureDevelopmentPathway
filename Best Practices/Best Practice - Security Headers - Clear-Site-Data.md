# Clear-Site-Data

## Wat is het?

Deze header Clear-Site-Data wist browser gegevens (cookies, opslag, cache) die aan de bezoekende website gekoppeld zijn. Hiermee is het mogelijk meer controle te krijgen over de gegevens die door een browser worden opgeslagen.

## Best Practice

```text
Clear-Site-Data: "cache","cookies","storage"
```

Deze header verwijderd de cache, cookies en storage die in de browser zijn opgeslagen.

## Testen

Via een terminal verstuur het volgende commando:

```bash
curl -s -D- https://exampe.nl | grep -i clear
```

De verwachte response is: `Clear-Site-Data: "cache","cookies","storage"`

## FAQ

### Wat zijn de belangrijke opties voor deze header?

- **cache:** Wis alle lokaal gecachte gegevens in de browser.
- **cookies:** Wis alle cookies voor de website in de browser.
- **storage:** Wis alle lokale en sessieopslag voor het domein.
- **executionContexts:** Herlaad het browsertabblad voor het domein.
- **clientHints:** Informatie over de client verkregen via de Accept-CH (niet benodigd wanneer "cache", "cookies" of "*" gebruikt wordt)
- ***:** Wis alle gegevens uit de bovenstaande opslaggebieden voor het domein.

### In welke situatie gebruik ik deze header?

Bijvoorbeeld voor een logout actie, waar je de volgende header meestuurt, deze zal de browser sessie en informatie verwijderen en vervolgens de pagina verversen:

```text
Clear-Site-Data: "cache", "cookies", "storage", "executionContexts"
```

## Sources

- <https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Clear-Site-Data>
- <https://owasp.org/www-project-secure-headers/>
