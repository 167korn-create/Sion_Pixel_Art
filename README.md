# Sion Pixel Art — site portfolio

Site vitrine d'une page pour l'activité de développement web de David, à Sion.
Structure reprise de la concurrence directe (mydmc.ch, Sion), contenu et
positionnement adaptés à un indépendant plutôt qu'à une agence.

## Fichiers

| fichier | rôle | poids |
|---|---|---|
| `index.html` | **tout le site** — aucune image, aucune bibliothèque | 34 Ko |
| `og-image.jpg` | vignette des aperçus WhatsApp / Messenger, 1200 × 630 | 64 Ko |
| `.nojekyll` | fichier vide, obligatoire sinon GitHub Pages reste en 404 | 0 |

Le site pèse 34 Ko. La photo du château a été retirée, il n'y a plus une seule
image dans la page : le fond est calculé.

---

## Déploiement

1. GitHub → **New repository** → nom `sion-pixel-art` → **Public** → **Create repository**
2. **Add file → Upload files** → `index.html`, `og-image.jpg`, `README.md` → **Commit**
3. **Add file → Create new file** → taper exactement `.nojekyll` → laisser vide → **Commit**
4. **Settings → Pages** → Source **Deploy from a branch** → branche **main**, dossier **/ (root)** → **Save**
5. L'adresse apparaît en haut de cette même page Pages.

---

## Le fond fractal

Un réseau qui se ramifie depuis un point unique, en cinq bras, et qui **pousse à
mesure que la page défile** : au premier écran il n'y a presque rien, en bas de
page la structure est complète — environ 2 976 branches. L'ensemble tourne très
lentement du haut au bas de la page.

Aucune image, aucune bibliothèque, aucun fichier vidéo. Le hasard est
déterministe : chaque nœud tire ses angles d'une fonction de son propre indice,
donc la figure est toujours la même et il n'y a rien à stocker entre deux images.

**Ce qui rend ça tenable sur téléphone** : les branches sont groupées par niveau
de ramification, et chaque niveau est tracé d'un seul trait. Neuf appels de dessin
pour près de trois mille branches, au lieu de trois mille.

Le dégradé est volontairement inversé — braise au cœur, froid et effacé aux
pointes. Dans l'autre sens, la couronne dense devenait un massif lumineux et le
texte ne se lisait plus par-dessus.

### Réglages, tout en haut du `<script>`

- `profMax` (8) — niveaux de ramification. 9 double la finesse et le coût.
- `echelle` (0.128) — taille de la figure. Plus grand = elle déborde de l'écran.
- `bras` (5) — 6 ou 7 donnent une figure plus dense et plus symétrique.
- `rotation` (0.20) — rotation du haut au bas de la page. 0 pour la figer.
- `opacite` (0.90) — à baisser si le texte devient dur à lire par-dessus.

Le code mesure son temps de rendu : au-delà de 12 ms par image, il retire le
dernier niveau de ramification et les pointes lumineuses.

---

## Le bloc contact

Repris sur celui de mydmc.ch, qui est la meilleure partie de leur site : grand
titre sur deux lignes, puis quatre entrées étiquetées — Téléphone, E-mail,
Localisation, WhatsApp. Un bloc **Réseaux** est déjà écrit dans le HTML, en
commentaire : il suffit de retirer les balises `<!--` et `-->` et de mettre la
vraie adresse le jour où le compte existe.

En face, ce que MYDMC renvoie vers une autre page : **un formulaire de devis**.
Il tient dans la page, avec une liste déroulante qui reprend tes formules — ça te
fait arriver la demande déjà qualifiée.

### Comment il marche, et sa limite

Un site statique n'a pas de serveur pour recevoir un envoi de formulaire. Le
bouton **compose donc un e-mail déjà rempli et ouvre l'application de courrier** :
le visiteur n'a plus qu'à appuyer sur envoyer.

- Sur téléphone, ça marche bien : Gmail ou Mail s'ouvre avec tout le texte dedans.
- Sur un ordinateur sans logiciel de messagerie configuré, il ne se passe rien de
  visible. C'est pour ça que le téléphone, l'e-mail et WhatsApp restent affichés
  juste à côté, en clair et cliquables.
- **Défaut réel** : tu ne sauras jamais combien de personnes ont commencé à
  remplir puis abandonné.

Si tu veux un vrai envoi, sans quitter le statique : **Formspree** ou **Web3Forms**
donnent une adresse à mettre dans `action=""`, gratuite jusqu'à environ 50 messages
par mois, et le message arrive directement dans ta boîte. Une ligne à changer.
Dis-le moi et je le branche.

---

## Ce que j'ai repris de mydmc.ch, et ce que j'ai écarté

**Repris** : l'en-tête fixe, l'étiquette au-dessus de chaque section, les grands
titres d'affirmation, la grille de cartes de prestations, la liste numérotée
01–06, le bandeau de chiffres, la structure du bloc contact, les deux boutons
d'appel à l'action dans le héros.

