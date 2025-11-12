# JSON Schema Validation

## Wat is het?

JSON Schema Validation zorgt ervoor dat alle JSON-invoer die door een applicatie wordt ontvangen, wordt gevalideerd tegen een vooraf (door ons) gedefinieerd schema. Dit schema definieert de structuur, vereiste velden, datatypes en eventuele beperkingen van de JSON-gegevens.

### Waarom is het belangrijk?

* Het voorkomt ongeldige gegevens (alleen de goed gevormde & verwachte gegevens worden geaccepteerd)
* Beschermt tegen injectie aanvallen
* Verminderd het risico op security problemen door ervoor te zorgen dat de gegevensstructuur en inhoud aan onze verwachte normen voldoen

## Best Practice

### Hoe te implementeren

1) Definieer een JSON Schema
    * Maak een JSON-schema dat de structuur, vereiste velden, datatypes en beperkingen van de JSON-gegevens specificeert.

      Voorbeeld JSON Schema:

      ```text
      {
        "$schema": "http://json-schema.org/draft-07/schema#",
        "type": "object",
        "properties": {
          "name": {
            "type": "string"
          },
          "age": {
            "type": "integer",
            "minimum": 0
          }
        },
        "required": ["naam", "leeftijd"]
      }
      ```

2) Gebruik een JSON Schema Validatiebibliotheek
    * Gebruik een JSON-schema validatiebibliotheek in je programmeertaal om de JSON-invoer te valideren tegen het schema.

      Voorbeeld in JavaScript (met behulp van [ajv](https://ajv.js.org/)):

      ```text
      const Ajv = require('ajv');
      const ajv = new Ajv();

      const schema = {
        type: 'object',
        properties: {
          naam: { type: 'string' },
          leeftijd: { type: 'integer', minimum: 0 }
        },
        required: ['naam', 'leeftijd']
      };

      const validate = ajv.compile(schema);

      const data = {
        name: 'Example',
        age: 30
      };

      const valid = validate(data);
      if (!valid) console.log(validate.errors);
      else console.log('JSON is valid');
      ```

3) Valideer Invoer in de Applicatie
    * Integreer de validatiestap in de gegevensverwerkingsstroom van je applicatie, zodat elke inkomende JSON-invoer wordt gevalideerd voordat verdere verwerking plaatsvindt.

4) Handel validatiefouten correct af
    * Implementeer error handling om te reageren op ongeldige JSON-invoer. Stuur bijvoorbeeld een foutmelding terug naar de gebruiker en log de fout voor verdere analyse.

## Testen

* Handmatig testen
  * Review de codebase in je IDE:
    * Zoek naar codefragmenten die JSON-gegevens verwerken
    * Controleer of er een verwijzing is naar een JSON-schema en of er validatie plaatsvindt tegen dit schema

* Automatisch testen
  * Er zijn test-tools beschikbaar om JSON-validatie te kunnen controleren, zoals [JSON Schema Lint](https://jsonschemalint.com/)

## FAQ

Geen vragen op het moment

## Sources

[JSON Schema Lint](https://jsonschemalint.com/)

[AJV](https://ajv.js.org/)

[OWASP Cheat Sheet Series](https://cheatsheetseries.owasp.org/cheatsheets/HTML5_Security_Cheat_Sheet.html#authentication-and-inputoutput-validation)
