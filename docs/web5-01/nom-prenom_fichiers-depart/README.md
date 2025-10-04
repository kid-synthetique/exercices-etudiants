# FestiPixel – Exercice (Évaluation)

## Contexte
Vous devez créer une mini-application **Vue.js (Options API)** qui affiche la programmation d’un festival fictif : **FestiPixel**.  
Les données proviennent d’un fichier **JSON** chargé via **Fetch API**.  
L’interface doit être présentée en **CSS Grid**, avec deux dispositions possibles : **uniform** (uniforme) et **featured** (en vedette).
L'interface doit **s'adapter selon le format de l'écran**, voir l'aperçu afin d'appliquer le placement de la grille selon ce qui est attendu.

---

## Objectif
Mettre en pratique les notions suivantes :
- **Vue.js (Options API)** : `data`, `computed`, `methods`, directives (`v-model`, `v-for`, `v-if`, `:class`, `@click`, etc.).
- **Fetch API** : chargement de données externes via une méthode appelée par un bouton.
- **CSS Grid** : création de layouts responsives et avec mise en avant d’un artiste vedette.
- **Utilisation de fonctions utilitaires (helpers)** déjà fournies dans `utils.js`.

---

## Fichiers fournis
- `index.html` → squelette de l’application.
- `style.css` → base de styles + classes pour les deux layouts.
- `main.js` → code Vue à compléter.
- `data.json` → données des artistes.
- `utils.js` → **fonctions utilitaires prêtes** pour filtrer, chercher et trier les artistes.

> Vous n’avez pas besoin d’écrire vous-mêmes des fonctions complexes sur les tableaux (`sort`, `filter`, etc.).  
> Utilisez simplement les helpers de `utils.js` dans vos `computed` ou `methods`.

---

## Exigences fonctionnelles

1. **Création de l'app Vue**
   - Importer Vue.js 3
   - Créer l'application Vue

2. **Chargement des données**
   - Au clic du  bouton **« Charger la programmation »**, une **méthode Vue** fait appel à `fetch('./data.json')`.  
   - Gérer les états de l'app à partir de la progression de ce fetch :  
     - `init` → afficher le bouton  « Charger la programmation ». Ce sera l'état initial lors du chargemetn de l'app.
     - `loading` → afficher « Chargement… »  
     - `error` → afficher un message d’erreur  
     - `loaded` → afficher la grille  

3. **Affichage en grille**
   - Chaque artiste s’affiche en tant que carte avec :
     - Nom  
     - Scène  
     - Heure (début–fin)  
     - Style  
     - Popularité (⭐ nombre)  
   - Mise en page (layout) **CSS Grid** responsive :
     - **Uniform** : cartes toutes pareilles.  
     - **Featured** : l’artiste vedette (`featured:true` dans `data.json`) occupe plus d’espace sur la grille.
     - Appliquer les styles des 2 types de grille pour écran format moyen
     - Appliquer les styles des 2 types de grille pour écran petit format (mobile)

4. **Filtres et recherche**
   - **Recherche par nom** (input texte).
   - **Filtre par scène** (liste déroulante).
   - Afficher le nombre de résultats filtrés.

5. **Tri**
   - Possibilité de trier les artistes par :
     - Heure (début ↑)
     - Popularité (↓)
     - Nom (A→Z)

6. **Vue.js**
   - Définir les propriétés de l'app Vue pour:
      - l'état de chargement des données, initialisée à `init`
      - un tableau (array) contenant les données chargée à partir de `data.json`
      - le contenu du champ **Recherche**
      - la scène sélectionnée
      - le type de tri sélectionné (heure, popularité, nom)
      - la disposition (layout) sélectionnée: `featured` ou `uniform`
   - Définir une **propriété calculée** `artistsSortedArr` contenant un tableau (array) qui contient la liste des artistes et leurs données et qui lui applique le pipeline suivant :

     ```
     vedette en premier → filtre par stage → recherche par nom → tri (réordonner par...)
     ```

     - Utiliser les helpers de `utils.js` :
        - `putFeaturedFirst(list)`
        - `filterByStage(list, stage)`
        - `searchByName(list, q)`
        - `sortByMode(list, mode)`
     - Dans `artistsSortedArr`, enchaîner ces fonctions dans le bon ordre.
     - C'est cette propriété qui permettra d'afficher les cartes d'artiste dans l'élément `.schedule`


7. **États d’interface**
   - Message clair si aucun résultat : « Aucun artiste ».
   - Bouton « Réinitialiser » pour effacer les filtres et la recherche.

---

## Contraintes
- Pas de framework CSS externe (pas de Bootstrap/Tailwind).
- Vue doit être chargée via le CDN fourni dans `index.html`.
- L’application doit être lancée via un **serveur local** (ex. *Live Server* dans VS Code), pas avec `file://` (sinon `fetch` échoue).

---

## Livrables
- `index.html`, `style.css`, `main.js`, `data.json`, `utils.js`.
- Une application fonctionnelle respectant les consignes.
- Facultatif : un court `README.md` personnel expliquant vos choix.

---

## Barème (100 points)
- **Fetch via bouton & gestion des états** → 15 pts  
- **Grille responsive & layouts (uniforme/featured)** → 25 pts  
- **Filtre & recherche** → 20 pts  
- **Tri** → 10 pts  
- **Vue.js (computed `artistsSortedArr`, directives, events, data binding)** → 20 pts  
- **UX & accessibilité (messages, labels, réinitialisation)** → 10 pts  
