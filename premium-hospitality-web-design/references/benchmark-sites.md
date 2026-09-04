# Benchmark — quinze sites d'hébergement et de voyage premium analysés

> Synthèse des audits réalisés le **2026-09-04** (série 1 : cinq hôtels et une collection « quiet luxury » ; série 2 : dix références choisies pour diversifier les mécanismes : couleur, animation GSAP, communauté, groupes, expédition, croisière, slow luxury, marque de design, voyage sur mesure) (Chromium headless 1440×900 et 390×844 via Playwright, captures desktop/mobile, sous-pages, flux d'interaction, moteurs ouverts sans validation). Les fiches complètes (14 rubriques, notes justifiées) sont dans `research/phase-1-audits/` du dépôt ; la matrice comparative dans `research/phase-2-comparative.md`. Ce fichier retient, pour chaque site, les faits utiles, l'interprétation et les enseignements réutilisables. Ne jamais copier les identités décrites : elles servent à comprendre des mécanismes.

Limites communes : lecture des vidéos autoplay non vérifiable en headless (attributs seuls) ; transitions de page non testées ; Lighthouse non disponible (mesures Performance API et réseau seulement) ; moteur Marriott inaccessible aux automates ; Borgo Egnazia protégé par un anti-bot (certaines pages capturées uniquement en mobile).

## Notes attribuées (fiches Phase 1)

| Site | Branding | Direction artistique | Animations | UX | Conversion | Mobile | Globale |
|---|---|---|---|---|---|---|---|
| FORESTIS Dolomites | 9 | 9 | 5 | 6 | 5 | 6 | **6,7** |
| Hotel Corazón | 8,5 | 8 | 3,5 | 6 | 5 | 6 | **6,0** |
| Borgo Egnazia | 8 | 7 | 4 | 5 | 5 | 4 | **5,5** |
| The Seagate | 8 | 8 | 3 | 6 | 4 | 5 | **5,7** |
| Le Collectionist | 8 | 7,5 | 5 | 7 | 7,5 | 6,5 | **7,0** |

Lecture : les hôtels dominent en branding et direction artistique, la plateforme domine en UX et conversion ; aucun site n'atteint 6 en animations (pas de signature de mouvement dans le secteur) ; le mobile reste le maillon faible partout.

---

## 1. FORESTIS Dolomites — https://www.forestis.it/en/

**Pages étudiées** : accueil, Hideaway, Suites, Tower Suite, Villa, Spa, Forest Cuisine, Experiences, Contact & Arrival, page Request, moteur SynXis ; mobile pour accueil, suites, suite, villa.

**Faits**
- Système : fond unique #f2f1eb, texte #333333 (≈ 11:1), une police (Brandon Text Light 400, un seul fichier woff), échelle 40 / 30 / 26 / 20 px (30 / 22 / 22 / 18 mobile), interlettrage 1,5 → 0,75 px, rayon 0, zéro `<button>` (tous les CTA sont des liens texte de 25–27 px de haut).
- Home : hero image fixe 1920×1080 (aucune balise vidéo sur 12 pages malgré video.js et dash.js chargés), titre de 4 mots, « Menu / Request / Book » ; 8 427 px pour 261 mots ; alternance stricte image → titre → paragraphe (713 px) → lien « Discover more » ; mosaïques sur 5 ratios ; citation des hôtes en 30 px ; première mention d'hébergement à 3 003 px ; 0 CTA de réservation dans le corps.
- Navigation : « Menu » ouvre un panneau fixe de 224 px (9 entrées, la première est « Hideaway » = le lieu et les hôtes) ; mobile : barre basse fixe 390×50 (téléphone / e-mail / localisation) sans « Book ».
- Conversion : « Request » → formulaire interne de 11 champs (sans enfants) ; « Book » → SynXis en nouvel onglet, rethématisé (fond crème, Brandon, badges) ; prix uniquement dans SynXis (chambre 35 m² 1 300 € B&B, acompte 30 %, annulation 50 % à 29–11 j) et sur la villa (« from € 25,000 a night ») ; 0 avis, 0 bénéfice direct ; labels footer (14+, SLH, Odles Lodge, Michelin 2024, YERA).
- Page suite : titre → carrousel 5 images → ligne « 55 m² – 2 persons – 1 bedroom » → 147 mots factuels ; 0 prix, 0 CTA dans le corps, 0 suggestion.
- Mouvement : fadeInUp 1 s, hover opacité 0,25 s, une transition de 6 s sur le hero (hypothèse : zoom) ; 0 règle reduced motion ; scroll-snap et onepage-scroll déclarés sans effet.
- Perf / a11y / SEO : 171 requêtes, 8,4 Mo dont 6,5 Mo de scripts (tiers : GTM, Bing, Facebook, Cookiebot, Maps sur toutes les pages) ; Villa load 12,8 s ; 86–116 éléments sans focus ; 0 landmark ; zoom bloqué ; 2 H1 sur la home ; hreflang 4 langues ; 0 JSON-LD.

**Interprétation** : la sensation « haut de gamme » vient du système minimal (2 couleurs, 1 police, rayon 0), du vide et de la photographie de matières ; le site vend une retraite, pas des nuits, et s'arrête avant la vente. Le luxe se dit par soustraction (« only », « exclusively »), jamais par l'adjectif.

**Enseignements réutilisables** : un système à deux couleurs et une police tenu partout ; le menu qui commence par le lieu ; la ligne de faits sous le nom ; la citation des hôtes signée ; le moteur rethématisé ; la barre contact mobile. À corriger dans un projet : offre plus tôt, prix sur les fiches, un CTA principal en bouton, preuve sociale, reduced motion, scripts tiers.

**À ne pas copier** : Brandon Text, le crème #f2f1eb, la mosaïque d'herbier, « Peace as a new luxury », le logo à la flèche.

---

## 2. Hotel Corazón — https://www.hotelcorazon.com/

**Pages étudiées** : accueil, Rooms, Baba Royale, About, Contact, restaurant (sous-site WordPress), moteur eZee ; mobile pour accueil, chambre, restaurant.

**Faits**
- Système : fond rouge #d0342c texturé sur 100 % des pages, texte brun #371810 (contraste ≈ 3,2:1, échec AA assumé), beige #eadcc7 au hover ; une police display (Klinsman, 34 Ko) en capitales par CSS + Soerip 13 px pour les listes ; échelle 56 / 48 / 24 / 18 / 15 identique desktop et mobile ; rayon 0 ; header fixe 128 px avec logo centré et menu 3 + 3.
- Home (4 sections, 4 887 px, 207 mots) : bandeau « BOOK NOW » 1 020×78 (360×78 mobile) placé avant tout contenu → vidéo Vimeo autoplay loop muted dans un cadre 1 020×574 (« Player error » en headless) → manifeste en capitales (1 043 px de texte : gestes, « no TVs, views », « luxury but wild ») → grille 2×6 de chambres (500×330, noms propres) → footer.
- Micro-interactions : soulignement des liens de menu par `::after` de 69 px depuis le centre (0,3 s), cartes `brightness(0.8)` (0,5 s), inversion brun/rouge du header au scroll (mécanisme non prouvé) ; 0 animation de scroll ; règle reduced motion globale.
- Page chambre : galerie portrait 2:3 (427×640) une image à la fois → sur-titre « Superior double room » → nom 56 px → récit de 60 mots → BOOK NOW pré-filtré (`roomtypeunkid`) → « Features / Amenities » en 13 px → blason → « Show all rooms » ; 0 prix, 0 capacité, 0 lightbox, 0 suggestion.
- Conversion : moteur eZee (Inter, gris, 44 Mo, 8/12 chambres « Sold Out » par défaut à cause d'un minimum de 2 nuits non annoncé) ; aucun CTA persistant (ni header, ni footer) ; 0 avis, 0 condition, 0 téléphone ; écosystème éclaté (restaurant WordPress/Elementor, événements Odoo, boutique).
- Perf / a11y / SEO : front très léger (main.css 33,9 Ko, page chambre 858 Ko) mais 39,8 Mo de segments Vimeo ; 0 srcset ; 32–45 éléments sans focus ; 0 H1 sur home/rooms/about ; 0 canonical ; anglais seul.

**Interprétation** : la marque tient dans deux couleurs, une police et un ton ; les photos sont étalonnées pour le rouge, ce qui rend l'ensemble indissociable. Le site est un manifeste, pas un outil de vente : le bandeau géant compense l'absence de tout le reste.

**Enseignements réutilisables** : le manifeste par gestes et négations ; les noms propres de chambres ; le CTA pré-filtré depuis la fiche ; l'ordre émotion → action → faits sur la page chambre ; le reduced motion global comme filet ; la légèreté du front. À corriger : contraste, prix, CTA persistant, preuve, moteur hors charte, capitales sur mobile, domaines multiples.

**À ne pas copier** : le rouge #d0342c, Klinsman, les blasons, « luxury but wild », « KM 56.7 ».

---

## 3. Borgo Egnazia — https://www.borgoegnazia.com/

**Pages étudiées** : accueil, Rooms, La Corte (mobile), Your Experience, Food & Drink, Events & Offers, Awards, Vair Spa, Overview del Borgo, Contacts, moteur propriétaire ; mobile pour accueil, La Corte, moteur.

**Faits**
- Entrée : préloader gris #888b8d avec logo → vidéo fixe plein écran (2024_overview.mp4, 18,5 Mo transférés, autoplay muted, sans loop, poster ni playsinline) avec « SKIP » 102×41 → grille 2×2 de tuiles plein écran sous voile brun #2b241e à 60 % (« LOOK INSIDE / DREAM », « YOUR BORGO / EXPERIENCE », « BOTTEGA EGNAZIA », « EVENTS & OFFERS ») ; 94 mots ; 0 H1 ; docHeight 1 016 px.
- Système : Optima auto-hébergée, H2 25 px capitales interlettrage 3 px, corps 14/21, textes de 9 px en footer, paragraphes beige à 2,47–3,43:1 ; Bootstrap 4.1.3 + Bootswatch + jQuery + animate.css + WOW + fancybox + datepicker ; header fixe 64 px transparent avec burger ; onglet vertical « BOOK » fixe 46×140 ; signature « Nowhere Else » sous le logo, répétée sur préloader, cookies, footer et moteur.
- Menu : 20 entrées dont 11 externes (Bottega, Egnazia, LHW Leaders Club, Associazione Clara, Media Hub, Travel Trade, sustainability…) ; non ouvrable par script.
- Mouvement : `zoominimg 40s ease` sur les tuiles (seule animation d'auteur) ; WOW fadeIn 1 s ; 0 hover sur tuiles ; 5 vidéos de tuiles en boucle non muettes (1,1–3,95 Mo) ; reduced motion inopérant.
- Conversion : onglet BOOK → modale brune (check-in / check-out / adultes / enfants) → booking.borgoegnazia.com en nouvel onglet, à la charte, avec liste des chambres, « Last room left », tarifs Advance purchase 880 € / Best available 980 € (annulation J-7) / demi-pension, jusqu'à 3 780 € « avg price per night » ; aucun prix, surface ni capacité sur le site ; 4 clics jusqu'à une chambre ; page Accolades de 754 mots (Michelin, 50 Best, T+L, CN Traveler, GSTC) ; 0 avis.
- Perf / a11y / SEO : home 179 requêtes / 28,4 Mo ; Offers 30,1 Mo (JPEG de 6,3 et 5,5 Mo) ; rooms load 13,2 s ; 0 lazy, 0 srcset ; 42–47 éléments sans focus ; alt manquants ; formulaire de 7 champs sans label ; zoom bloqué ; title identique partout ; description vide ; JSON-LD WebSite seul.

**Interprétation** : l'univers (village, fête, artisanat, nuit) est vendu par la vidéo et les tuiles ; le moteur vend la chambre avec une vraie richesse (conditions, prix moyen, urgence) ; entre les deux, il manque la page qui rend l'offre concrète. Le site est une expérience cinématographique portée par une stack de 2018.

**Enseignements réutilisables** : la signature de marque partout (y compris le moteur) ; l'onglet de réservation persistant ; le moteur à la charte avec conditions explicites ; le zoom lent de 40 s comme échelle de mouvement d'ambiance ; les tuiles-univers pour un resort à univers multiples ; la page Accolades. À corriger : intro bloquante, poids, menu-annuaire, information absente sur les chambres, contrastes, textes de 9 px, mobile.

**À ne pas copier** : le logo « quatre dalles », « Nowhere Else », Optima, le voile brun 60 %, les noms « Magnifica / Bella / Splendida ».

---

## 4. The Seagate — https://www.seagatedelray.com/

**Pages étudiées** : accueil, Rooms & Suites (page unique), Dining, Events & Experiences, Wellness, About, Membership, Contact, page Marriott ; mobile pour accueil, rooms, membership.

**Faits**
- Système : fond #f2f1ec, encre et boutons #203a4d (≈ 10,5:1), footer #163041 ; une police (Owners, 5 fichiers .otf, 788 Ko) ; H1 de sections 48 px capitales interlettrage 13 px graisse 300 (32 px / 7 px mobile), hero 34 px bas de casse interlettrage 4 px, corps 16/22,4 ; rayon 0 ; bouton plein « RESERVE » 119×40 (12 px capitales interlettrage 3 px) ; header fixe 112 px (97 mobile) ; widget fixe 248×242 à 70 % d'opacité à droite (desktop uniquement ; barre 358×32 sur mobile).
- Home (6 944 px, 5 H1) : hero vidéo 864 px sans poster (13,9 Mo desktop + 10 Mo mobile, les deux chargées sur les deux breakpoints), titre publicitaire blanc illisible tant que la vidéo n'est pas rendue ; puis motif répété 5 fois « titre 48 px / 2 lignes / grille » (Stay avec 4 coquillages packshot 305×305, Where taste meets table, Amid green and blue, Private events, Balance from inside out) ; un seul changement de fond (footer).
- Rooms : page unique, 4 catégories (coquillage + photo + binôme émotionnel « Rarity & ceremony », « Serenity & tactility », « Opening to the horizon ») + « Room types » repliant 13 types avec lits/capacité ; 8 amenities communes en H4 12 px ; 0 prix, 0 galerie, 0 surface ; « Reserve your stay » en lien 12 px.
- Conversion : RESERVE → marriott.com (nouvel onglet, identité Marriott, accès refusé aux automates) ; Bourbon Steak → SevenRooms ; membership → sous-domaine avec `?preview=yes` ; 0 avis, 0 offre, 0 prix, 0 argument direct.
- Mouvement : aucune animation de scroll, 0 cubic-bezier, 60 transitions 0,3 s, hover #203a4d → #333638 imperceptible ; vidéos sans poster ni pause ; 1 règle reduced motion (formulaire).
- Perf / a11y / SEO : 278 requêtes, 164,6 Mo transférés (media 138 Mo desktop / 70,7 Mo mobile) ; 0 lazy ; jpg jusqu'à 3,27 Mo ; 73 scripts (Bing, Google Ads, Floodlight, Pinterest, Meta) ; `main` absent ; 54–81 sans focus ; CONTACT invisible dans le menu desktop à 900 px ; JSON-LD Hotel ; og:image absent ; canonical sans www.

**Interprétation** : un des systèmes bichromes les plus cohérents du panel, une écriture par binômes émotionnels, des icônes photographiques ; mais une vitrine qui délègue toute la vente à Marriott et une dette média qui contredit le calme promis dès le hero.

**Enseignements réutilisables** : les icônes photographiques de catégories ; les binômes émotionnels ; le widget de réservation visible dès le hero ; la barre CTA pleine largeur sous le logo sur mobile ; la version vidéo mobile dédiée (principe) ; le lexique unique sans « luxury ». À corriger : poster et poids vidéo, chargement des deux vidéos, page par catégorie, prix, preuve, moteur hors charte, landmarks, H1 multiples.

**À ne pas copier** : les coquillages, Owners, le marine #203a4d, « Coastal Luxe Style Meets Private Club Living ».

---

## 5. Le Collectionist — https://www.lecollectionist.com/fr/

**Pages étudiées** : accueil, destination Ibiza, Villa Blue (fiche), Collections, S'inspirer, Conciergerie, Contact, pages thématiques ; mobile pour accueil, destination, villa, collections, s'inspirer ; flux recherche et CTA villa.

**Faits**
- Système : blanc / #f7f7f7 / #202020 / #757575, sans couleur d'accent ; trio Brown (sans, corps 16/22,4, titres capitales interlettrage 1 px) + GT Alpina Light (serif d'intro) + Ayer Medium (display 60 px desktop / 48 mobile, 4 occurrences par page) ; échelle 60 / 36 / 32 / 24 / 20 / 18 / 16 / 14 / 12 / 10 ; rayon 0 sur boutons, champs et cartes, icônes rondes 32–40 px ; boutons 44–52 px de haut, 14 px capitales ; container 1 280 px ; Nuxt + Tailwind (prouvés).
- Home (8 454 px) : hero vidéo de 458 px (51 % du viewport, ≈ 4,3 Mo par requête, sans poster ; image sur mobile) avec « Partagez l'extraordinaire », triptyque, barre de recherche (Destination | Arrivée → Départ | Voyageurs | RECHERCHER) et « S'inspirer » ; puis maisons par onglets saisonniers (3 cartes 4:5 avec lieu) → 3 arguments chiffrés (2 300 maisons, sur-mesure, conciergerie locale) → « Votre hiver commence ici » → collections ◇/◇◇/◇◇◇ (= ménage 1× / 3× / 5× par semaine) avec 6 maisons → « Imaginons vos prochaines vacances » (conseiller) → « La conciergerie autrement » (4 images verticales) → destinations avec nombre de maisons → « Louez votre maison » → presse (Ideat, AD, L'Officiel, Elle, Challenges) → certification Condé Nast → newsletter.
- Fiche villa (2 190 mots) : fil d'Ariane → nom + lieu → « 10 voyageurs · 5 chambres · 5 sdb · 630 m² » → description → collection + avis 4,8/5 → incontournables → chambres avec couchages (lit 200×200) → services inclus / à la carte → prix et disponibilités par semaine (minimum 5 nuits) → mosaïque 1+4 (« voir les 56 photos ») → « Bon à savoir » (4 contraintes réelles) → conseiller avec photo et horaires 7 h–22 h (« Planifier un appel ») → « Leurs souvenirs » → arrivée 16 h / départ 10 h → carte et distances → conditions (FAQ) → 3 villas recommandées avec prix ; encart sticky 488 px : dates, total « 33 160 € / 7 nuits », « Réserver », « Faire une demande », téléphone ; formulaire in-place ; mobile : barre basse 390×95 (prix + dates + deux CTA de 35 px).
- Liste destination : 864 px de résultats + carte Mapbox sticky 100 dvh ; filtres ; favoris ; modale « dates » à l'ouverture.
- Mouvement : AOS ×6–49, hover image scale 1,01 → 1,1 en 0,35 s ease-out, transitions 0,8 s, easing Material ; 0 parallaxe, 0 curseur, 0 sticky narratif ; reduced motion sans effet sur la vidéo.
- Interruptions : cookies Axeptio (696 Ko), modale newsletter au premier scroll desktop, smart banner AppsFlyer 62 px + Google One Tap 144 px sur mobile.
- Perf / a11y / SEO : home 527 requêtes / 21 Mo (scripts 9,8 Mo sur 348 fichiers, 4 gtag) ; liste 896 requêtes / 26 Mo ; FCP 0,6–1,5 s ; `main` absent ; 5–32 boutons sans nom ; 161–180 sans focus ; zoom bloqué ; hreflang fr/en/x-default ; JSON-LD Organization + Accommodation + TouristDestination ; bug de title « de luxe de luxe » sur des URL filtrées.

**Interprétation** : la seule fiche produit complète du panel (faits, prix, conditions, humain, alternatives) et une DA tenue malgré la densité ; la couche marketing et technique (bannières, One Tap, 10 Mo de scripts) contredit le calme que la typographie installe.

**Enseignements réutilisables** : la barre de recherche dans un hero court ; les collections nommées avec inclusions ; le conseiller nommé avec horaires ; la fiche normalisée (ligne de faits, incontournables, couchages, bon à savoir, prix par semaine, total visible, conditions, similaires) ; l'encart sticky à deux voies ; l'image à la place de la vidéo sur mobile ; les pages destination et thématiques SEO. À corriger : interruptions, poids JS, boutons < 44 px, zoom, accessibilité des boutons, menu à trois audiences.

**À ne pas copier** : Ayer / Brown / GT Alpina, les losanges ◇, « Partagez l'extraordinaire », la structure exacte de la home.

---

## 6. Ce que la compétence retient (résumé)

| À reprendre (mécanismes) | Observé chez | À corriger systématiquement | Observé chez |
|---|---|---|---|
| Système 2–3 couleurs / 1–2 polices / rayon 0 tenu partout | F, C, S | Prix absent avant le moteur | F, C, B, S |
| Manifeste par soustraction et gestes | F, C | Preuve sociale absente | F, C, B, S |
| Noms propres et personnes nommées | F, C, L | Vidéo hero lourde sans poster ni pause | C, B, S, L |
| Ligne de faits sous le nom | F, L | Moteur hors charte / nouvel onglet | C, S (F et B partiellement traités) |
| Icônes photographiques et natures mortes | S, F | Accessibilité (focus, landmarks, contrastes, zoom) | tous |
| CTA persistant (onglet, bouton, barre basse) | B, S, L | Scripts tiers > 4 Mo | F, B, S, L |
| Moteur rethématisé avec conditions | F, B | Menu-annuaire ou sous-menu de chambres | B, C |
| Fiche produit complète + conseiller + similaires | L | Interruptions (préloader, bannières, One Tap) | B, L |
| Collections / catégories nommées par sensation | L, S | Capitales et textes < 13 px sur mobile | C, B, L |
| Barre contact mobile / barre prix + CTA | F, L | H1 absents ou multiples, JSON-LD pauvre | F, C, B, S |


---

# Série 2 — dix références « au-delà du quiet luxury »

## Notes attribuées (fiches 06 à 15)

| Site | Modèle | Branding | DA | Animations | UX | Conversion | Mobile | Globale |
|---|---|---|---|---|---|---|---|---|
| Hotel Odisej (Mljet) | hôtel d'île | 7 | 8 | 7 | 6 | 3 | 6 | **6,5** |
| Mas Girbau | maison rurale entière | 8 | 8,5 | 8 | 6,5 | 5,5 | 7 | **7,3** |
| Our Habitas | collection-communauté | 8 | 7 | 5 | 6 | 4,5 | 5,5 | **6,0** |
| Aethos | collection + club + retraites | 9 | 8 | 7 | 6 | 5 | 7 | **7,0** |
| White Desert | expéditions | 9 | 8,5 | 8 | 7 | 8 | 6,5 | **8,0** |
| Explora Journeys | croisières | 7,5 | 7,5 | 5 | 7 | 7,5 | 6,5 | **7,0** |
| Experimental Group | groupe multi-lieux | 9 | 8 | 6 | 7 | 6,5 | 6 | **7,3** |
| Soneva | resorts slow luxury | 8,5 | 8 | 6,5 | 7 | 6,5 | 6,5 | **7,5** |
| Vipp Guesthouses | marque de design qui héberge | 9 | 8 | 4 | 6 | 5 | 6,5 | **7,0** |
| Pelorus Travel | voyage sur mesure | 8 | 7 | 5 | 6 | 6 | 5 | **6,5** |

Lecture : la série 2 est plus forte en animations (Mas Girbau 8, White Desert 8, Odisej 7, Aethos 7) et en conversion pour les offres datées (White Desert 8, Explora 7,5) ; elle est plus lourde (65 à 440 Mo par page) et aussi faible en accessibilité que la série 1.

## 6. Hotel Odisej — https://hotelodisej.com/
**Faits** : palette tri-tonale du paysage (#f7f7ee crème, #5b6647 olive, #03364f bleu nuit, liaison #e3e3c4) tenue sur 6 pages ; PP Woodland 80/88 px (−2,4 px) + DM Sans ; home 14 967 px en 7 chapitres à fonds pleins séparés par des vagues SVG bicolores ; statements de 80 px à remplissage progressif au scroll (deux copies superposées de chaque phrase) ; 67 reveals, 4 parallaxes, 6–22 transforms par palier, sans bibliothèque d'animation ; header 90 px transparent → crème ; pills « Book now » (109×36 olive) et « Online Check-in » (contour) ; chambres en accordéon numéroté 01–05 sur page unique (12 296 px), tags « Sea view / Balcony / Park view », 0 prix, 0 m² ; destination Mljet traitée comme premier produit (citation Time) ; réservation book-secure en nouvel onglet avec dates codées `arrival=2023-04-25` ; 0 avis ; home 84 requêtes / 5,9 Mo, FCP 3,1 s ; 0 H1, 0 hreflang malgré /hr/.
**Interprétation** : la couleur pleine et les phrases géantes portent le récit ; la vente est déléguée à un moteur de groupe non entretenu.
**Enseignements** : chapitrage chromatique, text-fill comme cadence, accordéon-sommaire numéroté, destination avant hôtel. **À ne pas copier** : PP Woodland, le trio crème/olive/bleu nuit, les vagues.

## 7. Mas Girbau — https://www.masgirbau.com/
**Faits** : one-page Webflow de 16 843 px, 13 sections-chapitres (prologue, essence, pierre / feu / bois, services 01–05, entorno, activités) ; GSAP 3.10.4 + ScrollTrigger (24 triggers) + split-type (439 nœuds) + ukiyo (parallaxe) + Swiper/Flickity ; H1 80 px Editor's Note révélé caractère par caractère ; palette #fff8eb / #252b15 / #242c04 / #121602 / #e1e7dd / corail #ff906d (CTA pilule 129×63) ; section « Entorno » épinglée 2 045 px avec 77–85 transforms simultanés puis rideau vers une photo de rivière épinglée ; unité vendue = maison entière (14 personnes, 6 chambres, 10 lits, 30 ha) avec tableau de distribution des lits et 12 inclusions ; 0 prix, onglets saison cachés ; réservation par iframe BookingMood (« Send booking Request » en anglais) ; CTA fixe corail desktop, barre mobile 390×64 ; poids 104,5 Mo (vidéo MP4 22,3 Mo + WebM 18,2 Mo, galerie 56,5 Mo) ; 81 sans focus, 119/121 alt vides, 9 H1.
**Interprétation** : la référence d'animation narrative maîtrisée du panel ; le récit vend la maison mieux que la fiche, mais la vente (prix, conditions, moteur) n'est pas au niveau.
**Enseignements** : rythme chromatique par chapitres, texte scrubbé en section épinglée + rideau, numérotation 01/–06/, CTA persistant sur les deux supports. **À ne pas copier** : Editor's Note, corail #ff906d, arches SVG, monogramme G.

## 8. Our Habitas — https://www.ourhabitas.com/
**Faits** : home = page de marque (7 758 px, 769 mots, 0 chambre, 0 prix, 0 H1) : hero Vimeo 90 vh sans texte ni poster, manifeste « Luxury for the Soul » + six piliers, cartes de lieux nommés par phrase-monde (« Our Home of Play »), itinéraire Mexique, stories, Rise, durabilité, footer par région ; Canela + Arboria + acumin ; header 52 px blur + nav secondaire de 8 entrées par hôtel + tiroir « Select Property » (9 lieux) ; story épinglée 682×700 sur ≈ 2 000 px ; hover 1,05 / 0,6 s ; Barba chargé ; réservation SynXis par hôtel avec devises imposées et dates codées 2023–2024, `nights=4` ; Rooms Bacalar : 3 catégories « Sleeps 2 | King Bed », 12 images Swiper, 145 mots ; Dis-loyalty 35/20/10 % ; 60 % de scènes humaines ; 559 requêtes / 26,5 Mo, CSS 2,3 Mo, load 8,2 s ; ≥ 200 sans focus, `lang` inversé, lien staging.
**Interprétation** : le branding communautaire et promotionnel est cohérent et chaleureux ; l'absence de chemin vers une chambre tarifée en fait une vitrine.
**Enseignements** : manifeste + piliers réutilisés comme filtres, nommage par phrase-monde, possessif « Our », bibliothèque de films filtrable, footer par région, sélecteur de lieu. **À ne pas copier** : « Luxury for the Soul », Canela/Arboria, « Our Home of … ».

## 9. Aethos — https://www.aethos.com/
**Faits** : papier #f9f4ef / charbon #2a2826 / accroches #ac9e91 / accent par lieu (#72818b) / club #1e1d1b ; Amerigo BT capitales 100–120 px + Fakt 10–16 px ; hero et footer en cadre inset 32 px ; slogan « The rules are different here » porté par le H1, l'entrée de menu « Different rules » et un t-shirt ; GSAP 3.12.5 + ScrollTrigger (25) + ScrollSmoother + SplitText (17) + Lottie + clip-path en arche ; 61 reveals ; un seul bloc sombre par page (club, 1 417 px) ; club tarifé publiquement (650 / 1 800 / 2 500 €/an) + portail ; pages hôtel en 11 ancres (header 152 px) sans prix ni capacité ; pop-up promo qui fige le scroll ; moteur hotelchamp same-domain ; 399 requêtes / 38,8 Mo (JPEG drone 3 Mo sur 5 pages), load 6,7–14,9 s ; 124–200 sans focus, 68–144 liens sans nom, 0 reduced motion.
**Interprétation** : branding « nouvelle génération » : attitude, communauté tarifée, journal ; la conversion devient l'adhésion ; la chambre disparaît.
**Enseignements** : manifeste omniprésent, cadre inset, accent couleur par lieu, gabarit unique pour Wellness / Experiences / Retreats, club avec tarifs publics. **À ne pas copier** : Amerigo BT, le slogan, l'arche.

## 10. White Desert — https://white-desert.com/
**Faits** : trois voix typographiques : Oswald pour la donnée (« ANTARCTICA » 256 px, coordonnées, « 05:30 HRS »), Cardinal serif italique pour l'émotion (noms de voyages 42 px), Inter Tight pour l'information ; palette #1f2a44 / orange #ff7e15 (action) / crème #f3f1ec / verre ; home 20 782 px avec séquence horizontale épinglée ≈ 10 000 px (camps → presse → carte de vol), brume épinglée, curseur custom, sans bibliothèque ; prix publics partout avec variantes de camp côte à côte ($75 250 vs $65 000), page /prices en 8 cartes filtrables par saison, « How it works » en 6 étapes (onglet orange fixe) ; itinéraire jour par jour scrubbé en trois colonnes (contexte sticky / étapes / images) avec note météo franche ; /enquire en cartes cliquables (saison, mois, intérêts), promesse 24 h, `?itinerary=` ; preuves IAATO, CarbonNeutral, Global Vision Awards, CN Traveler, T+L, Vogue, scientifique nommé ; 462 requêtes / 43,9 Mo, load 6,4 s ; mobile : chat proactif + cookies + bulle sur 40 % du hero ; 69–106 sans focus, labels absents, 0 reduced motion.
**Interprétation** : la meilleure conversion du panel parce que la transparence (prix, méthode, logistique) fait partie du récit d'expédition.
**Enseignements** : prix comparatifs, « comment ça marche », itinéraire jour par jour, langage cartographique, trois voix typographiques, formulaire en cartes. **À ne pas copier** : Oswald/Cardinal, l'orange, la grille verticale.

## 11. Explora Journeys — https://explorajourneys.com/us/en
**Faits** : hero vidéo + widget « Where to ? / When ? » + bouton or « VIEW 658 JOURNEYS » ; header 132 → 63 px ; sable #f4f2ef / navy #0c2340 (action) / bronze #866d4b ; WT Monarch Nova + SangBleu + Shapiro ; cartes de croisière normalisées (région, carte, ports, dates, navire, nuits, pastille offre, « Per guest, from $6,375 ~~$8,500~~ · $797 per night ») ; 658 résultats, 12 par page ; encadré « All Journeys Include » (10 puces) sur 4 gabarits ; tableau 4 catégories × ≈ 25 bénéfices avec surfaces 35–280 m² ; 2 516 excursions payantes dès 145 $ ; 7 mécaniques d'offres datées ; pages suite sans prix ni CTA ; 0 avis ; Adobe AEM + Dynamic Media ; 366 requêtes / 89 Mo (suites 440 Mo, master mp4 de 82 Mo rechargé) ; 0 H1 sur la home, 37 alt manquants, zoom bloqué, accessiBe ; 45 hreflang.
**Interprétation** : la combinatoire (658 × régions × saisons × navires × suites) est résolue par un outil simple et des cartes complètes ; la marque tient par la palette et le système verbal ; le poids et l'accessibilité sont hors norme.
**Enseignements** : home-moteur à deux champs avec nombre de résultats, cartes de produit daté complètes, inclusions répétées, comparatif de catégories, pages saison comme argumentaires. **À ne pas copier** : WT Monarch Nova, « ocean state of mind ».

## 12. Experimental Group — https://www.experimentalgroup.com/
**Faits** : architecture ombrelle → destination → lieu → service portée par URL, fils d'Ariane 3–4 niveaux, JSON-LD typés et couleur de fond par niveau (#b1beb7 Cotswolds, #3b4b5f Cowley, #d1cfc8 Val d'Isère) ; invariants : Nantes 60–159 px + Linux Biolinum, pilule BOOK NOW 120×37, chapitres 120 px avec astérisque ; header 72 px en `mix-blend-mode: exclusion` ; home : 9 cartes 447×559, carrousel 14 destinations, carte Mapbox épinglée 635×812 avec 70 lieux et légende par type, manifeste ; tiroir « Make a booking » (Rooms / Tables / Wellness / Events) → Namastay overlay avec calendrier de prix (€610–1 190/nuit) ; one-pages de lieu 23 000–25 500 px avec chapitres vides, chambres sans m², capacité ni prix ; 0 avis ; 552 requêtes / 73 Mo (webm + mp4 chargés ensemble) ; 200 sans focus, 0 reduced motion ; hreflang 5 langues.
**Interprétation** : la multiplicité est assumée comme signe de curation ; la hiérarchie est rendue visible par la couleur et le logo ; la fiche produit est le maillon faible.
**Enseignements** : couleur par niveau, carte typologique épinglée, tiroir de réservation à 4 choix, calendrier de prix, moule de titre « impératif + ville + italique ». **À ne pas copier** : Nantes, l'astérisque, la matrice exacte.

## 13. Soneva — https://soneva.com/
**Faits** : palette de matières nommée dans le CSS (linen haze #f4f1e9, blue hour #012531, golden ember #e6b33c) + accent d'action #6d2e1d ; Moulin 300 + Scto Grotesk ; header 97 px → 159 px avec sous-nav de resort ; trois resorts-chapitres avec phrase de positionnement ; signature « Just What Matters. » en H2 de clôture de chaque page dans une image 1440×1800 avec bandeau de réservation épinglé (h = 148) ; 21 villas avec ligne de faits standardisée (« Sleeps 9 Adults (6 Adults 3 Child) • 3 Bedrooms • 1,370 m² »), 4 filtres, comparateur, chips, 7 inclusions, plan et carte téléchargeables ; 0 prix ; « Book » = route hash sans navigation observée (moteur azds en hypothèse) ; WhatsApp, WeChat, directeurs nommés ; Lenis ; révélations 0,45 s cubic-bezier(.33,1,.45,1) sur 551 éléments ; 668 requêtes / 19,2 Mo, FCP 4,2 s, villas load 26,8 s, 11 Mo de tiers ; `user-scalable=no`, 59–200 sans focus.
**Interprétation** : le récit sensoriel et le catalogue à faits coexistent ; la signature de clôture et le bandeau épinglé ferment chaque page sur l'action.
**Enseignements** : catalogue à faits dans un récit, signature de clôture répétée avec bandeau de réservation, palette de matières nommée, collection hiérarchisée en chapitres, hôtes nommés. **À ne pas copier** : « Just What Matters », Moulin, les noms de couleurs.

## 14. Vipp Guesthouses — https://vipp.com/en/world-of-vipp/our-guesthouses
**Faits** : « Guesthouses » au premier niveau du header de la boutique (44 px) ; 15 maisons, 11 pays, filtres d'humeur (Solitude / Tropical / Urban) ; liste de 280 mots à trois énoncés serif sable 43 px (« Not a hotel. Not a showroom… ») ; hero scindé lieu | cuisine, film 29,9 Mo épinglé z −1 recouvert par le contenu ; palette #222325 / #f4f3ec / #d6d0c5 / #804a2e ; Vipp Neue + IvyPresto ; page maison en long-form d'architecture (1 072 mots, architecte nommé et photographié, 160 m², coordonnées GPS en overlay, 6 produits shoppables, stories) ; prix d'appel en clair (« From AUD $970 per night, 2 adults ») puis « Book now » → Lodgify (même onglet) ou Planyo (nouvel onglet) selon la maison ; fiche « Information » en 13–14 accordéons ; 0 CTA sur la liste et le header ; 0 avis ; 10–13 vidéos `preload="auto"` : 65–226 Mo par page ; pop-up Sleeknote fixe ; 0 H1 sur 12 pages, ni hreflang ni JSON-LD ; 7 règles `scroll-timeline`.
**Interprétation** : modèle curateur abouti (la marque raconte et signe, le partenaire vend) ; la boucle boutique ↔ séjour est fermée ; l'exécution technique et la réservation ne suivent pas.
**Enseignements** : catégories d'humeur, énoncé de posture, long-form d'architecture, prix « from » avant le bouton, fiche pratique standardisée, page shoppable. **À ne pas copier** : Vipp Neue/IvyPresto, « Not a hotel… », le hero scindé cuisine.

## 15. Pelorus Travel — https://pelorustravel.com/
**Faits** : triple porte d'entrée destination / type d'expérience / profil du voyageur (mega-menu, home, catalogue de 186 fiches) ; cartes « MAY-OCT • £125,000 PP », filtre budget, budget obligatoire dès 40 000 £ au formulaire (10 champs) ; verbe unique ENQUIRE (orange #f38b00, 117–144×42) fixe sur 16/16 pages, jamais « Book » ; pages process (6 étapes), why (7 raisons), testimonials (~20 citations signées par type de voyage), 9 badges ; campagnes incarnées (4 employés nommés en vidéo, 5 archétypes d'enfants) ; architecture Land / Sea / Air + Foundation, cross-sell yachts ; MFred 96–128 px + Montserrat eyebrow interlettré 40 % + Berlingske ; Alpine.js + Swiper, 48 reveals ; home 2 417 mots, 120,9 Mo (vidéo 21 Mo ×2, images 66,5 Mo, 0 srcset) ; modale cookies jamais fermée + pop-in Sleeknote plein écran mobile ; /enquire sans humain nommé ni délai ; 200 sans focus ; JSON-LD TravelAgency, FAQ.
**Interprétation** : la découverte et la réassurance argumentée sont exemplaires pour le sur mesure ; le poids, les interruptions et le formulaire impersonnel freinent.
**Enseignements** : trois portes d'entrée, auto-qualification par le prix, méthode et raisons numérotées, témoignages signés par type, campagnes avec employés nommés, verbe unique. **À ne pas copier** : MFred, l'orange, « Curious Minds ».

## 16. Ce que la série 2 ajoute à la compétence

| Mécanisme nouveau | Observé chez | Où il est intégré |
|---|---|---|
| Couleur pleine et chapitres comme structure | Odisej, Mas Girbau, Experimental, Aethos | `visual-design-system.md` §1, `homepage-blueprints.md` |
| Display 80–256 px, trios typographiques à rôles | Odisej, White Desert, Aethos, Pelorus, Experimental | `visual-design-system.md` §2–3 |
| Text-fill, split-text, section épinglée + rideau, séquence horizontale | Odisej, Mas Girbau, White Desert, Habitas | `motion-guidelines.md` §2 (niveau signature narrative) |
| Transparence tarifaire (cartes, grilles, prix barrés, « from ») | White Desert, Explora, Pelorus, Vipp, Experimental (moteur) | `ux-booking-conversion.md` §7, `accommodation-pages.md` |
| « Comment ça marche », formulaire en cartes, budget qualifiant | White Desert, Pelorus | `ux-booking-conversion.md` §10, blueprint J |
| Manifeste-produit, piliers, club tarifé, communauté | Habitas, Aethos, Experimental, Soneva | `brand-strategy.md` §8, blueprint I |
| Invariants et marqueurs multi-entités | Experimental, Soneva, Habitas | blueprint I, `visual-design-system.md` §9 |
| Home-moteur à deux champs, cartes de produit daté, inclusions, comparatif | Explora | blueprint K |
| Modèle curateur, page shoppable, prix « from » | Vipp | blueprint L |
| Catalogue à faits dans un récit, signature de clôture + bandeau épinglé | Soneva | `accommodation-pages.md`, `visual-design-system.md` §9.16 |
