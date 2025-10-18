# Agent Analyse

## Agent Analyse — Description & Manuel d’utilisation

### 1. Description de l’agent

### Nom

**Agent Analyse**

### Rôle & mission

L’agent Analyse joue un rôle critique dans le pipeline Spec-Driven : il réalise une **analyse croisée** des artefacts (constitution, spécification, plan, tâches) pour détecter les **incohérences, redondances, lacunes, conflits, ou risques** entre les différentes couches du projet. Son objectif est d’assurer que les artefacts ne divergent pas les uns des autres, que tout ce qui est exigé est bien planifié et découpé, et qu’aucune hypothèse implicite ou contradiction ne reste non examinée.

L’agent Analyse correspond à la phase `/speckit.analyze` dans Spec Kit. ([The GitHub Blog](https://github.blog/ai-and-ml/generative-ai/spec-driven-development-with-ai-get-started-with-a-new-open-source-toolkit/?utm_source=chatgpt.com))

### Entrées & sources d’information

- Le document **constitution** (principes, contraintes, priorités)
- Le document **spécification** (exigences, cas d’usage, interfaces)
- Le document **plan** (architecture, modules, flux, contraintes techniques)
- Le document **tâches** (liste des tâches, dépendances, priorités)
- Le modèle de structure d’analyse (non toujours explicite, mais implicite)
- Le guide d’interrogation `prompt.demande.analyse.md` fournissant les questions à poser pour détecter les anomalies / divergences.

### Sortie attendue

- Un fichier `analyse.md` (ou un sous-ensemble structuré) contenant :
    - Pour chaque couple ou section (par exemple, Spec vs Plan, Plan vs Tâches, Constitution vs Spec, etc.) :
        - Une **liste de points d’analyse** (incohérences, omissions, conflits, redondances)
        - Pour chaque point :
            - Le *libellé* du problème
            - La *source(s)* (quel artefact / section est concerné)
            - La *gravité ou priorité* (critique, élevé, moyen, faible)
            - Une *suggestion d’action / correction*
    - Une **synthèse globale** : les zones les plus critiques à corriger, les suggestions prioritaires, et un ordre proposé d’ajustement
- Le rapport versionné (version, date, nom d’agent)
- Ce document sert de guide de relecture et de correction avant de lancer l’implémentation.

---

### 2. Manuel d’utilisation

### 2.1 Quand utiliser l’agent Analyse

- Une fois que les principaux artefacts (constitution, spécification, plan, tâches) sont générés ou mis à jour.
- Avant de lancer l’implémentation, pour s’assurer que tout est aligné et que rien ne manque.
- Lors de modifications d’un artefact existant (nouvelle spec, mise à jour de plan ou tâches), pour vérifier l’impact sur les autres artefacts.
- En phase de revue / validation : l’agent Analyse agit comme un contrôleur de cohérence.

### 2.2 Commande d’invocation

Tu invoques l’agent via :

```
/Analyse

```

Le prompt maître (défini précédemment) pilotera l’agent pour interroger, analyser et générer le rapport d’analyse.

### 2.3 Étapes de fonctionnement

1. **Demande des zones ou couples à analyser**
    
    L’agent commence par te demander quelles parties du projet tu veux analyser :
    
    > “Sur quels artefacts ou couples d’artefacts (Constitution vs Spec, Spec vs Plan, Plan vs Tâches, global, etc.) souhaitez-vous focaliser l’analyse ?”
    > 
2. **Pour chaque couple / section choisi : interrogation & collecte**
    
    L’agent utilise le guide `prompt.demande.analyse.md` pour poser des questions ciblées afin d’extraire les incohérences, manques ou tensions dans les artefacts concernés.
    
    Par exemple : “Cette exigence de la spec est-elle mappée dans le plan ?”, “Le plan introduit-il des composants non présents dans la spec ?”, “Les tâches respectent-elles les dépendances du plan ?”, etc.
    
3. **Génération des points d’analyse**
    
    Pour chaque bloc (couple / section), l’agent compile une **liste de points d’analyse**. Chaque point est structuré avec :
    
    - libellé clair du problème
    - référence aux artefacts / sections concernés
    - gravité / priorité
    - suggestion d’action pour corriger ou investiguer
    
    L’agent te présente ces points et demande :
    
    > “✅ Points d’analyse pour le bloc X prêts. Voulez-vous les modifier / ajouter / classer autrement ? Prêt à passer au bloc suivant ?”
    > 
4. **Itération jusqu’à finalisation**
    
    L’agent couvre tous les blocs / couples choisis. Tu peux valider, ajuster ou commenter après chaque bloc.
    
5. **Compilation du rapport final**
    
    Une fois tous les blocs traités, l’agent assemble le rapport final `analyse.md`, avec une **synthèse globale**, une **priorisation des points critiques**, des suggestions d’ordre de correction.
    
    Il affiche ce rapport pour que tu puisses le télécharger / l’enregistrer dans ton dossier projet.
    

### 2.4 Bonnes pratiques & recommandations

- **Choisir les blocs clés pour commencer** : commence souvent par Spec vs Plan, puis Plan vs Tâches, puis les comparaisons constitution ↔ spec si nécessaire.
- **Ne pas ignorer les contradictions mineures** : ce sont souvent les petites divergences (ex : un cas d’erreur non explicitement mappé) qui provoquent des bugs ou des surprises.
- **Utiliser la priorité / gravité** : tous les problèmes ne sont pas égaux — corrige d’abord ceux qui peuvent bloquer ou entraîner des incohérences majeures.
- **Prendre en compte les contraintes de la constitution** : si une exigence métier ou technique viole la constitution, cela doit être signalé.
- **Faire des itérations** : tu peux lancer /Analyse plusieurs fois, à mesure que tu mets à jour les spec / plan / tâches.
- **Documenter les ajustements** : quand tu corrige ou modifie un artefact en réponse à l’analyse, note ce qui a changé et pourquoi (versionner, trace).
- **Ne pas négliger la synthèse globale** : le rapport doit te donner une vue d’ensemble des points à traiter, pas seulement une série de problèmes isolés.
- **Intégrer ce rapport dans la revue / plan d’action** : les développeurs, architectes ou parties prenantes doivent considérer les suggestions d’analyse avant d’implémenter.

---

[prompt.demande.analyse](prompt%20demande%20analyse.md) 

[Prompt Agent](Prompt%20Agent.md)
