# Fiche d'audit — Our Habitas (« Luxury for the Soul »)

Clé : `habitas` · Analyse du 2026-09-04 · Chromium headless via Playwright, 1440×900 (desktop) et 390×844 DPR 2 (mobile). Série 2 « au-delà du quiet luxury » : collection d'hôtels, vidéo immersive, branding communautaire.

---

## 0. En-tête

**Nom** : Our Habitas — collection d'hôtels (Mexique, Arabie saoudite/NEOM, Qatar, Émirats, Maroc, Namibie, Chili). **URL de départ** : https://www.ourhabitas.com/. Title de la home : « Our Habitas - Luxury for the Soul - Award Winning Hotels & Resorts ». CMS : WordPress (générateur WP Rocket 3.18.3, thème `habitas-theme`), WPML (EN/ES sur les pages Bacalar).

### Pages étudiées

| Label | URL | Desktop | Mobile |
|---|---|---|---|
| home | https://www.ourhabitas.com/ | oui | oui |
| destination (page hôtel Bacalar) | https://www.ourhabitas.com/bacalar/ | oui | non |
| rooms (Bacalar) | https://www.ourhabitas.com/bacalar/rooms/ | oui | oui |
| room-detail (= version ES de la page rooms, pas de fiche par chambre) | https://www.ourhabitas.com/es/bacalar/rooms/ | oui | oui (hero seulement) |
| experiences (Bacalar) | https://www.ourhabitas.com/bacalar/experiences/ | oui | non |
| signature (expériences marque) | https://www.ourhabitas.com/signature-experiences/ | oui | non |
| dining (Siete) | https://www.ourhabitas.com/bacalar/dining/ | oui | non |
| spa (wellness Bacalar) | https://www.ourhabitas.com/bacalar/wellness/ | oui | non |
| offers (Bacalar) | https://www.ourhabitas.com/bacalar/offers/ | oui | non |
| about / films (même page, deux passes) | https://www.ourhabitas.com/our-films/ | oui ×2 | non |
| loyalty (Dis-loyalty) | https://www.ourhabitas.com/dis-loyalty/ | oui | non |
| contact | https://www.ourhabitas.com/contact-us/ | oui | non |
| booking (sonde « Book » sur la page Bacalar) | https://www.ourhabitas.com/bacalar/ | oui (sonde : « no obvious booking CTA visible », moteur SynXis non atteint) | non |

### Limites de l'observation

