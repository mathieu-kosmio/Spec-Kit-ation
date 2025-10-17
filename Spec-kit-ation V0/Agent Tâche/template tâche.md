# template.tâche

# Génération des tâches

**Version** : v1.0

**Date** : YYYY-MM-DD

**Auteur / Agent** : Agent Tâches

---

## 1. Contexte & références

- Référence à la **spécification** concernée (ID, nom, version)
- Référence au **plan technique** associé
- Contraintes ou éléments critiques à garder à l’esprit (non-fonctionnels, dépendances, priorités)

## 2. Principes de découpage & critères de granularité

- Critères retenus pour découper les tâches (ex : cohérence, testabilité, atomicité)
- Limites / seuils (durée max, complexité max)
- Règles de nommage, structuration des tâches

## 3. Liste des tâches / tickets

Pour chaque tâche :

| ID | Titre | Description / détail | Module / composant cible | Dépendances | Priorité | Estimation (temps / effort) | Critères d’acceptation / métriques de réussite |

## 4. Regroupement & hiérarchisation

- Lots / groupes de tâches (par module, par version, par priorité)
- Ordonnancement recommandé (séquence de dépendances, parallèle possible)
- Milestones / jalons intermédiaires

## 5. Non-fonctionnel & critères transverses

- Tests requis (unitaires, intégration, end-to-end)
- Qualité (performance, sécurité, robustesse)
- Normes ou principes à respecter (code style, documentation, logs)
- Monitoring, observabilité liées aux tâches

## 6. Risques & incertitudes dans le découpage

- Tâches à haut risque ou incertaines
- Points où des investigations / clarifications sont nécessaires
- Hypothèses utilisées pour l’estimation

## 7. Instruction à l’agent Implémentation (ou Export / Implement)

> À la fin, fournir une consigne claire :
> 
> 
> comment l’agent suivant (Implémentation ou Export) doit consommer ces tâches pour générer du code ou des artefacts (par ex., itérer, vérifier, exécuter, produire les fichiers, etc.).
> 

---