# Fiche d'audit — Borgo Egnazia (clé `borgo`)

## 0. En-tête

- **Nom** : Borgo Egnazia — signature « Nowhere Else » (Savelletri di Fasano, Pouilles, Italie)
- **URL d'entrée** : https://www.borgoegnazia.com/
- **Date de l'analyse** : 2026-09-04 (captures 16:43 → 16:48 UTC)
- **Environnement** : Chromium headless, desktop 1440×900 et mobile 390×844 (DPR 2), Playwright.

### Pages étudiées

| Label | URL exacte | Desktop | Mobile |
|---|---|---|---|
| home | https://www.borgoegnazia.com/ | Oui (`home.json`, `home-01/02`, `flow-home-after-skip`, `flow-book-modal`) | JSON = écran anti-bot ; captures utilisables `flow-mobile-home-noloader.png`, `flow-mobile-home-15s.png` |
| rooms | https://www.borgoegnazia.com/rooms/ | Oui (`rooms.json`, `flow-rooms.png`) | Non capturée |
| room-detail (La Corte) | https://www.borgoegnazia.com/rooms/la-corte/ | **Non** (`room-detail.json` = « Robot Challenge Screen », capture = préloader) | Oui (`room-detail-mobile.json` recapturé, `flow-mobile-room-detail.png`) |
| experiences | https://www.borgoegnazia.com/your-experience/ | Oui | Non capturée |
| dining | https://www.borgoegnazia.com/food-and-drink/ | Oui | JSON = écran anti-bot |
| offers | https://www.borgoegnazia.com/events-and-offers/ | Oui | Oui |
| awards | https://www.borgoegnazia.com/awards/ | Oui | Oui |
| spa (Vair Spa) | https://www.borgoegnazia.com/?section=time-for-you&t=sport&rn=vair-spa | Oui | Oui |
| about (Borgo overview) | https://www.borgoegnazia.com/time-for-you/borgo/overview-del-borgo/ | Oui | Oui |
| contact | https://www.borgoegnazia.com/contacts/ | JSON oui ; captures = préloader bloqué | Non capturée |
| moteur | https://booking.borgoegnazia.com/#/hotel/1917/channel/514/language/1/rooms/… | Sonde → 404 (fragment `#/` perdu) | Oui, `flow-mobile-engine.png` (étape chambres/tarifs) |

### Limites de l'observation

- Protection anti-bot (page « Robot Challenge Screen », scripts `d1rozh26tys225.cloudfront.net` ; hypothèse : SiteGround) : plusieurs captures `00/01` et les JSON mobiles de home et dining sont inexploitables et ont été ignorés. La page chambre desktop n'a pas pu être lue : elle est décrite via `rooms.json` + `flow-rooms.png` (liste) et via la version mobile (détail).
- Le préloader (fond `#888b8d` + logo) reste affiché sur les captures `contact`, `experiences-01`, `dining-01`, `room-detail-02` et `room-detail-mobile-02` ; la home mobile n'a été lisible qu'après retrait forcé du préloader.
- Vidéo d'intro : autoplay muted mais « paused » en headless ; lecture réelle, fin de vidéo (non loop) et transition vers la grille non vérifiées.
- Menu hamburger non ouvrable par le script (« menu open failed ») : décrit à partir du DOM (checkbox `openmenu`, 20 liens).
- Hover mesurable uniquement sur les boutons cookies ; les tuiles n'exposent aucun changement de style calculé.
- Moteur ouvert jusqu'à la liste chambres/tarifs sur mobile ; aucune réservation, aucun formulaire validé, étape 2 non vue.
- Lighthouse non disponible ; LCP null ; contrastes calculés à partir des hex du JSON.
- Sur 8 captures (desktop `home-04-reduced-motion`, `offers-01`, `spa-01`, `about-01`, `awards-01` ; mobile `offers/spa/about-mobile-02-full`), le contenu n'occupe que ≈1 085 px sur 1 440 (desktop) ou ≈205 px sur 390 (mobile), bande blanche à droite. Hypothèse : interaction entre le widget iubenda « Notice at collection / Your Privacy Choices » (injecté après fermeture de la bannière) et la grille, ou artefact de capture. Non vérifié en navigateur réel.

---

## 1. Positionnement de marque

