# Design system hospitality premium — identité visuelle, tokens, composants

> Système réutilisable pour concevoir un site d'hébergement haut de gamme. Il ne prescrit pas une esthétique unique : il donne des palettes types, des associations typographiques, des échelles, des grilles, des ratios, des formes et une bibliothèque de composants documentés, à instancier selon la direction artistique retenue. Niveaux : Indispensable / Recommandé / Signature premium.

## 0. Tokens observés dans le benchmark (mesures Chromium, 2026-09-04)

| Site | Fond | Texte | Accent / bouton | Titres | Corps | Largeur contenu | Rayons | Header |
|---|---|---|---|---|---|---|---|---|
| FORESTIS | #f2f1eb (crème), sections photo sombres | #333333 | aucun bouton plein : liens texte ; blanc sur photo | BrandonTextLight 40 px (H1), 30 px (H2), bas de casse, interlettrage 1–1,5 px, graisse 400 | 20 px / 32 px, centré, largeur 713 px | ≈ 864 px | 0 | transparent sur hero, liens « Menu / Request / Book », logo centré |
| Hotel Corazón | #d0342c (rouge) partout, texture | #371810 (brun) | bandeau brun #371810 / texte rouge ; beige #eadcc7 au hover | Klinsman 48 px (H2), 15 px sur-titres, tout en capitales, interlettrage −1 à 1 px | 18 px / 27 px, capitales, centré, 693 px | 1 080–1 200 px | 0 | fixe, 128 px, fond rouge, logo centré, menu horizontal |
| Borgo Egnazia | #888b8d (gris intro), tuiles photo avec scrim #2b241e à 60 %, #e3e3e3 | #ffffff sur photo, #000 | onglet vertical « BOOK », modale sombre, bouton « Check availability » | Optima 25 px capitales interlettrage 3 px (tuiles), 14 px | 14 px / 21 px (Optima), textes 9 px dans le footer | 1 140 px (Bootstrap) | Bootstrap (≈ 4 px) | fixe 64 px transparent, burger |
| The Seagate | #f2f1ec (crème) | #222222 / #203a4d (bleu marine) | bouton plein #203a4d texte blanc 12 px capitales interlettrage 3 px, 119×40 ; bouton contour 1 px #203a4d 202×44 | Owners 300 : 48 px capitales interlettrage 13 px (H1 de sections), 34 px hero interlettrage 4 px | 16 px / 22 px, 300, centré, 890 px | 1 136–1 340 px | 0 | fixe 112 px crème, logo centré, burger à gauche, bouton à droite ; widget de réservation fixe 248×242 à droite |
| Le Collectionist | #ffffff / #f7f7f7 | #202020, gris #757575 | bouton plein #202020 texte blanc 14 px capitales interlettrage 1 px, hauteur 44–52 ; icônes rondes 40 px (rayon 9999) | Brown 32 px capitales (H2), 24 px (H3), 14 px onglets ; GTAlpina (serif) 60 px pour la signature du hero et les chiffres ; Ayer | 16 px / 22 px | 1 280 px | 0 sur boutons, 9999 sur icônes | 72 px, transparent sur hero, burger + logo à gauche, téléphone + app + favoris + compte à droite |

