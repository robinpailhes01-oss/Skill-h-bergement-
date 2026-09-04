# Fiche d'audit — Hotel Odisej, Mljet (Adriatic Luxury Hotels)

Clé : `odisej` · Analyse du 2026-09-04 · Chromium headless via Playwright, 1440×900 (desktop) et 390×844 DPR 2 (mobile). Série 2 « au-delà du quiet luxury » : site primé (CSS Design Awards) retenu pour le storytelling naturel, la couleur, le scroll et la présentation des chambres.

---

## 0. En-tête

**Nom** : Hotel Odisej Mljet (Pomena 16, 20226 Pomena, Croatie), hôtel du groupe Adriatic Luxury Hotels (ALH, Dubrovnik). **URL de départ** : https://hotelodisej.com/. Title : « Hotel Odisej - Mljet Island Hotel ». Site conçu par Bornfight Studio (crédit en footer), thème WordPress `alh-hotel-odisej-web-2023`, WPML 4.9.4 (version croate `/hr/`).

### Pages étudiées

| Label | URL | Desktop | Mobile |
|---|---|---|---|
| home | https://hotelodisej.com/ | oui (3 passes : initiale, scroll, sonde réservation) | oui |
| rooms (page unique, 5 catégories en accordéon) | https://hotelodisej.com/rooms/ | oui | oui |
| experiences / destination (« Discover Mljet ») | https://hotelodisej.com/mljet/ | oui (2 passes) | non |
| dining | https://hotelodisej.com/dining/ | oui | non |
| spa (« Wellness ») | https://hotelodisej.com/wellness/ | oui | non |
| contact | https://hotelodisej.com/contact-us/ | oui | non |
| booking (sonde « Book now ») | https://www.book-secure.com/index.php?s=results&group=wrensgroup&property=hrisl24139&… | ouvert, bloqué par un interstitiel captcha | non |
| room-detail | inexistant : aucune URL de chambre individuelle dans les liens internes | — | — |

### Limites de l'observation

