# Agent Constitution

# Agent Constitution — Description & Manuel d’utilisation

## 1. Description de l’agent

### Nom

**Agent Constitution**

### Rôle & mission

L’agent Constitution est chargé de définir les **fondations du projet**. Il produit le document de constitution (ou charte du projet) qui fixe les **valeurs, principes, contraintes, exigences non fonctionnelles, normes, priorités** que tous les autres agents (Spécification, Plan, Tâches, etc.) devront respecter.

Avec cette constitution, on s’assure que les choix futurs (architecture, fonctionnalités, découpage) restent **alignés** avec les objectifs, la vision et les contraintes du projet.

### Entrées & sources d’information

- Le **contexte du projet** : domaine métier, objectifs, utilisateur cible, périmètre, contraintes éventuelles.
- Documents contextuels ou préexistants (cahier des charges, notes, exigences métier).
- Les modèles / templates de constitution (`template.constitution.md`) et le guide d’interrogation (`prompt.demande.constitution.md`) que l’agent utilisera pour structurer les questions et la rédaction.

### Sortie attendue

- Un fichier `constitution.md` (ou autre nom convenu) structuré selon le modèle, avec les sections remplies :
    1. Contexte & objectifs
    2. Valeurs & principes
    3. Contraintes & limites techniques
    4. Exigences non fonctionnelles
    5. Normes & bonnes pratiques
    6. Priorités & arbitrages
    7. Checklist de conformité
    8. Instruction à l’agent Spécification
- Ce document est versionné (version, date) et enregistré dans le **dossier projet** pour servir de référence aux agents suivants.

---

## 2. Manuel d’utilisation

### 2.1 But & moment d’utilisation

- L’agent Constitution est la **première étape** du pipeline Spec-Driven Development.
- Il doit être exécuté dès que le projet est initié, avant que les autres agents commencent leur travail.
- Si le contexte évolue (changement de stack, nouvelles contraintes, pivot métier), tu peux relancer cet agent pour ajuster la constitution (versionner) avant de continuer.

### 2.2 Commande d’invocation

- Tu lances l’agent via la commande :
    
    ```
    /Constitution
    
    ```
    
- Le prompt maître (déjà défini) sera utilisé pour guider l’agent dans son travail.

### 2.3 Étapes de fonctionnement

1. **Lecture du contexte & documents**
    
    L’agent examine le prompt utilisateur (contexte initial) et les fichiers uploadés (notes métier, cahier des charges, contraintes) présents dans le chat.
    
2. **Pose de questions initiales**
    
    Avant de rédiger, l’agent demande toutes les informations manquantes nécessaires à la constitution : par exemple la stack technique envisagée, priorités non fonctionnelles (performance, sécurité…), exclusions, contraintes budgétaires ou temporelles.
    
3. **Rédaction section par section**
    
    L’agent avance selon le modèle `template.constitution.md`:
    
    - Il rédige **section 1 – Contexte & objectifs** à partir des réponses obtenues.
    - Avant de passer à **section 2 – Valeurs & principes**, il peut revenir poser des questions complémentaires si une zone manque de clarté.
    - Il continue ainsi jusqu’à la **section 8 – Instruction à l’agent Spécification**.
4. **Validation progressive**
    
    Après chaque section rédigée, l’agent demande :
    
    > “✅ Section X terminée. Voulez-vous la modifier avant de passer à la section suivante ?”
    > 
    > 
    > Tu peux demander des ajustements immédiatement avant de continuer.
    > 
5. **Finalisation**
    
    Une fois toutes les sections validées, l’agent compile le document complet `constitution.md`, y insère la version, la date, le nom d’agent, et une **instruction finale claire** pour l’agent Spécification.
    
    Il propose un résumé exécutif (points clés, décisions majeures).
    
    Enfin, il “enregistre” le document (upload / téléchargement) dans le dossier projet dans le chat.
    

### 2.4 Bonnes pratiques & conseils

- **Préparer le contexte** : avant d’invoquer l’agent, fais un prompt résumant le projet (domaine, objectifs, contraintes, stack envisagée).
- **Ne pas omettre les priorités non fonctionnelles** : performance, sécurité, maintenabilité, évolutivité, compatibilité.
- **Valider section par section** : ne laisse pas l’agent continuer sans que tu aies revu / corrigé.
- **Versionner** : chaque constitution doit porter une version (v1.0, v1.1, …) pour suivre les évolutions.
- **Conserver l’historique** : si tu modifie la constitution suite à un pivot, garde la version précédente pour traçabilité.
- **Utiliser la checklist / analyse par la suite** : la constitution est la base de toutes les vérifications ultérieures.

---

[Prompt.demande.constitution](Prompt%20demande%20constitution.md)

[`template.constitution`](template%20constitution.md)

[Prompt Agent](Prompt%20Agent.md)
