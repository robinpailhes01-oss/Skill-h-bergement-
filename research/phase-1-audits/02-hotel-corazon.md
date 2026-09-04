# Fiche d'audit — Hotel Corazón (clé `corazon`)

## 0. En-tête

- **Nom** : Hotel Corazón — agroturismo, 12 chambres listées (le texte About en annonce 15), Serra de Tramuntana entre Deià et Sóller, Majorque.
- **URL de départ** : https://www.hotelcorazon.com/ — **Date** : 2026-09-04 (16:40 UTC site principal, 16:51 UTC moteur).
- **Environnement** : Chromium headless / Playwright, 1440×900 (desktop) et 390×844 DPR 2 (mobile).

| Label | URL | Desktop | Mobile |
|---|---|---|---|
| home | https://www.hotelcorazon.com/ | oui | oui |
| rooms | https://www.hotelcorazon.com/rooms | oui | non |
| room-detail (Baba Royale) | https://www.hotelcorazon.com/rooms/baba-royale | oui | oui |
| about | https://www.hotelcorazon.com/about | oui | non |
| contact | https://www.hotelcorazon.com/contact | oui | non |
| restaurant (sous-site WordPress) | https://hotelcorazon.com/restaurantbookings/ | oui | oui |
| engine (moteur eZee) | https://live.ipms247.com/booking/book-rooms-hotelcorazon | oui | non |
| booking (sonde depuis la home) | https://www.hotelcorazon.com/ | oui | non |
| flows (menu mobile, chambre mobile) | flows.json, flow-mobile-menu.png, flow-mobile-room-full.png | — | oui |

**Limites de l'observation**

- Le hero est un iframe Vimeo (`player.vimeo.com/video/814672819?autoplay=1&loop=1&autopause=0&muted=1`) qui affiche « Player error » sur toutes les captures : **lecture, autoplay, boucle et contenu non vérifiés**. Les segments vidéo ont bien été téléchargés (§13), preuve que le lecteur s'initialise.
- Le bloc de 574 px de l'iframe apparaît vide (rouge) dans `home-02-full.png` ; une bande translucide du header fixe traverse les captures pleine page (ex. `rooms-02-full.png` y≈1080) : artefacts de capture.
- Seule l'étape 1 du moteur a été ouverte (dates par défaut 4→5 sept. 2026) ; aucune réservation validée. Les sous-sites Shop et Events (Odoo) n'ont pas été capturés ; le moteur n'a pas été capturé en mobile.
- Hovers mesurés par styles calculés ; tactile non vérifiable ; Lighthouse indisponible (pas de LCP/CLS).
- Le header apparaît inversé (fond brun, texte rouge) sur `home-03-scroll1`, `home-04-reduced-motion`, `home-03-scroll5`, mais le style calculé mesuré après scroll rapporte `#d0342c` : le mécanisme (classe JS via `toggle.js` ?) est une hypothèse.

---

## 1. Positionnement de marque

**Faits observés**

- Meta description home : « Mallorca luxury agroturismo in the Tramuntana Mountains, between Deià and Sóller » ; About : « 15-room Mallorca luxury hotel, farm, restaurant, art space ».
- Intro home (207 mots indexables) : lieu → manifeste → liste de gestes (pieds nus, manger dans les arbres, nager la nuit) → punchline de deux lignes opposant luxe et sauvage.
- Vocabulaire récurrent : « agroturismo », « finca », « wild », « freedom », « barefoot », « no TVs », « artists », « community », « medicinal », « regenerative ».
- About : quatre blocs H4+H2 bilingues EN/ES (« THE PROPERTY / EL AGROTURISMO », « POOL / LA PISCINA », « THE FAMILY CORAZÓN / LA FAMILIA CORAZÓN », « EXTENDED FAMILY / AMIGOS / RIDE OR DIES ») ; propriétaires (Kate et Edgar), artistes et cheffe (Eliza Parchanska) nommés.
- Chambres désignées par des noms propres (Baba Royale, Holy Wood, Smoked Cedar…), la catégorie « Superior Double Room » en H4 15 px.
- Écosystème sur 4 technologies : site principal (statique, Swiper, `toggle.js`), restaurant (WordPress + Elementor 4.2.3, Zenchef), events (Odoo), moteur (eZee / ipms247).
- Prix moteur (1 nuit, 4→5 sept.) : 427,27 € (Holy Ficus) à 1 654,55 € (El Corazón Suite), +≈10 % de taxes, séjour minimum 2 nuits.

**Interprétation**

- Positionnement : bohème-luxe rural, entre agroturismo majorquin et « creative retreat » pour urbains internationaux. Promesse centrale : la **liberté** (pas de télé, pas de règles), pas le confort.
- Cible : couples et petits groupes 30–50 ans, créatifs, budget 430–1 650 €/nuit, en quête d'adresse d'initiés et de communauté.
- Gamme perçue : luxe non conventionnel — prix du luxe, aucun code visuel du luxe hôtelier (pas de blanc, de serif, de photo de spa). La différence avec un site générique tient à **la couleur unique et la typographie unique en guise de signature**, là où un site générique empile blocs blancs, icônes et badges.
- Territoire : chaleur, nuit d'été, terre rouge, insolence douce (« insane egg-shaped dome shower »). Personnalité : hôte-artiste qui tutoie. Valeurs : simplicité, artisanat local, régénération agricole, communauté.
- L'expérience passe avant la chambre : manifeste de 1 043 px **avant** la grille, lieu décrit par ses activités (yoga, sound healing, randonnées, jam sessions) plutôt que par ses services.
- Cohérence forte mots/images (photos chaudes, ambrées, sans personnes), plus faible avec les interactions (site quasi statique) et **rompue sur les sous-sites** (H3 caché Raleway cyan `#1bb0ce` sur le restaurant, moteur en Inter sur `#f3f6f9`).

**Enseignements réutilisables**

- Un seul geste radical (couleur + police) différencie si tout le reste s'y soumet.
- Nommer les gens (propriétaires, cheffe, artistes) crédibilise sans avis clients.
- Le manifeste précède l'inventaire : ordre BOOK NOW → vidéo → manifeste → chambres.

---

## 2. Première impression (5 premières secondes)

**Faits observés** (`home-00-initial.png`, `home-01-hero.png`, `home-mobile-01-hero.png`)

