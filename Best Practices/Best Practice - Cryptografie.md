# Cryptografie

> [!NOTE]
> Gebasseerd op [ICT-beveiligingsrichtlijnen voor Transport Layer Security (TLS) v2.1](https://www.ncsc.nl/documenten/publicaties/2021/januari/19/ict-beveiligingsrichtlijnen-voor-transport-layer-security-2.1)

## TLS voor publiek beschikbare websites

- TLS 1.2 met de volgende Ciphers:
  - (Aanbevolen) TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384
  - (Aanbevolen) TLS_ECDHE_RSA_WITH_CHACHA20_POLY1305_SHA256
  - (Aanbevolen) TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256
  - (Comptabiliteit) TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384
  - (Comptabiliteit) TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256
  - (Comptabiliteit) TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA
  - (Comptabiliteit) TLS_ECDHE_RSA_WITH_AES_218_CBC_SHA
  - TLS 1.3 (behalve TLS_AES_128_CCM_8_SHA256)
- OCSP stapling staat aan
- Zet insecure renegotiation for TLS 1.2 uit
- 0-RTT staat uit
- Andere protocols of cipher suites zijn niet toegestaan (voorkomen van downgrade aanval)
- HSTS dient geconfigureerd te zijn.

## TLS voor interne systemen

- Wanneer mogelijk, gebruik TLS 1.3. Indien dit nit het geval is, gebruik TLS 1.2 met deze ciphers:
  - TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384
  - TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256
  - TLS_DHE_RSA_WITH_AES_256_GCM_SHA384
  - TLS_DHE_RSA_WITH_AES_128_GCM_SHA256
  - TLS_ECDHE_RSA_WITH_CHACHA20_POLY1305_SHA256
- OCSP stapling staat aan
- Zet insecure renegotiation for TLS 1.2 uit
- 0-RTT staat uit
- Zet TLS 1.3 alleen uit als deze problemen oplevert.
- Andere protocols of cipher suites zijn niet toegestaan (voorkomen van downgrade aanval)
- HSTS dient geconfigureerd te zijn.

## SSH Keys voor gebruik Git

- Gebruik ED25519 met een minimum van 100 KDF (Key derivation function) rounds.
  - (Alternatief) in het geval van backwards compatibility kan er voor worden gekozen voor RSA i.c.m. een keylength van 4096 bits.
  