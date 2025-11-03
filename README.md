# 8) Instaurer la confiance à chaque signature ! Collecte électronique fédérée et vérifiée cryptographiquement

*[Hackathon Guidelines](https://www.bk.admin.ch/bk/de/home/politische-rechte/e-collecting/aktuelles.html)

## Approche

### 1. Introduction
Notre approche repose sur l’adaptation des processus réglementaires existants à une architecture décentralisée et vérifiable. Pour plus de détails, consultez notre documentation complète (à compléter) et les livrables déjà produits (le cas échéant).

Nous recherchons des contributeurs avec des compétences en :
- Modélisation de processus réglementaires
- Expérience des systèmes communaux et cantonaux
- citoyens intéressé à la numérisation des services publiques

<img width="2463" height="1394" alt="image" src="https://github.com/user-attachments/assets/a3ca31d0-87da-42eb-be51-3b5de96826c1" />
<img width="2470" height="1393" alt="image" src="https://github.com/user-attachments/assets/58adf86a-37e0-41c9-a8c8-c4abd0430212" />
<img width="2467" height="1394" alt="image" src="https://github.com/user-attachments/assets/9d7ba9f7-3238-4e66-88cb-c6c8349de9f2" />
<img width="2471" height="1385" alt="image" src="https://github.com/user-attachments/assets/ab424852-d8ef-49e2-99e5-268ec815d056" />
<img width="2471" height="1392" alt="image" src="https://github.com/user-attachments/assets/d79caaeb-5fba-4827-88df-fcd13bebcdab" />

### 2. Description synthétique

Notre solution s’appuie sur les architectures open source DKMS (Decentralised Key Management System) et OCA v2.0 (Overlays Capture Architecture), développées par la fondation Human Colossus, pour numériser et sécuriser les processus civiques tout en garantissant la transparence et la vérifiabilité.

#### Étape 1 : Cas d’usage — Collecte de signatures en milieu physique
Nous modélisons et implémentons la numérisation du processus de collecte de signatures, en intégrant :
- Numérisation de la collect de signature dans la rue
- La vérification en temps réel des signatures électroniques
- La complémentarité avec les solutions "papier"

#### Étape 2 : "Trust but Verify" Analyse des 10 thèmes du Hackathon
Nous évaluons chaque thème en identifiant :
- Les avantages apportés par notre solution (transparence, traçabilité, inclusion)
- Les risques potentiels (accessibilité, adoption, conformité réglementaire)
- Une analyse de risque des technologies numériques (e.g. anonymity, linkability)

Objectifs de ces deux étapes :
1. Démontrer la faisabilité d’une solution civique basée sur des protocoles ouverts et décentralisés
2. Mettre en évidence les bénéfices concrets par rapport aux systèmes papier ou centralisés
3. Révéler des fonctionnalités exclusives à la version numérique — notamment, une preuve de comptage de signatures accessible au citoyen


## Approach
### 1. Introduction
Our approach is based on adapting existing regulatory processes to a decentralized and verifiable architecture. For more details, see our full documentation (to be completed) and any deliverables already produced (if applicable).

We are seeking contributors with skills in:
- Modeling regulatory processes
- Experience with municipal and cantonal systems
- Citizens interested in the digitization of public services
  
### 2. Summary Description
Our solution leverages the open-source architectures [DKMS](https://dkms.colossi.network/) (Decentralised Key Management System) and [OCA](https://oca.colossi.network/) v2.0 (Overlays Capture Architecture), developed by the [Human Colossus Foundation](https://humancolossus.foundation/), to digitize and secure civic processes while ensuring interoperability, transparency and verifiability.

#### Step 1: Use Case — Steeet Signature Collection
We model and implement the digitization of the signature collection process, integrating:
- Digitization of signature collection in the street
- Real-time verification of electronic signatures by all actors
- Complementarity with “paper” solutions

#### Step 2: Analysis of the 10 Hackathon Themes
We evaluate each theme by identifying:
1. Benefits provided by our solution (transparency, traceability, inclusion)
2. Potential risks (accessibility, adoption, regulatory compliance)
3. Objectives of these two steps:

Demonstrate the feasibility of a civic solution built on open, decentralized protocols
Highlight tangible benefits compared to paper-based or centralized systems
Reveal features exclusive to the digital version — notably, citizen-accessible proof of signature count

## Documentation and Diagrams
Over the course of 2 days hackathon we worked with all [stakeholders](#sequence-diagram-details-des-interactions--flux-de-données) to reflect their requirments, governance and limitations.

<img width="2463" height="1394" alt="Proposed architecture diagram for protocol-based approach" src="./docs/E-collecting Hackathon..png" />


Below sequence diagram present possible scenario showcase how propsed architecture could improve e-collecting process, few highlights presented on the below diagram:
- Anonymity and linkability are the two main characteristics to consider when securing and protecting citizen privacy. Linkability is only needed between citizens and the commune, while anonymity should be in place for any other actors, who should not be able to discover citizen identity. This is especially important for the Federal Council when counting votes.
- It is assumed that the authentication (identification) process between the commune and citizen can be carried out using various ID providers (SwissPass, Swiss e-ID, passport, SwissSign, etc.). After this, the commune can issue a `one-time certificate` that can be used to digitally sign that specific initiative. This ensures that the citizen will not be linked in the subsequent stages of the process, while maintaining the audibility and cryptographic provability of the entire process.
- Introduce an additional notification mechanism to inform citizens about eligibility checks and signatures included in initiatives. This increases transparency and allows citizens to regain trust in the digital system. If someone tries to 'steal' their signature, they will at least be informed.
- Thanks to `DKMS`, we can establish distributed (digital) governance around the ecosystem and designate different parties which can be verified (as well as all the objects e.g. survey with content) during the process, for example:
  - Inclusive organisations, who can enrich existing initiatives with additional layers, e.g. local translation, improved text for people with ADHD, improved reading materials for blind people, and so on.
  - Collectors, so citizens can verify whether a collector is authorised to collect votes.
  - ID providers
  - Verify that the content which citizens are signing is actually registered for the initiative.
- The protocol-based approach enables each actor to define their own rules, facilitating integration with existing IT systems and reducing the costs and complexity of e-collection. This is particularly important in the context of various registries used to verify citizens and different parties within the ecosystem.
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

###  Desciption générale des processus selon la réglementation en vigeure
### 1 Lancement D'initiative populaires et demande de référendum
*à faire*

### 2 Collecte des signature
#### Flow chart
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

#### Sequence Diagram: Details des interactions & Flux de données
Le processus de collecte des signatures pour les initiatives et les référendums est décrit dans le rapport du Conseil fédéral (réf. AAA).
Il implique les acteurs suivants :
| 🎯 Acteur                      | 📝 Description                                                                 | 📜 Base légale / Notes                                     | 🛠️ Responsabilités dans la phase de récolte             |
|-------------------------------|--------------------------------------------------------------------------------|------------------------------------------------------------|----------------------------------------------------------|
| **Comité**                    | Comité lançant l’initiative populaire ou la demande de référendum. Gère la campagne, la logistique et le traitement des données. | Art. 60a, 69a LDP (listes) ; LPD Art. 5c (protection des données) | Diffuser les listes, engager des collecteurs, respecter la finalité des données |
| **Électeurs**                 | Citoyens suisses qui signent les listes. Leurs données sont sensibles selon la LPD. | LPD Art. 5c (données sensibles) ; principe de finalité     | Renvoyer les listes signées (par la poste ou en personne) |
| **Organisations professionnelles**         | Organismes professionnels engagés pour récolter des signatures ou obtenir des attestations. | En cours de réglementation (soupçons de falsification)      | Récolter en espace public ; obtenir les attestations d’électeur |
| **Chancellerie fédérale (CH)** | Autorité fédérale qui met à disposition les listes de signatures téléchargeables. | Art. 60a, 69a LDP                                          | Fournir les formulaires — *non impliquée dans la récolte* |
| **Services électoraux**       | Services cantonaux ou communaux gérant les registres électoraux.               | Droit cantonal (vérification de l’éligibilité)             | Délivrer les attestations d’électeur aux collecteurs     |
| **Cantons/Communes (CC)**     | Autorités locales régulant l’utilisation de l’espace public pour la récolte.   | Droits fondamentaux (Art. 5, 10, 35 Cst.)                  | Autoriser l’utilisation de l’espace public sous conditions |

**Diagramme de séquences**
![Signature Collection Diagram](https://github.com/the-human-colossus-foundation/e-collecting-hackathon-team8/blob/main/docs/SD_signatureCollection.png)


## User Experience

Although our approach does not directly address UX, it has a significant impact on UX design. This is because the protocol-based approach enables the development of applications or integrations tailored to the specific needs of each stakeholder without compromising interoperability. For instance, an independent organisation could develop a referendum app tailored to blind people, enabling them to participate in the initiative more easily. Similarly, people unable to sign could use a dedicated application with facial recognition for identification purposes, reducing barriers to participation. The SMPT protocol has also enabled various solutions for email clients and servers on the internet, and DKMS does the same here. This allows the creation of a rich, stable ecosystem that is resilient and can address the needs of all parties (with no vendor locking).

## Topics addressed
L'équipe 8 *Confiance pour chaque signature" abordéra les 10 thèmes présentés dans les [directives](https://www.bk.admin.ch/bk/de/home/politische-rechte/e-collecting/aktuelles.html). La table ci-dessous identifié l'approche:
- *Gouvernance:* Quelles règles définissent le système
- *Data:* Comment la définission et l'intégrité des données est-elle assurée.
- *Tech.:* Quelles inovations technologiques nous allons introduire
En fonction de l'avancement du hackathon, des liens seront ajouté pour donner plus de détails.

*Explain how you addressed the topics presented in the [guidelines](https://www.bk.admin.ch/bk/de/home/politische-rechte/e-collecting/aktuelles.html), filling in the template below.*

| Topic | (How) is it addressed? |c.f. Cas d'étude|
| -| ------- |---- |
| 1 « De la volonté de soutien à la déclaration de soutien »| *Gouvernance:* ...||
|| *Data:* ...||
||**Tech. perspective:** Authentication décentralisée||
| 2 « Accès aux informations concernant les déclarations de soutien déposées » | *Gouvernance:* ...||
|| *Data:* ...||
||**Tech. perspective:** ... ||
| 3 « Attribution des attestations de soutien aux comités et aux entreprises de récolte »| *Gouvernance:* ...||
|| *Data:* ...||
||**Tech. perspective:** ...  ||
| 4 « Diffusion des arguments des comités via le logiciel de récolte électronique de signatures » | *Gouvernance:* ...||
|| *Data:* ...||
||**Tech. perspective:** ...  ||
| 5 « Exclusion des attestations de soutien illicites »  |*Gouvernance:* ...||
|| *Data:* ...||
||**Tech. perspective:** ...   ||
| 6 « Prévention des attestations de soutien non dépouillées »  | *Gouvernance:* ...||
|| *Data:* ...||
||**Tech. perspective:** ...  ||
| 7 « Respect du secret du vote »  |*Gouvernance:* ...||
|| *Data:* ...||
||**Tech. perspective:** ...   ||
| 8 « Intégration avec le processus papier »  |*Gouvernance:* ...||
|| *Data:* ...||
||**Tech. perspective:** ...   ||
| 9 « Introduction facilitée pour les communes avec un gain d'efficacité ; sur la base des
infrastructures et des processus existants »  | *Gouvernance:* ...||
|| *Data:* ...||
||**Tech. perspective:** ...  ||
| 10 « Récolte électronique pour tous les niveaux fédéraux »  | *Gouvernance:* ...||
|| *Data:* ...||
||**Tech. perspective:** ...  ||

### 3 Vérification des signature et soumission à la Chancellerie Fédérale
*à faire*

## Points forts et faiblesses (*Key Strenghts and Weaknesses*)

*List the key strengths and weaknesses of your solution.*

### Points forts:
(*Key strenght*)
- ...
- ...

### Faiblesses:
(*Weaknesses*)
- ...
- ...

## Getting Started  (*prochaine mise à jour vendredi*)

*These instructions will get you a copy of the technical prototype (if applicable) up and running on your local machine for development and testing purposes. **If you are not developing a technical prototype, please present or reference your conceptual and/or clickable prototype.***

### Conditions préalables
*Ce dont vous avez besoin pour commencer.*
Nous formons une équipe multidisciplinaire. 
- Citoyen 
- Cantons et communes
- Initiateur d'une initiative / d'un référendum
- Chancellerie fédérale
- Développeur de solutions
La condition préalables principale est la volonté de poser des questions afin de construire une solution les prenant en compte.

### Installation (*prochaine mise à jour vendredi*)
*Une série d'exemples étape par étape qui expliquent comment mettre en place l'environnement de développement.*
*A step by step series of examples that tell you how to get a development env running.*
*What things you need to install the software and how to install them.*

## Contribution & Code de conduite
Veuillez lire [CONTRIBUTING.md](/CONTRIBUTING.md) pour plus de détails sur notre code de conduite.

## Team Members

- Philippe Page (*gouvernance digitale*)
- Robert Mitwicki (*technologies décentralisées*)
- Damian VIZÁR (*sécurité, cryptographie*)
- Michał Pietrus (*Digital Identity & Applied Cryptography*)
  
- *Contactez Philippe Page <philippe.page@humancolossus.org> si vous voulez rejoindre l'équipe 8*
- *Wenden Sie sich an Philippe Page <philippe.page@humancolossus.org>, wenn Sie dem Team 8 beitreten möchten.*
- *Contatta Philippe Page <philippe.page@humancolossus.org> se desideri entrare a far parte del team 8*

## License

Tous les documents contenus dans ce référentiel sont soumis à une licence EUPL1.2. Pour plus d'informations, consultez le fichier [LICENCE](LICENCE).

Alle Materialien in diesem Repository unterliegen einer EUPL1.2-Lizenz – Einzelheiten finden Sie in der Datei [LICENSE](LICENSE).

Tutti i materiali presenti in questo archivio sono concessi in licenza ai sensi della licenza EUPL1.2. Per ulteriori dettagli, consultare il file [LICENZA](LICENZA).

Ĉiuj materialoj en ĉi tiu deponejo estas licencitaj laŭ EUPL1.2-licenco - vidu la dosieron [LICENSE](LICENSE) por detaloj.

All materials under this repository is licensed under a EUPL1.2 License - see the [LICENSE](LICENSE) file for details.

