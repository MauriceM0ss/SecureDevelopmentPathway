# Wachtwoorden

Deze informatie is gebaseerd op de 2025 updates en best practices volgens de NIST: [NIST Password Guidelines: 2025 Updates and Best Practice](https://www.strongdm.com/blog/nist-password-guidelines).

De recentste updates in de NIST-wachtwoordrichtlijnen (waaronder de updates van 2025 en de SP 800-63-4 conceptversie van september 2024) verschuiven de focus van complexiteit naar bruikbaarheid. De richtlijnen vormen de geaccepteerde kaders voor veilige wachtwoordpraktijken voor vrijwel alle sectoren.

## Overzicht van NIST Wachtwoord Best Practices

### Prioriteiten en Fundamentele Vereisten

- Focus op lengte boven complexiteit: De richtlijnen stellen de lengte van het wachtwoord boven de complexiteit.
- Controle op gecompromitteerde gegevens: Screening van wachtwoorden tegen databases met bekende gecompromitteerde inloggegevens is verplicht. Organisaties moeten rigoureuze wachtwoordblokklijsten (blocklists) implementeren met grotere databases om veelvoorkomende wachtwoordkeuzes te weren.
- Ondersteuning van wachtwoordloze methoden: Organisaties dienen ondersteuning te bieden voor wachtwoordloze authenticatie en passkeys, aangezien deze methoden worden aangemoedigd.

### Wachtwoordconstructie (Lengte en Karakters)

- Minimale Lengte: Een minimum van 8 karakters is vereist voor standaardaccounts.
- Lengte voor bevoorrechte accounts: Voor bevoorrechte accounts (privileged accounts) is een minimum van 15 karakters vereist.
- Maximale Lengte: NIST pleit voor wachtwoorden tot 64 karakters voor maximale beveiliging.
- Karakterondersteuning: Acceptatie van alle afdrukbare ASCII-tekens, spaties en Unicode-symbolen (inclusief emoji's en internationale tekens) is verplicht. Dit stelt gebruikers in staat om gedenkwaardige wachtwoordzinnen te creëren.

### Afgeschafte en Nieuwe Beleidsregels

Wat is afgeschaft (Niet langer verplicht):

- Verplichte complexiteitsregels: Vereisten voor hoofdletters, cijfers en symbolen zijn afgeschaft.
- Willekeurige complexiteitsbeleiden zijn niet meer nodig.
- Geforceerde periodieke resets: Verplichte wachtwoordresets om de 90 dagen (of andere vaste periodes) zijn geëlimineerd, tenzij er een vermoeden van compromis is.
Nieuwe Resets en Rotatie:
- Wachtwoordwijzigingen moeten worden geactiveerd door specifieke beveiligingsincidenten (event-based) in plaats van vaste kalenderperioden.
- Onmiddellijke resets moeten worden afgedwongen bij het detecteren van verdachte inlogpogingen, ongebruikelijke accountactiviteit of mogelijke datalekken.

### Wachtwoordbeheer en Opslag

- Opslagvereisten: Veilige wachtwoordopslag via geavanceerde encryptietechnieken is verplicht.
- Hashing en Salting: Organisaties moeten salting en hashing implementeren met behulp van memory-hard functions (zoals PBKDF2, bcrypt, en Argon2), die worden beschouwd als voorkeursoplossingen. Wachtwoorden moeten worden opgeslagen in een vorm die bestand is tegen offline aanvallen.
- Rate Limiting: Het wordt aanbevolen om rate limiting te implementeren op authenticatiepogingen en verplichte afkoelperiodes af te dwingen na mislukte herstelpogingen.
- Wachtwoordherstel: Kennisgebaseerde authenticatievragen (zoals "naam van eerste huisdier") worden niet langer als veilig beschouwd. Moderne herstelprotocollen moeten gebruikmaken van veilige kanalen die gescheiden zijn van de primaire authenticatiemethode (multi-channel verificatie).
- Wachtwoordmanagers: De richtlijnen ondersteunen het gebruik van wachtwoordmanagers als essentieel hulpmiddel. Deze moeten zero-knowledge encryption implementeren en copy-paste functionaliteit in wachtwoordvelden ondersteunen om aan de NIST-vereisten te voldoen.

### Richtlijnen voor Service Accounts

- Lengte van Service Accounts: Wachtwoorden voor service accounts moeten ten minste 32 karakters beslaan.
- Generatie en Rotatie: Deze wachtwoorden moeten cryptografisch worden gegenereerd via veilige willekeurige nummergeneratoren. Organisaties moeten geautomatiseerde rotatieschema's en strikte toegangsbeperkingen implementeren.
