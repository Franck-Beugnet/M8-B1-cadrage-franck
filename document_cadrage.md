# Document de cadrage — Cabinet Maître Devalle (3 pages max)

> **Projet :** Assistant interne de recherche de jurisprudence locale et d'aide à la rédaction de courriers  
> **Client :** Cabinet Maître Devalle (12 avocats, Bordeaux)  
> **Auteur :** Franck (Consultant IA FastIA) — Date : 29/09/2026

---

## 1. Synthèse exécutive (5-6 lignes — rédigée EN DERNIER)
_Section finalisée à 14h30 après l'imprévu client._

> **Imprévu client (14h30) — ce que ça change** : _À renseigner lors de la réception de l'imprévu à 14h30._

---

## 2. Besoin métier et contexte (1 paragraphe)

**Demande exprimée par le client :**  
> *« On rédige beaucoup de courriers types (mise en demeure, transmission dossier). On voudrait un assistant pour aller plus vite, et aussi pour retrouver les bonnes jurisprudences en 30 secondes au lieu de 30 minutes. »*

**Besoin réel reformulé :**  
Le cabinet souffre d'une dispersion documentaire historique (courriers dupliqués sur postes individuels, modèles communs non maintenus depuis 2019, recherche orale informelle) qui ralentit la production juridique et fragilise la capitalisation du savoir. Le besoin réel consiste à **sécuriser et accélérer l'accès au fonds jurisprudentiel propre du cabinet** (~2 000 décisions bordelaises) et à **standardiser la pré-rédaction des courriers récurrents** (recouvrement et baux commerciaux) via un outil d'aide interne. L'enjeu central n'est pas une automatisation complète mais un **gain de productivité strict sans risque déontologique**, avec contrôle humain systématique (avocat signataire), sous contrainte budgétaire maîtrisée (15 000 € de mise en place) et dans un délai de 6 mois.

---

## 3. Données

| Donnée | Existante / à acquérir | Volume, qualité estimée | Personnelle ? |
|---|---|---|---|
| **Registre des décisions internes** | Existante (fournie dans `data/cas_A_registre_decisions_sample.csv`) | ~2 000 entrées sur 15 ans. Très bonne qualité de métadonnées (colonnes identifiant, date, matière, juridiction TJ Bordeaux, issue). | Non (métadonnées d'affaires et de procédure). |
| **Fichiers textuels des décisions** | Existante | ~2 000 documents (PDF natifs, Word, scans anciens). Qualité hétérogène : PDF/Word récents très exploitables, scans papier plus anciens nécessitant une extraction de texte (OCR). | Oui : noms des parties, adresses, éléments de contentieux (PII couvertes par secret pro). |
| **Modèles de courriers types** | Existante | Quelques dizaines de modèles (dossier partagé 2019 + versions locales avocats). Qualité moyenne : disparité des versions et risque d'obsolescence juridique. | Non dans les gabarits types, mais données réelles dans les anciens courriers réutilisés. |
| **Historique des courriers rédigés** | Existante | Plusieurs milliers de courriers Word archivés par dossier client. Bonne qualité formelle mais forte dispersion sur disques locaux. | Oui : identité des clients, débiteurs, montants, faits litigieux. |
| **Jurisprudence nationale publique** | Existante (externe) | Accessible via abonnement commercial existant du cabinet. Qualité excellente et à jour. | Non. Hors périmètre d'ingestion de la solution (déjà couvert). |
| **Données d'entraînement labellisées** | À acquérir (non requises) | Aucune donnée annotée pour entraînement ML supervisé. RAG retenu : pas d'annotation lourde requise. | Sans objet. |

**Constats de qualité observés sur l'extrait réel (`cas_A_registre_decisions_sample.csv`) :**
1. **Excellente structuration des métadonnées** : les décisions disposent déjà d'un identifiant unique (`DEC-xxxx`), d'une date normée (`YYYY-MM-DD`), d'une matière juridique claire (*recouvrement, bail commercial, famille, prud'hommes, droit des sociétés*), d'une juridiction (*TJ Bordeaux*) et d'une issue (*favorable, défavorable, transaction*).
2. **Priorisation facilitée** : l'extrait confirme la prédominance des contentieux cibles (recouvrement et baux commerciaux représentent plus de 50 % des affaires), ce qui valide le périmètre initial restreint convenu avec Maître Devalle.

---

## 4. Risques et conformité

**Usage réel (2-3 lignes) :**  
L'assistant est utilisé **exclusivement en interne** par les assistantes juridiques (pour préparer les projets de courriers) et les 12 avocats (pour retrouver les décisions passées du cabinet et sourcer leurs arguments). L'outil propose des brouillons et des extraits référencés : **il ne prend aucune décision, n'envoie aucun acte et ne conseille aucun client directement**. L'avocat conserve l'obligation déontologique de relire, corriger, valider et signer chaque acte.

