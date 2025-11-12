# XSD Schema Validation

## Wat is het?

XSD Schema validatie is een methode om ervoor te zorgen dat XML-documenten die door je applicatie worden verwerkt, voldoen aan een gedefinieerde structuur en datatypes. Dit helpt om de veiligheid, integriteit en betrouwbaarheid van de gegevensverwerking te waarborgen.

XSD (XML Schema Definition) Schema Validatie is het proces waarbij een XML-document wordt gecontroleerd op conformiteit met een vooraf gedefinieerd schema. Dit schema definieert de structuur, elementen en attributen die een XML-document moet bevatten, evenals de datatypes en beperkingen van deze elementen.

### Waarom is het belangrijk?

* Zorgt voor correcte structuur: Verzekert dat het XML-document correct is opgebouwd en voldoet aan de verwachte structuur
* Voorkomt XML-injectie: Beschermt tegen aanvallen waarbij schadelijke XML-inhoud wordt geïnjecteerd
* Verbetert dataintegriteit: Zorgt ervoor dat de gegevens binnen de verwachte limieten vallen, wat fouten en onvoorspelbaar gedrag voorkomt
* Beschermt tegen DoS-aanvallen: Vermijdt slecht gevormde XML-documenten die oneindige lussen of excessief geheugenverbruik kunnen veroorzaken tijdens het parsen

## Best Practice

### Hoe te implementeren

1) Definieer een XSD-schema

* Maak een XML Schema Definition (XSD) bestand dat de structuur, elementen, attributen en datatypes van je XML-documenten specificeert. Voorbeeld:

    ```html
    <?xml version="1.0" encoding="UTF-8"?>
    <xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">
      <xs:element name="persoon">
        <xs:complexType>
          <xs:sequence>
            <xs:element name="naam" type="xs:string"/>
            <xs:element name="leeftijd" type="xs:int"/>
          </xs:sequence>
        </xs:complexType>
      </xs:element>
    </xs:schema>
    ```

1) Valideer XML-documenten tegen het XSD-schema

* Gebruik een XML-parser in je programlanguage of platform om het XML-document te valideren tegen het XSD-schema. Voorbeeld in Node.js:

    ```javascript
    const fs = require('fs');
    const libxmljs = require('libxmljs');

    const xsd = fs.readFileSync('schema.xsd', 'utf8');
    const xml = fs.readFileSync('example.xml', 'utf8');

    const xsdDoc = libxmljs.parseXml(xsd);
    const xmlDoc = libxmljs.parseXml(xml);

    const isValid = xmlDoc.validate(xsdDoc);
    console.log(isValid ? 'XML is valid' : 'XML is invalid');
    console.log(xmlDoc.validationErrors);
    ```

1) Integreer validatie in je applicatie

* Voeg de validatiestap toe aan je gegevensverwerkingsstroom, zodat elk inkomend XML-document wordt gevalideerd voordat verdere verwerking plaatsvindt.

1) Handel validatiefouten correct af

* Implementeer foutafhandeling om te reageren op invalid XML-documenten. Dit kan betekenen dat je de verwerking stopt en een foutmelding geeft aan de gebruiker of logt voor latere analyse.

## Testen

* Handmatig testen
  * Review de codebase:
    * Zoek naar codefragmenten die XML-gegevens verwerken
    * Controleer of er een verwijzing is naar een XSD-schema en of er validatie plaatsvindt tegen dit schema
  * Voer handmatige tests uit:
    * Probeer handmatig een goed gevormd XML-bestand en een slecht gevormd XML-bestand in te dienen via de webpagina
    * Check of het systeem het slecht gevormde XML-bestand afwijst en het goed gevormde bestand accepteert

* Automatisch testen
  * Er zijn test-tools beschikbaar om XML-validatie te kunnen controleren, zoals [Online XML Validator (XSD)](https://www.liquid-technologies.com/online-xsd-validator) of [XML Validation](https://www.xmlvalidation.com/)

## FAQ

Geen vragen op het moment

## Sources

[Techtarget XSD Schema Validation](https://www.techtarget.com/whatis/definition/XSD-XML-Schema-Definition#:~:text=XML%20Schema%20Definition%20or%20XSD,types%20the%20document%20can%20contain.)

[W3 Schools XSD Schema intro](https://www.w3schools.com/xml/schema_intro.asp)

[OWASP Cheat Sheet Series](https://cheatsheetseries.owasp.org/cheatsheets/Web_Service_Security_Cheat_Sheet.html#schema-validation)
