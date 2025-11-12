# Content-Security-Policy (CSP)

> [!NOTE]
> Waar andere headers minimale impact hebben kan de CSP header de werking van je applicatie zeer beperken. Neem dan ook de tijd met het toevoegen van deze header en zorg dat na aanpassing functionaliteit goed wordt getest.

## Wat is het?

Content Security Policy (CSP) is een extra beveiligingslaag die helpt bij het detecteren en afweren van bepaalde soorten aanvallen, waaronder Cross-Site Scripting (XSS) en data-injectie-aanvallen. Deze aanvallen worden gebruikt voor alles van gegevensdiefstal tot defacing en malware verspreiding.

## Best Practice

```text
Content-Security-Policy: default-src 'self'; form-action 'self'; object-src 'none'; frame-ancestors 'none'; upgrade-insecure-requests;
```

> [!NOTE]
> We wijken af van de OWASP Best Practice met block-all-mixed-content, dit omdat deze deprecated is.

Deze header legt de volgende restricties op aan de browser:

- Bronbeperkingen: Externe bronnen voor scripts, stylesheets, afbeeldingen en plugins worden geblokkeerd. Enkel resources van de eigen website ('self') zijn toegestaan. Dit minimaliseert het risico op kwaadaardige code of content.
- Formulierbeveiliging: Formulierverzending wordt beperkt tot de eigen website, waardoor gevoelige data minder snel in verkeerde handen valt.
- Pluginblokkering: Plugins zoals Flash en Silverlight worden geblokkeerd vanwege hun kwetsbaarheid voor beveiligingslekken.
- Framebeperkingen: De website kan niet worden geladen in frames of iframes van andere websites, waardoor manipulatie of misbruik moeilijker wordt.
- HTTPS-afdwinging: Alle verbindingen met de website worden geforceerd via HTTPS, de veilige variant van het HTTP-protocol. Dit beschermt tegen man-in-the-middle aanvallen.

## Testen

Gebruik de CSP evaluator van Google: <https://csp-evaluator.withgoogle.com/>

## FAQ

### Wat als ik toestemming wil geven aan een externe bron?

Gebruik in plaats daarvan "Nonce" of "Hashes" om scripts van externe bronnen toe te staan.
Ga eerst in overleg met je team of er echt geen andere mogelijkheid is. Er zijn de afgelopen jaren namelijk meerdere aanvallen geweest via 'Supply chain attacks' waarbij scripts of data uit externe bronnen onveilig bleek te zijn.

Indien er echt geen andere optie is, vermijd dan het gebruik van toestemmingslijsten (allow-listing), waarmee geaccepteerde websites hardcoded staan beschreven. Gebruik in plaats daarvan "Nonce" of "Hashes" om scripts van externe bronnen toe te staan.

- Nonce verwijst naar een uniek willekeurig getal dat wordt toegewezen aan een `<script>`-tag om vertrouwen vast te stellen.
- Hash is een wiskundige bewerking die invoergegevens omzet in een gecomprimeerde waarde die altijd dezelfde uitkomst heeft indien de input hetzelfde is. Door een hash te gebruiken (zoals SHA-256), kun je een inline `<script>` tag als vertrouwd markeren.

Voor een meer gedetailleerde uitleg kun je deze handige guide raadplegen: <http://web.archive.org/web/20221119151940/https://web.dev/i18n/en/strict-csp/>.

### Wat als ik eval wil gebruiken?

Kort antwoord: Niet gebruiken!

Iets langer antwoord: Het wordt sterk afgeraden om de functie "eval" te gebruiken in je code. Overweeg in plaats daarvan de code te herschrijven. Mozilla biedt een uitgebreide lijst met redenen om de risico's en nadelen van het gebruik van "eval" te benadrukken,zie <https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/eval#never_use_eval>!

### Wat als ik inline code wil gebruiken?

Als de richtlijnen default-src of script-src zijn gedefinieerd in de CSP header, wordt JavaScript-code die inline in de HTML-bron wordt geplaatst standaard uitgeschakeld.

