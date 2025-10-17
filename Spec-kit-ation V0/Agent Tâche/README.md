# Agent Tâche

## Agent Tâches — Description & Manuel d’utilisation

### 1. Description de l’agent

### Nom

**Agent Tâches** (ou Agent Tasks)

### Rôle & mission

L’agent Tâches est responsable de **transformer le plan technique validé** en une **liste de tâches actionnables**, claires et exploitables par les développeurs. Il structure le développement en “tickets” ou items indépendants, avec des critères de réussite, des estimations, des dépendances et un ordonnancement logique. L’idée est que chaque tâche soit suffisamment petite pour être implémentée, testée et validée de façon isolée, tout en restant tracée à la spec et au plan.

Ce rôle correspond à l’étape “Tasks” du pipeline Spec Kit — c’est l’agent qui « prend la spec + le plan et les découpe en morceaux de travail » ([The GitHub Blog](https://github.blog/ai-and-ml/generative-ai/spec-driven-development-with-ai-get-started-with-a-new-open-source-toolkit/?utm_source=chatgpt.com)).

### Entrées & sources d’information

- Le **plan technique** produit par l’agent Plan (document `plan.md` ou équivalent), incluant l’architecture, les modules, les composants, les flux, etc.
- La **spécification** (et éventuellement le document de clarification) pour comprendre les exigences, critères d’acceptation, comportements attendus.
- Le modèle `template.tâche.md` qui définit la structure attendue des tâches (titres, description, dépendances, estimation, etc.).
- Le guide d’interrogation `prompt.demande.tâche.md` qui fournit les questions à poser pour collecter les détails nécessaires.
- Les contraintes / priorités définies dans la constitution du projet (pour s’assurer que les tâches respectent les normes, performance, modularité, etc.).

### Sortie attendue

- Un fichier `tasks.md` (ou un ensemble de fichiers par module) contenant les tâches décrites selon `template.tâche.md`, avec les sections remplies :
    1. Contexte & références
    2. Principes de découpage & critères de granularité
    3. Liste des tâches / tickets
    4. Regroupement & hiérarchisation
    5. Non-fonctionnel & critères transverses
    6. Risques & incertitudes dans le découpage
    7. Instruction à l’agent suivant (Implémentation / Export)
- Chaque tâche contient : un identifiant unique, un titre, une description détaillée, le module / composant cible, les dépendances, la priorité, une estimation, les critères d’acceptation / métriques de réussite.
- Le document est versionné (version, date) et enregistré dans le dossier projet.

---

### 2. Manuel d’utilisation

### 2.1 Quand utiliser l’agent Tâches

- Dès que le plan technique (produit par l’agent Plan) est validé.
- Pour chaque nouvelle spécification / plan modifié / évolution, relance l’agent Tâches pour produire les nouveaux tickets.
- Avant de lancer l’implémentation, pour s’assurer que le travail est bien structuré et traçable.

### 2.2 Commande d’invocation

Utilise la commande suivante dans le chat :

```
/Tâches

```

Elle déclenche l’agent Tâches selon le prompt maître qui orchestre le processus de dialogue et de production.

### 2.3 Étapes de fonctionnement

1. **Lecture du plan & contexte**
    
    L’agent récupère le plan technique, la spécification, et les contraintes du projet (constitution) pour comprendre le périmètre du découpage.
    
2. **Pose de questions / collecte d’informations**
    
    Pour chaque section du template, l’agent pose les questions pertinentes (via `prompt.demande.tâche.md`) pour obtenir les détails manquants : critères de granularité, durée maximale, dépendances, priorités, restrictions non fonctionnelles, etc.
    
3. **Rédaction section par section**
    - Il commence par la section “Contexte & références” (référence du plan, de la spec).
    - Puis “Principes de découpage & critères de granularité” : comment il va découper (durée max, atomicité, séparation de responsabilité).
    - Ensuite “Liste des tâches / tickets” : il liste chaque tâche avec tous les champs (ID, titre, description, dépendances, estimation, critères).
    - Puis “Regroupement & hiérarchisation” pour organiser les tâches en lots / jalons / phases.
    - Puis “Non fonctionnel & critères transverses” pour indiquer les aspects non fonctionnels à respecter (tests, logs, performance).
    - Ensuite “Risques & incertitudes”, et enfin “Instruction à l’agent suivant (Implémentation / Export)”.
4. **Validation progressive**
    
    Après chaque section, l’agent affiche ce qu’il a rédigé et demande :
    
    > “✅ Section X terminée. Voulez-vous la modifier / compléter avant de passer à la section suivante ?”
    > 
    
    Tu peux apporter des corrections ou enrichissements avant de continuer.
    
5. **Finalisation du document**
    
    Une fois toutes les sections validées, l’agent compile le document final `tasks.md`, ajoute les métadonnées (version, date, agent), et la **section 7** : instruction claire à l’agent suivant (Implémentation / Export) sur la façon de consommer les tâches.
    
    Il fournit également un **résumé global** (nombre de tâches, phases, jalons, tâches critiques / risques).
    
    Enfin, il invite à télécharger / sauvegarder le fichier dans le dossier projet du chat.
    

### 2.4 Bonnes pratiques & recommandations

- **Définir une granularité raisonnable** : chaque tâche doit être réalisable en un bloc de temps raisonnable (quelques heures à 1-2 jours selon projet).
- **Ne pas mélanger responsabilités** : une tâche ne doit pas porter sur plusieurs modules ou domaines distincts si cela nuit à la clarté ou à l’indépendance.
- **Toujours inclure les critères d’acceptation** : cela permet de tester / valider facilement.
- **Identifier les dépendances explicitement** : cela évite des blocages imprévus lors de l’implémentation.
- **Prioriser & ordonner** les tâches selon les dépendances, les risques et les phases.
- **Inclure des tâches de spike / investigation** pour les zones incertaines (recherche, prototypage, validations techniques).
- **Propager les exigences non fonctionnelles** : chaque tâche doit respecter les contraintes (performance, sécurité, logs, normes).
- **Versionner les tâches / modifications** : si tu ajoutes ou modifie des tâches, incrémente la version (v1.1, v2.0) et documente les changements.
- **Relier chaque tâche à la spec / au plan** : grâce aux identifiants, tu peux tracer l’origine métier / technique de chaque tâche.
- **Réviser / valider manuellement** : même si l’agent propose les tâches, tu dois vérifier que rien n’est oublié ou mal attribué avant de passer à l’implémentation.

---

[template.tâche](Agent%20T%C3%A2che%2028dd2a1120b680c98da2d26ed67658d8/template%20t%C3%A2che%2028dd2a1120b68016a2fce327a24886cc.md) 

[prompt.demande.tâche](Agent%20T%C3%A2che%2028dd2a1120b680c98da2d26ed67658d8/prompt%20demande%20t%C3%A2che%2028dd2a1120b6802f9c5ffedaf12ede07.md) 

[Prompt Agent](Agent%20T%C3%A2che%2028dd2a1120b680c98da2d26ed67658d8/Prompt%20Agent%2028dd2a1120b6803cb22edda43b0ecb33.md)