- **Hero vidéo bloqué** : le lecteur Vimeo (`player.vimeo.com/video/915913538?background=1&autoplay=1` sur la home, `656697002` sur Bacalar) affiche « We couldn't verify the security of your connection » (proxy) ou « The player is having trouble ». Les captures `home-00/01`, `destination-01`, `booking-01` montrent donc un fond noir : le hero réel n'est **pas jugeable** sur ces images ; seuls la structure (iframe 1440×810, fond noir, flèche de scroll) et les paramètres d'embed sont exploitables.
- **Transitions de page Barba.js** : la bibliothèque est détectée (`libs.Barba: true`) mais son comportement (fondu, préloader `#loadpage .loader`) n'est pas observable en headless.
- **Menu burger** : la sonde n'a pas trouvé de déclencheur (`menu: no burger found`) ; `home-05-menu-open` est identique au hero. L'architecture du menu est déduite du DOM (`nav Zero-level-nav`, `two-level-nav`, `thirdLevel`), pas d'une capture.
- **Moteur SynXis** : aucune étape n'a été capturée (pas de `06-booking-step1`). Seuls les liens et leurs paramètres sont analysés.
- **Pieds de page non rendus** sur les captures pleine page `rooms-02-full`, `dining-02-full`, `signature-02-full` (bandes unies #807566 / #464543 sans texte) ; les textes sont visibles dans `rooms-03-scroll4/5` et `destination-03-scroll6`. Hypothèse : révélation `js-visibility` non déclenchée par la capture pleine page.
- LCP `null`, Lighthouse indisponible, curseur tactile et lecture vidéo non mesurables. Les hovers hors viewport (cartes « DISCOVER ») n'ont pas pu être survolés.
- La capture `home-04-reduced-motion` montre en réalité le **tiroir « Select Property »** ouvert (clic sur BOOK) : exploitée en rubrique 8, non représentative du reduced-motion.

---

## 1. Positionnement de marque

**Faits observés**
- Title : « Luxury for the Soul - Award Winning Hotels & Resorts » ; description : « global collection of sustainable hotels & resorts. Experience wellness, music, art, adventure and more ».
- Home sans H1 (`h1count 0`) ; premier titre H2 « Luxury for the Soul » (36 px Canela) suivi d'un manifeste de ~70 mots : « global home for a global community of like-minded people », six piliers (music, wellness, art, adventure, food, learning), « strangers become friends and friends become family ».
- Section « Our Homes » : carrousel de 11 cartes, chacune nommée « LIEU | PAYS » (22 px Arboria capitales) + une tagline « Our Home … » (« Our Home in a Living Museum » pour AlUla, « Our Home of Play » pour Caravan AlUla, « Our Home Where the Jungle Meets the Sea » pour Tulum, « Our Home on the Lagoon » pour Bacalar). Quatre cartes portent « Coming Soon | … » (Leyja Adventure/Oasis/Wellness à NEOM, Caravan Hatta « Our Expedition Outpost »).
- Architecture de marque visible dans le footer : « OUR HOMES » classés par région (Americas 3, Middle East 7, Africa 1) + sous-marque « Caravan … by Our Habitas » (AlUla, Agafay, Hatta, Dakhla) ; colonne « OUR HABITAS » : Contact, Sustainability, Community Impact, Journal, Mantra, Press, Careers, Real Estate.
- Home : 3 blocs sur 7 parlent d'impact/valeurs (Our Stories, Giving Back/Rise, Our Sustainability) ; 1 seul bloc présente les hôtels ; 0 bloc « chambres ».
- Page Bacalar : eyebrow « BACALAR, MEXICO », H3 « Our Home on the Lagoon », description « holistic oasis for recharging the body, mind, and soul », mention « adults-only, 16 years old or older ».
- Page films : fond #161616, filtres par hôtel, tuiles « Stories By Topic » = les six piliers, section RISE (Ouganda, Madrasat Addeera).
- Programme « Dis-loyalty » (« Our Travel & Food Membership ») : 120+ hôtels, 35 % de réduction Latin America/Middle East jusqu'au 1er septembre 2025, 20 % première visite, 10 % F&B.

**Interprétation**
- Marque ombrelle communautaire : le site vend d'abord une **appartenance** (famille, communauté, piliers) puis des **lieux** (« homes », jamais « hotels » hors balises SEO), et enfin des chambres. La hiérarchie est ombrelle → région → home → sous-pages (Rooms, Offers, Dining, Experiences, Weddings, Wellness, Gallery).
- Cible : voyageurs 25-45 ans internationaux, sensibles aux festivals/retraites, prêts à payer un lodge en tente A-frame comme un hôtel de luxe ; le programme Dis-loyalty (marque Ennismore) et les remises en pourcentage indiquent un luxe **accessible et promotionnel**, pas ultra-luxe.
- Territoire émotionnel : chaleur, feu de camp, coucher de soleil, rituels, eau turquoise. Personnalité : accueillante, militante (Rise, reforestation Noh Bec, coraux Blue Hope), « nomade » (Caravan). Niveau perçu : haut de gamme lifestyle.
- Différence avec un site hôtelier générique : le vocabulaire possessif (« Our Homes/Rooms/Offers/Stories »), le manifeste en ouverture, une bibliothèque de films, des cartes « Coming Soon » qui vendent la croissance du réseau, un programme de fidélité tiers.
- Cohérence offre/mots/images : forte (photos de groupes, feu, rituels = « strangers become friends »). Rupture : les rendus 3D des projets NEOM (PNG 1 067 Ko) côtoient des photos réelles sans distinction.

**Enseignements réutilisables** : nommer chaque lieu par sa promesse (« Our Home of Play ») ; faire précéder les hôtels d'un manifeste court ; grouper par région dans le footer ; assumer un programme d'avantages chiffré quand la cible est lifestyle.

---

## 2. Première impression (5 premières secondes)

**Faits observés**
- `home-00-initial` : hero noir plein écran (810 px sur 900), header transparent (`h 0`, bg `rgba(0,0,0,0)`), burger 48×48 à gauche, logo « ⊛ OUR HABITAS » centré, « BOOK » 98×40 blanc à droite ; bannière cookies OneTrust centrée en haut (boîte blanche ~650×165 px, bouton « ACCEPT ALL COOKIES » taupe, lien « COOKIES SETTINGS »). Flèche de scroll circulaire à y≈745.
- Aucun texte dans le hero : ni H1, ni tagline (`aboveFold` : « Skip to content BOOK Luxury for the Soul… » — le titre n'apparaît qu'à y=860).
- Mobile (`home-mobile-01-hero`) : même composition, hero 844 px = 100 vh, iframe Vimeo 1 502 px de large (débordement masqué, texte d'erreur tronqué).
- Pas de préloader visible (`#loadpage .loader is-hidden`, opacity 0) ; hypothèse : loader utilisé lors des transitions Barba.
- Page Bacalar : même hero vidéo, avec H1 « Bacalar » 60 px Canela + label « MEXICO » 14 px espacé, nav secondaire horizontale (BACALAR ROOMS OFFERS DINING EXPERIENCES WEDDINGS & EVENTS WELLNESS GALLERY).

**Interprétation**
- Le message des 5 premières secondes repose **entièrement sur la vidéo** (non vérifiable ici). Sans elle, l'écran est vide : c'est un pari immersif fort, mais fragile (proxy, données mobiles, reduced-motion).
- Le logo centré et le BOOK isolé donnent une lecture « marque d'abord » ; la bannière cookies centrée (et non en bas) coupe le hero en deux à l'arrivée.
- Raison de continuer : la flèche de scroll et, hypothèse, le mouvement de la vidéo ; sur Bacalar, le nom du lieu en 60 px suffit.

**Enseignements réutilisables** : ne jamais laisser un hero vidéo sans texte de secours (poster + H1) ; placer la bannière cookies en bas ; garder le CTA de réservation seul à droite.

---

## 3. Direction artistique

**Faits observés**
- Palette (JSON) : fonds `#ffffff` (126-289 occurrences), crème `#fff9f2` (section Stories, 311 occ. sur mobile), gris chaud `#464543` (footer global), taupe `#807566` (footer propriété, boutons, `--track-color`), brun `#796c5c` (titres, CTA outline, bouton cookies), `#55504b`, noir `#161616` (page films). Textes : `#444444` (corps), `#333333` (cartes), `#796c5c`/`#807566` (titres), `#b2b2ae` (labels footer), blanc.
- Typographies chargées : **Canela** Light 300 / Regular 400 (woff2 auto-hébergés) pour les titres ; **Arboria** Book 400 / Medium 500 (woff2) pour labels, boutons, noms de lieux ; **acumin-pro** 300 (kit Adobe Fonts `mwq2wei.css`, hypothèse) pour les paragraphes. Font-faces déclarées mais non chargées : Canaro, Bressay Arabic, FFShamelSans (versions arabes, hypothèse).
- Échelle desktop : H1 60 px Canela 400, ls 4,5 px, **lh 54 px < corps** ; H2 52 px Canela 300 capitales ls 2,5 px lh 72,8 (offres, « OUR STORIES ») ; H3 36 px Canela 300 (lh 36-38) ; « Our Homes » 36 px capitalize ls 1,7 ; noms de lieux 22 px Arboria 500 capitales ls 2 px ; eyebrow 18 px Arboria Book 700 capitales ls 6,92 px ; H4 18 px 600 ls 2 px ; corps 18 px / 25,2 acumin-pro 300 ; secondaire 16 / 22,4 ; labels 14 px. Mobile : H2 26 px, H3 26 px, cartes 18 px, « Join our family » 30 px, mais « Our Homes » monte à **45 px / 65 px** sur mobile (incohérence).
- Grille : conteneurs 1314 px (principal), 1358, 990, 750 (intro centrée). Composant img-text : image 620×764 (ratio 0,81) + colonne texte de 300 px centrée, alternance gauche/droite (`img-text--reverse`). Cartes carrousel 410×526 (0,78), doubles cartes 595×397 (1,5), story épinglée 682×700, heros 1440×810/900 (hero--100) ou 1440×720 (hero--80, ratio 2).
- Boutons : pilule « DISCOVER … » 1 px `#807566`, rayon 20 px, 14 px capitales ls 2 px, 28 px de haut ; « BOOK YOUR STAY » carré (rayon 0) 365×58-64, 15 px ls 4,4 px, padding 21/55, hover fond `#796c5c` + texte blanc en 0,3 s ease-in ; liens « BOOK NOW / LEARN MORE » 118×20 soulignés d'un filet 1 px ; accordéons 380×63 avec trait « — » ; chips films rayon 24 px 140×36 ; « BOOK » header rayon 18 px.
- Iconographie : logo-astérisque ⊛ (rose des vents/flocon), flèche circulaire de scroll, chevrons Swiper, traits horizontaux d'accordéon ; aucune illustration, aucune texture ; 25 SVG par page (icônes sociales, drapeaux WPML).
- Espacements : classes `u-mb-125`, `u-mb-100`, `u-mb-75`, `u-mb-50` (marges de 125/100/75/50 px entre sections).

**Interprétation**
- Système « éditorial chaud » : serif Canela fine sur blanc, capitales espacées, taupe/brun comme unique couleur d'accent, aucune couleur saturée hors photos. Les photos (turquoise, or, feu) portent seule la couleur : contraste voulu entre UI neutre et images saturées.
- Le composant img-text répété (7 fois sur Bacalar, 3 sur Rooms, 4 sur Experiences) crée une cohérence forte mais une monotonie de rythme.
- Les rayons mélangés (pilule 20 px, carré 0 px, chips 24 px, header 18 px) trahissent plusieurs générations de composants.
- Interlignage 54 px pour un H1 de 60 px : titres sur deux lignes qui se chevauchent potentiellement (non observé sur les pages étudiées, titres courts).

**Tokens approximatifs**

| Token | Valeur |
|---|---|
| Fond principal / secondaire | #ffffff / #fff9f2 |
| Fond footer global / propriété | #464543 / #807566 |
| Fond page films | #161616 |
| Accent (titres, CTA, hover) | #796c5c ; #807566 |
| Texte corps / cartes / muted | #444444 / #333333 / #b2b2ae |
| Display | Canela 300-400 : 60 / 52 / 45 / 36 px (mobile 26-30) |
| Labels | Arboria 500 22 px capitales ls 2 px ; eyebrow 18 px ls 6,92 px |
| Corps | acumin-pro 300, 18 / 25,2 px ; 16 / 22,4 px |
| Conteneurs | 1314 · 990 · 750 px ; colonne texte 300 px |
| Ratios images | 0,78 (cartes) · 0,81 (img-text) · 1,5 (doubles) · 2 (hero--80) · 16:9 (hero vidéo) |
| Rayons | 0 (CTA principal) · 18-20 (pilules) · 24 (chips) |
| Header | 52 px fixe, blanc 80 % + `backdrop-filter: blur(20px)` au scroll |
| Transitions | 0,3 s ease-in (défaut) · 0,6 s cubic-bezier(.405,.005,0,1) (reveal/hover) · 1 s (cartes) |

**Enseignements réutilisables** : un seul accent chaud + photos saturées ; colonne texte de 300 px centrée face à une image portrait 0,81 ; eyebrow très espacé (ls ≈ 0,38 em) pour hiérarchiser sans grossir.

---

## 4. Architecture de la page d'accueil

Reconstruction à partir de `sections` (desktop, y en px) et de `home-02-full` / `home-03-scroll1-6`.

| Position | Section | Objectif | Contenu | Interaction | CTA | Émotion créée |
|---|---|---|---|---|---|---|
| 0-810 | Hero vidéo (`hero--100 hero--embed`) | Immersion | Iframe Vimeo background/autoplay, header transparent, flèche | Scroll (flèche) ; vidéo non vérifiée | BOOK (header) | Attente, mystère (aucun texte) |
| 860-1116 | Intro « Luxury for the Soul » | Manifeste | H2 36 px + paragraphe 500 px centré, ~70 mots | Reveal `js-visibility` | aucun | Adhésion, tribu |
| 1241-2119 | Our Homes (fond blanc) | Présenter la collection | Swiper 11 cartes 410×526, nom + tagline « Our Home … », 4 « Coming Soon » | Carrousel horizontal (loop, cartes triplées dans le DOM) | 11 pilules « DISCOVER X » | Choix, appétit géographique |
| 2119-2883 | Our Mexico Journey | Vendre un itinéraire multi-lieux | Texte 300 px + image 620×764 (ponton, ananas) | reveal | DISCOVER MEXICO → /journeys-mexico/ | Envie de voyage |
| 3009-5168 | Our Stories (fond #fff9f2, 2 159 px) | Contenu éditorial, preuve d'engagement | Story épinglée à gauche (Blue Hope, 682×700) + colonne droite : titre 52 px, 3 stories signées | **sticky** gauche pendant 2 000 px ; hover image ×1,05 en 0,6 s | READ OUR JOURNALS | Profondeur, sincérité |
| 5293-6057 | Giving Back (reverse) | Impact | Image enfant + texte Rise | reveal | LEARN MORE (http://ourhabitas.com/rise, non-www) | Générosité |
| 6182-6946 | Our Sustainability | Valeurs | Aérien mangrove + texte | reveal | LEARN MORE | Responsabilité |
| 6858-7758 | Footer (#464543) | Capture + maillage | « JOIN OUR FAMILY » email 470 px + JOIN US ; Our Homes par région ; Our Habitas ; 5 réseaux | Formulaire (Revinate/Mailchimp scripts) | JOIN US | Appartenance |

**Logique narrative** : début = vidéo muette → manifeste (qui nous sommes) → catalogue des lieux (où) → un itinéraire (comment voyager) → histoires (pourquoi) → impact → inscription. **Il n'y a ni chambres, ni prix, ni preuve sociale, ni bloc réservation sur la home** : l'offre ne devient concrète qu'à partir de la page hôtel (clic « DISCOVER BACALAR »), puis la page Rooms. La home est une page de marque, pas une page de vente ; le seul chemin transactionnel est le BOOK du header (tiroir de sélection de propriété).

---

## 5. Scroll et storytelling

**Faits observés**
- `animAttrs` home : `reveal 18`, `sticky 1`, `horizontal 2`, `parallax 0` ; Bacalar : `reveal 15, parallax 2, sticky 3, horizontal 3` ; Signature : `parallax 8` ; Dining/Wellness : `parallax 3`. Classes DOM : `js-visibility`, `reveal-slide`, `is-visible`.
- Scroll home desktop : header devient `is-scrolling` dès y=490 (fond `rgba(255,255,255,0.8)`, 52 px, blur 20 px sur les pages propriété). `pinned: a.story.js-visibility h=700` de y=2449 à y=4409 (≈ 2 000 px d'épinglage). `opacityLow` 1 à plusieurs paliers (éléments en attente de révélation). Fond central : transparent → blanc (Our Homes) → `#fff9f2` (Stories) → transparent → `#464543` (footer).
- Alternance : vidéo → texte centré → carrousel → img-text (texte gauche) → sticky/colonne → img-text (image gauche) → img-text (texte gauche) → footer. Sur Bacalar, 7 blocs img-text alternés + 2 carrousels blancs + 1 double carte.
- Scroll horizontal : Swiper « Our Homes » (11 cartes, `swiper-icons` chargées), « Our Rooms » et « Our Offers » sur Bacalar, galeries de chambres (12 images) avec chevrons ; la carte hors cadre à gauche est rognée volontairement (peek de 40 px).
- Captures `03-scrollN` : aucun élément transformé au scroll autre que le sticky ; images fixes, pas de zoom lié au défilement.
- Mobile : pas de sticky (`pinned []`), même ordre de sections, docHeight 9 346 px (7 758 sur desktop).

**Interprétation**
- Rythme « long-scroll éditorial » : une respiration de 125 px entre chaque bloc, chaque bloc = un titre + un paragraphe + un lien ; le sticky Stories est le seul moment de tension (fonction : orienter le regard, donner du poids à la story principale). Les carrousels (fonction : densité sans allonger la page) contrastent avec les blocs img-text (fonction : rythme, respiration).
- Les changements de fond (blanc → crème → gris) balisent trois actes : lieux / histoires / engagement.
- Les attributs `parallax` existent mais aucune transformation n'a été mesurée dans les paliers de scroll : hypothèse, parallaxe légère sur les images des blocs `multiple` (dining, wellness), non observable en headless.
- L'envie de poursuivre vient des photos (chaque bloc en contient une grande) plus que d'effets ; la page est prévisible après le troisième bloc.

**Enseignements réutilisables** : un seul bloc sticky par page, placé au milieu, sur du contenu éditorial ; fond crème pour isoler la section « histoires » ; peek de carte à gauche pour signaler le scroll horizontal.

---

## 6. Animations et micro-interactions

**Faits observés** : libs Swiper, jQuery 3.3.1, jQuery UI (324 Ko), Barba, Vimeo, YouTube, FontAwesome ; aucun GSAP, Lenis, AOS. `transitionDurations` : 0,3 s ×213, 0,5 s ×93, 0,6 s ×33, 1 s ×22, 0,4 s ×12. `easings` : ease-in ×197, `cubic-bezier(0.405, 0.005, 0, 1)` ×20, `cubic-bezier(0.895, 0.03, 0.685, 0.22)` ×1. Keyframes propres : `rotating 2s linear`, `slideDown/slideUp 0.3s ease-in-out`, `MobileRotateAnimation 3s ease`, spinners 1,4 s. `customCursor: none`, `cursorNone 2` (règles CSS, non observées). `reducedMotionRules 9` mais le `rmSnippet` provient du CSS YouTube (`.html5-video-player`) : aucune règle propre au thème.

| Animation | Déclencheur | Élément | Effet | Fonction | Risque UX |
|---|---|---|---|---|---|
| Préloader | Chargement / transition Barba (hypothèse) | `#loadpage .loader` + spinner 1,4 s | Voile fixe, opacité 0 → 1 → 0 | Masquer le swap de page | Non observé ; latence ajoutée si transitions longues |
| Hero vidéo | Autoplay (`background=1&autoplay=1`) | iframe Vimeo 1440×810 | Boucle muette (hypothèse) | Immersion, marque | Bloqué par proxy/données ; aucun texte de secours |
| Reveal de section | Entrée dans le viewport (`js-visibility` → `is-visible`) | 15-18 blocs/page | Opacité + translation (`reveal-slide`), 0,6-1 s, cubic-bezier(.405,.005,0,1) (ease-out expo, hypothèse) | Rythme | Footers non rendus en capture : contenu invisible si JS échoue |
| Hover story | Survol | `a.story img` | `scale(1.05)` en 0,6 s | Feedback | Faible |
| Hover carte signature | Survol | `.card` | translateY 0,0083 px (négligeable) + image ×1,05 ; voile `#796c5c` à 90 % avec description (capture `signature-02-full`, carte Tulum) | Révéler le texte | Texte inaccessible sans hover (tactile) |
| Hover CTA plein | Survol | « BOOK YOUR STAY », « JOIN NOW », « RESERVE A TABLE » | Fond transparent → `#796c5c`, texte → blanc, 0,3 s ease-in | Affordance | Faible |
| Hover accordéon | Survol | `.accordion__btn` 380×63 | Fond `#796c5c`, texte blanc, bordures blanches | Affordance | Contraste fort, bon |
| Hover chip/VIEW ALL | Survol | Films | Fond blanc, texte `#404242`, 0,3-0,4 s | Filtre | Faible |
| Header au scroll | y > ~490 | `.page-header.is-scrolling` | Transparent → blanc 80 % + blur 20 px ; logo réduit à ⊛ sur mobile | Lisibilité | Faible |
| Carrousels | Drag / chevrons | Swiper (homes, rooms, offers, galeries) | Glissement, `scrollSnap` (7 règles) | Densité | Chevrons 30×30 petits |
| Accordéons | Clic | Expériences, menus, contacts, Dis-loyalty | slideDown/slideUp 0,3 s | Compacter | Contenu caché par défaut |
| Tiroir BOOK | Clic « BOOK » (home) | Panneau droit 432 px, fond taupe, liste de 9 propriétés | Glissement latéral (hypothèse) | Choix de l'hôtel | Aucune date ; sort vers SynXis |
| Flèche de scroll | — | Icône circulaire | `rotating 2s linear` (hypothèse : rotation continue) | Inviter à scroller | Faible |
| Reduced motion | `prefers-reduced-motion` | — | Aucune règle du thème ; vidéo autoplay conservée | — | Non conforme WCAG 2.3.3 |

**Interprétation** : le vocabulaire est celui d'un thème WordPress soigné (reveal, scale 1,05, hover plein) sans couche d'animation avancée. La signature reste la courbe `cubic-bezier(.405,.005,0,1)` (départ rapide, arrivée très amortie) appliquée aux reveals et hovers, qui donne une impression de glissement doux. Barba est chargé mais rien ne prouve des transitions élaborées.

**Enseignements réutilisables** : une seule courbe « expo-out » pour reveals et hovers ; scale 1,05 sur 0,6 s comme hover d'image standard ; voile coloré avec texte sur les cartes destination (à doubler d'un affichage tactile).

---

## 7. Navigation et architecture de l'information

**Faits observés**
- Header global : burger 48×48 (gauche), logo centré, « BOOK » (droite). Header propriété : logo réduit + nav secondaire horizontale de 8 entrées (BACALAR · ROOMS · OFFERS · DINING · EXPERIENCES · WEDDINGS & EVENTS · WELLNESS · GALLERY, 14 px capitales) + BOOK. Entrée active en blanc/noir, autres à 65-80 %.
- Menu (DOM) : panneau `nav` fixe pleine hauteur, fond `rgba(0,0,0,0.3)`, structure en tiroirs : « our Homes » → « Back to Habitas Home » → liste d'hôtels → « Back to Our Homes » → sous-menu d'hôtel (Rooms/Villas, Offers, Dining, Experiences, Weddings & Events, Wellness, Gallery). Classes `Zero-level`, `one-level`, `two-level-nav`, `thirdLevel`. Pages marque : Experiences (signature), Offers, Community Impact (Rise), Journal, Films, Sustainability, Mantra, Dis-loyalty, Press, Careers, Real Estate.
- Anomalies : lien « Offers » de Ras Abrouq vers `habisstage22sp.wpengine.com` (staging), « LEARN MORE » Rise en `http://ourhabitas.com/rise` (non-www, non-https), footer Bacalar en deux couches (footer propriété taupe + footer global gris = 900 px cumulés).
- Contact : accordéon par hôtel (9 entrées 100 % largeur, 63 px), « Other contacts » (Press, Influencers, Careers, Rise, Development) ; footer Bacalar : téléphone, WhatsApp, `reservations.bacalar@`, `sales.bacalar@`, adresse.
- Chemin vers une chambre : Home → DISCOVER BACALAR → Our Rooms (carrousel) → DISCOVER OUR ROOMS → page Rooms → BOOK NOW (SynXis) = **4 clics** ; via BOOK header : 1 clic (tiroir) + 1 clic (hôtel) → SynXis sans passer par les chambres.
- Bouton de réservation persistant : oui, « BOOK » fixe dans le header sur toutes les pages hôtel (98×40 desktop, **48×20 mobile**), absent des pages marque (films, signature, loyalty, contact : pas de CTA dans les FIXED).

**Interprétation**
- L'IA est claire à deux niveaux (marque / hôtel) et la nav secondaire des pages hôtel rend chaque prestation atteignable en 1 clic. Le menu en tiroirs successifs (3 niveaux) est logique pour 11 lieux mais impose des allers-retours « Back to… ».
- Frustrations : disparition du BOOK sur les pages marque, double footer, lien de staging, mélange « Rooms » / « Villas » selon les hôtels sans explication.

**Enseignements réutilisables** : nav secondaire horizontale par lieu dans un header commun ; « Back to … » explicites dans un menu à niveaux ; ne jamais retirer le CTA de réservation, même sur les pages éditoriales.

---

## 8. Parcours de réservation et conversion

**Faits observés**
- Type : **moteur transactionnel externe SynXis** (be.synxis.com) pour les nuits ; **demande par email** (mailto) pour expériences et wellness ; **OpenTable** pour Siete ; **Dis-loyalty** (site tiers) pour l'adhésion.
- Home : « BOOK » ouvre un tiroir droit « Select Property » (capture `home-04-reduced-motion`) listant 9 hôtels ; liens SynXis `chain=30700` (Caravan Hatta : `chain=33122&hotel=98046`), `adult=2&rooms=1`, devises pré-réglées **SAR** (AlUla, Caravan AlUla), **QAR** (Ras Abrouq), **EUR** (Agafay, Dakhla), **USD** (Tulum), **AED** (Hatta), aucune pour Bacalar ; `nights=4` pré-rempli pour Bacalar, Tulum, San Miguel ; dates d'arrivée **codées en dur dans le passé** : `arrive=2023-07-03` (AlUla), `2023-09-23` (Caravan AlUla), `2024-04-07` (Ras Abrouq) ; Caravan Hatta `arrive=2026-09-28&adult=1`.
- Pages Bacalar : « BOOK » header → SynXis `hotel=41781` direct ; « BOOK YOUR STAY » (188×20 lien sur Bacalar, 365×64 bouton sur Rooms à y=1219) ; « BOOK NOW » sous chaque catégorie (118×20). Aucun champ date/voyageurs sur le site (`dateInputs []`), aucun tarif affiché sur aucune page.
- Offres : 5 cartes (Dis-loyalty, Spirit of the Lagoon, Stay Local Resident Rate, Culinary Journey, Ritual Wellness) ; « Spirit of the Lagoon » = séjour 4 nuits incluant voile, paddle au lever du soleil, temazcal ou cacao, Janzu, dîner 4 services ; inclusions générales : « Daily breakfast and activities … included with every stay » ; Dis-loyalty : 20 % première visite, 10 % F&B, 35 % jusqu'au 1er sept. 2025, « 50% off newly opened hotels ». Aucun prix, aucun acompte, aucune condition d'annulation sur ces pages.
- Réassurance : adults-only 16+, activités complémentaires listées (Yoga, Treebar, Cinema Club, Pinto and Tinto, Meditation, Temazcal), WhatsApp et deux emails, « Award Winning » dans le title seulement. Aucun avis, note, badge ou distinction visible dans les pages.
- Newsletter « Join our family » en pied de chaque page (input 470×40 + JOIN US 125×40).
- Points de rupture : sortie vers be.synxis.com (domaine, identité visuelle non capturés), OpenTable, mailto ; le tiroir home ne demande ni dates ni voyageurs avant de sortir.

**Interprétation**
- Le site distingue bien **découvrir** (DISCOVER/EXPLORE), **demander** (EMAIL TO RESERVE, BOOK YOUR EXPERIENCE en mailto) et **réserver** (BOOK/BOOK NOW), mais le passage à l'acte est pauvre : pas de prix, pas de calendrier, des liens SynXis avec des dates passées (probable écran d'erreur ou reset côté moteur, non vérifié) et une devise imposée.
- La conversion est déportée sur les **pourcentages** (Dis-loyalty) et les **inclusions** (petit-déjeuner, activités) : mécanique lifestyle plutôt que luxe, efficace pour la cible mais elle affaiblit la valeur perçue.
- Le contact humain est réel (WhatsApp, emails dédiés) mais enfoui dans le footer et l'accordéon contact.

**Enseignements réutilisables** : pré-remplir `nights` et `adult` mais **jamais** de date fixe ; un tiroir de sélection d'hôtel dans le header pour les collections ; afficher les inclusions en une phrase sous les offres ; distinguer les CTA par verbe.

---

## 9. Pages chambres / propriétés

**Objet vendu** : une **nuit en tente A-frame** (2 adultes, lit king) dans l'un de 3 types classés par vue, ou un **séjour de 4 nuits** packagé (offres). Pas de fiche par chambre : `room-detail` renvoie la version espagnole de la même page (title « Habitaciones | Habitas », `og:title` seul, pas de description).

**Desktop — https://www.ourhabitas.com/bacalar/rooms/ (docHeight 5 365, 145 mots)**
- Hero image 1440×900 (vue aérienne des A-frames, ponton, lagune), nav secondaire « ROOMS » active, aucun H1 (`h1count 0`).
- y=1025 : H3 « Our Rooms » 36 px + paragraphe 750 px (« seven shades of blue », « A-framed tented rooms ») + **BOOK YOUR STAY** 365×64 outline.
- y=1407, 2296, 3185 : trois blocs img-text alternés « LAGOON ROOMS », « JUNGLE ROOMS », « LAGOON BREEZE ROOMS » (H3 36 px Canela capitales), ligne « Sleeps 2 | King Bed » 14 px, filet 1 px, paragraphe 300 px (30-35 mots : vue, sons, végétation), « BOOK NOW » 118×20. Colonne image = Swiper de 12 images 620×764 (chevrons blancs 30 px).
- y≈4 100 : « VIEW PROPERTY MAP » (lien souligné). Puis footer propriété taupe + footer global.
- Ordre : ambiance → catégorie → capacité → description sensorielle → CTA. Absents : surface, équipements, services, prix, disponibilité, photos plan, chambres complémentaires suggérées, avis.

**Mobile — rooms-mobile (docHeight 7 410)**
- Hero 390×844 (image recadrée verticalement, ponton visible), header blanc 52 px avec logo complet puis ⊛ seul au scroll, BOOK 48×20.
- Titres 26 px, corps 18 px conservé, image 390×527 (0,74) galerie glissable, « BOOK YOUR STAY » 298×64, « BOOK NOW » 118×20. Trois blocs de 1 000-1 176 px chacun. Ordre identique, aucune section supprimée.

**Page destination — https://www.ourhabitas.com/bacalar/ (docHeight 8 780, 839 mots)** : H1 « Bacalar » + « MEXICO » ; copy-block 374 px ; carrousel « Our Rooms » (3 cartes 410×526 avec description de 25 mots) + DISCOVER OUR ROOMS 365×58 ; DINING (Siete, deux étages dans la canopée) ; ONE WITH WATER ; carrousel « Our Offers » (5) + DISCOVER ALL OFFERS ; WELLNESS ; WEDDINGS & EVENTS ; « DISCOVER OUR NEARBY HOMES » (Tulum, Atacama en 595×397). C'est la page hôtel qui vend l'expérience : sur 9 sections, 1 seule concerne les chambres.

**Interprétation**
- La chambre est traitée comme un décor (« overlook seven shades of blue », « tucked amongst lush palms ») et non comme un produit : une seule donnée factuelle (« Sleeps 2 | King Bed »). Cela colle au positionnement communautaire mais laisse le visiteur sans repère de surface ni de prix avant SynXis.
- La galerie de 12 images par catégorie est le principal outil de projection ; le « VIEW PROPERTY MAP » ajoute une lecture spatiale absente ailleurs.
- Les hébergements complémentaires sont remplacés par des **hôtels voisins** (Tulum, Atacama) : logique de collection.

**Enseignements réutilisables** : trois catégories nommées par leur vue ; ligne de faits « Sleeps 2 | King Bed » minimaliste ; galerie par catégorie plutôt que page par chambre ; « nearby homes » en fin de page pour une collection.

---

## 10. Copywriting

**Faits observés**
- Possessif systématique : « Our Homes », « Our Rooms », « Our Offers », « Our Stories », « Our Mexico Journey », « Our Sustainability », « Our Home on the Lagoon », « Our Experiences », jusqu'au nom de marque « Our Habitas ».
- Lexique de famille/communauté : « global home », « global community », « like-minded », « strangers become friends and friends become family », « Join our family », « our global family », « gather », « celebrate ».
- Substitution lexicale : « home » pour hôtel, « Caravan » pour camp, « journey » pour itinéraire, « ritual » pour soin, « Dis-loyalty » pour programme de fidélité.
- Leitmotiv « seven shades of blue » / « Lagoon of Seven Colors » repris dans meta description Rooms, Lagoon Rooms, Dining, Catamaran.
- Titres : 1 à 4 mots en capitales (« ONE WITH WATER », « GIVING BACK », « LIVE INSPIRED », « NEW PERSPECTIVES ») ; eyebrows factuels (« BACALAR, MEXICO », « ON PROPERTY EXPERIENCES », « OUR TREATMENTS »).
- Paragraphes de 30-70 mots, toujours centrés, ton à la première personne du pluriel, verbes d'invitation (Embark, Discover, Explore, Immerse, Reconnect, Awake).
- Caractéristiques techniques réduites : « Sleeps 2 | King Bed », « adults-only 16+ », « Additional cost applies », « complimentary », « 40-minute drive from Marrakech », « a 4-night stay includes… ».
- CTA : DISCOVER (lieu), EXPLORE (page voisine), LEARN MORE (impact), VIEW OFFER, DINE WITH US, EMAIL TO RESERVE, BOOK YOUR EXPERIENCE, BOOK NOW, BOOK YOUR STAY, JOIN NOW, JOIN US, WATCH, VIEW ALL, LOAD MORE.
- Le mot « luxury » n'apparaît que dans la signature « Luxury for the Soul » et le title SEO ; jamais « exclusive » sauf « exclusive offers » ; « sustainable » dans la meta.
- Titres SEO longs et descriptifs (« Tranquil Hotel Rooms in Bacalar, Mexico », « Holistic Lagoon Resort ») en décalage avec le vocabulaire « home » du site.

**Interprétation**
- Mécanisme central : **l'appropriation** (Our + nom commun) transforme chaque prestation en objet partagé avec le lecteur ; le second mécanisme est le **remplacement des mots d'industrie** par des mots de vie (home, family, journey, ritual). Troisième : une **phrase-monde** par lieu (« Our Home of Play », « Our Home in a Living Museum ») qui résume la promesse sans description.
- La transformation prestation → expérience se fait par le verbe (« Awake to a multihued sunrise », « Begin your day with a guided sunrise tour ») et par l'inclusion dans un rituel de groupe.
- Faiblesse : les CTA en capitales espacées sont nombreux et parfois interchangeables (LEARN MORE vs EXPLORE vs DISCOVER pour des cibles internes similaires) ; les mentions de prix sont remplacées par des pourcentages.

**Enseignements réutilisables** : un possessif de marque ; une phrase-monde par lieu ; un leitmotiv sensoriel réutilisé sur 4 pages ; ligne de faits minimale ; verbes différents pour découvrir / demander / réserver.

---

## 11. Photographie et vidéo

**Faits observés**
- Heros : vidéos Vimeo (home, Bacalar, Bacalar Wellness hypothèse), images 1440×900 (Rooms : aérien des A-frames), 1440×720 (Offers : kayaks transparents vus du ciel ; Experiences/Contact : paddles au coucher de soleil ; Signature : femme à la lanterne devant le camp AlUla ; Dis-loyalty : feu de camp et groupe à Agafay ; Dining : plat en fonte).
- Cartes hôtels (410×526) : architecture d'abord (Leyja = rendus 3D CGI, pics de roche, piscine vitrée ; Hatta = montagnes ; Tulum = tente ouverte sur la mer ; Bacalar = A-frame au bord de l'eau).
- Blocs img-text : mélange plans larges (mangrove aérienne, coraux de Blue Hope), scènes de groupe (feu à Agafay, tablée dans la jungle, bateau à voile), rituels (miel versé, herbes sur le corps, eau versée sur les mains), détails de matière (kilim, chaise, rideau).
- Présence humaine : très forte (groupes de 4-6, couples sur ponton, yogini, enfant du programme Rise, artisane AlUla, musicien). Lumière : dominante golden hour, contre-jours, silhouettes ; couleurs : turquoise/or/terre.
- Films : 6 vignettes 410×530 + 6 tuiles piliers + carrousel RISE ; « Video placeholder image » en alt ; segments Vimeo de 2,4 à 4,8 Mo chargés sur cette page uniquement (`videosNet` ≈ 15 Mo), aucun ailleurs.
- Proportion lieu / expérience sur Bacalar : ≈ 40 % lieu (chambres, restaurant, mangrove) / 60 % expérience (personnes en activité).
- Poids : images JPG 300-500 Ko (1280-1536 px de large), 2 PNG de rendus NEOM à 1 067 Ko et 647 Ko sur la home ; 8-16 images avec `srcset` par page, `lazy 0` (aucun `loading="lazy"` sauf 11 sur Films).

**Interprétation**
- La photo raconte la **communauté** (personnes ensemble) plus que l'architecture ; l'hôtel est le décor de scènes de vie. C'est la différence la plus nette avec les références quiet luxury (chambres vides, matières).
- Les rendus 3D des projets à venir affaiblissent la crédibilité photographique de la home ; leur poids PNG pénalise aussi la perf.
- Les vidéos jouent un rôle de **marque** (films documentaires par lieu et par pilier), pas de produit : aucune vidéo de chambre.

**Shot list pour reproduire ce niveau**
1. Aérien drone du site entier à l'heure dorée (hero Rooms).
2. Aérien vertical eau + embarcations (kayaks, voilier) pour heros d'offres.
3. Groupe de 4-6 personnes autour d'un feu au crépuscule, lanternes.
4. Tablée en extérieur avec verres levés, végétation en fond.
5. Silhouettes de couple sur ponton au coucher de soleil.
6. Personnes en activité (paddle, voile, yoga) prises de loin, contre-jour.
7. Rituel de soin en gros plan (mains, miel, herbes, eau versée).
8. Trois plats vus de dessus en lumière naturelle dure.
9. Chambre depuis l'intérieur avec ouverture sur le paysage (rideau, chaise, tapis).
10. Extérieur de l'unité (A-frame, tente) à la tombée de la nuit, lampes allumées.
11. Portrait d'un partenaire local (artisan, musicien) pour la section impact.
12. Film de 60-90 s par lieu + film de marque, format 16:9, boucle muette de 15 s pour le hero avec poster.

---

## 12. Mobile

**Faits observés** (390×844)
- Hero home : 844 px = 100 vh, iframe 1 502 px de large rognée, aucun texte ; header : burger 42×48, logo complet 190 px, BOOK 48×20 (police 14 px). Au scroll : header blanc 52 px, logo réduit à ⊛ 40 px.
- Titres : H2 26 px, H3 26 px (chambres), cartes 18 px, « Our Homes » 45 px ; corps 18 / 25,2 conservé ; largeur de texte 340 px (intro), 300 px (blocs).
- Rythme : docHeight 9 346 px (home), 7 410 (rooms) ; sections 1 000-1 150 px ; images 390×527 (0,74) ; carrousel « Our Homes » en cartes 360×461 avec marge de 30 px (1 carte visible).
- Animations : reveals conservés (`reveal 18`), sticky supprimé (`pinned []`), hover inexistant (voile texte des cartes signature inaccessible).
- Boutons : DISCOVER pilules 28 px de haut, BOOK YOUR STAY 298×64, BOOK NOW 118×20, JOIN US 124×40, email input 300 px.
- Réservation : BOOK 48×20 → SynXis (pages hôtel) ; tiroir de sélection non capturé sur mobile.
- Vitesse : home mobile 300 requêtes, 14,7 Mo, TTFB 590 ms, FCP 1 304 ms, load 5 585 ms ; rooms mobile 339 req., 13,5 Mo, FCP 1 844, load 5 712 ; room-detail mobile TTFB 1 794 ms.
- Menu : sonde « no burger found » — non vérifié.
- Lisibilité : 18 px sur blanc, ratio 9,7:1 ; labels footer 14 px `#b2b2ae` sur `#464543` (≈ 4,5:1).

**Interprétation / problèmes**
- La cible tactile « BOOK » de 20 px de haut est sous le minimum de 44 px ; les liens « BOOK NOW » 118×20 aussi.
- Le hero vidéo en 100 vh sans texte coûte un écran entier avant tout message ; 14,7 Mo pour une home mobile est lourd (11 Mo de scripts et CSS).
- Le passage à 45 px de « Our Homes » sur mobile (36 px sur desktop) et la taille unique des cartes rendent la section plus imposante que sur desktop.
- Différences pertinentes : perte du sticky Stories (la section devient une simple liste), perte du texte au survol, gain d'un logo compact.

**Enseignements réutilisables** : logo symbole au scroll mobile ; conserver 18 px de corps ; mais prévoir des cibles ≥ 44 px, un poster + titre dans le hero et un budget < 5 Mo.

---

## 13. Performance, accessibilité, SEO

**Faits observés**
| Page | Requêtes | Poids total | TTFB | FCP | Load |
|---|---|---|---|---|---|
| home desktop | 559 | 26,5 Mo | 1 010 ms | 2 288 ms | 8 238 ms |
| home mobile | 300 | 14,7 Mo | 590 | 1 304 | 5 585 |
| Bacalar | 706 | 27,2 Mo | 805 | 2 364 | 9 134 |
| Rooms | 612 | 21,6 Mo | 392 | 1 200 | 8 439 |
| Offers | 606 | 21,9 Mo | 460 | 1 096 | 3 215 |
| Films (2 passes) | 1 907 / 1 896 | 159 / 135 Mo | 669 / 373 | 1 120 / 1 280 | 12 240 / 30 350 |

- Plus gros fichiers : CSS du thème `build/theme/index.css` **2 329 Ko** (chargé deux fois dans certaines passes), document HTML 1 907 Ko (nav complète + cartes triplées), `jquery-ui.js` 324 Ko, `player_embed` YouTube 472 Ko, PNG de rendus 1 067 Ko. `totalCssBytes` 3,37 Mo (14,8 Mo sur Films).
- Tiers : Google (36-70 req.), Cloudflare challenges (16-54), GTM, DoubleClick, YouTube, OneTrust, Facebook, Snapchat, Clarity, Sojern, Adform, AdNexus, relay-t.io (hypothèse : outil de suivi hôtelier), Hotjar.
- Images : `lazy 0` sur toutes les pages sauf Films (11) ; `withSrcset` 4-16 ; formats JPG/PNG, 7 WebP sur Films seulement.
- Stabilité visuelle : hero vidéo à hauteur fixe (pas de saut) ; reveals à opacité (pas de reflow) ; les Swiper triplent les cartes dans le DOM.
- Contrastes estimés : `#444444`/blanc 9,7:1 ; `#333333`/blanc 12,6:1 ; `#796c5c`/blanc ≈ 5,1:1 ; `#807566`/blanc ≈ 4,5:1 (pilules DISCOVER 14 px : limite AA) ; blanc/`#807566` ≈ 4,5:1 ; `#b2b2ae`/`#464543` ≈ 4,5:1 ; blanc sur photos (titres de cartes films, chips) : variable, voile 40-50 % ajouté.
- Clavier : `focusOutlineNone 200` (plafond de comptage atteint sur chaque page) ; `tabindexNeg 3-6` ; `buttonsNoName 9` (burger, chevrons Swiper, boutons de fermeture) ; `linksNoName 2-6` ; `iframesNoTitle 2-6`.
- Alt : home 0 manquant / 9 vides ; Rooms 3 manquants / **44 vides** (galeries) ; Bacalar 6 / 21 ; Films alt « Video placeholder image » ×6.
- `skipLink: true`, landmarks main/nav/header/footer présents (footer ×2 sur pages hôtel).
- Formulaires : 1 email par page avec label ; validation « Enter a valid email address ».
- Reduced motion : 9 règles, toutes issues de CSS tiers (YouTube, OneTrust) ; capture `04-reduced-motion` identique au hero (hors artefact du tiroir).
- Titres : `h1count 0` sur home, rooms, experiences, films, ES rooms ; 1 sur Bacalar, wellness, offers, contact, signature, loyalty. Hiérarchie H2/H3 mêlée (H3 « Our Homes » avant H2 « Join our family »).
- Métadonnées : title et description sur la plupart des pages (absente sur `/es/bacalar/rooms/` et Signature) ; `og:title`/`og:description` ; `og:image` seulement sur Experiences ; canonical correct ; hreflang `en`/`es`/`x-default` sur Bacalar, `en`/`x-default` sur home ; JSON-LD `@graph` WebPage (Yoast, hypothèse) sans `Hotel`/`LodgingBusiness`.
- **`lang="es"` sur les pages anglaises de Bacalar** (`/bacalar/`, `/bacalar/rooms/`, `/bacalar/offers/`…) et `lang="en"` sur la version espagnole : attributs inversés (WPML, hypothèse).
- Contenu indexable : 769 mots (home), 839 (Bacalar), 145 (Rooms), 366 (Experiences), 118 (Dining), 242 (Wellness), 256 (Offers), 334 (Dis-loyalty), 90 (Signature), 219 (Films), 162 (Contact).

**Interprétation**
- Équilibre immersion/performance défavorable : la vidéo hero ne pèse rien en headless (bloquée) mais la page pèse déjà 26 Mo à cause du CSS (2,3 Mo), du HTML (1,9 Mo), de 200 scripts et d'une quinzaine de traceurs publicitaires. La page Films atteint 159 Mo avec les segments Vimeo.
- L'accessibilité est en retrait : focus supprimé, alts vides sur les galeries, aucune règle reduced-motion, cibles tactiles petites, langue inversée.
- SEO : titres descriptifs et canonicals propres, mais absence de H1 sur la home et les Rooms, pas de schema hôtel, `og:image` manquant sur la home, lien de staging indexable dans la nav.

---

## 14. Conclusion

**15 meilleurs éléments**
1. Manifeste de ~70 mots placé avant tout catalogue (« Luxury for the Soul », six piliers).
2. Nommage des lieux par une phrase-monde (« Our Home of Play », « Our Home in a Living Museum »).
3. Possessif de marque étendu à tous les titres de section.
4. Footer par région (Americas / Middle East / Africa) qui matérialise le réseau.
5. Nav secondaire horizontale de 8 entrées sur les pages hôtel, dans un header commun de 52 px.
6. Header transparent → blanc 80 % + blur 20 px, logo réduit au symbole sur mobile.
7. Bloc « Our Stories » avec story épinglée (sticky 700 px sur ~2 000 px) et fond crème `#fff9f2`.
8. Composant img-text : image portrait 620×764 + colonne texte de 300 px centrée, alternée.
9. Galerie Swiper de 12 images par catégorie de chambre au lieu de fiches produit.
10. Ligne de faits minimale « Sleeps 2 | King Bed » + note « adults-only 16+ ».
11. Photographie de communauté (groupes, feu, tablée, rituels) à 60 % des visuels.
12. Bibliothèque de films filtrable par lieu et par pilier (page dédiée, fond #161616).
13. Tiroir « Select Property » au clic BOOK pour une collection de 9 hôtels réservables.
14. Offres packagées en 4 nuits avec inclusions listées et phrase « breakfast and activities included ».
15. Contacts humains explicites par hôtel (téléphone, WhatsApp, deux emails, adresse).

**5 faiblesses / limites**
1. Hero vidéo sans texte ni poster : écran vide si la vidéo ne joue pas ; aucun H1 sur la home et la page Rooms.
2. Liens SynXis avec dates d'arrivée codées en 2023-2024, devise imposée, aucun sélecteur de dates/voyageurs sur le site, aucun prix nulle part.
3. Poids : 26 Mo / 559 requêtes sur la home desktop, CSS de 2,3 Mo, HTML de 1,9 Mo, ~15 domaines publicitaires ; 159 Mo sur Films.
4. Accessibilité : BOOK mobile 48×20, focus supprimé, 44 alts vides sur Rooms, aucune règle reduced-motion, `lang` inversé EN/ES.
5. Hygiène : lien de staging `habisstage22sp.wpengine.com` dans la nav, `http://ourhabitas.com/rise` non-www, double footer de 900 px, footers non révélés en capture.

**10 principes réutilisables**
1. Manifeste avant catalogue quand on vend une appartenance.
2. Une phrase-promesse par lieu, jamais une liste d'équipements.
3. Possessif de marque cohérent sur tous les titres.
4. Header commun + nav secondaire par lieu, CTA de réservation fixe partout.
5. Un seul accent chaud (#796c5c/#807566), la couleur vient des photos.
6. Image portrait 0,81 face à une colonne texte de 300 px, alternée, 125 px d'air.
7. Un seul bloc sticky par page, sur le contenu éditorial, fond crème.
8. Une courbe d'easing unique (expo-out ≈ cubic-bezier(.405,.005,0,1)) pour reveals et hovers.
9. Galerie par catégorie + ligne de faits minimale pour des hébergements atypiques.
10. Tiroir de sélection d'hôtel dans le header pour une collection, avec `nights`/`adult` pré-remplis mais dates libres.

**Éléments propres à la marque à ne PAS copier** : le logo-astérisque ⊛, la signature « Luxury for the Soul », les noms « Caravan … by Our Habitas », « Dis-loyalty », « Rise », « Mantra », le leitmotiv « seven shades of blue », les taglines « Our Home of … », les titres de films et de stories, les textes de manifeste.

**Notes /10**
- **Branding : 8/10** — architecture ombrelle lisible (11 homes, 4 Caravan, footer par région), manifeste et piliers cohérents avec 60 % de photos de communauté ; retenue : rendus 3D non distingués, 4 cartes « Coming Soon » sur 11, home sans H1.
- **Direction artistique : 7/10** — système typographique à trois familles bien réparti (Canela / Arboria / acumin-pro), palette taupe unique, composant img-text discipliné ; retenue : rayons hétérogènes (0/18/20/24), lh 54 px sous un H1 de 60 px, répétition du même bloc 7 fois sur Bacalar.
- **Animations : 5/10** — reveals (15-18/page), hover ×1,05 en 0,6 s, sticky story, accordéons 0,3 s ; retenue : aucune couche avancée malgré Barba chargé, voile texte des cartes inaccessible au tactile, zéro règle reduced-motion, vidéo bloquée sans fallback.
- **UX / navigation : 6/10** — nav secondaire à 1 clic, menu à niveaux avec « Back to… », contacts par hôtel ; retenue : BOOK absent des pages marque, 4 clics jusqu'à une chambre, lien staging, double footer, menu non vérifiable.
- **Conversion : 4,5/10** — CTA hiérarchisés (365×64 outline, liens 118×20), inclusions et remises chiffrées, WhatsApp ; retenue : aucun prix, aucune date sur site, liens SynXis avec dates passées, aucune preuve sociale, moteur non atteint par la sonde.
- **Mobile : 5,5/10** — corps 18 px conservé, logo compact, sections empilées proprement, 14,7 Mo ; retenue : BOOK 48×20, hero 100 vh vide, sticky et hovers perdus, titre « Our Homes » à 45 px.
- **Note globale : 6/10** — un site de **marque** convaincant (vocabulaire, photos, films, réseau) porté par une exécution technique et transactionnelle en retrait (poids, accessibilité, moteur externe mal paramétré, absence de prix). L'écart entre l'ambition narrative et la conversion est le fait principal.

**Ce que ce site apporte que les sites « quiet luxury » (FORESTIS, Seagate, Le Collectionist) n'apportent pas**
- Une **architecture de collection** : cartes de lieux avec phrase-monde, « Coming Soon », footer par région, tiroir de sélection d'hôtel, « nearby homes » en fin de page hôtel.
- Un **branding communautaire** explicite : manifeste, six piliers repris en filtres de films, « family » comme appel à l'action, photos de groupes plutôt que de matières.
- Une **bibliothèque vidéo** structurée (par lieu, par pilier, par programme d'impact) sur fond sombre, distincte des pages de vente.
- Des **mécaniques promotionnelles assumées** : pourcentages, adhésion tierce (Dis-loyalty), tarif résident, day pass, séjours 4 nuits packagés.
- Un **contenu d'impact** intégré à la home (Rise, coraux, reforestation) au même niveau que les hôtels.
- Une **couleur chaude** (taupe/brun + crème) là où les références quiet luxury restent gris/noir/blanc.

---

## Observations clés à conserver pour la phase comparative

- Home = page de marque : 0 H1, 0 chambre, 0 prix, 0 avis ; 7 sections (vidéo, manifeste, 11 homes, itinéraire Mexique, 4 stories, Rise, durabilité) sur 7 758 px desktop / 9 346 px mobile ; 769 mots.
- Hero : iframe Vimeo `background=1&autoplay=1` 1440×810 (90 vh desktop, 100 vh mobile), aucun texte de secours ; bloqué en headless (« couldn't verify the security of your connection ») — non jugeable.
- Typo : Canela 300/400 (60/52/36 px, ls 4,5/2,5/1,7 px) + Arboria 500 capitales 22 px ls 2 px + acumin-pro 300 18/25,2 px ; mobile 26 px titres, 18 px corps.
- Palette : #ffffff / #fff9f2 / #464543 / #807566 / #796c5c ; texte #444444 ; contraste pilules #807566 sur blanc ≈ 4,5:1.
- Composants : img-text 620×764 + colonne 300 px, cartes 410×526, doubles 595×397, CTA outline 365×58-64 rayon 0, pilules 28 px rayon 20, liens 118×20 soulignés, header 52 px blanc 80 % blur 20 px.
- Animation : 18 reveals, 1 sticky (story 682×700 épinglée ≈ 2 000 px), hover scale 1,05 / 0,6 s cubic-bezier(.405,.005,0,1), Swiper ×3-4 par page, aucune règle reduced-motion propre, Barba chargé non observable.
- Réservation : tiroir « Select Property » (9 hôtels) → SynXis chain 30700/33122 avec devises SAR/QAR/EUR/USD/AED, `nights=4`, `adult=2`, dates d'arrivée codées 2023-07-03 / 2023-09-23 / 2024-04-07 ; aucun `dateInput`, aucun prix ; expériences en mailto, restaurant en OpenTable.
- Page Rooms : 3 catégories A-frame (« Sleeps 2 | King Bed »), 12 images Swiper par catégorie, 145 mots, 5 365 px ; page hôtel Bacalar 9 sections dont 1 chambres, 839 mots, 8 780 px.
- Perf : home desktop 559 req. / 26,5 Mo / TTFB 1 010 ms / FCP 2 288 / load 8 238 ; CSS thème 2 329 Ko ; HTML 1 907 Ko ; Films 1 907 req. / 159 Mo ; mobile home 300 req. / 14,7 Mo.
- A11y/SEO : focusOutlineNone ≥ 200, 44 alts vides (Rooms), BOOK mobile 48×20, `lang="es"` sur pages EN, h1count 0 sur home/rooms, JSON-LD WebPage sans Hotel, lien staging wpengine dans la nav.
- Copy : possessif « Our » sur tous les titres, « home » pour hôtel, « family/community/like-minded », leitmotiv « seven shades of blue » ×4 pages, six piliers (music, wellness, art, adventure, food, learning) réutilisés comme filtres.
- Photo : 60 % scènes humaines (groupes, feu, tablée, rituels), golden hour, aériens drone ; 2 PNG de rendus 3D NEOM (1 067 + 647 Ko) sur la home.
- Offres : 5 sur Bacalar, inclusions « breakfast and activities included », Dis-loyalty 35 % / 20 % / 10 %, séjour 4 nuits packagé, tarif résident, day pass.
- Nav : header commun + nav secondaire 8 entrées par hôtel ; menu à 3 niveaux « Back to… » (non capturé) ; BOOK absent des pages marque (films, signature, loyalty, contact).
- Mobile : sticky et hovers perdus, logo réduit à ⊛ au scroll, docHeight +20 %, cibles 20 px, hero 100 vh vide.
