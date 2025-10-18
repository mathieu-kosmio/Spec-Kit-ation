# Agent Clarification

## Agent Clarification — Description & Manuel d’utilisation

### 1. Description de l’agent

### Nom

**Agent Clarification** (ou Agent Spécification-Clarification)

### Rôle & mission

L’agent Clarification intervient juste après la rédaction initiale de la spécification fonctionnelle. Son objectif est de **repérer les zones ambiguës, les manques, les hypothèses implicites, les incertitudes** dans la spec, et de poser des questions ciblées pour lever ces incertitudes avant le passage à la planification. En d’autres termes : rendre la spécification solide, non ambigüe et prête pour l’architecture — c’est une étape de “nettoyage" de la spec.

Cette étape est recommandée dans Spec Kit avant de lancer le plan, pour réduire les erreurs ou retours coûteux en aval. ([GitHub](https://github.com/github/spec-kit?utm_source=chatgpt.com))

### Entrées & sources d’information

- La **spécification fonctionnelle** produite (avec ses sections remplies).
- Le modèle de spec (template) pour connaître les sections à clarifier (`template.spécification.md`).
- Le guide d’interrogation `prompt.demande.clarification.md`, qui structure les questions à poser section par section.
- Le contexte global / constitution du projet, pour vérifier que les choix de la spec ne violent pas les principes définis.

### Sortie attendue

- Un document `clarification.md` (ou intégré à la spec) qui liste, section par section, les **points de clarification / questions ouvertes / zones à confirmer**.
- Ce document est structuré selon les sections de la spec, avec pour chaque point :
    - le libellé de la zone à clarifier
    - la nature du manque / ambiguïté
    - les sections / exigences concernées
    - (optionnel) des suggestions de reformulation ou des hypothèses à valider
- L’agent peut proposer un ordre de priorisation des clarifications à traiter avant de lancer l’agent Plan.

---

### 2. Manuel d’utilisation

### 2.1 Quand utiliser l’agent Clarification

- Juste après la rédaction initiale de la spécification / avant de lancer la planification.
- Chaque fois que tu sens que la spec pourrait contenir des zones floues ou des hypothèses implicites qu’il vaut mieux expliciter.
- Si des réactions (de l’agent Plan ou des revues) montrent que certaines parties de la spec ne sont pas claires, relance Clarification pour creuser.

### 2.2 Commande d’invocation

Tu invoques l’agent avec la commande :

```
/Clarification

```

Le prompt maître de Clarification (que tu as défini) pilotera les interactions.

### 2.3 Étapes de fonctionnement

1. **Lecture de la spécification & du contexte**
    
    L’agent examine la spec existante, ses sections, et les contraintes ou principes de la constitution pour identifier les zones potentiellement ambiguës.
    
2. **Pose de questions / interrogation section par section**
    
    Pour chaque section de la spec (par exemple, “Introduction & contexte”, “Cas d’usage”, “Exigences fonctionnelles”, etc.), l’agent pose les questions du guide `prompt.demande.clarification.md` visant à débusquer les manques ou ambiguïtés (ex : “Y a-t-il des cas d’erreur non mentionnés ?”, “les critères d’acceptation sont-ils complets et mesurables ?”, etc.).
    
    Il attend tes réponses / éclaircissements pour chaque section avant de passer à la suivante.
    
3. **Compilation des points de clarification**
    
    Après avoir posé les questions pour une section, l’agent rédige une **liste des points de clarification** pour cette section, structurée :
    
    - point à clarifier
    - nature du manque / ambiguïté
    - référence à la section de la spec
    - (optionnel) suggestion ou hypothèse à confirmer
    
    Il te propose de valider / ajuster cette liste avant de passer à la section suivante.
    
4. **Finalisation du document de clarification**
    
    Lorsque toutes les sections ont été couvertes, l’agent assemble le document `clarification.md`, contenant les listes de points de clarification section par section, et propose un **ordre de traitement prioritaire** pour les clarifications les plus critiques.
    
    Il peut aussi recommander quelles clarifications doivent absolument être résolues avant de lancer l’agent Plan.
    
5. **Intégration ou mise à jour de la spec**
    
    Une fois que tu réponds aux clarifications, tu peux soit :
    
    - mettre à jour la spec (manuellement ou avec l’aide d’un agent) avec les réponses / corrections,
    - ou relancer /Spécification avec les éléments clarifiés pour produire une version corrigée de la spec.
    - Ensuite, lancer /Plan avec la spec clarifiée.

### 2.4 Bonnes pratiques & recommandations

- **Ne pas sauter la clarification** : c’est un garde-fou utile pour diminuer les retours coûteux en amont du plan / code.
- **Répondre précisément** : tes réponses aux questions de clarification doivent être aussi claires que possible.
- **Documenter les hypothèses** : si certaines réponses restent incertaines, signale-le clairement dans le document de clarification — c’est mieux que d’ignorer le doute.
- **Prioriser les clarifications critiques** : certaines zones ambiguës peuvent bloquer le plan ou l’implémentation — traite-les en priorité.
- **Relecture collaborative** : si possible, fais relire les points de clarification par un collègue métier ou technique avant de procéder au plan.
- **Relance si nécessaire** : même après la planification, si le plan révèle des zones de la spec non suffisamment clarifiées, tu peux rappeler /Clarification centré sur ces zones.
- **Mettre à jour la spec avec les clarifications** : ne laisse pas les ambiguïtés dans la spec finale — la version de la spec utilisée par Plan doit être la version clarifiée.

---

[prompt.demande.clarification](prompt%20demande%20clarification.md) 

[Prompt Agent](Prompt%20Agent.md)