- **Menu hamburger non capturé** : `home-05-menu-open` et `home-mobile-05-menu-open` sont identiques aux captures hero (le clic sur le bouton 40×22 px sans libellé n'a pas ouvert l'overlay). Contenu connu par le DOM (7 liens), rendu et animation inconnus.
- **Moteur non observable** : book-secure.com renvoie « Verification Required » (iframe `geo.captcha-delivery.com`, slider anti-bot). Aucun champ, prix ou étape vus ; aucune réservation tentée.
- **Révélations au scroll** : les captures `02-full` montrent des zones vides ou des textes à opacité partielle (67 éléments `reveal` sur la home non déclenchés d'un coup) ; les captures `03-scrollN` donnent les états rendus, le DOM donne hauteurs et couleurs.
- Aucune balise `<video>` sur les 7 pages : caractéristique du site, pas limite d'outil.
- Non mesurables : transitions de page (conteneur `o-barba-container`), LCP (`null`), Lighthouse, curseur tactile, zoom réel de l'image de hero des sous-pages, rendu mobile de dining / wellness / mljet / contact.

---

## 1. Positionnement de marque

**Faits observés**
- Meta description home : « Your hotel sanctuary located on Mljet Island in the vicinty of Mljet National Park » (coquille « vicinty » sur 2 pages). Aucun H1 sur la home ; premier statement en 80 px : situation dans la forêt de pins et chênes du parc national, « just two hours by passenger or car ferry from Dubrovnik ».
- H1 des sous-pages : « Sweeping view of the Adriatic in your Room », « An island where nature remains utterly unspoilt », « Wellness Treatments for Mind and Body », « Dining options with regional specialities », « Get in touch with us to discover secret of Mljet » (contact, faute).
- Menu (DOM) : Rooms & Suites · Dining Options · Wellness · Contact · Discover Mljet + Croatian + socials du groupe (facebook.com/ALHhotels, instagram.com/adriaticluxuryhotels). Les deux articles « Beyond the hotel » renvoient au blog adriaticluxuryhotels.com.
- Logo lion ALH en footer (lien vers le site groupe), mention « ALH GROUP MEDIA ». Wellness opéré sous la marque « Energy Clinic ».
- Page Mljet : « Time magazine once named Mljet as one of the 10 most beautiful islands in the world », « the green island », légende d'Ulysse et de Calypso, église du XIIᵉ siècle.
- Rooms : 5 catégories (Classic, Superior, Deluxe, Family, Executive Suite) ; équipements « Satellite TV », « Free wifi in the lobby », « Safety deposit box at the front desk » ; services « Currency exchange », « Souvenir & gift shop ». Aucun prix, aucune surface.
- Dining : 4 points de vente avec horaires saisonniers « 10:00 – 23:00 (May–September) ».

**Interprétation**
- Architecture de marque : ALH quasi invisible (logo footer, socials, blog, check-in, moteur) ; site mono-hôtel qui parle d'abord de l'île. Hiérarchie de la home : lieu → chambres → table → bien-être → parc → culture → réservation. L'hôtel est la porte d'entrée d'un parc national, pas un objet de design.
- Gamme perçue : villégiature 4* dans le discours (« sanctuary »), mais l'inventaire (wifi au lobby, coffre à la réception, mobilier des années 2000 sur les photos Superior) situe l'offre en milieu de gamme balnéaire. Le site vend au-dessus de ce que montrent ses photos de chambres.
- Cible : familles et couples européens en été, plaisanciers (marina de Pomena, voiliers), randonneurs/cyclistes ; version croate pour le marché domestique.
- Territoire émotionnel : nature méditerranéenne saturée (olive des pins, bleu nuit de l'Adriatique), mythologie, lenteur insulaire (« silent solitude of the wild »). Personnalité chaleureuse, illustrative (blobs, vagues), plus « guide de l'île » que « manifeste ».
- Différence avec un site hôtelier générique : couleurs pleines et vagues au lieu de fonds blancs ; chambres en liste-accordéon numérotée au lieu de cartes ; contenu d'île (légende, église, ânes, lacs) plus long que le contenu hôtel. Le site vend un séjour dans le parc ; la chambre est « un balcon sur l'Adriatique ».
- Cohérence forte entre couleurs, mots et photos de paysage ; faible entre le ton (« mesmerising ») et les intérieurs datés / l'inventaire listé.

**Enseignements réutilisables** : faire porter l'identité par le lieu (palette du paysage, rubrique destination aussi longue que les chambres) ; ne pas laisser l'écart texte/photos de chambres ouvrir un doute ; donner au moins un fait par catégorie (vue, balcon, capacité).

---

## 2. Première impression (5 premières secondes)

**Faits observés**
- `home-00-initial` : pas de préloader visible (un `<svg>` fixe plein écran z-index 20 existe — hypothèse : calque de transition de page). Pas de bannière cookies dans le viewport initial ; la sonde a cliqué « Accept all » (CookieYes). Un bouton flottant bleu #0056a7 de 45×45 px (« Revisit consent ») reste fixé en bas à gauche sur toutes les pages, seul élément hors palette.
- `home-01-hero` : photo aérienne 1920×1280 (470 Ko) en `cover` sur 1440×900, baie de Pomena, hôtel blanc aux toits orange, lumière de fin d'après-midi. Logotype « Hotel Odisej / MLJET » centré en haut (PP Woodland, #434b34, ≈ 60 px) sur le ciel. Hamburger à gauche (x=60), deux pills à droite : « Online Check-in » 157×36 contour #d4d4b9, « Book now » 109×36 plein #5b6647 texte #f7f7ee. Header fixe 90 px transparent. Aucun titre, aucune date, aucun prix dans le premier écran.
- Mobile : même photo recadrée en portrait 390×844 à partir d'un fichier 600×400 (flou visible), logo sur 2 lignes, « Book now » seul en haut à droite, header 80 px.

**Interprétation**
- Ce que l'on comprend en 5 s : « un hôtel dans une baie boisée, accessible par la mer ». Le nom fait office de titre ; la photo raconte. Cohérent avec un site qui vend un lieu, au prix d'un H1 et d'un message.
- Premier CTA immédiat et double (check-in pour les clients, réservation pour les prospects) : site pensé aussi comme outil opérationnel du groupe.
- Distractions : le bouton cookie bleu, le flou du hero mobile.
- Raison de continuer : dès 936 px de scroll le fond devient olive plein #5b6647, ce qui installe une attente de « chapitres ».

**Enseignements réutilisables** : un hero « image + logotype + 2 pills » suffit si la photo est une carte (hôtel, mer, port visibles) ; prévoir un cadrage portrait dédié pour mobile ; re-styler le rappel cookies.

---

## 3. Direction artistique

**Faits observés**
- Fonds (occurrences DOM home) : #f7f7ee crème (2 155), #5b6647 olive (388), #03364f bleu nuit (333). Textes : #e3e3c4 crème chaud (61), #434b34 vert foncé (50), #2e3323 (paragraphes), #043f5d (titre dining), #000. Contact ajoute #e5e3df (carte Google).
- Typographies : PP Woodland Regular (woff2 auto-hébergé ; fonderie Pangram Pangram — hypothèse de licence commerciale), DM Sans 400/500 (auto-hébergé). Contact charge Roboto via Google Maps.
- Échelle desktop : H1/H2/statements 80 px / 88 px, interlettrage −2,4 px (−3 %), casse normale ; H3 40/48, −1,2 px ; « Get back to nature » 60/66 ; sous-titres DM Sans 26/31,2, −0,78 px ; corps 16/20,8 ; libellés de liens ≈ 26 px. Mobile : 80 → 40/46 (−1,2 px), 40 → 30/36, 60 → 36 ; corps inchangé.
- Grille : marges 60 px à 1440 (contenu 1 320 px), colonnes de texte 834 px (`containerWidths`), textes de chambre ≈ 300 px à gauche, galeries sur 2/3 à droite ; statements centrés sur 665–720 px.
- Composants : pills `border-radius: 999px` 36 px de haut, padding 0 20 px ; pastilles numérotées « 01 »–« 05 » (≈ 60×24, fond #5b6647) ; tags d'attributs pill (« Sea View », « Balcony », « FACIAL », horaires) sur #e3e3c4 ou bleu translucide ; lignes d'accordéon bordées 1 px #d4d4b9, rayon ≈ 12 px ; images à coins ≈ 12–16 px ; grilles d'équipements en cellules bordées 1 px translucide, 7 colonnes desktop / 3 mobile.
- Formes : séparateurs en vague SVG double (bande #e3e3c4 puis couleur suivante) ; blobs organiques ton sur ton dans les fonds pleins et le footer ; dégradés doux d'olive sur la section équipements.
- Iconographie quasi nulle (flèche → dans les pills, hamburger, lion ALH) ; aucune icône d'équipement.
- Photos : hero 1,6 ; galeries 4:3 et 1,78 ; carrés 340/540 px ; portraits 0,75 ; pleine largeur 1440×972 (1,48). Fichiers 800 à 2880 px (`bf-advanced-images`), JPEG.
- Vide : sections pleine couleur de 900 à 1 400 px n'accueillant qu'un statement centré.

**Interprétation**
- Palette tri-tonale « paysage » (pierre, pins, mer) sans accent chaud — l'orange des toits n'est jamais repris. Le crème chaud #e3e3c4 sert de « blanc » sur fonds sombres et de bande de vague : c'est le liant.
- PP Woodland (empattements arrondis, contreformes larges) apporte la rondeur « nature » ; DM Sans fait le service. Rapport 80/40/26/16 franc, interlettrage négatif marqué.
- Grille classique ; l'asymétrie vient des galeries (grande image droite, petite bas gauche, portrait) et des blobs. Coins arrondis partout et vagues : DA « douce », proche de l'illustration, à l'opposé des angles droits du quiet luxury.
- Cohérence élevée sur 6 pages. Faiblesses : grilles sans icônes, bouton cookie bleu, titres ton sur ton avant révélation.

### Tokens approximatifs

| Token | Valeur |
|---|---|
| bg-base / bg-forest / bg-sea | #f7f7ee / #5b6647 / #03364f |
| text-dark / text-body / text-cream | #434b34 / #2e3323 / #e3e3c4 |
| accent-sea-title / border-soft | #043f5d / #d4d4b9 |
| font-display / font-text | PP Woodland 400 / DM Sans 400–500 |
| display / h3 / lead / body | 80/88 −2,4 px · 40/48 −1,2 px · 26/31,2 −0,78 px · 16/20,8 |
| mobile display / h3 | 40/46 −1,2 px · 30/36 −0,9 px |
| radius pill / card / img | 999 px / ≈ 12 px / ≈ 12–16 px |
| header desktop / mobile | 90 px / 80 px |
| button primary / secondary | 109×36 #5b6647→#434b34 · 157×36 contour #d4d4b9→fond #e3e3c4 |
| container / text column | 1 320 px / 834 px |
| easing UI / surfaces | cubic-bezier(.55,.085,.68,.53) 0,2 s · cubic-bezier(.19,1,.22,1) 1 s |

**Enseignements réutilisables** : 3 couleurs du paysage + 1 crème de liaison ; serif ronde réservée aux 80 px ; rayons unifiés ; les vagues SVG rythment des sections pleines à peu de frais.

---

## 4. Architecture de la page d'accueil

Reconstruction d'après `home-02-full` (14 967 px desktop, 11 189 px mobile), paliers de scroll et captures `03-scrollN`. Hauteurs approximatives.

| Position | Section | Objectif | Contenu | Interaction | CTA | Émotion créée |
|---|---|---|---|---|---|---|
| 0–900 | Hero aérien | Situer | Photo baie, logotype, nav | Header transparent → barre crème `has-scrolled` | Online Check-in, Book now | Reconnaissance |
| 900–2 300 | Statement olive | Poser la promesse | 1 phrase 80 px crème (forêt, parc, 2 h de ferry), blobs, vague | Text fill au scroll (18 transforms à y=936) | — | Immersion |
| 2 300–4 700 | Chambres (crème) | Ouvrir l'offre | H2 « Sweeping view… », paragraphe 300 px + « Explore Rooms → », galerie 3 images asymétrique, accordéon 5 lignes 01–05, slider 1/3 | Hover ligne : fond olive 1 s ; slider Swiper | Explore Rooms, lignes | Curiosité |
| 4 700–7 300 | Restauration (bleu nuit) | Élargir le séjour | H2 ton sur ton, 3 outlets (photo 4:3 + H3 crème + texte), « Dining locations → » | Reveals | Dining locations | Appétit |
| 7 300–9 000 | Statement bien-être (crème) | Respirer | « Surrender yourself… » 80 px, H2 « Relaxing treatments » entre piscine ronde et visage dans l'eau | Text fill, reveals | — | Détente |
| 9 000–11 200 | Parc national (photo + olive) | Vendre la destination | Lac au crépuscule 1440×972, vague, H2 « Oak tree forest… », 2 photos (archipel, âne), « Discover Mljet → » | Reveals, parallaxe | Discover Mljet | Émerveillement |
| 11 200–13 200 | Beyond the hotel (crème) | Profondeur | 2 articles (« A Bead in My Palm », « The Island of Ulysses ») photo + H3 + 3 lignes + « Read More → » (blog ALH) | Reveals | Read More (externe) | Culture |
| 13 200–14 200 | « Get back to nature » | Convertir | Carte olive translucide 1 320 px sur photo du lac, H2 60 px, « Book your stay → » | — | Book your stay → book-secure | Décision |
| 14 200–14 967 | Footer bleu nuit | Rassurer | Logo, lion ALH, adresse, e-mail, téléphone, socials, légal, crédits | — | mail / tel | Sérieux |

**Logique narrative** : arrivée par la mer → promesse d'isolement → l'offre devient concrète tôt (chambres dès 2 300 px) mais sans prix → élargissement (table, spa) → l'île comme argument principal → la seule preuve est éditoriale (Time, sur la page Mljet, pas sur la home) → réservation en fin de page. Aucun bloc avis, distinction ou offre.

**Interprétation** : brochure en 7 chapitres colorés (crème / olive / crème / bleu / crème / olive / crème / bleu) : la progression se lit sans lire. Mobile : même ordre, statements en 40 px sur ≈ 9 lignes, slider et accordéon conservés.

**Enseignements réutilisables** : alterner fond plein / crème par chapitre ; un statement de 80 px entre deux blocs d'offre ; finir par une carte de réservation posée sur la meilleure photo.

---

## 5. Scroll et storytelling

**Faits observés**
- `animAttrs` : home 67 `reveal`, 4 `parallax`, 3 `horizontal`, 0 sticky ; rooms 69 / 2 / 1 / 1 sticky ; dining 51 / 4 / 1 / 1 ; wellness 53 / 2 / 1 / 1 ; mljet 34 / 2 / 1 / 1 ; contact 34 / 4 / 1 / 0.
- Paliers home desktop (pas 936 px) : transforms en cours 18, 8, 8, 15, 8, 11, 6, 14, 2, 8, 6, 5, 10, 5 ; opacités partielles jusqu'à 9 (y=12 164). Mobile : 22, 8, 14, 9, 5, 17, 10, 6, 6, 2. Fond central : crème → olive (936) → crème → bleu (5 614–6 550) → crème → olive (10 293) → crème → bleu (footer).
- Deux copies de chaque statement dans le DOM : « Set within… » en #434b34 (665 px) et #e3e3c4 (720 px) ; « Surrender yourself… » en #e3e3c4 (714) et #434b34 (720). `home-03-scroll3` montre la phrase crème pâle sur crème (non révélée) ; `rooms-03-scroll5` la montre vert foncé (révélée) ; `destination-03-scroll4` montre « Oak tree forest… » crème sur olive alors que le DOM le donne #434b34.
- CSS : 0 `position: sticky`, 0 `scroll-timeline`, 0 `will-change`, 0 `clip-path` ; 7 règles `scroll-snap` (Swiper).
- Hero des sous-pages : H1 80 px puis image 499×281 px (35 % de largeur) centrée à y=474, suivie de ≈ 1 000 px de vide avant le contenu (idem mobile, image 190×340).
- Vagues SVG à chaque changement de fond ; photo du lac 1440×972 utilisée 2 fois par page.

**Interprétation par effet et fonction**
- *Changement de fond par chapitre* : rythme + marque ; c'est l'outil narratif principal, il remplace la vidéo.
- *Text fill au scroll* (deux couches, la couche contrastée se découvre) : orienter le regard et ralentir la lecture. Hypothèse technique : masque piloté en JS (pas de clip-path CSS). Risque : texte invisible tant que l'on ne scrolle pas (crème sur crème = 1,21).
- *Zoom de l'image de hero des sous-pages* : image petite au chargement, espace réservé ; hypothèse : agrandissement jusqu'à 1 320 px pendant le scroll (1 élément `sticky`, lien `js-focus-shifting-item is-active`). Fonction : transition d'échelle. Non vérifiable.
- *Reveals* (translation + fondu) sur titres, images, cartes, lignes : 6 à 22 éléments en mouvement par palier, la page « s'assemble » en continu. Fonction : rythme. Risque : contenu invisible en navigation rapide ou sans JS.
- *Parallaxe* (4 éléments) : hypothèse blobs et photo pleine largeur ; profondeur faible.
- *Horizontal* : le slider de galerie « 1 / 3 » (Swiper), pas de section pinnée.
- *Densité* : 1 400–2 400 px par section pour 1 titre et 2–3 paragraphes ; respirations très longues (1 400 px pour 24 mots) ; envie de poursuivre soutenue par la vague qui annonce la couleur suivante.

**Enseignements réutilisables** : un text fill sur une phrase de 20–30 mots en 80 px est un effet à fort impact et peu coûteux ; l'annoncer par une vague ; garder ≈ 10 éléments animés par écran ; prévoir un état final lisible sans JS.

---

## 6. Animations et micro-interactions

Durées (`transitionDurations`) : 0,2 s ×43, 1 s ×30, 0,15 s ×4, 0,6 s ×3, 0,3 s ×2. Easings de la feuille de style : (.55,.085,.68,.53) = easeInQuad ×16 ; (.19,1,.22,1) = easeOutExpo ×12 ; (.39,.575,.565,1) = easeOutSine ×8 ; (.25,.46,.45,.94) = easeOutQuad ×6 ; 7 `@keyframes`. Reveals pilotés en JS (vendor.js 377 Ko + bundle.js) : durées = hypothèses.

| Animation | Déclencheur | Élément | Effet | Fonction | Risque UX |
|---|---|---|---|---|---|
| Arrivée / transition de page | chargement, navigation | `<svg>` fixe z=20, `o-barba-container` | Hypothèse : rideau Barba.js (nom de classe, non mesuré) | Continuité | Délai perçu si présent |
| Header au scroll | scroll > hero | `nav` 90 px | Transparent → barre crème, logo réduit centré, hamburger #5b6647 (`.has-scrolled`) | Orientation, CTA persistant | Aucun |
| Reveal | entrée viewport | 67 `reveal` | Translation + fondu ; hypothèse 0,6–1 s easeOutExpo | Rythme | Contenu invisible avant scroll |
| Text fill | progression scroll | statements 80 px | Découvrement de la couche contrastée | Orienter le regard | Contraste 1,21 avant révélation |
| Zoom hero sous-pages | scroll | image 499×281 | Hypothèse : scale jusqu'à 1 320 px | Émotion | ≈ 1 000 px de vide sans JS |
| Hover bouton primaire | survol | « Book now » | #5b6647 → #434b34, 0,2 s easeInQuad | Feedback | Variation faible |
| Hover bouton secondaire | survol | « Online Check-in » | fond → #e3e3c4, bordure #d4d4b9 → #e3e3c4, texte → #5b6647 | Feedback | Aucun |
| Hover ligne d'accordéon | survol | `c-link-list-big__link` | fond → rgba(91,102,71,.996) en 1 s easeOutExpo, barre verticale gauche, texte crème | Sélection | Traînée visuelle en balayant la liste |
| Accordéon chambres | clic | lignes 01–05 | Hypothèse : ancre vers le bloc chambre (aucune URL de détail) | Navigation intra-page | Non vérifié |
| Slider galerie | clic flèches | Swiper « 1 / 3 » | Défilement, `scroll-snap` | Exploration | Indicateur discret |
| Hamburger | clic | bouton 40×22 sans nom | Overlay non capturé ; opacité/filter 0,15 s linéaire | Navigation | Pas de nom accessible |
| Reduced motion | `prefers-reduced-motion` | `*` | `animation-duration: 0s`, `transition-duration: 0s`, `scroll-behavior: auto` | Accessibilité | Ne couvre pas les transforms JS (hypothèse) |
| Curseur, préloader, vidéo, marquee, split-text | — | — | Absents (`customCursor` none, aucune vidéo) | — | — |

**Interprétation** : vocabulaire réduit à trois gestes (reveal, text fill, fond qui change) et deux hovers. L'easeOutExpo 1 s sur le fond des lignes est le geste signature ; le reste est standard. Pas de curseur, pas de vidéo : le site tient par la couleur et le rythme.

**Enseignements réutilisables** : deux easings (rapide pour l'UI, long expo pour les surfaces) ; hover de surface plus lisible qu'un hover de texte sur des listes ; neutraliser aussi les transforms JS sous reduced motion.

---

## 7. Navigation et architecture de l'information

**Faits observés**
- Header fixe 90 px (80 mobile), transparent puis crème. Hamburger (gauche), logo centré après scroll, « Online Check-in » + « Book now » (droite). Mobile : hamburger + « Book now » seulement.
- Menu (DOM) : Rooms & Suites, Dining Options, Wellness, Contact, Discover Mljet, Croatian, socials. Pas de page Offres, Galerie, À propos, Groupe, Événements.
- Chambres : home → « Explore Rooms » ou ligne d'accordéon → `/rooms/` (1 clic), détail sur la même page (ancres), moteur externe au clic suivant. 2 clics jusqu'au moteur.
- Infos essentielles : adresse, +385 20 300 300 (réservations), +385 20 362 111 (hôtel), e-mails en footer ; « How to get here » (ferry depuis Dubrovnik) et codes GDS sur contact ; horaires sur dining ; brochure Wellness PDF 2025.
- Réservation persistante : « Book now » dans le header fixe partout, desktop et mobile ; « Book your stay » en pré-footer de chaque page (y=11 375 rooms, 8 704 mljet, 9 252 dining, 9 048 wellness, 6 294 contact).
- 2 liens image sans nom, 2 boutons sans nom (hamburger, cookie), pas de `<main>`, pas de skip link.

**Interprétation** : IA très plate (5 rubriques), adaptée à un hôtel saisonnier ; trouver une chambre est facile, trouver un prix impossible sans quitter le site. Frustrations : titres WordPress par défaut (« Rooms Archive - Hotel Odisej »), sorties non annoncées vers le blog ALH, check-in retiré du header mobile, menu non vérifié.

**Enseignements réutilisables** : header à 3 zones lisible à 390 px si l'on ne garde qu'un pill ; répéter le CTA en pré-footer ; ne pas laisser les titres d'archive en production.

---

## 8. Parcours de réservation et conversion

**Faits observés**
- Type : moteur transactionnel externe **book-secure.com** (groupe « wrensgroup », `property=hrisl24139`, `Hotelnames=HREXCHTLOdisej`), en nouvel onglet (`_blank`) depuis « Book now » et « Book your stay ».
- L'URL contient des dates codées en dur : `arrival=2023-04-25&departure=2023-04-26&adults1=1&children1=0&locale=en_GB&currency=EUR` — plus de trois ans avant l'audit.
- Aucun sélecteur de dates, champ voyageurs ou formulaire sur les 7 pages (`forms []`, `dateInputs []`). Aucun prix, « à partir de », inclusion, acompte, politique d'annulation, offre, avantage direct, avis, note ou label.
- Contact humain : téléphone et e-mail en footer et sur contact (4 cartes : Hotel Address, Hotel Contact, Reservations, Sales) ; « Contact our Wellness » ; pas de chat.
- Sonde : « Verification Required » (DataDome) — `home-06-booking-step1` et `booking-06-booking-step1` identiques, aucune étape 1 visible.
- Découvrir vs réserver : liens texte + flèche pill (« Explore Rooms », « Dining locations », « Discover Mljet », « Read More ») vs pill pleine. Pas de « demander / devis ».
- Réassurance B2B : « Online Check-in » (pay.adriaticluxuryhotels.com), codes GDS.

**Interprétation** : vitrine, commerce entièrement délégué. Le prospect ne peut vérifier ni disponibilité ni prix sans changer de domaine et affronter un anti-bot ; les dates 2023 sont une dette de maintenance visible. Aucune preuve n'est affichée alors que le site a un prix de design et l'île une citation Time. Ruptures : domaine, nouvel onglet, perte totale de l'identité (page blanche Roboto), interstitiel.

**Enseignements réutilisables** : même avec un moteur externe, exposer dates + voyageurs et générer l'URL dynamiquement ; « à partir de » par catégorie ; centraliser la preuve dans le pré-footer.

---

## 9. Pages chambres

**Objet vendu** : une nuit dans l'une de 5 catégories, sur la page unique `/rooms/` (« Rooms Archive », type archive WordPress). Aucune page de détail.

**Faits observés (desktop, 12 296 px)**
1. Hero crème : H1 80 px, image balcon 499×281 (table blanche, jus d'orange, voilier), espace réservé.
2. Accordéon 5 lignes bordées 1 320 px : H3 40 px + 1 phrase + pastille 01–05 (Classic « Comfortable rooms with impressive views », Superior « sea views… centrepiece », Deluxe « beyond the trees, a mesmerising view », Family « balcony facing the sea or the lush parkland », Executive Suite « sweeping views… private balcony »). Hover : fond olive 1 s.
3. Vague → bleu nuit (y≈3 000–5 700) : Classic (tag « With or without balcony » ; deux variantes décrites), Superior (« Sea View » ; « white walls, tiled floor, cool hued furnishings »), Deluxe (« Balcony » + « Sea View » ; « whitewashed balcony furnished with a table and chairs ») ; chacun H3 crème, paragraphe 5–8 lignes, galerie 3 photos 4:3 (351×263, 475×356, 536×402 ; fichiers 800–960 px).
4. Olive (y≈5 700–7 300) : « Room Amenities » 9 cellules (Ensuite bathrooms with shower, Mini bar, Satellite TV, Air conditioning, Direct telephone line, Free wifi in the lobby, Hairdryer, Safety deposit box at the front desk, Laundry service) ; « Suite highlights » 4 (Balcony, Sea view, Separate living and dining space, Two bedrooms) ; « Hotel Services » 5 (Car, scooter & bicycle rental ; Currency exchange ; Excursions available ; Souvenir & gift shop ; Transfers).
5. Crème : Family Room (Balcony, Park view, Sea View ; « comfortably sleeps four » ; lits jumeaux bleus + balcon), Executive Suite (Balcony, Sea View ; « two Executive suites… two light filled, ensuite bedrooms… al fresco meal »).
6. Statement « Surrender yourself… », « Relaxing treatments » (2 photos + paragraphe), photo du lac, carte « Get back to nature » + « Book your stay → », footer.
- Absents : m², capacité (sauf Family), prix, disponibilité, plan, type de lit, nombre par catégorie (sauf 2 suites), politique enfants, comparaison, suggestions.
- Ordre : promesse → liste → description sensorielle → galerie → équipements communs → services → suites → spa → réservation. Pas de CTA de réservation par chambre.

**Mobile (`rooms-mobile-02-full`, 10 315 px)** : H1 40 px sur 3 lignes, image hero 190×340 portrait, ≈ 700 px réservés, accordéon avec H3 30 px, 1 phrase et bouton flèche pill 109×48 (titres sur 2 lignes pour Superior/Executive), blocs bleu/olive/crème empilés (texte 16 px sur 358 px, galeries en colonne), grilles 3 colonnes (cellules ≈ 115×230 px pour 2 mots), « Book your stay » 203×26.

**Interprétation** : « une page, cinq chambres » convient à 5 catégories proches ; l'accordéon numéroté sert de sommaire et la couleur de fond groupe les catégories (bleu = Classic/Superior/Deluxe, crème = Family/Suite). Récit sensoriel réussi, mais sans faits structurants il faut sortir vers le moteur pour tout. Projection assurée par la photo du balcon (utilisée 3 fois), affaiblie par les intérieurs datés plein cadre. « Wifi au lobby » et « coffre à la réception » jouent contre « sanctuary ».

**Enseignements réutilisables** : garder l'accordéon-sommaire, ajouter par catégorie 3 faits (m², occupation, lit), un « à partir de » et un CTA pré-filtré ; ne montrer les intérieurs qu'au niveau des extérieurs.

---

## 10. Copywriting

**Faits observés**
- Volume indexable faible : 174 mots home, 101 rooms, 28 dining, 62 wellness, 88 mljet, 52 contact (`wordCount`) ; paragraphes de 40–70 mots.
- Structures : statements de 20–30 mots en 80 px (« Set within the verdant pine and oak tree forest… », « Surrender yourself to the silent solitude of the wild… ») ; H2 de 3 à 6 mots (« Relaxing treatments », « Beyond the hotel », « Get back to nature ») ; titres de page en promesse spatiale.
- Champ lexical : nature (pine, oak, forest, lakes, wild, untamed, green island), mer (Adriatic, sea view, marina, crystal-clear), calme (silent solitude, tranquil, calming connection), mythe (Ulysses, Calypso), table régionale (regional seafood specialities, gelato).
- Sensoriel : « breathe in the pure Mediterranean air », « soak up the sun over an al fresco meal », « gently shaded waterfront ». Superlatifs : « mesmerising », « glorious sweeping views », « picture perfect », « sublime ».
- CTA : verbes d'exploration (« Explore Rooms », « Discover Mljet », « Dining locations », « Read More ») ; réservation « Book now » / « Book your stay ».
- Faits techniques relégués aux grilles et pills (équipements, horaires « 07:00 - 10:00 (BREAKFAST) 19:00 - 21:00 », codes GDS).
- Coquilles : « vicinty » ×2, « discover secret of Mljet », « Developement », « A glorious sweeping views ».

**Interprétation** : ton de guide de voyage bienveillant, adresse directe (« your Room », « Surrender yourself »), phrases longues. Le luxe n'est jamais nommé (seulement dans le nom du groupe), il est suggéré par « sanctuary » et les vues. Mécanismes : titre = vue + lieu ; statement = position + temps d'accès ; chaque chambre/outlet = 1 phrase de vue + 1 phrase de matière ; preuve externe et mythe ancrent la destination ; caractéristiques sorties du récit. Faiblesse : superlatifs non soutenus par des faits, coquilles sur un site primé.

**Enseignements réutilisables** : statement géographique concret plutôt que manifeste ; séparer récit et grille de faits ; relire.

---

## 11. Photographie et vidéo

**Faits observés**
- Aucune vidéo. 28 images home, 27 rooms, 20 dining, 12 wellness, 11 mljet ; contact 81 (68 tuiles Google Maps sans alt).
- Plans : aérien (baie, archipel, lac au crépuscule), balcon avec table dressée, intérieurs grand angle (bois miel, terre cuite, rideaux bleus, lits jumeaux bleus), terrasses (nappes blanches, rotin, lanternes), piscine ronde carrelée, femme flottant dans l'eau (banque d'image — hypothèse), massage N&B (Energy Clinic), âne derrière une grille, collier sur une épaule.
- Lumière dorée (hero, lac), midi saturé (archipel), naturelle en intérieur. Couleurs = palette du site (pins, eau, façades blanches, toits orange).
- Présence humaine ≈ 3 images, aucun client, aucun staff, aucune scène de restaurant occupé.
- Ratios 1,6 / 1,78 / 1,33 / 1 / 0,75 / 1,48 ; coins arrondis ; fichiers jusqu'à 2880 px (439 Ko) ; hero mobile 600×400 upscalé.
- Réutilisation : balcon ×3 (hero rooms, home, galerie), lac ×2 par page, piscine de l'Hotel Supetar à Cavtat (`ALH_Hotel_Supetar_Cavtat_Pool18`, autre hôtel ALH) sur home, mljet, wellness et contact.
- Proportion : ≈ 60 % destination, 30 % hôtel, 10 % bien-être, 0 % moments de vie.

**Interprétation** : la photographie fait le positionnement « île » — les extérieurs portent la couleur, les intérieurs tirent vers le bas. L'absence d'humains renforce la « silent solitude » mais prive des scènes que le texte promet (dîner en famille, vélo dans le parc). L'emprunt de visuels d'un autre hôtel est un risque de confiance.

**Shot list pour reproduire ce niveau (et combler les manques)**
1. Drone du site à l'heure dorée, 3:2 + recadrage 9:16 dédié mobile.
2. Drone du paysage protégé (lac, archipel) à midi, saturé.
3. Balcon de chambre avec table dressée, mer en fond, 4:3 et 3:4.
4. Par catégorie : 3 plans (large, lit + fenêtre, salle de bain), lumière naturelle, mobilier actuel.
5. Restaurant : terrasse au coucher du soleil, puis avec 2–4 convives ; 2 plats en macro.
6. Beach bar : lanternes, cocktails ; piscine/plage du site (pas d'un autre hôtel).
7. Soins : main, peau, serviette, lumière douce, 1:1.
8. Destination : faune, église, sentier, vélo, kayak, 3:4 ; une scène de vie par chapitre (famille sur le ponton, couple à vélo, baigneur à l'aube).
9. Facultatif : boucle vidéo 15 s (drone → balcon) pour ajouter ce que ce site n'a pas.

---

## 12. Mobile

**Faits observés (390×844)**
- Home 11 189 px (14 967 desktop), rooms 10 315 px. Header 80 px : hamburger + « Book now » 109×36 ; pas de check-in.
- Hero : fichier 600×400 en `cover` 390×844 → flou ; logo 2 lignes ≈ 50 px ; aucun texte.
- Titres : statements/H2 40 px / 46 px (−1,2 px), H3 30/36, « Get back to nature » 36 px ; corps 16/20,8 ; largeur de texte 333–358 px (marges 16 px). Un statement de 24 mots = 9 lignes ≈ 420 px.
- Animations conservées : reveals (22 transforms au premier palier, 5–17 ensuite), text fill, vagues, blobs, slider 1/3 (flèches 109×48), accordéon avec bouton flèche par ligne. Aucune simplification détectée.
- Cibles : « Book now » 109×36 (< 44 px de haut), flèches 109×48, lignes d'accordéon ≈ 358×150, « Book your stay » 203×26, liens footer 20 px de haut.
- Réservation identique (nouvel onglet, dates 2023) ; pas de barre sticky en bas.
- Vitesse : home 47 requêtes, 2 888 Ko (images 1 709, scripts 948), TTFB 981 ms, FCP 1 576 ms, load 1,9 s ; rooms 59 requêtes, 3 648 Ko (images 2 478), TTFB 2 505 ms, FCP 3 404 ms, load 5,6 s.
- Footer : logo + lion centrés, 3 lignes de contact, 2 colonnes de liens.

**Interprétation** : réduction fidèle (mêmes chapitres, effets, couleurs) ; les 40 px sont lisibles une fois révélés (4,67 à 8,5). Problèmes techniques : hero flou, CTA de 36 px, liens de 20 px, images 1200 px pour 390 px, TTFB jusqu'à 2,5 s. Différences : check-in retiré, accordéon à boutons, galeries empilées, grilles 3 colonnes trop hautes.

**Enseignements réutilisables** : hero portrait dédié ; 44 px minimum pour tout CTA ; liste 2 colonnes compacte au lieu des grilles ; variantes 400–800 px pour les galeries.

---

## 13. Performance, accessibilité, SEO

| Page (desktop) | Req. | Ko | TTFB | FCP | Load | Plus lourd |
|---|---|---|---|---|---|---|
| home | 84 | 5 914 (images 3 918 / scripts 1 533) | 1 035 ms | 3 116 ms | 3 782 ms | aérien 470 Ko, suite 2880 px 439 Ko, vendor.js 377 Ko |
| rooms | 73 | 3 467 | 1 165 ms | 2 220 ms | 2 353 ms | vendor.js 377 Ko, lac 248 Ko |
| dining | 74 | 4 053 | 1 016 ms | 1 852 ms | 1 914 ms | terrasse 389 Ko |
| wellness | 64 | 3 154 | 4 616 ms | 6 896 ms | 7 311 ms | piscine 327 Ko |
| mljet | 63 | 4 115 | 1 706–1 759 ms | 2 384–3 792 ms | 2 782–4 075 ms | jpeg 1920 px 740 Ko |
| contact | 148 | 6 413 | 788–863 ms | 1 272–1 612 ms | 2 513–3 045 ms | PNG 2 597 Ko + Google Maps 377 Ko (74 requêtes) |

**Faits observés**
- Images : 0 `srcset` partout ; lazy sur 3/28 (home), 0 ailleurs ; JPEG/PNG seulement ; alt techniques (« alh_odisej_exterior_aerial_07 », « classic-room-2 »).
- Scripts : vendor.js 377 Ko + bundle.js, GTM/GA4 167 Ko, CookieYes (18 requêtes), Cloudflare Insights ; 3 polices woff2 (147 Ko) ; CSS 146 693 octets, 11 media queries (352–1920 px).
- Stabilité : espace réservé sous les heros (pas de saut), mais reveals qui déplacent le contenu ; LCP non mesuré.
- Contrastes calculés : #434b34/#f7f7ee 8,5 ; #2e3323/#f7f7ee 12,1 ; #e3e3c4/#5b6647 4,67 (AA limite) ; #e3e3c4/#03364f 9,76 ; #5b6647/#e3e3c4 (bouton secondaire survolé) 4,67 ; avant révélation : #e3e3c4/#f7f7ee 1,21, #043f5d/#03364f 1,14, #434b34/#5b6647 1,5.
- Clavier : `focusOutlineNone` 54 (home), 47 (rooms), 69 (contact) ; `tabindex=-1` ×5 ; 0 skip link ; 0 `main` ; hamburger et bouton cookie sans nom ; 2 liens image sans nom ; iframe Maps sans `title`. Aucun formulaire.
- Reduced motion : 1 règle globale (`*{animation-duration:0s; transition-duration:0s; scroll-behavior:auto}`) ; capture `04-reduced-motion` identique au hero ; `animatedElements 0` — reveals JS non couverts (hypothèse).
- Structure : home **sans H1** ; sous-pages 1 H1 ; H2 « Get back to nature » et « Oak tree forest… » répétés sur chaque page ; H2 DM Sans 26 px utilisés comme paragraphes (mljet, wellness, contact).
- Métadonnées : title home correct ; « Rooms Archive - Hotel Odisej », « Dining - Hotel Odisej » ; description sur 4/6 pages (absente rooms, dining) ; og:image home seule ; canonical partout ; **aucun hreflang** malgré `/hr/` ; JSON-LD WebPage / CollectionPage sans `Hotel`, `LodgingBusiness` ni `Offer` ; robots index/follow.
- Contenu indexable : 28 à 174 mots par page.

**Interprétation** : l'immersion coûte peu en scripts (1,5 Mo dont un tiers d'analytics/cookies) et beaucoup en images non responsives ; serveur irrégulier (TTFB 0,8 à 4,6 s à la même heure). L'accessibilité est le point faible : clavier neutralisé, pas de H1 home, menu sans nom, contenu masqué par les reveals. SEO de « thème sur mesure sans plan » : pas de hreflang, pas de schéma hôtel, titres d'archive, textes courts.

**Enseignements réutilisables** : `srcset` + WebP + lazy sauf hero ; un H1 par page même discret ; hreflang dès 2 langues ; JSON-LD `Hotel` + `Offer` ; jamais d'`outline: none` sans focus de remplacement.

---

## 14. Conclusion

### 15 meilleurs éléments
1. Palette tri-tonale crème / olive / bleu nuit (#f7f7ee, #5b6647, #03364f) issue du paysage, tenue sur 6 pages.
2. Chapitrage de la home par fonds pleins alternés, annoncés par des vagues SVG bicolores.
3. Statements de 20–30 mots en PP Woodland 80/88 px (−2,4 px) centrés sur 720 px.
4. Text fill au scroll sur ces statements (deux couches de texte), effet signature sans librairie visible.
5. Accordéon-sommaire des 5 chambres numéroté 01–05, hover de surface olive 1 s easeOutExpo.
6. Groupement des catégories par couleur de fond (bleu = Classic/Superior/Deluxe, crème = Family/Suite).
7. Header 90 px transparent puis crème, deux pills persistantes, CTA visible partout y compris mobile.
8. Photo du balcon avec table dressée réutilisée comme image-promesse.
9. Section destination plus longue que la section hôtel (lac, archipel, légende, Time).
10. Pré-footer « Get back to nature » : carte olive translucide sur la meilleure photo, avec le CTA.
11. Galeries asymétriques à coins arrondis qui évitent l'effet grille.
12. Tags pill d'attributs (« Sea View », « Balcony », « FACIAL », horaires) : faits lisibles en 1 s.
13. Grilles d'équipements en cellules bordées ton sur ton (9 + 4 + 5), sans icônes.
14. Rayons cohérents (pill 999, cartes 12, images 12–16) et deux easings seulement.
15. Mobile fidèle : mêmes chapitres, statements 40 px lisibles, slider et accordéon conservés.

### 5 faiblesses / limites
1. Conversion : moteur externe en nouvel onglet avec dates 2023 dans l'URL, aucun prix ni date sur le site, anti-bot à l'arrivée, zéro preuve sociale.
2. Accessibilité : pas de H1 home, 47–69 `outline: none`, hamburger sans nom, pas de `main`, contenu à contraste 1,1–1,5 avant scroll.
3. Images : pas de `srcset`, hero mobile 600×400 upscalé, PNG de 2,6 Mo sur contact, fichiers 2880 px, photos d'un autre hôtel du groupe.
4. Écart promesse / inventaire : « sanctuary » vs « Free wifi in the lobby », intérieurs datés, 5 coquilles.
5. SEO et maintenance : titres « Rooms Archive », pas de hreflang, pas de schéma Hotel, 28–174 mots par page, TTFB jusqu'à 4,6 s.

### 10 principes réutilisables
1. Extraire la palette du paysage et fixer un crème de liaison pour les fonds sombres.
2. Chapitrer par couleur pleine ; une vague ou une forme organique à chaque changement.
3. Une phrase géographique concrète (où, temps d'accès) en très grand corps avant toute offre.
4. Text fill au scroll : une phrase par page, jamais plus.
5. Liste-accordéon numérotée pour ≤ 6 hébergements ; cartes au-delà.
6. Hover de surface plutôt que hover de texte sur des lignes larges.
7. Un CTA de réservation dans le header, un en pré-footer sur la plus belle image.
8. Séparer récit sensoriel (paragraphe) et faits (pills + grille).
9. Destination = au moins un tiers de la home quand le lieu est l'argument.
10. Toute animation d'entrée doit avoir un état final lisible sans JS et sous reduced motion.

### Éléments propres à la marque à ne pas copier
Logotype PP Woodland « Hotel Odisej / MLJET » et lion ALH ; blobs et vagues bicolores exactes (formes reconnaissables du travail Bornfight) ; textes (« Sweeping view of the Adriatic in your Room », « Surrender yourself… »), légende d'Ulysse, citation Time ; photos ALH (balcon, lac, archipel, piscine de Cavtat).

### Ce que ce site apporte que les sites « quiet luxury » (FORESTIS, Seagate, Le Collectionist) n'apportent pas
- **La couleur comme structure narrative** : 3 fonds saturés alternés avec vagues, là où le quiet luxury reste sur 1–2 neutres ; la progression se lit sans texte.
- **Le rythme typographique par statements de 80 px à remplissage au scroll** : lecture cadencée, quasi cinématographique, à la place de paragraphes discrets en 16–20 px.
- **Des formes** (vagues, blobs, coins arrondis, pills) qui rendent le site « illustré » et chaleureux plutôt que photographique et rectiligne.
- **Une liste-accordéon numérotée** et des tags de faits, au lieu de cartes photo uniformes.
- **La destination comme premier produit** (page Mljet, légende, parc, faune), là où FORESTIS vend le silence et Le Collectionist la maison.

### Notes /10
- **Branding : 7/10** — palette et typographie tenues sur 6 pages, positionnement « île / parc national » clair ; mais marque groupe floue, coquilles, écart promesse/inventaire, photos empruntées.
- **Direction artistique : 8/10** — 3 fonds + crème de liaison, PP Woodland 80/88 −2,4 px, vagues et blobs, rayons cohérents, galeries asymétriques ; retenue par les intérieurs datés et le bouton cookie bleu.
- **Animations : 7/10** — 67 reveals, text fill à deux couches, hover olive 1 s easeOutExpo, header `has-scrolled` ; mais reduced motion partiel, contenu invisible avant scroll, menu et zoom de hero non vérifiés.
- **UX : 6/10** — IA plate et lisible, CTA persistant, chambres en 1 clic, tags de faits ; mais menu sans nom, `outline: none` ×47–69, pas de H1 home, sorties non annoncées, titres d'archive.
- **Conversion : 3/10** — aucun prix, aucune date, aucune preuve, moteur externe en nouvel onglet avec `arrival=2023-04-25` et interstitiel anti-bot ; positifs : CTA visible partout, contact humain en footer.
- **Mobile : 6/10** — chapitrage et effets conservés, 40 px lisibles, accordéon à boutons ; mais hero flou, CTA de 36 px, liens de 20 px, images 1200 px pour 390 px, TTFB 2,5 s sur rooms.

**Note globale : 6,5/10.** Référence tenue pour le storytelling naturel par la couleur, le rythme et l'accordéon de chambres — mécanismes directement transposables. Mais le site reste une vitrine : réservation, accessibilité et images sont en dessous de son niveau de design, et l'écart entre le récit et l'inventaire réel limite la crédibilité de l'expérience vendue.

---

## Observations clés à conserver pour la phase comparative

- Palette : fonds #f7f7ee (2 155 occ.), #5b6647 (388), #03364f (333) ; textes #434b34, #2e3323, #e3e3c4 ; bordures #d4d4b9 ; un intrus #0056a7 (CookieYes).
- Typo : PP Woodland 400 (80/88 px −2,4 px ; 40/48 ; 60/66) + DM Sans 400/500 (26/31,2 ; 16/20,8) ; mobile 40/46, 30/36, 36/43 ; 45 éléments en 80 px sur la home.
- Home 14 967 px desktop / 11 189 mobile, 7 chapitres, 4 changements de fond, vagues SVG bicolores, aucune vidéo.
- Animation : 67 `reveal`, 4 `parallax`, 3 `horizontal` ; 6–18 transforms par palier de 936 px (22 sur mobile) ; text fill via 2 copies de chaque statement (#434b34 + #e3e3c4) ; easings easeInQuad 0,2 s (UI) et easeOutExpo 1 s (surfaces) ; 7 keyframes ; reduced motion = 1 règle CSS globale.
- Header fixe 90 px (80 mobile), transparent → crème `has-scrolled` ; pills 999 px : « Book now » 109×36 #5b6647→#434b34, « Online Check-in » 157×36 contour #d4d4b9.
- Chambres : page unique 12 296 px, accordéon 5 lignes 01–05, hover olive 1 s, 3 catégories sur bleu + 2 sur crème, grilles 9 + 4 + 5 cellules, tags « Sea View / Balcony / Park view » ; 0 prix, 0 m², capacité seulement « sleeps four ».
- Réservation : book-secure.com (wrensgroup, hrisl24139) en `_blank`, URL avec `arrival=2023-04-25&departure=2023-04-26`, aucun champ date/voyageurs, interstitiel DataDome ; CTA pré-footer 236×31 desktop / 203×26 mobile.
- Preuve : 0 avis, 0 label, 0 offre ; seule citation « Time magazine… 10 most beautiful islands » sur `/mljet/`.
- Perf : home 84 req / 5 914 Ko (images 3 918), TTFB 1 035 ms, FCP 3 116 ms ; contact 148 req / 6 413 Ko dont PNG 2 597 Ko et 74 requêtes Maps ; wellness TTFB 4 616 ms ; 0 `srcset`, 3 images lazy sur 28 ; hero mobile 600×400 upscalé.
- A11y : H1 absent sur la home, `outline: none` 47–69 par page, 0 `main`, 0 skip link, hamburger 40×22 sans nom, iframe Maps sans title, contrastes avant révélation 1,14–1,5.
- SEO : « Rooms Archive - Hotel Odisej », description absente sur rooms/dining, og:image home seule, 0 hreflang malgré `/hr/`, JSON-LD sans `Hotel`, 28–174 mots par page.
- Photos : ratios 1,6 / 1,78 / 1,33 / 1 / 0,75 / 1,48, coins arrondis, fichiers jusqu'à 2880 px (439 Ko), balcon ×3, piscine d'un autre hôtel ALH (Cavtat) sur 4 pages ; ≈ 3 images avec humains.
- Copy : 5 coquilles (« vicinty » ×2, « discover secret of Mljet », « Developement », « A glorious sweeping views ») ; CTA d'exploration « verbe + flèche pill », réservation « Book now / Book your stay ».
- Marque : mono-hôtel, ALH réduit à un lion en footer + socials + blog ; « Beyond the hotel » sort vers adriaticluxuryhotels.com ; check-in sur pay.adriaticluxuryhotels.com.
- Non vérifiés en headless : menu overlay (captures 05 = hero), zoom de l'image de hero des sous-pages (1 `sticky`, image 499×281, ≈ 1 000 px réservés), étape 1 du moteur.
