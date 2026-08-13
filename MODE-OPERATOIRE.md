# Remise en ligne — mode opératoire

Neuf pages HTML + une image. Chaque page est **autonome** : style, script et
animation sont à l'intérieur du fichier. Rien d'autre à côté.

---

## 1. Vider le dossier Téléchargements — c'est l'étape qui a tout fait rater

Android ne remplace jamais un fichier existant : il ajoute un numéro. En
téléchargeant `index.html` une dizaine de fois pendant qu'on travaillait, tu as
accumulé `index.html`, `index (1).html`, `index (2).html`… **et le fichier qui
s'appelle exactement `index.html` est le plus ancien de tous.** C'est celui que le
sélecteur de fichiers propose en premier, et c'est celui que tu as envoyé.

Avant de télécharger quoi que ce soit :

1. Ouvre **Mes fichiers** → **Téléchargements**
2. Trie par nom et **supprime tous les fichiers `.html`** qui s'y trouvent
3. Supprime aussi les `og-image.jpg`, `og-image (1).jpg`, etc.

Le dossier doit ne plus contenir aucun de ces fichiers. Ensuite seulement,
télécharge les dix fichiers de ce message.

---

## 2. Vérifier avant d'envoyer — dix secondes

Ouvre `index.html` depuis tes téléchargements et descends tout en bas de la page.

- Tu lis **« © 2026 David Sarrasin — Sion Pixel Art, Sion (VS) »** → c'est la bonne version.
- Tu lis « © 2026 Sion Pixel Art — Sion, Valais » → c'est une vieille copie, recommence l'étape 1.

---

## 3. GitHub

**Ne renomme pas le dépôt pour l'instant.** Une seule chose à la fois, et ce n'est
plus nécessaire : voir le point 5.

1. Ouvre ton dépôt → **Add file** → **Upload files**
2. Sélectionne les **9 fichiers HTML + `og-image.jpg`** — les dix d'un coup
3. Descends en bas de la page et appuie sur **Commit changes**.
   *C'est le bouton qu'on oublie le plus souvent : sans lui, rien n'est enregistré.*
4. Si tu as tout supprimé, il faut **recréer `.nojekyll`** :
   **Add file** → **Create new file** → taper exactement `.nojekyll` → laisser le
   contenu vide → **Commit changes**. Sans ce fichier, GitHub Pages répond 404.
5. **Settings** → **Pages** : vérifie que la source est bien la branche `main`,
   dossier `/ (root)`.

Compte une à deux minutes de reconstruction. Si tu vois encore l'ancienne page,
ouvre le site en **navigation privée** — ton navigateur garde l'ancienne en cache.

---

## 4. Vérifier que c'est passé

Sur GitHub, l'onglet **Commits** doit montrer un envoi daté de maintenant. Dans la
liste des fichiers, les dix doivent afficher la même heure.

Sur le site en ligne, descends en bas de l'accueil : **David Sarrasin** doit
apparaître dans le copyright.

---

## 5. Ce que j'ai changé dans les fichiers, et pourquoi

**Il n'y a plus aucune adresse absolue dans les pages.** Avant, chaque page
contenait trois balises qui pointaient vers `167korn-create.github.io/sion-pixel-art/`
— une adresse qui n'existait pas, puisque ton dépôt s'appelle `Sion_Pixel_Art`.

- La balise `canonical` disait à Google « la vraie page est ici », en désignant une
  adresse en 404. Je l'ai **supprimée** : Google devine très bien l'adresse seul, et
  une balise fausse fait plus de mal que pas de balise.
- `og:url` supprimée pour la même raison.
- `og:image` est devenue **relative** (`og-image.jpg` au lieu de l'adresse complète).

**Conséquence utile :** ces pages fonctionnent maintenant sous n'importe quel nom de
dépôt, et plus tard sous ton propre nom de domaine, **sans qu'une seule ligne soit à
changer**. Le renommage du dépôt devient purement cosmétique — tu le feras quand tu
voudras, ou jamais si tu prends un domaine.

---

## 6. Rappel de ce qu'il y a dans cette version

- **David Sarrasin** comme éditeur et responsable de la publication (mentions
  légales), comme prestataire (conditions générales, article 1), et dans le
  copyright du pied de page.
- Forme juridique **raison individuelle**, **TVA non assujetti** (art. 10 al. 2
  let. a LTVA). Corrige-moi si l'une des deux est fausse.
- Ligne « numéro IDE » retirée : tu n'en as pas encore, rien n'oblige à afficher un
  numéro qu'on ne possède pas.
- Présentation nominative sur l'accueil : « Je m'appelle David Sarrasin, je
  travaille seul depuis Sion. »
- Deux bugs corrigés : les pourcentages affichés en double (`50 %%`), et la barre de
  progression en bas de page qui ne se remplissait jamais.

**Fais relire les trois pages légales par une fiduciaire ou un juriste.** Elles ont
été rédigées par une intelligence artificielle qui n'est pas juriste.

---

## 7. Les dix fichiers

| fichier | poids |
|---|---|
| `index.html` | 33 Ko |
| `sites.html` | 30 Ko |
| `animations.html` | 32 Ko |
| `reprise.html` | 31 Ko |
| `tarifs.html` | 31 Ko |
| `contact.html` | 32 Ko |
| `mentions-legales.html` | 29 Ko |
| `confidentialite.html` | 30 Ko |
| `conditions-generales.html` | 35 Ko |
| `og-image.jpg` | 66 Ko |

Plus `.nojekyll`, à créer directement sur GitHub.

**Ce fichier-ci ne va pas en ligne.** Il est pour toi.
