---
title:  "Barcelona's Resident Registry: A Case Where Governmental Procedures Can Be Completed via Multiple Digital Identities"
date:   2026-04-27 00:00:00 -0600
category: Identidades Digitales
image: assets/images/covers/tom-barrett-hvvRg72aXCw-unsplash.jpg
image-alt: Photo by <a href="https://unsplash.com/@wistomsin?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Tom Barrett</a> on <a href="https://unsplash.com/photos/silhouette-of-people-hvvRg72aXCw?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a>
tags: digitalid esignature
description: | 
  This real-life use case documents how different digital identities can co-exist in a government ecosystem and be applied to the same government procedure.
---

{% include components/panel.html type="warning" title="This is a post awaiting validation. I am actively looking for feedback from people that understand about digital signatures or the spanish legal instruments that allow them. If you want to provide feedback, write me at ali @ basicavisual.io" %}

# Barcelona's Resident Registry: A Case Where Governmental Procedures Can Be Completed via Multiple Digital Identities

## Context

In GovStack we tend to assume the Identity Building Block (ID BB) is implemented only once per country. However, governments may find themselves with more than one digital identity system in operation — sometimes several, at different levels of jurisdiction and with different technical architectures. Rather than prescribing unification as a necessary condition for a healthy digital identity environment, this real-life use case documents how different digital identities can co-exist in a government ecosystem and be applied to the same government procedure.

The case is the **Padró Municipal d'Habitants** (Municipal Register of Residents) in Barcelona, Spain — a procedure administered by the Ajuntament de Barcelona that citizens can complete online using at least four distinct digital identity systems, spanning national and regional (Catalan) levels of government.

**Digital identities covered:**
- Cl@ve (National Government, operated by AEAD)
- DNIe (National Government, issued by Dirección General de la Policía)
- idCAT Mòbil / idCAT Mòbil+ (Catalan Government, operated by AOC Consorci)
- Digital Certificate from FNMT-RCM (National Government, issued by the national mint)

---

## 1. The Padró Municipal: A Local Procedure with National Legal Force

### What It Is

The **Padró Municipal d'Habitants** — commonly called the *empadronament* in Catalan or *empadronamiento* in Spanish — is the official administrative register of all persons who habitually reside in a given municipality. In Barcelona, it is maintained by the **Ajuntament de Barcelona**. Registration is not optional: every person residing in Spain — whether a Spanish national, EU citizen, or non-EU foreign national, and regardless of immigration status — is legally obligated to register in the padrón of their municipality of habitual residence.

The **certificat d'empadronament** (certificate of registration) is issued by the municipality as proof that a person is registered. It is widely demanded by other administrations and institutions for purposes including: enrolling children in local schools, accessing the public health system (the SISCAT in Catalonia), applying for residence permits or nationality, accessing social services, and numerous other administrative and legal transactions. The document therefore starts at the municipal level but circulates throughout the national administrative system.

### How a Local Procedure Achieves National Validity

The padrón system achieves its national validity through a combination of legislation and real-time digital coordination between municipalities and the national statistical authority.

**Legal framework:**

- **Ley 7/1985, de 2 de abril, Reguladora de las Bases del Régimen Local (LBRL)** establishes the padrón as a mandatory municipal register (Article 15) and defines the data held (Article 16). Crucially, Article 17 gives the **Instituto Nacional de Estadística (INE)** the role of coordinating and unifying all municipal padrones at the national level, resolving duplicities and maintaining an authoritative national record. This single law transforms what would otherwise be a fragmented collection of local registers into a unified national infrastructure.[^1]

- **Ley 4/1996, de 10 de enero**, which modified the LBRL, introduced the modern *padrón continuo* — a permanently maintained, computer-based register that replaced the previous system of 5-year census renewals. This reform made the padrón a living database rather than a periodic snapshot, and established the current model of automatic coordination with the INE.[^2]

- **Real Decreto 1690/1986** (modified by **Real Decreto 2612/1996** and most recently by **Real Decreto 141/2024, de 6 de febrero**) provides the implementing regulations. Notably, Real Decreto 141/2024 updated the data transmission schedule to require real-time updates from municipalities to the INE, replacing the previous monthly batch-update model. This ensures the national record is always current.[^3]

- **Real Decreto 523/2015** eliminated the requirement to obtain certain certificates in person, opening the door to digital delivery of empadronamiento certificates.

**How coordination works in practice:**

Every municipal padrón in Spain is digitally connected to the INE's national database. When an Ajuntament registers or updates a resident, that change is now transmitted in real time to the INE. The INE deduplicates entries (ensuring a person cannot be simultaneously registered in two municipalities), publishes official population statistics, and serves as the authoritative national source. The certificate issued by the Ajuntament de Barcelona carries legal validity throughout Spain and the EU because it reflects data in this nationally coordinated system. The national, regional, and local administrations all accept it on the basis of this shared legal and technical infrastructure.

**Online access in Barcelona:**

Barcelona's Seu Electrònica ([https://seuelectronica.ajuntament.barcelona.cat](https://seuelectronica.ajuntament.barcelona.cat)) enables residents to complete the full padrón registration online — the *Alta al Padró Municipal d'Habitants* — as well as obtain digital certificates of existing registration. These certificates are issued with an electronic signature and a **Código Seguro de Verificación (CSV)**, a unique code that allows any third party to verify the document's authenticity online, making the digital certificate as legally valid as a paper original.[^4]

---

## 2. The Four Digital Identities: Why Four, and What Each Covers

### Why Are There Four?

The coexistence of four distinct digital identity systems is not the result of deliberate planning but of the layered constitutional, jurisdictional, and historical context of Spain:

1. **Constitutional asymmetry**: Spain is a state of autonomous communities. Catalonia has broad self-governance powers, including in e-government, leading the Generalitat de Catalunya to develop its own identity infrastructure rather than rely solely on the national state. The same pattern exists in other communities (País Vasco, Comunidad Valenciana, etc.).

2. **Historical sequencing**: The DNIe predates Cl@ve by nearly a decade. When Cl@ve was created (2014), it was explicitly designed as a *broker* to wrap and unify existing credentials — including the DNIe — rather than replace them. The FNMT certificate is older still, and was the primary credential for interacting with the national Tax Agency and Social Security long before either Cl@ve or the modern DNIe existed.

3. **Functional differentiation**: Each system was designed for a different primary purpose. The DNIe is a physical identity document with embedded cryptographic hardware. The FNMT certificate is a software certificate enabling qualified electronic signatures. Cl@ve is an authentication broker simplifying access for citizens who do not have — or cannot use — hardware credentials. idCAT Mòbil targets mobile-only users within Catalonia.

4. **Institutional ownership**: Each system belongs to a different issuing authority with different governance, legal mandates, and user populations.

### Cl@ve — The National Identity Broker

**What it is:** Cl@ve (the name means "key" in Spanish) is Spain's national unified electronic identification and authentication platform, operated by the **Agencia Estatal de Administración Digital (AEAD)** (formerly the Secretaría General de Administración Digital, restructured by Real Decreto 1118/2024). Its purpose is not to issue new identities but to act as a **federated identity broker**: citizens select their preferred authentication method (PIN, password, certificate, or DNIe), and Cl@ve relays the authenticated identity to any participating public service at any level of government. It also provides **Cl@ve Firma**, a cloud-based qualified electronic signature service that stores personal certificates in a Hardware Security Module (HSM) server, enabling citizens to sign documents without carrying physical hardware.

**Scope:** All levels of Spanish public administration — national ministries, regional governments, municipalities — can integrate with Cl@ve. This makes it the widest-scope identity system in the Spanish ecosystem: a Cl@ve credential accepted by the national Tax Agency is in principle the same credential that can log a citizen into Barcelona's municipal office.

**Legal basis:** Founded by *Orden PRE/1838/2014, de 8 de octubre* (Council of Ministers Agreement of 19 September 2014). It operates under *Ley 39/2015, de 1 de octubre* (Common Administrative Procedure Act, which mandates digital access to public services), *Ley 40/2015* (Legal Regime for the Public Sector, requiring interoperability), and *Regulation (EU) 910/2014 (eIDAS)*.[^5]

**Authentication tiers within Cl@ve:**

| Method | Description | eIDAS-equivalent level |
|---|---|---|
| Cl@ve PIN | One-time PIN via SMS; for occasional users | Low |
| Cl@ve Permanente | Username + password + SMS OTP | Low to Substantial |
| Cl@ve (advanced registration) | Video ID or in-person registration | Substantial |
| Cl@ve Firma | Cloud qualified certificate; requires *nivel alto* registration | High (qualified) |

---

### DNIe — The Electronic National Identity Card

