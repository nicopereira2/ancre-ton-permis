# Ancre ton permis

Appli web pour réviser le code de la route (examen théorique général, ETG) avec la méthode des révisions espacées : chaque thème revient à **J+1, J+3, J+7, J+14 puis J+30**.

## Fonctions

- **10 thèmes** (L, C, R, U, D, A, P, M, S, E), chacun avec un cours en sous-parties et un quiz corrigé.
- **165 questions**, dont certaines à plusieurs réponses, avec explication après chaque réponse.
- **Révisions J+** : une révision réussie (80 % ou plus) fait passer au palier suivant ; sinon retour à J+1.
- **Mes erreurs** : chaque question ratée revient à J+1, J+3 puis J+7, jusqu'à 3 bonnes réponses d'affilée.
- **Panneaux** : 27 panneaux dessinés, en cartes et en quiz.
- **Examen blanc** : 40 questions, 20 secondes chacune, réussite à 35/40, historique des scores.
- **Chiffres clés** : vitesses, alcool, points, distances, numéros d'urgence.
- **Installable sur téléphone** et utilisable hors connexion après la première ouverture.

La progression est enregistrée dans le navigateur (localStorage) : elle reste sur l'appareil utilisé.

## Lancer en local

Aucune installation nécessaire. Ouvrez `index.html` dans un navigateur, ou lancez un petit serveur pour tester l'installation et le mode hors connexion :

```bash
python3 -m http.server 8000
# puis ouvrez http://localhost:8000
```

## Mettre en ligne avec GitHub Pages

1. Dans le dépôt sur GitHub : **Settings → Pages**.
2. Source : **Deploy from a branch**, branche `main`, dossier `/ (root)`.
3. Après une minute, l'appli est disponible à l'adresse `https://<votre-pseudo>.github.io/ancre-ton-permis/`.

Sur téléphone, ouvrez cette adresse puis « Ajouter à l'écran d'accueil ».

## Structure

```
index.html              l'appli complète (cours, questions, logique)
manifest.webmanifest    nom, couleurs et icônes pour l'installation
sw.js                   cache pour l'usage hors connexion
icon-*.png              icônes de l'appli
```

Pour ajouter des questions, modifiez le tableau `RAW` dans `index.html` :

```js
["L", "Question ?", ["Réponse A", "Réponse B", "Réponse C"], 1, "Explication."],
// plusieurs bonnes réponses : [0, 2] au lieu de 1
```

Après une modification, changez le numéro de `CACHE` dans `sw.js` (par exemple `v2`) pour que les téléphones récupèrent la nouvelle version.

## Avertissement

Questions et cours rédigés pour l'entraînement : ce n'est pas la banque officielle de l'examen. Les règles peuvent évoluer, vérifiez les points importants sur [securite-routiere.gouv.fr](https://www.securite-routiere.gouv.fr) ou [service-public.fr](https://www.service-public.fr).
