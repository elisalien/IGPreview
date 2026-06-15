# IG Preview

Outil local de **prévisualisation de feed Instagram** : visualise tes photos candidates en miniatures dans une grille de profil, mélangées à tes posts existants. Aucune publication, aucune connexion à Instagram — tout reste sur ta machine.

## Lancement

Double-clique sur `index.html` (ou ouvre-le dans n'importe quel navigateur). C'est tout.

> Les données (photos, scénarios) sont stockées dans l'IndexedDB du navigateur. Elles persistent entre les sessions mais sont liées au navigateur utilisé.

## Utilisation

| Action | Comment |
|---|---|
| Ajouter des photos candidates | Bouton **＋ Nouvelles photos**, ou glisser-déposer des images n'importe où sur la page. Elles arrivent en haut du feed avec un badge « NOUVEAU ». |
| Charger ton feed existant | Bouton **🖼 Importer une capture du feed** : prends une capture d'écran de ta grille Instagram, ajuste la grille verte (haut, marges, espacement, rangées), et chaque miniature devient un post « existant ». |
| Réorganiser | Glisse-dépose les miniatures dans la grille pour tester l'ordre de publication. |
| Recadrer une miniature | Survole une miniature → bouton ✥ : glisse l'image et zoome (molette ou curseur). |
| Basculer nouveau ↔ existant | Survole une miniature → bouton **N**. |
| Supprimer un post | Survole une miniature → bouton ✕. |
| Personnaliser le profil | Clique sur le pseudo, le nom, la bio ou les stats pour les éditer ; clique sur l'avatar pour changer la photo de profil. Le compteur de publications est automatique. |
| Scénarios | Le menu déroulant en haut à gauche permet de créer / renommer / dupliquer / supprimer plusieurs combinaisons de feed sauvegardées. |
| Badge « NOUVEAU » | Case « Marquer les nouvelles » pour activer/désactiver le marquage visuel. |

## Décisions de conception

- **Page HTML unique** (zéro dépendance, zéro build) — l'outil tient dans `index.html`.
- **Import par capture d'écran découpée** plutôt que scraping ou API Meta : fiable, instantané, aucun risque de blocage de compte. Le scraping Instagram est fragile en 2026 (login-wall) et l'API Graph exige un compte pro + app Meta.
- **Grille 3:4** uniquement — le format de grille actuel d'Instagram (depuis 2025).
- **Stockage IndexedDB** : images en blobs, scénarios multiples, nettoyage automatique des images orphelines au démarrage.

## Limites connues

- Les recadrages sont visuels (préview) — l'outil n'exporte pas les images recadrées.
- Le glisser-déposer de réorganisation est conçu pour la souris (desktop).
- Vider les données de navigation du navigateur efface les scénarios.

## Publier en ligne (GitHub Pages)

Le dépôt étant un site statique mono-fichier, il s'héberge tel quel :

1. Dans **Settings → Pages**, choisis la source **Deploy from a branch**.
2. Branche `main`, dossier `/ (root)`, puis **Save**.
3. L'outil sera disponible à l'adresse `https://<utilisateur>.github.io/<repo>/`.

## Licence

[GPL-3.0](LICENSE) © elisalien
