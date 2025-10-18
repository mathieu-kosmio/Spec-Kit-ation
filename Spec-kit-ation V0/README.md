# Spec-kit-ation V0.1

**Manuel d’utilisation des agents** (Constitution, Spécification, Planification, Tâches, Clarification, Checklist, Analyse) pour piloter un projet via ChatGPT selon la méthode Spec-Driven Development que tu es en train de mettre en place.

![Cheval pixelisé sur rouleau parchemin.png](media/speck-kit-ation.png)

---

## 1. Vue d’ensemble du flux projet

Voici le **cycle de vie typique** d’un projet avec tes agents :

1. **Initialisation / Constitution** — définir le cadre, les principes et contraintes de haut niveau.
2. **Spécification** — définir les fonctionnalités, cas d’usage, exigences, interfaces.
3. **Clarification** — vérifier les zones floues de la spécification, lever les incertitudes.
4. **Planification (Plan)** — définir l’architecture, les modules, le flux technique, les dépendances.
5. **Tâches** — découper le plan en tickets / tâches actionnables avec critères, estimations, dépendances.
6. **Checklist** — générer un audit de conformité / qualité pour chacun des artefacts produits.
7. **Analyse** — croiser les artefacts pour détecter incohérences, redondances, manques et proposer des ajustements.
8. (Prochaine version) **Implémentation / Export / Génération de code** — consommer les tâches pour produire du squelette de code ou artefacts livrables.
9. **Itérations / évolution** — à chaque nouvelle spécification (fonctionnalité ou modification du backlog) : relancer le pipeline (Spécification → Clarification → Plan → Tâches → Checklist → Analyse), puis implémenter.

Chacun de ces agents produit un document structuré (Markdown ou format convenu) que tu stockes dans le “dossier projet” dans ChatGPT (par upload / contexte), et qui sera exporté pour être utilisé par les développeurs dans leur IDE.

---

## 2. Installation / configuration initiale du projet dans ChatGPT

Voici comment démarrer :

1. **Créer une nouvelle session / nouveau “projet” dans ChatGPT**
    - Ouvre un nouveau chat dédié au projet.
    - Donne un nom de projet, un contexte général (domaine, but, périmètre) dans le prompt initial.
2. **Charger le contexte & fichiers de base**
    - Uploade dans la session tous les fichiers de contexte existants (ex : documents métier, cahier des charges, diagrammes, notes) tant que le nombre de fichiers reste dans la limite (20 fichiers par chat).
    - Tu peux également structurer un “dossier projet” mental ou listé dans le chat : par exemple mentionner que le dossier contient `constitution.md`, `specification/`, `plan/`, `tasks/`, etc.
3. **Définir les modèles / templates**
    - Upload ou insère le fichier `template.constitution.md`, `template.spécification.md`, `template.plan.md`, `template.tâche.md`.
    - Upload les guides `prompt.demande.*.md` si tu veux que les agents s’y réfèrent.
    - Ces fichiers servent de “contrat de format” pour tes agents : les agents doivent produire des documents qui respectent ces modèles.
4. **Définir le prompt maître d’orchestration**
    - Tu peux avoir un prompt initial ou “super-prompt” qui décrit aux agents leur rôle, leur ordre, comment utiliser les fichiers modèles, etc.
    - Par exemple :
        
        > “Nous allons produire un pipeline avec les agents suivants dans cet ordre : /Constitution → /Spécification → /Clarification → /Plan → /Tâches → /Checklist → /Analyse. Chaque agent doit produire un document dans le format du template correspondant, poser les questions manquantes, valider section après section, et enregistrer le document dans le dossier projet.”
        > 
5. **Versionner les documents au fur & à mesure**
    - Chaque document produit doit porter une version (v1.0, v1.1, …) et une date.
    - Lorsque tu modifies une specification ou un plan, incrémente la version, et indique les changements majeurs.
    - Cela permet de garder une trace historique et de revenir en arrière si besoin.

---

## 3. Mode d’utilisation agent par agent dans le projet

Voici comment tu utilises chaque agent dans le cycle :

### 3.1 Agent Constitution

- Commande : `/Constitution`
- Le prompt maître déclenche l’agent Constitution qui va :
    1. Consulter le contexte initial que tu as donné + tout document uploadé.
    2. Poser des questions pour combler les manques (stack, priorités, contraintes).
    3. Rédiger le document `constitution.md` section par section selon `template.constitution.md`.
    4. Te demander validation à la fin.
    5. Enregistrer / exporter le document dans le dossier projet.

### 3.2 Agent Spécification

- Commande : `/Spécification`
- L’agent Spécification :
    1. Prend la constitution et le contexte (documents du projet) comme références.
    2. Pose des questions section par section selon `prompt.demande.spécification.md`.
    3. Rédige les sections de `template.spécification.md` dans `specification.md`.
    4. Demande validation, corrige si besoin, puis finalise.
    5. Enregistre le document.

### 3.3 Agent Clarification

- Commande : `/Clarification`
- L’agent Clarification :
    1. Prend la spécification produite.
    2. Analyse section par section selon `prompt.demande.clarification.md` pour identifier les zones floues ou manquantes.
    3. Pose des questions pertinentes pour lever les incertitudes.
    4. Compile un document `clarification.md` contenant les points notés, par section.
    5. Te donne les questions ouvertes à répondre avant de poursuivre le plan.

### 3.4 Agent Planification (Plan)

- Commande : `/Plan`
- L’agent Plan :
    1. Prend la spécification (et le document clarification, le cas échéant) comme input.
    2. Pose des questions selon `prompt.demande.plan.md` pour collecter les détails techniques.
    3. Rédige le plan selon `template.plan.md`.
    4. Demande validation section par section, corrige si besoin.
    5. Finalise `plan.md` et l’enregistre.