**Faits observés**
- Signature « BORGO EGNAZIA / NOWHERE ELSE » intégrée au logo (4 dalles de pierre) et présente sur préloader, header des sous-pages, bannière cookies, footer et moteur. JSON-LD `WebSite` : « Borgo Egnazia - Puglia, Italy | Hotel 5 stelle lusso ». `og:description` (italien) : hôtel 5 étoiles près de la mer, villas, spa, terrains de sport.
- Page overview (328 mots) : « accueil authentique des Pouilles », parcours architectural (arche → La Corte « structure mère » → ruelles et Casette → Piazza → Villas avec piscines et toits de tuf), « nowhere else experiences » racontées par les gens du pays.
- Page Vair Spa : « Vair » = « vrai » en dialecte, « Science of Happiness », « therapist-artists, musicians and local dancers ».
- Menu : 20 entrées dont un écosystème de sous-marques externes (Bottega Egnazia, Egnazia, Foglie Magazine, Associazione Clara, Media Hub, LHW Leaders Club, Sustainability, Voucher, Christmas).
- Awards : 754 mots, 2011→2025 (Michelin 2 clés, World's 50 Best n°63, T+L, Condé Nast, étoile Michelin Due Camini, GSTC, Top Employers). Footer : 7 logos blancs (LE, sceau rond, The Leading Hotels of the World, sceau « Best of the Best » type Virtuoso, 50 Best, GSTC, un logo vertical illisible à 40 px).
- Moteur : 880 € à 3 780 € « avg price per night » (2 adultes, octobre 2026).

**Interprétation**
- Resort de luxe « village reconstitué » vendant une immersion territoriale (tradition, dialecte, matières) plutôt qu'un catalogue de chambres ; promesse centrale = unicité de lieu. Cible : internationaux haut de gamme (EN par défaut), familles (tuile FAMILY), bien-être, mariages/événements, séjours packagés.
- Territoire émotionnel : chaleur dorée, lenteur, fête méridionale. Personnalité : fière, hospitalière, mais institutionnelle (menu-annuaire).
- Différence avec un site générique : entrée par vidéo puis par intentions (« LOOK INSIDE / DREAM », « YOUR BORGO / EXPERIENCE ») et non par « Rooms / Dining / Spa » ; noms italiens conservés.
- Cohérence : forte sur mots et images, faible sur interactions : la mécanique « tuile → DISCOVER » est répétée à chaque niveau et le texte se raréfie (94 mots sur la home, 103 sur rooms).

**Enseignements réutilisables**
- Une signature courte intégrée au logo assure la continuité jusque dans les widgets tiers et le moteur.
- Nommer les catégories par des intentions, à condition que le niveau suivant redevienne concret.
- Conserver les noms vernaculaires des hébergements et les expliquer une fois.

---

## 2. Première impression (5 premières secondes)

**Faits observés**
- Séquence desktop : (1) préloader gris `#888b8d` plein écran, logo blanc, spinner `sk-bouncedelay 1.4s` ; (2) vidéo fixe `assets/video/main/2024_overview.mp4` (1440×900, autoplay, muted, `preload=metadata`, non loop, sans poster ni `playsinline`), lien « SKIP » vertical bas gauche (bloc 102×41 px) ; (3) grille de 4 tuiles 720×450 : LOOK INSIDE / DREAM (bougainvillier, arche, vélo), YOUR BORGO / EXPERIENCE (toits au couchant), BOTTEGA EGNAZIA (robe en dentelle, pieds nus), EVENTS & OFFERS (place illuminée de nuit).
- Header fixe 64 px transparent, hamburger 3 traits blancs à gauche, « IT EN » à droite (36×20 px) ; pas de logo sur la home desktop ; bloc logo 190×87 px centré (fond `rgba(48,41,34,.38)`) sur les sous-pages.
- Onglet « BOOK » vertical fixe droite, 46×140 px, centré (y = 380).
- Bannière iubenda bas droite ≈448×340 px (gris/noir, Arial, boutons noirs « Reject » / « Accept »), z-index 99999998, couvrant ≈30 % de la tuile EVENTS & OFFERS ; après fermeture, widget blanc « Notice at collection | Your Privacy Choices » (Arial gras, bleu) au milieu droit + bouton vert 38×38.
- Titres de tuile : H2 Optima 25 px, capitales, interlettrage 3 px, blanc ; sous-titre ≈9 px. Aucun H1 ; 94 mots ; meta description vide.
- Mobile : header 54 px opaque `#888b8d` (pictogramme logo à gauche, IT/EN et hamburger à droite) ; tuiles 100vh (844 px) ; onglet BOOK 30×140 px.

**Interprétation**
- On voit une attente, puis un film (non vérifié), puis quatre photos chaudes et des verbes d'invitation ; on comprend « village-hôtel dans les Pouilles » grâce au logo et aux toits ; on ressent chaleur et lenteur, puis hésitation : aucun texte d'accroche, aucun bouton, aucune indication de lieu.
- Premier CTA : l'onglet BOOK (gris clair sur photo, peu contrasté) ; premier CTA de contenu : un titre de tuile. Distraction majeure : la bannière puis le widget « Your Privacy Choices », seul élément en Arial/bleu d'un site en Optima.
- Raison de continuer : lumière dorée, détail de dentelle, mot « DREAM ». Raison de partir : attente (DOMContentLoaded 2,4 s, load 3,8 s home ; 13,2 s rooms) et vidéo lourde.

**Enseignements réutilisables**
- Styler les widgets tiers (iubenda le permet) pour ne jamais rompre la typographie.
- Vidéo d'intro : toujours `poster` + `playsinline`.
- Une grille de 4 tuiles peut servir de hero si un élément textuel ancre lieu et promesse.

---

## 3. Direction artistique

**Faits observés**
- Palette (JSON) : gris chaud `#888b8d` (préloader, footer, header mobile ; 147 occurrences sur rooms), `#e3e3e3` (138), blanc (130), brun `#2b241e` en overlay α 0,6 sur toutes les tuiles (112–137) et opaque sur contact (« brownbox ») et modale, `#575757` (bannière), `#302922` α 0,38 (bloc logo), `#362f29` (tuile OVERVIEW pleine et H1 de sous-pages). Textes : blanc, noir, `#919aa1` (footer), `#b0a392` beige (paragraphes overview/spa), `#888b8d` (paragraphes awards/contact).
- Typographie : `@font-face optima` (optima-webfont.woff2, 26–31 éléments/page), Lato 400 via Google Fonts (7 éléments), Nunito Sans déclarée par Bootswatch Lux non chargée, FontAwesome 4.7. Hypothèse : Optima est la police commerciale de marque (logotype en capitales à empattements fins similaires).
- Échelle desktop : H2 tuiles 25/30 px, 400, capitales, ls 3 px ; H1 awards 26 px 600 ls 1 px ; H1 spa/overview 16 px 600 capitales ls 3 px `#362f29` ; H2 contact 20 px 600 ls 3 px ; corps 14/21 px ; paragraphes 13/19,5 px graisse 300 ; contact 14/21 graisse 200 ; menu 22 px (×18, hypothèse : entrées fold-out) ; méta 9 px (×11). Mobile : menu 17 px, H2 25 px inchangés.
- Grille : Bootstrap 4.1.3 `row no-gutters` ; home/experiences/dining/offers `col-md-6` (2×720 px) ; rooms 3 colonnes 480×450 ; page La Corte `col-md-4 vh50` (3 tuiles) puis `col-md-3 vh50` (4 tuiles) — hypothèse desktop : 2 rangées de 50vh, 3 + 4 colonnes ; spa/overview : texte 483 px + photo portrait 542×900. Container 1 140 px (footer, contact). Rayon 0 partout (bouton SEND `radius 0px`, modale, champs, tuiles).
- Boutons : SEND 110×32 px, blanc, bordure 1 px `#888b8d`, 11 px capitales, transition 0,15 s ease-in-out ; « Check availability » ≈506×50 px brun (≈`#4a4038`, estimé) ; moteur : BOOK NOW ≈120×38 px CSS brun, rayon ≈4 px ; SEARCH blanc bordé ; EXPLORE pilule blanche.
- Iconographie quasi absente (croix, chevrons FontAwesome) ; le moteur ajoute cadeau/loupe/traduction/calendrier/personnes/poussette/porte.
- Photos plein cadre sous overlay 60 %, animation `zoominimg 40s ease` ; 0 `srcset`, 0 lazy ; formats mêlés (`vairspaph.png` 2,2 Mo, `newevents.jpeg` 6,3 Mo, `cover_corte_meravigliosa.jpeg` 1,1 Mo).
- Vidéos de tuile 720×450 / 720×900 (experiences 4 sources dont 2 images `.webp/.jpg` dans `<video>`, dining 2, rooms 1 + 1 image), `loop`, non autoplay, `muted:false`, `preload=metadata`.
- Vide : nul sur les mosaïques (bord à bord) ; large sur les sous-pages texte (colonne 45 % de largeur, marge 30 px).

**Interprétation**
- Trois matériaux : photo dorée sous voile brun, capitale Optima espacée, gris neutre des zones techniques. Le brun `#2b241e` est la couleur de marque implicite. Rayon 0 + zéro gouttière prolongent le motif « 4 dalles » du logo : c'est le vrai fil conducteur.
- Faiblesses : beige sur blanc 2,47:1 et gris sur blanc 3,43:1 sous AA ; échelle plate (H1 16 px < H2 25 px) ; trois univers typographiques (Optima / Lato / Arial des widgets, plus la police système du moteur).

**Tableau de tokens approximatifs**

| Token | Valeur | Usage |
|---|---|---|
| color.brand.brown | `#2b241e` | overlay α 0,6, modale, contact, moteur |
| color.brand.brownDark | `#362f29` | H1 sous-pages, tuile OVERVIEW pleine |
| color.neutral.grey | `#888b8d` | préloader, footer, header mobile, bordures |
| color.neutral.greyLight | `#e3e3e3` | fonds secondaires |
| color.text.beige | `#b0a392` | paragraphes overview/spa |
| color.text.meta | `#919aa1` | footer |
| font.display | Optima woff2 auto-hébergée | titres, menu, corps |
| font.secondary | Lato 400 (Google Fonts) | 7 éléments |
| type.h2.tile | 25/30 px, 400, caps, ls 3 px | tuiles |
| type.h1.page | 16/19,2 px, 600, caps, ls 3 px | spa, overview |
| type.body / para | 14/21 px ; 13/19,5 px 300 | corps / textes longs |
| type.meta | 9–11 px | footer, sous-titres |
| radius | 0 px (site) / ≈4 px (moteur) | — |
| header.h | 64 px desktop / 54 px mobile | fixe |
| tile.h | 450 px (2 rangées) ; 100vh mobile ; 50vh page chambre | sections |
| book.tab | 46×140 desktop / 30×140 mobile | fixe droite |
| motion | `zoominimg 40s ease` ; `fadeIn 1s` ; UI 0,15 s ease-in-out | — |

**Enseignements réutilisables**
- Overlay brun (et non noir) à 60 % : photos unifiées, blanc lisible à ≈6–9:1.
- Rayon 0 + grille sans gouttière = signature, à compenser par de la respiration sur les pages texte.
- Trois niveaux de titre nettement distincts (ex. 48 / 25 / 16).

---

## 4. Architecture de la page d'accueil

**Faits observés** (docHeight 1 016 px = 900 px de tuiles + 116 px de footer ; 1 seule section DOM)

| Position | Section | Objectif | Contenu | Interaction | CTA | Émotion créée |
|---|---|---|---|---|---|---|
| Avant page | Préloader | Masquer le chargement | Gris `#888b8d`, logo, spinner | Disparition au `window-loaded` | — | Attente |
| 0–900 (état 1) | Vidéo fixe | Immersion | `2024_overview.mp4`, 9,3 Mo par requête partielle (×2 = 18,5 Mo) | SKIP ; fin → grille (hypothèse) | SKIP | Anticipation |
| 0–450 g. | LOOK INSIDE / DREAM | Ouvrir la visite | Bougainvillier, arche, vélo ; overlay 60 % | Zoom 40 s ; lien → /rooms/ (hypothèse d'après le flux) | Titre-lien | Curiosité |
| 0–450 d. | YOUR BORGO / EXPERIENCE | Vendre le lieu-vie | Toits au couchant | → /your-experience/ | Titre-lien | Émerveillement |
| 450–900 g. | BOTTEGA EGNAZIA | Renvoi boutique | Dentelle, pieds nus | Lien externe | Titre-lien | Sensualité |
| 450–900 d. | EVENTS & OFFERS | Convertir | Place de nuit | → /events-and-offers/ | Titre-lien | Fête |
| Fixe | Onglet BOOK | Réserver | 46×140 | Modale CHECK AVAILABILITY | BOOK | — |
| 900–1 016 | Footer | Réassurance / légal | Réseaux, adresse, 2 téléphones (info / prenotazioni), Maps, CIN, Legal, PDR125, 3 boutons iubenda, 7 logos | Liens | — | Crédibilité |

**Interprétation**
- Narration : attente → film → quatre photos sans texte ; l'offre ne devient jamais concrète sur la home (ni chambre, ni prix, ni date) ; les chambres sont à 1 clic (→ mosaïque de 6 → mosaïque de 7 → moteur) ; la preuve est reléguée aux logos du footer ; la réservation est un onglet latéral ; la fin est administrative.
- Home-portail, pas page de vente : elle distribue vers quatre univers dont un externe. Le moment concret est déporté dans le moteur (prix, conditions, « Last room left »).

**Enseignements réutilisables**
- Une home de 4 tuiles est comprise en une seconde ; ajouter au moins une tuile concrète (hébergement phare + prix d'appel ou saison).
- Des logos de distinctions blancs de 40 px sur gris en footer sont permanents mais invisibles.

---

## 5. Scroll et storytelling

**Faits observés**
- Home, rooms, experiences, dining, offers : 900–1 016 px, aucun scroll utile ; `pinned: []`, transforms 0, `parallax 0`, `scrollSnap 0`, `scrollTimeline 0`, `data-reveal` ×2, `wow fadeIn` sur logo et langues ; header inchangé au scroll.
- Awards : seule page longue (4 334 px ; 8 467 px mobile) : hero nocturne 900 px, titre centré, chevron ↓ encadré 60×60, puis liste centrée gris 13 px sur blanc, années en noir.
- Spa / overview : un écran, texte beige à gauche, photo portrait à droite avec flèches ‹ › encadrées (slider ; hypothèse : fancybox ou carousel Bootstrap).
- Page La Corte (mobile) : 7 tuiles de 50vh (422 px), la 2e (OVERVIEW) en aplat brun `#362f29` sans photo ; 2 954 px de tuiles + footer.
- Changements de fond : aucun sur la home ; photo → blanc sur awards/spa/overview ; brun opaque sur contact.

**Interprétation**
- Le storytelling passe par le clic, pas par le scroll : « plein écran / clic / plein écran ». Aucune révélation progressive ni alternance texte/image ; la seule respiration textuelle (overview) est à 3 clics de la home.
- Fonctions des rares effets : zoom 40 s = lenteur/émotion ; fadeIn logo = marque ; chevron = orienter ; overlay = lisibilité ; tuile brune OVERVIEW = rythme dans une série de photos.

**Enseignements réutilisables**
- Une mosaïque sans scroll exige un chemin texte à 1 clic.
- Alterner une tuile en aplat de couleur dans une série de tuiles photo crée un repère sans coût.

---

## 6. Animations et micro-interactions

**Faits observés** : jQuery 3.3.1, Bootstrap 4.1.3 + Popper, WOW 1.1.2, animate.css 3.7.0, fancybox 3.5.6, bootstrap-datepicker 1.8.0 (locale IT), moment.js 2.24.0 ; 84–86 keyframes ; cubic-beziers d'animate.css (`.215,.61,.355,1` ×24, `.55,.055,.675,.19` ×24, `.175,.885,.32,1` ×24, `.755,.05,.855,.06` ×8), `cubic-bezier(0.77,0.2,0.05,1.0)` ×3 et `.49,.78,.46,1.34` ×2 (hypothèse : fold-out et main-mobile.css) ; durées 0,15 s ×36, 0,5 s ×15, 0,3 s ×12, 0,55 s ×4 ; 23 règles reduced-motion.

| Animation | Déclencheur | Élément | Effet | Fonction | Risque UX |
|---|---|---|---|---|---|
| Préloader | Chargement | `.window-loading` + `#loaderLogo` + spinner `sk-bouncedelay 1.4s ease-in-out` (hypothèse SpinKit) | Gris + logo jusqu'à `window-loaded` | Masquer le chargement | Bloqué sur 5 captures ; 3,8–13,9 s de load |
| Vidéo intro | Chargement | `video#myVideo` fixe z0 | Autoplay muted non loop, SKIP | Émotion, marque | 9,3 Mo/requête, sans poster ni playsinline |
| Apparition grille | Fin vidéo / SKIP | 4 tuiles | Hypothèse fadeIn animate.css | Transition | Non vérifié |
| Zoom photo | Permanent ou survol (non mesuré) | Fonds de tuile | `zoominimg 40s ease` | Lenteur, vie | Si permanent, texte fixe sur image mouvante |
| Fade logo/langues | Chargement | `.homeloogotop`, `.selettore-lingue` | `fadeIn 1s ease` (0 s sur la home) | Marque | Aucun |
| Hover cookies | Survol | Boutons iubenda | opacité 0,7→1 ; inset 10 % | Feedback | Hors DA |
| Hover tuiles | Survol | Titres/tuiles | **Aucun changement mesuré** (`changed: {}`) | — | Pas d'affordance : le titre est un lien sans état |
| Menu | Clic hamburger (checkbox `openmenu`) | Panneau fold-out (`fold-out.css`) | Hypothèse : dépliage CSS `cubic-bezier(0.77,0.2,0.05,1)` 0,5–0,55 s | Navigation | Non ouvrable par script ; clavier incertain (checkbox-hack) |
| Modale BOOK | Clic onglet | `#booking` | Modale Bootstrap ≈586×340 sur fond assombri (fade 0,15–0,3 s, hypothèse) | Conversion | Masque la home ; datepicker |
| Carrousel | Clic flèches | Spa/overview | Slider (hypothèse fancybox) | Galerie | Flèches fines 40×40 peu visibles |
| Curseur / scroll | — | `cursor:auto`, aucun effet scroll | — | — | — |
| Reduced motion | media query | 4 éléments animés + 23 transitions restent actifs ; vidéo autoplay conservée ; seule règle site-side : `.animated{animation:unset}` (main-mobile.css) | — | Non conforme pour vidéo et zoom |

**Interprétation**
- Animation « a minima » : une seule animation d'auteur (`zoominimg`), le reste fourni par les librairies. Ni transition de page, ni reveal, ni curseur. Le manque le plus visible : aucun état de survol sur les tuiles ; le zoom 40 s est trop lent pour servir de feedback.

**Enseignements réutilisables**
- Zoom 30–40 s ease + hover court 0,3–0,5 s (overlay éclairci, titre souligné) : deux vitesses, deux fonctions.
- Respecter reduced-motion pour vidéo autoplay et zooms permanents.

---

## 7. Navigation et architecture de l'information

**Faits observés**
- Header fixe transparent 64 px (mobile 54 px opaque) ; hamburger gauche desktop / droite mobile ; IT/EN via `culture.php?lang=`.
- Menu DOM (20 entrées) : BOOKING (deep-link moteur, dates du jour, 2 adultes) · ROOMS · BAR AND RESTAURANTS · BOTTEGA EGNAZIA* · VAIR SPA · EVENTS & OFFERS · CHRISTMAS AT BORGO EGNAZIA* · FOGLIE MAGAZINE* · ACCOLADES · EGNAZIA* · LHW LEADERS CLUB* · ASSOCIAZIONE CLARA* · MEDIA HUB* · TRAVEL TRADE · BE STAFF · VOUCHER* · SUSTAINABILITY* · CONTACT US (+ IT/EN). * = hors domaine principal (11 sur 20). Mobile : 17 px, CTA BOOKING 87×24 px, CONTACT US 117×24 px.
- Arborescence : home (4) → /rooms/ (6 : LA CORTE, IL BORGO, LE CASE, BAR AND RESTAURANTS « TASTE », BORGO OVERVIEW, OTHER SERVICES) → /rooms/la-corte/ (7 : LA CORTE MAGNIFICA, OVERVIEW, LA CORTE BELLA, LA EMMA, LA CORTE MERAVIGLIOSA, LA CORTE SPLENDIDA, LA EGNAZIA) → moteur. /your-experience/ (4), /food-and-drink/ (2), /events-and-offers/ (2).
- URL dupliquées : VAIR SPA et EVENTS & OFFERS du menu pointent vers `/?section=…` alors que des chemins propres existent ; `//travel-trade` (double slash).
- Infos essentielles : adresse et 2 téléphones dans chaque footer ; page contact « HOW TO GET THERE » (voiture, train, Bari 55 km / Brindisi 50 km), formulaire 7 champs + select département + case privacy, bouton SEND, reCAPTCHA v3, Google Maps.
- Réservation persistante : oui, onglet BOOK fixe sur toutes les pages (46×140 / 30×140) + BOOKING en tête de menu. Skip link : home uniquement ; landmarks main/nav/header/footer présents.

**Interprétation**
- Arborescence de mosaïques : 3 clics pour une catégorie, 4 pour une chambre précise, sans prix hors moteur ; 3 clics pour une offre.
- Menu = annuaire d'entreprise sans hiérarchie client/institutionnel ; 11 sorties de domaine diluent l'attention.
- Frustrations : /rooms/ mélange 3 hébergements et 3 non-hébergements ; tuile OVERVIEW dupliquée ; onglet BOOK mobile de 30 px et CTA de 24 px sous le seuil tactile de 44 px.

**Enseignements réutilisables**
- Séparer le menu en deux blocs (client / entreprise) ou reléguer le second au footer.
- Une mosaïque de niveau 2 ne doit contenir que des objets de même nature.
- Onglet vertical persistant : efficace s'il dépasse 44 px sur mobile.

---

## 8. Parcours de réservation et conversion

**Faits observés**
- CTA : onglet BOOK (lien `#booking` sans texte DOM, `target=_blank`) ; BOOKING dans le menu avec `arrival=20260904&departure=20260905&adults=2`.
- Modale « CHECK AVAILABILITY » : titre Optima 26 px capitales, boîte brune ≈586×340 px, Check In / Check out (inputs texte + bootstrap-datepicker), Adults 1–10 (défaut 1), Children 0–10 (défaut 0), bouton plein ≈506×50 px, croix. Pas de nombre de chambres, pas de code promo, aucune mention de prix ni de garantie.
- Sonde desktop : URL sans `#/` → « Sorry, nothing here…(404) GO BACK » (Roboto, bouton vert-bleu) — hors charte.
- Moteur mobile (hypothèse : solution propriétaire/white-label, footer « E.I.T. S.p.a. ») : header logo complet + icônes cadeau/loupe/traduction ; photo hero ; « Arrival and departure » (04 → 06 October 26), « Guests » (2 adultes, 0 enfant, 1 chambre), « Promocode », SEARCH ; bannière iubenda rejouée ; bloc « Unique special offers every day » + EXPLORE ; cartes chambre : photo, nom (LA CORTE BELLA VISTA PISCINA, LA EGNAZIA…), badge noir « Last room left » sur plusieurs catégories, description tronquée, LEARN MORE / GALLERY ; 2–3 tarifs par chambre : ADVANCE PURCHASE (breakfast, non-refundable, prepaid) 880 €, BEST AVAILABLE RATE (free cancellation until 7 days before arrival, prepaid) 980 €, 'DINE AROUND' RATE (half board) 1 180 € ; jusqu'à 3 780 € ; « Avg price per night » ; BOOK NOW. Pied : booking@borgoegnazia.com, téléphone, note taux de change, MY RESERVATION, ENGLISH | EUR. ≈16 000 px CSS de haut.
- Réassurance site : logos footer, page Awards, téléphones, e-mail. Aucun avis, aucune note, aucun bénéfice de réservation directe, aucune conciergerie ; Voucher externe ; newsletter (lien). Page offers = 2 tuiles sans contenu.

**Interprétation**
- Découvrir / demander / réserver = DISCOVER / CONTACT US / BOOK : clair mais pauvre (pas de demande de devis villas/mariages, pas de rappel).
- Ruptures : sous-domaine `booking.` (identité conservée : logo, brun, police proche d'Optima — point fort), nouvel onglet, bannière rejouée, 404 hors charte si fragment perdu, 16 000 px sans filtre ni ancre sur mobile, double saisie (chambres, promo).
- Transparence : bonne dans le moteur (annulation J-7, prépaiement, pension, prix moyen) ; nulle sur le site. Urgence « Last room left » répétée : crédibilité discutable.

**Enseignements réutilisables**
- Moteur dans la charte = rupture minimale ; conditions tarifaires visibles dès la liste.
- Aligner les champs de la modale sur ceux du moteur (chambres, promo) pour éviter la double saisie.

---

## 9. Pages chambres / propriétés

**Limite** : la page La Corte n'a pas pu être lue en desktop (écran anti-bot puis préloader) ; le desktop est décrit via `rooms.json` + `flow-rooms.png` (liste des hébergements), le détail via `room-detail-mobile.json` (recapturé) et `flow-mobile-room-detail.png`.

**Faits observés — liste desktop (/rooms/, 1440×900)**
- 6 tuiles 480×450 : LA CORTE « DISCOVER » (façade et bassins au couchant), IL BORGO (ruelles, bougainvilliers), LE CASE (piscine privée turquoise, chaises longues, façade), BAR AND RESTAURANTS « TASTE » (bar blanc voûté), BORGO OVERVIEW (clocher), OTHER SERVICES (vidéo `Altri Servizi-1.mp4` 1,7 Mo). Bloc logo, onglet BOOK, footer. 103 mots. Aucun prix, surface, capacité, équipement. Load 13,2 s (FCP 0,9 s).

**Faits observés — détail mobile (/rooms/la-corte/, 390×844)**
- Header 54 px gris ; 7 tuiles `vh50` de 422 px : LA CORTE MAGNIFICA (lit à baldaquin de voile, textiles crème, porte-fenêtre), OVERVIEW (aplat brun `#362f29`, sans photo), LA CORTE BELLA, LA EMMA, LA CORTE MERAVIGLIOSA, LA CORTE SPLENDIDA, LA EGNAZIA ; chaque tuile = H2 25 px + « DISCOVER » + photo d'intérieur (blanc/crème, pierre, lanternes) ; classes `col-md-4` (3 premières) puis `col-md-3` (4 suivantes) → hypothèse desktop : 2 rangées de 50vh. Hauteur 2 954 px + footer ≈ 3 190 px CSS. Aucun texte, galerie, prix, capacité, CTA hors onglet BOOK. 108 mots ; 0 H1 ; 10 images sans alt ; 7 images de fond dont `cover_corte_meravigliosa.jpeg` 1,1 Mo ; 96 requêtes, 5,6 Mo ; FCP 1,5 s, load 13,9 s ; feuille `main-mobile.css` dédiée.
- Niveau suivant (fiche d'une chambre) : non capturé. Le moteur, lui, donne par catégorie photo, nom, description courte, galerie, tarifs et conditions.

**Interprétation**
- La « page chambre » du site est une double mosaïque (catégorie → sous-catégorie) puis le moteur. Ordre : photo → nom → DISCOVER. Aucune promesse écrite, capacité, équipement, service, ni hébergement complémentaire (hors tuiles voisines).
- Projection : intérieurs homogènes vendant une atmosphère, pas une chambre ; sans surface ni vue, aucune comparaison possible. Réassurance absente à ce niveau.
- Mobile : 7 demi-écrans à parcourir ; la tuile brune OVERVIEW rompt utilement la série mais son libellé est ambigu (overview de quoi ?).

**Enseignements réutilisables**
- Adjectifs de marque (Magnifica, Bella, Splendida) : mémorables ; ajouter une ligne factuelle (m², vue, capacité).
- Regrouper catégorie + sous-catégories sur une page à ancres plutôt qu'un niveau de mosaïque supplémentaire.

---

## 10. Copywriting

**Faits observés**
- Volume : 94 mots (home, experiences), 103 (rooms), 108 (La Corte), 100 (offers), 156 (spa), 179 (dining, bannière incluse), 255 (contact), 328 (overview), 754 (awards).
- Titres : 1 à 3 mots en capitales (LOOK INSIDE, LE CASE, EAT, DRINK, HAVE FUN, DISCOVER PUGLIA) ; sous-titre verbe/nom 9 px (DREAM, EXPERIENCE, DISCOVER, TASTE).
- Overview : ouverture en deux phrases nominales (« Borgo Egnazia. Nowhere Else. »), énumération de matières et plantes (bougainvillier, jasmin, romarin, olivier, pierre sèche, tuf), lexique mémoire/appartenance, formule-refrain de clôture répétée deux fois (« …enhance the pleasure of the senses »).
- Spa : étymologie (« Vair means "true"… »), métiers artistiques, « Science of Happiness » entre guillemets, promesse de personnalisation.
- Moteur : registre commercial (« Unique special offers every day », « Last room left », « Avg price per night »).
- CTA : DISCOVER (≈15 occurrences), TASTE, BOOK, BOOKING, Check availability, SEND, « Discover our web site > », BOOK NOW, LEARN MORE, GALLERY, EXPLORE, SEARCH.
- Anglais avec italianismes (Casetta, Borgo, Piazza, Corte) ; og en italien ; `<title>` « Borgo Egnazia » partout.

**Interprétation**
- Ton lyrique et institutionnel ; le luxe n'est jamais nommé sur les pages (seulement dans le JSON-LD et le nom de l'og:image). Caractéristiques techniques absentes du site, présentes dans le moteur.
- Mécanismes : signature nominale, énumération sensorielle locale, mot dialectal expliqué, verbe d'invitation en sous-titre, refrain de clôture. Transformation prestation → expérience : « spa » → « poetic experiences » par des « therapist-artists ».
- Limites : DISCOVER ×15 vide le CTA de sens ; aucune promesse chiffrée ; refrain dupliqué dans 328 mots ; titres de page identiques.

**Enseignements réutilisables**
- Sous-titre-verbe sous un nom de section.
- Un mot vernaculaire expliqué = actif de marque.
- Varier les CTA par tuile (« See the rooms », « Read the story », « Book a table »).

---

## 11. Photographie et vidéo

**Faits observés**
- Plans : aériens (toits au couchant ; place de nuit avec illuminations et foule ; village nocturne sur awards), architecturaux (arche + vélo ; escalier sous bougainvillier ; bar blanc voûté ; clocher), détails (dentelle, pieds nus, luminaires ambrés du moteur), humains (danseuses de pizzica blanc/rouge ; femme de dos dans un bassin turquoise ; enfant de dos ; mains et nourriture floue), intérieurs (7 chambres crème/blanc, baldaquins, lanternes, porte-fenêtres).
- Lumière : heure dorée dominante, nuit chaude, spa en turquoise froid. Couleurs : ocre, crème, tuf, fuchsia, rouge.
- Humains : jamais de visage frontal ; home 1 corps partiel sur 4 tuiles ; experiences 3 sur 4 (dos, mains).
- Proportion lieu/expérience : home 3/1 ; experiences 0/4 ; rooms 5 lieux + 1 vidéo.
- Ratios : 720×450 (1,6) home, 480×450 (1,07) rooms, 542×900 (0,6) spa/overview, 100vh mobile (0,46), 50vh mobile (0,92) : mêmes fichiers, aucun `srcset`.
- Poids : `newevents.jpeg` 6,27 Mo et `newoffers.jpeg` 5,47 Mo (offers = 24 Mo d'images desktop, 12 Mo mobile) ; `vairspaph.png` 2,2 Mo ; `cover_corte_meravigliosa.jpeg` 1,1 Mo ; `BorgoEgnazia_Festa_piazza_2.jpg` 559 Ko ; `botteganew.jpg` 426 Ko.
- Vidéos : intro 18,5 Mo transférés (2 requêtes 206) ; `Eat Drink Have Fun-2.mp4` 3,95 Mo ; `Risoranti2-2.mp4` 1,9 Mo ; `Altri Servizi-1.mp4` 1,7 Mo ; `Family-3.mp4` 1,14 Mo ; `Bar2-1.mp4` 1,1 Mo ; toutes loop, non autoplay, `muted:false`, `preload=metadata` ; 2 « vidéos » sont des images dans `<video>` (hypothèse : gabarit commun).

**Interprétation**
- La photo est le moteur du site : un style unique (heure dorée + voile brun), cadrages sur matière et lumière, humains anonymes pour la projection. Les intérieurs sont cohérents mais interchangeables.
- La vidéo est une « texture de tuile » (loop, sans son coupé, sans contrôle ; hypothèse : lecture au survol via JS, non vérifiée). Incohérence technique : mêmes fichiers pour 5 ratios, poids déraisonnables.

**Shot list pour reproduire ce niveau**
1. Aérien du lieu à l'heure dorée (drone 30–45°), toits et repère vertical.
2. Aérien de nuit avec éclairage d'événement et foule.
3. Porche d'entrée avec objet de vie (vélo) et végétation floue en premier plan.
4. Détail de matière artisanale porté par un corps partiel.
5. Danse/fête locale en mouvement.
6. Enfant ou couple de dos face au paysage.
7. Femme de dos dans l'eau du spa, lumière froide.
8. Mains et nourriture en gros plan ; table de nuit aux bougies.
9. Bar/restaurant vide, lumière blanche, symétrie.
10. Chambre : baldaquin, lumière latérale, porte-fenêtre ouverte ; une variante distinctive par catégorie (terrasse, piscine, bureau).
11. Piscine privée avec deux chaises longues et façade.
12. Ruelle avec bougainvillier fuchsia.
13. Film 60–90 s (aérien + détails + humains), 1080p ≤ 4 Mo, poster dédié.
14. Boucles 6–10 s par tuile (bar, restaurant, famille, services), 720×450 et 720×900, ≤ 1 Mo, muettes.

---

## 12. Mobile (390×844, DPR 2)

**Faits observés**
- Home (préloader retiré) : header 54 px opaque `#888b8d` (pictogramme logo, IT/EN, hamburger), tuiles 100vh : LOOK INSIDE / DREAM, YOUR BORGO (masquée aux 2/3 par la bannière ≈560 px de haut), BOTTEGA EGNAZIA, EVENTS & OFFERS ; footer centré (réseaux, adresse sur 3 lignes, 3 boutons iubenda, 7 logos sur 2 rangées) ; ≈1 926 px CSS. Vidéo d'intro : présence non vérifiée (JSON mobile = anti-bot).
- Titres : H2 25 px / ls 3 px et sous-titres 9 px inchangés ; menu 17 px ; corps 14 px.
- Tailles tactiles : onglet BOOK 30×140 px (x = 360, y = 352) ; BOOKING 87×24 ; CONTACT US 117×24 ; boutons iubenda ≈173×27 ; bouton vert préférences 38×38 (z-index 2147483647).
- Hauteurs : La Corte ≈3 190 px (7 × 50vh), overview 2 875, spa 2 065, offers 2 065, awards 8 467.
- Anomalie de largeur (≈205/390 px) sur `offers/spa/about-mobile-02-full`, absente de `flow-mobile-home-noloader` ; hypothèse widget iubenda / artefact, non vérifiée.
- Réseau : offers 89 req / 15,1 Mo (12 Mo d'images), La Corte 96 req / 5,6 Mo, spa 5,5 Mo, overview 4,4 Mo, awards 3,6 Mo ; FCP 0,37–1,53 s ; load 1,1 s (spa) à 13,9 s (La Corte). Fonts : 2 fichiers / 36 Ko.
- Moteur mobile : champs gris 56 px de haut, SEARCH bordé, cartes pleine largeur, BOOK NOW ≈120×38, texte 14–16 px ; ≈16 000 px ; bannière rejouée.
- `maximum-scale=1` (zoom bloqué) ; 13 textes < 12 px.

**Interprétation**
- Transposition directe : 1 tuile = 1 écran (100vh) ou 1 demi-écran (50vh sur La Corte), sans aperçu de la suite ni indicateur de scroll ; animations conservées (zoom 40 s, fadeIn) ; pas de hover donc aucune affordance.
- BOOK 30 px et CTA 24 px sous les 44 px ; sous-titres 9 px illisibles à DPR 2 avec zoom bloqué.
- Vitesse perçue correcte (header opaque et première tuile rapides) sauf offers (12 Mo) et La Corte (load 13,9 s).
- Différences avec desktop : header opaque avec logo, commandes à droite, tuiles empilées, bannière à 66 % de l'écran.

**Enseignements réutilisables**
- Tuiles de 85vh (pas 100vh) pour laisser dépasser la suivante ; 50vh est un bon compromis pour les listes longues.
- Ne jamais bloquer le zoom avec des textes de 9 px.
- Variantes portrait via `srcset`/`<picture>`.

---

## 13. Performance, accessibilité, SEO

**Faits observés — performance**
- Home : TTFB 154 ms, FCP 804 ms, DOMContentLoaded 2 375 ms, load 3 787 ms ; 179 requêtes / 28,4 Mo (médias 18,6 Mo, 73 scripts / 4,2 Mo, 31 images / 3,65 Mo, 28 CSS / 831 Ko, 6 fonts / 223 Ko) ; CSS total 495 Ko (Bootstrap, Bootswatch Lux, FontAwesome, animate.css, fancybox, datepicker, main.min.css, fold-out.css).
- Rooms : load 13 221 ms, 178 req / 11,9 Mo. Experiences : 181 req / 18 Mo (7 médias 10,5 Mo). Dining : 185 req / 10,7 Mo. Offers : 154 req / 30,1 Mo (2 JPEG de 6,3 et 5,5 Mo chargés deux fois). Spa : 11 Mo. Awards : 7,1 Mo, FCP 368 ms. Contact : 224 req, 99 scripts (chat `hotelchat.ai`, recrutement `inrecruiting.intervieweb.it`, `optimand.com`, Maps, reCAPTCHA, GTM, GA, `pagead2`).
- Tiers (home) : cdnjs 18, bootstrapcdn 10, iubenda 13, google-analytics 9, google.com 9, gstatic 8, optimand 6, googletagmanager 6, cloudfront 6, jsdelivr 4, fonts.googleapis 4, maps 4, googlesyndication 4.
- 0 lazy loading, 0 `srcset`, `preload=metadata` partout, 0 `will-change`. Préloader plein écran jusqu'à `window-loaded` (masque les décalages mais s'est bloqué sur 5 captures).

**Faits observés — accessibilité**
- Contrastes calculés : blanc sur `#888b8d` (footer, header mobile) 3,43:1 ; `#888b8d` sur blanc (awards/contact 13–14 px) 3,43:1 ; `#b0a392` sur blanc (overview/spa 13 px) 2,47:1 ; `#919aa1` sur blanc 2,86:1 ; `#362f29` sur blanc 13,2:1 ; blanc sur `#2b241e` 15,3:1 ; blanc sur overlay 60 % au-dessus d'une photo claire ≈6,3:1, moyenne ≈9,2:1. Titres conformes, paragraphes sous AA.
- `focusOutlineNone` 42–47 règles ; 4 liens sans nom ; 1 iframe sans titre ; images sans alt 9–12 par page (seul le logo est décrit) ; fonds CSS non décrits.
- Formulaire contact : 7 champs sans `<label>` (placeholders), e-mail et téléphone en `type=text`, classe `hasDatepicker` appliquée par erreur au champ Email ; case privacy avec label.
- Menu en checkbox-hack, aucun `<button>` dans le header. Skip link : home seulement. `lang="en"`, landmarks corrects.
- Reduced motion : 23 règles (Bootstrap `.form-control` etc.) + `.animated{animation:unset}` (main-mobile.css) ; capture `04-reduced-motion` identique ; 4 éléments animés, 23 transitions et la vidéo autoplay restent actifs. Vidéo sans bouton pause hors SKIP.

**Faits observés — SEO**
- `<title>` « Borgo Egnazia » sur 100 % des pages ; meta description vide ; og:title/description en italien sur pages EN ; `og:image` `luxury-hotel-puglia.jpg` ; canonical absent ; hreflang absent (2 langues) ; JSON-LD `WebSite` seul (pas de `Hotel`/`Offer`).
- H1 : 0 sur home, rooms, experiences, offers, La Corte ; 1 sur dining, spa (16 px), overview (16 px), awards (26 px), contact. H4 avant H2 sur contact.
- Contenu indexable : 94–108 mots sur les pages principales ; URL dupliquées (`/?section=` vs chemins) sans canonical ; `maximum-scale=1`.

**Interprétation**
- Équilibre immersion/performance défavorable : vidéo d'intro (18,5 Mo) et JPEG de 6 Mo sont critiques ; la pile 2018 (Bootstrap 4.1.3, jQuery 3.3.1, animate.css complet) coûte 5 Mo de code pour une animation d'auteur.
- Accessibilité traitée par défaut de librairie, pas par conception. SEO quasi inexistant hors notoriété de marque.

**Enseignements réutilisables**
- Budget : intro ≤ 4 Mo avec poster ; images ≤ 400 Ko WebP/AVIF + `srcset` ; lazy sous le pli.
- Titres/descriptions uniques, H1 visible, JSON-LD `Hotel` + `Offer`, canonical + hreflang.
- Jamais `outline:none` sans focus de remplacement ; labels sur chaque champ.

---

## 14. Conclusion

### 15 meilleurs éléments
1. Signature « Nowhere Else » intégrée au logo et répétée sur préloader, bannière, moteur, footer.
2. Logo « 4 dalles » justifiant la grille sans gouttière ni rayon.
3. Home en 4 tuiles plein écran avec intentions (DREAM / EXPERIENCE).
4. Overlay brun `#2b241e` à 60 % : photos unifiées, titres blancs ≥ 6:1.
5. Optima en capitales espacées (25 px / ls 3 px) reconnaissable.
6. Photographie cohérente : heure dorée, matières, humains anonymes de dos.
7. Zoom `zoominimg 40s ease` : vie sans agitation.
8. Onglet BOOK vertical fixe 46×140 : persistance discrète.
9. Modale de disponibilité dans la charte, 4 champs, un bouton.
10. Moteur conservant logo, couleur et police : rupture minimale.
11. Conditions tarifaires explicites dès la liste (annulation J-7, prépaiement, pension, prix moyen/nuit).
12. Nommage des hébergements par adjectifs de marque (Magnifica, Bella, Splendida).
13. Tuile en aplat brun `#362f29` dans la série de chambres : repère de rythme.
14. Texte overview structuré en promenade architecturale ; mot dialectal « Vair » expliqué.
15. Capital de preuve disponible : Awards 2011–2025, logos LHW/GSTC/50 Best.

### 5 faiblesses / limites
1. Poids : 28 Mo (home), 30 Mo (offers), vidéo 9,3 Mo/requête, JPEG de 6 Mo, 0 lazy/srcset, 73 scripts ; load 13 s sur rooms et La Corte.
2. Profondeur : 4 clics et 3 mosaïques identiques pour une chambre ; aucun prix, surface, capacité hors moteur.
3. Menu-annuaire de 20 entrées dont 11 externes ; URL dupliquées ; rooms mélange hébergements et services.
4. Accessibilité/SEO : paragraphes 2,5–3,4:1, `outline:none` ×43, alt manquants, formulaire sans labels, zoom bloqué, titres identiques, description vide, H1 absents, reduced-motion non géré.
5. Tiers hors charte (bannière et widget iubenda en Arial/bleu, 404 du moteur) et rendus fragiles observés (bande blanche, préloader bloqué).

### 10 principes réutilisables
1. Une signature courte partout, y compris dans les composants tiers.
2. Un motif graphique → une règle de layout (grille sans gouttière, rayon 0).
3. Overlay de couleur de marque plutôt que noir.
4. Tuile = photo + nom + verbe d'intention ; jamais plus de deux niveaux.
5. Zoom lent permanent + hover court.
6. CTA de réservation persistant et discret, modale courte, moteur dans la charte.
7. Conditions d'annulation et pension visibles avant le prix.
8. Texte sensoriel en promenade, à 1 clic de la home.
9. Budget média strict (poster, ≤ 4 Mo, ≤ 400 Ko, lazy).
10. SEO et accessibilité par conception (H1, titres uniques, labels, focus, reduced-motion).

### Éléments propres à la marque à ne PAS copier
- Vocabulaire italien (Borgo, Corte, Casette, Vair) et signature « Nowhere Else ».
- Logo « 4 dalles » + Optima en capitales espacées (association identifiable).
- Photos du village reconstitué, danseuses de pizzica, robe en dentelle (contenus propriétaires).
- Écosystème de sous-marques (Bottega, Foglie, Associazione Clara), pertinent pour un groupe seulement.

### Notes /10
- **Branding : 8/10** — signature omniprésente (logo, préloader, cookies, moteur), noms d'hébergements et lexique dialectal cohérents ; retenue par le menu-annuaire (11 liens externes) et les widgets hors charte.
- **Direction artistique : 7/10** — palette brun/gris/blanc et Optima 25 px/ls 3 px tenues sur 10 pages, overlay 60 % efficace ; mais H1 16 px < H2 25 px, paragraphes beige 2,47:1, mélange Optima/Lato/Arial.
- **Animations : 4/10** — une seule animation d'auteur (`zoominimg 40s`), aucun hover mesurable sur les tuiles, ni transition de page ni reveal ; reduced-motion sans effet (4 éléments animés + vidéo autoplay conservés).
- **UX : 5/10** — mosaïques lisibles et BOOK persistant ; mais 4 clics pour une chambre, page rooms hétérogène, menu de 20 entrées, préloader bloquant observé, load 13 s sur rooms.
- **Conversion : 5/10** — moteur dans la charte avec conditions claires et prix moyen/nuit ; mais aucun prix, capacité ni avis sur le site, modale sans nombre de chambres, nouvel onglet, 404 hors charte, aucun bénéfice direct affiché.
- **Mobile : 4/10** — header opaque et tuiles lisibles, moteur mobile propre, tuiles 50vh sur La Corte ; mais BOOK 30 px, CTA 24 px, sous-titres 9 px avec zoom bloqué, 12 Mo d'images sur offers, load 13,9 s sur La Corte, anomalies de largeur sur 3 captures.

**Note globale : 5,5/10.** Identité forte et photographie de haut niveau (branding et DA portent le site) sur une exécution technique et ergonomique datée (stack 2018, 28–30 Mo par page, accessibilité et SEO non traités, mobile fragile). Le site vend l'univers, le moteur vend la chambre ; il manque entre les deux la page qui rend l'offre concrète.

---

## Observations clés à conserver pour la phase comparative

- Home = préloader gris `#888b8d` → vidéo fixe `2024_overview.mp4` (18,5 Mo transférés en 2 requêtes 206, autoplay muted, non loop, sans poster ni playsinline, SKIP 102×41) → grille 2×2 de tuiles 720×450 sous overlay `#2b241e` α 0,6 ; docHeight 1 016 px ; 94 mots ; 0 H1.
- Typo : Optima auto-hébergée ; H2 tuiles 25/30 px, 400, capitales, ls 3 px ; H1 sous-pages 16 px ; paragraphes 13/19,5 px graisse 300 en `#b0a392` (2,47:1) ou `#888b8d` (3,43:1) ; corps 14/21 ; méta 9 px ; menu 22 px desktop / 17 px mobile.
- Layout : Bootstrap 4.1.3 `row no-gutters` ; 2×720 (home), 3×480 (rooms), `col-md-4`/`col-md-3` + `vh50` (La Corte), texte 483 px + photo 542×900 (spa/overview) ; rayon 0 ; container 1 140 ; header fixe transparent 64 px (mobile 54 px opaque `#888b8d`).
- Réservation : onglet BOOK fixe 46×140 (mobile 30×140) → modale brune (check-in/out, adultes 1–10, enfants 0–10, bouton ≈506×50) → booking.borgoegnazia.com en nouvel onglet ; 880 € (advance purchase) / 980 € (BAR, annulation J-7) / 1 180 € (demi-pension) → 3 780 € « avg price per night » ; badges « Last room left » ; 404 hors charte sans `#/`.
- Profondeur : home → /rooms/ (6 tuiles, 3 hébergements) → /rooms/la-corte/ (7 tuiles 50vh, dont OVERVIEW en aplat `#362f29`) → moteur ; aucun prix, surface, capacité sur le site.
- Menu : checkbox-hack, 20 entrées dont 11 externes, non ouvrable par script ; URL dupliquées `/?section=`.
- Animations : `zoominimg 40s ease` (unique animation d'auteur), WOW `fadeIn 1s`, spinner 1,4 s, transitions Bootstrap 0,15 s ×36 ; 0 hover sur tuiles ; 0 parallaxe / sticky / transition de page ; reduced-motion inopérant.
- Réseau : home 179 req / 28,4 Mo ; offers 154 req / 30,1 Mo (JPEG 6,27 + 5,47 Mo ×2) ; experiences 18 Mo ; contact 224 req / 99 scripts ; 73 scripts, 28 CSS, 495 Ko de CSS ; 0 lazy, 0 srcset.
- Temps : TTFB 127–458 ms ; FCP 356–1 532 ms ; load 3,8 s (home), 13,2 s (rooms), 13,9 s (La Corte mobile), ≈1 s (awards, overview).
- A11y : `outline:none` ×42–47, alt manquants 9–12/page, 4 liens sans nom, formulaire 7 champs sans label, `maximum-scale=1`, 13 textes < 12 px, skip link home seulement.
- SEO : `<title>` identique partout, description vide, og en italien, pas de canonical/hreflang, JSON-LD `WebSite` seul, H1 absent sur 5 pages/10.
- Preuve : Awards 754 mots (Michelin 2 clés, 50 Best n°63, T+L, CN Traveler, GSTC…) ; 7 logos blancs 40 px en footer ; aucun avis ni note ni bénéfice direct.
- Tiers hors charte : bannière iubenda ≈448×340 (mobile ≈66 % de l'écran), widget « Your Privacy Choices » blanc/bleu, bouton vert 38×38 ; anomalie de largeur (1 085/1 440 ; 205/390) sur 8 captures, hypothèse widget, non vérifiée.
- Vidéos de tuile : 5 mp4 de 1,1 à 3,95 Mo en loop, non muted, `preload=metadata` ; 2 « vidéos » sont des images dans `<video>`.
- Mobile : tuiles 100vh (home ≈1 926 px) ou 50vh (La Corte ≈3 190 px), awards 8 467 px ; H2 25 px inchangés ; CTA menu 24 px de haut ; moteur ≈16 000 px CSS.
