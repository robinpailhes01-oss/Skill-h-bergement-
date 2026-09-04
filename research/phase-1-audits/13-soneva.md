# Fiche d'audit — Soneva (Maldives)

Clé : `soneva` · Analyse du 2026-09-04 · Chromium headless via Playwright, 1440×900 (desktop) et 390×844 DPR 2 (mobile). Série 2 « au-delà du quiet luxury » : slow luxury, storytelling sensoriel, groupe multi-resorts.

---

## 0. En-tête

**Nom** : Soneva (Soneva Fushi — Baa Atoll, Soneva Jani — Noonu Atoll, Soneva Secret — Haa Dhaalu Atoll ; siège Soneva Management (DIFC), Dubaï). **URL de départ** : https://soneva.com/. Positionnement affiché : « Luxury Resorts in the Maldives », « Barefoot Luxury » devenu « Bare Luxury », signature « Just What Matters. ».

### Pages étudiées

| Label | URL | Desktop | Mobile |
|---|---|---|---|
| home | https://soneva.com/ | oui (+ balayage `home-sweep` 15 paliers) | oui |
| rooms / villas (liste) | https://soneva.com/villas/ | oui | oui (`villas-mobile`) |
| room-detail (villa) | https://soneva.com/villa/soneva-fushi-3-bedroom-residence-with-pool-villa-14/ | oui | oui |
| resorts (collection) | https://soneva.com/resorts/ | oui | non |
| resort (Soneva Fushi) | https://soneva.com/resorts/soneva-fushi/ | oui | non |
| experiences | https://soneva.com/experiences/ | oui | non |
| dining | https://soneva.com/dining/ | oui | non |
| spa / wellness (Soneva Soul) | https://soneva.com/wellness/ | oui | non |
| about (Our Story) | https://soneva.com/about-soneva/ | oui | non |
| contact | https://soneva.com/contact-us/ | oui | non |
| offers | https://soneva.com/offers/ | oui | non |
| booking v1 (heuristique) | https://soneva.com/responsibility/covid-19-updates/ → **404** | non exploitable | — |
| booking v2 (sonde clic « Book » sur la home) | https://soneva.com/#/booking/destination/dates (reste sur soneva.com) | oui | non |

### Limites de l'observation

- **Mega-menu jamais capturé** : toutes les captures `*-05-menu-open` montrent le panneau « Customise Consent Preferences » de CookieYes (le clic de sonde a touché « Customise »). Dimensions et contenu du menu viennent du DOM seul. Sur mobile, `home-mobile-05-menu-open` est identique au hero : navigation mobile non vue.
- Même cause pour `home-04-reduced-motion` ; reduced-motion connu par le CSS seulement.
- Vidéos : aucune balise `<video>` ; heros = iframes Gumlet (`background=true&autoplay=true&loop=true&muted=true&playsinline=false`, 1600×900). Playlists HLS demandées (200/206, 0–2 Ko) mais lecture non vérifiable ; les captures montrent le poster. Effet de `playsinline=false` sur iOS : **hypothèse** non testable.
- Sonde booking v2 : le clic sur « Book » (`href="#/booking/destination/dates"`) n'a produit ni navigation, ni nouvel onglet, ni surcouche visible (`booking-06-booking-step1` = hero) ; seuls deux champs cachés `hotel` et `arrive` sont apparus dans le DOM. **Aucune requête vers azds** dans le journal réseau : le moteur newbooking.azds.com indiqué par le brief est une **hypothèse** non observée ; ses étapes, prix et identité visuelle n'ont pas pu être vus.
- Page wellness : ≈1 000 px vides sous « Visiting Wellbeing Specialists » dans la capture (révélation non déclenchée). LCP `null`, pas de Lighthouse, transitions de page et Lenis non ressentis, curseur tactile non testé.

---

## 1. Positionnement de marque

