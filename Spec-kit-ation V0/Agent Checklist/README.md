# Agent Checklist

## Agent Checklist — Description & Manuel d’utilisation

### 1. Description de l’agent

### Nom

**Agent Checklist**

### Rôle & mission

L’agent Checklist est responsable de générer des **listes de contrôle (checklists de vérification / QA)** pour les artefacts produits (constitution, spécification, plan, tâches). Ces checklists servent de garde-fous qualitatifs : elles définissent des points de contrôle que chaque document / étape doit respecter (cohérence, exhaustivité, respect des principes, conformité aux contraintes). L’idée est que chaque artefact soit “révisable” selon des critères préétablis, afin de détecter les oublis ou violations avant l’implémentation.

Dans Spec Kit, les checklists sont utilisées pour “unittest l’anglais” — c’est-à-dire pour vérifier la qualité de la rédaction, la complétude et la cohérence des specs / plans. ([martinfowler.com](https://martinfowler.com/articles/exploring-gen-ai/sdd-3-tools.html?utm_source=chatgpt.com))

### Entrées & sources d’information

- Les artefacts à auditer : **constitution**, **spécification**, **plan**, **tâches** (ou tout sous-ensemble selon souhait).
- Le modèle de checklist (que tu aurais défini, ou ton propre standard) — éventuellement un “template.checklist.md”.
- Le guide d’interrogation `prompt.demande.checklist.md`, qui structure les questions à poser pour extraire les points de contrôle pertinents.
- Le contexte global / constitution du projet, pour déterminer les critères primordiaux à vérifier (sécurité, performance, modularité).

### Sortie attendue

- Un fichier `checklist.md` ou équivalent, structurée par artefact (et par section), contenant une **liste de critères de vérification** tels que :
    - Pour chaque point de contrôle :
        - formulation claire du contrôle (ex : “toutes les exigences ont un identifiant unique”, “chaque module du plan correspond à une exigence”, etc.)
        - niveau de criticité (obligatoire / recommandé / optionnel)
        - indication de l’artefact / section où s’applique le contrôle
        - (optionnel) action recommandée si le contrôle n’est pas respecté
- Le document peut aussi proposer une **priorisation** des contrôles (ce qui doit être vérifié en priorité).
- Le document est versionné (version, date) et enregistré dans le dossier projet.

---

### 2. Manuel d’utilisation

### 2.1 Quand utiliser l’agent Checklist

- Après avoir généré un ou plusieurs artefacts (constitution, spécification, plan, tâches), mais **avant** leur utilisation en implémentation.
- Pour chaque nouvelle itération ou version d’un artefact, tu peux relancer Checklist pour vérifier que les nouveaux changements respectent les standards.
- En phase de revue / audit des livrables : utiliser la checklist comme “liste de contrôle qualité” à valider avant d’avancer.

### 2.2 Commande d’invocation

Tu invoques l’agent via :

```
/Checklist

```

Le prompt maître de l’agent (celui que tu as défini) déclenchera une série d’interactions basées sur le guide d’interrogation pour construire la checklist.

### 2.3 Étapes de fonctionnement

1. **Demande des artefacts & priorités à auditer**
    
    L’agent commence par te demander :
    
    > “Sur quels artefacts souhaitez-vous générer la checklist ? (Constitution, Spécification, Plan, Tâches, ou tous) — et quelles priorités (sécurité, performance, UX, modularité, etc.) voulez-vous mettre en avant ?”
    > 
2. **Interrogation section par section / artefact par artefact**
    
    Pour chaque artefact sélectionné, l’agent parcourt ses sections pertinentes et pose les questions du guide `prompt.demande.checklist.md` afin de dégager les points de contrôle essentiels.
    
3. **Génération des points de contrôle**
    
    Après avoir collecté des remarques / critères pour une section, l’agent rédige les points de contrôle associés (avec libellé, criticité, artefact / section référente).
    
    Il affiche ces points pour validation :
    
    > “✅ Voici les points de contrôle pour l’artefact / section X : souhaitez-vous les modifier, ajouter ou supprimer ?”
    > 
4. **Itération jusqu’à validation de tous les artefacts sélectionnés**
    
    L’agent passe aux artefacts suivants une fois les points du précédent validés, jusqu’à ce que tous soient traités.
    
5. **Compilation du document final**
    
    À la fin, l’agent assemble le dossier `checklist.md` regroupant toutes les listes de contrôle (par artefact, section) dans un format structuré (tableaux, listes), avec les métadonnées (version, date, agent).
    
    Il peut fournir une **vue synthétique des contrôles critiques** à prioriser.
    
6. **Livraison / export**
    
    L’agent propose la sortie du fichier `checklist.md` dans le chat pour que tu puisses l’exporter / enregistrer dans le dossier projet.
    

### 2.4 Bonnes pratiques & recommandations

- **Sélectionner les bons artefacts** : il n’est pas toujours nécessaire de faire une checklist sur tous les artefacts ; tu peux te concentrer sur ceux récemment modifiés.
- **Adapter les critères aux priorités du projet** : si la sécurité est un focus fort, demande que les contrôles de sécurité soient mis en avant dans la checklist.
- **Ne pas surcharger** : privilégie des contrôles clés (essentiels), et ne liste pas de critères triviaux ou redondants.
- **Validation / revue humaine** : la checklist produite par l’agent doit être relue et éventuellement enrichie par un expert avant de l’appliquer.
- **Utilisation comme contrat de revue** : tu peux utiliser la checklist lors des revues de documents / code pour vérifier si tout est conforme.
- **Itération & mise à jour** : à chaque évolution majeure d’un artefact, relance l’agent Checklist pour vérifier que les nouveaux éléments respectent les critères.
- **Linkage traceable** : ajoute dans les points de contrôle des liens (IDs, sections) vers les artefacts / sections concernés pour faciliter la validation.

---

[prompt.demande.checklist.md](prompt%20demande%20checklist%20md.md) 

[Prompt Agent](Prompt%20Agent.md)
