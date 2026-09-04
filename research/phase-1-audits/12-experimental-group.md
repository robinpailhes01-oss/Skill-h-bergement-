# Fiche d'audit — Experimental Group (`experimental`)

## 0. En-tête

- **Nom** : Experimental (Experimental Group) — groupe d'hospitalité fondé à Paris en 2007 (bar à cocktails), devenu réseau d'hôtels, restaurants, bars, beach clubs, night clubs, spas et boutiques ; 13 destinations actives + 3 annoncées « Coming Soon » (Rome, Comporta, Porto) dans le menu ; « Showing results (70) » sur la carte de la home, « 62 results » sur `/explore`.
- **URL de départ** : https://www.experimentalgroup.com/
- **Date** : 2026-09-04 (captures 17:42 → 17:53 UTC, passe complémentaire jusqu'à ~18:30 UTC), Chromium headless 1440×900 et 390×844 (DPR 2), Playwright.
- **Nature** : marque ombrelle multi-lieux. La rubrique 9 traite la **page hôtel** (Experimental Chalet Val d'Isère), la **page restaurant** fille (L'Aigle d'Or) et, en complément, Cowley Manor (Cotswolds).

| Label | URL | Desktop | Mobile |
|---|---|---|---|
| home | https://www.experimentalgroup.com/ | oui (+ sweep 15 paliers) | oui |
| rooms (= page hôtel) | https://www.experimentalgroup.com/val-disere/experimental-chalet-val-disere | oui | non (absent) |
| room-detail (= restaurant de l'hôtel) | https://www.experimentalgroup.com/val-disere/experimental-chalet-val-disere/aigle-dor | oui | oui |
| experiences (= explore) | https://www.experimentalgroup.com/explore | oui | non |
| dining | https://www.experimentalgroup.com/explore-restaurants-bars | oui | non |
| spa | https://www.experimentalgroup.com/explore-wellness | oui | non |
| about (= manifesto) | https://www.experimentalgroup.com/manifesto | oui | non |
| offers | https://www.experimentalgroup.com/exclusive-offers | oui | non |
| contact | https://www.experimentalgroup.com/contact | oui | non |
| booking (sonde v1, captures) | https://www.experimentalgroup.com/paris/experimental-marais?namastay=true | oui (widget Namastay ouvert) | non |
| booking (sonde v2, JSON) | https://www.experimentalgroup.com/cotswolds/cowley-manor-experimental | oui (tiroir « Make a booking ») | non |
| hotels | https://www.experimentalgroup.com/explore-hotels | oui | non |
| destination | https://www.experimentalgroup.com/cotswolds | oui | non |
| hotel (Cowley Manor) | https://www.experimentalgroup.com/cotswolds/cowley-manor-experimental | oui | non |
| restaurant (Cowley Manor) | https://www.experimentalgroup.com/cotswolds/cowley-manor-experimental/restaurant-cowley-manor | oui | non |
| design | https://www.experimentalgroup.com/design | oui | non |
| beach | https://www.experimentalgroup.com/explore-beach-clubs | oui | non |

**Limites de l'observation**
- **Vidéos** : contrairement aux autres sites de la série, les vidéos hero (`SUMMER_T2_compressed_webm.webm`, `Val_dIsere_optimized_webm.webm`) sont rapportées `paused: false` et les captures successives montrent des plans différents (toits de Paris, restaurant, Venise, Regina Biarritz) : la lecture a bien eu lieu en headless. Fluidité, boucle et son réels non vérifiés. Sous `prefers-reduced-motion` émulé, la vidéo est rapportée `paused: true` (hypothèse : arrêt scripté, aucune règle CSS `prefers-reduced-motion` trouvée).
- **Modale Vimeo « WATCH FULL VIDEO »** (1440×900, z-index 2147483647) non ouverte.
- **Cookies Axeptio** : bannière FR (« Les cookies sur notre site ») visible sur la quasi-totalité des captures scrollées desktop (≈ 420×420 px en bas à gauche) et **plein écran sur mobile** (bloque la moitié basse) ; la capture `home-mobile-05-menu-open` montre la bannière et non le menu : **menu mobile non observé**.
- **Réservation** : tiroir « Make a booking » ouvert (captures `home-06-booking-step1`, `booking-06-booking-step1`) et widget Namastay ouvert avec calendrier de prix (`booking-03-scroll1`, Hôtel Experimental Marais) ; aucune date saisie, aucune étape 2 ; SevenRooms, Pure Online, Resy, Tock non ouverts.
- **Hover** : mesuré uniquement sur BOOK NOW (changement de fond) ; cartes de lieux, onglets de sous-nav et liens de menu sans variation mesurée (transition `all`), donc hypothèse pour un éventuel zoom image.
- **Page hôtel mobile** absente du jeu de données ; mobile analysé sur home et page restaurant.
- **Lighthouse / LCP / CLS** non disponibles ; transitions de page non mesurées ; carte Mapbox interactive non manipulée ; tactile réel non testé.

---

## 1. Positionnement de marque

**Faits observés**
- Title home : « Experimental | Crafted Escapes in Storied Places, Boutique Hotels » ; description : « hotels, restaurants, bars and spas. Crafted escapes in the world's most storied places ». Tagline reprise en H1 (60 px Nantes, « most storied places » en italique), en footer et en JSON-LD.
- Paragraphe d'intro (36 px, 1 380 px de large, alinéa) : chronologie bar 2007 → restaurants et wine bars → hôtels « the ultimate measure of hospitality… under one roof ». Manifesto : fondateurs nommés (trois amis d'enfance, quatrième associé en 2010), sections « A bespoke design, a consistent ethos », « An Epicurean Spirit », « An Original Spirit, Unbound », citation « True expertise is felt, not announced ».
- **Architecture de marque visible dans le DOM et les captures** :
  - *Niveau 1* : marque ombrelle « EXPERIMENTAL* » (astérisque = signe distinctif, repris en 120 px après chaque titre de chapitre : « ROOMS & SUITES* », « ABOUT* »).
  - *Niveau 2* : 13 destinations (Paris, London, New York, Venice, Biarritz, Menorca, Ibiza, Verbier, Cannes, Cotswolds, Val d'Isère, Rome, Comporta) + Porto « Coming Soon » ; URL `/{destination}`.
  - *Niveau 3* : lieux, chacun avec **son propre logotype** (Hôtel Experimental Marais en capitales Art nouveau, Grands Boulevards manuscrit, Grand Pigalle avec figure, Henrietta en script, Il Palazzo ludique, Regina en monogramme, Le Garage en didone, Menorca en stencil, Montesol serif + script) et, sur sa page, **sa couleur de fond** (Val d'Isère `#d1cfc8` via classe `background-color-experimental-val-disire`, Cowley Manor via variable `--_cowley-manor---background-blue:#3b4b5f`). URL `/{destination}/{lieu}`.
  - *Niveau 4* : services du lieu (restaurant, bar, spa, événements, boutique) avec logos propres (L'Aigle d'Or et son aigle, L'Aiglon et son chalet) ; URL `/{destination}/{lieu}/{service}`.
  - *Axe transversal* : 8 types de lieux (légende Mapbox : Hotel, Restaurant, La Compagnie Wine Bar, Experimental Cocktail Club, Beach Club, Night Club, Wellness, Boutique) avec pages `/explore-*`.
- Sur la page hôtel, le logo central devient celui de l'hôtel ; la marque groupe se réduit à un sigle « E* » à gauche du burger ; deux footers empilés (hôtel : logo, About, Offers, Instagram du lieu ; groupe : tagline, liens, wordmark géant).
- Nomenclature : « Experimental Marais », « Grands Boulevards Experimental », « Experimental Chalet Val d'Isère », « Cowley Manor Experimental » — le mot Experimental encadre presque toujours le nom du lieu.
- JSON-LD `Organization` (adresse 14-16 bd Poissonnière, Paris 75009, téléphone), `Hotel` sur la page Val d'Isère (adresse, e-mail), `Restaurant` sur L'Aigle d'Or, `CollectionPage`, `AboutPage`, `ContactPage`.
- Offres avec prix affichés (« £95.00 per person », « Members only £70.00 ») et `ratePlanCode` dans les liens.

**Interprétation**
- Positionnement : **hospitalité créative née du bar**, où l'hôtel est présenté comme l'aboutissement d'une culture du cocktail et de la table, non l'inverse. La promesse centrale est l'« escape » (évasion courte) dans un lieu « storied » (chargé d'histoire), avec design signé et gastronomie.
- Cible : urbains 30-50 ans, voyageurs européens multi-villes (hreflang en/fr/it/pt/es), à la fois clients d'hôtel et clients locaux de restaurants/bars (les CTA « BOOK A TABLE » sont aussi nombreux que « BOOK NOW » chambres).
- Gamme perçue : haut de gamme lifestyle (4 étoiles annoncé pour Val d'Isère), pas palace : les prix des offres, la présence de « Loft Mezzanine Bunk Beds » et de « Kids » dans la sous-nav signalent un luxe accessible et familial.
- Territoire émotionnel : convivialité, nuit, table, humour visuel (logos dessinés, astérisque). Personnalité : hôte cultivé et joueur. Valeurs affichées : amitié, lieu, design non répété, expertise discrète.
- Différence avec un site hôtelier générique : la home ne vend pas une chambre mais **un réseau** (grille de logos, carte, carrousel de destinations). L'architecture ombrelle → destination → lieu → service est portée par les URL, les logos, les fonds de couleur et les doubles footers : cohérence forte entre offre, mots (« crafted », « storied », « escape ») et images (intérieurs signés, scènes de bar).
- Point de tension : le fil « Experimental » reste lisible grâce à la typographie commune (Nantes + Linux Biolinum) et aux composants identiques (pilule BOOK NOW, chapitres 120 px), alors que chaque lieu a son logo et sa couleur : c'est un système « même grammaire, vocabulaire local ».

**Enseignements réutilisables**
- Une marque ombrelle multi-lieux tient par des **invariants de composant** (police, pilule, titres de chapitre, footer groupe) et des **variables de lieu** (logo, couleur de fond, Instagram) ; ne jamais faire varier les deux à la fois.
- Nommer les lieux avec le mot de marque en préfixe ou suffixe crée une famille sans uniformiser.
- Un signe graphique minimal (astérisque) suffit comme signature transversale.

---

## 2. Première impression (5 premières secondes)

**Faits observés — desktop**
- Header 72 px, fond transparent, `mix-blend-mode: exclusion` (le texte s'inverse selon le fond), z-index 9 999 999 : burger à gauche (≈ 30 px), wordmark « EXPERIMENTAL* » centré (≈ 155 px de large), « EN ⌄ » et pilule « BOOK NOW » 120×37 (bordure 1 px blanche, rayon 15 984 px, Linux Biolinum 16 px capitales, interlettrage 0,48 px) à droite.
- Hero plein viewport 1440×900 (100 %), vidéo autoplay/muted/loop (webm 5,9 Mo + mp4 4,0 Mo tous deux sollicités en 206), voile `rgba(0,0,0,.3)`, H1 centré 60 px/72 px blanc, lien « WATCH FULL VIDEO » 16 px capitales centré à 852 px du haut. Aucune barre de recherche, aucune date.
- Plans vus : toits de Paris, rire au restaurant, lagune de Venise, façade « REGINA » — destinations et personnes, pas de chambre.
- Distractions : bannière Axeptio ≈ 420×420 px bas gauche (présente sur `01-hero`), pastille Axeptio flottante 46 px ; pas de pop-up newsletter.
- TTFB 436 ms, FCP 1 288 ms, DOMContentLoaded 1 849 ms, load 5 812 ms ; 552 requêtes, 73 Mo transférés (voir rubrique 13).

**Faits observés — mobile**
- Nav 58 px, hero vidéo 390×540 (64 % du viewport), H1 30 px/33 px sur deux lignes, « WATCH FULL VIDEO » 16 px ; sous la ligne de flottaison, le paragraphe d'intro justifié 20 px commence à 540 px.
- **Barre fixe basse** `navbar_book-button.is-mobile` 390×65 (y 779), fond `#f5f4f2` à 85 % + `backdrop-filter: blur(5px)`, bouton BOOK NOW 358×37 bordure noire.
- Bannière Axeptio plein écran (moitié basse) sur toutes les captures scrollées ; un bouton « Continuer sans accepter ».

**Interprétation**
- En 5 secondes : on voit un film de voyage, un mot de marque, une pilule de réservation ; on comprend « groupe de lieux », pas encore « hôtel ». L'absence de moteur dans le hero est un choix éditorial : l'utilisateur est invité à regarder, puis à choisir un lieu dans la grille.
- Le logo centré et l'inversion par `exclusion` maintiennent la lisibilité quel que soit le plan vidéo (blanc sur toits sombres, sombre sur ciel clair dans `home-04`).
- Raison de continuer : la promesse « storied places » + la vidéo ; le premier contenu sous la ligne est un texte de 36 px — dense, mais l'alinéa et la taille en font un manifeste, pas une description.
- Sur mobile, la barre basse blur est le mécanisme le plus utile de la page (CTA persistant sans masquer la vidéo), mais la bannière cookies FR sur un site EN crée une rupture de langue immédiate.

**Enseignements réutilisables**
- Un hero de groupe peut se passer de moteur si un CTA pilule et un tiroir de réservation sont à un clic.
- Barre de réservation mobile en bas, translucide + blur, 37 px de haut, laisse le hero respirer.
- Header en `mix-blend-mode: exclusion` : une seule couleur de texte pour tous les fonds.

---

## 3. Direction artistique

**Faits observés**
- Fonds mesurés : blanc `#ffffff` (3 151 occurrences), noir `#000000`, gris chaud `#bdbcb9` (grille de lieux, offres), gris clair `#dedede` (section carte), terracotta `#954935` (newsletter, toutes pages), gris-beige `#d1cfc8` (fond de page Val d'Isère), kaki `#8a816e` (blocs actualités des pages explore), brun `#622e1f` (bloc contact restaurant), bleu ardoise `#3b4b5f` (variable Cowley Manor). Voiles noirs à 0,2 / 0,3 / 0,4 / 0,5 / 0,7.
- Textes : `#000000` (405), `#ffffff` (380), `#222222` (chips de filtre).
- Polices chargées : **Nantes** (Book, Light, Book Italic — police commerciale, fonderie non vérifiée : hypothèse) pour titres et paragraphes éditoriaux ; **Linux Biolinum** (libre, famille Libertine) pour le corps 18 px, l'UI, les boutons et les titres de chapitre ; Source Sans 3 uniquement dans la bannière Axeptio.
- Échelle desktop : H1 hero 60/72 ; H2 carrousel 64/76 ; chapitre hôtel 120 px (7 occurrences) ; mots géants explore 140,65 px (« EXPLORE »), 118 px (« WELLNESS »), 89 px (« RESTAURANTS ») avec interligne 0,8 ; H2 section 48/57,6 ; H2/H3 36/43,2 ; noms de chambres 32 px capitales interlettrage 0,32 px ; intro 36 px Nantes ; paragraphe éditorial 24/28,8 ; corps 18/21,6 ; UI 14 px capitales 0,42 px ; méta 12 px ; italique Nantes pour le second segment des titres (« most storied places », « in touch », « city escape »).
- Échelle mobile : H1 30/33 ; H2 32 ; corps 14 px (42 occ.) et 12 px (55 occ.) ; **10 px** ×27 sur la home mobile (`fontSizeSmall: 10`) ; paragraphe carrousel 12/14,4.
- Grille : marges 30 px (contenu 1 380 px), 3 colonnes de 447 px avec gouttières 20 px ; deux colonnes 650 + 650 ; texte long en 680 px ; images de carte 447×559 (ratio 0,8) sur la home, 447×621 (0,72) sur explore, 650×904 (0,72) en colonne épinglée, 1 380×836 (1,65) en carrousel, 1 283×904 (1,42) pour les chambres, 1 440×495 (2,91) pour le carrousel de destinations.
- Composants : boutons pilule (rayon 15 984 px), bordure 1 px, transparents ; chips de filtre 311×38 blanches à 70 % ; boutons de zoom carte rayon 12 px ; cartes et images **sans rayon** ; pas d'ombres portées ; légende de carte en carte blanche arrondie.
- Iconographie : quasi absente (flèches fines ← →, pin, enveloppe, téléphone dans les cartes explore) ; le logo du lieu sert d'illustration.
- Photos : intérieurs très composés, lumière naturelle rasante (manifesto : ombres sur chaise paillée), chambres avec papiers peints géométriques, food en gros plan sur marbre rouge ; présence humaine fréquente (rire au bar, femme au téléphone, skieuse à la fenêtre).
- Vide : sections d'intro 293 px (home), 232–419 px (about) ; footer avec wordmark 1 380 px de large sur ≈ 130 px de haut.

| Token | Valeur approx. |
|---|---|
| Fond principal / secondaire | `#ffffff` / `#bdbcb9` |
| Fond section utilitaire | `#dedede` |
| Accent chaud (newsletter) | `#954935` |
| Fond de lieu (variable) | `#d1cfc8` (Val d'Isère), `#3b4b5f` (Cowley Manor) |
| Kaki éditorial (explore) | `#8a816e` |
| Texte | `#000000` / `#ffffff` |
| Voile vidéo / image | `rgba(0,0,0,.3)` / `.4` |
| Display | Nantes 400, 60–140 px, interligne 1,2 → 0,8 |
| Corps | Linux Biolinum 18/21,6 ; éditorial Nantes 24/28,8 |
| UI | Linux Biolinum 14–16 px capitales, interlettrage 0,42–0,48 px |
| Bouton | pilule 120–153×37, bordure 1 px, transition 0,2 s |
| Chips | pilule 311×38, blanc 70 % |
| Rayons images | 0 |
| Header | 72 px desktop / 58 px mobile ; sous-nav hôtel +59 px (131 px total) |
| Marges | 30 px ; gouttière 20 px ; contenu 1 380 px ; texte 680 px |

**Interprétation**
- Display serif (Nantes) + police libre humaniste (Linux Biolinum) = voix éditoriale ; pilule fine et images sans rayon évitent l'effet template.
- La palette est **neutre au niveau groupe** (blanc, noir, deux gris, un terracotta) et **colorée au niveau lieu** : c'est ce qui permet aux logos multiples de cohabiter sans cacophonie.
- La cohérence graphique entre types de lieux tient au fait que restaurants, spas et boutiques utilisent les mêmes gabarits (carte 447 px + logo + BOOK NOW ; chapitre 120 px + image pleine largeur), seul le contenu change.
- Faiblesse : les tailles 10 et 12 px sur mobile, et le kaki `#8a816e` sous du blanc 18 px (≈ 3,9:1) sont en dessous des attentes de lisibilité.

**Enseignements réutilisables**
- Deux polices, une palette groupe à 5 valeurs, une couleur par lieu : suffisant pour 70 lieux.
- Titres de chapitre à 120 px avec signature (astérisque) sur image pleine largeur = repère de navigation autant que geste graphique.
- Ratios d'image stables par usage (0,8 carte, 0,72 colonne, 1,42 chambre) simplifient la production photo.

---

## 4. Architecture de la page d'accueil

| Position (desktop, y) | Section | Objectif | Contenu | Interaction | CTA | Émotion créée |
|---|---|---|---|---|---|---|
| 0–900 | Hero vidéo | Immersion, promesse | Vidéo plein écran (plans de villes et de bars), H1 60 px, lien vidéo | Lecture auto ; modale Vimeo | WATCH FULL VIDEO ; BOOK NOW (header) | Curiosité, voyage |
| 899–1 192 (293) | Intro texte | Expliquer l'origine | Un paragraphe 36 px sur 1 380 px, alinéa | — | — | Légitimité (2007, bar → hôtel) |
| 1 191–3 287 (2 096), fond `#bdbcb9` | Grille de lieux | Faire choisir | Onglets destinations (13 + « Coming Soon »), onglets types (8), 9 cartes 447×559 avec logo, « Hotel / France, Paris », LOAD MORE | Filtres Finsweet (radios cachés), pagination | 9 × BOOK NOW 132×37 → `/{dest}/{lieu}?namastay=true` | Abondance, identité de chaque lieu |
| 3 286–3 781 (495), fond noir | Carrousel destinations | Vendre la ville | 14 slides 1 440×495 (2,91), H2 64 px + italique, paragraphe 20 px centré 600 px, flèches | Splide, flèches ← → | DISCOVER PARIS… (texte) | Désir de destination |
| 3 780–4 988 (1 208), fond `#dedede` | Carte + liste | Outil de recherche | H2 36 px, chips Locations / Experience, « Showing results (70) », 6 vignettes 213 px + tags « City escapes | Wellness retreats », carte Mapbox 635×812 épinglée à droite, légende 8 types, clusters numérotés (13, 14, 11, 7, 5, 5, 4, 3) | Carte zoom/pan ; sticky | BOOK NOW 75×15 (texte), VIEW ALL | Maîtrise, vue d'ensemble |
| 4 987–5 863 (876), blanc | Manifesto | Marque | Image pleine largeur (30 px de marge) chaise paillée en lumière rasante, « MANIFESTO » 64 px capitales, 4 lignes 18 px | — | MANIFESTO (lien) | Chaleur, artisanat |
| 5 862–6 429 (567), `#954935` | Newsletter | Capter | Image de fond (fauteuil), « Stay *in touch* », 3 champs pilule, case RGPD, Subscribe | Formulaire Webflow | Subscribe → | Appartenance |
| 6 429–6 786 | Footer | Orienter | Tagline, 9 liens sur 3 colonnes, Instagram/LinkedIn, wordmark géant | — | Contact | Signature |

**Logique narrative**
- Début : film + tagline (émotion). Construction du désir : récit d'origine puis **grille de logos** — le désir passe par l'identité des lieux, pas par des chambres. Moment où l'offre devient concrète : dès la grille (BOOK NOW sur chaque carte à 1 840 px, soit 2 viewports). Présentation des chambres : **absente de la home** (aucune photo de chambre hors vignettes). Preuve : aucune note, aucun avis, aucune presse ; la preuve est le nombre (70 résultats, 14 destinations, carte). Réservation : header + cartes + liste. Fin : manifeste et newsletter, pas de rappel de réservation en bas.
- Mobile : même ordre, hauteur totale 9 353 px (11 viewports) ; la grille passe à 4 484 px (9 cartes empilées de 358×448), la carte à 2 101 px.

**Enseignements réutilisables**
- Pour un groupe, mettre la grille de lieux en deuxième position (avant tout carrousel) : c'est le vrai sommaire.
- Une carte épinglée à droite d'une liste = pattern « recherche » sans moteur de dates.
- Le carrousel « une ville = une phrase + une image » est une couche de désir distincte de la couche produit.

---

## 5. Scroll et storytelling

**Faits observés**
- Sweep home (15 paliers de 395 px) : `transforms` 4 sur le hero, 1 dans la grille, **15 entre 2 763 et 3 552 px** (carrousel Splide + carte), 1 ensuite ; `partialOpacity` 0 partout ; `pinned` vide dans le sweep GSAP ; `triggers: 0` (ScrollTrigger chargé, version GSAP 3.15.1, mais aucun trigger enregistré sur la home). `ScrollSmoother`, `SplitText`, `Lenis`, `Locomotive`, `Lottie` : absents.
- Éléments épinglés observés : `div.home-map_right` (sticky, 635×812, fond blanc) sur la home ; `home-map_right.is-fullscreen` 1 380×812 sur explore/hotel ; `two-columns_image-wrapper` 650×904 (sticky, 5 occurrences sur la page hôtel, 4 sur le manifesto et le restaurant) ; `section_destination-header` sticky 1 440×890 sur les pages explore, avec `destination-header_heading` **fixed** en `mix-blend-mode: exclusion` (mot géant « EXPLORE » 140 px qui s'inverse sur la vidéo portrait 446×610 puis sur le texte qui passe dessous, visible sur `experiences-01-hero`).
- Changements de fond au scroll (home) : transparent (vidéo) → blanc → `#bdbcb9` → noir → `#dedede` → blanc → terracotta → blanc. Page hôtel : `#d1cfc8` → voile noir 0,4 (chapitres) → `#d1cfc8`, alternance à chaque chapitre.
- Scroll horizontal : `horizontal: 3` sur la page hôtel (carrousel de chambres 1 283×904 avec compteur « 1 / 4 » et flèches), carrousels Splide dans chaque carte explore (« 1 / 4 », « 1 / 3 »).
- Pas de parallaxe (`parallax: 0`), pas de marquee, pas de split-text, pas de scroll-snap, `scrollTimeline: 0`.
- Hauteurs : home 6 786 px (7,5 viewports) ; page hôtel **23 267 px (25,9 viewports)** ; explore 12 735 ; restaurant 14 310 ; manifesto 10 229 ; offers 6 631 ; contact 4 451.

**Interprétation et fonction de chaque effet**
- *Colonne image épinglée (650×904) + texte qui défile* — fonction : **expliquer** sans perdre l'image ; sur le manifesto, le texte 24 px en colonne de 650 px défile sur ≈ 1 000–1 450 px pendant que la photo reste.
- *Carte épinglée* — fonction : **orienter** ; la liste devient un index de la carte.
- *Mot géant fixe en exclusion* (explore) — fonction : **marque + rythme** ; le titre de rubrique reste 890 px puis se fait recouvrir : c'est la seule « révélation » scriptée du site, visuellement forte mais elle rend le H1 36 px secondaire.
- *Chapitres 120 px sur image pleine largeur avec voile 0,4* (page hôtel) — fonction : **rythme et navigation** ; chaque 2 000–3 000 px, un nouveau chapitre, relayé par la sous-nav fixe. C'est un long-scroll « one page » de 26 viewports : la respiration est assurée par les fonds `#d1cfc8` et les colonnes de texte, mais la densité est élevée (1 509 mots).
- *Carrousel de destinations* — fonction : **émotion** ; le seul bloc noir de la home.
- Absence de parallaxe et de fondu à l'entrée : le mouvement vient des vidéos, des carrousels et du sticky, pas des reveals. Envie de poursuivre : bonne sur la home (chaque section change de fond et de fonction), moyenne sur la page hôtel (les 13 chapitres se ressemblent).

**Enseignements réutilisables**
- Sticky + changement de fond suffisent à rythmer un long scroll ; les reveals ne sont pas nécessaires.
- Un titre de rubrique géant fixé en `exclusion` crée une signature de scroll à coût nul (CSS seul).
- Limiter un one-page hôtel à ≈ 12–15 viewports, ou couper en sous-pages : 26 viewports est au-delà de l'attention.

---

## 6. Animations et micro-interactions

| Animation | Déclencheur | Élément | Effet | Fonction | Risque UX |
|---|---|---|---|---|---|
| Vidéo hero | Chargement | `<video>` webm/mp4, 1440×900 | Lecture auto en boucle, voile 0,3 | Émotion | 9,9 Mo de médias ; pas de poster (`poster: ''`) |
| Modale vidéo | Clic « WATCH FULL VIDEO » | `vimeo-modal_component` 1440×900, fond noir, z max | Plein écran, « CLOSE » | Marque | Non testée ; lecteur Plyr 3.7.8 chargé |
| Préloader vidéo | Chargement | `.vimeo-background-video-loader-js.hide` | Masqué (non visible) | Technique | — |
| Hover BOOK NOW | Survol | Pilule header/cartes | Fond transparent → blanc (texte noir) sur home, → noir sur pages intérieures ; 0,2 s | Feedback | Sur photo claire, contraste variable |
| Hover cartes de lieu | Survol | `home-location_card`, `hotel-rooms_overlay` | Aucun changement mesuré (transition `all`) ; zoom image = hypothèse | — | Manque de feedback |
| Hover onglets sous-nav | Survol | `subnav-tab_link` | Aucun changement mesuré ; 0,2 s | — | — |
| Menu | Clic burger | `navbar_menu` 1440×552, blanc 60 % + blur (visible) | Panneau 4 entrées + colonne de 14 destinations, « Coming Soon » en italique | Navigation | Le hero reste visible en dessous : bon repère ; « Coming Soon » cliquable ? non vérifié |
| Tiroir réservation | Clic BOOK NOW | Panneau droit ≈ 613 px blanc | 4 lignes (Rooms, Restaurants & Bars, Wellness, Private Events) avec flèche | Action | Étape supplémentaire avant les dates |
| Carrousel destinations | Flèches | Splide 4.1.4 | Slide 1 440×495 | Émotion | Auto-play non vérifié |
| Carrousels de cartes | Flèches | Splide dans chaque carte explore et chambre | Compteur « 1 / 4 » | Expliquer | 226 images sur explore |
| Filtres | Clic onglet | Finsweet Attributes (radios cachés) | Filtre la grille, « Showing results (n) » | Orienter | Radios sans label (`hasLabel: false`) |
| Sticky | Scroll | Carte, colonnes image, header explore | Épinglage natif CSS | Orienter / expliquer | Sur mobile, 146 sticky = risque de saccade (non mesuré) |
| Mot géant exclusion | Scroll | `destination-header_heading` fixed | Inversion de couleur au passage du contenu | Marque | Lisibilité du H1 36 px au-dessus |
| Interactions Webflow | Divers | 17 `data-w-id` (home), 18 (hôtel) | Non identifiées individuellement (hypothèse : ouverture menu, tiroir, onglets) | — | — |
| Reduced motion | `prefers-reduced-motion` | Aucune règle CSS (`reducedMotionRules: 0`) ; vidéo rapportée en pause | Partiel | Accessibilité | Carrousels et transitions inchangés |

**Faits complémentaires** : durées CSS `.2s` ×48, `.3s` ×18, `1s` ×3, `2s` ×2 ; un seul easing nommé `cubic-bezier(.4,0,.2,1)` ×2 (hypothèse : composant tiers) ; 8 `@keyframes` non attribuables ; `backdrop-filter` ×40 ; curseur natif.

**Interprétation**
- Le site est **peu animé** malgré GSAP : l'énergie vient du contenu (vidéos, logos, carrousels). Les transitions sont courtes (0,2 s) et sans easing signature. C'est cohérent avec un groupe qui gère 70 lieux : la maintenance prime.
- Manques : aucun feedback au survol des cartes (sur un site où la carte est l'unité de navigation), aucune gestion `prefers-reduced-motion` en CSS.

**Enseignements réutilisables**
- 0,2 s + inversion de couleur pour une pilule : suffisant si constant partout.
- Les tiroirs latéraux (menu, réservation) qui laissent le contenu flouté derrière gardent le contexte.
- Prévoir au minimum un `@media (prefers-reduced-motion)` qui arrête vidéos et carrousels.

---

## 7. Navigation et architecture de l'information

**Faits observés**
- Header groupe (toutes pages) : burger, wordmark centré, langue (EN, FR, IT, PT, ES — 5 langues + `x-default`), BOOK NOW. `position: static` sur le `<nav>` mais `navbar_background` fixed 72 px ; `header` landmark absent, 14 `<nav>` landmarks sur la home.
- Menu : 4 entrées (LOCATIONS, EXPLORE, GALLERY, ABOUT). LOCATIONS → 14 destinations ; EXPLORE → View all + 8 types (`/explore-hotels`, `/explore-restaurants-bars`, `/explore-la-compagnie-wine-bar`, `/explore-experimental-cocktail-club`, `/explore-beach-clubs`, `/explore-night-clubs`, `/explore-wellness`, `/explore-boutiques`) ; ABOUT → Manifesto, Design, Work with us (`/careers`), Offers (`/exclusive-offers`), What's on, Private Events, Press, Contact us, Sustainability. Blog et Map en footer.
- Page hôtel : fil d'Ariane « ‹ Back / Val d'Isère / Experimental Chalet Val d'Isère » (16 px, 92 px du haut) ; **sous-nav fixe** `subnav-tab_component` 1 440×131 (blanc 80 %, blur 35 px) avec 13 onglets 14 px capitales : ROOMS & SUITES, ABOUT, RESTAURANTS & BAR (dropdown 3 lieux), GALLERY, WELLNESS, OFFERS, WHAT'S ON, PRIVATE EVENTS, KIDS, BOUTIQUE & GIFTS, SKI, ACCESS & CONTACT ; ancres internes (`#`) sauf ACCESS & CONTACT (`/…/access-contact`).
- Page restaurant : sous-nav réduite « ‹ HOTEL | MENUS | PRIVATE EVENTS | DESIGN | OUR COCKTAIL BAR | CONTACT & ACCESS » ; fil d'Ariane à 4 niveaux.
- Mobile (page restaurant) : header 58 px avec texte « Discover Experimental destinations HOTEL EN FR IT PT ES MENUS… BOOK NOW » dans le panneau (menu contextuel du lieu intégré au menu principal) ; barre BOOK NOW fixe en bas 65 px.
- Infos essentielles : adresse, e-mail, téléphone **dans chaque carte explore** (ex. « 29 Rue Victor Massé, Paris, France 75009 ») ; sur la page hôtel, bloc ACCESS & CONTACT avec « Contact Us » mailto à 19 753 px (22 viewports) ; JSON-LD complet.
- Étapes pour atteindre une chambre depuis la home : hero → grille (scroll 1 viewport) → BOOK NOW carte (ouvre le lieu avec `?namastay=true`, hypothèse : tiroir Namastay pré-ouvert) = **2 clics** ; ou header BOOK NOW → Rooms → (choix d'hôtel dans l'iframe Namastay, non vérifié).
- Étapes pour atteindre une table : carte explore → BOOK NOW `#booktable-{slug}` (SevenRooms, iframe titrée) = 2 clics ; New York via Resy/Tock (liens externes).
- Frustrations : « What's on » de Val d'Isère en placeholder ; « Envoyer » en français sur le formulaire EN ; « Coming Soon » dans le menu ; onglets destinations qui débordent (« COMPOR… ›») ; aucun lien « chambres » direct dans le menu groupe.

**Interprétation**
- L'IA est une **matrice** destinations × types, doublée par la carte : trois chemins convergent vers la même fiche lieu. C'est robuste pour 70 lieux.
- La sous-nav fixe de 131 px sur la page hôtel remplace des sous-pages ; elle coûte 15 % du viewport en permanence.
- Le bouton de réservation est persistant partout (header desktop, barre basse mobile) ; c'est un tiroir de **routage** (chambre / table / spa / événement), pas un moteur : le premier écran de réservation est une question de type de service, adaptée à un groupe qui vend quatre choses.

**Enseignements réutilisables**
- Matrice destination × type + carte = IA type pour toute collection multi-lieux.
- Fil d'Ariane à 3–4 niveaux visible dès le hero sur les pages de lieu.
- Le tiroir « que voulez-vous réserver ? » est un bon premier pas quand chambres, tables et soins ont des moteurs différents.

---

## 8. Parcours de réservation et conversion

**Faits observés**
- Premier CTA : « BOOK NOW » header desktop (y 18, 120×37) ; mobile : barre basse fixe (y 779, 358×37). Home : 9 BOOK NOW sur cartes (132×37, dès y 1 840) + 6 BOOK NOW texte (75×15) dans la liste carte.
- Tiroir « Make a booking » (capture `home-06-booking-step1`) : titre 36 px Nantes, quatre choix « Rooms », « Restaurants & Bars », « Wellness », « Private Events » (24 px, flèches), croix ; le reste de la page flouté derrière.
- Moteurs identifiés (preuves : iframes, hrefs, hosts réseau) :
  - **Chambres** : Namastay (`app.namastay.io/en/chain/b2edf737…` en iframe, 68 requêtes `app.namastay.io` + 11 `api.namastay.io` sur la home, `sdk.namastay.io/index.js` 725 Ko) ; liens `/{dest}/{lieu}?namastay=true` et, pour les offres, `/offers?namastay=true&ratePlanCode=SEASO…`. Hypothèse : moteur transactionnel intégré en overlay sur le domaine du site (pas de nouvel onglet : `newTab: false`).
  - **Tables** : SevenRooms (iframe « SevenRooms », liens `#booktable-{slug}?hideAddress=true&hideTabs=true`) ; Resy et Tock pour New York (liens externes, `resy.com`, `exploretock.com`) ; Farm Club et STEREO (Londres) vers sites tiers.
  - **Spa** : Pure Online (`#bookpure-https://book-widget.pure-informatique.com/?locationID=45532`).
  - **Événements privés** : formulaire (sujet, destination, prénom, nom, e-mail, téléphone, date, nombre de personnes, budget, heures début/fin, occasion, société) ; sur la page restaurant `#bookevent-{email}`.
  - **Boutique** : lien externe (Montesol → `bonkdo.com`).
- Dates / voyageurs : aucun champ de date sur les pages (`dateInputs: []`) ; tout est dans l'iframe Namastay.
- Prix : non affichés sur les pages hôtel ; affichés sur `/exclusive-offers` pour certains packages (£95, £70 « Members only »), et « 4 Star hotel » dans le texte Val d'Isère.
- Réassurance : aucune note, aucun avis, aucun logo presse, aucun bénéfice « réservation directe » explicite ; mentions « Gift Vouchers », « Give the gift of Val d'Isère », Instagram du lieu, e-mails de réservation par lieu (`reservation@experimentalchaletvaldisere.com`) et téléphone dans les cartes explore.
- Offres : 11 cartes sur `/exclusive-offers` (filtre par destination), label hôtel en capitales 14 px, titre 32 px, extrait 18 px, « BOOK NOW » ou « LEARN MORE ».
- Contact humain : page `/contact` avec formulaire labellisé (Type of request, Location), adresse siège, e-mails Jobs / Press / Reservations, Sales & Events ; bouton « Envoyer → » (français).
- Points de rupture : changement de moteur selon le service (Namastay / SevenRooms / Pure / Resy / Tock / bonkdo), certains en nouvel onglet externe (New York, Londres) ; les offres Marais renvoient à un domaine différent (`experimentalmarais.com//?namastay=true`, double slash).

**Interprétation**
- Le site distingue clairement **découvrir** (DISCOVER, VIEW ALL, LEARN MORE en texte 14–16 px) et **réserver** (pilule BOOK NOW / BOOK A TABLE) ; il ne propose pas de niveau « demander » pour l'hôtel, sauf événements et contact.
- L'overlay Namastay évite la rupture de domaine, mais le parcours compte au moins trois écrans avant les dates (tiroir → type → moteur), et aucune preuve sociale ne soutient la décision.
- L'exposition de prix dans les offres seulement crée une asymétrie : le visiteur d'une page hôtel ne sait pas à quel niveau tarifaire il se situe.

**Enseignements réutilisables**
- Router par type de service en overlay, sans quitter le domaine, est la bonne réponse pour un groupe multi-service.
- Ajouter le nom du lieu et un « à partir de » dans le tiroir réduirait l'écart entre découverte et transaction.
- Un e-mail et un téléphone par lieu dans les cartes de liste sont une réassurance simple et rarement faite.

**Faits observés — widget Namastay (Hôtel Experimental Marais, `?namastay=true`, capture `booking-03-scroll1`)**
- Panneau blanc ≈ 568×796 px ancré à droite (y 32), page floutée/assombrie derrière ; en-tête : burger, « EUR », « EN », logo de l'hôtel centré, partage, croix ; « Add Promo Code ».
- **Calendrier avec prix par nuit** avant toute sélection : September 2026, « €1,190 » (ven. 4), « €970 », « €610 », puis €648–€860 en semaine ; jours passés grisés ; « Browse all Experimental hotels › » ; compteur « Rooms 1 − + » ; bas de panneau « Select dates and guests to proceed » + bouton « Next » désactivé ; « Secured by namastay », Privacy, Terms.
- Sur Cowley Manor (`booking.json`), le CTA de la section chambres pointe vers `https://namastay-widget-button` (href non résolu, hypothèse : intercepté par le SDK) ; iframe `app.namastay.io/en/bdaa00fc…` ; bon de cadeau vers `cowleymanor.wearegifted.co.uk` (nouvel onglet externe).
- Aucun prix « à partir de » sur la page hôtel elle-même ; les prix n'apparaissent qu'une fois le widget ouvert.

**Interprétation (complément)**
- Le parcours réel est : BOOK NOW → type de service → widget avec **grille tarifaire immédiate** ; c'est une transparence supérieure à la moyenne des hôtels lifestyle, mais cachée derrière deux clics. Le lien « Browse all Experimental hotels » dans le widget montre que le moteur est pensé « chaîne » (comparaison d'hôtels sans quitter le panneau).
- Le style du widget (sans-serif, gris, bouton bleu-gris) rompt avec Nantes/Linux Biolinum : seule la présence du logo de l'hôtel maintient la continuité.

*(Complément pages hotels / destination / Cowley Manor / beach : §8 bis ci-dessous.)*

---

## 9. Pages chambres / propriétés

**Objet vendu** : une **nuit d'hôtel** (chambre ou suite) dans un lieu qui vend aussi des tables, des soins et des événements ; la page hôtel est un one-page de 13 chapitres, la chambre n'a pas de page propre (carrousel).

**Faits observés — Experimental Chalet Val d'Isère (desktop)**
- Hero 1440×900 : vidéo (skieuse à la fenêtre), logo ovale du chalet centré, fil d'Ariane, « WATCH FULL VIDEO ».
- H1 60 px sur fond `#d1cfc8` : nom + promesse (« A Winter Haven in the French Alps »), 304 px de section.
- Carrousel 1 380×836 « 1 / 4 » avec texte 36 px (« winter escape of epic proportions », « 4 Star hotel »), puis deux colonnes : image épinglée 650×904 + texte 24 px (altitude 1 850 m, saison de novembre à mai).
- Chapitre **ROOMS & SUITES*** (image pleine largeur, titre 120 px, « VIEW ALL ») : carrousel horizontal 1 283×904 de **13 catégories** (Val d'Isère, Balcony, Mountain View, Under the Eaves, Olympic Deluxe, Junior Suite Solaise, Loft Mezzanine Bunk Beds, Loft Mezzanine, Loft Mezzanine with Balcony, Glacier Suite with Balcony, Iseran Suite, Solaise Suite, Bellevarde Suite) ; chaque slide : nom 32 px capitales, description 18 px (« King size beds, rustic touches, and a rainfall shower »), BOOK NOW 129×26 ; **pas de surface, pas de capacité, pas de prix, pas de liste d'équipements**.
- Chapitre **GALLERY** (48 px) : mosaïque.
- Chapitre **RESTAURANTS & BAR*** : 3 cartes 796×… avec logos (L'Aigle d'Or, L'Aiglon, ECC Val d'Isère), description 18 px, DISCOVER + BOOK A TABLE, BOOK NOW 132×37 sur l'image.
- **WELLNESS*** : deux colonnes sticky + BOOK NOW (Pure). **WHAT'S ON*** : placeholder. **PRIVATE EVENTS*** : formulaire. **ABOUT*** : « A hotel comes to *life* », « Adventures Await ». **Give the gift** (48 px). **ACCESS & CONTACT*** : « Contact Us » (mailto, 135×44), adresse. Carte sticky 1 380×812 « 6 results » (les lieux du chalet). LOCATIONS (autres destinations), newsletter, double footer.
- Hauteur 23 267 px ; 98 images ; 1 509 mots ; load 10,3 s (voir §13).

**Faits observés — L'Aigle d'Or (restaurant de l'hôtel), desktop et mobile**
- Desktop : hero image (pas de vidéo), H1 64 px « a place to gather », H2 60 px, carrousel 1/4 avec texte 36 px (feu de cheminée, plateaux de fruits de mer), deux colonnes sticky (« A table for every moment »), chapitres MENUS (80 px, vide), PRIVATE EVENTS, DESIGN (« The spirit of the forest », portrait de la designer), OUR COCKTAIL BAR (ECC Val d'Isère), bloc « Gift Vouchers », contact brun `#622e1f` (« Contact Us » mailto), LOCATIONS, newsletter. CTA « BOOK A TABLE » 153×37 (y 763) → SevenRooms. 820 mots.
- Mobile : H1 32 px, H2 30 px, intro justifiée 20 px, corps 14/15,4 ; BOOK A TABLE 153×37 à y 707 ; barre BOOK NOW basse ; docHeight 11 712 ; 85 requêtes, 5,9 Mo ; TTFB 712, FCP 2 472, load 7 290 ms ; 491 mots (contenu réduit par rapport au desktop : 820).

**Interprétation**
- La page hôtel vend **l'écosystème** (restaurants, spa, ski, kids, boutique) plus que la chambre : les 13 catégories sont présentées comme des ambiances, sans faits comparables. Projection : forte par les images (lumière, textiles), faible par les données (m², vue, lits).
- Les éléments de réassurance sont l'ancrage local (altitude, saison, adresse), la marque du groupe et les logos ; pas d'avis.
- Hébergements complémentaires suggérés : uniquement via LOCATIONS (autres destinations), pas de « chambres similaires ».
- La page restaurant réutilise à l'identique le gabarit hôtel (hero, carrousel, sticky, chapitres, contact) : cohérence maximale, mais un chapitre MENUS vide et un WHAT'S ON en attente montrent la limite du gabarit unique.

**Enseignements réutilisables**
- Réserver un gabarit unique aux lieux, mais masquer les chapitres vides.
- Ajouter, par catégorie de chambre, trois faits (surface, occupation, vue) sous la description sensorielle.
- Le fil d'Ariane + logo du lieu au centre + sigle groupe à gauche est un bon pattern pour un lieu fille.

*(Complément Cowley Manor et pages hotels / destination / beach : §9 bis.)*

---

## 10. Copywriting

**Faits observés (mécanismes, pas de recopie)**
- Ton : narratif, à la troisième personne, sans « you » dans les titres ; phrases nominales enchaînées par virgules (« A haven of…, an escape with… where days are filled with… »). Wordcount : 888 (home), 1 509 (hôtel), 1 317 (explore), 796 (manifesto), 473 (contact).
- Titres : structure **« [verbe impératif] + [ville] + [complément sensoriel] »** pour le carrousel (Pay Paris a visit / Fall in love with London / Embrace… Venice / Bask… Menorcan sun / Soak up… New York nights) ; les 14 slides suivent ce moule, avec le second segment en italique.
- Titres de lieu : « [Nom], a [type] in the heart of [ville] » ; « [Nom], a place to gather ».
- Champ lexical : escape, storied, crafted, haven, hideaway, sanctuary, oasis, retreat, epicurean, gather, linger, tucked away, beneath (l'idée de « caché / en dessous » revient sur les spas : « beneath city streets », « subterranean sanctuary »).
- Sensoriel : verbes de perception et sons (« the pop of a champagne cork », « gentle hum », « candle light flickers ») ; météo et lumière (« misty mornings », « winter's chill », « starry skies »).
- Luxe : jamais le mot « luxury » dans les titres (présent dans les meta descriptions pour le SEO : « luxury ski hotel ») ; on parle de « 4 Star », « gastronomic », « Biologique Recherche ».
- Caractéristiques techniques : reléguées aux meta et à une phrase (« Located at 1,850m… season from November to May ») ; les chambres sont décrites par matières et gestes (« rustic touches », « rainfall shower »).
- CTA : capitales, verbes courts (BOOK NOW, BOOK A TABLE, DISCOVER, VIEW ALL, LEARN MORE, LOAD MORE, WATCH FULL VIDEO, Subscribe →) ; « DISCOVER [VILLE] » personnalise le carrousel.
- Manifesto : phrases courtes en quatre lignes, chacune commençant par un nom (« Born from… », « A belief… », « A place… », « A life… »).
- Scories : « Envoyer » sur le formulaire EN ; placeholder « x / y » sur le compteur mobile ; bannière cookies en français.

**Interprétation**
- L'écriture transforme une prestation en scène (heure, lumière, son, objet) : la chambre devient un moment, le spa un lieu caché. Le moule « impératif + ville » rend 14 destinations comparables sans répétition.
- L'italique sur le second segment du titre fait office de « respiration typographique » et d'accent oral.

**Enseignements réutilisables**
- Un moule de titre par type de contenu (destination, lieu, chapitre) permet d'écrire 70 fiches sans perdre la voix.
- Décrire une chambre par un geste + une matière + un son avant tout fait.
- Bannir « luxe » des titres, le garder pour les meta.

---

## 11. Photographie et vidéo

**Faits observés**
- Vidéos : hero home (plans courts de villes, bars, personnes ; webm 5,9 Mo + mp4 4,0 Mo), hero hôtel (skieuse à la fenêtre), vidéos portrait 446×610 en tête des pages explore (`gallery_summer_4x5`, `restaurant`, `spa (480p)`), modale Vimeo. 6 requêtes média sur la home, 29,4 Mo (range requests répétées).
- Photos : 190 images sur la home (179 webp, 146 avec `srcset`), 226 sur explore, 98 sur l'hôtel ; alts descriptifs générés (« Cozy reading nook with leather chairs… », « Waves gently crashing… ») ; `missingAlt: 0`.
- Types de plans : intérieurs frontaux (lit + tête de lit + papier peint), détails (chaise paillée, verre de cocktail versé), scènes de vie (rire au restaurant, femme au téléphone sur canapé rayé, skieuse se réchauffant les mains, femme au balcon de Biarritz avec phare), architecture (façade Regina, chalet de pierre sous la neige, lagune), food (plat sur marbre rouge, huîtres).
- Lumière : naturelle rasante, ombres longues (manifesto), chaleur artificielle en intérieur (bar, restaurant), grain et étalonnage légèrement désaturé sur les vidéos (toits de Paris verdâtres).
- Couleurs : bleus profonds (Grands Boulevards), verts (Henrietta), rouges/bordeaux (L'Aigle d'Or), terracotta (newsletter), sables (Ibiza) — la photo porte la couleur, l'UI reste neutre.
- Présence humaine : élevée sur les vidéos et les pages éditoriales (manifesto, contact), faible sur les cartes de lieux (intérieurs vides) ; personnes toujours de trois-quarts ou en action, jamais en pose frontale.
- Proportion lieu / expérience : cartes ≈ 90 % lieu ; hero et chapitres ≈ 60 % expérience.
- Cohérence forte (étalonnage, hauteur de regard) ; les logos blancs superposés unifient les cartes.

**Interprétation**
- La photographie fait le travail de branding local (couleur, style) tandis que la vidéo fait le branding groupe (mouvement, ville, gens). Les vidéos portrait des pages explore sont une déclinaison « social » (4:5) réemployée.
- Le poids média est le prix de ce choix : 29 Mo de vidéo sur la home desktop, 9,9 Mo sur mobile.

**Shot list pour reproduire ce niveau**
1. Film groupe 60–90 s, plans de 2–4 s : arrivée en ville depuis une fenêtre, bar en service, table à deux, rue, eau, façade avec enseigne, nuit ; version 16:9 (hero) et 4:5 (explore / social).
2. Par lieu : 1 façade avec enseigne, 1 plan frontal de chaque catégorie de chambre (lit centré, lumière du jour), 3 détails de matière (tête de lit, textile, robinetterie), 1 salle de bains.
3. Par restaurant/bar : salle vide en lumière naturelle, salle en service (mains, verres), 2 plats en plongée sur nappe ou marbre, 1 geste de barman.
4. Spa : bassin avec une personne de dos, cabine, détail eau/pierre.
5. Scènes de vie destination : une personne en action (téléphone, lecture, ski, balcon) avec le paysage local en fond.
6. Manifesto : 3 natures mortes de mobilier en lumière rasante, 1 portrait de groupe des fondateurs, 1 portrait de designer.
7. Contact / newsletter : 1 image « pause » (canapé, fauteuil) pouvant recevoir un voile.

---

## 12. Mobile

**Faits observés (home 390×844 ; restaurant L'Aigle d'Or)**
- Header 58 px transparent ; hero 540 px (64 %) ; H1 30/33 ; intro 20 px **justifiée** (rivières visibles sur `home-mobile-01-hero`).
- Grille : 9 cartes 358×448 empilées (section de 4 484 px) avec logo et BOOK NOW 132×37 ; onglets remplacés par deux pilules pleine largeur « ALL DESTINATIONS » et « HOTEL » 358×30 (14 px).
- Carrousel destinations 390×500 ; paragraphe 12/14,4 centré ; liste carte à 2 colonnes (vignettes 165 px) ; chips « Locations » / « Experience » 152×24 (12 px) ; carte Mapbox sous les filtres.
- **Barre BOOK NOW fixe** en bas : 390×65, `#f5f4f2` 85 % + blur 5 px, bouton 358×37, texte 16 px capitales.
- Tailles : 12 px ×55, 10 px ×27, 14 px ×38 ; `fontSizeSmall: 10`.
- Menu non observé (cookies) ; le DOM du panneau contient les 4 entrées, 5 langues et BOOK NOW ; sur la page restaurant il intègre aussi les onglets du lieu.
- Restaurant mobile : H1 32 px, CTA BOOK A TABLE 153×37 à 707 px (visible avant la barre basse), corps 14/15,4, docHeight 11 712 ; contenu réduit à 491 mots (820 en desktop : chapitres condensés).
- Perf mobile home : TTFB 324, FCP 1 072, DCL 2 752, load 5 416 ms ; 219 requêtes, 28,4 Mo (média 9,9 Mo, scripts 10,5 Mo, images 2,9 Mo). Restaurant mobile : 85 requêtes, 5,9 Mo, load 7 290 ms.
- Animations : mêmes vidéos autoplay (`playsinline`), sticky conservés (146 sur home mobile), carrousels conservés ; pas de version allégée.
- Problèmes : bannière cookies plein écran ; texte justifié ; 10–12 px ; 9,9 Mo de vidéo sur réseau mobile ; deux pilules de filtre au lieu des onglets (perte de la matrice destination × type visible).

**Interprétation**
- Le mobile est une réduction fidèle du desktop : mêmes sections, même ordre, barre CTA basse bien pensée. Mais la densité typographique (12 px, justification) et le poids média pèsent sur la lisibilité et la vitesse perçue (load > 5 s).
- Différence pertinente : la grille devient une pile de 9 « affiches » (logo sur photo) : c'est efficace comme feuilletage de marques, moins comme comparaison.

**Enseignements réutilisables**
- Barre CTA basse translucide + blur, 37 px de bouton, à copier.
- Sur mobile, servir une vidéo ≤ 3 Mo (ou un poster) et remonter les tailles à 14–16 px minimum.
- Garder les deux axes de filtre visibles (chips scrollables) plutôt qu'un seul menu.

---

## 13. Performance, accessibilité, SEO

**Faits observés**
- Home desktop : TTFB 436 ms, FCP 1 288 ms, DCL 1 849 ms, load 5 812 ms ; **552 requêtes, 73 Mo** (scripts 239 requêtes / 20,3 Mo ; média 6 / 29,4 Mo ; images 128 / 13,2 Mo ; polices 47 / 3,4 Mo ; fetch 91 / 2,3 Mo ; documents 5 / 3,3 Mo). Tiers : `cdn.prod.website-files.com` 213, `cdn.jsdelivr.net` 93 (Finsweet, Splide), `app.namastay.io` 68, `api.mapbox.com` 25, Axeptio, Sentry, GTM, `pagead2.googlesyndication.com`, Apple Pay, split.io.
- Page hôtel : TTFB 674, FCP 3 700, load 10 308 ms ; 448 requêtes, 51 Mo (média 18,2 Mo, scripts 12,9 Mo, images 10,3 Mo, fetch 136 / 5,6 Mo, Mapbox 94 requêtes).
- Mobile home : 219 requêtes, 28,4 Mo ; restaurant mobile 85 / 5,9 Mo.
- Lazy loading : 187/190 images `loading=lazy` sur la home, 224/226 sur explore ; webp majoritaire ; `srcset` sur 146 images. Vidéos `preload=metadata` sans poster.
- CSS : 294 Ko (2 fichiers Webflow + Splide + Plyr + Mapbox), `reducedMotionRules: 0`, 7 media queries (991, 767, 479, 768, 480, 1024, 992).
- Accessibilité : `lang=en` ; 1 H1 par page ; hiérarchie H1 → H2 (carrousel 64 px) → H3 (cartes 16 px) sur la home ; sur la page hôtel, H2 « ROOMS & SUITES » puis 13 H3 puis H2 « Gallery » : cohérent. **`focusOutlineNone: 200`** (outline supprimé sur 200 éléments, plafond du compteur) ; `tabindex="-1"` ×50 ; 8 à 16 liens sans nom (`linksNoName`) ; 13 boutons sans nom sur la page hôtel (flèches Splide, hypothèse) ; pas de skip link ; 14 `<nav>` landmarks (menus Finsweet) ; radios de filtre sans label ; formulaires newsletter sans `<label>` (placeholders), formulaire contact labellisé ; iframes titrées ; `ariaHidden` 13.
- Contrastes estimés : noir sur `#bdbcb9` ≈ 11:1 ; noir sur `#dedede` ≈ 15:1 ; noir sur `#d1cfc8` ≈ 13:1 ; blanc sur `#954935` ≈ 6,4:1 ; blanc sur `#622e1f` ≈ 11:1 ; **blanc 18 px sur `#8a816e` ≈ 3,9:1** (sous AA) ; blanc sur vidéo avec voile 0,3 : variable, 3–8:1 selon le plan (H1 60 px acceptable, « WATCH FULL VIDEO » 16 px à risque sur plan clair).
- SEO : title/description/og sur chaque page ; canonical ; hreflang 6 entrées ; JSON-LD typé par page (Organization, Hotel, Restaurant, CollectionPage, AboutPage, ContactPage, WebPage) ; URL parlantes et traduites (`/fr/explorer-bien-etre`, `/it/esplora-benessere`) ; 888 mots indexables sur la home, 1 509 sur l'hôtel ; `generator` absent (Webflow détecté par les scripts et les classes `w-`).
- Stabilité visuelle : non mesurée ; risques identifiés = polices custom (Nantes) sans `font-display` connu, vidéos sans poster, iframes Namastay.

**Interprétation**
- L'immersion (vidéos multi-formats, 190 images, carte vectorielle, moteur en overlay) coûte 73 Mo et 552 requêtes : c'est le site le plus lourd de la série, principalement à cause du double téléchargement webm + mp4 et de 239 scripts (Finsweet, Namastay, Mapbox, Splide, Plyr, GSAP, Sentry, analytics).
- Le SEO structurel est le point fort : maillage destination/lieu/service, hreflang, JSON-LD typé, alts complets.
- L'accessibilité clavier est le point faible : outlines supprimés, boutons de carrousel sans nom, filtres sans label, aucune règle reduced-motion.

**Enseignements réutilisables**
- Ne charger qu'un format vidéo par navigateur, avec poster, et différer Mapbox/Namastay au scroll ou au clic.
- Garder le JSON-LD par type de page et les alts descriptifs : facile, rarement fait à cette échelle.
- Réintroduire `:focus-visible` et nommer les flèches de carrousel.

---

## 8 bis / 9 bis — Compléments de la passe (hotels, destination, Cowley Manor, restaurant, design, beach)

**Page `/explore-hotels` (hotels)**
- Même gabarit que `/explore` : H1 36 px « Come for the design, return for the *experience* », mot fixe « HOTELS » 159 px en exclusion sur vidéo portrait 446×610 (`hotel_web-optimized_full` : webm 13,1 Mo + mp4 5,8 Mo), intro 36 px, carte sticky 1 380×812, 15 cartes hôtel 447×621 avec adresse / e-mail / téléphone / description 18 px / DISCOVER + BOOK NOW, blocs kaki `#8a816e` (« Everything at your fingertips », « The luxury of time away »), Offers (`#dedede`), LOCATIONS, newsletter. docHeight 12 036 ; 1 322 mots ; **420 requêtes, 96 Mo** (images 34,5 Mo, média 34,7 Mo) ; TTFB 405, FCP 1 704, load 5 724 ms.

**Page destination `/cotswolds`**
- Fil d'Ariane « ‹ Back / Costwolds » (coquille), H1 36 px italique « An escape to the countryside », mot fixe « COTSWOLDS » 101 px en exclusion sur photo portrait 446×610 du manoir ; fond de page vert-gris `#b1beb7` (classe `background-color-costwolds`) ; sous-nav fixe 131 px à 5 onglets (HOTEL, RESTAURANT, EXPERIMENTAL COCKTAIL CLUB, WELLNESS, BOUTIQUE) ; 5 chapitres de 1 864–1 923 px avec titres 140 px (5 occurrences) sur image pleine largeur voile 0,2, puis deux colonnes (image sticky 650×904 + texte 32 px / 18 px) et BOOK NOW 132×37 sur l'image épinglée ; pas de carte, pas de LOCATIONS. docHeight 13 886 ; 554 mots ; 224 requêtes, 19,8 Mo ; TTFB 231, FCP 920, load 2 322 ms.

**Page hôtel Cowley Manor (`/cotswolds/cowley-manor-experimental`)**
- Même gabarit que Val d'Isère, fond bleu ardoise `#3b4b5f` (texte blanc, `body.color: #ffffff`), logo « COWLEY MANOR » centré, sigle E* à gauche, fil d'Ariane 3 niveaux, hero photo (façade et parc, pas de vidéo), H1 60 px « a 5-star hotel, spa and restaurant… », carrousel 1/4 avec texte 36 px (« 300 years »), deux colonnes sticky, **12 catégories** (Wildflower, Petite Cowley, Treehouse, Wildflower with Terrace, Alpaca's Room, Water Lily, …, Grand Cowley Manor Suite) dans le carrousel 1 283×904, RESTAURANT & BARS (3 cartes : restaurant, ECC Cotswolds, Pool Bar), WELLNESS & SPA (« Our Pools »), WHAT'S ON **rempli** (« A New Chapter in Wellness », « Garden Tour with Lunch », date « OCTOBER 2026 »), PRIVATE EVENTS, ABOUT (« Discover the Gardens »), ACCESS & CONTACT (`stay@cowleymanor.com`), carte « 6 results », LOCATIONS, newsletter, double footer ; bloc contact bordeaux `#4f2828`. docHeight **25 469 px (28 viewports)** ; 1 728 mots ; 568 requêtes, 49,7 Mo (fetch Mapbox 227 requêtes / 10,8 Mo) ; TTFB 235, FCP 1 064, load 2 356 ms (pas de vidéo : chargement 4× plus rapide que Val d'Isère). 12 boutons sans nom (flèches Splide).

**Page restaurant Cowley Manor**
- Hero photo, H1 64 px, sous-nav « ‹ HOTEL | MENUS | SUNDAY ROAST | PRIVATE EVENTS | DESIGN | OUR COCKTAIL BAR | CONTACT & ACCESS », BOOK A TABLE 153×37 à y 763 ; chapitre MENUS **rempli** : 7 H3 32 px (Breakfast, Lunch, Dinner, Afternoon Tea Time, Sunday Roast, Barbecue, Winelist) + bloc chef « JACKSON BOXER X EXPERIMENTAL » ; plats nommés dans le texte 18 px (gougères, porc Old Spot) ; contact `eat@cowleymanor.com`. docHeight 17 897 ; 1 109 mots ; 294 requêtes, 26,8 Mo ; load 2 295 ms.

**Page `/design`**
- Hero image 913 px avec label « DESIGN » (H1 16 px gras) et H2 60 px ; intro 36 px ; carrousel 1/4 ; sections deux colonnes sticky (« Bespoke design as a *Signature* », « Rooted *in place* ») ; **galerie de 4 designers** (portraits 3:4, nom 24 px, rôle en capitales 12 px, bio 18 px : Dorothée Meilichzon « A reference for design », Rodolphe Parente, Tristan Auer, Fabrizio Casiraghi) ; citation « A partnership 17 years in the making » ; carrousel « Experimental x Anthony Dickens », « x Ingo Maurer » ; « An ethos evolving ». docHeight 10 505 ; **1 973 mots** (page la plus dense) ; 16 carrousels horizontaux (`horizontal: 16`) ; load 2 325 ms. Le produit « design » devient argument d'hébergement : « Design becomes the first encounter with the place ».

**Page `/explore-beach-clubs`**
- Mot fixe « BEACH CLUBS » 95 px ; 2 lieux seulement (Experimental Beach Ibiza, Bijou Plage Cannes) avec carte ; BOOK NOW vers `#restaurant&location&experimental-beach-ibiza` (ancre atypique) et `#booktable-bijouplage` ; blocs kaki éditoriaux ; 540 mots ; 362 requêtes, 35,2 Mo (scripts 18,6 Mo).

**Interprétation (compléments)**
- La chaîne destination → lieu → service est visuellement continue : la destination porte sa couleur (`#b1beb7`), le lieu la sienne (`#3b4b5f`), le service hérite du lieu ; le sigle E* et la sous-nav restent identiques. C'est l'exemple le plus abouti de la série d'un système à **trois niveaux de couleur**.
- Cowley Manor montre le gabarit hôtel « rempli » (What's on, menus, chef) : le gabarit fonctionne quand le contenu est là ; Val d'Isère montre ses trous.
- Le poids reste le problème structurel : 96 Mo sur `/explore-hotels` (une vidéo webm de 13 Mo + 100 images), 568 requêtes sur Cowley Manor.

---

## 14. Conclusion

**15 meilleurs éléments**
1. Architecture ombrelle → destination → lieu → service portée par les URL, les fils d'Ariane (3–4 niveaux) et les JSON-LD typés.
2. Système « invariants groupe / variables lieu » : mêmes polices, pilules et chapitres 120 px ; logo et couleur de fond propres à chaque lieu (`#d1cfc8`, `#3b4b5f`, `#b1beb7`).
3. Grille de lieux en deuxième position de la home : 9 « affiches » 447×559 avec logo, type, ville et BOOK NOW.
4. Double filtre destinations (13) × types (8) répété sur home, explore, offres.
5. Carte Mapbox épinglée (635×812 / 1 380×812) avec légende à 8 types et clusters, doublée par la liste.
6. Tiroir « Make a booking » à 4 entrées (chambres / tables / spa / événements) en overlay, sans changement de domaine.
7. Widget Namastay avec calendrier de prix par nuit et lien « Browse all Experimental hotels ».
8. Header 72 px en `mix-blend-mode: exclusion` : logo et CTA lisibles sur tout plan vidéo.
9. Barre CTA mobile basse 390×65 translucide + blur, bouton 358×37.
10. Mot de rubrique géant (89–159 px) fixé en exclusion sur vidéo portrait 4:5 des pages explore.
11. Colonne image épinglée 650×904 + texte défilant, réutilisée sur manifesto, design, hôtel, restaurant, destination.
12. Carrousel de destinations « impératif + ville + italique » : 14 slides au même moule.
13. Cartes de liste avec adresse, e-mail et téléphone cliquables par lieu.
14. Page design avec portraits de 4 designers et collaborations nommées : preuve par les auteurs plutôt que par les avis.
15. Alts descriptifs sur 100 % des images (190 / 226 / 98), webp et `srcset` généralisés, hreflang 5 langues avec slugs traduits.

**5 faiblesses / limites**
1. Poids : 73 Mo / 552 requêtes (home), 96 Mo (`/explore-hotels`), 51 Mo / load 10,3 s (Val d'Isère) ; webm et mp4 chargés tous les deux ; 239 scripts.
2. Pages hôtel de 23 000–25 500 px (26–28 viewports) en one-page, avec chapitres vides sur certains lieux (What's on, Menus).
3. Accessibilité clavier : `outline: none` généralisé, 12–13 boutons de carrousel sans nom, filtres sans label, aucune règle `prefers-reduced-motion`.
4. Mobile : 10–12 px fréquents, intro justifiée, bannière cookies plein écran en français sur un site anglais, 9,9 Mo de vidéo.
5. Chambres décrites sans surface, capacité ni prix « à partir de » ; aucune preuve sociale (avis, presse) nulle part.

**10 principes réutilisables**
1. Une palette groupe neutre (blanc, noir, 2 gris, 1 accent) + une couleur par lieu.
2. Deux polices seulement, l'une display serif, l'autre pour l'UI et le corps, italique pour le second segment des titres.
3. Titres de chapitre géants + signature graphique (astérisque) sur image pleine largeur, relayés par une sous-nav fixe.
4. Grille de lieux = sommaire ; carrousel de destinations = désir ; carte = outil ; ne pas mélanger les trois.
5. Fil d'Ariane visible dès le hero sur toute page de niveau ≥ 2.
6. Routage de réservation par type de service avant le moteur ; moteur en overlay avec prix visibles immédiatement.
7. Contact par lieu (e-mail, téléphone) dans les cartes de liste.
8. Ratios d'image fixes par usage (0,8 carte, 0,72 colonne, 1,42 chambre, 1,65 carrousel).
9. Une page « auteurs » (designers, chefs) comme preuve de marque quand on ne veut pas d'avis.
10. Barre CTA mobile basse, translucide, jamais plus haute que 65 px.

**Éléments propres à la marque à ne pas copier**
- L'astérisque « EXPERIMENTAL* » et le wordmark géant en footer.
- Les logotypes dessinés par lieu (Art nouveau, script, stencil) — ils tiennent à l'histoire bar → hôtel du groupe.
- Les fonds de couleur par lieu (bleu Cowley, beige Val d'Isère, vert Cotswolds).
- Le récit d'origine 2007 / trois amis / cocktail et la nomenclature « X Experimental ».
- Les mots fixes en exclusion (EXPLORE, HOTELS, COTSWOLDS) tels quels.

**Notes /10**
- **Branding : 9/10** — architecture à 4 niveaux lisible dans les URL, les logos et les couleurs ; tagline reprise en H1, footer, JSON-LD ; page design avec auteurs nommés. Retenue d'un point : « Coming Soon » et coquille « Costwolds » dans la navigation.
- **Direction artistique : 8/10** — deux polices, échelle de 12 à 159 px cohérente, ratios d'image stables, photographie étalonnée de façon homogène sur 70 lieux ; mais tailles 10–12 px mobile et blanc sur kaki `#8a816e` à ≈ 3,9:1.
- **Animations : 6/10** — sticky et exclusion bien utilisés, transitions constantes 0,2 s ; mais aucun feedback de survol sur les cartes, aucun `prefers-reduced-motion`, GSAP chargé sans trigger sur la home.
- **UX : 7/10** — matrice destination × type + carte, fil d'Ariane, sous-nav fixe ; contre : one-pages de 26–28 viewports, chapitres vides, sous-nav qui consomme 131 px, onglets qui débordent.
- **Conversion : 6,5/10** — CTA persistant desktop et mobile, tiroir de routage, calendrier de prix Namastay, offres avec prix et `ratePlanCode` ; contre : 3 écrans avant les dates, zéro preuve sociale, pas de « à partir de » ni de faits chambre, 6 moteurs différents.
- **Mobile : 6/10** — barre CTA basse et sections fidèles ; contre : 28,4 Mo, 10–12 px, justification, cookies plein écran, menu contextuel non vérifié.
- **Note globale : 7,3/10** — le meilleur système de marque multi-lieux de la série (cohérence graphique entre hôtels, restaurants, spas et beach clubs par gabarit unique et couleurs de niveau), pénalisé par un poids exceptionnel et une accessibilité négligée.

**Ce que ce site apporte que les sites « quiet luxury » (FORESTIS, Seagate, Le Collectionist) n'apportent pas**
- Une **hiérarchie d'entités** (groupe → destination → lieu → service) rendue par la couleur de fond, le logo et le fil d'Ariane, là où le quiet luxury travaille une seule entité.
- La **carte comme colonne épinglée** avec légende typologique et clusters numérotés : l'abondance devient un argument.
- Des **logotypes multiples** assumés sur une grammaire commune : la variété graphique comme signe de curation, à l'opposé de l'uniformité.
- Une **couleur chaude franche** (terracotta `#954935`) et des fonds kaki/ardoise : pas de beige unique.
- Un **calendrier de prix par nuit** et des offres à prix affichés, là où le quiet luxury reste sur « demander ».
- Une page **design par auteurs** (designers, chefs) comme preuve.
- Un **tiroir de routage** chambres / tables / spa / événements : le site vend quatre choses, pas un séjour.

---

## Observations clés à conserver pour la phase comparative

- Header 72 px (58 mobile) transparent, `mix-blend-mode: exclusion`, pilule BOOK NOW 120×37, rayon 15 984 px, hover 0,2 s inversion ; barre mobile basse 390×65 blur 5 px.
- Polices : Nantes (display 60–159 px, italique sur 2ᵉ segment) + Linux Biolinum (corps 18/21,6, UI 14–16 px capitales 0,42–0,48 px) ; mobile H1 30 px, corps 12–14 px, 27 occurrences de 10 px.
- Palette groupe `#ffffff / #000000 / #bdbcb9 / #dedede / #954935` ; couleurs de niveau : destination `#b1beb7`, lieu `#d1cfc8` et `#3b4b5f`, explore `#8a816e`, contact `#622e1f` / `#4f2828`.
- Home 6 786 px (7,5 vp) : hero vidéo 100 % → intro 36 px → grille 9 cartes 447×559 (2 096 px) → carrousel 14 destinations (495 px) → carte sticky 635×812 + liste « 70 » → Manifesto → newsletter → footer wordmark.
- Pages hôtel one-page : Val d'Isère 23 267 px / 13 chapitres 120 px / 13 catégories ; Cowley Manor 25 469 px / 12 catégories ; sous-nav fixe 131 px (blanc 80 %, blur 35 px) ; chambres sans m², capacité ni prix.
- Explore : mot fixe 89–159 px en exclusion sur vidéo 446×610 ; cartes 447×621 avec adresse / e-mail / tél ; carte 1 380×812 sticky ; « 62 results ».
- Réservation : tiroir 4 choix → Namastay overlay (calendrier €610–€1 190/nuit, « Browse all hotels ») ; SevenRooms `#booktable-`, Pure `#bookpure-`, Resy/Tock NY, wearegifted, bonkdo ; offres avec `ratePlanCode` et prix (£70–£95).
- Mouvement : GSAP 3.15.1 + ScrollTrigger chargés, 0 trigger ; 17–18 interactions Webflow ; sticky = carte + colonnes 650×904 ; 0 parallaxe, 0 reveal, transitions .2s ×48, easing `cubic-bezier(.4,0,.2,1)` ×2 ; `reducedMotionRules: 0`.
- Poids : home 552 req / 73 Mo (média 29,4, scripts 20,3, images 13,2) ; mobile 219 req / 28,4 Mo ; `/explore-hotels` 96 Mo ; Val d'Isère 448 req / 51 Mo / load 10,3 s ; Cowley (sans vidéo) load 2,4 s.
- TTFB 231–712 ms, FCP 920–3 700 ms selon page ; vidéos webm + mp4 toutes deux sollicitées (206), `poster` vide.
- A11y : `focusOutlineNone` 200, `tabindex -1` ×50, 12–13 boutons sans nom (hôtel), 8–18 liens sans nom, radios de filtre sans label, pas de skip link, 9–14 `<nav>` ; alts 100 %.
- SEO : 1 H1 partout, hreflang en/fr/it/pt/es + x-default avec slugs traduits, JSON-LD Organization / Hotel / Restaurant / CollectionPage / AboutPage / ContactPage ; wordCount 888 (home) → 1 973 (design).
- Copy : moule « impératif + ville + italique » ×14 ; lexique escape / storied / crafted / haven / sanctuary / beneath ; « luxury » réservé aux meta.
- Défauts de contenu : « Costwolds », « Envoyer » sur formulaire EN, cookies FR, What's on et Menus vides à Val d'Isère, « Coming Soon » dans le menu, double slash `experimentalmarais.com//`.
- Contrastes : noir/`#bdbcb9` ≈ 11:1 ; blanc/`#954935` ≈ 6,4:1 ; blanc/`#8a816e` ≈ 3,9:1 (sous AA en 18 px).