- Fond rouge `#d0342c` plein avec grain fin (2 `bgImages` détectées ; nature exacte = hypothèse).
- Header fixe `#header.header__nav` 128 px, z-index 99, logo « HOTEL / CORAZÓN » centré, menu 3 + 3 : ROOMS · RESTAURANT · EVENTS | ABOUT · SHOP · CONTACT, 18 px capitales brun `#371810`.
- Premier élément : bandeau **BOOK NOW** 1020×78 à y = 160, fond brun, texte rouge 24 px, lien vers `live.ipms247.com`.
- Iframe Vimeo 1020×574 à y = 318 → « Player error » sur dégradé rouge→noir, bouton « Unmute ». À 900 px de haut, on voit header + BOOK NOW + 58 % de la vidéo.
- Aucun bandeau cookies (`cookie: None`), aucun pop-up, aucun préloader.
- Mobile : logo centré, burger 48×41, BOOK NOW 360×78 à y = 160, iframe 360×203.
- 0 H1 ; premier texte lisible « WELCOME TO THE / HOTEL CORAZÓN » à y ≈ 1 130.

**Interprétation**

- On voit un aplat rouge et un logo — une affiche. On comprend « hôtel » (dans le logo) et « réservez ». On ressent chaleur et insistance.
- Le message principal est la couleur ; la vidéo devait porter le reste (non vérifié). Le premier CTA est le plus gros élément visible, rare sur ce segment.
- Distraction en headless : l'erreur du lecteur ; en navigateur réel, risque de démarrage lent (chunks ≥ 4 Mo, §13).
- Raison de continuer : la curiosité créée par l'absence d'explication et ROOMS en première position du menu.

**Enseignements réutilisables**

- Un fond plein en guise de hero fonctionne avec un logo très dessiné.
- Un CTA pleine largeur sous le header exige une accroche à côté : ici aucun H1 ne dit où l'on est.

---

## 3. Direction artistique

**Faits observés**