### 3.5 Agent Tâches

- Commande : `/Tâches`
- L’agent Tâches :
    1. Prend `plan.md` comme référence.
    2. Pose des questions via `prompt.demande.tâche.md` sur découpage, granularité, estimations, dépendances.
    3. Rédige les tâches selon `template.tâche.md`.
    4. Validation section par section, modifications si nécessaire.
    5. Produit `tasks.md` (ou dossier `tasks/` si multiples fichiers).

### 3.6 Agent Checklist

- Commande : `/Checklist`
- L’agent Checklist :
    1. Te demande sur quels artefacts tu veux générer la checklist (constitution, spec, plan, tâches ou tous).
    2. Pour chaque artefact, pose les questions de `prompt.demande.checklist.md` pour identifier les contrôles essentiels.
    3. Compile un document `checklist.md` avec les points de contrôle (formulés, criticité, artefact de référence).
    4. Te propose de vérifier / ajuster les contrôles.

### 3.7 Agent Analyse

- Commande : `/Analyse`
- L’agent Analyse :
    1. Te demande les couples d’artefacts que tu veux analyser (ex : Spec vs Plan, Plan vs Tâches, global).
    2. Applique `prompt.demande.analyse.md` pour chaque bloc choisi, pose des questions pour clarifier si besoin.
    3. Génère une liste de points d’analyse (incohérences, manques, conflits) avec priorité et suggestions.
    4. Compile `analyse.md` (ou sections par bloc) et la présente.
    5. Tu pourras corriger ou demander modifications, puis relancer certains agents si nécessaire.

---

## 4. Export & usage des documents dans l’IDE des développeurs

Une fois les documents produits et validés :

1. **Exporter / télécharger** les fichiers Markdown (ou JSON/YAML) depuis ChatGPT.
    - ChatGPT permet de télécharger les fichiers uploadés / générés.
    - Si plusieurs fichiers (spec002, plan003, tasks005…), tu peux les zipper ou les exporter un à un.
2. **Organisation du dossier projet**
    - Par exemple :
        
        ```
        /SpekKitProject
          constitution.md
          specification/
            spec_user.md
            spec_order.md
          plan/
            plan_user.md
            plan_order.md
          tasks/
            tasks_user.md
            tasks_order.md
          checklist.md
          analyse.md
        
        ```
        
    - Les développeurs cloneront ou importeront cette structure dans leur dépôt / répertoire local.
3. **Consultation & implémentation**
    - Les devs utilisent les specs, plans et tâches comme bible : chaque ticket (tâche) décrit précisément ce à quoi doit correspondre l’implémentation.
    - Ils peuvent reporter les critères d’acceptation, interfaces, contraintes non fonctionnelles dans les tests et le code.
    - La checklist sert de guide de revue (Code Review) pour vérifier que le travail respecte les engagements.
    - Le document d’analyse peut aider à identifier les zones à surveiller, les ajustements potentiels, les risques à anticiper.

---

## 5. Gestion de l’évolution / itérations / backlog

Pour faire évoluer le projet (ajouter une nouvelle fonctionnalité, modifier une spec existante, corriger un bug) :

1. **Créer une nouvelle spec / amendment**
    - Par exemple, tu lances `/Spécification` pour la fonctionnalité ou la modification.
    - L’agent génère la spec (ou mise à jour) selon le template.
2. **Clarification**
    - Tu lances `/Clarification` sur la spec mise à jour pour identifier les incertitudes.
3. **Planification & tâches**
    - `/Plan` génère le plan pour la nouvelle spec ou intégration à l’existant.
    - `/Tâches` produira les tickets d’évolution.
4. **Checklist & analyse**
    - `/Checklist` pour vérifier que les nouveaux artefacts respectent la constitution et les normes existantes.
    - `/Analyse` pour vérifier les impacts : cohérence entre anciens artefacts et nouveaux (spec vs plan vs tâches).
5. **Intégration / Fusion**
    - Si tout est validé, tu merges les nouveaux documents (spec, plan, tâches) dans le “dossier projet”.
    - Tu incrémentes les versions globales.
    - Tu exportes les nouveaux fichiers pour les développeurs.
6. **Boucle continue**
    - À chaque sprint / itération, tu répètes ce cycle pour tout nouveau backlog ou ajustement.
    - Les documents deviennent ainsi “vivants” et synchronisés avec le code produit.

---

## 6. Bonnes pratiques & recommandations

- **Modularité & découpage** : si une spec ou un plan devient trop volumineux, découpe-le par module / domaine (ex : spécification “utilisateur”, “paiement”, etc.).
- **Validation fréquente** : ne jamais laisser une section non validée passer à l’étape suivante.
- **Traçabilité** : chaque exigence, tâche, module doit avoir un identifiant unique pour pouvoir s’y référer dans le plan / tâches / code.
- **Clarté dans les prompts** : sois explicite dans tes commandes (/Spécification, /Plan, etc.) et inclus le contexte nécessaire (module, domaine, version).
- **Nettoyage contextuel** : si tu uploades beaucoup de fichiers intermédiaires, supprime-les ou archive-les pour ne pas dépasser la limite de 20 fichiers dans ChatGPT.
- **Versionnage** : attribut une version (vX.Y) et date à chaque document.
- **Relecture & revue humaine** : même si l’IA produit les artefacts, tu dois lire / ajuster / corriger les propositions avant de les livrer.
- **Utilisation de la checklist / analyse comme garde-fou** : ne saute jamais les vérifications de qualité.
- **Dialogues interactifs** : profite du mode interactif des agents pour affiner, corriger, poser des questions quand quelque chose te semble flou.
- **Archiver les itérations** : conserve les anciennes versions des specs/plans pour pouvoir revenir ou comparer.

