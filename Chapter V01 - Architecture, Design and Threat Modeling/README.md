# Chapter V01 - Architecture, Design and Threat Modeling

Het eerste hoofdstuk van de SDP, "V01 - Architecture, Design and Threat Modeling", draait om de basis leggen voor een veilige applicatie. Het gaat erom vanaf het begin goed na te denken over hoe je applicatie in elkaar zit, welke mogelijke bedreigingen er zijn, en hoe je deze kunt voorkomen.

Denk hierbij aan:

* **Duidelijke Structuur**: Zorg voor een overzichtelijke en doordachte architectuur van je applicatie.
* **Dreigingsanalyse**: Bedenk welke soorten aanvallen je zou kunnen tegenkomen en hoe je je daartegen kunt beschermen.
* **Veilig Ontwerpen**: Bouw je applicatie vanaf het begin met veiligheid in gedachten, zodat je later niet allerlei reparaties hoeft uit te voeren.

Dit hoofdstuk helpt je om een solide en veilige basis voor je applicatie te leggen, zodat je problemen voor kunt zijn in plaats van ze later te moeten oplossen.

> [!NOTE]
> Chapter V01 - Architecture, Design and Threat Modeling heeft alleen L2 en L3 items, *geen* baseline items. Voorlopig slaan we dit hoofdstuk dan ook over.

## V1.1 Secure Software Development Lifecycle

### Baseline

Dit item heeft geen Level 1 items.

### Enhanced

| ID    | Description |
| ----- | ----------- |
| 1.1.1 | Verify the use of a secure software development lifecycle that addresses security in all stages of development.  |
| 1.1.2 | Verify the use of threat modeling for every design change or sprint planning to identify threats, plan for countermeasures, facilitate appropriate risk responses, and guide security testing. |
| 1.1.3 | Verify that all user stories and features contain functional security constraints, such as "As a user, I should be able to view and edit my profile. I should not be able to view or edit anyone else's profile" |
| 1.1.4 | Verify documentation and justification of all the application's trust boundaries, components, and significant data flows. |
| 1.1.5 | Verify definition and security analysis of the application's high-level architecture and all connected remote services. |
| 1.1.6 | Verify implementation of centralized, simple (economy of design), vetted, secure, and reusable security controls to avoid duplicate, missing, ineffective, or insecure controls.  |
| 1.1.7 | Verify availability of a secure coding checklist, security requirements, guideline, or policy to all developers and testers. |

### Advanced

Dit item heeft geen Level 3 items.

## V1.2 Authentication Architecture

### Baseline

Dit item heeft geen Level 1 items.

### Enhanced

| ID    | Description |
| ----- | ----------- |
| 1.2.1 | Verify the use of unique or special low-privilege operating system accounts for all application components, services, and servers. |
| 1.2.2 | Verify that communications between application components, including APIs, middleware and data layers, are authenticated. Components should have the least necessary privileges needed. |
| 1.2.3 | Verify that the application uses a single vetted authentication mechanism that is known to be secure, can be extended to include strong authentication, and has sufficient logging and monitoring to detect account abuse or breaches. |
| 1.2.4 | Verify that all authentication pathways and identity management APIs implement consistent authentication security control strength, such that there are no weaker alternatives per the risk of the application. |

### Advanced

Dit item heeft geen Level 3 items.

## V1.3 Session Management Architecture

### Baseline

Dit item heeft geen Level 1 items.

### Enhanced

Dit item heeft geen Level 2 items.

### Advanced

Dit item heeft geen Level 3 items.

## V1.4 Access Control Architecture

### Baseline

Dit item heeft geen Level 1 items.

### Enhanced

| ID    | Description |
| ----- | ----------- |
| 1.4.1 | Verify that trusted enforcement points, such as access control gateways, servers, and serverless functions, enforce access controls. Never enforce access controls on the client. |
| 1.4.4 | Verify the application uses a single and well-vetted access control mechanism for accessing protected data and resources. All requests must pass through this single mechanism to avoid copy and paste or insecure alternative paths. |
| 1.4.5 | Verify that attribute or feature-based access control is used whereby the code checks the user's authorization for a feature/data item rather than just their role. Permissions should still be allocated using roles. |

### Advanced

Dit item heeft geen Level 3 items.

## V1.5 Input and Output Architecture

### Baseline

Dit item heeft geen Level 1 items.

### Enhanced

| ID    | Description |
| ----- | ----------- |
| 1.5.1 | Verify that input and output requirements clearly define how to handle and process data based on type, content, and applicable laws, regulations, and other policy compliance. |
| 1.5.2 | Verify that serialization is not used when communicating with untrusted clients. If this is not possible, ensure that adequate integrity controls (and possibly encryption if sensitive data is sent) are enforced to prevent deserialization attacks including object injection. |
| 1.5.3 | Verify that input validation is enforced on a trusted service layer. |
| 1.5.4 | Verify that output encoding occurs close to or by the interpreter for which it is intended. |

### Advanced

Dit item heeft geen Level 3 items.

## V1.6 Cryptographic Architecture

### Baseline

Dit item heeft geen Level 1 items.

### Enhanced

