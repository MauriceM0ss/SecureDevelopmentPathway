# HTTP Cookies

## Wat is het?

Deze header instrueert de browser hoe om te gaan met cookies en welke cookies mee te sturen bij nieuwe verzoeken richting de server.

## Best Practice

```text
Set-Cookie: __Host-SID=<session token>; path=/; Secure; HttpOnly; SameSite=Strict.
```

Bovenstaande header zorgt ervoor dat de cookie binnen de context van de website blijft en alleen op een veilige manier wordt verstuurd.

- **__Host- prefix:** Cookies die beginnen met __Host- moeten worden ingesteld met de Secure  flag, moeten afkomstig zijn van een veilige pagina (HTTPS), mogen niet naar subdomeinen worden gestuurd en het pad moet / zijn.
- **path=/:** zorg dat de cookie geldig is voor alle pagina's op de website
- **Secure:** De cookie wordt alleen verzonden via HTTPS-verbindingen.
- **HttpOnly:** De cookie kan niet worden gewijzigd door JavaScript (Minder impact XXS aanval).
- **SameSite=Strict:** De cookie wordt alleen verzonden naar de website die de cookie heeft verstuurd.

## Testen

Via een terminal verstuur het volgende commando:

```bash
curl -s -D- https://pgb-exampe.nl | grep -i set-cookie
```

De verwachte response is:
`Set-Cookie: __Host-SID=f1d4368d-e5be-4d5e-85e1-d813f4f6afdb; path=/; Secure; HttpOnly; SameSite=Strict.`

## FAQ

### Is het toegestaan `Lax` te gebruiken voor de `SameSite` attribuut?

In principe wel, dit is ook de standaard waarde voor `SameSite`. Overleg dit wel even met security omdat `Strict` de voorkeur heeft. Als je `Lax` gebruikt is het nog steeds op te nemen in je `Set-Cookie` header.

### Wat zijn de belangrijke opties voor deze header?

- **Naam en waarde (vereist):** Geeft de naam en waarde van de cookie.
- **Expires (optioneel):** Specificeert de datum en tijd waarop de cookie verloopt. Als deze niet is ingesteld, verloopt de cookie aan het einde van de browsersessie.
- **Max-Age (optioneel):** Specificeert de duur van de cookie in seconden vanaf het moment dat deze wordt ingesteld. Dit is een alternatief voor Expires.
- **Domain (optioneel):** Bepaalt het domein waarop de cookie geldig is. Als deze niet is ingesteld, is de cookie alleen geldig voor het huidige domein.
- **Path (optioneel):** Bepaalt het pad waarop de cookie geldig is. Als deze niet is ingesteld, is de cookie geldig voor alle paden op het domein.
- **Secure (optioneel):** Geeft aan of de cookie alleen via HTTPS mag worden verzonden.
- **HttpOnly (optioneel):** Geeft aan dat de cookie niet via JavaScript mag worden bekeken of gewijzigd.
- **SameSite (optioneel):** Bepaalt wanneer de cookie mag worden verzonden met cross-site HTTP-verzoeken. Mogelijke waarden zijn:
  - **Strict:** De cookie wordt alleen verzonden met verzoeken van hetzelfde domein (first-party).
  - **Lax:** De cookie wordt verzonden met verzoeken van hetzelfde domein (first-party) en met verzoeken naar subdomeinen van hetzelfde domein.
  - **None:** De cookie wordt verzonden met alle verzoeken, ongeacht het domein.

## Sources

- <https://owasp.org/www-project-web-security-testing-guide/latest/4-Web_Application_Security_Testing/06-Session_Management_Testing/02-Testing_for_Cookies_Attributes>
- <https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Set-Cookie>
