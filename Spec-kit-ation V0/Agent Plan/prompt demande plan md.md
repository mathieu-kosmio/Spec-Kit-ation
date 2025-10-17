# prompt.demande.plan.md

# Guide d’interrogation — Agent Plan

Ce document sert à guider l’agent Plan dans sa phase de collecte d’information, section par section, avant de produire le plan technique complet selon `template.plan.md`.

---

## Section 1 : Contexte & prérequis

Avant de rédiger cette section :

1. Quelle est la **spécification / module / fonctionnalité** à planifier (référence du document spec) ?
2. Quels sont les **contraintes déjà définies** dans la constitution ou le contexte global (stack, choix imposés, limites) ?
3. Y a-t-il des **technologies déjà choisies** ou favoritisme (langages, frameworks, bases de données, services externes) ?
4. Quels composants ou services externes doivent être considérés comme **prérequis** (APIs externes, services déjà en place) ?
5. Quelles **hypothèses techniques** (capacité, latence acceptable, volume maxi attendu) devons-nous considérer ?

---

## Section 2 : Vision d’ensemble de l’architecture

Avant rédaction :

1. Quelle est la **vision souhaitée** du module (monolithique, microservices, event-driven, modulaire) ?
2. Quels sont les **composants majeurs** que vous envisagez (ex : service A, module B, bus d’événements) ?
3. Quels **flux de données majeurs / dépendances externes** doivent être représentés ?
4. Y a-t-il des contraintes ou choix concernant la **communication entre composants** (synchrone, asynchrone, file, broker) ?
5. Quels **frontières / limites de module** doivent être clairement marquées (zones de découplage) ?

---

## Section 3 : Décomposition en composants / sous-modules

Avant rédaction :

1. Pour chaque composant ou sous-module envisagé :
    - Quel **nom / identifiant** ?
    - Quelle est sa **responsabilité principale** ?
    - Quelles **interfaces / API internes** expose-t-il ?
    - Quelles **dépendances vers d’autres composants** ?
    - Y a-t-il des **contraintes techniques spécifiques** (performance, isolement) ?
2. Y a-t-il des composants que vous **ne souhaitez surtout pas mélanger / regrouper** pour des raisons d’isolation, de sécurité ou de scalabilité ?

---

## Section 4 : Modèles de données & schémas

Avant rédaction :

1. Quelles **entités / objets / tables / documents** sont impliqués dans cette fonctionnalité ?
2. Pour chaque entité :
    - Quelles **propriétés / champs** principales (type, contraintes) ?
    - Y a-t-il des **relations** (1-à-n, n-à-n, héritage) à modéliser ?
    - Quelles contraintes d’intégrité (unicité, nullité, foreign key) ?
    - Y a-t-il des besoins liés à la **performance** (indexation, cache, partitionnement) ?

---

## Section 5 : API externes & intégrations

Avant rédaction :

1. Quelles **APIs / services externes** votre module doit consommer ou exposer ?
2. Pour chaque API :
    - Quel **endpoint / méthode** (URL, HTTP verb, etc.) ?
    - Quels **paramètres en entrée** (URL, requête, corps) ?
    - Quel **schéma de réponse** / format attendu ?
    - Quels **codes d’erreur / statuts** peuvent survenir ?
    - Quels **formats / protocoles** (JSON, XML, gRPC, event, etc.) ?
3. Y a-t-il des **exigences de sécurité / authentification** dans ces appels externes (token, OAuth, chiffrement) ?
4. Faut-il prévoir des **stratégies de fallback / retry / circuit breaker** en cas d’échec ?

---

## Section 6 : Flux, orchestrations & workflows internes

Avant rédaction :

1. Quels **scénarios / flux internes** le module doit orchestrer (ex : validation, appel à sous-services, transactions) ?
2. Quelle logique d’**orchestration** (séquentielle, parallèle, événementielle, orchestrateur / sagas) ?
3. Y a-t-il des **transactions distribuées / contraintes de cohérence** à gérer (rollback, compensation) ?
4. Quelles actions / notifications internes / événements doivent être envoyés au cours du flux ?
5. Y a-t-il des contraintes de latence / délais ou de temporisation à intégrer ?

---

## Section 7 : Non-fonctionnel & contraintes techniques

Avant rédaction :

1. Quels **objectifs de performance** (latence maximale, débit, charge cible) ?
2. Quelles **contraintes de sécurité / audit / logs / traçabilité** doivent s’appliquer ?
3. Quels niveaux de **disponibilité / tolérance aux pannes** sont requis (failover, redondance) ?
4. Quelles **pratiques de monitoring / observabilité / métriques** envisagées ?
5. Y a-t-il des **contraintes d’infrastructure** (CPU, RAM, stockage, limites réseau, quota) ?
6. Quelles **exigences d’évolutivité / modularité** pour les futures extensions ?

---

## Section 8 : Plan de migration / coexistence

Avant rédaction :

1. Si ce module s’intègre à un système existant : comment **coexister / migrer** ?
2. Quelle **stratégie de migration des données** envisagée (par étapes, conversion, script) ?
3. Comment assurer **la compatibilité ascendante / rétrocompatibilité** avec les anciennes versions ?
4. Quelle approche de **déploiement progressif / feature flag** peut être utilisée ?

---

## Section 9 : Risques techniques & points de vigilance

Avant rédaction :

1. Quels choix technologiques sont **incertains / expérimentaux** dans ce plan ?
2. Quelles sont les **dépendances externes critiques / à risque** ?
3. Y a-t-il des **verrous / goulots potentiels** identifiés (I/O, réseau, base) ?
4. Quelles hypothèses nécessitent une **validation future** ?
5. Quels **plans de mitigation / alternatives** peut-on prévoir ?

---

## Section 10 : Plan de découpage / phasage / roadmap technique

Avant rédaction :

1. Comment **découper le plan** en **étapes / lots / versions** ?
2. Pour chaque lot / version : quels sous-modules ou fonctionnalités livrer ?
3. Quelles sont les **priorités** ?
4. Si possible, quelles **estimations / charges / durées** pour chaque lot ?
5. Quel est le **calendrier / jalons** proposé ?

---

## Section 11 : Instruction à l’agent Tasks

Avant rédaction :

1. Que doit faire l’agent Tasks avec ce plan ?
    - Transformer chaque composant / lot en tâches actionnables
    - Respecter les priorités et contraintes techniques
    - Prendre en compte les critères non fonctionnels, les dépendances, la roadmap
2. Quelles instructions *obligatoires* l’agent Tasks doit respecter pour rester fidèle au plan ?

Rédigez une consigne claire, par exemple :

> “Agent Tasks : à partir de ce plan, générez les tâches / user stories / tickets pour chaque lot / sous-module, respectant les priorités, dépendances, contraintes et critères non fonctionnels. Votre sortie doit être structurée (JSON / Markdown) et inclure estimation, dépendances et priorité.”
> 

---

**Notes de conduite pour l’agent Plan** :

- Ne pas rédiger toute la section sans d’abord obtenir les réponses aux questions correspondantes.
- Réutiliser le contexte / documents antérieurs quand disponibles.
- Après chaque section rédigée, demander à l’utilisateur s’il souhaite des modifications ou clarifications.
- Respect strict de l’ordre des sections.
- Chacune des questions doit être claire, non ambigüe et ouverte.