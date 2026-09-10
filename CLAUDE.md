# VFOURNIER — Instructions Claude

<!-- project-notes-system -->
## Système de notes

Ce projet utilise le système de notes/todos universel V pour Design.
**Convention :** `_AGENCY/CTO/conventions/project-notes.md`

Quand Vincent écrit dans ce chat une note, todo, rappel ou idée — auto-classer dans `NOTES.md` selon les 6 catégories : 📅 Échéances · ✅ À faire · 💭 Long shots · 📝 Notes client · 🔍 Précisions · ✓ Fait. Confirmer en une ligne après chaque ajout.

### À l'ouverture de la session (toujours, avant toute chose)
Tableau de todos cliquable (artéfact Claude, base `db`, collection `todos`) : https://claude.ai/code/artifact/caa7e22a-6320-4220-ac2b-9b9dc77aea56
Ce projet y apparaît sous `project` = nom du dossier (ex. `JACQUESROUSSEL`). `NOTES.md` reste la source de vérité; le tableau et le panneau Progress en sont les miroirs.

1. **Rapatrier ce que Vincent a coché ou ajouté dans le tableau** : `Artifact` action `read_db`, `db_op` `query`, `collection` `todos`, `query.where` `[["project","==","<NOM DU DOSSIER>"],["synced","==",false]]`. Pour chaque doc : `done:true` → déplacer la ligne correspondante de `NOTES.md` dans `✓ Fait` sous la forme `- [AAAA-MM-JJ] <texte>` (date de `doneAt`); `source:"page"` et `done:false` → ajouter la ligne `- [ ] <texte> (AAAA-MM-JJ)` dans `✅ À faire` (ou `📅 Échéances` avec `**due**` si `due` est rempli). Puis `write_db` `update` sur chaque doc avec `{"synced": true}`.
2. Lire `NOTES.md` (le créer depuis la convention s'il manque).
3. Créer une tâche `TaskCreate` par ligne `- [ ]` de `📅 Échéances` puis de `✅ À faire`, même ordre, même libellé. Le panneau Progress affiche ainsi ce qui reste à faire dès l'ouverture, avant même la première réponse.
4. Tâche terminée en session : `TaskUpdate` completed, déplacer la ligne dans `✓ Fait` avec la date du jour, et `write_db` `update` du doc correspondant avec `{"done": true, "doneAt": "<ISO>", "synced": true}` (doc_id = `<NOM DU DOSSIER>__<8 hex>`, retrouver par `query` sur `project` + texte).
5. Toute action décidée en session s'ajoute à `NOTES.md`, au panneau, et au tableau (`write_db` `set`, `collection` `todos`, `doc_id` `<NOM DU DOSSIER>__<8 hex aléatoires>`, data `{"project","text","section":"afaire"|"echeances","due":null|"AAAA-MM-JJ","done":false,"source":"notes","synced":true}`).
<!-- /project-notes-entry -->