**Qualification AI Act :**  
- **Niveau retenu : Système sans obligation spécifique (hors pratiques interdites et hors haut risque).**  
- **Justification raisonnée :** L'Annexe III point 8 (administration de la justice) ne vise que les systèmes d'IA utilisés par une **autorité judiciaire** pour assister l'interprétation des faits ou du droit, ce qui n'est pas le cas d'un cabinet libéral privé. L'outil n'interagit pas non plus avec les justiciables ou le grand public (l'article 50 sur les obligations de transparence des chatbots grand public ne s'applique donc pas). Enfin, le système n'effectue aucun profilage d'individus.  
- **Condition de bascule vers le Haut Risque ou Transparence :** Le système basculerait sous l'article 50 (transparence) si l'assistant était déployé sur le site web du cabinet pour dialoguer directement avec les clients (projet d'associé expressément écarté), ou sous l'Annexe III s'il était utilisé pour évaluer la performance individuelle des collaborateurs ou automatiser des décisions juridictionnelles.

**RGPD :**  
- **Base légale retenue et justifiée :** **Intérêt légitime** (art. 6 §1 f du RGPD) pour l'amélioration de l'organisation interne du cabinet et l'aide à la gestion documentaire de ses dossiers, combiné à l'**exécution du mandat/contrat de prestation juridique** (art. 6 §1 b) pour le traitement des pièces des dossiers confiés par les clients.  
- **Profilage :** Aucun profilage ni notation d'individus ou de salariés n'est réalisé par le système.  
- **Article 22 du RGPD (décision exclusivement automatisée produisant des effets juridiques) :** **Non applicable**. Deux conditions cumulatives font défaut : l'avocat relit et valide obligatoirement chaque acte (décision non exclusivement automatisée, boucle humaine obligatoire) et l'outil n'émet aucun acte juridique autonome.

### Tableau des risques (éthique, métier, conformité)

| Risque (éthique, métier, conformité) | 🔴/🟠/🟡 | Obligation ou raison | Traitement dans l'architecture |
|---|---|---|---|
| **Violation du secret professionnel de l'avocat** | 🔴 Rouge | Obligation d'ordre public (loi du 31/12/1971 art. 66-5 + déontologie Barreau). Sanctions disciplinaires et pénales directes. | **Hébergement souverain étanche certifié** (ou serveur on-premise) ; interdiction formelle de transit vers des API tierces non conformes ; chiffrement des données au repos et en transit. |
| **Hallucination juridique ou fausse jurisprudence** | 🔴 Rouge | Responsabilité civile professionnelle (RCP) de l'avocat engagée ; risque de sanctions judiciaires pour fausse citation (jurisprudence inventée). | **Architecture RAG avec ancrage strict (Grounding)** : le modèle n'a pas le droit de citer une source hors du corpus injecté ; chaque citation génère un lien direct et cliquable vers le PDF d'origine. |
| **Fuite de données personnelles de clients/justiciables (RGPD)** | 🔴 Rouge | Art. 32 RGPD (sécurité des traitements de données sensibles et judiciaires). | Module de **pseudonymisation / masquage automatique des PII** (noms, adresses, coordonnées bancaires) avant transmission au moteur sémantique. |
| **Obsolescence de la règle de droit citée** | 🟠 Orange | Risque d'erreur de conseil si une décision interne de 2012 applique un texte abrogé. | Filtrage temporel dans les métadonnées et alerte visuelle de date dans l'interface invitant l'avocat à vérifier la validité actuelle sur sa base en ligne. |
| **Dépendance ou sur-confiance des assistantes (automation bias)** | 🟡 Jaune | Risque de validation machinale d'un courrier sans relecture approfondie. | Garde-fou ergonomique imposant une étape explicite de relecture et signature personnelle de l'avocat responsable. |

### Sécurité du modèle — Menaces et robustesse (selon exposition de l'architecture)

*L'architecture étant un outil interne accessible uniquement aux 12 avocats et assistantes via authentification, la surface d'attaque est circonscrite (pas d'API publique ouverte).*

| Menace | Plausibilité sur CE cas | Mitigation proposée | Risque résiduel |
|---|---|---|---|
| **Injection indirecte de prompt (Indirect Prompt Injection)** | 🟠 Plausible (via pièces adverses indexées) | Des documents externes ou courriers de parties adverses numérisés et indexés pourraient contenir des instructions malveillantes dissimulées visant à fausser la réponse du modèle. | **Séparation stricte instructions / données** dans le prompt système, filtrage/assainissement textuel (sanitization) des documents ingérés avant vectorisation. | Document adverse très sophistiqué altérant la forme du résumé sans toutefois court-circuiter la relecture humaine. |
| **Fuite de données confidentielles via requêtes (Data Leakage)** | 🟠 Plausible (en cas d'usage d'API cloud non étanche) | Risque de réutilisation des courriers ou requêtes pour réentraîner un modèle externe public. | **Modèle open-source souverain hébergé localement ou sur infrastructure cloud qualifiée SecNumCloud** avec engagement contractuel de non-rétention des données. | Compromission de l'infrastructure réseau locale du cabinet (géré par PRA/antivirus). |
| **Empoisonnement du jeu de données (Data Poisoning)** | 🟡 Faible | Le corpus de jurisprudence est un fonds fermé validé par le cabinet (seules les décisions réelles du cabinet sont intégrées). | Processus d'ingestion sécurisé : validation des nouveaux documents et contrôle d'accès en écriture au registre documentaire. | Erreur humaine d'enregistrement d'une mauvaise décision dans le registre. |
| **Attaque contradictoire (Adversarial Examples) / Evasion** | ⚪ Sans objet | Pas d'attaquant externe cherchant à classifier une entrée à la volée. Système d'aide documentaire interne. | Écarté : pas d'exposition d'inférence publique. | Aucun. |

---

## 5. Architecture cible et sobriété — mini-cours `05`
_Renvoi vers `schema_archi_cible.md` pour le diagramme complet Mermaid (composants : Ingestion/OCR, Base vectorielle & métadonnées, Module de pseudonymisation, Moteur RAG & LLM souverain, Interface métier / plugin Word)._

**Sobriété argumentée (LLM retenu ou refusé) :**  
Pour ce projet, **un modèle de fondation propriétaire géant américain (ex. GPT-4) est formellement refusé** en raison de l'interdit déontologique de fuite des données (secret professionnel), du coût récurrent imprévisible au token et de son surdimensionnement écologique.  
Nous retenons une approche frugale et souveraine : **un modèle compact open-source spécialisé (ex. Mistral 7B / Llama 8B) déployé en local sur le serveur du cabinet ou hébergé sur un cloud souverain français**, couplé à une base vectorielle légère (ex. ChromaDB/Qdrant) et à un filtrage préalable sur métadonnées SQL/CSV. Ce choix garantit la stricte confidentialité, respecte l'enveloppe de 15 000 € de build et limite le coût récurrent à moins de 200 €/mois.

---

## 6. Indicateurs, seuils, questions ouvertes — mini-cours `03`

| Indicateur | Cible | Seuil d'acceptabilité | Comment on le mesure |
|---|---|---|---|
| **Gain de temps quotidien par avocat** | **1 heure / jour / avocat** (soit 12 h/jour cabinet) | ≥ 45 minutes / jour / avocat | Enquête déclarative mensuelle + chronométrage comparatif sur la préparation des dossiers types. |
| **Temps de recherche d'une décision interne** | **< 1 minute** (vs 30 minutes actuellement) | < 3 minutes | Horodatage logs système entre la soumission de la requête et la consultation de la décision pertinente. |
| **Précision et fidélité des sources citées** | **100 % des sources vérifiables et exactes** | 100 % (0 tolérance d'hallucination) | Audit aléatoire par les associés sur 50 requêtes mensuelles : conformité du lien vers le PDF d'origine. |
| **Taux d'adoption par les équipes** | **> 85 % des courriers cibles pré-rédigés via l'outil** | ≥ 70 % après 3 mois | Statistiques d'utilisation : volume mensuel de courriers initiés via l'assistant rapporté au volume total. |
| **Incidents de secret professionnel / fuites** | **0 incident** | **0 incident (seuil absolu)** | Audit continu des flux de données et journalisation des accès. |

### Prochaines étapes (3 jalons clés)
1. **Mois 1-2 : POC ciblé sur un corpus restreint** (Recouvrement & baux commerciaux) sur 200 décisions avec test d'ingestion OCR et validation de l'interface de recherche.
2. **Mois 3-4 : Intégration du module de génération de courriers et sécurisation** (pseudonymisation, ancrage strict RAG, déploiement sur infrastructure souveraine).
3. **Mois 5-6 : Phase pilote en cabinet** avec 3 avocats et les assistantes, ajustements ergonomiques, formation déontologique et déploiement général aux 12 avocats.

### Questions ouvertes restant à clarifier avec le client (reprises de `notes_entretien.md` §3)
1. **Qualité exacte de l'OCR sur les archives anciennes (scans papier)** : Quel est le pourcentage exact de scans papier non lisibles, et faut-il prévoir une prestation de numérisation/OCRisation professionnelle dans les 15 000 € ou se concentrer dans un premier temps sur les 5 dernières années déjà numérisées ?
2. **Spécifications techniques du serveur local** : Quel est le système d'exploitation et la capacité de stockage/calcul du serveur physique au cabinet pour arbitrer entre un hébergement local pur ou une instance cloud souveraine managée (ex. OVHcloud / Scaleway SecNumCloud) ?
3. **Gouvernance de mise à jour du registre** : Quel collaborateur sera désigné pour maintenir à jour le registre CSV/SQL des décisions au fur et à mesure des nouveaux jugements rendus par le TJ de Bordeaux ?