**What it is:** The **Documento Nacional de Identidad electrónico (DNIe)** is the Spanish national identity card, issued since birth (or upon naturalisation) to every Spanish citizen by the **Dirección General de la Policía (Ministry of the Interior)**. Since 2006 (DNIe 1.0), the card has contained a cryptographic chip. The current generation, **DNI 3.0** (issued from approximately 2015), adds a dual-interface chip supporting both ISO/IEC 7816 contact and ISO/IEC 14443 Type A/B NFC contactless interfaces — allowing use with a smart card reader or directly via NFC with a smartphone and the official DNI App.[^6]

The chip contains the citizen's personal data, biometric data (photo and fingerprint, encrypted), and two X.509 certificates: an **authentication certificate** (for accessing online services) and a **qualified electronic signature certificate** (for signing documents with full legal force).

**Scope:** The DNIe is Spain's only formally **notified eID scheme** under the eIDAS Regulation, notified to the European Commission on 7 November 2018 (Official Journal reference 2018/C 401/08). Mutual recognition across the EU became mandatory in September 2019. This makes the DNIe the only Spanish digital identity with automatic legal recognition in all EU member states for cross-border transactions.[^7]

**Legal basis:** *Real Decreto 1553/2005, de 23 de diciembre* (establishes the electronic functions of the DNI); *Ley Orgánica 4/2015, de 30 de marzo* (general DNI governance); *Regulation (EU) 910/2014 (eIDAS)*.[^8]

---

### idCAT Mòbil / idCAT Mòbil+ — Catalan Mobile Identity

**What it is:** **idCAT Mòbil** is a mobile-based electronic identification system operated by the **Consorci Administració Oberta de Catalunya (AOC)** — a public consortium co-owned by the Generalitat de Catalunya, the Diputació de Barcelona, and other Catalan local governments. As of 2025 it has over **3 million registered users**.[^9]

