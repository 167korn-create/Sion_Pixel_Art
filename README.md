# Sion Pixel Art — site portfolio

Site vitrine d'une page pour l'activité de création de sites web de David, à Sion.
L'animation d'accueil sert aussi de démonstration : c'est l'argument de vente de la
formule « Immersive ».

## Fichiers

| fichier | rôle | poids |
|---|---|---|
| `index.html` | **tout le site, photo comprise** | 172 Ko |
| `og-image.jpg` | vignette des aperçus WhatsApp / Messenger, 1200 × 630 | 74 Ko |
| `.nojekyll` | fichier vide, obligatoire sinon GitHub Pages reste en 404 | 0 |

**La photo est maintenant à l'intérieur d'`index.html`.** Tu peux ouvrir le fichier
directement depuis tes téléchargements, sans rien d'autre à côté, et l'animation
fonctionne. C'est ce qui manquait à la version précédente : elle allait chercher un
`valere.jpg` séparé, donc sans lui tu ne voyais rien du tout.

172 Ko reste très loin du seuil qui avait posé problème sur ton téléphone (740 Ko).
Seule `og-image.jpg` doit rester un fichier séparé : les robots d'aperçu de WhatsApp
ne savent pas lire une image intégrée.

---

## Déploiement

1. GitHub → **New repository** → nom `sion-pixel-art` → **Public** → **Create repository**
2. **Add file → Upload files** → `index.html`, `og-image.jpg`, `README.md` → **Commit**
3. **Add file → Create new file** → taper exactement `.nojekyll` → laisser vide → **Commit**
4. **Settings → Pages** → Source **Deploy from a branch** → branche **main**, dossier **/ (root)** → **Save**
5. L'adresse apparaît en haut de cette même page Pages : `167korn-create.github.io/sion-pixel-art/`

⚠️ Ne rien écrire dans **Custom domain** avant d'avoir acheté le domaine et configuré
les 4 enregistrements A.

---

## L'animation d'accueil

Plus aucun dessin, plus aucun pixel : **c'est ta photo, découpée en briques fines**
— 15 px sur grand écran, 12 px sur téléphone, soit environ 2 900 briques sur écran
large et 1 800 sur téléphone.

Deux couches, du fond vers l'avant :

1. **Le ciel.** Ta photo à pleine lumière, détourée le long de la silhouette du
   rocher. Le ciel ne se bâtit pas, il est déjà là. En dessous, **rien** : le
   château et son rocher se découpent en ombre chinoise noire.
2. **Les assises posées.** La photo à pleine lumière, révélée du bas vers le haut,
   avec un liseré chaud le long de l'assise en cours — la pierre s'allume au moment
   où elle se pose.

Par-dessus, seules les briques réellement en vol sont dessinées une par une : environ
250 à 350 à un instant donné, sur les 2 900. C'est ce qui permet des briques aussi
fines sans faire souffrir le téléphone. Elles prennent la lumière des projecteurs
pendant leur vol, sinon celles qui portent un morceau de rocher noir passaient pour
des trous dans le ciel.

**À la fin, la photo est redessinée d'un seul trait** : aucune jointure, aucune grille,
c'est ton image intacte.

### Le détail technique qui rend tout possible

Les briques se posent dans un ordre strict : rangée du bas d'abord, puis de gauche à
droite. Du coup, à tout instant, l'ensemble de ce qui est déjà posé forme **deux
rectangles** — les rangées complètes du bas, plus le début de la rangée en cours.
Deux appels de dessin suffisent donc pour tout le déjà-bâti, quel que soit le nombre
de briques. Sans cette astuce, il aurait fallu redessiner 2 900 morceaux à chaque
image, et il aurait fallu se contenter de gros morceaux.

### La photo a été préparée

- **Échafaudage retiré par recadrage.** Ta photo montre la tour d'échafaudage des
  travaux, à gauche. Je n'ai rien retouché ni inventé de pixels : j'ai recadré juste
  à sa droite. La braise du couchant est conservée sur le bord gauche.
- Ramenée à 1600 px, JPEG qualité 78, progressif.
- La palette du site entier est relevée sur cette photo.

### Si tu changes de photo

Le code contient une liste `HORIZON` : 72 mesures de la silhouette, de gauche à droite,
en fraction de la hauteur de l'image. C'est elle qui dit où s'arrête le ciel. **Elle
doit être refaite en même temps que la photo**, sinon le ciel sera détouré au mauvais
endroit. Envoie-moi la nouvelle photo, je regénère les deux ensemble.

### Réglages faciles à toucher

Tout en haut du `<script>`, dans `CFG` :

- `brique` / `briqueMobile` — taille des morceaux. Plus petit = plus fin, mais plus
  lourd. En dessous de 10 px, ça devient de la poussière et on ne lit plus l'effet.
- `fantome` — à **0** aujourd'hui : rien derrière, ombre chinoise noire. Le passer à
  `0.34` fait réapparaître le château en sourdine derrière le chantier, comme dans la
  version précédente. Un seul chiffre à changer si tu veux comparer.
- `debut` / `fin` — à quel moment du défilement le chantier commence et se termine.