Bijvoorbeeld de volgende inline code:

```html
<script>var foo = "314"</script>
```

Om de code weer bruikbaar te maken, kan deze worden verplaatst naar een aparte JavaScript-bestand. De HTML-code wordt dan als volgt gewijzigd:

```html
<script src="app.js"></script>
```

In dit geval zou het app.js bestand de code var foo = "314"  bevatten.

CSP beperkt ook inline event handlers. De volgende constructie zou bijvoorbeeld worden geblokkeerd onder CSP:

```html
<button id="button1" onclick="doSomething()">Klik op mij</button>
```

Om deze beperking te omzeilen, kun je deze vervangen door addEventListener:

```html
<script>document.getElementById("button1").addEventListener('click', doSomething);</script>
```

Door deze wijziging wordt de event handler programmatisch toegevoegd in plaats van met inline code, waardoor wordt voldaan aan de CSP beperkingen.

### Wat als ik unsafe-inline wil gebruiken voor de `style-src`

Bij het inladen van externe scripts kan het voorkomen dat hierbij ook inline styles ingeladen worden. Als de CSP header dit blokkeert, beperkt dit de werking van de applicaties. Om dit te verhelpen geld altijd als eerst het advies om de scripts zelf te hosten. Hierdoor draai je alles in de 'self' context van de pagina waardoor het probleem zichzelf oplost. Echter zijn er natuurlijk situaties waar dit niet kan, in dat geval kan er voor gekozen worden om de unsafe-inline te gebruiken.

Bij het toestaan van inline style-src ontstaat het risico dat wanneer een aanvaller style tags kan injecteren in de pagina de volgende acties kan uitvoeren:

- Injection met inladen afbeeldingen
- Keylogger met inladen afbeeldingen
- Keylogger met inladen fonts

Hierbij wordt er wel gebruik gemaakt van het aanroepen van afbeeldingen en lettertypes. Dit wordt geblokkeerd door het gebruik van font-src  en img-src.

Concluderend komt het dus neer op:

Probeer indien mogelijk `unsafe-inline`  te voorkomen, in het geval dat dit echt niet lukt is `unsafe-inline` toegestaan, maar niet aanbevolen, overleg dit met security. Hierbij geldt wel dat `font-src` en `img-src` niet voorkomen in de allow list voor de zelfde website as de `style-src`.

### Hoe zit het met de `base-uri` tag?

Zoals te zien is in de specificaties van deze tag: <https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy/base-uri> wordt de base-uri niet automatisch overgenomen van de default-src.

De security risico's die mogelijk kunnen ontstaan zijn:

- HTML injection via `<base>` tag
- XSS injection via `<base>` tag

Beide gevallen zijn corner cases, waarbij de eerste ook wordt afgevangen door de form-action 'self', toch met de gedachte "baat het niet dan schaadt het niet" adviseren we om de header in te stellen.

tldr:

- Gebruik base-uri 'none';  als de `<base>` tag niet wordt gebruikt.
- Gebruik base-uri 'self'; als de `<base>` tag wel wordt gebruikt
- Uitzondering bespreken met je security liaison.

### Wat als ik een API aan het bouwen ben?

Als je zeker weet dat de API niet als HTML wordt weergegeven, is het aan te raden de volgende Content-Security-Policy header te gebruiken:

```html
Content-Security-Policy: frame-ancestors 'none'
```

Deze richtlijn geeft aan dat de API niet in een frame of iframe mag worden weergegeven.

Als je echter niet zeker weet hoe de API wordt gerenderd is het aanbevolen om de volgende header te gebruiken:

```html
Content-Security-Policy: default-src 'none'
```

Deze richtlijn stelt het standaardbeleid in om te voorkomen dat inhoud wordt geladen, wat een veiligere aanpak biedt.

### Wat als ik een andere policy wil gebruiken?