**Écarté volontairement :**

- **Les logos clients** (« Ils nous font confiance »). Tu n'as pas encore de
  références publiables — en inventer se verrait, et un artisan valaisan appelle
  pour vérifier. C'est la section à ajouter en premier dès qu'un vrai client
  accepte d'être cité. Espace Nouvel Air peut être le premier, avec l'accord de Gaël.
- **La page équipe.** Tu es seul. MYDMC affiche cinq personnes et une mascotte ;
  jouer à l'agence contre une vraie agence est un combat perdu d'avance.
- **Les chiffres de notoriété** (« 2021 fondée », « 100+ projets »). Remplacés par
  quatre chiffres qui sont vrais et vérifiables en regardant le site : 1 fichier,
  0 dépendance, 0 abonnement, Valais.
- **L'étendue de l'offre** (vidéo, NFC, community management, merchandising).
  La section Prestations dit explicitement ce que tu ne fais pas et renvoie
  ailleurs. C'est ce qui te distingue d'eux, pas ce qui te dessert.

---

## Coordonnées en place

- Téléphone : **078 203 78 64** — lien d'appel et lien WhatsApp actifs
- E-mail : **167korn@gmail.com** — lien avec objet pré-rempli
- Adresse : **Route de Vissigen 22a, 1950 Sion**
- Pied de page : **Fait par Abracadabra0420**

### Une remarque sur l'e-mail

`167korn@gmail.com` fonctionne, mais face à un artisan qui signe pour 3 000 francs,
une adresse au nom du domaine (`contact@sionpixelart.ch`) change la perception —
c'est souvent compris entre 10 et 30 CHF par an chez le registrar, et la
redirection vers ta boîte Gmail se configure en dix minutes. À faire en même temps
que l'achat du domaine.

---

## À trancher avant de démarcher

- [ ] **Nom.** Il ne reste plus rien de « pixel » dans le site. « Sion Pixel Art »
      reste défendable, mais mérite d'être arrêté une bonne fois : c'est ce que tu
      diras au téléphone pendant les deux prochaines années.
- [ ] **Forme juridique.** En Suisse, une raison individuelle doit porter le nom de
      famille de son titulaire ; « Sion Pixel Art » reste utilisable comme enseigne
      commerciale. Le site peut donc s'appeler ainsi, mais devis et factures devront
      porter ton nom. Je ne suis pas juriste — à vérifier au registre du commerce du
      Valais ou auprès d'une fiduciaire avant de facturer.
- [ ] **Mentions légales.** Pas obligatoires pour un site vitrine sans formulaire ni
      cookie ; à prévoir dès qu'un formulaire de contact est ajouté (LPD).
- [ ] **Adresse privée rendue publique.** Normal pour une entreprise suisse, mais
      c'est ton domicile. On peut n'afficher que « Sion, Valais ».

### Contenu que j'ai écrit et qui t'engage

- [ ] **« Réponse sous 24 heures ouvrables »** (bloc contact)
- [ ] **« 72 heures pour une page, une semaine pour un site complet »**
- [ ] **« Deux tours de retouches compris »**
- [ ] **« Mise en ligne et domaine compris dans chaque formule »**
- [ ] **Les prix.** Le **suivi à 150-250 CHF/mois** reste élevé pour un site
      statique : rien à mettre à jour techniquement. Défendable seulement si le
      forfait comprend de vraies retouches de contenu ; sinon 200-400 CHF/an est
      plus tenable et plus facile à vendre.

---

## Historique

### V7 — 12.08.2026
- Bloc contact refait sur le modèle de mydmc.ch : grand titre sur deux lignes,
  quatre entrées étiquetées, bloc Réseaux prêt en commentaire
- Ajout d'un formulaire de devis avec liste déroulante des formules. Sans serveur :
  il compose un e-mail pré-rempli. Coordonnées directes maintenues à côté.

### V6 — 12.08.2026
- **Photo du château supprimée**, remplacée par une fractale calculée. Le site ne
  contient plus aucune image : 172 Ko → 29 Ko.
- Structure de page refaite sur le modèle de mydmc.ch (cartes de prestations,
  bandeau de chiffres, deux boutons dans le héros, en-tête avec bouton Devis)
- Fond fixé derrière toute la longueur de la page, croissance liée au défilement
  total du document et non plus au seul héros — donc beaucoup plus lente
- Coordonnées réelles en place ; crédit « Fait par Abracadabra0420 »

### V5 — 12.08.2026
- Fantôme du château retiré, halo supprimé

### V4 — 12.08.2026
- Photo intégrée dans le HTML, briques ramenées à 15 px

### V3 — 12.08.2026
- Passage du pixel art à la photo découpée en briques

### V2 — 12.08.2026
- Monument refait depuis la photo de Valère ; Tourbillon supprimé

### V1 — 11.08.2026
- Structure de la page ; moteur voxel maison, deux collines sur fond de nuit