Le code mesure aussi son temps de rendu : au-delà de 12 ms par image, il retire
rotation et ombre portée. Et `prefers-reduced-motion` est respecté — la photo
s'affiche alors entière, le héros ne fait plus qu'un écran de haut.

---

## À trancher avant de montrer le site à un client

### Bloquant

- [ ] **Le numéro de téléphone.** La dictée donnait deux lectures, toutes deux valides
      comme mobile suisse :
      - `076 807 82 03`
      - `078 203 78 64`
      Le site affiche `[numéro à confirmer]`. Une fois tranché, remplacer le texte
      **et** poser le lien : `<a href="tel:+41768078203">`.
- [ ] **L'adresse e-mail** — pas encore donnée. Affichée `[votre adresse e-mail]`.

### Vérifications

- [ ] **`Route de Vissigen 22, 1950 Sion`** — la dictée disait « route de Vigan ».
      Vérifié : il existe bien une *Route de Vissigen* à 1950 Sion (environ 3,3 km).
      Confirme quand même l'orthographe.
- [ ] **Adresse privée rendue publique.** Normal pour une entreprise suisse, mais c'est
      ton domicile. On peut n'afficher que « Sion, Valais ».
- [ ] **Balises `og:url` / `og:image`** à corriger si l'adresse finale change.

### Le nom

Il ne reste plus rien de « pixel » dans le site : ni fonte bitmap, ni graphisme en
blocs. **« Sion Pixel Art » mérite peut-être d'être rediscuté.** Ou assumé autrement :
le site construit bien ses images à partir de briques. À toi de voir.

### Identité de l'émetteur

ALPKING a été retiré : tu m'as dit que ça n'existe pas. Le pied affiche
« Sion Pixel Art · Sion, Valais ».

- [ ] Je n'ai **pas** mis `abracadabra0420` sur le site public, et je préfère te dire
      pourquoi plutôt que de le faire en silence :
      - « 0420 » est très largement lu comme une référence au cannabis. Sur un site qui
        vend de 1 500 à 8 000 CHF à des artisans et PME valaisannes, c'est un risque
        gratuit.
      - Un client qui engage plusieurs milliers de francs cherche un nom de personne
        responsable, pas un pseudo.
      Si tu veux quand même l'afficher, dis-le et je le remets.
- [ ] **Forme juridique.** En Suisse, une raison individuelle doit porter le nom de
      famille de son titulaire ; « Sion Pixel Art » reste utilisable comme enseigne.
      Le site peut donc s'appeler ainsi, mais devis et factures devront porter ton nom.
      Je ne suis pas juriste — à vérifier au registre du commerce du Valais ou auprès
      d'une fiduciaire avant de facturer.

### Contenu que j'ai inventé et qui t'engage

- [ ] **« 72 heures pour une page, une semaine pour un site complet »** (section Méthode)
- [ ] **« Deux tours de retouches compris »**
- [ ] **Les prix.** Cohérents avec le marché romand. Deux remarques :
      - Affichés en « dès X CHF », fourchette en petit dessous : afficher la fourchette
        en grand invite à négocier vers le bas.
      - Le **suivi à 150-250 CHF/mois** est élevé pour un site statique — rien à mettre
        à jour techniquement. Défendable seulement si le forfait comprend de vraies
        retouches de contenu. Sinon 200-400 CHF/an est plus tenable, et plus facile à
        vendre à un artisan.
- [ ] Aucun témoignage n'a été inventé.

---

## Historique

### V5 — 12.08.2026
- **Plus rien derrière.** Le fantôme du château est retiré : sous le ciel, ombre
  chinoise noire, et tout se construit à la brique. Le réglage reste accessible
  (`fantome`, à 0) pour revenir en arrière d'un chiffre.
- Halo lumineux supprimé : sur fond noir il faisait une tache grise. Il ne reste
  qu'un liseré chaud, discret, sur l'assise en cours.

### V4 — 12.08.2026
- **La photo est intégrée dans `index.html`.** La V3 allait chercher un fichier
  séparé : sans lui, l'écran d'accueil restait vide.
- Briques ramenées de 36 px à 15 px (12 px sur téléphone) : environ 2 900 morceaux
  au lieu de 570
- Le vrai château est visible dès le départ, en fantôme froid et sombre, et s'allume
  à mesure que les assises se posent
- Lueur chaude sur l'assise en cours ; les briques en vol prennent la lumière
- Le déjà-posé est dessiné en deux rectangles au lieu d'une brique à la fois : c'est
  ce qui a permis de descendre à des morceaux aussi fins

### V3 — 12.08.2026
- Passage du pixel art à la photo elle-même, découpée en briques
- Photo recadrée pour exclure l'échafaudage
- Ciel détouré au tracé continu de la silhouette
- Silkscreen remplacée par IBM Plex Mono

### V2 — 12.08.2026
- Monument refait depuis la photo de Valère ; Tourbillon supprimé
- Palette relevée sur la photo ; ALPKING retiré, adresse ajoutée

### V1 — 11.08.2026
- Structure de la page ; moteur voxel maison, deux collines sur fond de nuit
