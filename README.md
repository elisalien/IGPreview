# IG Preview

> Outil local de prévisualisation de feed Instagram : teste l'ordre de tes prochaines photos dans ta grille de profil, sans rien publier.

![Platform](https://img.shields.io/badge/platform-Web-informational) ![Stack](https://img.shields.io/badge/stack-HTML%20%2F%20CSS%20%2F%20JS-orange) ![License](https://img.shields.io/badge/license-GPL--3.0-green)

## À propos

IG Preview visualise tes photos candidates en miniatures dans une grille de profil Instagram, mélangées à tes posts existants. Aucune publication, aucune connexion à Instagram depuis l'outil — tout reste sur ta machine. L'outil tient dans un seul fichier `index.html`, sans dépendance ni étape de build.

## Fonctionnalités

- Ajout de photos candidates (bouton ou glisser-déposer), marquées d'un badge « NOUVEAU » optionnel.
- Import du feed existant à partir d'une capture d'écran de ta grille, découpée automatiquement selon une grille ajustable.
- Import d'un profil via un bookmarklet « Siphon IGPreview » exécuté dans ton navigateur déjà connecté (export `.json`, rien ne passe par un serveur tiers).
- Réorganisation des miniatures par glisser-déposer.
- Recadrage visuel de chaque miniature (déplacement + zoom).
- Profil éditable : pseudo, nom, bio, stats, avatar ; compteur de publications automatique.
- Scénarios multiples : créer, renommer, dupliquer, supprimer des combinaisons de feed.
- Grille au format 3:4 (format de grille actuel d'Instagram depuis 2025).
- Stockage persistant dans l'IndexedDB du navigateur.

## Installation

Double-clique sur `index.html` (ou ouvre-le dans n'importe quel navigateur). C'est tout.

Pour le servir en local (configuration présente dans `.claude/launch.json`) :

```bash
python -m http.server 8765
```

puis ouvre `http://localhost:8765`.

> Les données (photos, scénarios) sont stockées dans l'IndexedDB du navigateur. Elles persistent entre les sessions mais sont liées au navigateur utilisé.

### Publier en ligne (GitHub Pages)

Le dépôt étant un site statique mono-fichier, il s'héberge tel quel :

1. Dans **Settings → Pages**, choisis la source **Deploy from a branch**.
2. Branche `main`, dossier `/ (root)`, puis **Save**.
3. L'outil sera disponible à l'adresse `https://<utilisateur>.github.io/<repo>/`.

## Utilisation

| Action | Comment |
|---|---|
| Ajouter des photos candidates | Bouton **＋ Nouvelles photos**, ou glisser-déposer des images n'importe où sur la page. Elles arrivent en haut du feed avec un badge « NOUVEAU ». |
| Charger ton feed existant | Bouton **🖼 Importer une capture du feed** : prends une capture d'écran de ta grille Instagram, ajuste la grille verte (haut, marges, espacement, rangées), et chaque miniature devient un post « existant ». |
| Siphonner un compte | Bouton **🔗 Siphonner un compte** : glisse le bouton « Siphon IGPreview » dans ta barre de favoris, ouvre `instagram.com/le_compte`, scrolle pour charger les posts voulus, clique le favori → un fichier `.json` se télécharge ; importe-le ensuite via **📂 Importer un fichier siphonné (.json)**. |
| Réorganiser | Glisse-dépose les miniatures dans la grille pour tester l'ordre de publication. |
| Recadrer une miniature | Survole une miniature → bouton ✥ : glisse l'image et zoome (molette ou curseur). |
| Basculer nouveau ↔ existant | Survole une miniature → bouton **N**. |
| Supprimer un post | Survole une miniature → bouton ✕. |
| Personnaliser le profil | Clique sur le pseudo, le nom, la bio ou les stats pour les éditer ; clique sur l'avatar pour changer la photo de profil. Le compteur de publications est automatique. |
| Scénarios | Le menu déroulant en haut à gauche permet de créer / renommer / dupliquer / supprimer plusieurs combinaisons de feed sauvegardées. |
| Badge « NOUVEAU » | Case « Marquer les nouvelles » pour activer/désactiver le marquage visuel. |

### Décisions de conception

- **Page HTML unique** (zéro dépendance, zéro build) — l'outil tient dans `index.html`.
- **Import par capture d'écran découpée** plutôt que scraping ou API Meta : fiable, instantané, aucun risque de blocage de compte. Le scraping Instagram est fragile en 2026 (login-wall) et l'API Graph exige un compte pro + app Meta.
- **Grille 3:4** uniquement — le format de grille actuel d'Instagram (depuis 2025).
- **Stockage IndexedDB** : images en blobs, scénarios multiples, nettoyage automatique des images orphelines au démarrage.

### Limites connues

- Les recadrages sont visuels (préview) — l'outil n'exporte pas les images recadrées.
- Le glisser-déposer de réorganisation est conçu pour la souris (desktop).
- Vider les données de navigation du navigateur efface les scénarios.

## Structure du projet

| Fichier | Rôle |
|---|---|
| `index.html` | L'outil complet (HTML, CSS et JavaScript). |
| `LICENSE` | Texte de la licence GPL-3.0. |
| `.nojekyll` | Désactive Jekyll pour l'hébergement GitHub Pages. |
| `.claude/launch.json` | Configuration du serveur local (`python -m http.server 8765`). |

## Stack technique

HTML, CSS, JavaScript vanilla, IndexedDB.

## Crédits & licence

Réalisé par elisalien. Distribué sous licence [GPL-3.0](LICENSE).

---

<p align="center">
  Fait par <a href="https://github.com/elisalien">Élisalien</a> ·
  <a href="https://gitlab.com/elisalien/catalog">Catalogue des shaders, sources & logiciels</a>
</p>
