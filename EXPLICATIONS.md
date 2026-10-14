| Étape/version testée                                                   | Action                                                                                  | Résultat attendu                              | Résultat constaté                                                                              |
| ---------------------------------------------------------------------- | --------------------------------------------------------------------------------------- | --------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `19d7f46` modification des couleurs, passage vers un mode sombre       | modifie la couleur du site tel que:  le fond devient bleu foncer et le texte blanc.     | site lisible et contrasté                     | les couleurs ont été appliquer.                                                                |
| `b3e8341` Afficher les places confirmer a coter du nombre de places    | affiche un compteur de nombre de places reserver                                        | compteur spécifique pour les places confirmer | Sa marche mais probleme de lecture la couleur du compteur est la meme que elle du fond du site |
| `b4964b6` Correction des couleur qui rendait le site en parti ilisible | orrection des couleur qui rendait le site en parti ilisible                             | corriger le probleme de lecture.              | sa marche.                                                                                     |
| `e7b8dc2` Afficher le nom de l'atelier dans la confirmations           | modification du compteur dans reservation (on precise le nom de l'atelier selectionner) | affichage du nom de l'atelier                 | sa a marché.                                                                                   |

### 1. Base et branches
Le point de départ commun de A et B est le commit `67aeb4f` (tag `depart-cc`). Je l'ai vérifié avec `git log --oneline --all --graph`, qui montre `19d7f46` (A) et `b3e8341` (B) partant tous les deux de ce commit, pendant que `main` restait dessus.
La branche `hotfix/lisibilite` a été créée depuis le commit `8db89c9` de `main` (la fusion de A et B). La quatrième branche, `feature/nom-atelier-confirmation`, a été créée depuis le commit `b4964b6` de `main` (après le hotfix).

### 2. Fusion et fonctionnement
Une fusion Git réussie ne garantit pas que le site fonctionne : Git fusionne du texte et détecte seulement les conflits textuels, il ne vérifie pas le rendu dans le navigateur.
Dans mon cas, A modifiait `style.css` et B modifiait `app.js`, donc la fusion s'est faite sans conflit. Pourtant, le fond de page de A est `#17223b` et le message de confirmation de B (`.receipt`) avait la même couleur `#17223b` : le texte était illisible sur la version fusionnée. Je l'ai corrigé dans le commit `b4964b6`, en passant `.receipt` en `#ffffff`.

### 3. Commit et publication
Après un commit local, il reste à faire `git push` (la première fois `git push -u origin <branche>`) pour que le changement soit visible sur GitHub.
Mon commit `e7b8dc2` est visible sur GitHub à l'adresse : https://github.com/yassine1du3k-ship-it/CC-git-github/commit/e7b8dc2
