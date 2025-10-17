# template.plan

# Plan technique

**Version** : v1.0

**Date** : YYYY-MM-DD

**Auteur / Agent** : Agent Plan

---

## 1. Contexte & prérequis

- Bref rappel de la **spécification** concernée (fonctionnalité / module).
- Contraintes / points issus de la constitution ou du contexte général à respecter.
- Technologies imposées / stack préférée / choix déjà faits.
- Hypothèses techniques (base de données, APIs existantes, services externes, limites).

## 2. Vision d’ensemble de l’architecture

- Diagramme (conceptuel) ou description textuelle de l’architecture globale du module / du système (couches, composants, microservices ou monolithe, communication interne).
- Modules ou sous-composants proposés.
- Flux de données majeurs / échanges entre composants / frontières.

## 3. Décomposition en composants / sous-modules

Pour chaque composant / sous-module :

- Nom / identifiant
- Rôle / responsabilité
- Interfaces / API internes
- Dépendances vers d’autres composants
- Contraintes spécifiques (ex : performance, isolation, accès)

## 4. Modèles de données & schémas

- Entités / objets / types de données — schéma (ex : tables, JSON, classes)
- Relations entre entités
- Contraintes d’intégrité, clés, index
- Adaptations pour les performances (caching, partition, verrous)

## 5. API externes & intégrations

- Endpoints / services externes à consommer
- Protocoles / formats (HTTP, gRPC, événementiel, etc.)
- Contrats attendus (en entrée, en sortie, erreurs)
- Sécurité des appels (authentification, autorisation, chiffrement)
- Stratégies de fallback / retry / résilience

## 6. Flux, orchestrations & workflows internes

- Scénarios / flux d’appel (succession de modules, états)
- Logique d’orchestration (séquentiel, parallèle, événementielle)
- Gestion des transactions / cohérence / rollback
- Notifications, événements internes

## 7. Non-fonctionnel & contraintes techniques

- Performance (latence, débit)
- Scalabilité, montée en charge
- Disponibilité, tolérance aux pannes, reprise / redondance
- Sécurité (contrôles, validation, audit, logs)
- Monitoring, observabilité, métriques
- Extensibilité, modularité, évolutivité
- Contraintes d’infrastructure (ressources, quotas, limites)

## 8. Plan de migration / coexistence (si module dans un système existant)

- Stratégie d’intégration / coexistence avec le système actuel
- Migration des données (si besoin)
- Backward compatibility / versions
- Stratégie de mise en production progressive / feature flag

## 9. Risques techniques & points de vigilance

- Choix technologiques risqués / incertitudes
- Verrous (goulots) possibles
- Hypothèses à valider
- Dépendances externes critiques

## 10. Plan de découpage / phasage / roadmap technique

- Découpage en étapes / versions / livrables
- Priorisation des sous-modules
- Estimations / charges (si possible)
- Chronologie / jalons

## 11. Instruction à l’agent Tasks

> À la fin du document, donner une consigne claire à l’agent Tasks pour transformer ce plan en tâches actionnables :
> 
> 
> quelles priorités respecter, comment découper les composants, quelles contraintes techniques à prendre en compte, etc.
>