The standard **idCAT Mòbil** authenticates via SMS OTP (one-time password sent to the citizen's registered mobile phone) combined with their identity document number (DNI or NIE). The enhanced **idCAT Mòbil+** adds a second static factor — the expiry date of the identity document — raising the assurance level. Registration can be done online (including via video identification, available since 2020, or via WhatsApp since 2025) or in person at participating Catalan entities.

**Scope:** idCAT Mòbil is designed for use with Catalan public administrations — the Generalitat, Catalan municipalities, and public bodies in Catalonia. It is not federated directly with Cl@ve at the national level, and is not accepted by national Spanish ministries. Citizens needing to interact with national Spanish administration must use Cl@ve, DNIe, or an FNMT certificate. However, Barcelona's municipal services accept both Catalan and national identities, making the Ajuntament a point of intersection between both ecosystems.

**Legal basis:** *Llei 29/2010, del 3 d'agost, de l'ús dels mitjans electrònics al sector públic de Catalunya* (Catalan e-government law); the *Protocol d'Identificació i Signatura Electrònica de Catalunya* published by the AOC Consortium; *Ley 39/2015* (applicable across all Spanish administrations); *Real Decreto 311/2022* (Esquema Nacional de Seguridad, ENS); *Regulation (EU) 910/2014 (eIDAS)*.[^10]

---

### FNMT-RCM Digital Certificate — The National Qualified Certificate

**What it is:** The **Fábrica Nacional de Moneda y Timbre – Real Casa de la Moneda (FNMT-RCM)** is Spain's national mint. Through its **CERES** (CERtificación ESpañola) division, it operates as a **Qualified Trust Service Provider (QTSP)** listed on Spain's Trusted List and the EU Trust Service Status List. FNMT-CERES issues the most widely used digital certificates in Spain — software certificates (delivered as P12/PFX files for installation in browsers and operating systems) used by citizens, companies, and public servants alike.

Unlike the DNIe, the FNMT certificate is purely a software credential — no hardware token is required for the standard personal certificate. The most common type is the **Certificado de Ciudadano** (*Certificado de Persona Física*), valid 4 years, obtainable online (after an in-person identity verification step at an authorised entity such as a Tax Agency office, Social Security office, or consulate).

**Scope:** FNMT certificates are not an eID scheme under eIDAS's identification pillar; they are **trust services** (the signature pillar). A Qualified Electronic Signature created with an FNMT certificate on a Qualified Signature Creation Device has the same legal effect as a handwritten signature across all EU member states under eIDAS Article 25(2). When used as an authentication credential, an FNMT certificate effectively provides *de facto* identity verification at the highest level — but this flows from certificate law rather than from eID scheme notification. FNMT certificates are accepted by virtually all Spanish public administration online services.

**Legal basis:** *Ley 6/2020, de 11 de noviembre, reguladora de determinados aspectos de los servicios electrónicos de confianza* (the Spanish implementing law for eIDAS, replacing the former *Ley 59/2003 de Firma Electrónica*); *Regulation (EU) 910/2014 (eIDAS)*; ETSI standards EN 319 401, EN 319 411-1/-2, EN 319 421. FNMT is certified at **ENS ALTA** level (Spain's highest National Security Scheme tier, per Real Decreto 311/2022).[^11]

---

## 3. Identity Assurance and Institutional Trust

### The X.1254 Framework

The ITU-T **Recommendation X.1254** (Entity authentication assurance framework) provides the conceptual underpinning for evaluating how strongly any identity system can vouch for a user. It structures identity assurance across four phases, which map directly onto the systems described here:[^12]

**1. Enrolment phase** — How is a person registered and their identity verified before they receive a credential?

This is the most critical differentiator between the four systems. The DNIe requires in-person appearance at a police station with physical biometric capture (fingerprint, photo). FNMT certificates require in-person verification at an authorised registration authority. idCAT Mòbil (standard) relies on submitting a document number plus a mobile number — a weaker enrolment; idCAT Mòbil with video identification uses operator-reviewed video identity proofing, raising the assurance. Cl@ve ranges from postal invitation codes (weakest) to in-person enrolment or video identification.

**2. Credential management phase** — How are credentials issued, stored, and renewed?

The DNIe stores private keys in a hardware-certified chip (Common Criteria EAL4+, QSCD-certified). FNMT certificates are software files, but the certificate policy and qualified status impose strict issuance and renewal controls. Cl@ve Firma certificates are stored in an HSM server operated by the AEAD. idCAT Mòbil does not issue a stored credential — each authentication generates a fresh OTP, so credential management is limited to the registration binding between a document number and a phone number.

**3. Authentication phase** — How does the user prove their identity when accessing a service?

- DNIe: cryptographic challenge-response using the certificate's private key (stored on the chip). User must provide their PIN to activate the private key.
- FNMT certificate: TLS client certificate authentication or digital signature, using the software certificate and user password.
- Cl@ve: varies by method (SMS OTP, username+password+SMS, or certificate).
- idCAT Mòbil: document number + SMS OTP (one factor of knowledge + one factor of possession). idCAT Mòbil+ adds document expiry date as a second knowledge factor.

**4. Management and organisational considerations** — Who operates the system? What governance and audit structures exist?

Each system has a distinct institutional anchor: the Dirección General de la Policía (DNIe), the AEAD (Cl@ve), the FNMT-RCM (certificates), and the AOC Consorci (idCAT Mòbil). Spain's supervisory body for QTSPs is the **Ministerio para la Transformación Digital**. The ENS (Esquema Nacional de Seguridad) provides a cross-cutting security framework applicable to all Spanish public administration ICT systems.

### eIDAS Assurance Levels

The eIDAS framework — specifically **Commission Implementing Regulation (EU) 2015/1502** — defines three assurance levels for electronic identification: Low, Substantial, and High. Each level specifies requirements for identity proofing, credential issuance, and authentication mechanism strength.[^13]

| Identity System | eIDAS Assurance Level | Basis |
|---|---|---|
| DNIe | **HIGH** (formally notified) | In-person biometric enrolment; QSCD-certified hardware chip; notified to EU Commission November 2018 |
| FNMT-RCM certificate | **Equivalent to High** (Trust Services pillar, not eID scheme) | Qualified certificate issued by QTSP; in-person identity proofing; legally equivalent to handwritten signature (eIDAS Art. 25) |
| Cl@ve (advanced registration / nivel alto) | **High-equivalent** | In-person or video-verified enrolment; required for Cl@ve Firma qualified certificates |
| Cl@ve (basic registration) | **Substantial** (Cl@ve Permanente) / **Low** (Cl@ve PIN) | Postal or basic online enrolment; SMS OTP |
| idCAT Mòbil+ (video ID registration) | **Substantial** | Video identification meets Substantial identity proofing criteria |
| idCAT Mòbil (basic registration) | **Low** | SMS OTP with basic online enrolment only |

The DNIe holds the unique distinction of being Spain's only **formally notified** eID scheme — the mechanism by which Spain's eID is automatically recognised and accepted in other EU member states. Spain was among the first six EU countries to achieve cross-border recognition (November 2019).[^14]

### The OECD G7 Mapping Exercise

The OECD's **G7 Mapping Exercise of Digital Identity Approaches** (2023) provides a comparative framework for how different nations structure their digital identity ecosystems. It distinguishes between *monolithic* approaches (a single national eID as the only recognised credential, as in parts of the eIDAS model) and *multi-dimensional* approaches (layered systems combining different assurance levels and use cases, closer to the NIST SP 800-63 model).[^15]

The Spanish case sits closer to the multi-dimensional end: there is no single mandatory national eID credential for digital services. Citizens can choose among multiple methods with different assurance levels. This reflects both the constitutional structure (autonomous communities having independent e-government systems) and the deliberate design of Cl@ve as a broker that can accept any of the available methods. The OECD framework also emphasises governance, legal certainty, and inclusion as dimensions of digital identity maturity — themes visible in the Spanish approach, where the weakest credential (Cl@ve PIN) was explicitly designed for digital inclusion, allowing citizens without smartphones or hardware tokens to access public services via any mobile phone.

### Legal Elements Enabling the Institutional Trust of Each System

Each identity system derives its institutional trustworthiness from a specific legal anchor that connects technical operations to enforceable rights and obligations:

- **DNIe**: The legal obligation of citizens to hold a DNI (Ley Orgánica 1/1992; Ley Orgánica 4/2015) creates a foundational identity record that the chip merely extends into the digital domain. The State's certificate policy (Declaración de Prácticas de Certificación, DPC) is the legal document governing how DNIe certificates are issued and trusted.

- **Cl@ve**: The Council of Ministers agreement (*Orden PRE/1838/2014*) established Cl@ve as a shared platform service — giving it legal status as part of Spain's administrative infrastructure, obligating other public bodies to accept it.

- **FNMT-RCM**: As a QTSP under eIDAS, FNMT is subject to mandatory audit, supervision, and liability requirements. Its certificates carry the presumption of legal validity under EU and Spanish law. The *Ley 6/2020* defines the liability regime and supervision framework.

- **idCAT Mòbil**: Its trust derives from the Consorci AOC's status as a public body jointly owned by Catalan administrations, and from the *Protocol d'Identificació i Signatura Electrònica de Catalunya*, which defines the conditions under which idCAT Mòbil is accepted within the Catalan public sector.

---

## 4. Technical Implementation: How Barcelona Accepted Multiple Identity Systems

The fact that the Ajuntament de Barcelona accepts all four identity systems for a single procedure — the Padró Municipal — was not accidental. It required a specific technical integration strategy connecting Barcelona's digital office to both the national Cl@ve/SARA network and the Catalan AOC federation.

### The Two Integration Pathways

**Pathway 1 — The AOC VALId service (for Catalan identities and more):**

The **Consorci AOC** operates **VALId** (*Verificació i Autenticació en Línia d'Identitat*), a federated authentication gateway that enables any Catalan public administration to accept multiple identity methods through a single integration. VALId supports idCAT Mòbil, idCAT Mòbil+, idCAT Certificat (AOC's software certificate), DNIe, Cl@ve, and FNMT certificates.

The Ajuntament de Barcelona integrates with VALId using **OAuth 2.0** / **OpenID Connect**. The municipality registers as a client application with the AOC (obtaining a `client_id` and `client_secret`) and redirects users to VALId for authentication. VALId handles all the complexity of verifying each credential type and returns a standardised identity assertion to the municipal service.

This means that from Barcelona's perspective, there is essentially **one integration point** (VALId) that internally routes to all the identity methods. The AOC acts as a federation hub — matching what the GovStack ID BB specification calls the **Upstream Federation** service category: "harmonizing multiple identities across systems."[^16]

Developer documentation for VALId is publicly available at:
- VALId 2.0 documentation (GitHub Pages): [https://consorciaoc.github.io/VALId2/](https://consorciaoc.github.io/VALId2/)
- VALId original documentation: [https://consorciaoc.github.io/VALId/](https://consorciaoc.github.io/VALId/)
- AOC services portal: [https://www.aoc.cat/en/serveis-aoc/valid/](https://www.aoc.cat/en/serveis-aoc/valid/)[^17]

**Pathway 2 — Direct Cl@ve integration (for national identities):**

For national-level identities (Cl@ve PIN, Cl@ve Permanente, DNIe via Cl@ve, FNMT certificate), public bodies can also integrate directly with the **Cl@ve gateway** (pasarela) using **SAML 2.0**. The Cl@ve gateway uses the STORK/eIDAS SAML profile. Service providers send `AuthnRequest` messages specifying the required quality of authentication level (QAA), and the gateway returns signed `SAMLResponse` assertions.

Spain's **@firma** shared platform validates certificate-based authentication (DNIe and FNMT certificates), handling OCSP and CRL validation so individual services do not need to implement certificate validation themselves.

In practice, for Barcelona's municipal services, the AOC's VALId layer abstracts over both Cl@ve and the direct certificate path — so the Ajuntament receives a unified identity token regardless of which underlying system the citizen used.

Developer documentation for Cl@ve integration:
- Official integration guide (PAe/CTT, Spanish government portal): [https://administracionelectronica.gob.es/ctt/clave/infoadicional](https://administracionelectronica.gob.es/ctt/clave/infoadicional)[^18]
- Junta de Andalucía Proxy-Cl@ve integration guide (PDF, practical SAML example): [https://desarrollo.juntadeandalucia.es/sites/default/files/2023-06/Guía_Integración_Proxy_Clave.pdf](https://desarrollo.juntadeandalucia.es/sites/default/files/2023-06/Gui%CC%81aIntegracio%CC%81nAplicacionesEnProxyClave-0100.pdf)[^19]

Developer documentation for DNIe:
- DNIe downloads portal (drivers, PKCS#11 library, Android NFC source): [https://www.dnielectronico.es/PortalDNIe/PRF1_Cons02.action?pag=REF_1100](https://www.dnielectronico.es/PortalDNIe/PRF1_Cons02.action?pag=REF_1100)[^20]
- DNIe NFC reference guide (PDF): [https://www.dnielectronico.es/PDFs/Guia_de_Referencia_DNIe_con_NFC.pdf](https://www.dnielectronico.es/PDFs/Guia_de_Referencia_DNIe_con_NFC.pdf)[^21]

Developer documentation for FNMT certificates:
- FNMT CERES portal: [https://www.fnmt.es/en/ceres](https://www.fnmt.es/en/ceres)
- FNMT Trust Services Practice Statement (English PDF): [https://www.sede.fnmt.gob.es/documents/10445900/10536309/dgpc_english.pdf](https://www.sede.fnmt.gob.es/documents/10445900/10536309/dgpc_english.pdf)[^22]

### The Technical Architecture in Summary

```
Citizen
   │
   ├── Uses idCAT Mòbil / idCAT Mòbil+ / idCAT Certificat
   │        │
   │        ▼
   │   AOC VALId federation gateway (OAuth 2.0 / OIDC)
   │        │
   ├── Uses Cl@ve PIN / Cl@ve Permanente
   │        │
   │        ▼
   │   Cl@ve gateway/pasarela (SAML 2.0)
   │        │
   ├── Uses DNIe (smart card or NFC)
   │        │
   │        ▼
   │   @firma certificate validation platform
   │        │
   └── Uses FNMT certificate (browser/OS installed)
            │
            ▼
       @firma certificate validation platform
            │
            ▼
   Ajuntament de Barcelona Seu Electrònica
   (integrates with VALId as primary auth gateway,
    which in turn federates national methods)
            │
            ▼
   Padró Municipal procedure
```

---

## 5. How These Identities Co-exist: A GovStack Building Block Perspective

The Barcelona case illustrates several patterns that GovStack Building Block specifications describe. The co-existence of four digital identity systems is not simply a technical challenge — it is a governance, design, and architectural choice with implications for trust, inclusion, and interoperability.

### Identity Building Block: The Federated Architecture Pattern

The GovStack Identity BB specification identifies three architectural patterns: centralised, federated, and distributed. It notes that "there is no one-fits-all solution and often a combination of those approaches enables most benefits."[^23]

The Spanish ecosystem is a textbook federated architecture: each identity system (DNIe, FNMT, Cl@ve, idCAT Mòbil) is an independent **Identity Provider (IdP)** with its own enrolment, credential management, and authentication infrastructure. The AOC's VALId and the Cl@ve gateway function as **federation brokers** — aggregating multiple IdPs behind a unified interface for Service Providers (like Barcelona's municipal office). This maps directly to the **Upstream Federation** service category in the GovStack ID BB, which provides "harmonizing multiple identities across systems."

The GovStack ID BB also describes the **Orchestrator** component, which "coordinates the workflow for identity verification, combining multiple services as necessary." In this case, VALId plays this role: when a citizen initiates a padrón procedure, VALId presents the available identity options, routes to the appropriate IdP, receives the authenticated identity, and delivers a normalised identity assertion to the Ajuntament's service.

### eSignature Building Block: Cl@ve Firma and FNMT as Digital Signing Enablers

The GovStack eSignature BB describes two deployment models: one-time signatures (where a new key pair is generated in an HSM and a short-lived certificate is created for each signing event) and SCD-based approaches (where a user registers a personal signing device for reuse).[^24]

**Cl@ve Firma** corresponds to the GovStack eSignature BB's one-time HSM model: when a citizen needs to sign a document, Cl@ve Firma generates a signing operation on the citizen's remote certificate stored on the AEAD's HSM servers, with PIN confirmation as the user-side step. No persistent device is required.

**FNMT and DNIe certificates** correspond to the SCD-based model: the citizen registers a personal device (their computer with the software certificate installed, or the DNIe chip) and can sign documents repeatedly without re-registering. The private key lives on the citizen's device or card.

Both models are reflected in the procedures available at Barcelona's electronic office: citizens can sign submissions digitally using either cloud signatures (Cl@ve Firma) or local certificates (FNMT/DNIe), and the Seu Electrònica supports both paths.

### Consent Building Block: Data Sharing Between Levels of Government

When the Ajuntament de Barcelona shares padrón data with national bodies (for example, updating the INE's national database), this involves a formal data-sharing relationship governed by both the LBRL framework and the GDPR-implementing *Ley Orgánica 3/2018 (LOPDGDD)*.

The GovStack Consent BB notes that "GDPR discourages consent in government services where power imbalances exist between citizens and authorities" — and indeed, the padrón does not operate on the basis of citizen consent; registration is a legal obligation. However, the Consent BB framework is relevant to the *downstream* use of padrón data: when other institutions (banks, utilities, notaries) request proof of residence, the citizen actively presents their certificate, which is an act of selective disclosure. The **CSV (Código Seguro de Verificación)** mechanism embeds this disclosure control — only the specific certificate the citizen chooses to present can be verified, not the broader padrón record.[^25]

### Wallet Building Block: The Path Toward a Unified Credential

The GovStack Wallet BB describes a system where "issuers create credentials, holders store them securely, and verifiers authenticate them" — the Issuer-Holder-Verifier model. It emphasises user control over credential presentation and support for multiple credential standards (W3C VCs, SD-JWT, mDL).[^26]

The current Spanish identity ecosystem predates the wallet model. However, Spain is participating in the EU's EUDI (European Digital Identity) Wallet pilot program under **eIDAS 2.0 (Regulation EU 2024/1183)**. The planned Spanish EUDI Wallet would consolidate many of these credentials — effectively allowing a citizen to carry a digital version of their DNIe, FNMT certificate access, and potentially health and social benefits credentials — in a single, user-controlled wallet app. The four identity systems described in this document represent the *current* state; the wallet represents the trajectory these systems are following.

The co-existence problem that Barcelona has solved through federation (VALId as a broker) would be solved differently under the wallet model: rather than four separate IdPs with one broker, citizens would hold multiple credentials in one wallet and choose which to present. The trust anchors would remain the same (the State, the FNMT, the AOC) but the user experience and the locus of control would shift toward the citizen.

### Summary: The GovStack BB Lens on Multi-Identity Co-existence

| GovStack Building Block | Role in the Barcelona Case |
|---|---|
| **Identity BB** — Federated architecture | VALId (AOC) and Cl@ve act as federation brokers, harmonising four IdPs behind a single integration point for the Ajuntament |
| **Identity BB** — Upstream Federation service | VALId normalises identity assertions from Cl@ve, DNIe, FNMT, and idCAT Mòbil into a uniform format for Barcelona's services |
| **eSignature BB** — One-time HSM model | Cl@ve Firma provides cloud-based qualified signatures for citizens without hardware tokens |
| **eSignature BB** — SCD-based model | DNIe chip and FNMT software certificates provide persistent signing devices for repeated use |
| **Consent BB** — Selective disclosure | The empadronament certificate's CSV mechanism enables citizens to present only the credential they choose to present; GDPR applies to downstream data sharing |
| **Wallet BB** — Future trajectory | Spain's EUDI Wallet participation signals convergence of the current multi-system landscape toward a citizen-controlled credential wallet under eIDAS 2.0 |

---

## 6. Verifying Electronically Signed Documents: Technical Validation and Jurisdictional Concordance

Receiving a digitally signed PDF — whether it is a citizen-submitted form, an empadronament certificate issued by the Ajuntament, or a document signed using Cl@ve Firma — requires answering two distinct questions that are often conflated:

1. **Technical validity**: Was the cryptographic signature correctly produced, and is the certificate still valid at the time of verification?
2. **Jurisdictional concordance**: Was the correct type of signature used for this document — in this jurisdiction, for this legal purpose, by the right category of signer?

Neither question answers the other. A technically valid signature may be legally insufficient for a document that required a higher assurance level. A qualified certificate from a recognised QTSP may still be the wrong instrument if used where an organisational eSeal — not a personal signature — was required. Both checks are necessary.

---

### 6.1 Means of Verification by Signature Type

The four identity and signature systems present in the Barcelona case do not all produce the same kind of verifiable artefact. The appropriate verification mechanism differs by system.

#### FNMT Certificate Signatures (PAdES)

Documents signed with an FNMT personal certificate (Certificado de Ciudadano or Certificado en Tarjeta) are embedded as **PAdES (PDF Advanced Electronic Signatures)** — the format defined by ETSI EN 319 142 for PDF-based qualified signatures.[^27] Verification relies on:

- **VALIDe** (primary tool): Spain's official online signature validation portal, operated by the AEAD at [https://valide.redsara.es/](https://valide.redsara.es/). Upload the PDF; the service verifies the certificate chain, checks revocation via OCSP against FNMT's infrastructure, and returns a structured validation report indicating signature level (*básico, avanzado, cualificado*) and policy conformance.[^28]
- **@firma validation API**: For automated backend validation, public administrations call the `VerifySignature` operation of the @firma shared platform web service. The platform handles OCSP/CRL checking so that individual systems need not implement revocation checking themselves.[^29]
- **Adobe Acrobat Reader (with EUTL)**: FNMT-RCM appears on the EU Trust Service Status List and is therefore recognised as a trusted root by Acrobat when configured to load European Trusted Lists (detailed in Section 6.3 below).
- **EC Digital Signature Service (DSS)**: The European Commission's open-source library for signature creation and validation, implementing the ETSI EN 319 102-1 validation algorithm. Usable as a standalone web application or embedded REST API.[^30]

#### DNIe Qualified Signature Certificate (PAdES or CAdES)

The DNIe chip contains two X.509 certificates: an authentication certificate and a separate **qualified electronic signature certificate**. Only the latter creates signatures with the legal weight of a handwritten signature. Signatures produced using the DNIe signature certificate are verified through the same tools as FNMT signatures. The certificate chain leads to the **Dirección General de la Policía (DGP)** as the issuing CA, which is listed on Spain's Trusted List as a Qualified Trust Service Provider under the service type "QCert for ESig."

One important distinction: the DNIe's authentication certificate (used to log in to online services) should never be confused with the signature certificate. A PDF signed using the authentication certificate is technically a valid advanced electronic signature but is **not** a qualified electronic signature — the QcStatements extension will be absent or will not include `id-etsi-qcs-QcSSCD` (OID `0.4.0.1862.1.4`), because the authentication private key is not held on a Qualified Signature Creation Device for signature purposes. Verification tools will show this as "Avanzado" rather than "Cualificado."

#### Cl@ve Firma (PAdES, Remote QSCD)

Cl@ve Firma produces PAdES signatures using certificates stored in the AEAD's Hardware Security Module infrastructure — a remote QSCD under eIDAS Annex II. The certificate chain leads to a subordinate CA operating under the AEAD's accreditation as a QTSP. These certificates carry the full set of QcStatements and are verifiable via VALIDe and @firma in the same manner as FNMT and DNIe signatures. The resulting "Nivel de firma: Cualificado" result from VALIDe is legally equivalent to the outcome for hardware-based certificates.

#### CSV (Código Seguro de Verificación) — Administrative Documents

The empadronament certificate and similar documents issued by the Ajuntament de Barcelona carry a **Código Seguro de Verificación (CSV)** — a unique alphanumeric code printed or embedded in the document. This mechanism is defined by **Ley 39/2015, Article 27**, which gives documents accompanied by a verifiable CSV the same legal status as certified paper originals, enabling any receiving authority to verify authenticity without needing software to validate a cryptographic signature.[^31]

Verification procedure:
1. The receiving authority notes the CSV code printed on the document (typically on the footer of each page).
2. They navigate to the issuing body's electronic office verification portal.
3. They enter the CSV code (and sometimes a document type or date).
4. The portal confirms whether the document is genuine and displays the official electronic copy for comparison.

For Barcelona:
```
Portal:   [https://seuelectronica.ajuntament.barcelona.cat](https://seuelectronica.ajuntament.barcelona.cat)
Function: "Verificació de documents" → enter CSV code
```

The CSV mechanism is deliberately designed for receiving parties — a court, a notary, a foreign consulate, a university — that may have no ability to validate cryptographic signatures but can open a web browser. It shifts the verification burden from the receiving party to the issuing authority's infrastructure.

#### Note on idCAT Mòbil

idCAT Mòbil is an **authentication** system, not a document signature creation system. It does not produce standalone cryptographic signatures embedded in PDFs. Documents submitted to the Ajuntament via idCAT Mòbil authentication are recorded as authenticated submissions in the **Registre Electrònic**, where the timestamp and identity of the submitter are retained by the system — but the citizen does not apply a personal electronic signature to the document itself. The resulting record is an entry in the administrative register, verifiable as a system act rather than as an individual's cryptographic signature.

Where a personal electronic signature on the submitted document is required (rather than mere authentication), the procedure requires the citizen to use **idCAT Certificat** (the AOC's software certificate product), an FNMT certificate, or the DNIe.

---

### 6.2 Step-by-Step: Validating an Embedded PDF Signature

#### Method A — VALIDe (Recommended for Spanish Public Administration)

VALIDe is the reference validation tool for any Spanish public administration. Its use is the normative method for verifying whether a received document carries a qualified signature under Spanish and eIDAS law.

1. Open a browser and navigate to [https://valide.redsara.es/](https://valide.redsara.es/)
2. Select **"Validar Firma"** from the main menu.
3. Click **"Seleccionar fichero"** and upload the signed PDF (maximum file size applies; for automated batch validation, use the @firma API).
4. Click **"Validar"**.
5. The validation report returned includes:
   - **Estado de la firma**: *Válida / Inválida / Con advertencias* — the primary validity result
   - **Información del firmante**: The signer's name and NIF/NIE as encoded in the certificate subject field
   - **Información del certificado**: Issuer, serial number, and validity period
   - **Nivel de firma**: *Básico / Avanzado / Cualificado* — whether the certificate is a qualified certificate issued by a recognised QTSP under eIDAS
   - **Política de firma**: Whether the signature conforms to a declared signature policy (e.g., the AGE policy OID `2.16.724.1.3.1.1.2.1.9`)
   - **Estado de revocación**: Whether the certificate was valid and unrevoked at the time of signing (OCSP response or CRL check result)
   - **Sello de tiempo**: Whether a trusted timestamp is embedded, and its validity

The result **"Nivel de firma: Cualificado"** is the definitive machine-readable confirmation that the signature carries qualified electronic signature status under eIDAS, with the legal force of a handwritten signature across all EU member states (eIDAS Article 25(2)).

#### Method B — Adobe Acrobat Reader (with European Trusted Lists)

Adobe Acrobat Reader can validate FNMT and DNIe signatures natively, but only if it is configured to load European trusted root certificates. Without this configuration, FNMT and DGP root certificates will not be in Acrobat's trust store and the signature will appear as unverified even if cryptographically correct.

**Enabling European Trusted Lists in Acrobat:**
1. Open **Edit** (Windows) or **Acrobat** (Mac) → **Preferences** → **Trust Manager**
2. Under *Automatic Adobe Approved Trust List (AATL) updates*, ensure **"Load trusted root certificates from an Adobe server"** is enabled.
3. Also enable **"Load European Union Trusted Lists (EUTL)"** (Acrobat XI and later support this).
4. Click **"Update Now"** and allow the download to complete.

**Validating a signature:**
1. Open the signed PDF. A notification bar typically appears: *"Signed and all signatures are valid"* or *"At least one signature has problems."*
2. Open the **Signatures panel** (the pen-nib icon in the left sidebar) to see all embedded signatures.
3. Click on a specific signature entry to expand its details.
4. Right-click the visible signature field on the page → **"Validate Signature"** → **"Signature Properties"**.
5. The Signature Properties dialog shows:
   - **Validity Status** with the reason for the determination
   - **Signer's identity** as it appears in the certificate subject
   - **Signing Time** — with or without a trusted timestamp; the latter is essential for long-term validity
6. Click **"Show Certificate"** to inspect the underlying X.509 certificate.

**Reading the certificate details:**

The Certificate Viewer has three relevant tabs:

- **Summary**: Common Name (the signer), Organisation, Issuer chain, Validity dates
- **Details**: All X.509 extensions — this is where to find the legally significant fields
- **Trust**: The full chain from the signing certificate to the root CA, and whether each level is trusted

In the Details tab, the extensions of greatest legal significance are:

| Extension | OID | What to look for |
|---|---|---|
| Certificate Policies | `2.5.29.32` | The policy OID identifies the QTSP's certificate type (e.g., FNMT Ciudadano, DNIe QES) |
| QcStatements | `1.3.6.1.5.5.7.1.3` | The set of qualified-certificate statements under eIDAS (see below) |
| Key Usage | `2.5.29.15` | `nonRepudiation` bit set → signature certificate; `digitalSignature` only → authentication certificate |
| Subject | n/a | Individual name + SERIALNUMBER (NIF) → personal signature; Organisation name + CIF → eSeal |

**Decoding QcStatements:** Within the QcStatements extension, look for the following sub-statement OIDs. Their presence or absence determines the legal category of the certificate:

| Sub-statement OID | Name | Meaning if present |
|---|---|---|
| `0.4.0.1862.1.1` | `id-etsi-qcs-QcCompliance` | Certificate is qualified under eIDAS — issued by a supervised QTSP |
| `0.4.0.1862.1.4` | `id-etsi-qcs-QcSSCD` | The private key is held on a Qualified Signature Creation Device (QSCD) — required for full QES status |
| `0.4.0.1862.1.6.1` | `id-etsi-qcs-QcType-eSign` | Certificate type: electronic signature (natural person) |
| `0.4.0.1862.1.6.2` | `id-etsi-qcs-QcType-eSeal` | Certificate type: electronic seal (legal person / organisation) |
| `0.4.0.1862.1.6.3` | `id-etsi-qcs-QcType-Web` | Certificate type: website authentication — not a signature certificate |

A certificate carrying both `0.4.0.1862.1.1` and `0.4.0.1862.1.4` and `0.4.0.1862.1.6.1` is a Qualified Electronic Signature certificate for a natural person — the maximum assurance level. A certificate with only `0.4.0.1862.1.1` but without `0.4.0.1862.1.4` is qualified but not QSCD-backed (the private key was software-generated), which corresponds to the FNMT Certificado de Ciudadano (software certificate, no hardware token required).

#### Method C — EC Digital Signature Service (Programmatic Validation)

The **Digital Signature Service (DSS)** is the European Commission's open-source reference implementation for creating and validating electronic signatures according to the ETSI EN 319 series.[^32] It supports CAdES, XAdES, PAdES, and JAdES formats and applies the ETSI EN 319 102-1 validation algorithm — the EU standard for electronic signature validation. It is the validation engine used internally by the EC's own trust services infrastructure.

For a receiving authority needing to validate documents programmatically (e.g., a document management system checking every incoming signed PDF automatically), DSS can be deployed as a REST/SOAP service:

```
POST /services/rest/validation/validateSignature
Content-Type: application/json

{
  "signedDocument": {
    "bytes": "<base64-encoded PDF content>",
    "name": "document.pdf"
  },
  "policy": null,
  "tokenExtractionStrategy": "EXTRACT_CERTIFICATES_ONLY"
}
```

The response contains a `SimpleReport` (per-signature indication: TOTAL_PASSED / TOTAL_FAILED / INDETERMINATE) and a `DetailedReport` with the complete ETSI EN 319 102-1 sub-step breakdown. The source code, release binaries, and deployment documentation are maintained at the EC's open-source platform: [https://ec.europa.eu/digital-building-blocks/sites/display/DIGITAL/Digital+Signature+Service+-++DSS](https://ec.europa.eu/digital-building-blocks/sites/display/DIGITAL/Digital+Signature+Service+-++DSS)

---

### 6.3 Establishing Concordance Between Signature and Document Jurisdiction

Technical validity confirms that the signature is cryptographically sound and the certificate was issued by a recognised authority. Jurisdictional concordance is the further question of whether the right kind of signature was applied to this document — given the document's legal nature, the required assurance level, and the geographic scope in which it will be used.

Three factors must be checked in combination:

1. **Signature type**: Personal electronic signature (natural person) vs. organisational eSeal (legal person)
2. **Qualification level**: Advanced electronic signature vs. qualified electronic signature (QES)
3. **Jurisdictional recognition**: Is the issuing QTSP recognised in the jurisdiction where the document is being used?

#### Factor 1 — Personal Signature vs. Organisational eSeal

In the Barcelona empadronament workflow, two distinct signing acts occur:

- **The Ajuntament's issuance act**: The certificat d'empadronament issued by the Ajuntament de Barcelona is signed by the municipality as a legal person, using an **organisational eSeal** — a qualified certificate in which the Subject field identifies the Ajuntament de Barcelona (an organisation), not an individual. This is a `QcType = eSeal` certificate (OID `0.4.0.1862.1.6.2`). A receiving authority should see the eSeal, not a personal signature, on this document.
- **A citizen's submission act**: If a citizen is required to sign (rather than merely authenticate) a form they submit to the Ajuntament, they use their personal qualified certificate (DNIe signature cert, FNMT cert, or Cl@ve Firma). This is a `QcType = eSign` certificate (OID `0.4.0.1862.1.6.1`).

In Acrobat's certificate viewer, check the Subject field:
```
CN=Ajuntament de Barcelona, O=Ajuntament de Barcelona, C=ES
  → organisational eSeal ✓ — correct for an authority-issued document

CN=Joan Garcia Garcia, SERIALNUMBER=12345678Z, C=ES
  → personal electronic signature ✓ — correct for a citizen-signed submission
```

A document that should bear an organisational eSeal but instead carries a personal certificate — for example, a certificate signed by a municipal employee's personal DNIe rather than the Ajuntament's institutional certificate — may indicate a procedural gap. The signature may be technically valid but jurisdictionally incorrect: it asserts an individual committed to the document, not the institution.

#### Factor 2 — Required Qualification Level Under Spanish Law

**Ley 39/2015, Article 10** establishes the hierarchy of acceptable electronic identification and signature forms for Spanish administrative procedures.[^31] The minimum required level increases with the legal weight of the act:

| Procedure category | Minimum acceptable | Which systems qualify |
|---|---|---|
| Accessing administrative services (authentication only) | Any recognised eID | All four systems (Cl@ve PIN, DNIe, FNMT, idCAT Mòbil) |
| Submitting documents and forms electronically | Advanced electronic signature | DNIe auth cert (advanced), FNMT cert, idCAT Certificat |
| Acts with the legal effect of a handwritten signature | Qualified electronic signature (QES) | DNIe *signature* cert (QSCD), FNMT qualified cert, Cl@ve Firma |
| Documents replacing a notarial act or with equivalent force | QES + declared signature policy | DNIe or FNMT cert + conformance to AGE policy or sector-specific policy |

To determine whether a received PDF's signature meets the required level:

1. Run validation in VALIDe and read the "Nivel de firma" field: *Cualificado* confirms QES status.
2. In the certificate, confirm OID `0.4.0.1862.1.1` (`id-etsi-qcs-QcCompliance`) is present — without it, the certificate is not qualified.
3. For documents requiring QSCD backing, confirm OID `0.4.0.1862.1.4` (`id-etsi-qcs-QcSSCD`) is also present.
4. For documents requiring conformance to a declared signature policy, check the `SignaturePolicyId` field in the signature. For Spanish AGE-compliant signatures, this should reference the published policy OID `2.16.724.1.3.1.1.2.1.9` and include a hash of the policy document, allowing the verifier to retrieve and confirm the policy at the published URL.

#### Factor 3 — Jurisdictional Scope and Cross-Border Recognition

The hardest check to automate is whether the QTSP that issued the signing certificate is recognised **in the jurisdiction where the document will be used**. Automatic cross-border recognition within the EU is governed by eIDAS: a qualified electronic signature based on a certificate from any QTSP on the EU Trust Service Status List (EUTL) has the same legal effect in all EU member states as a handwritten signature (eIDAS Article 25(2)).[^33] No bilateral agreement is needed within the EU for QES.

For the four identity systems in this document, the cross-border validity picture is as follows:

| Identity system | Within Spain | EU cross-border | Outside EU |
|---|---|---|---|
| **FNMT-RCM certificate (qualified)** | ✓ (QTSP on Spain Trusted List + EUTL) | ✓ (eIDAS Art. 25 — QES legally equivalent to handwritten signature in all EU MS) | Case by case |
| **DNIe qualified signature certificate** | ✓ (DGP on Spain Trusted List + EUTL) | ✓ (eIDAS Art. 25 + formally notified eID scheme — strongest cross-border basis) | Case by case |
| **Cl@ve Firma (HSM-based QES)** | ✓ (AEAD-accredited chain on Trusted List) | ✓ (same QES chain; EUTL-recognised QTSP) | Case by case |
| **idCAT Mòbil (authentication act)** | ✓ within Catalonia and Spain | ✗ (not a notified eID scheme; no EUTL entry) | ✗ |
| **Ajuntament de Barcelona eSeal** | ✓ (FNMT or AOC-issued organisational cert) | Conditional (FNMT-issued eSeal ✓; AOC-issued seal depends on EUTL status of AOC as QTSP) | ✗ |

**How to verify EUTL status manually:**

1. Open the signing certificate in Acrobat (Show Certificate → Details) and note the Root CA — the Issuer at the top of the chain (e.g., "AC Componentes Informaticos — FNMT-RCM").
2. Navigate to the EU Trust Service Status List browser, maintained by the European Commission's Digital Building Blocks programme: [https://ec.europa.eu/digital-building-blocks/sites/display/ESIGKEYPAGE](https://ec.europa.eu/digital-building-blocks/sites/display/ESIGKEYPAGE)
3. Search by country (Spain — ES) and QTSP name.
4. Confirm the trust service type listed is **"QCert for ESig"** (for personal signature certificates) or **"QCert for ESeal"** (for organisational seal certificates).
5. Confirm the status is **"granted"** — a status of "withdrawn" means the QTSP is no longer supervised and new certificates from it should not be trusted, though previously issued certificates remain valid for signatures made during the grant period.

---

### 6.4 Summary: The Concordance Checklist

For a receiving authority that needs to determine whether a signed PDF was correctly signed for its legal purpose, the following checklist consolidates all three factors:

| Check | Where to look | Tool |
|---|---|---|
| **Is the signature cryptographically intact?** | Signature block in the PDF | VALIDe / Acrobat / DSS |
| **Was the certificate valid at the time of signing?** | Certificate validity period + OCSP/CRL at time of signing | VALIDe ("Estado de revocación") |
| **Is this a qualified electronic signature?** | QcStatements OID `0.4.0.1862.1.1` in the certificate | VALIDe ("Nivel: Cualificado") / Acrobat cert viewer |
| **Was the key on a QSCD?** | QcStatements OID `0.4.0.1862.1.4` | Acrobat cert viewer → Details tab |
| **Is this a personal signature or organisational eSeal?** | QcStatements OID `0.4.0.1862.1.6.X` + certificate Subject | Acrobat cert viewer — confirms individual vs. institution |
| **Does the document's procedure require QES?** | Ley 39/2015 Art. 10 + the issuing body's procedural rules | Legal framework — not a technical check |
| **Is the QTSP recognised in the destination jurisdiction?** | EUTL (EU) or Spain Trusted List (national) | EC Trust Service Status List browser |
| **Does the signature conform to a declared policy?** | `SignaturePolicyId` OID and hash in the signature | VALIDe ("Política de firma") |
| **For authority-issued documents: is the CSV verifiable?** | CSV code printed on the document | Issuing body's electronic office verification portal |

---

## References

[^1]: Spain. *Ley 7/1985, de 2 de abril, Reguladora de las Bases del Régimen Local.* Boletín Oficial del Estado, núm. 80, 3 de abril de 1985. Articles 15–17. [https://www.boe.es/buscar/doc.php?id=BOE-A-1985-5392](https://www.boe.es/buscar/doc.php?id=BOE-A-1985-5392).

[^2]: Spain. *Ley 4/1996, de 10 de enero, por la que se modifica la Ley 7/1985, de 2 de abril, Reguladora de las Bases del Régimen Local, en relación con el Padrón Municipal.* Boletín Oficial del Estado, núm. 11, 12 de enero de 1996. [https://www.boe.es/buscar/doc.php?id=BOE-A-1996-753](https://www.boe.es/buscar/doc.php?id=BOE-A-1996-753).

[^3]: Spain. *Real Decreto 141/2024, de 6 de febrero, por el que se modifica el Real Decreto 1690/1986, de 11 de julio.* Boletín Oficial del Estado, núm. 33, 7 de febrero de 2024. [https://www.boe.es/buscar/doc.php?id=BOE-A-2024-2248](https://www.boe.es/buscar/doc.php?id=BOE-A-2024-2248).

[^4]: Ajuntament de Barcelona. "Alta al Padró Municipal d'Habitants — Seu Electrònica." Accessed April 2026. [https://seuelectronica.ajuntament.barcelona.cat/oficinavirtual/es/tramit/20200001402/](https://seuelectronica.ajuntament.barcelona.cat/oficinavirtual/es/tramit/20200001402/).

[^5]: Spain. *Orden PRE/1838/2014, de 8 de octubre, por la que se publica el Acuerdo del Consejo de Ministros, de 19 de septiembre de 2014, por el que se aprueba Cl@ve.* Boletín Oficial del Estado, núm. 246, 10 de octubre de 2014. [https://www.boe.es/buscar/doc.php?id=BOE-A-2014-10295](https://www.boe.es/buscar/doc.php?id=BOE-A-2014-10295). See also: Agencia Estatal de Administración Digital. "Cl@ve: Plataforma de Identificación y Autenticación." [https://clave.gob.es](https://clave.gob.es).

[^6]: Dirección General de la Policía. "DNI Electrónico — Portal Oficial." [https://www.dnielectronico.es](https://www.dnielectronico.es). See also: Policía Nacional. *Guía de Referencia DNIe con NFC.* PDF. [https://www.dnielectronico.es/PDFs/Guia_de_Referencia_DNIe_con_NFC.pdf](https://www.dnielectronico.es/PDFs/Guia_de_Referencia_DNIe_con_NFC.pdf).

[^7]: European Commission. "Overview of Pre-Notified and Notified eID Schemes Under eIDAS." Digital Building Blocks, European Commission. Accessed April 2026. [https://ec.europa.eu/digital-building-blocks/sites/display/EIDCOMMUNITY/Overview+of+pre-notified+and+notified+eID+schemes+under+eIDAS](https://ec.europa.eu/digital-building-blocks/sites/display/EIDCOMMUNITY/Overview+of+pre-notified+and+notified+eID+schemes+under+eIDAS). Reference: Official Journal of the EU 2018/C 401/08.

[^8]: Spain. *Real Decreto 1553/2005, de 23 de diciembre, por el que se regula la expedición del documento nacional de identidad y sus certificados de firma electrónica.* Boletín Oficial del Estado, núm. 307, 24 de diciembre de 2005. [https://www.boe.es/buscar/doc.php?id=BOE-A-2005-21163](https://www.boe.es/buscar/doc.php?id=BOE-A-2005-21163).

[^9]: AOC Consorci. "3 Milions de Persones amb idCAT Mòbil." AOC Blog, 2025. [https://www.aoc.cat/en/blog/2025/3milions-persones-idcatmobil/](https://www.aoc.cat/en/blog/2025/3milions-persones-idcatmobil/). See also: Consorci AOC. "idCAT Mòbil." [https://idcat.aoc.cat/en/idcat-mobile/](https://idcat.aoc.cat/en/idcat-mobile/).

[^10]: Catalonia. *Llei 29/2010, del 3 d'agost, de l'ús dels mitjans electrònics al sector públic de Catalunya.* Diari Oficial de la Generalitat de Catalunya, núm. 5686, 5 d'agost de 2010. [https://dogc.gencat.cat/ca/pdogc_canals_interns/pdogc_resultats_fitxa/?action=fitxa&documentId=555557](https://dogc.gencat.cat/ca/pdogc_canals_interns/pdogc_resultats_fitxa/?action=fitxa&documentId=555557). See also: Consorci AOC. *Protocol d'Identificació i Signatura Electrònica de Catalunya.* [https://www.aoc.cat/en/serveis-aoc/valid/](https://www.aoc.cat/en/serveis-aoc/valid/).

[^11]: Spain. *Ley 6/2020, de 11 de noviembre, reguladora de determinados aspectos de los servicios electrónicos de confianza.* Boletín Oficial del Estado, núm. 298, 12 de noviembre de 2020. [https://www.boe.es/buscar/doc.php?id=BOE-A-2020-13069](https://www.boe.es/buscar/doc.php?id=BOE-A-2020-13069). See also: FNMT-RCM CERES. "Certification Practice Statement." PDF. [https://www.sede.fnmt.gob.es/documents/10445900/10536309/dgpc_english.pdf](https://www.sede.fnmt.gob.es/documents/10445900/10536309/dgpc_english.pdf).

[^12]: International Telecommunication Union. *ITU-T Recommendation X.1254: Entity Authentication Assurance Framework.* Geneva: ITU, 2012. [https://www.itu.int/rec/T-REC-X.1254/en](https://www.itu.int/rec/T-REC-X.1254/en).

[^13]: European Commission. *Commission Implementing Regulation (EU) 2015/1502 of 8 September 2015 on setting out minimum technical specifications and procedures for assurance levels for electronic identification means pursuant to Article 8(3) of Regulation (EU) No 910/2014 of the European Parliament and of the Council on electronic identification and trust services for electronic transactions in the internal market.* Official Journal of the European Union L 235/7, 9 September 2015. [https://eur-lex.europa.eu/legal-content/EN/TXT/PDF/?uri=CELEX:32015R1502](https://eur-lex.europa.eu/legal-content/EN/TXT/PDF/?uri=CELEX:32015R1502).

[^14]: European Commission. "eIDAS eID Mutual Recognition Goes Live." Press release, September 2019. [https://ec.europa.eu/digital-building-blocks/sites/display/EIDCOMMUNITY](https://ec.europa.eu/digital-building-blocks/sites/display/EIDCOMMUNITY). See also: Secretaría General de Administración Digital. "España despliega la primera versión de su nodo eIDAS." December 2016. [https://administracionelectronica.gob.es/pae_Home/pae_Actualidad/pae_Noticias/Anio2016/Diciembre/Noticia-2016-12-21.html](https://administracionelectronica.gob.es/pae_Home/pae_Actualidad/pae_Noticias/Anio2016/Diciembre/Noticia-2016-12-21.html).

[^15]: Organisation for Economic Co-operation and Development. *G7 Mapping Exercise of Digital Identity Approaches.* Paris: OECD Publishing, 2023. [https://www.oecd.org/en/publications/g7-mapping-exercise-of-digital-identity-approaches_56fd4e94-en.html](https://www.oecd.org/en/publications/g7-mapping-exercise-of-digital-identity-approaches_56fd4e94-en.html). See also: National Institute of Standards and Technology. *NIST Special Publication 800-63-3: Digital Identity Guidelines.* Gaithersburg, MD: NIST, 2017. [https://pages.nist.gov/800-63-3/](https://pages.nist.gov/800-63-3/).

[^16]: GovStack Initiative. *Identity Building Block Specification, Section 2: Description.* GovStack, 2024. [https://specs.govstack.global/identity/2-description](https://specs.govstack.global/identity/2-description).

[^17]: Consorci AOC. "VALId 2.0 — Developer Documentation." GitHub Pages, 2024. [https://consorciaoc.github.io/VALId2/](https://consorciaoc.github.io/VALId2/). See also: Consorci AOC. "VALId Service." [https://www.aoc.cat/en/serveis-aoc/valid/](https://www.aoc.cat/en/serveis-aoc/valid/).

[^18]: Agencia Estatal de Administración Digital. "Cl@ve — Additional Information for Integration (CTT)." Portal de Administración Electrónica, 2024. [https://administracionelectronica.gob.es/ctt/clave/infoadicional](https://administracionelectronica.gob.es/ctt/clave/infoadicional).

[^19]: Junta de Andalucía. *Guía de Integración de Aplicaciones en Proxy-Clave, v0.1.00.* Sevilla: Consejería de la Presidencia, 2023. PDF. [https://desarrollo.juntadeandalucia.es/sites/default/files/2023-06/Gui%CC%81aIntegracio%CC%81nAplicacionesEnProxyClave-0100.pdf](https://desarrollo.juntadeandalucia.es/sites/default/files/2023-06/Gui%CC%81aIntegracio%CC%81nAplicacionesEnProxyClave-0100.pdf).

[^20]: Dirección General de la Policía. "DNIe — Descargas y Documentación." [https://www.dnielectronico.es/PortalDNIe/PRF1_Cons02.action?pag=REF_1100](https://www.dnielectronico.es/PortalDNIe/PRF1_Cons02.action?pag=REF_1100).

[^21]: Dirección General de la Policía. *Guía de Referencia del DNIe con NFC.* Madrid: Ministerio del Interior, 2019. PDF. [https://www.dnielectronico.es/PDFs/Guia_de_Referencia_DNIe_con_NFC.pdf](https://www.dnielectronico.es/PDFs/Guia_de_Referencia_DNIe_con_NFC.pdf).

[^22]: FNMT-RCM CERES. *Declaración de Prácticas de Certificación / Certification Practice Statement.* Madrid: FNMT-RCM, 2023. English PDF. [https://www.sede.fnmt.gob.es/documents/10445900/10536309/dgpc_english.pdf](https://www.sede.fnmt.gob.es/documents/10445900/10536309/dgpc_english.pdf).

[^23]: GovStack Initiative. *Identity Building Block Specification, Section 2: Description.* GovStack, 2024. [https://specs.govstack.global/identity/2-description](https://specs.govstack.global/identity/2-description).

[^24]: GovStack Initiative. *eSignature Building Block Specification, Section 2: Description.* GovStack, 2024. [https://specs.govstack.global/esignature/2-description](https://specs.govstack.global/esignature/2-description).

[^25]: GovStack Initiative. *Consent Building Block Specification, Section 2: Description.* GovStack, 2024. [https://specs.govstack.global/consent/2-description](https://specs.govstack.global/consent/2-description).

[^26]: GovStack Initiative. *Wallet Building Block Specification, Section 2: Description.* GovStack, 2024. [https://specs.govstack.global/wallet/2-description](https://specs.govstack.global/wallet/2-description).

[^27]: ETSI. *EN 319 142-1: Electronic Signatures and Infrastructures (ESI) — PAdES Digital Signatures — Part 1: Building blocks and PAdES baseline signatures.* Sophia Antipolis: ETSI, 2016. [https://www.etsi.org/deliver/etsi_en/319100_319199/31914201/01.01.01_60/en_31914201v010101p.pdf](https://www.etsi.org/deliver/etsi_en/319100_319199/31914201/01.01.01_60/en_31914201v010101p.pdf). See also ETSI EN 319 122 (CAdES) and EN 319 132 (XAdES) for non-PDF signature formats.

[^28]: Agencia Estatal de Administración Digital. "VALIDe — Plataforma de Validación de Firmas Electrónicas." Portal de Administración Electrónica. [https://valide.redsara.es/](https://valide.redsara.es/). See also: AEAD. "VALIDe — Guía de Uso." [https://administracionelectronica.gob.es/ctt/valide](https://administracionelectronica.gob.es/ctt/valide).

[^29]: Agencia Estatal de Administración Digital. "@firma — Plataforma de Validación y Firma Electrónica." Portal de Administración Electrónica. [https://administracionelectronica.gob.es/ctt/afirma](https://administracionelectronica.gob.es/ctt/afirma). See also: Ministerio para la Transformación Digital y de la Función Pública. *Manual de Integración de @firma.* Madrid: MTTD, 2023. [https://administracionelectronica.gob.es/ctt/afirma/infoadicional](https://administracionelectronica.gob.es/ctt/afirma/infoadicional).

[^30]: European Commission. "Digital Signature Service (DSS) — Open Source Library." Digital Building Blocks, European Commission. [https://ec.europa.eu/digital-building-blocks/sites/display/DIGITAL/Digital+Signature+Service+-++DSS](https://ec.europa.eu/digital-building-blocks/sites/display/DIGITAL/Digital+Signature+Service+-++DSS). The DSS implements the ETSI EN 319 102-1 validation algorithm: ETSI. *EN 319 102-1: Electronic Signatures and Infrastructures (ESI) — Procedures for Creation and Validation of AdES Digital Signatures — Part 1: Creation and Validation.* Sophia Antipolis: ETSI, 2019. [https://www.etsi.org/deliver/etsi_en/319100_319199/31910201/01.03.01_60/en_31910201v010301p.pdf](https://www.etsi.org/deliver/etsi_en/319100_319199/31910201/01.03.01_60/en_31910201v010301p.pdf).

[^31]: Spain. *Ley 39/2015, de 1 de octubre, del Procedimiento Administrativo Común de las Administraciones Públicas.* Boletín Oficial del Estado, núm. 236, 2 de octubre de 2015. Articles 10 (electronic signature requirements by procedure type) and 27 (legal equivalence of digital documents with verifiable CSV). [https://www.boe.es/buscar/act.php?id=BOE-A-2015-10565](https://www.boe.es/buscar/act.php?id=BOE-A-2015-10565).

[^32]: ETSI. *EN 319 102-1: Electronic Signatures and Infrastructures (ESI) — Procedures for Creation and Validation of AdES Digital Signatures.* Sophia Antipolis: ETSI, 2019. [https://www.etsi.org/deliver/etsi_en/319100_319199/31910201/01.03.01_60/en_31910201v010301p.pdf](https://www.etsi.org/deliver/etsi_en/319100_319199/31910201/01.03.01_60/en_31910201v010301p.pdf).

[^33]: European Parliament and of the Council. *Regulation (EU) 910/2014 (eIDAS), Article 25(2): A qualified electronic signature shall have the equivalent legal effect of a handwritten signature.* Official Journal of the European Union L 257, 28 August 2014. [https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A32014R0910](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A32014R0910). The EU Trust Service Status List (EUTL), listing all supervised QTSPs by member state, is maintained at: European Commission. "EU Trust Services Dashboard." [https://eidas.ec.europa.eu/efts/](https://eidas.ec.europa.eu/efts/).

---

*Additional sources consulted:*

- Ajuntament de Barcelona. "Registration at the Municipal Register of Residents." Barcelona International Welcome. [https://www.barcelona.cat/internationalwelcome/en/registration-municipal-register-residents-city-barcelona](https://www.barcelona.cat/internationalwelcome/en/registration-municipal-register-residents-city-barcelona).
- Generalitat de Catalunya. "idCAT Mòbil — Com donar-te d'alta." [https://web.gencat.cat/en/atenem/suport-tramitacio/durant-la-tramitacio/signar-i-identificar-digitalment/idcat-mobil](https://web.gencat.cat/en/atenem/suport-tramitacio/durant-la-tramitacio/signar-i-identificar-digitalment/idcat-mobil).
- European Parliament and of the Council. *Regulation (EU) 910/2014 on Electronic Identification and Trust Services for Electronic Transactions in the Internal Market (eIDAS).* Official Journal of the European Union L 257, 28 August 2014. [https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A32014R0910](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A32014R0910).
- European Parliament and of the Council. *Regulation (EU) 2024/1183 amending Regulation (EU) No 910/2014 as regards establishing the European Digital Identity Framework (eIDAS 2.0).* Official Journal of the European Union L 1183, 30 April 2024. [https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=OJ:L_202401183](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=OJ:L_202401183).
- FNMT-RCM. "CERES — Certificación Española." [https://www.fnmt.es/en/ceres](https://www.fnmt.es/en/ceres).
- Spain. *Real Decreto 311/2022, de 3 de mayo, por el que se regula el Esquema Nacional de Seguridad.* Boletín Oficial del Estado, núm. 106, 4 de mayo de 2022. [https://www.boe.es/buscar/doc.php?id=BOE-A-2022-7191](https://www.boe.es/buscar/doc.php?id=BOE-A-2022-7191).
- Interoperable Europe Portal. "Cl@ve — Unifying and Simplifying Identification for Spanish Online Public Services." [https://interoperable-europe.ec.europa.eu/collection/egovernment/document/clve-unifying-and-simplifying-identification-spanish-online-public-services-clve](https://interoperable-europe.ec.europa.eu/collection/egovernment/document/clve-unifying-and-simplifying-identification-spanish-online-public-services-clve).
- AOC Consorci. "idCAT Mòbil — Video Identification." AOC Blog, 2022. [https://www.aoc.cat/en/blog/2022/idcatmobil-videoidentificacio/](https://www.aoc.cat/en/blog/2022/idcatmobil-videoidentificacio/).
- Instituto Nacional de Estadística. "Padrón Municipal — Legislación." [https://idapadron.ine.es/repositorio/legislacion/a2301alt.htm](https://idapadron.ine.es/repositorio/legislacion/a2301alt.htm).