Enseignements : (1) une seule famille typographique bien choisie suffit à trois sites sur cinq ; (2) le crème (#f2f1eb–#f7f7f7) est la couleur de fond dominante du luxe calme, tandis que la couleur pleine (rouge Corazón) crée une marque « statement » ; (3) les boutons sont rectangulaires (rayon 0) partout, en capitales interlettrées 12–14 px ; (4) les largeurs de contenu texte tournent autour de 700–900 px ; (5) les headers fixes mesurent 64–128 px.

## 1. Palettes types

Une palette = 1 fond principal, 1 fond secondaire, 1 texte, 1 texte atténué, 1 accent (une seule couleur d'action), 1 accent secondaire optionnel, 3 couleurs fonctionnelles (succès, erreur, focus). Toujours vérifier les contrastes (texte 4,5:1, composants 3:1).

| Palette | Pour | Fond principal | Fond secondaire | Texte | Texte atténué | Accent | Accent 2 | Notes |
|---|---|---|---|---|---|---|---|---|
| **Crème & encre** (calme, montagne, wellness) | boutique, chalet, wellness | #f3f1ea | #e8e4d9 | #1f1f1d | #6b675f | #2f3a2f (vert profond) | #b08d57 (laiton) | proche de FORESTIS / Seagate ; l'accent sert uniquement aux CTA |
| **Marine & sable** (mer, club) | 5 étoiles balnéaire, resort | #f4f2ec | #e6e1d5 | #1c2f3d | #5d6b76 | #1c2f3d | #c9a87a | Seagate-like ; bouton plein marine |
| **Pierre & nuit** (Méditerranée, patrimoine) | domaine, 5 étoiles historique | #ece7df | #d8d0c3 | #2b241e | #7a6f63 | #2b241e | #9c7b4f | inspiré des scrims Borgo ; fort contraste nuit/blanc |
| **Couleur pleine** (statement) | boutique à forte personnalité, insolite | une couleur saturée (ex. #c8472f, #2f4f3f, #1d3557) | même teinte −10 % | teinte très sombre de la même famille | idem à 70 % | inversé (fond sombre / texte de la couleur pleine) | crème | Corazón ; exige des photos traitées dans la même gamme |
| **Blanc plateforme** (collection, conciergerie) | collection, agence | #ffffff | #f7f7f7 | #202020 | #757575 | #202020 | #b08d57 | Le Collectionist ; l'image porte la couleur |
| **Forêt & brume** (nature, insolite) | cabanes, lodges, éco-resorts | #eef0ea | #dfe3d9 | #1e2620 | #5f6b62 | #3d5a45 | #c6a15b | — |
| **Nuit & or** (hôtel urbain, bar) | 5 étoiles urbain, membres | #141414 | #1f1f1f | #f2efe8 | #a9a49a | #c9a75f | #f2efe8 | mode sombre par défaut ; attention à la lisibilité des longs textes |

Règles : pas plus d'une couleur saturée ; les photos doivent « entrer » dans la palette (traitement colorimétrique) ; les états hover/focus dérivent de l'accent (−10 % luminosité, ou inversion) ; les couleurs fonctionnelles restent discrètes (erreur #b23a2a, succès #2e6b3f, focus = accent avec anneau 2 px).

## 2. Associations typographiques

| Association | Titres | Texte | Caractère | Pour |
|---|---|---|---|---|
| **Sans géométrique léger seul** | Brandon Text Light / Futura PT Light / Jost Light / Owners Light (graisse 300, bas de casse ou capitales interlettrées) | même famille 400 | calme, contemporain, discret | wellness, montagne, boutique minimal (FORESTIS, Seagate) |
| **Serif à contraste + sans neutre** | GT Alpina / Canela / Ogg / Editorial New / Fraunces (titres 48–72 px, bas de casse) | Brown / Inter / Söhne / Untitled Sans 16–18 px | éditorial, raffiné, chaleureux | 5 étoiles, domaine, collection (Le Collectionist mélange GTAlpina + Brown) |
| **Humaniste classique** | Optima / Albertus / Cormorant Garamond SemiBold en capitales interlettrées | Lato / Source Sans / Nunito Sans | patrimoine, méditerranéen | domaine, hôtel historique (Borgo) |
| **Display de caractère + sans** | Klinsman / Druk / Reckless / une display sur-mesure en capitales | même display ou sans simple | statement, personnalité forte | boutique « rebelle », insolite (Corazón) |
| **Serif transitionnel + serif texte** | Freight Display / Tiempos Headline | Tiempos Text / Freight Text 17–18 px | littéraire, lent | maison d'hôtes, retraites |

Règles (Indispensable) : 2 familles maximum ; 4 fichiers de police maximum ; titres en graisse 300–500 (jamais 700 en display luxe, sauf choix statement) ; capitales seulement avec interlettrage 0,08–0,25 em et taille ≥ 12 px ; bas de casse pour les titres longs ; texte courant 16–20 px, interligne 1,5–1,65, largeur 55–75 caractères.

## 3. Échelle typographique (desktop / mobile)

| Rôle | Desktop | Mobile | Interligne | Interlettrage | Casse |
|---|---|---|---|---|---|
| Display hero | 56–72 px | 34–42 px | 1,05–1,15 | −0,01 à 0,02 em | selon famille |
| H1 page | 44–56 px | 32–38 px | 1,1 | 0–0,02 em (capitales : 0,15–0,25 em) | — |
| H2 section | 32–40 px | 26–30 px | 1,15 | idem | — |
| H3 carte | 22–26 px | 20–22 px | 1,25 | — | — |
| Sur-titre (eyebrow) | 12–13 px | 12 px | 1,4 | 0,15–0,25 em | capitales |
| Corps | 17–20 px | 16–17 px | 1,55–1,65 | 0 | — |
| Corps large (manifeste, citation) | 24–30 px | 20–22 px | 1,4 | 0 | — |
| Petit (légendes, conditions) | 13–14 px | 13 px | 1,45 | 0 | jamais < 12 px |
| Bouton | 12–14 px capitales interlettrage 0,15–0,25 em, ou 16 px bas de casse | idem | — | — | — |

Ratio d'échelle recommandé : 1,25 (majeur tierce) pour les sites calmes ; 1,333 pour les sites statement. FORESTIS utilise 20 / 30 / 40 px (ratio 1,5 puis 1,33) avec très peu de niveaux : la sobriété vient aussi du nombre réduit de tailles (3 tailles sur la home).

## 4. Grille, espacements, proportions

- **Grille** : 12 colonnes, gouttière 24–32 px desktop, 16 px mobile ; largeur max de page 1 280–1 440 px ; largeur max du texte courant 640–720 px ; images pleine largeur autorisées (bleed) pour le hero et 1 à 2 sections par page.
- **Marges latérales** : 20–24 px (mobile), 40–48 px (tablette), 64–120 px (desktop).
- **Rythme vertical** : échelle 4/8 px ; espacements de section 96–160 px desktop, 64–96 px mobile ; entre titre et texte 16–24 px ; entre blocs d'une section 48–64 px.
- **Place du vide** (Signature premium) : au moins 30 % de la hauteur d'une page « calme » est du vide ; FORESTIS enchaîne des sections de 590–900 px avec des marges de 150–220 px entre blocs.
- **Symétrie / asymétrie** : centrer les manifestes et les hero (les cinq sites centrent le hero) ; décaler les grilles d'images (2 colonnes inégales, images décalées verticalement : FORESTIS, Seagate) pour créer du rythme ; garder les listes d'hébergements régulières (comparaison).
- **Ratios d'images** : hero 16:9 (desktop) et 4:5 ou 9:16 (mobile) ; cartes hébergements 4:5 (Le Collectionist 0,74) ou 3:2 (Corazón 1,5) ; expériences 3:2 ou 1:1 (Seagate 1:1 pour les natures mortes) ; pleine largeur 21:9 ou 2:1 (Seagate 2,14) ; portrait 2:3 pour les colonnes éditoriales.

## 5. Formes et composants de base

| Élément | Recommandation | Notes |
|---|---|---|
| Rayons | 0 px (luxe classique / minimal) ou 2–4 px (contemporain) ; 9999 px seulement pour les icônes rondes et les tags | les cinq sites du benchmark sont à 0 px sur les boutons |
| Boutons | hauteur 44–56 px, padding 16–32 px horizontal ; plein (accent) pour l'action principale, contour 1 px pour la secondaire, lien souligné pour la tertiaire ; texte 12–14 px capitales interlettrées ou 16 px bas de casse | un seul bouton plein par viewport |
| Traits et séparateurs | 1 px, couleur texte à 15–20 % d'opacité | pas d'ombres portées lourdes |
| Ombres | aucune ou très diffuse (0 8px 24px rgba(0,0,0,.06)) sur les modales et le widget de réservation | — |
| Icônes | trait 1–1,5 px, 20–24 px, une seule bibliothèque (Lucide, Phosphor Light, ou set sur mesure) ; ou icônes photographiques (natures mortes) | pas de Font Awesome multicolore ; Seagate remplace les icônes par des coquillages photographiés |
| Illustrations | rares : cartes stylisées, plans, motifs discrets (dentelle, bois) en texture à 5–10 % | Corazón utilise un blason dessiné (palmier, cheval ailé) comme ponctuation |
| Textures | grain fin, papier, lin, à opacité ≤ 8 % sur les fonds pleins | — |
| Formulaires | champs hauteur 48–56 px, bordure 1 px, label visible au-dessus, focus anneau 2 px accent | — |
| Tags / badges | capitales 11–12 px, interlettrage 0,15 em, bordure 1 px ou fond secondaire | pour catégories, saisons, « nouveau » |

## 6. Traitement des photos et vidéos dans l'interface

- Scrim sur texte : dégradé vertical noir 0 → 45 % (jamais un voile uniforme opaque à plus de 40 %) ; Borgo utilise un voile brun à 60 %, ce qui assombrit beaucoup : à réserver aux tuiles-menus.
- Cadres : images sans bordure ni rayon ; possibles marges internes (inset) de 40–64 px pour les grilles éditoriales (FORESTIS insère ses images dans la largeur du contenu, pas en pleine largeur).
- Hover : scale 1,04–1,08 ou brightness 0,85 (Corazón) ; jamais les deux.
- Vidéos : toujours dans un conteneur au ratio réservé, poster, bouton pause en bas à droite (32–40 px).

## 7. Cohérence

- Un fichier de tokens unique ; aucune couleur hors tokens ; aucune taille hors échelle.
- Mêmes composants sur toutes les pages, y compris le moteur de réservation s'il est intégré (sinon, thème du moteur aligné : logo, couleurs, police).
- Vérifier la cohérence sur trois écrans : home, page hébergement, moteur.

## 8. Fichier de tokens (modèle)

```
/* Couleurs */
--color-bg: #f3f1ea;
--color-bg-alt: #e8e4d9;
--color-ink: #1f1f1d;
--color-ink-muted: #6b675f;
--color-accent: #2f3a2f;
--color-accent-hover: #24302a;
--color-accent-2: #b08d57;
--color-line: rgba(31,31,29,.16);
--color-scrim: linear-gradient(180deg, rgba(0,0,0,0) 40%, rgba(0,0,0,.45) 100%);
--color-error: #b23a2a; --color-success: #2e6b3f; --color-focus: #2f3a2f;

/* Typographie */
--font-display: "Nom serif", Georgia, serif;
--font-text: "Nom sans", system-ui, sans-serif;
--text-display: clamp(2.25rem, 1.5rem + 3vw, 4.5rem);
--text-h1: clamp(2rem, 1.4rem + 2.2vw, 3.5rem);
--text-h2: clamp(1.625rem, 1.3rem + 1.2vw, 2.5rem);
--text-h3: clamp(1.25rem, 1.1rem + .5vw, 1.625rem);
--text-body: clamp(1rem, .95rem + .3vw, 1.25rem);
--text-small: .875rem; --text-eyebrow: .75rem;
--leading-tight: 1.1; --leading-body: 1.6;
--tracking-caps: .18em;

/* Espacements */
--space-1: 4px; --space-2: 8px; --space-3: 16px; --space-4: 24px; --space-5: 32px; --space-6: 48px; --space-7: 64px; --space-8: 96px; --space-9: 128px; --space-10: 160px;
--container: 1360px; --measure: 68ch; --gutter: 24px; --page-margin: clamp(20px, 5vw, 96px);

/* Formes */
--radius: 0px; --radius-pill: 9999px; --line: 1px;
--shadow-soft: 0 8px 24px rgba(0,0,0,.06);

/* Mouvement : voir motion-guidelines.md §4 */
```

## 9. Bibliothèque de composants

Pour chaque composant : objectif, contenu, comportement, variantes, mobile, erreurs à éviter.

### 9.1 Header
- **Objectif** : identifier la maison, donner accès au menu et à l'action principale depuis n'importe où.
- **Contenu** : logo (centré ou à gauche), menu (burger ou 5–7 liens), CTA principal (Réserver / Demander), langue, téléphone (mobile).
- **Comportement** : transparent sur le hero (texte blanc avec scrim), devient opaque (fond de la palette) après 80 px de scroll ; hauteur 64–96 px (réduite à 56–64 px au scroll) ; option : se cache au scroll vers le bas, réapparaît au scroll vers le haut (FORESTIS).
- **Variantes** : centré (FORESTIS, Corazón, Seagate), aligné à gauche avec outils à droite (Le Collectionist), minimal burger + onglet vertical (Borgo).
- **Mobile** : 56–64 px ; burger + logo + CTA court ; ou CTA pleine largeur sous le logo (Seagate) ; jamais de menu horizontal.
- **Erreurs** : header de 128 px qui mange le hero mobile ; CTA invisible sur fond photo ; logo trop petit ; menu déroulant au hover seulement.

### 9.2 Navigation (menu)
- **Objectif** : trouver un hébergement ou une prestation en une action.
- **Contenu** : 5–7 entrées principales dans l'ordre du parcours ; entrées secondaires (presse, carrières, cadeaux, propriétaires) séparées ; liens externes signalés (boutique, magazine).
- **Comportement** : panneau latéral (Le Collectionist, 395 px) ou plein écran (Seagate) ; ouverture 300–450 ms ; focus piégé ; Escape ; scroll bloqué ; fermeture par croix et par clic hors zone.
- **Variantes** : menu avec image d'aperçu au hover de chaque entrée (Signature premium) ; menu à deux colonnes (principal / secondaire) ; menu bandeau horizontal révélé au scroll vers le haut (FORESTIS : 10 entrées).
- **Mobile** : plein écran, items 20–24 px, cascade ≤ 6, CTA en bas du panneau, téléphone et langue visibles.
- **Erreurs** : plus de 12 entrées au même niveau (Borgo : 20 entrées, dont 9 externes) ; menu qui n'indique pas la page active ; hamburger sans libellé accessible.

### 9.3 Hero
- **Objectif** : la promesse en 5 secondes.
- **Contenu** : média (vidéo ou photo signature), sur-titre optionnel (lieu), titre (2–8 mots), sous-titre (≤ 20 mots), CTA ou moteur, indice de scroll discret.
- **Comportement** : hauteur 85–100 svh desktop, 70–90 svh mobile ; média avec scrim ; titre apparaît en 600–700 ms ; pas de carrousel de slides.
- **Variantes** : plein écran immersif (FORESTIS, Seagate, Borgo) ; hero court 50–60 vh avec barre de recherche (Le Collectionist : 458 px) ; hero « objet » (vidéo dans un cadre sur fond de couleur : Corazón) ; hero éditorial (titre à gauche, image à droite).
- **Mobile** : image ou vidéo verticale, titre 32–40 px, CTA visible, moteur replié en bouton.
- **Erreurs** : titre blanc sur vidéo non chargée sans fond (observé) ; texte de plus de 2 lignes en display ; plusieurs CTA de même poids ; hero de 100 vh sur mobile avec le CTA sous le pli.

### 9.4 Moteur de disponibilité (widget)
- **Objectif** : passer des dates à l'offre en ≤ 3 interactions.
- **Contenu** : arrivée, départ (calendrier à 2 mois desktop, 1 mois mobile), voyageurs (adultes / enfants avec +/−), code promo replié, bouton « Voir les disponibilités » ; bénéfices directs à côté (2–3 lignes).
- **Comportement** : dans le hero (Seagate : colonne fixe 248×242 à droite) ou en barre horizontale (Le Collectionist : 4 champs + bouton) ; devient sticky réduit après le hero ; pré-rempli depuis les pages hébergement ; erreurs en ligne ; envoie vers le moteur avec les paramètres dans l'URL.
- **Variantes** : modale déclenchée par un onglet fixe (Borgo : « BOOK » vertical → modale check-in / check-out / adults / children) ; formulaire de demande (villa, conversationnel) : dates souhaitées, souplesse, personnes, message.
- **Mobile** : bouton « Réserver » qui ouvre un panneau plein écran avec les champs empilés.
- **Erreurs** : widget qui masque la photo du hero ; champs sans label ; calendrier non tactile ; départ possible avant arrivée ; pas de message si indisponible.

### 9.5 Carte hébergement
- **Objectif** : comparer et choisir.
- **Contenu** : image 4:5 ou 3:2, nom propre, accroche (≤ 15 mots), ligne de faits (m² · personnes · vue), prix « à partir de », CTA « Découvrir » + lien « Disponibilités ».
- **Comportement** : toute la carte cliquable ; hover image scale 1,04 ou brightness 0,85 + titre souligné ; favoris optionnel (collection).
- **Variantes** : grille 2 colonnes (Corazón : 12 chambres en 2×6) ; grille 3 colonnes (Le Collectionist) ; liste éditoriale image + texte alternés (Seagate : catégorie + icône photo + image + description) ; slider horizontal.
- **Mobile** : 1 colonne ; image 4:5 ; prix et CTA visibles.
- **Erreurs** : cartes sans prix ni capacité ; nom générique ; hover qui déplace la carte ; 12 cartes identiques sans hiérarchie (proposer 3 mises en avant puis « toutes les chambres »).

### 9.6 Galerie
- **Objectif** : projeter le client dans l'espace.
- **Contenu** : 8–15 images ordonnées (large → moyen → détail), légendes, compteur.
- **Comportement** : carrousel avec flèches (FORESTIS, Corazón : flèches fines latérales + points) ou mosaïque (Le Collectionist : 1 grande + 4 petites + « Voir toutes les photos (36) ») ; lightbox plein écran avec clavier et swipe ; lazy loading ; dimensions réservées.
- **Variantes** : masonry éditorial (FORESTIS : 2 colonnes décalées) ; défilement horizontal natif ; vidéo en première position.
- **Mobile** : défilement horizontal, compteur « 3/12 », tap = plein écran.
- **Erreurs** : autoplay ; images de ratios différents dans un même carrousel ; sans flèches ni indicateurs ; miniatures minuscules.

### 9.7 Section expérience
- **Objectif** : prouver la promesse par des moments.
- **Contenu** : 3–4 expériences : image, titre-sensation, 20–40 mots, lien.
- **Comportement** : grille ou alternance image/texte ; révélation au scroll.
- **Variantes** : bloc sticky (image fixe, textes qui défilent) ; slider horizontal ; mosaïque verticale (Le Collectionist : 4 images 2:3 décalées).
- **Mobile** : empilé, 1 image par expérience.
- **Erreurs** : icônes génériques à la place des photos ; textes interchangeables.

### 9.8 Section destination
- **Objectif** : ancrer dans le lieu et rassurer sur l'accès.
- **Contenu** : 2–3 images du territoire, 40–80 mots, distances (aéroport, gare, ville), carte stylisée ou lien vers la page accès, saisons.
- **Comportement** : carte interactive uniquement sur la page contact/accès ; ici une image ou une carte statique.
- **Mobile** : image + 3 distances + lien.
- **Erreurs** : carte Google brute non stylisée dans la home ; oublier les temps de trajet.

### 9.9 Témoignages
- **Objectif** : preuve sociale crédible.
- **Contenu** : 2–3 verbatims ≤ 25 mots, prénom, ville, date, source ; note globale avec source (Google 4,8/5 – 312 avis) ; lien vers les avis.
- **Comportement** : statique ou slider lent (8 s, pause au hover, flèches).
- **Variantes** : citation des hôtes en grand (FORESTIS : 30 px) ; carnet de souvenirs de clients (Le Collectionist : « Leurs souvenirs » avec note 4,8/5 et date).
- **Mobile** : 1 verbatim visible, swipe.
- **Erreurs** : avis anonymes ; slider automatique rapide ; logos de plateformes en couleurs vives.

### 9.10 Récompenses et labels
- **Objectif** : légitimité en un regard.
- **Contenu** : 3–6 logos vectoriels monochromes (Michelin, Small Luxury Hotels, LHW, Condé Nast, Gault&Millau, écolabels), année.
- **Comportement** : ligne discrète en pied de page (FORESTIS, Borgo, Seagate : Turnberry + Marriott Bonvoy) ou dans la section preuve ; monochrome, hauteur 24–40 px.
- **Mobile** : 2 lignes max, centré.
- **Erreurs** : logos en couleur de tailles différentes ; badges de widgets tiers.

### 9.11 Services (table, spa, conciergerie)
- **Objectif** : étendre le désir et le panier.
- **Contenu** : image large, titre-sensation, 2 phrases, CTA spécifique (Réserver une table / un soin).
- **Variantes** : alternance image/texte (Seagate) ; bandeau plein largeur 21:9.
- **Mobile** : image puis texte, CTA en bouton contour.

### 9.12 Conciergerie / contact humain
- **Objectif** : ouvrir un canal humain, réduire l'incertitude.
- **Contenu** : portrait ou prénom d'un interlocuteur, promesse de délai (« réponse sous 24 h »), téléphone, WhatsApp, e-mail, bouton « Planifier un appel » (Le Collectionist : conseiller nommé + « Planifier un appel »).
- **Comportement** : bloc sur la home, les pages hébergement et le footer ; formulaire court (4 champs).
- **Mobile** : boutons d'appel / message en ligne ; barre basse fixe possible (FORESTIS : téléphone / e-mail / localisation).
- **Erreurs** : chat bot intrusif ; formulaire de 12 champs ; pas de délai de réponse.

### 9.13 FAQ
- **Objectif** : lever les objections sans e-mail.
- **Contenu** : 5–8 questions réelles (arrivée, enfants, animaux, annulation, accès, parking, petit-déjeuner, saison) ; réponses ≤ 60 mots.
- **Comportement** : accordéons (un ouvert à la fois ou tous), balisage `FAQPage`.
- **Mobile** : accordéons pleine largeur, cible 48 px.
- **Erreurs** : questions marketing (« Pourquoi nous choisir ? »).

### 9.14 Contact
- **Objectif** : joindre et venir.
- **Contenu** : coordonnées, horaires, formulaire court, accès (temps depuis aéroport/gare, parking), carte stylisée, FAQ.
- **Mobile** : boutons tel/mail/itinéraire en haut.

### 9.15 Footer
- **Objectif** : clore, orienter, rassurer.
- **Contenu** : logo, adresse, téléphone, e-mail, plan du site en 2–3 colonnes, réseaux, newsletter, labels, langue, légal.
- **Comportement** : fond contrasté (marine Seagate) ou même fond que la page avec un trait (FORESTIS) ; textes ≥ 13 px.
- **Mobile** : colonnes empilées ou accordéons ; coordonnées cliquables.
- **Erreurs** : textes 9 px (Borgo) ; footer plus riche que le menu ; liens légaux en boutons.

### 9.16 CTA sticky
- **Objectif** : réserver ou demander sans remonter.
- **Contenu** : prix « à partir de » + bouton ; ou onglet latéral (Borgo : « BOOK » vertical à droite, 46×140).
- **Comportement** : apparaît après le hero, disparaît quand le moteur ou le footer est visible ; fond opaque ou flouté ; hauteur 56–64 px (barre) ; toujours au-dessus du bandeau cookies.
- **Mobile** : barre basse pleine largeur ; ne pas cumuler avec un autre élément fixe en bas.
- **Erreurs** : masquer le contenu ; deux CTA fixes ; bouton flottant rond sans texte.

### 9.17 Bandeau d'offre
- **Objectif** : promouvoir une offre sans dégrader la marque.
- **Contenu** : une phrase (≤ 12 mots) + lien ; dates.
- **Comportement** : au-dessus du header, 36–44 px, fermable, mémorisé ; ou dans la section offres.
- **Erreurs** : pop-up à l'arrivée ; compte à rebours ; couleurs criardes ; bandeau non fermable sur mobile.

### 9.18 Newsletter
- **Objectif** : garder le lien.
- **Contenu** : promesse concrète (« une lettre par saison : ouverture des réservations, recettes, sentiers »), 1 champ e-mail, consentement, confirmation.
- **Comportement** : en bas de page ; jamais en pop-up ; double opt-in.
- **Mobile** : champ + bouton empilés.
