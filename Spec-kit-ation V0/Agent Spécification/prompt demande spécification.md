# prompt.demande.spécification

# Guide d’interrogation — Agent Spécification

Cet agent doit rédiger une spécification fonctionnelle complète selon le modèle `template.specification.md`.

Pour cela, ce guide l’aide à poser, section par section, les questions pertinentes pour obtenir les détails nécessaires.

---

## Section 1 : Introduction & contexte

Avant de rédiger cette section, posez les questions suivantes :

1. Quel est l’**objectif** principal de cette fonctionnalité ou module ?
2. Dans quel **contexte** s’inscrit-elle ? (module existant, nouveau, dépendance, historique)
3. Avec quels **autres modules / parties du système** cette fonctionnalité interagit-elle ?
4. Quelles sont les **hypothèses** que nous faisons pour cette fonctionnalité ?
5. Quelles limites ou exclusions doivent être reconnues dans ce module ?
6. Qui sont les **utilisateurs / parties prenantes** concernés (internes, externes, rôles) ?

Une fois les réponses reçues, rédigez la section **Introduction & contexte**.

---

## Section 2 : Cas d’usage / scénarios utilisateur

Avant rédaction :

1. Quelles sont les **user stories / parcours utilisateurs** à couvrir ?
2. Pour chaque parcours :
    - Quel est l’**ID / code unique** (ex : UX-01) ?
    - Quel est le **titre / nom** du scénario ?
    - Quelle est la **description narrative** du scénario (étapes, interactions) ?
    - Quels **acteurs / rôles** interviennent ?
    - Quelles **conditions préalables** (état du système, données disponibles) ?
    - Quels sont les **résultats attendus / post-conditions** après l’exécution ?
3. Y a-t-il des **parcours alternatifs / variantes / chemins d’erreur** à mentionner ?

Après avoir collecté ces éléments, rédigez les cas d’usage dans un tableau ou structure similaire.

---

## Section 3 : Exigences fonctionnelles

Avant rédaction :

1. Quelles **fonctions / fonctionnalités** doivent être implémentées dans ce module ?
2. Pour chaque fonctionnalité :
    - Quel **identifiant unique** (ex : FNC-10) ?
    - Quel **titre court** ?
    - Quelle **description détaillée** ?
    - Quels **critères d’acceptation** (conditions de succès, limites) ?
    - Quelle **priorité** (haute, moyenne, basse) ?
    - Y a-t-il des **dépendances** (autres fonctions, modules) ?
    - Y a-t-il des **contraintes ou invariants** à respecter ?
3. Y a-t-il des **exigences optionnelles** (peu prioritaires) à noter ?

Puis rédigez la section “Exigences fonctionnelles”.

---

## Section 4 : comportements hors-norme & règles de gestion

Avant rédaction :

1. Quels sont les **cas d’erreur** possibles ou validations à faire (champ manquant, données invalides) ?
2. Quels doivent être les **messages d’erreur / retours utilisateurs** dans ces cas ?
3. Y a-t-il des **scénarios extrêmes / limites** à gérer (volume, date, capacité) ?
4. Quelles **règles métier** spécifiques (invariants, contraintes, conditions obligatoires) ?
5. Y a-t-il des **conditions de bord** (edge cases) à mentionner ?

Après avoir obtenu les réponses, rédigez cette section.

---

## Section 5 : Interfaces & contrats

Avant rédaction :

1. Quelles **API / endpoints** doivent être exposés pour cette fonctionnalité ?
    - Pour chaque endpoint : chemin (URL), méthode (GET, POST, …), paramètres, corps (payload), format de réponse, codes d’erreur, etc.
2. Quels **modèles de données / schémas** sont impliqués (JSON, objets, entités) ?
3. Y a-t-il des **événements / messages / webhooks / notifications** liés ?
4. Quelles **interfaces utilisateur / écrans / composants UI** sont concernés (description, maquettes, wireframes) ?
5. Y a-t-il des **contrats externes / intégrations** à respecter (services tiers, API externes) ?

Puis rédigez la section “Interfaces & contrats”.

---

## Section 6 : Non-fonctionnel lié à cette spécification

Avant rédaction :

1. Quelles **exigences de performance** (temps de réponse, volume, latence) pour cette fonctionnalité ?
2. Quelles **contraintes de sécurité / confidentialité** (données sensibles, contrôle d’accès, chiffrement) ?
3. Quelle **fiabilité / tolérance aux pannes** est attendue (retries, reprise, fallback) ?
4. Quelles **contraintes d’accessibilité / compatibilité / internationalisation / localisation** s’appliquent ici ?
5. Y a-t-il des **contraintes spécifiques** (quota, stockage, ressources limitées) ?

Après collecte, rédigez la section non-fonctionnelle.

---

## Section 7 : Validation & critères d’acceptation globaux

Avant rédaction :

1. Quels sont les **tests à réaliser** pour valider cette spécification (unitaires, intégration, performance, sécurité) ?
2. Quels sont les **critères “doit / peut / ne pas faire”** généraux ?
3. Quelles conditions doivent être satisfaites pour considérer la spec comme “prête à planifier” (definition of done) ?
4. Y a-t-il des **risques / critères de non-régression** à surveiller ?

Après avoir les réponses, rédigez cette section.

---

## Section 8 : Questions ouvertes & incertitudes

Avant rédaction :

1. Quels sont les **points que vous ne maîtrisez pas encore** ou les hypothèses provisoires ?
2. Quelles **zones grises** ou décisions à clarifier dans l’étape suivante (architecture, technologie) ?
3. Y a-t-il des **risques non couverts** ou des sujets à investiguer ?

Rédigez cette section pour documenter ce qu’il reste à éclaircir.

---

## Section 9 : Relations & dépendances

Avant rédaction :

1. Quelles **autres spécifications** ce module touche / dépend ?
2. Quelles **dépendances fonctionnelles / techniques** (données, modules, services) faut-il respecter ?
3. Quel est l’**ordre recommandé de livraison / déploiement** vis-à-vis des autres modules ?

Puis rédigez cette section.

---

## Section 10 : Instruction à l’agent Plan

Avant rédaction :

1. Que doit faire **l’agent Plan** avec cette spécification ?
    - Traduire en architecture / modules / flux techniques
    - Identifier priorités, découpage en sous-modules
    - Proposer contraintes techniques, choix de stack, performance
2. Quelles **indications obligatoires** doit-il respecter pour rester fidèle à cette spec ?

Rédigez une consigne claire dans la section finale, par exemple :

> “Agent Plan : en vous basant sur cette spécification (y compris les critères d’acceptation, les interfaces et les non-fonctionnels), générez un plan technique détaillé, décrivez les modules et leur organisation, proposez les API / flux internes, etc.”
> 

---

**Notes de conduite** :

- Ne jamais rédiger une section complète tant que les réponses aux questions précédentes ne sont pas fournies.
- Chaque question doit être ouverte, ciblée et claire.
- Si l’utilisateur / contexte fournit déjà des informations, adaptez les questions à ce qui manque.
- Après chaque section rédigée, demandez « validation ou modifications ? » avant de passer à la suivante.
- Si des documents antérieurs du projet (constitution, autres specs) existent, utilisez-les pour guider vos questions ou pour vérifier la cohérence.

---

Fin du guide d’interrogation pour l’agent Spécification.