**Faits observés**
- `<title>` home « Luxury Resorts in the Maldives | Discover Soneva » ; meta : « …private overwater or beach villas… sustainable barefoot living. Book direct for exclusive offers. »
- H1 « Welcome to Soneva » ; kicker « Just What Matters. » puis manifeste Moulin 32 px (≈110 mots) ; H2 « Our Resorts », « Returning to What Matters », « Summer at Soneva », « Awards », « Just What Matters. ».
- Architecture de marque : ombrelle Soneva + trois resorts à égalité en trois cartes 448×560 ; page `/resorts/` H1 « Three Distinct Worlds, All Soneva » (en #012531) et texte « what changes is the setting. What doesn't is that feeling… ». Chaque resort a une phrase-chapitre : Fushi « The original chapter of island life made for all ages », Jani « An energising chapter… », Secret « A hidden chapter… where privacy isn't a feature. It's the whole point. »
- Contexte resort : header 97 → **159 px**, logotype « SONEVA FUSHI · MALDIVES », sous-nav (Villas · Experiences · Wellbeing · Soneva Stars · The Den · Dining · Offers), lien « Return to homepage » dans le menu.
- About : H1 « The Pioneer », texte « A Gentle Evolution » (1995, Barefoot Luxury → Bare Luxury), onglets Vision / Mission / Promise / Values sous « To Pioneer Luxury That Matters. ».
- Preuve : bloc « Awards » sur home, about, resort, villa (World's 50 Best Hotels 2025, Michelin 2025, Forbes Travel Guide, Condé Nast Traveller 2025). « Soneva Stars » : calendrier d'invités nommés (chef, astronome, sportif) avec dates.
- Cible visible : familles multigénérationnelles (« made for all ages », The Den, « Children stay and dine for free », villas jusqu'à 9 chambres / 18 personnes), couples (« Romance Away »), longs séjours (« The Resident », 15 nuits ou plus). WhatsApp, WeChat QR, Baidu et LINE chargés → marchés asiatiques adressés.
- Aucun prix sur aucune page de marque, ni sur 21 cartes villas, ni sur 13 offres.

**Interprétation** : Soneva vend une philosophie de la soustraction (« the deliberate removal of everything that does not serve to reveal Just What Matters ») et s'approprie le mot « luxury » en le qualifiant, là où FORESTIS l'évite. Gamme ultra-luxe signalée par les preuves, les surfaces (272–2 280 m²) et les inclusions, jamais par un prix. Territoire : nature-hôte, pieds nus, émerveillement enfantin ; personnalité chaleureuse et ludique (« Flying Sauces », « Tipsy »). Différence avec un site hôtelier générique : navigation par piliers et par resorts, villas décrites par des faits durs sans tarif, manifeste avant toute offre. Cohérence mots/images/interactions élevée ; la rupture attendue est au moteur (rubrique 8).

**Enseignements** : promesse formulée comme une soustraction ; une phrase-chapitre par lieu ; hôtes et invités nommés ; bloc de preuve répété ; canaux de contact adaptés aux marchés.

---

## 2. Première impression (5 premières secondes)

**Faits observés**
- `home-00-initial` : poster de jungle plein écran, logotype blanc centré, « Menu » à gauche, H1 48 px blanc (y≈393), bandeau 684×60 flouté (Destination « Select Resort » · Dates « 4 Sep, 2026 – 11 Sep, 2026 » · Guests « 1 adult • 0 children » · loupe 55×54). Bannière CookieYes 440×295 en bas à gauche. Pas de préloader.
- `home-01-hero` : autre plan (lagon, mariés sur la plage) → la vidéo enchaîne plusieurs plans (**hypothèse**). Bouton « revisit consent » 45×45 #6d2e1d permanent en bas à gauche.
- « Book » (64×49, #6d2e1d) **absent du hero desktop** (`site-header--transparent`) ; il apparaît au premier palier (`home-sweep-01`, y=497) avec header opaque #f4f1e9 et logo réduit au soleil #e6b33c.
- Mobile : logo + wordmark blancs, H1 36 px, bandeau réduit à « Destination » + loupe en bas de viewport ; pas de « Book ».
- 504 mots indexables (424 sur mobile).

**Interprétation** : on voit une île sans bâtiment ; on comprend « une destination, pas un hôtel » ; on ressent la traversée (« the crossing begins » ouvre le manifeste). Le premier CTA est la loupe, pas un verbe. La bannière cookies occupe 15 % de l'écran et a parasité trois sondes ; un visiteur qui clique « Customise » subit un modal plein écran. Raison de continuer : l'absence de « Book » visible et la promesse d'un texte typographique juste sous l'image.

**Enseignements** : révéler le CTA au premier scroll quand le hero est contemplatif ; bannière cookies compacte ; tester la première frame.

---

## 3. Direction artistique

**Faits observés**
- Variables du thème : `--soneva-secondary-linen-haze:#f4f1e9`, `--soneva-primary-blue-hour:#012531`, `--soneva-accent-golden-ember:#e6b33c`, `--soneva-secondary-driftwood:#644e47`, `--soneva-secondary-sunshadowed:#9a9080`, `--soneva-font-title: Moulin Trial, Georgia, serif`, `--soneva-font-body: Scto Grotesk A Trial, system-ui`.
- Fonds : #f4f1e9 (2 778 éléments home), #19100d (388 : footer, panneaux sombres), #19100d a=0.1 (chips). Textes : #19100d, #19100d a=0.5 (descriptions 14 px), #fffffe, #fffffe a=0.5 (intitulés footer), #012531 (liens menu), #6d2e1d (liens contact).
- Boutons : pleins #6d2e1d/#fff radius 2 px (Book 64×49, Learn more 102×49, Check availability 139×49, Book now 92×49) ; outline 1 px blanc sur photo (Explore 81×51) ou #6d2e1d a=0.5 sur fond clair (Download Floor Plan 160×51) ; loupe 55×54 ; flèches rondes 40×40 ; points 6 px ; onglets texte 400×35.
- Typographie : **Moulin Trial 300** (titres et manifestes), **Scto Grotesk A Trial 400/500** (corps, kickers, boutons). Suffixe « Trial » dans les noms et fichiers (`Moulin-Light-Web.woff2`, `Scto Grotesk A Regular.woff`) : fait ; licences d'essai en production : **hypothèse**. 5 fichiers, 40 Ko.
- Échelle desktop : H1 48/52.8, −1.44 px ; H2 40/44, −1.2 ; H3 resorts 32/35.2 ; H3 cartes 24/26.4 ; manifeste 32/35.2 ; corps 16/19.2 ; cartes et boutons 14/16.8 ; footer 12. Mobile : 36.18 / 28.18 / 24.09 / manifeste 24.09 / corps 14.05 / kickers 12.05 (décimales → **hypothèse** `clamp()`). Aucune capitale hors logotype.
- Grille : conteneurs 1 140–1 188 px, marges 40 px ; grilles 3×448 (villas), 4×334 (offres, expériences). Ratios : cartes villas 1.5, offres ≈1.2, originals/expériences 0.8, awards 1.0, menu 0.42, hero villa 1.33.
- Asymétrie réservée aux sections « vie » : collage « Summer » (360×396, 240×265, 226×250, 226×248 débordant des marges), « Your Hosts » (560×400, 320×361, 320×305). Sections commerciales en grilles régulières.
- Iconographie quasi nulle (burger, loupe, flèches, croix, soleil) ; aucune illustration ni texture ; filigrane « SONEVA » ≈300 px en bas du footer. Photos : dominantes teal, sable, ocre ; grain et flou de bougé assumés.

| Token | Valeur | Usage |
|---|---|---|
| bg-base / bg-dark | #f4f1e9 / #19100d | pages ; footer, piliers |
| text-primary / secondary | #19100d / à 50 % | titres ; descriptions (3.45:1) |
| primary-cta | #6d2e1d → hover #012531 | Book, Learn more, Check availability |
| accent | #e6b33c | soleil du logo au scroll, `is-today` du datepicker |
| font-title / body | Moulin 300 / Scto Grotesk A 400–500 | 48-40-32-24 / 16-14-12 |
| radius | 2 px ; 1000 px (flèches) ; 50 % (dots) | |
| header | 97 px (159 px en contexte resort) | fixed, transparent → #f4f1e9 |
| transition-fast / reveal / long | 0.2 s ; 0.45 s cubic-bezier(.33,1,.45,1) ; 1.2–1.6 s | boutons ; textes ; images |

**Interprétation** : palette de matière (lin, bois flotté, heure bleue, braise), un seul accent pour l'action, la couleur vive vient des photos. Deux familles suffisent : le Moulin 300 sert titres et paragraphes, la hiérarchie est faite par la taille. Radius 2 px et outlines 1 px rapprochent les composants de l'imprimé. La DA alterne magazine (collages) et catalogue (grilles).

**Enseignements** : deux familles, un accent, un fond lin ; asymétrie réservée aux sections de vie ; tokens nommés avec le vocabulaire de la marque.

---

## 4. Architecture de la page d'accueil

Desktop 7 512 px, mobile 7 002 px CSS.

| Position (y) | Section | Objectif | Contenu | Interaction | CTA | Émotion |
|---|---|---|---|---|---|---|
| 0–900 | Hero vidéo | situer, ouvrir la réservation | iframe Gumlet, logo, H1 48 px, bandeau Destination/Dates/Guests | boucle, header transparent, `<details>` datepicker | loupe | arrivée par la mer |
| 900–1 700 | Manifeste | poser la philosophie | kicker + 2 paragraphes Moulin 32 px (≈1 180 px de large) | révélation 0.45 s (texte à 20 % sur `home-sweep-01`) | — | lenteur |
| 1 700–2 350 | Our Resorts | hiérarchiser la collection | 3 cartes 448×560, H3 32 px blanc, phrase-chapitre | — | 3 × Explore outline | choix du chapitre |
| 2 354–3 157 | Panneau piliers | marque | image 1440×803 (hamac de catamaran), 5 onglets à barre de progression, H2 blanc, para 576 px | carrousel Slick par onglets | About Soneva outline | contemplation |
| 3 160–4 200 | Summer at Soneva | saison, vie | collage 4 photos + para 560 px | clip-path 1.2–1.6 s | Explore plein | joie, famille |
| 4 200–4 730 | Awards | preuve | H2 gauche, para droite, 3 tuiles 356×356 | carrousel | — | crédibilité |
| 4 731–6 531 | Fermeture « Just What Matters. » | réserver | image 1440×1800 (apnéiste + raie manta), H2 blanc, bandeau | **bandeau épinglé** (`div.row` h=148) de y≈4 470 à 5 463 | loupe | immersion → acte |
| 6 531–7 431 | Footer | sortie, capture | 5 colonnes, newsletter 3 champs, filigrane | — | flèche | appartenance |

**Logique narrative** : traversée → credo → choix du lieu → ce que la marque défend → ce que l'on y vit → pourquoi la croire → plonger et réserver → rester en contact. L'offre est concrète au hero puis seulement en fin de page ; aucune villa, aucun prix sur la home : elle vend l'envie d'ouvrir une page resort. Mobile : resorts en carrousel 1 carte + 3 points ; piliers recadrés 390×747 sans titre visible ; collage réduit à 4 vignettes ≈85 px ; fermeture recadrée 390×1 688 (ratio 0.23) ; newsletter en tête de footer.

---

## 5. Scroll et storytelling

**Faits observés**
- `libs` : Lenis + Slick + jQuery + WordPress ; GSAP/ScrollTrigger/Locomotive/Webflow/Lottie absents. `animAttrs` : reveal 3–4, parallax 1, horizontal 1, splitText 0 (home) / 106 (villas) / 17 (villa) / 20 (dining). CSS : clip-path 41, will-change 26, sticky 11, backdrop-filter 27, scroll-snap 0, scroll-timeline 0.
- Balayage home (15 paliers) : 1–6 transforms, 0–8 opacités partielles (pic à y=1 987, entrée des piliers), 1–4 clip-path (y=3 477–4 470), un élément épinglé de 4 470 à 5 463. Villa : 11 transforms / 10 opacités à y=2 987 (carrousel « Discover Other Villas ») et image `amenities__media` sticky (640×773) de 1 494 à 2 987. `/resorts/` : titre `media-header__inner` sticky (1440×420, z 2) au-dessus de l'image de hero. Villas mobile : barre de filtres sticky (390×83, z 1024).
- Alternance de fonds identique sur toutes les pages : clair → photo pleine largeur sombre (piliers) → clair → photo pleine largeur (fermeture) → footer sombre. Le `body` reste #f4f1e9.
- Header transparent sur le hero, opaque dès le premier palier. Scroll horizontal = carrousels Slick uniquement. Contact : aucun effet.
- Densité : home 7 sections / 7 512 px ; villas 9 612 px dont ≈4 800 px de grille ; experiences 13 718 px (35 cartes) ; contact 3 612 px.

**Effets et fonctions** : révélation par lignes (opacité 0.2→1, 0.45 s, easeOut) = rythme et regard ; clip-path des collages = émotion, marque ; image sticky des inclusions = expliquer ; bandeau épinglé dans l'image de fermeture = action au moment d'émotion maximale ; onglets piliers = compression de 4–5 messages ; Lenis = **hypothèse** d'inertie qui étire les 0.45 s ; parallaxe détectée (1) mais non visible dans les captures.

**Interprétation** : le storytelling est porté par l'alternance clair/sombre, la typographie 32 px et la place des photos, pas par une chorégraphie GSAP. Les effets sont rares et placés (deux images pleine largeur par page), avec des respirations de 250–400 px.

**Enseignements** : deux images pleine largeur par page, une pour la marque, une pour l'action ; épingler le formulaire dans la seconde ; révéler les textes longs par lignes ; garder le contact sans effet.

---

## 6. Animations et micro-interactions

| Animation | Déclencheur | Élément | Effet | Fonction | Risque UX |
|---|---|---|---|---|---|
| Vidéo hero | chargement | iframe Gumlet | boucle muette multi-plans | émotion | ≈1.2 Mo de JS lecteur ; `playsinline=false` mobile |
| Bannière cookies | chargement | CookieYes 440×295 | apparition | légal | masque le bandeau mobile ; modal plein écran |
| Révélation titres/manifestes | entrée viewport | spans de lignes | opacité 0.2→1 + translateY, 0.45 s, cubic-bezier(.33,1,.45,1) | rythme | texte lu à 20 % si lecture rapide |
| Révélation d'images | entrée viewport | clip-path (41 règles) | 1.2–1.6 s | émotion | lenteur perçue mobile |
| Zoom photo cartes | hover | — | non mesuré | — | — |
| Transitions de page | clic | — | aucune (pas de préloader) | — | rechargement complet |
| Curseur | — | `cursorEls []` | aucun | — | — |
| Hover « Book » | hover | `.booking-btn` | #6d2e1d → #012531, bordure #7a4d12, 0.2 s | feedback | — |
| Hover liens menu | hover | `Resorts`, cartes | couleur 0.3 s ease-in, `::before` 336 px | orientation | non capturé |
| Hover logo resort | hover | `.navbar-brand` | #012531 → #6d2e1d, 0.3 s linear | feedback | — |
| Carrousels | flèches / points | Slick (galerie villa 9 slides, autres villas 8, originals 7, awards 4) | glissement, `cubic-bezier(.67,.17,.4,.83)` | expliquer | défilement manuel long |
| Onglets piliers | clic | 4–5 onglets à barre de progression | changement image + texte ; autoplay **hypothèse** | marque | contenu masqué sans clic |
| Filtre villas | select | grille Ajax | spinner `lds-ring 1.2s cubic-bezier(.5,0,.5,1)` | expliquer | attente non chiffrée |
| Bandeau épinglé | scroll | `div.row` h=148 (135 mobile) | reste 1 000 px | action | recouvre l'image |
| Image sticky inclusions | scroll | `.amenities__media` | reste pendant la liste | expliquer | désactivé mobile |
| Filtres villas mobile | scroll | `.raiser-filter` 390×83 | sticky z 1024 | action | — |
| Header | scroll > 0 | `.site-header` | transparent → #f4f1e9, logo → soleil | orientation | changement abrupt (non mesuré) |
| Reduced motion | media query | 27–31 règles (`.slick-button{transition:none}`) | ne coupe que Slick/Bootstrap | a11y | révélations non conditionnées (**hypothèse**) |

Easings CSS : `cubic-bezier(.33,1,.45,1)` (17–50 usages), `(0,0,.2,1)` (6), `(.67,.17,.4,.83)`, `(.22,1,.36,1)`, `(.65,0,.35,1)`, `(.55,0,1,.45)`, `(.49,.78,.46,1.34)` (8, Gravity Forms). Durées : 0.2 s ×78, 0.3 s ×44, 0.15 s ×15, 1.2/1.25/1.35/1.6 s pour les révélations.

**Interprétation** : trois familles d'animation (révélation, glissement, état de bouton) et un easing signature ; ni préloader, ni transition de page, ni curseur. **Enseignements** : un easing et deux durées suffisent ; conditionner toutes les révélations à `prefers-reduced-motion`.

---

## 7. Navigation et architecture de l'information

**Faits observés**
- Header fixed 97 px : « Menu » (x=25), logo centré, « Book » 64×49 à droite. Mega-menu (DOM) : fixed 1440×803 à y=177, fond #f4f1e9 ; Resorts (3 cartes 336×799 « Explore » + phrase-chapitre), Villas, Experiences, Wellbeing, Dining, Soneva Stars, Offers, Our Story, Celebrations & Events, Contact Us ; réseaux ; Stewardship, Newsroom, Travel Partners, Careers ; +960 660 4300, reservations@soneva.com, Whatsapp, WeChat ; T&C, Privacy. Overlay plein écran #f4f1e9 z −1.
- Contexte resort : header 159 px, sous-nav de 7 entrées vers `/resorts/soneva-fushi/villas/` etc., « Return to homepage ».
- `/resorts/` : H1 sticky sur image, 3 cartes, 4 offres avec « Book now » 92×49, fermeture. `/experiences/` : filtre Resort + Category, 35 cartes 0.8 avec double pastille (resort + catégorie : Wellbeing, Beyond the island, On the water, Beneath the stars, Under the canopy, On the sand, Created by Soneva), liste « Soneva Stars » (5 invités, discipline, dates), « Browse Experiences by Resort ».
- Chemins : villa = Menu → Villas (2) ou home → Explore resort → Our Villas → liste → villa (3) ; offre = Menu → Offers → Learn more (2) ; réservation = loupe du hero (0) ou « Book » après scroll (1). Page villas : onglets Signature / Overwater / Beach, 4 filtres, Reset, Compare villas, 21 cartes + Load more, pastille resort par carte ; mobile : bouton « Filters » + « Compare villas » sticky.
- Contacts humains : menu, footer, page contact (directeurs nommés avec e-mail et ligne directe, siège Dubaï, sélecteur de marché).
- Frustrations : 404 « covid-19-updates » encore liée ; `h1count 0` sur resort et contact ; villas 9 612 px sans retour haut ; burger non identifié par la sonde mobile (bouton « Menu Close » 62×24 présent) ; `user-scalable=no`.

**Interprétation** : IA double, transversale par thème et verticale par resort, réconciliée par les pastilles sur chaque carte. Le mega-menu sert aussi de page contact. 2–3 étapes vers une villa ; vers un prix, inconnu tant que le moteur n'est pas ouvert.

**Enseignements** : doubler la navigation (thème × lieu) et marquer chaque carte du lieu ; contacts humains dans le menu ; « Compare » au-delà de dix unités ; filtres sticky sur mobile.

---

## 8. Parcours de réservation et conversion

**Faits observés**
- Type : **moteur transactionnel externe (hypothèse azds, non observé)** précédé d'un assistant in-page. Le CTA « Book » est une route hash `#/booking/destination/dates` (villa : `#/booking/step-1` ; loupes des bandeaux : `#/booking/step-2`). En headless, le clic n'a ouvert aucune surcouche visible et n'a lancé aucune requête vers un domaine de réservation ; le DOM a gagné deux champs cachés `hotel` et `arrive`. Aucun `target=_blank` (`newTab false`).
- Bandeau de réservation : présent deux fois par page (hero + fermeture épinglée), formulaire `<details>` avec Destination (select), Dates (daterangepicker « CancelApply », `is-today` en `$bronze`), Guests (adults / children en `number`), champs cachés `hotel_id`, `hotel_name`, `adults`, `children`. Dates pré-remplies J → J+7 (4–11 sept.), 1 adulte. En contexte resort, la tuile Destination disparaît. Mobile : une seule tuile (Destination) + loupe.
- Formulations : « Book » (header), loupe sans libellé (bandeaux), « Check availability » (villa), « Learn more » (offres), « Book now » (offres sur `/resorts/`), « Explore » (découverte). Distinction découvrir / vérifier / réserver lisible.
- Prix : **aucun** sur home, resorts, villas, villa, offres. Inclusions : liste de 7 sur la villa ; « Best Price Guarantee » et « Book direct » dans la meta et l'intro des offres (« Choose What Feels Right »). Offres : 13 cartes avec pastilles « For Families », « Limited Time », « Early Bird », date « Available until December 20, 2026 », mécaniques nommées (« Stay Longer On Us », « The Resident » = tarif pour 15 nuits et plus, « Island to Island »).
- Réassurance : awards ×4, hôtes nommés (page resort), directeurs joignables (contact), villa manager (inclusions). Aucun avis client, aucune note, aucun logo de paiement ou de politique d'annulation visible.
- Contact humain : +960 660 4300, reservations@soneva.com, WhatsApp (`wa.me/9607223378`), WeChat QR, formulaire Gravity (8 champs dont dates d'arrivée/départ et 3 selects, reCAPTCHA), promesse « within 24 hours » (meta contact).
- Conciergerie / services : inclusions villa, « Soneva Stars », Celebrations & Events (menu), pas de module de services additionnels avant le moteur.
- Points de rupture attendus (**hypothèse** faute d'observation) : changement de domaine vers azds, perte de la vidéo/typographie, arrivée des prix seulement à cette étape ; risque de non-ouverture de l'assistant si le routeur hash échoue (constaté en headless).

**Interprétation** : le site optimise l'entrée (deux bandeaux, un épinglé, un « Check availability » par villa) mais reporte toute qualification tarifaire hors du site. La conversion repose sur l'émotion et la preuve institutionnelle ; la réassurance transactionnelle (prix, annulation, acompte, avis) est absente des pages de marque.

**Enseignements** : bandeau in-page qui pré-remplit destination/dates/invités avant le moteur ; bandeau répété en fermeture épinglée ; « Check availability » plutôt que « Book » sur l'unité ; nommer les mécaniques d'offre ; ajouter au moins une réassurance transactionnelle avant la sortie du site.

---

## 9. Pages chambres / propriétés

**Objet vendu** : une villa nommée et numérotée, à la nuit, dans un resort précis ; la page prépare un « Check availability » sans prix ni disponibilité.

### Liste (/villas/) — desktop 9 612 px, mobile 14 665 px

- Hero vidéo (apnéiste), kicker « Villas at Soneva », H1 « Living Without Boundaries », bandeau complet (mobile : Destination seule).
- Intro « A World of Your Own » Moulin 32 px (≈60 mots). H2 « Our Villas » 48 px + onglets typographiques 32 px (Signature / Overwater / Beach ; inactifs a=0.5) + deux images (chef 195×270, villa aérienne 453×803) + paragraphe par onglet (« Big enough for your whole crew. Private enough for each of you… »). Mobile : onglets en carrousel à points, images empilées.
- Filtres : Resort, Villa Type, Bedrooms, Features (+ Reset, Compare villas) ; mobile : bouton « Filters » 390×83 sticky + « Compare villas ».
- Grille 3×448 (mobile : 1 colonne 358×377) ; carte = pastille resort, ligne de faits « Sleeps 9 Adults (6 Adults 3 Child) • 3 Bedrooms • 1,370 m² », H3 24 px (20 px mobile), description 3 lignes 14 px (12 px mobile) à gabarit lieu → sensation → équipements → rythme. 21 cartes + Load more ; 272 m² (1 Bedroom Crusoe) à 2 280 m² (6 Bedroom Estate), un 9 Bedroom Estate ; 2 à 18 personnes. Aucun prix.
- Perf : desktop 546 requêtes / 19.9 Mo / load 26.8 s / TTFB 1.6 s (page la plus lourde) ; mobile 283 requêtes / 12.3 Mo / FCP 928 ms / load 3.5 s.

### Détail (Villa 14) — desktop 7 503 px, mobile 6 785 px

- Header resort 159 px (97 mobile). Hero scindé : image 865×649 (aérienne nocturne) + ligne de faits « Sleeps 9 Adults (6 Adults 3 Child) • Signature Villa • 1,370 m2 », H1 48 px, description 16 px, cinq chips « libellé / valeur » (Bedrooms 3 · Children's Room · Private Gym · Steam and Sauna Room · Spa Room) sur #19100d a=0.1, CTA « Check availability » 139×49 à y=735 (mobile : image 382×255 pleine largeur, H1 36 px, CTA à y=755, visible dans le premier écran et demi).
- Carrousel 9 slides 1050×700 (mobile 350×242), points 6 px + flèches 40×40 ; légendes H3 12 px « www.sandrobruecklmeier.com » (crédit photographe rendu en titre : 4 H3 parasites).
- Éditorial Moulin 32 px centré (« rustic-chic », « thatch, bamboo and sustainable woods », « swinging hammock ») + « Download Floor Plan » / « Download Resort Map » (160×51, 171×51).
- « Complimentary Inclusions » : 7 lignes à filets (Villa Manager & villa attendant ; Children stay and dine for free ; 24/7 unlimited chocolates, ice creams… ; Dedicated transport ; The Den ; Complimentary wellbeing experiences ; Bicycles & tricycles) avec image sticky 640×773 (désactivée mobile) et bande de 5 vignettes.
- « Discover Other Villas » : 8 cartes du même resort + « View all villas » ; Awards (Condé Nast Traveller 2025) ; fermeture avec bandeau Dates + Guests ; footer. Meta description cite « wine cellar and study », absents des chips.
- Perf : desktop 471 requêtes / 19.0 Mo dont 11.4 Mo d'images (160 fichiers, max 1 104 Ko, JPG 2021) ; mobile 168 requêtes / 4.9 Mo / FCP 1.2 s.

**Interprétation** : ordre faits → sensation → réassurance concrète → alternatives, inverse des sites « quiet luxury ». Plan et carte téléchargeables sont des outils de projection rares. L'absence de prix sur 1 370 m² reporte la qualification sur le moteur ; la réassurance est humaine et institutionnelle, sans avis. Le mobile conserve tout, perd le sticky et descend à 12 px.

**Enseignements** : ligne de faits standard (capacité éclatée • type • m²) sur carte et page ; chips libellé/valeur ; inclusions en phrases de bénéfice ; plan + carte ; alternatives du même lieu ; filtres sticky mobile.

---

## 10. Copywriting

**Faits observés**
- Deuxième personne, présent, phrases courtes juxtaposées (« The world slips away. Barefoot in the sand, salt air on your skin, time softens with the tide. »). Mots pivots : matter/matters (signature, « Returning to What Matters », « Luxury That Matters »), slow, unfold, rhythm, shaped by, gentle, quiet, whole.
- Titres de 2–5 mots sans capitales, souvent en opposition (« Living Without Boundaries », « Guided by Nature, Grounded in Balance », « Endorphins, Earned », « Gather, Your Way », « Choose What Feels Right », « Three Distinct Worlds, All Soneva »). Kicker fonctionnel au-dessus (« Villas at Soneva », « Tables to Travel for », « The Soulful Playground », « A Gentle Evolution ») : le kicker nomme, le titre émeut.
- Champ sensoriel : sable, sel, marée, lumière, silence, ombre, brise ; corps (barefoot, skin, mind) ; enfance (laughter, wonder, play, slide). Le luxe est nommé mais restreint (« the most meaningful luxuries are often simplest », « Bare Luxury is not minimalism, nor absence »).
- Technique reléguée à la ligne de faits et aux chips ; chiffres-preuves rares (« more than a dozen options », « 24-hour treat rooms », « thirty years », « 15 nights or more »).
- Prestation → expérience : restaurants nommés par attitude (« Out of This World », « Flying Sauces », « Tipsy », « Primitive »), spa ouvert par une question (« what does your body need today? »), expériences classées par lieu d'émotion (« Beneath the stars », « Under the canopy », « Beyond the island »), villas = « chapters » et « worlds ».
- CTA : « Explore », « Learn more », « Check availability », « Book », « Book now », « View all villas », « Download Floor Plan ». Rareté uniquement par pastilles (« Limited Time », « Early Bird »). 404 : « It looks like this page drifted away. »
- Longueurs : manifeste ≈110 mots ; intros 40–70 ; cartes 25–35 ; wellness 326 mots indexables. Coquille : `<title>` « Wellbeing at Sonveva ».

**Interprétation — mécanismes** : (1) signature de 3 mots en H2 de clôture de chaque page ; (2) kicker + titre ; (3) description de villa en quatre temps ; (4) « pas X, mais Y » pour définir le luxe ; (5) noms propres pour les prestations (Originals, The Den, Soneva Soul, Soneva Stars) ; (6) inclusions écrites en bénéfices ; (7) catégories d'expériences par lieu sensoriel. Le copywriting installe la lenteur que l'animation ne fait pas.

**Enseignements** : signature répétée en clôture ; kicker + titre ; gabarits ; nommer ses prestations ; taxonomie sensorielle.

---

## 11. Photographie et vidéo

**Faits observés**
- Plans : aériens zénithaux (cartes resorts, hero offers, awards, potager) ; sous-marins (fermeture manta, hero villas, hero experiences avec plongeur et raies) ; portraits d'hôtes en action (Nuha, Naifa, Zakia) ; détails mains (noix de coco, pinceau, cueillette, Tok Sen) ; nuit (observatoire, dîner aux lanternes, cinéma sur l'eau) ; crépuscule (enfants sur ponton, table sur sable).
- Lumière naturelle, contre-jour, heure dorée, bougie ; grain et flou de bougé assumés (hero resort : visage au soleil avec bokeh ; spa : femme suspendue floue).
- Humain : 5 alts sur 8 échantillonnés sur la home décrivent des personnes ; cartes villas et carrousel intérieur sans personne ; l'humain revient dans les inclusions et les hôtes. Proportion lieu/expérience : home ≈30/70, villas liste ≈90/10, villa ≈70/30, dining/wellness/experiences ≈20/80.
- Ratios : hero 16:9 ; cartes 3:2 (villas), 4:5 (originals, expériences, resorts), 1:1 (awards), 0.42 (menu). Vidéos : 4 embeds Gumlet (home, villas, resort, dining), arrière-plan, une par page, hero uniquement ; absentes sur wellness, about, villa, offers, contact, experiences, resorts.
- Poids : posters 245–645 Ko ; villa 1 104 Ko (JPG 2021) ; resort 577 Ko ; spa 404 Ko ; formats WebP minoritaires ; srcset sur 6–30 images. Alts : 0 manquant, 19–49 vides (décoratifs), alts renseignés descriptifs (~80 caractères).

**Interprétation** : la photo raconte des instants, l'architecture est montrée du ciel (abstraite, trame île/lagon) ; grain et flou signalent le vif, les intérieurs de villa restent du catalogue. La vidéo est un décor.

**Shot list** : (1) vidéo hero 16:9 30–60 s, 3–5 plans lents, muette, boucle propre ; (2) zénithal drone de chaque unité, même heure ; (3) aérien oblique de nuit villa éclairée ; (4) 8–10 intérieurs par villa dont un portrait 4:5 ; (5) 3 portraits d'hôtes en action par lieu, nom et rôle ; (6) enfants en contre-jour (ponton, toboggan) ; (7) détails mains + objet ; (8) sous-marin avec faune ; (9) table sur sable au crépuscule, dîner aux bougies ; (10) potager et cuisine vus du ciel ; (11) ciel de nuages doré et ciel étoilé ; (12) une image « joie flou » par page.

---

## 12. Mobile

**Faits observés** (390×844, DPR 2)
- Hero : vidéo Gumlet 1500×844 (`playsinline=false`), logo + wordmark 240×110, H1 36.18 px, bandeau à une tuile + loupe 55×54 en bas de viewport, pas de « Book ». Header 97 px fixed : « Menu » 62×24, « Book » 64×49 après scroll. Menu : fixed 390×747 à y=172 (non capturé).
- Titres : H2 28.18, H3 24.09, cartes 20 px, manifeste 24.09/26.5 aligné à gauche (358 px), corps 14.05, kickers 12.05, descriptions de cartes 12.05.
- Rythme : home 7 002 px ; villas 14 665 px (21 cartes en colonne) ; villa 6 785 px. Resorts et onglets villas en carrousels Slick à points 6 px ; piliers recadrés sans titre ; « Summer » = 4 vignettes ; fermeture 390×1 688.
- Animations conservées (0.45 s ×551, clip-path 42, backdrop 33) ; balayage : 1–5 transforms, 0–6 opacités, `div.row` épinglé h=135 (y≈3 787–4 418) ; sticky inclusions supprimé ; filtres villas sticky ajoutés.
- Boutons : Book 64×49, Explore 81×51, loupe 55×54, Learn more 102×49, Check availability 139×49, Filters 390×83, liens footer 14 px espacés ≈30 px ; points de carrousel 6×6 (insuffisant) ; flèches 40×40.
- Vitesse : home 268 requêtes / 9.0 Mo / TTFB 1 393 ms / FCP 5 160 ms / load 11.6 s ; villas 283 / 12.3 Mo / FCP 928 ms ; villa 168 / 4.9 Mo / FCP 1.2 s.
- Lisibilité : 14 px sur #19100d a=0.5 (3.45:1), 12 px sur les cartes ; `maximum-scale=1.0, user-scalable=no`.

**Interprétation** : contenu et vidéo intégralement conservés au prix d'un FCP de 5 s sur la home ; recadrages qui sacrifient les titres ; cibles tactiles de marque (points 6 px) non redimensionnées ; premier écran sans CTA verbal si la bannière cookies est présente. Le bandeau à une tuile et les filtres sticky sont de bons choix.

**Différences pertinentes** : bandeau 1 tuile vs 3 ; carrousels vs grilles ; manifeste aligné à gauche ; sticky d'image supprimé, sticky de filtres ajouté ; image de fermeture portrait ; newsletter en tête de footer.

---

## 13. Performance, accessibilité, SEO

**Faits observés**
- Temps (desktop / mobile) : home TTFB 528 / 1 393 ms, FCP 4 228 / 5 160 ms, load 11.4 / 11.6 s. Villas FCP 2 248 ms, load 26.8 s. Villa FCP 908 ms. Resort 4 108 ms. Resorts 644 ms, load 11.3 s. Experiences 652 ms, load 3.3 s. Dining 1 436. Wellness 1 036. About 976. Offers 728, load 3.4 s. Contact 1 052. LCP non mesuré.
- Poids : home 668 requêtes / 19.2 Mo (scripts 263 fichiers / 11.0 Mo, images 181 / 4.7 Mo, CSS 77 / 2.2 Mo) ; resort 564 / 20.9 Mo ; villas 546 / 19.9 Mo ; villa 471 / 19.0 Mo (images 11.4 Mo) ; experiences 497 / 18.5 Mo (images 10.3 Mo) ; dining 537 / 18.7 Mo ; resorts 382 / 10.3 Mo ; about 428 / 11.0 Mo ; contact 430 / 13.5 Mo. CSS ≈670–900 Ko (Autoptimize, 8 feuilles).
- Tiers : Gumlet (≈1.2 Mo de JS, 42 requêtes), AdRoll (56), TikTok (40), Google Ads/GTM/reCAPTCHA (344 Ko ×4), Clarity, Mouseflow, LinkedIn, LINE, Baidu, Bing, Nelio A/B + session recordings, Weglot, CookieYes. Fonts 5 fichiers, Scto en `.woff`.
- Lazy : 13/39 images home, 60/86 villas, 28/61 villa. Max unitaire 645 / 688 / 1 104 Ko ; WebP minoritaire. CLS non mesuré (**hypothèse** de décalage à l'arrivée de la bannière et des polices, fallback Georgia/system-ui).
- Contrastes : #19100d/#f4f1e9 16.6:1 ; #19100d à 50 % **3.45:1** (échec AA à 14 px) ; à 20 % 1.54:1 (texte en attente) ; #fff/#6d2e1d 10.2:1 ; #fffffe/#19100d 18.7:1 ; #fffffe à 50 % 5.3:1 ; #6d2e1d/#f4f1e9 9.0:1 ; #e6b33c/#f4f1e9 1.71:1 (soleil).
- Clavier : `focusOutlineNone` 59–200 règles ; `tabindex=-1` 3–56 ; `aria-hidden` 4–88 ; pas de skip link ; landmark `main` absent partout sauf sur la villa ; iframe vidéo sans `title` ; 1 bouton sans nom (villas, offers, experiences).
- Formulaires : bandeau `<details>` + inputs étiquetés + champs cachés ; newsletter Gravity (5 champs + reCAPTCHA) ; contact 8 champs avec dates `dd/mm/yyyy`.
- Reduced motion : 27–31 règles, extrait limité à Slick ; 627 éléments à transition sur la home, 0 animé par keyframes.
- Titres : H1 unique sur 9 pages ; **0 H1** sur resort et contact ; 4 H3 parasites sur la villa ; H2/H3 de footer en 14 px ; 404 en `noindex`.
- Métadonnées : titles et descriptions propres, canonical auto-référent, JSON-LD `@graph` WebPage/AboutPage/ContactPage (**hypothèse** Yoast), `lang="en-GB"`, **hreflang []** malgré Weglot, OG non vérifié. Mots indexables : 504 / 1 423 / 815 / 499 / 475 / 797 / 521 / 326 / 435 / 672 / 289 (home, villas, villa, resort, resorts, experiences, dining, wellness, about, offers, contact). Viewport `user-scalable=no`.

**Interprétation** : le site paie moins son immersion (une vidéo par page, posters ≤700 Ko) que son empilement marketing (11 Mo de scripts sur la home). Le FCP à 4–5 s sur la home est le vrai risque. L'accessibilité est traitée au niveau des alts et des formulaires, pas du clavier, des landmarks ni du zoom. SEO on-page propre ; hreflang et deux H1 manquants sont les trous.

---

## 14. Conclusion

### 15 meilleurs éléments
1. Signature « Just What Matters. » répétée en H2 de clôture de chaque page, dans une image pleine largeur avec bandeau de réservation épinglé.
2. Manifeste typographique Moulin 32 px révélé par lignes, avant toute offre.
3. Trois resorts présentés comme des « chapters » avec une phrase de positionnement chacun, et header contextuel 159 px avec sous-nav par resort.
4. Ligne de faits standardisée sur chaque villa : capacité éclatée adultes/enfants • chambres/type • m².
5. Filtre à 4 critères + « Compare villas » + pastille resort sur 21+ cartes ; filtres sticky sur mobile.
6. Chips « libellé / valeur » et liste d'inclusions en bénéfices (« Children stay and dine for free ») avec image sticky.
7. « Download Floor Plan » / « Download Resort Map » sur la villa.
8. Panneau piliers sombre à onglets (Our Story · Stewardship · Discovery · Wellbeing · Soneva Stars) qui compresse la marque en 803 px.
9. Hôtes nommés avec rôle (Nuha, Naifa, Zakia) et invités « Soneva Stars » datés.
10. Taxonomie sensorielle des 35 expériences (« Beneath the stars », « Under the canopy », « Beyond the island »).
11. Palette de matière nommée dans le CSS (linen haze, blue hour, golden ember, driftwood) et un seul accent d'action #6d2e1d.
12. Logo qui se réduit au soleil doré quand le header devient opaque.
13. Collages asymétriques réservés aux sections de vie, grilles régulières pour le commerce.
14. Photographie d'instants (grain, contre-jour, sous-marin, enfants) et vues zénithales pour l'architecture.
15. Contacts humains partout : menu, footer, WhatsApp, WeChat, directeurs nommés avec lignes directes.

### 5 faiblesses / limites
1. Performance : 19–21 Mo et 470–670 requêtes par page, 11 Mo de scripts tiers, FCP 4–5 s sur la home, load 26.8 s sur /villas/.
2. Aucun prix, aucune réassurance transactionnelle (annulation, acompte, avis) avant un moteur externe non observable ; le routeur hash du « Book » n'a rien ouvert en headless.
3. Accessibilité : `user-scalable=no`, pas de `main` ni de skip link, 88–200 `outline:none`, texte secondaire à 3.45:1, points de carrousel 6 px, révélations non conditionnées à reduced-motion.
4. Bannière CookieYes envahissante (15 % de l'écran, modal plein écran) qui a parasité menu, reduced-motion et booking.
5. Dettes éditoriales et SEO : 0 H1 sur resort et contact, H3 « www.sandrobruecklmeier.com », coquille « Sonveva », 404 covid liée, hreflang absent, polices « Trial ».

### 10 principes réutilisables
1. Un manifeste avant l'offre, en grand corps serif léger, révélé par lignes.
2. Deux images pleine largeur par page : une pour la marque, une pour l'action avec formulaire épinglé.
3. Phrase-chapitre par lieu d'une collection + header contextuel par lieu.
4. Faits durs en ligne standard, jamais dans les phrases.
5. Chips libellé/valeur + inclusions en bénéfices + documents téléchargeables.
6. Kicker fonctionnel + titre émotionnel.
7. Nommer les prestations (Originals, The Den, Soneva Soul) pour les rendre collectionnables.
8. Deux familles typographiques, un accent, un fond de matière, radius 2 px.
9. Un easing signature et deux durées (0.45 s texte, 1.2–1.6 s image).
10. Doubler la navigation thème × lieu et marquer chaque carte du lieu.

### Éléments propres à la marque à ne pas copier
Le soleil et la police Moulin ; la signature « Just What Matters » et « Bare Luxury » ; les noms de prestations (Flying Sauces, The Den, Soneva Stars, Soneva Soul) ; l'imagerie raie manta / apnéiste ; la structure à trois resorts maldiviens.

### Ce que ce site apporte que les sites « quiet luxury » (FORESTIS, Seagate, Le Collectionist) n'apportent pas
- Un **catalogue à faits** (capacité éclatée, m², filtres, comparateur, plan téléchargeable) inséré dans un storytelling sensoriel, là où le quiet luxury décrit en une phrase et trois chiffres.
- Un **panneau de marque à onglets** sur image sombre qui remplace la page « philosophie » par un composant répété.
- Un **bandeau de réservation épinglé dans l'image émotionnelle de fermeture**, présent sur toutes les pages.
- Une **collection hiérarchisée** (marque ombrelle, trois « chapters », header contextuel 159 px) et une taxonomie d'expériences par lieu sensoriel avec calendrier d'invités.
- La **joie et l'enfance** comme registre (toboggans, enfants en contre-jour, « Tipsy »), absentes du registre contemplatif du quiet luxury.

### Notes /10
- **Branding : 8.5** — signature répétée sur 11 pages, phrases-chapitres par resort, hôtes nommés, preuve ×4 ; retenue par les polices « Trial » et la coquille dans un `<title>`.
- **Direction artistique : 8** — tokens nommés, deux familles, collages asymétriques vs grilles, photo d'instants ; retenue par le texte secondaire à 3.45:1 et les recadrages mobiles qui coupent les titres.
- **Animations : 6.5** — un easing signature, révélations et clip-path placés, sticky utiles ; mais aucune transition de page, reduced-motion limité à Slick, Lenis non vérifiable, autoplay des piliers hypothétique.
- **UX : 7** — filtres + comparateur + pastilles, contacts humains partout, filtres sticky mobile ; retenue par `user-scalable=no`, absence de `main`, menu de 803 px non vérifié, 404 encore liée.
- **Conversion : 6.5** — deux bandeaux par page dont un épinglé, « Check availability » par villa, offres nommées et datées ; mais aucun prix, aucune réassurance transactionnelle, moteur externe non observé, routeur hash muet en headless.
- **Mobile : 6.5** — contenu et vidéo conservés, bandeau simplifié, filtres sticky, CTA villa visible ; mais FCP 5.2 s, 9–12 Mo, points 6 px, 12 px sur les cartes, zoom bloqué.

**Note globale : 7.5/10.** Soneva est la référence de la série pour la mise en récit d'une collection et pour la présentation d'unités par faits + sensations + inclusions ; elle perd des points sur la performance (empilement de scripts marketing) et sur la transparence tarifaire, entièrement déléguée à un moteur externe que l'audit n'a pas pu atteindre.

---

## Observations clés à conserver pour la phase comparative

- Header fixed 97 px, transparent sur hero → #f4f1e9 au scroll ; 159 px avec sous-nav de 7 entrées en contexte resort ; mega-menu fixed 1440×803 non capturé (CookieYes).
- Palette : fond #f4f1e9, texte #19100d, CTA #6d2e1d → hover #012531, accent #e6b33c ; radius 2 px ; contraste secondaire 3.45:1.
- Typo : Moulin Trial 300 (48/40/32/24 px ; 36/28/24/20 mobile) + Scto Grotesk A Trial (16/14/12) ; manifeste 32 px (24 mobile) découpé en spans (splitText 106 sur /villas/).
- Animations : 0.45 s cubic-bezier(.33,1,.45,1) ×551, clip-path 41 règles à 1.2–1.6 s, Lenis + Slick, ni GSAP ni transitions de page ; 27–31 règles reduced-motion limitées à Slick.
- Scroll : jusqu'à 8 opacités partielles par palier, `div.row` bandeau épinglé h=148 de y≈4 470 à 5 463 ; image sticky 640×773 sur la villa ; filtres sticky 390×83 sur villas mobile.
- Home 7 512 px / 7 sections / 504 mots ; deux images pleine largeur (1440×803 piliers, 1440×1800 fermeture) ; 3 cartes resorts 448×560.
- Villas : 21 cartes 448×299 (1.5), ligne « Sleeps 9 Adults (6 Adults 3 Child) • 3 Bedrooms • 1,370 m² », 272–2 280 m², 2–18 personnes, 4 filtres + Compare, 0 prix ; page 9 612 px, 19.9 Mo, load 26.8 s.
- Villa 14 : hero scindé 865×649 + 5 chips + « Check availability » 139×49 à y=735 ; 9 slides 1050×700 ; 7 inclusions ; plan + carte téléchargeables ; 11.4 Mo d'images (max 1 104 Ko).
- Booking : « Book » = `#/booking/destination/dates`, loupes = `#/booking/step-2`, champs cachés hotel_id/hotel_name/adults/children ; clic sans navigation ni requête azds (hypothèse de moteur externe non observée).
- Offres : 13 cartes 4 colonnes, pastilles For Families / Limited Time / Early Bird, « Available until… », « Best Price Guarantee », aucun prix.
- Experiences : 35 cartes 0.8 avec double pastille resort + catégorie sensorielle, 13 718 px, 797 mots ; « Soneva Stars » 5 invités datés.
- Vidéo : 4 embeds Gumlet 1600×900 HLS (home, villas, resort, dining), `playsinline=false`, ≈1.2 Mo de JS lecteur ; posters 245–688 Ko.
- Perf : home 668 req / 19.2 Mo / FCP 4 228 ms desktop, 268 req / 9.0 Mo / FCP 5 160 ms mobile ; scripts tiers 11 Mo (AdRoll 56 req, TikTok 40, Clarity, Mouseflow, Nelio).
- A11y/SEO : `user-scalable=no`, 0 skip link, `main` absent sauf villa, outline:none 59–200, H1 absent sur resort et contact, hreflang [], JSON-LD WebPage/AboutPage/ContactPage.
- Contact : +960 660 4300, reservations@soneva.com, WhatsApp wa.me, WeChat QR, directeurs nommés avec e-mail, formulaire 8 champs avec dates ; menu = page contact.