|                  | **Beschrijving<br>**                                                                                                                                                                                                                                 | **Aanbeveling**      |
| ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------- |
| 'none'           | Deze optie geeft aan dat er geen bronnen mogen worden geladen, inclusief die van dezelfde oorsprong.                                                                                                                                                 | Aanbevolen           |
| 'self'           | Deze optie maakt het mogelijk om bronnen te laden van dezelfde oorsprong als de huidige pagina. Bijvoorbeeld, als de huidige pagina wordt gehost op rijksoverheid.nl, dan staat 'self' toe dat bronnen van rijksoverheid.nl worden geladen.                        | Aanbevolen           |
| 'strict-dynamic' | Deze optie wordt gebruikt in combinatie met een nonce of hash om dynamische scripts te laden zonder ze te hoeven specificeren in de CSP header. Dit kan handig zijn voor sites die frameworks of plugins gebruiken die dynamische scripts genereren. | Niet aanbevolen      |
| 'unsafe-inline'  | Met deze optie kunnen inline scripts en stijlen worden uitgevoerd.                                                                                                                                                                                   | Niet aanbevolen      |
| 'unsafe-eval'    | Met deze optie wordt de functie eval() van JavaScript toegestaan.                                                                                                                                                                                    | Streng afgeraden     |

### Wat zijn de belangrijke opties voor deze header?

- **default-src:** Standaard waarde voor alle resources.
  - none: Blokkeert alle resources tenzij expliciet toegestaan.
  - 'self': Staat alleen resources toe van hetzelfde domein als de website.
  - Andere domeinen of bronnen kunnen worden toegevoegd (overleg met je security liaison).
- **script-src:** Waarde die bepaald waar scripts vandaan mogen komen.
  - 'self': Staat alleen scripts toe van hetzelfde domein als de website.
  - 'strict-dynamic': Staat dynamisch geladen scripts toe, mits geladen door een vertrouwd script met nonce of hash.
  - 'unsafe-inline': Staat inline scripts toe (onveilig, bespreek met security).
  - Specifieke domeinen kunnen worden toegevoegd voor externe scripts.
- **connect-src:** Toegestane waarde voor verbindingen (bijv. API's).
  - 'self': Staat verbindingen alleen toe naar hetzelfde domein.
  - Specifieke domeinen kunnen worden toegevoegd voor externe API's.
- **img-src:** Waarde die bepaald waar afbeeldingen vandaan mogen komen.
  - 'self': Staat alleen afbeeldingen toe van hetzelfde domein.
  - Specifieke domeinen kunnen worden toegevoegd voor externe afbeeldingen.
- **style-src:** Waarde die bepaald waar stylesheets vandaan mogen komen.
  - 'self': Staat alleen stylesheets toe van hetzelfde domein.
  - Specifieke domeinen kunnen worden toegevoegd voor externe stylesheets.
- **frame-ancestors:** Van waar de website in een frame mag worden geladen.
  - 'none': Staat niet toe de website als frame te laden.
  - 'self': Staat weergave alleen toe in frames van hetzelfde domein.
  - Specifieke domeinen kunnen worden toegevoegd voor toegestane framing.
- **form-action:** Waar formulieren naartoe mogen worden verzonden.
  - 'self': Staat formulierverzending alleen toe naar hetzelfde domein.
  - Specifieke domeinen kunnen worden toegevoegd voor toegestane formulieracties.
- **object-src:** Bronnen voor plugins (bijv. Flash, Silverlight, PDF's).
  - 'none': Blokkeert alle plugins.
  - Specifieke domeinen kunnen worden toegevoegd voor toegestane plugins (met voorzichtigheid).
- upgrade-insecure-requests: Forceert HTTPS voor alle resource requests.
- block-all-mixed-content: Blokkeert alle HTTP-content op HTTPS-pagina's (deprecated).

## Sources

- <https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP>
- <https://security.stackexchange.com/questions/190813/what-attacks-does-content-security-policy-base-uri-protect-against>
- <https://scotthelme.co.uk/can-you-get-pwned-with-css/>
- <https://owasp.org/www-project-secure-headers/>
