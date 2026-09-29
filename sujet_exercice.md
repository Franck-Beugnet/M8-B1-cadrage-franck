Situation professionnelle
Mardi 9h15, dernière mission FastIA avant la certification. Karim poste sur Discord : « Trois prospects cette semaine. Chacun veut faire de l'IA sans savoir ce qu'il veut vraiment. Je vous ai staffés : chacun reçoit en MP son client, son briefing et son code d'accès au rendez-vous. Le client est occupé : il vous accorde 45 minutes et 12 réponses. Préparez vos questions, il ne répond qu'à ce qu'on lui demande, et une question vague obtient une réponse vague. Pas de code aujourd'hui. Cadrage de 3 pages déposé à 15h30, lisible par le client. Ensuite, vous retrouvez les collègues staffés sur le même client pour la conception (M8-B2). Et on note la sobriété. »

Le cas :

Cabinet Maître Devalle (juridique PME, courriers types + recherche de jurisprudence) ;

🎯 Objectifs pédagogiques
Préparer et conduire un entretien de découverte sous contrainte (12 réponses) : prioriser les questions structurantes, distinguer demande exprimée et besoin réel, relancer quand la réponse est floue.
Identifier les données existantes (exploitables) vs à acquérir (manquantes), et en estimer la qualité, y compris sur un extrait réel si tu as pensé à le demander.
Définir des indicateurs business chiffrés et des seuils acceptables.
Identifier les risques éthiques et réglementaires dès le cadrage : qualifier le niveau de risque AI Act à partir de l'usage réel, proposer et justifier la base légale RGPD, repérer le profilage, et les risques métier (secret professionnel, surveillance des salariés, sécurité industrielle selon le cas).
Concevoir une architecture cible schématisée (Mermaid), sans coder, et l'ajuster quand le client change une contrainte.
Rédiger un document de cadrage de 3 pages lisible par un décideur métier.
🚫 Ce que tu n'as PAS à faire (et c'est volontaire)
Tu n'as PAS à coder. Pas une ligne, même pour regarder l'extrait de données : un tableur suffit.
Tu n'as PAS à prototyper un POC. Le schéma archi suffit.
Tu n'as PAS à choisir la stack précise. Tu donnes des familles — les arbitrages détaillés sont en M8-B2.
Tu n'as PAS à tout savoir. Ce que le client n'a pas dit va dans les questions ouvertes, pas dans des hypothèses cachées.
Tu n'as PAS à recommander un LLM par défaut. 2 cas sur 3 (tickets RH, maintenance) sont typiquement ML classique. La sobriété est valorisée.
🏗️ Architecture du livrable
Repo perso M8-B1-cadrage-prenom : notes_entretien.md (12 questions préparées et priorisées + trace dit / interprété + boussole des informations obtenues), schema_archi_cible.md (Mermaid), et le livrable principal document_cadrage.md (3 pages, 6 sections : synthèse, besoin, données, risques et conformité, architecture et sobriété, indicateurs et questions ouvertes). Le rendez-vous client est journalisé : la formatrice voit les questions posées.

Tâches macro
(1) 9h15-10h00 : prise de mission + préparation de 12 questions (+ 3 de réserve) classées par priorité dans notes_entretien.md — besoin réel, processus actuel, données (volume, qualité, accès à un extrait), données personnelles, critère de succès chiffré, coût d'une erreur, utilisateurs, SI et hébergement, budget et délai. Une question à la fois.

(2) 10h00-10h45 : entretien avec le client en ligne, relances quand une réponse surprend, notes dit / interprété. Après chaque réponse, mettre à jour la boussole de notes_entretien.md (information obtenue, partielle ou encore à obtenir) : c'est elle qui dit quelle information aller chercher avec les questions restantes. Si le client transmet un fichier, le télécharger dans le repo.

(3) 10h45-12h30 : cadrage directement dans document_cadrage.md — besoin reformulé, données existantes et à acquérir, risques et conformité (usage réel, qualification AI Act raisonnée avec condition de bascule, base légale RGPD justifiée, sécurité du modèle).

(4) 13h30-14h30 : architecture cible Mermaid (au moins 4 composants) + sobriété argumentée en 3 lignes, puis 3-5 KPI chiffrés + seuils + questions ouvertes.

(5) 14h30-15h30 : imprévu client (identifier ce qu'il change et mettre à jour les sections concernées), synthèse exécutive rédigée en dernier, relecture persona client, dépôt 15h30.

🆘 En cas de blocage
Mini-cours du pack (entretien, cartographie, indicateurs business, risques + AI Act, schéma archi, document de cadrage, sécurité). Garde-fou : pas de code, sobriété valorisée, 3 pages max.

Critères de performance

1. Le questionnement est préparé et priorisé : les 12 questions couvrent besoin, données, conformité et critère de succès ; le journal du rendez-vous montre des relances pertinentes.

2. Le besoin métier est reformulé (pas recopié de la demande exprimée) — preuve d'écoute active.

3. La cartographie distingue données existantes et à acquérir, avec estimation de qualité par source.

4. Les risques sont hiérarchisés (rouge/orange/jaune), associés à une obligation ou une raison métier, et les rouges ont un traitement dans l'architecture. La qualification AI Act est raisonnée (usage réel, cas du texte ou pourquoi aucun, condition de bascule) et la base légale RGPD est proposée et justifiée, pas posée d'office. Au moins 2 menaces de sécurité plausibles avec mitigation et risque résiduel.

5. Les indicateurs business sont chiffrés avec des seuils : pas améliorer le tri mais passer de 60 min/jour à 10 min/jour avec plus de 85 % des tickets dans la bonne équipe.

6. L'architecture cible est schématisée en Mermaid avec au moins 4 composants et leurs flux ; la sobriété est argumentée en 3 lignes (LLM retenu ou rejeté).

7. L'imprévu client de 14h30 est intégré : les sections concernées sont mises à jour et la synthèse dit ce qui a changé.

8. Le document tient en 3 pages et reste lisible par le persona client — pas un seul terme technique non défini.