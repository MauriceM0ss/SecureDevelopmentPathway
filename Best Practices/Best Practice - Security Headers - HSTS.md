# Strict-Transport-Security (HSTS)

## Wat is het?

De HTTP Strict-Transport-Security response header (vaak afgekort als HSTS) informeert browsers dat de website alleen toegankelijk is via HTTPS. Alle toekomstige pogingen om de website via HTTP te bezoeken, worden automatisch naar HTTPS omgeleid.

Dit helpt om man-in-the-middle-aanvallen (MitM-aanvallen) te voorkomen, waarbij kwaadwillenden het onversleuteld verkeer tussen een gebruiker en een website kunnen onderscheppen en manipuleren.

## Best Practice

```html
Strict-Transport-Security: max-age=31536000; includeSubDomains
```

- **max-age=31536000** specificeert dat browsers de instructie om de website alleen via HTTPS te bezoeken gedurende een jaar (31.536.000 seconden = 1 jaar) in hun cache moeten opslaan.
- **includeSubDomains** zorgt ervoor dat de HSTS-instructie ook van toepassing is op alle subdomeinen van de website.

## Testen

Via een terminal verstuur het volgende commando:

```bash
curl -s -D- https://pgb-exampe.nl | grep -i strict
```

De verwachte response is: `Strict-Transport-Security: max-age=31536000`

## FAQ

### Wat als ik de max-age van de HSTS header wil inkorten?

Het is toegestaan de `max-age` aan te passen, hanteer hier wel een minimum van 1 jaar (31536000). Indien er een specifieke reden is om het korter te maken dan een jaar, overleg met security. De meest valide reden om de `max-age` korter te maken is om te testen op een test-omgeving of de configuratie goed is.

### Online zie ik ook `preload`, wat is dit?

`preload` biedt extra veiligheid omdat het automatisch wordt meegenomen door browsers, waardoor dit lastiger te manipuleren is door aanvallers. Het advies is om gebruik te maken van preloading, enkel is dit geen wettelijke verplichting.

Voor meer informatie zie: <https://hstspreload.org/>

### Wat zijn de belangrijke opties voor deze header?

- **max-age** bepaalt hoelang de browser de HSTS-instructie moet onthouden.
- **includeSubDomains** breidt de HSTS-beveiliging uit naar alle subdomeinen.
- **preload** voegt de website toe aan de HSTS Preload List van Google.

## Sources

- <https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Strict-Transport-Security>
- <https://owasp.org/www-project-secure-headers/>
