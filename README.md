# Secure Development Pathway (SDP)

## Wat is de Secure Development Pathway (SDP)?

De Secure Development Pathway (SDP) is een framework gebaseerd op de OWASP ASVS 4.0.3 (Application Security Verification Standard), de ASVS heeft als doel een kader te bieden voor het verbeteren van de beveiliging van webapplicaties door een gedetailleerde checklist van beveiligingseisen aan te bieden. Het is als een beveiligingshandboek dat developers en product owners helpt te weten waar ze naar moeten streven om hun applicaties veilig te houden.

De website van de OWASP ASVS is hier te vinden: [OWASP Application Security Verification Standard | OWASP Foundation](https://owasp.org/www-project-application-security-verification-standard/)

Security liaisons, DevSecOps Engineers of Security Officers binnen DevOps die fungeren als de brug tussen beveiligingsexperts, Operations en ontwikkelteams, kunnen hier een grote rol in spelen. Ze kunnen product owners en developers begeleiden over hoe ze beveiligingsmaatregelen vanaf het begin en gedurende het hele ontwikkelproces kunnen integreren. Dit maakt het gemakkelijker om te voldoen aan beveiligingsnormen zoals de BIO (Baseline Informatiebeveiliging Overheid).

Door security liaisons erbij te betrekken, kunnen teams:

1. **De Checklist Begrijpen**: Een duidelijk beeld krijgen van welke beveiligingsmaatregelen nodig zijn door de OWASP ASVS-richtlijnen te volgen.
2. **Vroege Integratie**: Beveiligingspraktijken vanaf het begin in de ontwikkelingscyclus inbedden, in plaats van ze aan het einde toe te voegen.
3. **Voortdurende Ondersteuning**: Voortdurend advies en ondersteuning krijgen om ervoor te zorgen dat alle beveiligingsaspecten gedurende het hele project worden gedekt.
4. **Eenvoudige Naleving**: Het proces van het voldoen aan verplichte beveiligingseisen vereenvoudigen door beveiliging een natuurlijk onderdeel van de ontwikkelworkflow te maken.

De Secure Development Pathway biedt het wat en waarom, terwijl security liaisons helpen met het hoe, waardoor het relatief eenvoudig wordt om veilige applicaties te bouwen en te voldoen aan beveiligingsnormen; om samen te werken aan Secure Development.

## (OWASP) Application Security Verification Levels

De Application Security Verification Standard definieert drie beveiligingsverificatieniveaus, waarbij elk niveau in diepte toeneemt.
De standaard definities van deze levels zijn volgens OWASP de volgende:

* ASVS Level 1 is for low assurance levels, and is completely penetration testable
* ASVS Level 2 is for applications that contain sensitive data, which requires protection and is the recommended level for most apps
* ASVS Level 3 is for the most critical applications - applications that perform high value transactions, contain sensitive medical data, or any application that requires the highest level of trust

## Secure Development Maturity Levels

Omdat wij deze terminologie te onduidelijk vinden en het niet het juiste beeld schept, willen wij een eigen interpretatie van deze niveaus aanhouden:

* ASVS Level 1 is onze "**Baseline Security Compliance**"
* ASVS Level 2 is onze "**Enhanced Security Compliance**"
* ASVS Level 3 is onze "**Advanced Security Compliance**"

We beginnen dus bij niveau 1 om een baseline van veiligheid te behalen waar dit niet al het geval is. Samen gaan we er voor zorgen dat we op dit niveau komen, en steeds verder gaan waar mogelijk.
Op deze pagina's en de checklists zullen deze termen dus gebruikt worden zodat het duidelijk is aan welk niveau we werken, en wat het doel is van dat niveau.

## Wanneer is de SDP van toepassing

De SDP kan op elk moment gevolgd worden, het is niet afhankelijk van een specifiek moment. Uiteraard door de natuur van de SDP (Shift Left) is het meest opportune moment net na de ontwerpfase, op het moment dat de ontwikkelfase begint. Het is immers eenvoudiger security tijdens de ontwikkelfase mee te nemen in plaats van een bestaande applicatie aan te passen aan de richtlijnen.

Ook kan er gekozen worden voor het uitvoeren van specifieke onderdelen van de SDP, zoals alleen een hoofdstuk "Access Control" of "Authentication". Er zijn veel manieren hoe de SDP uitgevoerd kan worden. Echter is het goed om in de basis de gehele SDP waar van toepassing toe te passen, zodat je project meetbaar werkt aan compliancy en de algemene veiligheid van je applicatie. Ook is het verstandig om de SDP continue te blijven gebruiken, beide als richtlijn en als handboek.

Denk ook na over het opnieuw bezoeken van de SDP bij grote wijzigingen in je applicatie, nieuwe sprints en updates. Het is zelfs mogelijk om tijdens de ontwerpfase de SDP te gebruiken als bron van informatie bij specifieke vraagstukken, zoals wanneer je nadenkt over hoe de authenticatie in te richten of wat voor cryptografie je wil gaan gebruiken.

## Hoe werk je met de SDP

Zoals gezegd kan je op meerdere momenten de SDP gebruiken:

* Tijdens de ontwerpfase;
* Tijdens de ontwikkelfase;
* Tijdens de QA fase;
* Tussendoor om specifieke onderdelen van je applicatie te controleren;
* Tijdens of na grote wijzigingen.

Over het algemeen werk je samen met je Security Liaison om door de SDP te werken. Dit kan opgepakt worden tijdens je project hoe je het zelf wilt. Denk aan workshops, tijdens refinements, incidenteel en onderwerp specifiek. Wat wel belangrijk is, is dat als je de SDP gaat volgen je dit wel documenteert. Hierbij kan het voorkomen dat je niet kunt voldoen aan een requirement, indien dit het geval is, is het belangrijk dat dit ook goed is gedocumenteerd in de specifieke requirement.

## Waarom de SDP en niet gewoon de OWASP ASVS?

De OWASP ASVS is een zeer goede bron als het gaat om web applicatie security. Het is een goede bron als suggesties voor security richtlijnen. Echter om de implementatie van de ASVS te vereenvoudigen hebben wij er voor gekozen om deze richtlijnen over te nemen, en aan te vullen met het 'waarom' en vooral het 'hoe'. We willen een eenvoudig te gebruiken handboek creëren waarmee je kan zien *welke* richtlijnen van toepassing kunnen zijn voor jou, *waarom* deze van belang zijn en natuurlijk *hoe* je die zou kunnen implementeren in jouw project.

Waar we ook mee bezig zijn is een koppeling bouwen tussen de SDP en de backlog die je gebruikt binnen je project, zodat je eenvoudig een richtlijn uit de SDP kan pakken en deze opvoeren als backlog item. Hiermee krijg je een overzicht in de (Security) stappen die je maakt, en creëer je een audit-trail voor compliance.

## Wat als de OWASP ASVS geupdate wordt?

OWASP update de ASVS niet heel vaak, de major versies worden ongeveer elke drie tot vier jaar geupdate. Er kunnen nieuwe richtlijnen bijkomen, en bepaalde vervallen omdat ze bijvoorbeeld verouderd zijn of simpelweg niet meer van toepassing zijn. Wij houden de wijzigingen van de OWASP ASVS bij, en controleren deze tegen de SDP. Waar nodig worden aanpassingen gedaan op basis van de nieuwe ASVS versies.

> [!NOTE]
> Op dit moment (November 2025) is de OWASP ASVS 5.0 al een tijd uit, en deze SDP wordt op basis van deze nieuwe update aangepast.
