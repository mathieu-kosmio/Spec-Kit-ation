# Agent Plan

## Agent Plan — Description & Manuel d’utilisation

### 1. Description de l’agent

### Nom

**Agent Plan** (ou Agent Planification)

### Rôle & mission

L’agent Plan est chargé de traduire la **spécification fonctionnelle validée** en un plan technique clair et détaillé. Ce plan décrit l’architecture, les composants, les modules, les flux, les interfaces techniques, les contraintes non fonctionnelles, le phasage et les risques. Il sert de pont entre le monde métier (spécification) et l’implémentation (tâches / développement).

### Entrées & sources d’information

- La **spécification** produite par l’agent Spécification (et idéalement clarifiée via l’agent Clarification).
- La **constitution** du projet (les contraintes, principes, priorités non fonctionnelles).
- Documents contextuels existants (diagrammes, systèmes antérieurs, APIs existantes, contraintes techniques déjà identifiées).
- Le modèle `template.plan.md` qui définit la structure du plan.
- Le guide d’interrogation `prompt.demande.plan.md` qui oriente les questions pour collecter les informations manquantes.

### Sortie attendue

- Un fichier `plan.md` (ou plusieurs si tu découpes par modules) structuré selon `template.plan.md`, avec les sections :
    1. Contexte & prérequis
    2. Vision d’ensemble de l’architecture
    3. Décomposition en composants / sous-modules
    4. Modèles de données & schémas
    5. API externes & intégrations
    6. Flux, orchestrations & workflows internes
    7. Non-fonctionnel & contraintes techniques
    8. Plan de migration / coexistence
    9. Risques techniques & points de vigilance
    10. Plan de découpage / phasage / roadmap technique
    11. Instruction à l’agent Tâches
- Le document est versionné (numéro de version, date) et enregistré dans le dossier du projet.
- Le plan est conçu pour être immédiatement exploitable par l’agent Tâches pour découper les tâches, et pour servir de guide d’implémentation.

---

### 2. Manuel d’utilisation

### 2.1 Quand utiliser l’agent Plan

Tu utilises l’agent Plan une fois que la spécification est validée (et clarifiée) — c’est l’étape après /Spécification (et /Clarification) et avant /Tâches. Pour chaque nouvelle spec ou modification significative, lance /Plan pour produire ou mettre à jour le plan technique.

### 2.2 Commande d’invocation

Tu invoques l’agent avec la commande :

```
/Plan

```

Le prompt maître du Plan (que tu as défini) déclenchera le processus de dialogue pour construire le plan section par section.

### 2.3 Étapes de fonctionnement

1. **Lecture du contexte & de la spécification**
    
    L’agent commence par analyser la spec (et, le cas échéant, les clarifications) et la constitution du projet pour comprendre les contraintes, exigences non fonctionnelles, limites techniques.
    
2. **Pose de questions initiales / de collecte**
    
    Pour chaque section du modèle (via `prompt.demande.plan.md`), l’agent te pose les bonnes questions pour compléter les zones manquantes (architecture préférée, composants envisagés, communication, flux, contraintes performance, migration, etc.).
    
3. **Rédaction section par section**
    - Il rédige d’abord **Contexte & prérequis**, puis **Vision d’ensemble**, ensuite la **décomposition** des composants, etc., dans l’ordre du modèle.
    - Il peut revenir poser des précisions supplémentaires si une section ne peut pas être complétée avec les données fournies.
    - Pour chaque section, il attend confirmation ou corrections avant de passer à la suivante.
4. **Validation & ajustement progressif**
    
    Après chaque section, l’agent présente ce qu’il a rédigé et demande :
    
    > “✅ Section X terminée. Voulez-vous modifier ou ajouter des précision(s) avant de passer à la section suivante ?”
    > 
    
    Tu peux corriger, ajouter, reformuler avant de poursuivre.
    
5. **Finalisation du plan**
    
    Une fois toutes les sections complétées et validées, l’agent compile le document complet `plan.md`, ajoute les métadonnées (version, date, agent), et rédige la **section 11** (instruction claire à l’agent Tâches).
    
    Il fournit également un **résumé des choix d’architecture**, des modules clés, des jalons et des risques majeurs.
    
    Enfin, il invite à télécharger / sauvegarder le plan dans le dossier projet dans le chat.
    

### 2.4 Bonnes pratiques & recommandations

- **Clarifier avant de planifier** : assure-toi que la spécification est suffisamment détaillée (via l’agent Clarification si nécessaire) avant de lancer /Plan.
- **Gardes les contraintes & principes de la constitution à l’esprit** : la planification ne doit pas violer les choix de constitution (sécurité, performance, modularité).
- **Découpage modulaire clair** : identifie des composants ou sous-modules cohérents, avec des responsabilités bien définies.
- **Traçabilité entre spec et plan** : pour chaque exigence, assure une correspondance (mapping) vers un ou plusieurs modules ou composants du plan.
- **Documenter les choix d’architecture** : justifie pourquoi tu choisis tel pattern, communication synchrone vs asynchrone, microservices vs monolithe, etc.
- **Mentionner les compromis / arbitrages** (ex : performance vs maintenabilité) dans la section “Risques / points de vigilance”.
- **Versionner le plan** : si le plan évolue, incrémente la version (v1.0 → v1.1) et documente les changements.
- **Alignement avec les tâches** : le plan doit être suffisamment précis pour que l’agent Tâches puisse découper sans ambiguïté.
- **Itérations & rétroactions** : après avoir produit un plan, tu peux lancer /Checklist ou /Analyse pour vérifier sa qualité ou cohérence avant de générer les tâches.

---

[template.plan](Agent%20Plan%2028dd2a1120b680df854aec0ff3b5ffcd/template%20plan%2028dd2a1120b680a1b366efccb676fea9.md) 

[prompt.demande.plan.md](Agent%20Plan%2028dd2a1120b680df854aec0ff3b5ffcd/prompt%20demande%20plan%20md%2028dd2a1120b68076b8d9f80b30856d33.md) 

[Prompt Agent](Agent%20Plan%2028dd2a1120b680df854aec0ff3b5ffcd/Prompt%20Agent%2028dd2a1120b68015b257cd09764c5482.md)