| ID    | Description |
| ----- | ----------- |
| 1.6.1 | Verify that there is an explicit policy for management of cryptographic keys and that a cryptographic key lifecycle follows a key management standard such as NIST SP 800-57. |
| 1.6.2 | Verify that consumers of cryptographic services protect key material and other secrets by using key vaults or API based alternatives. |
| 1.6.3 | Verify that all keys and passwords are replaceable and are part of a well-defined process to re-encrypt sensitive data. |
| 1.6.4 | Verify that the architecture treats client-side secrets--such as symmetric keys, passwords, or API tokens--as insecure and never uses them to protect or access sensitive data. |

### Advanced

Dit item heeft geen Level 3 items.

## V1.7 Errors, Logging and Auditing Architecture

### Baseline

Dit item heeft geen Level 1 items.

### Enhanced

| ID    | Description |
| ----- | ----------- |
| 1.7.1 | Verify that a common logging format and approach is used across the system. |
| 1.7.2 | Verify that logs are securely transmitted to a preferably remote system for analysis, detection, alerting, and escalation. |

### Advanced

Dit item heeft geen Level 3 items.

## V1.8 Data Protection and Privacy Architecture

### Baseline

Dit item heeft geen Level 1 items.

### Enhanced

| ID    | Description |
| ----- | ----------- |
| 1.8.1 | Verify that all sensitive data is identified and classified into protection levels. |
| 1.8.2 | Verify that all protection levels have an associated set of protection requirements, such as encryption requirements, integrity requirements, retention, privacy and other confidentiality requirements, and that these are applied in the architecture. |

### Advanced

Dit item heeft geen Level 3 items.

## V1.9 Communications Architecture

### Baseline

Dit item heeft geen Level 1 items.

### Enhanced

| ID    | Description |
| ----- | ----------- |
| 1.9.1 | Verify the application encrypts communications between components, particularly when these components are in different containers, systems, sites, or cloud providers. |
| 1.9.2 | Verify that application components verify the authenticity of each side in a communication link to prevent person-in-the-middle attacks. For example, application components should validate TLS certificates and chains. |

### Advanced

Dit item heeft geen Level 3 items.

## V1.10 Malicious Software Architecture

### Baseline

Dit item heeft geen Level 1 items.

### Enhanced

| ID     | Description |
| ------ | ----------- |
| 1.10.1 | Verify that a source code control system is in use, with procedures to ensure that check-ins are accompanied by issues or change tickets. The source code control system should have access control and identifiable users to allow traceability of any changes. |

### Advanced

Dit item heeft geen Level 3 items.

## V1.11 Business Logic Architecture

### Baseline

Dit item heeft geen Level 1 items.

### Enhanced

| ID     | Description |
| ------ | ----------- |
| 1.11.1 | Verify the definition and documentation of all application components in terms of the business or security functions they provide. |
| 1.11.2 | Verify that all high-value business logic flows, including authentication, session management and access control, do not share unsynchronized state. |

### Advanced

| ID     | Description |
| ------ | ----------- |
| 1.11.3 | Verify that all high-value business logic flows, including authentication, session management and access control are thread safe and resistant to time-of-check and time-of-use race conditions. |

## V1.12 Secure File Upload Architecture

### Baseline

Dit item heeft geen Level 1 items.

### Enhanced

| ID     | Description |
| ------ | ----------- |
| 1.12.2 | Verify that user-uploaded files - if required to be displayed or downloaded from the application - are served by either octet stream downloads, or from an unrelated domain, such as a cloud file storage bucket. Implement a suitable Content Security Policy (CSP) to reduce the risk from XSS vectors or other attacks from the uploaded file. |

### Advanced

Dit item heeft geen Level 3 items.

## V1.13 API Architecture

### Baseline

Dit item heeft geen Level 1 items.

### Enhanced

Dit item heeft geen Level 2 items.

### Advanced

Dit item heeft geen Level 3 items.

## V1.14 Configuration Architecture

### Baseline

Dit item heeft geen Level 1 items.

### Enhanced

| ID     | Description |
| ------ | ----------- |
| 1.14.1 | Verify the segregation of components of differing trust levels through well-defined security controls, firewall rules, API gateways, reverse proxies, cloud-based security groups, or similar mechanisms. |
| 1.14.2 | Verify that binary signatures, trusted connections, and verified endpoints are used to deploy binaries to remote devices. |
| 1.14.3 | Verify that the build pipeline warns of out-of-date or insecure components and takes appropriate actions. |
| 1.14.4 | Verify that the build pipeline contains a build step to automatically build and verify the secure deployment of the application, particularly if the application infrastructure is software defined, such as cloud environment build scripts. |
| 1.14.5 | Verify that application deployments adequately sandbox, containerize and/or isolate at the network level to delay and deter attackers from attacking other applications, especially when they are performing sensitive or dangerous actions such as deserialization. |
| 1.14.6 | Verify the application does not use unsupported, insecure, or deprecated client-side technologies such as NSAPI plugins, Flash, Shockwave, ActiveX, Silverlight, NACL, or client-side Java applets. |

### Advanced

Dit item heeft geen Level 3 items.
