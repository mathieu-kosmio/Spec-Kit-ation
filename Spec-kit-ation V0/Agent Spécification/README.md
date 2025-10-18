# Agent Spécification

# Agent Spécification — Description & Manuel d’utilisation

## 1. Description de l’agent

### Nom

**Agent Spécification**

### Rôle & mission

L’agent Spécification a pour mission de produire la **spécification fonctionnelle** ou module / fonctionnalité à créer. Il formalise les cas d’usage, exigences, interfaces, règles métiers, comportements et non fonctionnels, dans un document selon le modèle `template.spécification.md`. Ce document sert de base de communication entre le besoin métier, les parties prenantes et les agents techniques (Plan, Tâches).

### Entrées & sources d’information

- **Constitution du projet** (les principes, contraintes, exigences non fonctionnelles de niveau global).
- **Contexte métier / documents de domaine** (cahier des charges, documentation, notes, études, utilisateurs cibles).
- **Templates & guides** : `template.spécification.md` (la structure à respecter) et `prompt.demande.spécification.md` (le guide d’interrogation pour poser les bonnes questions).
- Documents précédents ou modules existants pouvant servir de référence (autres specs, diagrammes, API déjà en place).

### Sortie attendue

- Un fichier `specification.md` (ou un ensemble de fichiers si modules séparés) qui reprend toutes les sections du modèle, dûment remplies :
    1. Introduction & contexte
    2. Cas d’usage / scénarios utilisateur
    3. Exigences fonctionnelles
    4. Comportements hors norme & règles de gestion
    5. Interfaces & contrats
    6. Non fonctionnel lié à cette spec
    7. Validation & critères d’acceptation globaux
    8. Questions ouvertes & incertitudes
    9. Relations & dépendances
    10. Instruction à l’agent Plan
- Le document doit être versionné (numéro de version, date) et être exploitable immédiatement par l’agent Plan suivant.

---

## 2. Manuel d’utilisation

### 2.1 Quand utiliser l’agent Spécification

- Toute fois que tu as besoin de formaliser une nouvelle **fonctionnalité**, un **module**, ou une **modification majeure**.
- Avant d’aller vers la planification / architecture, afin que le besoin soit clairement défini et compris.
- En phase d’évolution du projet : pour des ajouts ou modifications au backlog, relancer l’agent Spécification pour la nouvelle spec.

### 2.2 Commande d’invocation

Tu lances l’agent en utilisant la commande :

```
/Spécification

```

Le prompt maître de l’agent déclenchera le dialogue de collecte de données selon le guide, et produira la spec conforme au modèle.

### 2.3 Étapes de fonctionnement

1. **Lecture du contexte & constitution**
    
    L’agent lit le contexte du projet, les contraintes définies dans la constitution, les documents uploadés (métier, backlog) présents dans le chat.
    
2. **Pose de questions initiales / de clarification**
    
    Avant de rédiger chaque section, l’agent te posera des questions — issues de `prompt.demande.spécification.md` — pour récolter les informations nécessaires (cas d’usage, acteurs, scénarios, interfaces, contraintes non fonctionnelles, etc.). Si certaines infos sont déjà fournies dans le contexte, il ne redemandera pas inutilement.
    
3. **Rédaction section par section**
    
    L’agent avance dans l’ordre du modèle `template.spécification.md` :
    
    - D’abord **Introduction & contexte**
    - Puis **Cas d’usage / scénarios utilisateur**, etc.
        
        Pour chaque section, après avoir obtenu les réponses aux questions, il construit la partie correspondante de manière structurée (listes, tableaux, identifiants, relations).
        
4. **Validation progressive**
    
    Après avoir rédigé une section, l’agent demande :
    
    > “✅ Section X rédigée. Voulez-vous la modifier ou ajouter des détails avant de passer à la suivante ?”
    > 
    > 
    > Tu peux corriger ou compléter immédiatement.
    > 
5. **Finalisation**
    
    Une fois toutes les sections validées, l’agent assemble le document complet `specification.md`, ajoute version, date, nom d’agent et une consigne claire pour l’agent Plan dans la section 10. Il peut aussi fournir un **résumé des points clés** (fonctionnalités majeures, priorités, dépendances critiques).
    
    Enfin, il t’invite à télécharger / sauvegarder le document dans le dossier projet.
    

### 2.4 Bonnes pratiques & recommandations

- **Préparer le contexte métier / backlog** : avant de lancer l’agent, dispose une version sommaire du besoin, les objectifs et contraintes métiers.
- **Être précis dans les réponses** : plus tes réponses aux questions sont précises, meilleure sera la spec produite.
- **Utiliser des identifiants uniques** pour cas d’usage, exigences, interfaces — cela facilite la traçabilité dans les plans / tâches.
- **Ne pas laisser de zone ambiguë sans clarification** : si une question reste floue, l’agent doit te reposer pour clarifier avant de rédiger.
- **Documenter les incertitudes** : dans la section “Questions ouvertes & incertitudes”, ne cherche pas à forcer les réponses — liste les zones à confirmer plus tard.
- **Faire relire / valider par métier / parties prenantes** : la spec est l’un des principaux contrats entre le métier et la technique.
- **Mise à jour / versioning** : si la spec évolue (changement de besoin), incrémente la version (v1.1, v2.0, etc.) et documente ce qui change.
- **Lien vers la constitution** : la spec doit respecter les contraintes / principes de la constitution (sécurité, performance, modularité, etc.). Si une exigence de la constitution entre en conflit avec une idée métier, cela doit être discuté / résolu (par Clarification / Analyse).

---

[template.specification](template%20specification.md)

[prompt.demande.spécification](prompt%20demande%20sp%C3%A9cification.md)

[Prompt Agent](Prompt%20Agent.md)
