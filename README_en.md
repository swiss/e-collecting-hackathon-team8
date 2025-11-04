# Team 8. Build trust with every signature! Federated and cryptographically verified electronic collection
*(une version francaise est [ici](https://github.com/the-human-colossus-foundation/e-collecting-hackathon-team8/blob/main/README.md))*
## Team 8 Contributors
| Member  | Expertise  | Organisation |
|---------|---------------|-------------|
| Philippe Page | *distributed governance* | [Human Colossus Foundation](https://humancolossus.foundation)|
| Robert Mitwicki | *decentralised technologies* | [Human Colossus Foundation](https://humancolossus.foundation)|
| Jérôme Campese | *signature collection agency* | [VOX Communication SA](https://www.vox-communication.ch/presentation) |
| Alessua Pacino | *canton of Thurgau* | |
| Damian VIZÁR | *sécurity, cryptography* | CSEM |
| Michał Pietrus | *digital identity & applied cryptography* | ArgonAuths |
  
### References
1. [Récolte électronique des signatures à l'appui des initiatives populaires et des demandes de référendum au niveau fédéral](https://www.newsd.admin.ch/newsd/message/attachments/90668.pdf), Rapport du Conseil Fédéral, Novembre 2023
2. [Hackathon Guidelines](https://www.bk.admin.ch/bk/de/home/politische-rechte/e-collecting/aktuelles.html) Chancellerie Fédérale
3. Overlays Capture Architecture [OCA](https://oca.colossi.network/) specification
4. Distributed Key Managment System [DKMS](https://dkms.colossi.network/) specification

## Approach
### 1. Introduction
Our approach is based on adapting existing regulatory processes to a decentralised and verifiable architecture. 

During the hackathon, we interacted with experts with the following skills:
- Modelling of regulatory processes
- Experience with municipal and cantonal systems
- Citizens interested in the digitisation of public services
- Signature collection agents

#### Presentation of the approach in 4 minutes
<img width="2463" height="1394" alt="image" src="https://github.com/user-attachments/assets/a3ca31d0-87da-42eb-be51-3b5de96826c1" />
<img width="2470" height="1393" alt="image" src="https://github.com/user-attachments/assets/58adf86a-37e0-41c9-a8c8-c4abd0430212" />
<img width="2467" height="1394" alt="image" src="https://github.com/user-attachments/assets/9d7ba9f7-3238-4e66-88cb-c6c8349de9f2" />
<img width="2471" height="1385" alt="image" src="https://github.com/user-attachments/assets/ab424852-d8ef-49e2-99e5-268ec815d056" />
<img width="2471" height="1392" alt="image" src="https://github.com/user-attachments/assets/d79caaeb-5fba-4827-88df-fcd13bebcdab" />

### 2. Summary description: Federated and independent approach based on a single platform

#### Scope of the Hackathon: Phase 1
We propose a *small but significant steps* approach to ensure that changes to standards (e.g. number of signatures to be collected) can be adapted to technological progress.

| Phase  | Goal  | Description |
|---------|---------------|---- |
|1  |Essential digitisation | The status quo is not an option. This first phase, to be implemented rapidly, therefore focuses on key points and introduces **a digital signature for citizens** and **improves the efficiency of controls**  while preserving the role of municipalities, cantons, initiative committees and the Federal Chancellery.|
|2  |Feedback loop| Measuring the adoption of new developments and measuring societal impact. *This topic, although discussed during the hackathon, is not addressed here.*|
|3  |DDPI| Integration of E-Collecting into the broader concept of the Democratic Digital Public Infrastructure (DDPI). *Not relevant to the hackathon* |

According to the above approach, only phase 1, **Essential Digitisation**, is included in the scope of our solution for the hackathon.

#### Protocols for data integrity and authenticity
Our solution aims to establish a decentralised architecture enabling each participant in the e-collecting process to interact without the need for a single platform. This approach aims to integrate the systems of legitimate participants rather than creating centralised platforms or registers that create dependencies on different technology providers, a risk of hacking (honey pot), and deployment costs. Two innovations are described below:

A. Authenticity & Integrity by Design

B. Distributed Governance

#### Documentation and Diagrams
#### A Authenticité et Intégrité *by-design*
We introduce a protocole based approach where open-source protocoles for authentication and data integrity are intégrated in the different components of an E-Collecting system. Collectively, they enable a digital verification architecture that can be used by any stakeholders in the process. 

This architecture is based on two open source components [DKMS](https://dkms.colossi.network/) (Decentralised Key Management System) for the authentication and [OCA](https://oca.colossi.network/) v2.0 (Overlays Capture Architecture), developed by the [Human Colossus Foundation](https://humancolossus.foundation/) for data integrity and harmonisation. These are two architectures are particularly well suited to digitising and securing civic processes while ensuring interoperability, transparency and verifiability.

The following diagramme describes how these architectures integrate into an E-Collecting system from identification of a stakeholder up to the specific applications/integration.

The technology stack (left column) rests on a digital identifiers layer that assumes multiple providers. The **"Identity Provider"** layer provide flexibility to integrate different mechanisms for identification depending on the use case. An example discussed during the hackathon refers to the *accessibility* where the identification for visually impaired individual will require specific mechanisms (e.g. biometric).

The **Protocol Layer** ensure security and harmonisation across the different authentication methods. 

The **Governance** layer is where the purpose of the use case is defined in terms of actors and data flows. In the Hackathon, we considered on specific use case of the E-Collection in the street as a benchmark use case. Other use cases can be developed without changing the underlying layers. This approach ensures interoperability between use cases and is well suited for a "Program Approach" where multiple projects can be developed independently. During the Hackathon, the case of applying E-Collecting for cantonal petition was elaborated for example.

The **Application Layer** is where the UX/UI is developed according to the use case defined in the Governance Layer. This ensures that context dependent application can be developed with the assurance that each is secured through the same governance and rest on the same authentication and integrity protocols. This approach has a significant cost impact as the security of the the system in terms of authentication and integrity is in the protocol and does not need to be redeveloped at the application layer. In technical terms, the approach is a paradigm shift from *Fat Application on Thin Protocols* to *Thin Application to Fat Protocols*

<img width="2463" height="1394" alt="Proposed architecture diagram for protocol-based approach" src="./docs/E-collecting Hackathon..png" />

The architecture above provide a flexible framework to handel **Anonymity** and **Linkability**, the two main characteristics to consider when securing and protecting citizen privacy. It is well know that trade off between the two often occur. Within our layered approach, the two characteristics can be considered with a specific context. For E-Collecting, linkability is only needed between citizens and the commune. Anonymity between citizen and his commune reduces to the commune not recording the citizen support to an initiative/referandum longer than the strict minimum required. On the other hand anonymity should be in place for any other actors, who should not be able to discover citizen identity.  This is especially important for the Federal Council when counting votes.

Over the course of 2 days hackathon we worked with all [stakeholders](#sequence-diagram-details-of-interactions--data-flows) to reflect their requirments, governance and limitations. Below sequence diagram present possible scenario showcase how propsed architecture could improve e-collecting process, few highlights presented on the below diagram:

- Authentication (identification) process between the commune and citizen can be carried out using various ID providers (SwissPass, Swiss e-ID, passport, SwissSign, etc.). After this, the commune can issue a `one-time certificate` that can be used to digitally sign that specific initiative. This ensures that the citizen will not be linked in the subsequent stages of the process, while maintaining the audibility and cryptographic provability of the entire process.
- Introduction of additional notification mechanisms to inform citizens about eligibility checks and signatures included in initiatives. This increases security transparency and allows citizens to regain trust in the digital system. If someone tries to 'steal' their signature, they can opt-in a notification mechanism can informed them.
- `DKMS` to establish a distributed (digital) governance around the ecosystem and designate different parties which can be verified (as well as all the objects e.g. survey with content) during the process, for example:
  - Inclusive organisations, who can enrich existing initiatives with additional layers, e.g. local translation, improved text for people with ADHD, improved reading materials for blind people, and so on.
  - Collectors, so citizens can verify whether a collector is authorised to collect votes.
  - ID providers
  - Verify that the content which citizens are signing is actually registered for the initiative.
- The protocol-based approach enables each actor to define their own rules, facilitating integration with existing IT systems and reducing the costs and complexity of e-collection. This is particularly important in the context of various registries used to verify citizens and different parties within the ecosystem.

#### E-Signature in the street use case
We model and implement the digitization of the signature collection process, integrating:
- Digitization of signature collection in the street
- Real-time verification of electronic signatures by all actors
- Complementarity with “paper” solutions
Demonstrate the feasibility of a civic solution built on open, decentralized protocols
Highlight tangible benefits compared to paper-based or centralized systems
Reveal features exclusive to the digital version — notably, citizen-accessible proof of signature count

#### Collection process & artifacts.
The use case is describe in terms that will allow an in depth security analysis. These Hackaton notes sketches a notion of a scheme for electronic collection of signatures in supporting a referendum or an initiative.

The objective of such notion is to help define clear security requirements and assumptions, as well as to facilitate security analysis.

#### Notation
Parties denoted with **boldface**.
Artifacts denoted with *italics*.

#### Parties
1. **Committee**: Initiaties an initiative with the objective of collecting enough signatures to support it. 
2. **Chancellerie**: Validates the initiative, counts the signatures, attests the end result.
3. **Collectors**: Mandated by the Committee to collect signatures
4. **Voters**: Give their signatures to support the initiative
5. **Commune**: Verifies signatures (i.e. Voters eligibility) and ensures each Voter contributes at most once 

In addition, all parties except **Voters** have internal employees, denoted **XXX.Emp** where **XXX** is the party in question. The party **Commune** conflates Canton/Commune/Electoral committee for simplicity.

#### Process
In each party **XXX** with employees, each **XXX.Emp** that intervenes on an internal process of **XXX** receives a *Mandate* from **XXX**. The mandate may be role based, or task-based (a role specific to the initiative/batch of signatures etc.).

1. **Committee**: Creates and authenticates *Initiative* 
    * **Committee.Emps** contribute to the Initiative
2. **Chancellerie**: Verifies, approves and authenticates the  *Initiative*
    * Concrete **Chancellerie.Emps** perform the verification
3. **Committee**: Mandates **Collectors**  with the collections of *Support signatures* for the *Initiative* 
    * Inidividual mandates are issued by **Committee.Emps**
4. **Collectors**: Collect *Support signatures* for the *Initiative* from **Voters** and transfer them to **Committee**
    * Individual *Support signatures* are collected by concrete **Collector.Emps**
5. **Committee**: Send collected *Support signatures* to **Commune** for verification, in order to obtain *Signature certificates*
    * Verification and processing of signature (batches) could be performed by individual **Commune.Emps** but possibly also automatized
6. **Committee**: Obtains *Signature certificates* from the **Commune** and keeps track of the total count
7. **Chancellerie**: Obtains all collected *Signature certificates* from **Committee**, verifies them and if the count is sufficient, issues a *Confirmation of the initiative success*.
    * Verification and processing of signature (batches) could be performed by individual **Chancellerie.Emps** but possibly also automatized

#### Artifacts
The artifacts highlighted in the process may be constructed in many ways, depending on the construction. Additional, auxiliary artifacts may be used if needed, but those above shall be embodied in any distributed construction that aligns with the existing governance structures and procedures.
1. *Initiative*: Initiative for which **Voters** support is asked.
2. *Support signatures*: Set of support of **Voters** including mandatory attributes (name, address,signature,...) for each **Voters**. Support is collected asynchronously and are bundled together. **Commune** is the atomic unit (i.e. each signature list contains individual signatures of the same **Commune**
3. *Signature certificates*: Certifies the eligibility and unicity of individual **Voters** in one or more *Support signatures* of a specific **Commune**
4. *Confirmation of the initiative success*: is the certificate issued by the Chancellor in case of success. This artifact, or its absence after a define time limit, triggers sub-processes (e.g.  *Support signatures* destruction, launch popular vote) that terminate the support signature collection process.

The process is represented in the following sequence diagramme
```mermaid
sequenceDiagram
  actor A as Citizien
  actor K as Collector
  participant IdProvider@{"type":"entity"}
  participant Commune@{ "type" : "control" }
  participant Commitee
  participant FC as Federal Council
  participant InclusionOrg

  A->>IdProvider: Enroll digital ID
  IdProvider->>A: Provide Verifiable Credential (e.g. ID Card)
  FC->FC: Issue official template
  Note right of FC: OCA - assuring integrity of meaining and structure
  Commitee->Commitee: Register initative
  Commitee->FC: Request signature lists
  FC->>Commitee: Provide Initiative survey in OCA format
  FC->InclusionOrg: Retrive official survey 
  InclusionOrg->InclusionOrg: Enhance with inclusivens layers (e.g. for blind people, Dyslexia, Local translations)

  alt Digital
  Commitee->>A:Learn about Initiative
  opt Retrive inclusivens enhancment
    InclusionOrg->>A: Provide accessibility layer for initiative
  end
  A->>Commune: Authenticate for eligibility check
  Commune->>A: Provide certificate for signing
  A->>A: Sign
  A->>Commitee: Provide anonymouse digital prove to support initiative
  end
  
  alt Paper
  Commitee->>K: Order signature collection
  K->+A:Approach for signature collection
  A->-K:Sign (digital or paper)
  K->>Commune: Ask for eligibility check
  Commune->>A: Inform that Colletor ask for such check
  Commune->>K: Provide digital proof of the validated signatures
  K->>Commitee: Provide anonymouse digital prove to support initiative 
  end

  Commitee->>FC: Provide supporting signatures
  FC->>FC: Counts and announce results
  A->>FC: Verify cryptographically that my signature was included

    
```
A preliminary draft of a security analysis is provided [here for illustration purposes](https://github.com/the-human-colossus-foundation/e-collecting-hackathon-team8/blob/main/docs/SecurityAnalysis_v01.pdf).

#### B.Distributed Governance *by-design*
For the Governance Layer, we apply a digital distributed governance model that avoids the need of creating a centralised platform outside the control of a legitimate authority (e.g no data stored unless already provision in the law). 

A very simplified flow chart is
```mermaid
flowchart TD
    A[Lancement campagne] --> B[Obtention listes CH]
    B --> C{Distribution}
    C --> D[En ligne → Électeurs → Retour par poste]
    C --> E[En espace public → Optionel:Organisations professionnels → Services électoraux]
    D & E --> F[Cycle répété : rappels + cibles]
    F --> G[Gestion données sensibles LPD]
    G --> H[Fin récolte → Prêt pour validation par autorité compétentes]

```

#### Sequence Diagram: Details of interactions & Data flows
The process of collecting signatures for initiatives and referendums is described in the Federal Council report (ref. AAA).
It involves the following actors:
| 🎯 Actor                      | 📝 Description                                                                 | 📜 Legal Basis / Notes                                     | 🛠️ Responsibility in signature collection             |
|-------------------------------|--------------------------------------------------------------------------------|------------------------------------------------------------|----------------------------------------------------------|
| **Committee**                    | Committee launching the popular initiative or referendum request. Manages the campaign, logistics and data processing. | Art. 60a, 69a LDP (lists); LPD Art. 5c (data protection) | Distribute lists, hire collectors, respect the purpose of the data |
| **Voters**                 | Swiss citizens who sign the lists. Their data is sensitive according to the DPA. | DPA Art. 5c (sensitive data); principle of purpose     | Return the signed lists (by post or in person) |
| **Collectors**         | Professional organisations involved in collecting signatures or obtaining certificates. | Currently being regulated (suspected falsification)      | Collecting in public spaces; obtaining voter certificates |
| **Federal Chancellery** |  Federal authority that makes the signature lists available for download. | Art. 60a, 69a LDP                                          | Provide forms — *not involved in collection* |
| **Electoral Committee**       | Cantonal or municipal services managing electoral registers.               | Cantonal law (verification of eligibility)             | Issuing voter certificates to collectors     |
| **Cantons/Communes**     | Local authorities regulating the use of public space for harvesting.   | Fundamental rights (Art. 5, 10, 35 Cst.)                  | Authorise the use of public space under certain conditions |

**Sequence Diagram**
![Signature Collection Diagram](https://github.com/the-human-colossus-foundation/e-collecting-hackathon-team8/blob/main/docs/SD_signatureCollection.png)

## User Experience
Although our approach does not directly address UX, it has a significant impact on UX design. This is because the protocol-based approach enables the development of applications or integrations tailored to the specific needs of each stakeholder without compromising interoperability. For instance, an independent organisation could develop a referendum app tailored to blind people, enabling them to participate in the initiative more easily. Similarly, people unable to sign could use a dedicated application with facial recognition for identification purposes, reducing barriers to participation. The SMPT protocol has also enabled various solutions for email clients and servers on the internet, and DKMS does the same here. This allows the creation of a rich, stable ecosystem that is resilient and can address the needs of all parties (with no vendor locking).

## Topics covered
Team 8, ‘Trust for every signature’, addressed the 10 topics presented in the [guidelines](https://www.bk.admin.ch/bk/de/home/politische-rechte/e-collecting/aktuelles.html). 

## **Topic 1 — From Willingness to Support → Submission (UX & Trust)**

### Advanced Authentication for Identification: *Who is Who*

* **Multiple identity systems:** Expect many identity systems at different levels (e.g., national ID, canton ID, citizien ID etc.), requiring a **compatibility layer** between them.
* **PKI limits for long-term verification:** Today’s PKI relies on **short-lived, rotating keys**. Root compromises force **mass revocations**, making cross-time and cross-jurisdiction verification fragile.
* **DKMS shift — trust IDs, not keys:** Move trust from the **key** to a **stable identifier**, so keys and crypto suites (e.g., post-quantum) can evolve without breaking integrity. Design for **parallel identity systems** (national, canton, etc.).
* **Protocol-first, privacy-capable interoperability:** Use **open protocols** (not a central authority) to include diverse ID systems, choosing cryptography that supports **privacy-preserving features** like *selective disclosure* and *zero-knowledge proofs*.
  
### Distributed Governance

* Maintaining digital sovereignty would be a major challenge. This is why an approach based on decentralised protocols would help with the design and deployment of systems, allowing us to maintain the same digital sovereignty as in the real world without worrying that the technology would limit or restrict it. Technologies have a tendency to centralise and simplify things, which can harm the possibility of adapting them to local rules. We therefore suggest a local-first approach. 

---

## **Topic 2 — Access to Up-to-Date Information on Submitted Supports (Transparency)**

Verifiable access to information, **independent of origin**, is crucial for enabling people to access necessary information in their **own language**.
A **protocol-based approach** allows multiple implementations — written, voice, or video — creating an **inclusive** yet **verifiable** system.

Because multiple channels and intermediaries exist, data in motion must be secured to ensure verifiability without compromising openness in distribution. This aligns with the necessary characteristics of anonymity and linkability of the information where needed. A complex process of data flows is needed, for example when a commune sends information to a committee and the committee sends it to the Chancellory, as at any time the committee could pull out for various reasons and they have the sovereignty to decide about it. If the information were sent directly to the Chancellory, this would violate those rights.

---

## **Topic 3 — Committees’ Operating Conditions & Collection Ecosystem**

Built-in **data provenance** ensures traceability and compliance.
Onboarding and delegation should be **smooth and practical**, without disrupting the overall process.

All entities should have **freedom to organize** themselves within ecosystem governance.
To support this:

* The system must handle **multiple identity systems**.
* Allow **layered governance**, enabling each entity to define its own rules within jurisdictional scope.
* Ensure **flexibility and traceability** through a **protocol-based approach**, preventing misuse or overreach by any party.

---

## **Topic 4 — Presenting Committees’ Arguments via E-Collecting**

**Informed consent** and **transparency** in accessing information are essential to protect **citizen sovereignty** and prevent **correlation attacks**.

Even subscribing to a specific initiative can expose data useful for targeting campaigns.
Protocols that ensure **authenticity and origin** of arguments in a **multilingual** and **multi-format** environment (digital and physical) reduce the risk of **false presentation**.

---

## **Topic 5 — Excluding Unlawful Supports (Eligibility, Duplicates, Authenticity)**

In digital systems, **cryptography** is the only reliable defense against:

* Forged signatures
* Duplicate submissions
* Authenticity breaches

To build a **durable system**, **cryptographic agility** is essential — allowing compromised keys to be replaced without disrupting the entire network.

A robust **revocation and recovery mechanism** is a *must-have* for ecosystem sustainability.
Different use cases require different techniques:

* **Zero-knowledge proofs** for privacy-preserving verification
* **Selective disclosure** or **designated verifier signatures** for protecting against signature misuse

A **protocol-based approach** provides this flexibility without enforcing a one-size-fits-all model, ensuring **document integrity** across all formats and languages.

---

## **Topic 6 — Preventing Suppressed (Lost/Withheld) Supports**

Full **process transparency** with **confirmation mechanisms (receipts)** enables both sides to verify actions:

* The collector can prove a signature was received.
* The signer can prove their support was submitted for a specific purpose.

Verification is a vector of trust that allows everyone to verify their contributions and check on others. This enables us to regain trust in digital systems and make the entire solution more resilient to manipulation. Securing information at the protocol level enables us to achieve this without compromising interoperability. The design of DKMS allows observers to be introduced into the process, providing an additional layer of security. This is similar to the way observers are used for paper-based processes in real life.

**Event logs** must exist at the **protocol level** for interoperability and notification, allowing signers to confirm their vote was counted — even remotely or via mail.

**Authenticity & integrity protocols** enable **traceability**, while **platform-free design** eliminates central points of failure or attack.

---

## **Topic 7 — Preserving Secrecy & Privacy**

**Data minimization** and **privacy-preserving exchanges** depend on verifiable mechanisms that ensure trust in *who did what* and *what was checked*.

Verification establishes **trust vectors** — essential for both transparency and accountability.
Digital technologies introduce powerful **privacy-enhancing cryptography**, but require **cryptographic agility** to choose the right tool for each case.

A **protocol-based approach** anchored on **identifiers** (not keys) allows interoperability across ecosystems with varying privacy standards.

In addition, introducing unlinkability into the process after the citizen has interacted for eligibility allows user identities to be protected after signing an initiative.

---

## **Topic 8 — Integration with Paper Processes (Hybrid Operation)**

**Paper** remains a trusted, simple, and inclusive medium.
Integration with paper-based processes is essential for **inclusivity** and **adaptability** — digital systems should **enhance**, not replace, paper workflows.

A **protocol-based approach** supports this inclusivity, enabling hybrid configurations:

* Fully digital
* Fully paper-based
* Mixed or transitional setups

Baseline protocols ensure all combinations remain **interoperable and verifiable**.
Authentication and integrity protocols allow digitally enhanced papers to be produced, which increase security and address various forms of misuse and forgery that have led to recent scandals. 

---

## **Topic 9 — Easy Municipal Adoption & Efficiency Gains (Use Existing Infrastructure)**

Municipalities differ in resources and digital readiness:
Some can adopt advanced digital systems immediately, while others must **gradually integrate** new processes.

Security must remain consistent across all entities.
Starting with **paper-enhanced processes** provides a low-risk path to **building trust** among citizens and organizations.

A **protocol-based approach** lets each municipality **choose the right tool** for its context, supporting multiple implementations under the same secure and verifiable foundation.

## **Topic 10 — Electronic harvesting for all federal levels**

Securing data rather than location allows for easier data exchange, not only for collecting information from various sources, but also for creating a data provenance chain for verifiability. A zero-trust architecture approach based on protocols enables simple and complex connections between authorities at different levels of technological advancement. This reduces costs and gives access to information only to authorised users, who can be governed using both bottom-up and top-down approaches, allowing for greater flexibility.

## Key Strenghts and Weaknesses

### Key strenght
- Data Security in motion
- Decentralised protocols are increasing interoperability without compromising security.
- A lack of platform reduces the risk of failure (there is no single point of failure).
- There is a possibility of reducing costs and time to market for the multisteakholder development process.
  
### Weaknesses
- A new approach would lead to barriers to adoption due to a lack of understanding. 
- A more complicated system involving more components.

## Pilot

We suggest conducting a pilot with a consortium of stakeholders to demonstrate the benefits of the technology and identify any potential challenges that may arise during testing in the real world. The consortium should consist of:
- organisations that collect signatures on the streets
- an inclusivity organisation;
- at least two or more ID providers. 
- two or more communes.
- at least two cantons
- Cryptography experts
- IT providers of solutions for IT systems in communes/cantons (integration feasibility). 
- Federal Council

As initiatives are a very sensitive topic, we would suggest running a pilot in scope of collecting signatues for petition, which would give us the chance to prepare for a large-scale pilot of national initiatives. 

## License

Tous les documents contenus dans ce référentiel sont soumis à une licence EUPL1.2. Pour plus d'informations, consultez le fichier [LICENCE](LICENCE).

Alle Materialien in diesem Repository unterliegen einer EUPL1.2-Lizenz – Einzelheiten finden Sie in der Datei [LICENSE](LICENSE).

Tutti i materiali presenti in questo archivio sono concessi in licenza ai sensi della licenza EUPL1.2. Per ulteriori dettagli, consultare il file [LICENZA](LICENZA).

Ĉiuj materialoj en ĉi tiu deponejo estas licencitaj laŭ EUPL1.2-licenco - vidu la dosieron [LICENSE](LICENSE) por detaloj.

All materials under this repository is licensed under a EUPL1.2 License - see the [LICENSE](LICENSE) file for details.