- Variables CSS : `--color-red: #D0342C`, `--color-red-dark: #a2261f`, `--color-black: #371810`, `--color-beige: #EADCC7`. Fonds mesurés : `#d0342c` ×148, `#371810` ×8. Textes : `#371810` ×107, `#d0342c` ×13. Le beige n'apparaît qu'au hover (logo/lien header rouge → `rgb(234,220,199)`).
- Police unique **Klinsman** (`KlinsmanTypeface.woff2`, 34 Ko), graisse 400, `uppercase` sur body, titres et boutons. **Soerip** déclarée en `@font-face` et chargée seulement sur la page chambre pour FEATURES/AMENITIES en 13 px (police à petites capitales de type stencil d'après la capture — hypothèse).
- Échelle (identique mobile, aucune règle fluide) : H1 56 px / interlettrage −1 px / interligne 56 ; H2 48 / −1 / 48 ; H4 surtitre 15 / +1 / 15 ; corps 18 / 27 (ratio 1,5) ; bouton 16 / +1 ; listes 13 (Soerip) ; BOOK NOW 24.
- Grille : conteneurs 1080 et 1200 px ; contenu utile 1020 px ; paragraphes centrés 693 px (home, chambre) ou 720 px (about, contact). Tout est centré, y compris le tampon du footer.
- Espacements : intro home 1 043 px pour ~180 mots ; 80 px entre BOOK NOW et vidéo ; cartes 500×327–334, gouttières ~20 px.
- Rayons : 0 px sur les liens ; ~2–4 px sur cartes et bandeau (visible sur `home-03-scroll3.png`) ; « SHOW ALL ROOMS » 232×55, bordure 2 px, rayon 2 px.
- Étiquettes de cartes : bloc brun ~180×62 en bas à gauche, texte rouge 15 px, chevauchant la photo.
- Iconographie : palmier dans un cartouche (home), tampon circulaire à créature ailée (chambre), tampon « KM 56.7 HOTEL.CORAZON » (footer, alt « Corazón Milestone »). Aucune icône d'équipement.
- Photos accordées au fond (saumon, terracotta, olive), sans filtre CSS hors `brightness(0.8)` au hover. Vignettes webp 622–640×415 (ratio 1,5) ; carrousel chambre portrait 419–427×640 (≈2:3) ; About 16 JPG 1080×770 (1,4) + une 2400×1600.
- Restaurant : photos cerclées d'un filet noir ~8 px, Klinsman graisse 100, corps 16 px `#444444`.

**Tableau de tokens approximatifs**

| Token | Valeur | Usage |
|---|---|---|
| color.red | `#D0342C` | fond global, texte CTA sur brun, header inversé |
| color.red-dark | `#A2261F` | soulignement hover des mailto |
| color.black (brun) | `#371810` | texte, BOOK NOW, étiquettes, menu mobile |
| color.beige | `#EADCC7` | hover logo/lien header |
| font.display/body | Klinsman 400, uppercase | tout |
| font.detail | Soerip 13 px | listes features/amenities |
| type | H1 56/56 ls −1 · H2 48/48 ls −1 · eyebrow 15/15 ls +1 · body 18/27 · cta 24 · button 16 ls +1 | — |
| header.height | 128 px desktop = mobile | fixe |
| cta.book | 1020×78 / 360×78 | bandeau |
| card.room | 500×327–334, ratio 1,5 | grille 2 colonnes |
| gallery.room | 419–427×640, ratio 2:3 | Swiper |
| radius | 0–2 px boutons, ~2–4 px cartes | — |
| container | 1080/1200 ; contenu 1020 ; texte 693–720 | — |
| transition | 0.3 s (liens), 0.5 s ×24 (cartes, hypothèse filtre), 0.6 s ×3, 0.15 s (burger) | — |
| easing | non spécifié (1 `linear` détecté ; défaut `ease` = hypothèse) | — |

**Interprétation**

- Système **bichrome** à une famille typographique : la cohérence vient de la contrainte. La symétrie totale renvoie à l'affiche et à l'étiquette de produit.
- Le vide est abondant mais **monotone** : 1 043 px d'intro sans image ; 400 px de rouge vide avant le footer de Contact (1 254 px pour 67 mots).
- Les photos portent le luxe (lumière rasante, lin, laine, micro-ciment, laiton, voûtes) ; leur accord chromatique avec le fond est la trouvaille de la DA.
- Capitales 18 px sur 693 px (≈60 caractères/ligne) restent lisibles, mais le contraste ≈3,2:1 (§13) pénalise les 428 mots d'About.

**Enseignements réutilisables**

- Accorder la colorimétrie des photos au fond évite le « bloc blanc ».
- Cinq tailles suffisent avec une police de caractère ; prévoir une réduction mobile des titres.
- Réserver une couleur secondaire aux hovers crée un « effet secret ».

---

## 4. Architecture de la page d'accueil

**Faits observés** — hauteur 4 887 px desktop, 6 060 px mobile.

| Position (y) | Section | Objectif | Contenu | Interaction | CTA | Émotion créée |
|---|---|---|---|---|---|---|
| 0–128 (fixe) | Header | Orientation | Logo centré, 6 liens 3+3 | Hover : brun→rouge + soulignement centré (::after 69 px) ; inversion brun/rouge observée au scroll | RESTAURANT, CONTACT | Signalétique |
| 160–238 | `.booking__link` | Conversion immédiate | Bandeau 1020×78 brun, texte rouge 24 px | Hover : texte rouge→beige 0.3 s | BOOK NOW → moteur | Urgence calme |
| 318–892 | `.landing__video` | Immersion | Iframe Vimeo 1020×574 | Non vérifiable | — | Non vérifiable |
| 1 132–2 175 | `.landing__intro` | Manifeste | H4 + H2 « HOTEL CORAZÓN », 4 paragraphes 693 px, punchline, icône palmier | Aucune | — | Liberté, appartenance |
| 2 295–4 523 | `.rooms` | Inventaire | H4 + H2 « SUITES & ROOMS », grille 2×6 de cartes 500×330 étiquetées | Hover `brightness(0.8)` | 12 liens /rooms/<slug> | Désir, projection |
| ~4 700–4 887 | Footer | Sortie | CONTACT · PRIVACY POLICY / tampon KM 56.7 / INSTAGRAM · NEWSLETTER | Soulignement 0.3 s | CONTACT, NEWSLETTER | Signature |

**Interprétation — logique narrative**

- Début par l'action (BOOK NOW) puis l'image : ordre inversé par rapport à « hero → promesse → preuve → action ».
- Désir construit par le manifeste (texte seul) puis par 12 photos ; **aucune étape intermédiaire** (restaurant, piscine, activités) sur la home.
- L'offre devient concrète dans la grille, classée par prix décroissant (El Corazón Suite 1 654 € en premier, Smoked Cedar 472 € en dernier) — l'inverse du moteur.
- Preuve : aucune (0 avis, 0 presse). Réservation : un seul point d'entrée, sans rappel en bas. Fin : tampon-signature.

**Enseignements réutilisables**

- Quatre sections radicales peuvent suffire, mais sans section « expérience » le manifeste reste sans illustration.
- Classer du plus cher au moins cher ancre la gamme dès la première carte.

---

## 5. Scroll et storytelling

**Faits observés**

- Attributs d'animation : tous à 0 (`aos`, `data-scroll`, `reveal`, `parallax`, `marquee`, `splitText`, `sticky`, `horizontal`). `horizontal: 2` sur chambre et About = instances Swiper.
- Sonde de scroll (15 positions, 0→3 987 px) : 0 élément épinglé, 0 transform ou opacité en cours ; `tr 1` sur la page chambre entre y = 0 et 719 = translate du Swiper.
- `scrollSnap: 5`, `positionSticky: 2`, 32 keyframes, `clipPath: 3`, `mixBlend: 6` sur la home seulement ; CSS total 272 Ko (home) contre 33,9 Ko ailleurs → règles du lecteur Vimeo (hypothèse forte).
- Alternance : header → CTA → vidéo → texte 1 043 px → images 2 228 px → footer. Aucun changement de fond ; seuls contrastes : blocs bruns.
- About : texte 108 px → carrousel 16 images 1020×727 → texte 2 731 px avec deux images pleine largeur (Porsche rouge, parasols de chaume).
- Mobile : intro 1 442 px de texte, grille 3 262 px (12 cartes 360×235).

**Interprétation**

- Rythme **éditorial, pas cinétique** : brochure verticale sans révélation, parallaxe ni sticky.
- Fonctions des rares effets : header inversé (orienter, état « en navigation ») ; brightness au hover (feedback) ; soulignement centré (marque).
- Densité inégale : paroi de capitales, grille dense, Contact presque vide. Le rouge sert de respiration mais, sans variation de ton, devient uniformité. L'envie de poursuivre vient des photos.
- Mobile : aucun jank, mais 6 060 px sans ancre ni retour au CTA.

**Enseignements réutilisables**

- Sans animation de scroll, varier fonds ou largeurs pour créer un rythme.
- Éviter les parois de texte en capitales > 150 mots sans image.

---

## 6. Animations et micro-interactions

**Faits observés** : transitions 0.5 s ×24, 0.3 s ×5, 0.6 s ×3, 0.15 s ×1 ; easing détecté `linear` ×1 ; les cubic-beziers du CSS (`(0.215,0.61,0.355,1)`, `(0.55,0.055,0.675,0.19)`…) proviennent de Swiper/Vimeo (hypothèse). Libs : Swiper 9, Vimeo Player, GA ; aucune lib d'animation. Curseur `auto`, 0 curseur custom.

| Animation | Déclencheur | Élément | Effet | Fonction | Risque UX |
|---|---|---|---|---|---|
| Arrivée / préloader | chargement | — | Aucun (section visible opacity 1) | — | Page « sèche » |
| Vidéo hero | autoplay | iframe Vimeo | Non vérifiable ; autoplay/loop/muted/autopause=0 | Immersion | Chunks > 4 Mo, pas de poster propre, « Unmute » visible |
| Hover lien menu | survol | `a` header | `#371810→#d0342c` ; `::after` 69 px + `translateX(-34.57px)` = soulignement **depuis le centre** ; ~0.3 s (hypothèse) | Marque, feedback | Aucun |
| Lien actif | page courante | ex. CONTACT | Soulignement fixe | Orientation | Aucun |
| Hover BOOK NOW | survol | bandeau | texte/bordure `#d0342c→#EADCC7`, 0.3 s | Feedback | Aucun |
| Hover carte | survol | `img .room__thumb` | `brightness(1→0.8)`, ~0.5 s (24 transitions = 12 cartes × 2) | Feedback | Assombrit des photos déjà sombres ; n'apporte aucune info |
| Hover SHOW ALL ROOMS | survol | bouton | fond → `#371810`, 0.3 s | Feedback | Aucun |
| Hover footer / mailto | survol | `a` | border-bottom visible (`#a2261f` sur contact), 0.3 s | Feedback | Soulignement ≈2,2:1 sur brun |
| Header inversé | scroll (hypothèse `toggle.js`) | `#header` | fond brun, texte rouge | État | Bascule brutale si sans transition (non mesurée) |
| Burger | tap | 48×41 | `background-color/opacity 0.15s linear` ; overlay brun, `overflow: hidden` | Navigation | Ouverture sèche |
| Carrousel chambre | flèches/drag/dots | Swiper 7 slides | translate (easing Swiper, hypothèse `ease`) | Explorer | Flèches fines, 7 dots de 8 px |
| Carrousel About | idem | Swiper 16 slides | idem | Explorer | Sans légende ni compteur |
| Lightbox / zoom | — | — | Aucun | — | Photo non agrandissable |
| Transition de page | clic | — | Aucune | — | Neutre (rouge → rouge) |
| Reduced motion | `prefers-reduced-motion` | `*` | `animation/transition-duration: .01ms`, `scroll-behavior: auto` (1 règle main.css, 6 avec Vimeo) | Accessibilité | Capture identique : rien à couper |

**Interprétation**

- Site **quasi statique** : trois micro-interactions maison et deux composants tiers. La signature est le soulignement qui pousse depuis le centre, cohérent avec la symétrie.
- Manques : aucune apparition, aucun hover informatif (surface, vue, prix), aucun agrandissement d'image.

**Enseignements réutilisables**

- Un soulignement animé depuis le centre signe un menu centré à coût nul.
- Sur des cartes photo, préférer un hover qui apporte une information à un assombrissement.

---

## 7. Navigation et architecture de l'information

**Faits observés**

- Menu : ROOMS · RESTAURANT · EVENTS · [logo] · ABOUT · SHOP · CONTACT. Trois entrées sortent du site : RESTAURANT → WordPress (menu différent : HOTEL · RESTAURANT · MENU · BOOK A TABLE · EVENTS · SHOP · CONTACT US), EVENTS → `hotel-corazon.odoo.com/event`, SHOP → `/shop`. Ouverture dans le même onglet (hypothèse : aucun `target` détecté).
- Le DOM du header contient un sous-menu de 12 chambres non visible au repos ; 4 hrefs tronqués dans le JSON (« ttps://…/baba-royale », « //www.…/el-corazon-suite ») — troncature outil ou attributs mal formés (hypothèse).
- Aucun bouton de réservation dans le header ; BOOK NOW seulement sur home (y = 160) et pages chambre (y = 1 296). Rooms, About, Contact : **aucun CTA de réservation**.
- Mobile : burger 48×41 → overlay brun plein écran, 6 liens ~40 px rouges séparés de filets 1 px, croix en haut à droite, PRIVACY POLICY · INSTAGRAM en pied. Pas de BOOK NOW dans l'overlay. Ordre différent du desktop (EVENTS/SHOP/ABOUT).
- Contact : H1, distances (aéroport 45 min, Deià et Sóller 10 min), adresse, mailto `bookings@` et `events@`. Pas de téléphone, carte ni formulaire.
- Étapes vers une offre : home → BOOK NOW → moteur (1 clic) ; home → carte → BOOK NOW pré-filtré (2 clics) ; depuis About/Contact/Rooms : 2–3 clics.

**Interprétation**

- Architecture plate et lisible, mais écosystème fragmenté : trois technologies, trois menus, trois identités partielles ; le retour depuis le restaurant passe par « HOTEL ».
- Aucun numéro de téléphone pour un hôtel à 430–1 650 €/nuit : friction.
- Frustration principale : pas de CTA persistant ; sur la home mobile, après les 12 chambres, il faut remonter 5 800 px.
- Trouver une chambre est facile ; trouver une prestation demande de lire une liste à puces sur About.

**Enseignements réutilisables**

- Conserver le même header et un retour visible sur tous les sous-sites.
- Un bandeau géant en haut ne dispense pas d'un rappel sticky ou de fin de page.

---

## 8. Parcours de réservation et conversion

**Faits observés**

- Premier CTA : BOOK NOW 1020×78 / 360×78, y = 160, lien direct vers `live.ipms247.com/booking/book-rooms-hotelcorazon`. Sur la chambre : BOOK NOW → `roomwisedata.php?hid=hotelcorazon&roomtypeunkid=…` (pré-filtré) + « CHECK AVAILABILITY » 15 px.
- Formulations : BOOK NOW (réserver), CHECK AVAILABILITY (vérifier), SHOW ALL ROOMS (découvrir), CONTACT (demander, mailto).
- Site principal : `forms: []`, `dateInputs: []` — dates et voyageurs uniquement sur le moteur (défaut 4→5 sept., 1 chambre, 2 adultes).
- Moteur, étape 1 (`engine-01-hero.png`, `engine-02-full.png`) : header blanc sticky 84 px avec logo et « Explore Property », dates/voyageurs, code promo, devise EUR ; « Showing 12 of 12 Offers » ; cartes avec photo 380×253, « Max Adults / Max Child », literie (« Double 180×210 », « Twin 160×190 », « King 200×200 »), 3 chips (Air Conditioning, Bath Essentials, Bathrobe), « View Room Details ». Bloc tarif : badges « Filling Fast » / « Best seller », « Room only », « Non-refundable » en rouge, « Breakfast not included », « Total for 1 Night » + « Taxes & fees » (427,27 € + 42,73 €), bouton **« Sold Out »** gris et « You need 1 more night to book this room » sur 8 chambres sur 12 ; bandeau vert « Next available check-in: 7 Sep / 9 Sep » + « View availability » sur 4.
- Prix lus (1 nuit) : Holy Ficus 427,27 ; Smoked Cedar 472,73 ; La Calma 518,18 ; Rosewood, La Cueva, La Palmier 563,64 ; The Sage, Holy Wood 872,73 ; Baba Royale 1 090,91 ; Tramuntana Haze 1 109,09 ; The Sweet 1 363,64 ; El Corazón Suite 1 654,55 €.
- Réassurance sur le site : aucune (0 avis, 0 label, 0 politique d'annulation, 0 bénéfice direct, 0 package, 0 conciergerie). Services listés à puces sur About (yoga, massage, reiki, randonnées, bateau).
- Restaurant : widget Zenchef « Reserve a table » fixe (iframe 224×900, z-index 2147483647), horaires 8:30–11:00 / 12:30–16:00 / 18:00–22:00.
- Ruptures moteur : domaine, police Inter, fond `#f3f6f9`, rayons 8–20 px, ton (« Filling Fast », « Non-refundable »). Continuité : logo, rouge `#d0342c` sur 52 éléments.

**Interprétation**

- Parcours **court mais brutal** : d'une affiche rouge à un comparateur gris en un clic ; rien ne prépare au prix, au minimum 2 nuits ni au « room only, non-refundable ».
- Le pré-filtrage `roomtypeunkid` est un bon point.
- Défaut de paramétrage : dates par défaut d'une nuit + minimum 2 nuits ⇒ **8 « Sold Out » sur 12** à la première visite, avec des badges « Filling Fast » contradictoires.
- Le moteur pèse 44,2 Mo (28 JPG « (Large) » ≈ 2 Mo) contre 858 Ko pour la page chambre.

**Enseignements réutilisables**

- Annoncer conditions et fourchette de prix sur la page chambre avant le moteur.
- Passer le contexte chambre dans l'URL du moteur ; régler ses dates par défaut sur la durée minimale.

---

## 9. Pages chambres — Baba Royale

**Faits observés — desktop** (hauteur 2 578 px)

1. y = 160–840 : carrousel Swiper 680 px, 7 photos **portrait** 419–427×640 centrées, une visible à la fois (30 % de la largeur du viewport), flèches à x ≈ 264 et 1 176, 7 dots de 8 px. Sujets : rideaux saumon sur palmiers et montagne, baldaquin, fenêtre ouverte sur le jardin.
2. y = 960 : H4 « SUPERIOR DOUBLE ROOM » 15 px + H1 « BABA ROYALE » 56 px.
3. y = 1 101 : paragraphe 693 px, ~60 mots : étage, deux balcons français, vues, coin salon avec cheminée décorative, douche « en dôme en forme d'œuf », hauteur sous plafond.
4. y = 1 296 : **BOOK NOW** 1020×78 + « CHECK AVAILABILITY ».
5. y ≈ 1 500 : deux colonnes Soerip 13 px séparées d'un filet : **FEATURES** (super king, 4 oreillers plume, draps 100 % lin, **45 m²**, micro-ciment, vasque pierre, laiton, exposition sud/est, lit orienté est) et **AMENITIES** (produits de bain bio de l'île, deux peignoirs, minibar Nordaq/vins/boissons maison, bouilloire, tisanes du jardin, café Mistral, clim, enceinte Marshall, wifi).
6. y = 1 831 : tampon créature ailée ; y = 2 078 : « SHOW ALL ROOMS » 232×55 ; footer.
- Absents : prix, capacité (« 2 adultes » seulement sur le moteur), plan, vidéo, avis, chambres similaires, navigation précédente/suivante.
- Metadata : title et description spécifiques ; og:image générique `default.png`. 9 images, 7 lazy, alt « Baba Royale » ×7, 0 `srcset`.

**Faits observés — mobile** (`flow-mobile-room-full.png`, 3 040 px)

- Même ordre. Carrousel 590 px, image 360×540–550, flèches superposées à ~40 px des bords ; H1 56 px sur 2 lignes ; paragraphe 360 px sur 10 lignes ; BOOK NOW 360×78 à y = 1 370 ; FEATURES/AMENITIES empilés (996 px) ; burger 48×50.

**Interprétation**

- La page vend le **caractère** (douche-œuf, lit orienté est, tisanes du jardin) et l'**artisanat** (micro-ciment, pierre, laiton, lin) ; les specs en 13 px dans une police secondaire disent « l'histoire d'abord ».
- Ordre galerie → nom → récit → CTA → specs efficace ; CTA à 1,4 écran desktop, 1,6 mobile.
- Faiblesses de projection : une photo portrait étroite à la fois, pas de lightbox ni de plan, pas de prix « à partir de », pas de capacité, « SHOW ALL ROOMS » au lieu de 2–3 suggestions.
- Mobile : flèches sur les photos, dots de 8 px difficiles à viser ; ~35 caractères/ligne en capitales.

**Enseignements réutilisables**

- Séparer récit (18 px, centré) et specs (13 px, autre police, deux colonnes) permet de parler luxe sans catalogue.
- Ajouter surface, capacité et prix indicatif dans le premier écran, plus 2–3 chambres suggérées.

---

## 10. Copywriting

**Faits observés**

- Volumes : home 207 mots, rooms 40, chambre 145, about 428, contact 67, restaurant 154. Capitales par CSS. Anglais seul (`lang="en"`, 0 hreflang), titres EN/ES sur About.
- Titres : surtitre H4 de 2–3 mots + nom propre en H2/H1 ; aucun verbe, aucun bénéfice.
- Mécanismes (sans reproduire les textes) :
  1. **Oxymore** : luxe toujours accolé à son contraire (simplicité, sauvage, brut).
  2. **Négation-renversement** : pas de télé → des vues ; pas de règles à enfreindre → il n'y en a pas.
  3. **Verbes d'action à l'infinitif** : marcher pieds nus, nager, se perdre, méditer, sauter.
  4. **Hyperbole familière** : « insane » douche, plafonds « as high as the stars », piscine « tangerine dream », référence pop « heaven is a place on earth ».
  5. **Énumération de matières et couleurs** : baby pink, burnt orange, terracotta, micro-ciment, pierre, laiton, lin, plume.
  6. **Adresse directe** : « expect… » répété.
  7. **Nomination** : Kate, Edgar, Eliza, Bruno, Lee, Dan, Laura, Adam, Javiera, Yasmin, Lucy, Marina.
- CTA : BOOK NOW, CHECK AVAILABILITY, SHOW ALL ROOMS, CONTACT, NEWSLETTER, BOOK A TABLE. Impératifs courts sans promesse.
- Champ lexical : agroturismo, finca, farm, 50 garden beds, regenerative, medicinal, cacti, rosemary, mountain goats, sound baths, reiki, jam sessions. Mots d'univers : wild, alchemy, freedom, amigos, corazón (nom commun : « the world of Corazón »).
- Specs uniquement sur la page chambre (13 px) et le moteur.

**Interprétation**

- Ton d'un ami qui invite, pas d'un hôtel qui accueille. Le luxe est dit par **soustraction** et par **matière**, jamais par ses codes (spa, butler).
- La prestation devient expérience par le verbe et la couleur : la piscine n'est pas « 15 m chauffée » mais un rêve tangerine avec hamacs teints à la main.
- Limites : rien sur les conditions (petit-déjeuner, transferts, enfants), aucune langue locale, aucune réassurance ; 12 chambres listées vs « 15-room ».

**Enseignements réutilisables**

- Écrire le luxe par ce qu'il n'y a pas et par ce qu'on touche.
- Surtitre + nom propre suffit comme titre si le paragraphe suit.
- Nommer l'équipe remplace une section « à propos » impersonnelle.

---

## 11. Photographie et vidéo

**Faits observés**

- Home/rooms : 12 vignettes paysage (1,5), intérieurs seulement : 8 lits, 4 coins salon, une fenêtre sur la montagne (La Calma), une salle de bain voûtée (Tramuntana Haze). **Aucune personne.** Lumière naturelle chaude, rasante ; dominantes saumon/terracotta/ocre, trois chambres vert olive. Architecture : voûtes, arcs, poutres, enduits, terre cuite, laine, voiles.
- Baba Royale : 7 portraits 2:3 — rideau et vue, baldaquin, fenêtre sur jardin ; pas de salle de bain dans les captures.
- About : 16 photos 1080×770 (JPG 330–360 Ko) + Porsche rouge devant montagnes et cactus au couchant, parasols de chaume avec transats orange.
- Restaurant : 4 photos cerclées de noir (1,17–1,48) : terrasse à contre-jour, potager aux zinnias magenta, table basse et coussins saumon, lit de jour sous feuillage (une tête sur un coussin : seule présence humaine du corpus).
- Moteur : 12 photos 1 341–1 653 px du même shooting recadrées en 380×253.
- Vidéo : un iframe Vimeo 16:9 autoplay muted loop, contenu non vérifiable, chunks jusqu'à 4,7 Mo.

**Interprétation**

- Proportion ≈ 90 % lieu / 10 % expérience / 0 % personnes sur le site principal ; la chaleur humaine est portée par le texte.
- Cohérence exceptionnelle : même colorimétrie, même heure, même distance (plans moyens à hauteur d'œil). Les photos tiennent sur le rouge parce qu'elles en contiennent.
- La vidéo est le seul élément vivant d'un site sans mouvement, d'où l'importance de son chargement.
- Manques : vue d'ensemble de la finca, piscine dans la grille, plats, nuit, hiver, gestes de service.

**Shot list pour reproduire ce niveau**

1. 12–15 plans larges de chambre à hauteur d'œil, lumière de fin de journée, un mur d'accent par chambre.
2. Par chambre : un détail textile, un détail architectural, une vue depuis le lit, une salle de bain (matières).
3. 5–8 extérieurs à l'heure dorée : façade, piscine avec mobilier coloré, potager en gros plan, terrasse dressée, allée d'arrivée.
4. 3–5 objets-signature (voiture, tampon, uniformes, vaisselle, cendriers peints).
5. 3 plans avec présence humaine partielle (main, dos, silhouette) pour l'échelle.
6. Une boucle vidéo 15–30 s en 16:9 et 9:16, muette, plans fixes de 3–4 s, H.264 < 3 Mo + poster JPG.
7. Étalonnage commun : chaud, noirs relevés, rouges contenus pour dialoguer avec le fond.

---

## 12. Mobile

**Faits observés** (390×844)

- Header 128 px, logo centré, burger 48×41 (home) / 48×50 (chambre) sans libellé.
- Hero : BOOK NOW 360×78 à y = 160, iframe 360×203 à y = 318, puis ~320 px de rouge vide avant « WELCOME TO THE » (y ≈ 760).
- Titres non réduits : H2 48 px sur 2 lignes, H1 56 px sur 2 lignes ; corps 18/27 sur 360 px.
- Document 6 060 px ; intro 1 442 px ; 12 cartes 360×233–240 sur 3 262 px, étiquettes conservées.
- Menu : overlay brun, 6 liens ~40 px, filets 1 px, croix 48 px, `overflow: hidden`, pas de BOOK NOW.
- Tailles : BOOK NOW 360×78 ; SHOW ALL ROOMS 232×55 ; liens footer 82–147×**21 px** ; dots Swiper ~8 px ; flèches fines sur les photos.
- Vitesse : 50 requêtes, 5,3 Mo (4,1 Mo Vimeo), TTFB 891 ms, FCP 1 080 ms, load 2 037 ms ; chambre : 15 requêtes, 350 Ko, FCP 1 228 ms.
- 0 `srcset` : vignettes 622–640 px adéquates par hasard sur 780 px physiques ; About 1080–2400 px surdimensionnées.
- Restaurant mobile : « no burger found », `user-scalable=no`, 102 requêtes, 7,1 Mo, load 4 330 ms. Moteur mobile non capturé.
- Contraste ≈3,2:1 conservé.

**Interprétation**

- Réduction fidèle du desktop. Le BOOK NOW de 78 px pleine largeur est le meilleur élément mobile ; il est unique et hors du menu.
- Problèmes : vide au-dessus de la ligne de flottaison, titres qui cassent, 1 442 px de capitales, liens footer trop petits, aucun retour au CTA sur 6 060 px.
- Le sous-menu chambres existe dans le DOM mobile mais n'apparaît sur aucune capture (hypothèse : dépliable non déclenché).
- Vitesse perçue bonne hors vidéo ; la vidéo = 78 % du transfert mobile.

**Enseignements réutilisables**

- Reprendre le CTA pleine largeur 78 px, le rendre sticky après scroll ou le répéter dans le menu.
- `clamp()` sur H1/H2 (56 → ~36 px), `srcset` sur les images > 1 000 px, facade click-to-play pour la vidéo.

---

## 13. Performance, accessibilité, SEO

**Faits observés — performance**

| Page | Requêtes | Transfert | TTFB | FCP | DCL | Load |
|---|---|---|---|---|---|---|
| home desktop | 115 | 42,4 Mo (xhr Vimeo 39,8 ; images 1,28 ; scripts 1,1) | 808 ms | 992 ms | 1 305 ms | 2 508 ms |
| home mobile | 50 | 5,3 Mo (xhr 4,1) | 891 | 1 080 | 1 392 | 2 037 |
| rooms | 40 | 1,27 Mo (images 987 Ko) | 1 133 | 1 324 | 1 559 | 1 602 |
| room-detail | 34 | 858 Ko (images 584 Ko) | 1 144 | 1 344 | 1 550 | 1 570 |
| room-detail mobile | 15 | 350 Ko | 983 | 1 228 | 1 524 | 1 524 |
| about | 36 | 7,46 Mo (images 7,2 ; la-piscina-3.webp 829 Ko) | 1 020 | 1 216 | 1 485 | 1 558 |
| contact | 16 | 334 Ko | 847 | 1 100 | 1 374 | 1 374 |
| restaurant (WP) | 285 | 19,5 Mo (146 scripts 12,1 ; 72 CSS 2,9) | 761 | 1 224 | 1 732 | 4 015 |
| engine (eZee) | 100 | 44,2 Mo (28 images 39,6) | 855 | 2 188 | 1 017 | 1 383 |

- Vidéo : 8 requêtes `vod-adaptive-ak.vimeocdn.com`, chunks de 75 Ko à 4 710 Ko (4 chunks > 4 Mo) ; tiers : 21 vimeocdn, 13 arclight.vimeo.com, 7 lensflare.vimeo.com (télémétrie), GTM/GA.
- Lazy : home 0/14, chambre 7/9, about 16/18. 0 `srcset`. Formats : webp 11/14 (home), JPG ×16 (About), SVG icônes.
- CSS propre 33,9 Ko, 1 keyframe, `willChange: 0` ; scripts propres : `toggle.js` + Swiper 9 CDN. Police 34 Ko, `font-display` non détecté (hypothèse : défaut). Iframe à dimensions fixes → pas de décalage attendu.
- TTFB 808–1 144 ms sur toutes les pages : le serveur est le premier facteur de lenteur.

**Faits observés — accessibilité**

- `focusOutlineNone` : 45 (home), 44 (rooms), 34 (chambre), 32 (about), sans focus de remplacement mesuré.
- `skipLink: false` ; landmarks main 1, nav 1, footer 1, **header 0** (`div`).
- Burger sans nom, logo sans texte, iframe Vimeo sans `title`. Alt : 12/14 vides sur la home, « Baba Royale » ×7, « About » ×16.
- Contrastes estimés : `#371810` sur `#d0342c` ≈ **3,2:1** — échoue AA pour le corps 18 px (4,5:1), passe « large text » ≥ 24 px (3:1). Rouge sur brun ≈ 3,2:1 (BOOK NOW 24 px passe, étiquettes 15 px échouent). Beige sur rouge ≈ 3,7:1 ; beige sur brun ≈ 12:1 (le hover est le plus lisible de la palette). `#a2261f` sur brun ≈ 2,2:1.
- Capitales par CSS (DOM en casse mixte) : lecture d'écran normale. Aucun formulaire sur le site ; moteur : `ariaHidden: 175`, `tabindexNeg: 3`, `focusOutlineNone: 87`. Restaurant : `user-scalable=no`.
- Reduced motion : règle globale `*, *::before, *::after { animation-duration: .01ms !important; transition-duration: .01ms !important; scroll-behavior: auto !important }` ; capture identique, 201 transitions neutralisées.

**Faits observés — SEO**

- Titles « Hotel Corazón – Home / Rooms / Baba Royale / About / Contact » (patron cohérent, « Home » sans destination). Meta description identique sur home, rooms, contact ; spécifique sur about et chambre.
- H1 : **0 sur home, rooms, about** ; 1 sur chambre et contact. Hiérarchie H4 → H2 sans H1 ni H3.
- `canonical` None, `hreflang` [], `jsonld` [] sur le site principal ; `robots: index, follow` ; `og:image: default.png?fit=1200%2C628` (relatif — hypothèse : générique ou cassé). Le restaurant, lui, a canonical et JSON-LD `Restaurant`/`Organization`.
- Indexable : 207 / 40 / 145 / 428 / 67 mots. Une seule langue. `generator` absent (hypothèse Kirby d'après `/media/pages/about/<hash>-<timestamp>/`, non prouvée).

**Interprétation**

- Front **léger par nature** (33,9 Ko CSS, une police, 858 Ko par chambre) mais **plombé par deux tiers** : Vimeo (jusqu'à 39,8 Mo) et eZee (39,6 Mo d'images). Le TTFB > 800 ms relève de l'hébergement.
- La DA bichrome se paie en contraste ; outline supprimé et burger sans nom se corrigent en quelques lignes.
- SEO minimal (0 H1, 0 schema, descriptions dupliquées, 207 mots) face à des concurrents de Deià/Sóller bien référencés ; les pages chambre sont les mieux armées.

**Enseignements réutilisables**

- Vérifier le contraste dès le choix des deux couleurs d'une DA bichrome (un brun plus sombre suffirait).
- Remplacer l'iframe Vimeo par un `<video>` < 3 Mo avec poster, ou une facade au clic.
- H1, canonical, JSON-LD `LodgingBusiness`, description unique par page : une journée de chantier.

---

## 14. Conclusion

**15 meilleurs éléments**

1. Fond rouge `#d0342c` texturé sur 100 % du site : identité reconnue en une seconde.
2. Police unique Klinsman en capitales, échelle 56/48/24/18/15.
3. Logo lettré centré dans un menu 3 + 3 : composition d'affiche.
4. Bandeau BOOK NOW 1020×78 / 360×78 inversé brun/rouge sous le header.
5. Photos accordées au fond (saumon, terracotta, olive).
6. Étiquettes brunes chevauchant les cartes, texte rouge.
7. Noms propres de chambres avec catégorie en surtitre 15 px.
8. Copywriting par soustraction et par matière.
9. Page chambre : galerie → nom → récit → CTA → specs 13 px Soerip sur deux colonnes.
10. Pré-filtrage du moteur par `roomtypeunkid` depuis la page chambre.
11. Titres bilingues EN/ES et personnes nommées sur About.
12. Soulignement de menu animé depuis le centre.
13. Tampon « KM 56.7 HOTEL.CORAZON » en footer.
14. Menu mobile overlay brun, 6 entrées ~40 px, filets rouges.
15. Front propre : main.css 33,9 Ko, police 34 Ko, chambre 858 Ko, reduced-motion global.

**5 faiblesses / limites**

1. Aucun CTA persistant : absent du header, du menu mobile, du footer et de rooms/about/contact.
2. Contraste ≈3,2:1 sur tout le corps 18 px ; outline clavier supprimé sur 32–45 éléments par page.
3. Moteur en rupture (Inter, gris, 44,2 Mo) affichant 8 « Sold Out » sur 12 à cause d'un minimum 2 nuits non annoncé.
4. SEO minimal : 0 H1 sur trois pages, 0 canonical, 0 JSON-LD, descriptions dupliquées, og:image générique.
5. Vidéo Vimeo lourde (chunks 4,7 Mo, jusqu'à 39,8 Mo) et non vérifiable ; 4 technologies, 3 menus.

**10 principes réutilisables**

1. Un geste radical tenu sur toutes les pages vaut plus que dix effets.
2. Accorder la colorimétrie des photos au fond de marque.
3. CTA principal sous le header, pleine largeur, 78 px — puis persistant.
4. Nommer chambres, gens et objets ; reléguer les specs en petite police secondaire.
5. Écrire le luxe par soustraction et par matière, avec des verbes.
6. Surtitre 2–3 mots + nom propre ; paragraphes ≤ 720 px.
7. Passer le contexte (chambre, dates) dans l'URL du moteur.
8. Annoncer sur le site les conditions du moteur (minimum, petit-déjeuner, annulation, prix).
9. Réserver une couleur secondaire aux états hover/focus.
10. Garder le front léger et surveiller que les tiers ne multiplient pas le poids par 50.

**Éléments propres à la marque à ne PAS copier**

- Le rouge `#d0342c` en aplat total et le brun `#371810` ; le lettrage du logo et Klinsman en capitales intégrales.
- Le tampon « KM 56.7 », le palmier en cartouche, la créature ailée.
- Le ton « ride or dies / amigos », la punchline luxe/sauvage et l'oxymore tel qu'il est formulé.
- Le bandeau BOOK NOW brun/rouge tel quel (reprendre le principe, pas les couleurs).

**Notes /10**

| Critère | Note | Justification |
|---|---|---|
| Branding | **8,5** | Bichromie + police unique tenues sur 5 pages et reprises sur le restaurant ; mécanismes d'écriture identifiables ; icônes propres. Perd sur 12/15 chambres et 3 menus différents. |
| Direction artistique | **8** | 4 couleurs CSS, 5 tailles, grille 1020 px, photos accordées, étiquettes signées. Perd sur la monotonie (aucun changement de fond en 4 887 px), titres non réduits en mobile, contraste 3,2:1. |
| Animations | **3,5** | Trois micro-interactions maison + Swiper/Vimeo ; 0 attribut d'animation, 0 transform au scroll, 0 transition de page, 0 lightbox. Reduced-motion respecté. |
| UX | **6** | 6 entrées, grille dès la home, page chambre bien ordonnée, menu mobile lisible. Mais pas de CTA persistant ni de téléphone, liens footer 21 px, 320 px de vide mobile, 3 domaines. |
| Conversion | **5** | BOOK NOW géant et pré-filtrage ; mais 0 avis, 0 condition, 0 prix sur le site, aucun rappel, moteur en rupture avec 8 « Sold Out » par défaut et 44,2 Mo. |
| Mobile | **6** | CTA 360×78, FCP 1 080 ms, chambre 350 Ko, overlay clair. Mais H2 48/H1 56 px non réduits, 1 442 px de capitales, 6 060 px sans retour au CTA, 0 srcset, restaurant sans burger et `user-scalable=no`. |

**Note globale : 6 / 10.** Hotel Corazón est un cas rare de site hôtelier dont l'identité tient dans deux couleurs et une police, servies sans faille par les photos et le copywriting : sur branding et DA, il est dans le haut du corpus. Mais le site s'arrête où commence la conversion : aucun mouvement, aucune réassurance, un moteur qui contredit la promesse (gris, lourd, « Sold Out » par défaut), et une base SEO/a11y minimale (0 H1, 3,2:1, outline supprimé). La moyenne des six notes (6,2) traduit cet écart entre une marque aboutie et un parcours inachevé.

---

## Observations clés à conserver pour la phase comparative

- Fond unique `#d0342c` texturé sur 100 % des pages (148 fonds rouges sur la home, 0 section blanche), texte `#371810`, contraste ≈3,2:1 sur le corps 18 px — échec AA sur tout le texte courant par choix de marque.
- Une police (Klinsman 34 Ko, graisse 400, capitales par CSS) + Soerip 13 px pour les listes chambre ; échelle 56/48/24/18/15 identique desktop/mobile, 0 règle fluide.
- Header fixe 128 px (desktop = mobile), logo centré, menu 3 + 3, inversion brun/rouge observée au scroll (mécanisme non prouvé) ; hover = soulignement `::after` 69 px depuis le centre.
- CTA BOOK NOW = bandeau 1020×78 / 360×78 à y = 160, brun/rouge 24 px, lien direct eZee ; absent du header, du menu mobile, du footer et de rooms/about/contact.
- Home : 4 sections, 4 887 px desktop / 6 060 mobile ; intro texte 1 043 / 1 442 px sans image ; grille 2×6 cartes 500×330 (1,5) ; 0 H1 ; 207 mots.
- Hero iframe Vimeo 1020×574 autoplay/loop/muted, « Player error » en headless ; chunks jusqu'à 4,7 Mo, 39,8 Mo de xhr sur la session desktop, 5,3 Mo au total en mobile.
- 0 animation de scroll (0 attribut, 0 transform, 0 sticky) ; micro-interactions : brightness(0.8) 0.5 s, border-bottom 0.3 s, burger 0.15 s linear ; Swiper 9 ; reduced-motion = kill-switch global.
- Baba Royale : 7 photos portrait 2:3 (427×640) une à la fois, H1 56 px, récit 60 mots, BOOK NOW à y = 1 296 (1 370 mobile) avec `roomtypeunkid`, specs 13 px Soerip (45 m², lit orienté est) ; 0 prix, 0 capacité, 0 lightbox, 0 cross-sell.
- Moteur eZee : Inter, `#f3f6f9`, sticky 84 px, 12 offres de 427,27 à 1 654,55 €/nuit +≈10 % taxes, minimum 2 nuits → 8/12 « Sold Out » avec les dates par défaut ; 100 requêtes, 44,2 Mo dont 39,6 Mo d'images, FCP 2 188 ms.
- Écosystème éclaté : site statique (main.css 33,9 Ko) / restaurant WordPress-Elementor 4.2.3 (285 requêtes, 19,5 Mo, 146 scripts, Zenchef, `user-scalable=no`, H3 caché Raleway `#1bb0ce`) / events Odoo / shop ; 3 menus.
- Performance propre : TTFB 808–1 144 ms partout, FCP 992–1 344 ms, chambre 858 Ko / 350 Ko mobile, About 7,46 Mo (16 JPG 1080 px + 1 de 2400 px) ; 0 `srcset` ; lazy 0/14, 7/9, 16/18.
- Accessibilité : `focusOutlineNone` 32–45 par page, 0 skip link, header en `div`, burger et logo sans nom, iframe sans title, 12/14 alt vides sur la home.
- SEO : 0 H1 sur home/rooms/about, 0 canonical, 0 hreflang, 0 JSON-LD (le restaurant en a), description identique sur 3 pages, og:image `default.png` relatif, anglais seul.
- Copywriting : oxymore luxe/simplicité, négation-renversement, verbes d'action, hyperboles familières, 11 personnes nommées ; 0 avis, 0 condition, 0 téléphone ; 12 chambres listées vs « 15-room ».
- Photos : 100 % intérieurs sans personne sur la home, lumière chaude accordée au rouge, 3 chambres vert olive ; extérieurs (Porsche, parasols de chaume, potager) seulement sur About et restaurant.
