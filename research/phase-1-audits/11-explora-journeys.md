# Fiche d'audit — Explora Journeys

Clé : `explora` · Analyse du 2026-09-04 · Chromium headless via Playwright, 1440×900 (desktop) et 390×844 DPR 2 (mobile). Série 2 : croisière de luxe, offre combinatoire (destinations × dates × navires × suites), conversion haut de gamme.

---

## 0. En-tête

**Nom** : Explora Journeys (croisières de luxe du groupe MSC ; navires EXPLORA I à VI, « EXPLORA III Sailing Now »). **URL de départ** : https://explorajourneys.com/us/en (marché USA). Balise description : « the ultimate all-inclusive luxury ocean journey ».

### Pages étudiées

| Label | URL | Desktop | Mobile |
|---|---|---|---|
| home | https://explorajourneys.com/us/en | oui (+ sweep 15 paliers) | oui |
| rooms (liste des suites) | https://explorajourneys.com/us/en/suites | oui | non (capture non livrée) |
| room-detail (Owner's Residence) | https://explorajourneys.com/us/en/suites/owners-residence | oui | oui |
| experiences (globe des destinations) | https://explorajourneys.com/us/en/destinations-globe | oui | non |
| dining | https://explorajourneys.com/us/en/life-on-explora/dining | oui | non |
| spa (Ocean Wellness) | https://explorajourneys.com/us/en/life-on-explora/ocean-wellness | oui | non |
| about v1 (moteur « Find your journey ») | https://explorajourneys.com/us/en/find-your-journey | oui | non |
| about v2 (Ocean State of Mind) | https://explorajourneys.com/us/en/about-explora-journeys/ocean-state-of-mind | oui | non |
| contact | https://explorajourneys.com/us/en/my-explora/support---contact | **redirigée vers la home** (title, canonical, contenu identiques) | non |
| offers | https://explorajourneys.com/us/en/info/special-offers | oui | non |
| booking (sonde CTA → page d'offre) | https://explorajourneys.com/us/en/info/special-offers/explora-early-booking-benefit | oui | non |
| destinations (excursions) | https://explorajourneys.com/us/en/Destinations-Experiences | oui | non |
| collection (Summer 2026) | https://explorajourneys.com/us/en/collection-cruises/summer-2026-cruises | oui | non |
| awards | https://explorajourneys.com/us/en/awards | oui | non |

### Limites de l'observation

- 4 balises `<video>` sur la home, 3 sur les suites, 1 à 3 par page intérieure : toutes `autoplay muted loop` en état `paused` ; aucune lecture vérifiée, emplacements vides sur les captures (ex. colonne « Ocean Wellness » de « Life onboard », vidéo 390×488).
- Menu mobile non capturé (`no burger found`), pas de capture `05-menu-open`. Le mega-menu desktop apparaît en surimpression semi-transparente sur `room-detail-02-full`, `experiences-02-full`, `offers-02-full`, `booking-02-full`, `awards-02-full` (artefact de capture qui montre le panneau « Offers & Fares »).
- Sonde réservation : clic « Reserve » impossible sur la home (« outside of the viewport ») ; ailleurs la sonde a suivi un lien de menu vers la page « Early Booking Benefit ». Le tunnel « Details → suite → paiement » n'a **pas** été atteint.
- Aucune bannière cookies capturée alors que le SDK Didomi est chargé (hypothèse : pas de bandeau sur le marché US).
- La page contact redirige vers la home : aucun formulaire de contact observé. « Contact Us » pointe vers `#` / `#event-trigger--talktous` (modale non capturée).
- Non mesurables : LCP (`null`), Lighthouse, transitions de page, curseur tactile, rendu de la recherche au clic, lecture YouTube. Hover : 11 éléments testés, aucun changement de style calculé.

---

## 1. Positionnement de marque

**Faits observés**
- Title « Luxury Cruises | Explora Journeys » ; JSON-LD Organization + BreadcrumbList ; 45 `hreflang` ; sélecteur « USA / English » en pied de page.
- Hero : « *Maybe* the ocean has a *new address* » + « EXPLORA III Sailing Now ». Claims tournants 28 px : « Maybe the best hotel isn't a hotel », « …the finest dinner is even finer with a sunset view », « …the best rooftop doesn't need a city », « …the best suite comes with a new view every day ». Piliers 24 px : « Warm, Intuitive Hospitality », « Unmatched Inclusive Experiences », « Your Ultra-elegant Home at Sea ».
- Page Ocean State of Mind : H1 visuel « OCEAN STATE OF MIND » (h1count 0), citation 43,95 px/70 px sur 1 037 px de large, film « EN-Ocean-State-of-Mind.mp4 » (9,4 Mo) avec bouton lecture, cartes « Our Story » et « MSC Group » ; 385 mots.
- Pied de page : « Our Brand Ambassador Jannik Sinner », « MSC Foundation », « MSC Group », « Travel Advisors ». Page Awards : 11 lauriers (T+L 2026 World's Best, CNT 2025 Hot List, Virtuoso 2025, Cruise Critic 2024, CNT Readers' Choice 2024 Best New Cruise Line…) + accordéon 2023–2026.
- Prix dès la liste : « Per guest, from: $6,375 ~~$8,500~~ · $797 per night » ; page 1 de Find your journey : 5 550 à 32 775 $ par personne (7 à 28 nuits), 741 à 2 341 $ par nuit.
- « All Journeys Include » (10 puces) sur home, suites, offres, collection ; Dining : 9 restaurants inclus puis « Additional Epicurean Experiences » (Anthology, Chef's Table, cave) ; Destination Experiences : « Showing 10 of 2516 Experiences », « From $145.00 / $170.00 per guest ».

**Interprétation**
- Architecture de marque : ombrelle Explora Journeys → 6 navires numérotés quasi indifférenciés → 4 catégories de suites → 11 régions × 5 saisons. La home hiérarchise la **recherche** (où/quand) puis les **offres** ; le navire n'est qu'une ligne des cartes (« EXPLORA III · 8 Nights »).
- Promesse : un hôtel qui se déplace (« the best hotel isn't a hotel », « Home at Sea »). « Cruise » n'apparaît que dans les balises SEO ; la marque dit « Journey », « Ocean State of Mind », « Ambassador », « Residence Host ».
- Gamme : ultra-premium tarifé et remisé (−35 %, 5 500 $, −5 %, −20 %, −10 %) — à l'opposé du quiet luxury qui cache le prix.
- Cible : voyageurs aisés 45+, couples, familles multigénérationnelles et solos (« A Journey of One »), marché nord-américain (numéro gratuit 24 h, USD, « Labor Day Edition »), forte intermédiation agences.
- Territoire : lumière dorée, calme, bien-être plus que découverte. Personnalité rassurante, méthodique, corporate (MSC, Foundation, Codes of Conduct).
- « All-inclusive » vrai pour restauration, boissons, Wi-Fi, pourboires, spa thermal ; faux pour Anthology, Chef's Table, cave et les 2 516 excursions. Le site le dit, mais en fin de page.
- Cohérence offre/mots/images/interactions : un luxe *explicatif* (tableaux, inclusions, prix) plutôt que suggestif.

**Enseignements réutilisables** : faire de la home un moteur et loger la marque dans les interstices ; afficher l'unité vendue et son prix par nuit dès la liste ; un composant « inclus » répété sur toutes les pages de vente ; annoncer les exceptions au tout-inclus avant le tableau.

---

## 2. Première impression (5 premières secondes)

**Faits observés**
- `home-00-initial` = `home-01-hero` (844 199 octets) : ni préloader, ni bandeau cookies, ni pop-up. Widget accessiBe (bouton bleu 48 px, bas droite) sur toutes les pages.
- Header fixe 132 px (#f4f2ef, z 112) : barre « Talk to an Explora Ambassador. ☎ +1 833 925 1567 » (≈36 px), logo médaillon + wordmark, 6 entrées capitales 12 px or #866d4b, loupe, compte, « Contact Us » (contour or 81×35, rayon 5) et « Reserve » (navy #0c2340, 70×35).
- Hero vidéo 1440×719 : navire de trois quarts arrière au couchant ; titre serif blanc ≈40 px centré à y≈630 ; sous-titre 15 px.
- Widget y≈725 : carte blanche 816×68 (« Where to? Anywhere ▾ », « When? Anytime ▾ ») accolée au bouton or « VIEW 658 JOURNEYS » 250×68 (rayon 0 6 6 0). Sous le hero : « Explore more ˅ ».
- Mobile : header 81 px (burger, médaillon + wordmark centrés, compte, téléphone), vidéo 390×430, claim ≈30 px sur 2 lignes **sous** l'image, deux sélecteurs 148×40, bouton or 310×42 ; tout tient dans 844 px.
- TTFB 306 ms / FCP 596 ms desktop ; 1 109 / 2 148 ms mobile.

**Interprétation** : on voit un navire, un ciel doré, un moteur ; on comprend « croisière de luxe, 658 départs, cherchez maintenant » ; on ressent la sérénité mais aussi un site de réservation (trois CTA colorés dans le premier écran). Le chiffre 658 sert de preuve d'abondance. « Reserve » et le widget mènent à la même page de résultats : pas de moteur externe, pas de réservation directe. Distractions : le widget accessiBe et la barre téléphone qui grignote le hero. Raison de continuer : le hero ne dit rien des inclusions ni des suites.

**Enseignements réutilisables** : widget où/quand + compteur de résultats pour une offre à forte variété ; italique sur le mot-attitude du slogan ; pas trois CTA de couleurs différentes dans le premier écran.

---

## 3. Direction artistique

**Faits observés**
- Fonds (home) : #f4f2ef ×1205, #e7e1da ×143 (Journal, newsletter, panneaux de restaurants), #ede9e4 (tableau des suites ×497), #ffffff (cartes de résultats), #fefefc (cartes d'excursions). Textes : #222222 ×596, #866d4b ×46 (nav, liens, filets), #5d5d5d ; navy #0c2340 (boutons, titre Journal) ; #9c441d (« RESET FILTERS »).
- Polices (woff2) : **WT Monarch Nova** (H1 39 px capitales lettrage 1,95 px lh 54,6 ; Journal 36 px ; « FIND YOUR JOURNEY » 32 px/300), **SangBleu Republic** (claims 28 px lh 36,4 ; H4 34,05 px lh 67,95 ; restaurants 40,05 px ; corps 15/26), **Shapiro 35 Feather** (corps 15/21 graisse 300, nav 12 px), Helvetica Neue sur les boutons (10–14 px/500), police d'icônes « explora ». Home : 114 éléments Shapiro contre 39 en serif.
- Échelle desktop : 40 / 39 / 36 / 34 / 28 / 24 / 18 / 15 / 14 / 12 / 10 px. Mobile : H1 32 px (lettrage 1,6), H4 24/33, corps 15–16, nav 16.
- Largeurs : 1 360 px (carrousels), 1 217 px (texte), 1 340 px (YouTube), 776 px (claims), 1 037 px (citation Ocean State of Mind). Marges 40 px desktop / 16 px mobile. Grilles : 874 + 391 px (offres, highlights), 3 colonnes (Life onboard), 4 × 280 px (destinations), 50/50 image 650×451 + panneau sable 535 px (10 restaurants, 4 services spa, 7 offres), 3 carrés 417 px (collection), 328×100 lauriers.
- Boutons : rayon 5 px partout ; navy plein (« Reserve » 70×35, « LEARN MORE » 185×42 capitales 10 px lettrage 1,4, « Details » 93×44, « DISCOVER OUR JOURNEYS » 204×43) ; contour or (« Contact Us ») ; or plein (« VIEW 658 JOURNEYS ») ; blanc sur image (« EXPLORE » 100×36) ; la plupart des CTA de contenu sont des liens soulignés 15 px.
- Composants : filets or 64 px autour des claims ; encadré « All Journeys Include » bordure 1 px or, médaillon à cheval sur le bord (682×540) ; cartes blanches rayon ≈8 px ombrées ; pastilles d'offre sable rayon 20 px ; lauriers navy ; barres de progression + chevrons.
- Images : 0 `srcset` ; Adobe Dynamic Media (`/is/image/…fmt=webp`) ou JPEG bruts (Cover-Magazine.jpg 13,3 Mo ; South-America 15,8 Mo ; 4371×5464 affichée 322×403). Ratios : 1,8 / 0,81 / 1,44 / 2,62 (héros intérieurs 1440×550) / 1,0 / 6,86. Vidéos de 4 Mo (hero) à 82 Mo (suites), 72 Mo (collection), 57 Mo (awards).
- Iconographie filaire (téléphone, mail, devis, carte, navire, lune = nuits, vague = activité) ; médaillon rosace ; aucune illustration ; une seule texture (écume 680×728).

**Interprétation** : palette sable / navy / bronze où le navy reste un accent d'action (≈15,8:1 avec blanc) et n'est jamais un fond de section. Trois familles à rôles distincts : Monarch Nova réservée aux H1 (rareté = prestige), SangBleu pour les phrases, Shapiro pour les listes ; les boutons en Helvetica trahissent une couche « moteur » séparée de la couche « marque ». La grille 874/391 casse la monotonie des carrousels. Le vide est modéré (sections 500–760 px) : site dense, catalogue (suites 7 980 px, Dining 10 966 px). Rupture : cartes de résultats blanches à prix gras, de style OTA.

| Token | Valeur |
|---|---|
| Fond / sable / tableau | #f4f2ef / #e7e1da / #ede9e4 |
| Texte / secondaire | #222222 / #5d5d5d |
| Accent marque / accent action | #866d4b / #0c2340 |
| Display | WT Monarch Nova 400, 39 px (32 mobile), capitales, lettrage 1,95 (1,6) |
| Serif | SangBleu Republic 400, 44 / 34 / 28 / 24 / 15 px |
| Sans | Shapiro 300–700, 15 / 14 / 12 px |
| Boutons | Helvetica Neue 500, 10–14 px, rayon 5 px, hauteurs 35 / 42 / 44 / 47 / 68 px |
| Largeur de contenu | 1 360 max, 1 217 texte, 776 claims |
| Header | 132 px → ≈63 px au scroll ; mobile 81 → ≈56 px |
| Transitions | 0.4 s ×170, 0.2 s ×150 ; ease-in-out ×84 ; cubic-bezier(0,0,.2,1) ×307, (.05,0,0,1) ×174 |

**Enseignements réutilisables** : une display pour un seul niveau ; serif 28 px entre filets pour les claims ; navy = action uniquement ; gabarit 535 px image/panneau pour les listes de prestations.

---

## 4. Architecture de la page d'accueil

Desktop, docHeight 8 519 px, reconstruite à partir des sections, vidéos et 15 captures `home-sweep-*`.

| Position (y) | Section | Objectif | Contenu | Interaction | CTA | Émotion |
|---|---|---|---|---|---|---|
| 0–132 | Header fixe | Orienter, convertir | Tél 24 h, 6 entrées, recherche, compte | Mega-menu ; compaction ≈63 px | Contact Us, Reserve | Sérieux |
| 131–850 | Hero + widget | Lancer la recherche | Vidéo navire, claim italique, « EXPLORA III Sailing Now » | Vidéo (non vérifiée), 2 sélecteurs | VIEW 658 JOURNEYS | Calme, abondance |
| 850–976 | « Explore more ˅ » | Inviter au scroll | Texte + chevron | — | — | Curiosité |
| 976–1 700 | Offres 874/391 | Vendre maintenant | Labor Day −35 % + acompte 10 % ; Invitation to the Ocean 5 500 $ pp | Carrousel 2 slides | Discover the offer | Urgence tempérée |
| 1 700–2 200 | Claims « Maybe… » | Marque | 4 phrases 28 px entre filets | Fondu croisé automatique | — | Complicité |
| 2 200–2 950 | YouTube 1340×754 | Immerger | « Maybe the best hotel isn't a hotel » | Lecture au clic | — | Aspiration |
| 2 950–3 300 | Piliers tournants | Expliquer | 3 titres 24 px | Carrousel de titres | — | Confiance |
| 3 300–3 700 | Our Destinations | Faire choisir | 11 cartes 280×350 | Carrousel 4 visibles, 9 points | Liens soulignés | Envie |
| 3 700–4 350 | Life onboard | Présenter le produit | Suites, Dining, Ocean Wellness (vidéo) | — | Explore Suites / Dining / Wellness | Confort |
| 4 350–4 900 | All Journeys Include | Lever l'objection prix | Encadré or, 10 puces | — | additional benefits | Réassurance |
| 4 900–5 500 | Highlights | Pousser des collections | Caraïbes, Serene Mediterranean | Carrousel 2 slides | Explore our Journeys Collection | Projection |
| 5 500–6 100 | Explora Journal | Contenu de marque | Écume 680×728 + panneau sable | Vidéo | Read our Stories | Profondeur |
| 6 100–6 800 | Ocean State of Mind | Manifeste | Titre 34 px, 2 photos superposées | Reveal (opacité 0 par défaut) | Explore more | Adhésion |
| 6 800–7 100 | 3 lauriers | Preuve | T+L 2026, T+L 2025, CNT 2025 | — | — | Crédibilité |
| 7 100–7 300 | Newsletter | Capter | Bandeau sable | Champ sans label | Subscribe | — |
| 7 300–8 300 | Footer 4 colonnes | Servir | Contact, Pro, Plan, About | Sélecteurs pays/langue | Request a Quote | Service |
| 8 300–8 519 | Bandeau SEO | Maillage | Liens régions sur photo 1440×210 | — | — | — |

**Logique narrative** : la home commence par un moteur ; le désir est construit *après* l'offre (promotions au 2e écran, puis claims, film, piliers). L'offre devient concrète trois fois (widget, offres, inclusions). Les suites tiennent en un tiers de colonne : la home vend le voyage, pas la cabine. La preuve arrive à y≈6 900 ; la réservation n'a pas de bloc dédié, elle passe par le header.

---

## 5. Scroll et storytelling

**Faits observés**
- Sweep home : `transforms` = 1 sur 9 paliers, 13 à y=1 077–1 615 (carrousel d'offres + fondu de claims, `partialOpacity` 2), 8 à y=2 153–2 692, 3 à y=6 460–6 999 (images superposées). `pinned` = [] partout, `clipPath` 0. GSAP / ScrollTrigger / Lenis / Locomotive / Webflow / Lottie : false.
- Attributs : `sticky` 23, `horizontal` 6, `reveal` 8, `parallax` 2 (home) ; `reveal` 23 (Ocean Wellness) ; `horizontal` 33 (globe), 14 (collection) ; CSS `position: sticky` ×1 (home) / ×18 (b2c), `scroll-snap` ×3 / ×10.
- Sur Dining et Ocean Wellness, transforms et opacités **en cours** : Dining y=685 `tr 4 op 2` ; Ocean Wellness `tr 4–5 op 1–4` sur 8 paliers (335 → 2 680) ; Destination Experiences `tr 1–4 op 2` sur 4 paliers. Suites, globe, home (hors carrousels) : `tr 0 op 0`.
- Header 132 → ≈63 px dès le premier palier (médaillon seul, barre téléphone masquée) ; globe : classe `b2c-2026-all-destinations-menu-animated`, hauteur fixe 63 px.
- Fonds au scroll : #f4f2ef partout sauf #e7e1da (Journal, y=5 922) ; suites #ede9e4 de 3 023 à 6 046 ; résultats alternent #ffffff / #f4f2ef ; excursions #fefefc sur 6 000 px.
- Carrousels : offres (2), destinations (11), highlights (2), navires (6), suites (3), journeys departing soon, régions de collection. Héros intérieurs 550 px (61 % du viewport) puis fil d'Ariane 52 px.

**Interprétation** : le récit procède par **alternance de gabarits** (carrousel → claims → vidéo → grille → encadré → bandeau), non par mouvement. Effets mesurés : fondus de textes (fonction : marque, rythme) et révélations d'images superposées (orienter le regard vers l'éditorial). Aucun parallaxe visible malgré 2 attributs (hypothèse : réservé aux images superposées, invisible en headless). Le contenu « marque » (Wellness, Dining, Ocean State of Mind) est animé, le contenu « catalogue » (suites, résultats) ne l'est pas. Densité forte (7 carrousels ou grilles en 8 500 px) ; respirations = claims entre filets et bandeau Journal. L'envie de poursuivre tient aux titres explicites plus qu'à la mise en scène.

**Enseignements réutilisables** : rythmer un catalogue par des ruptures de gabarit ; réserver les reveals aux pages « univers » ; texte tournant entre filets comme respiration ; compacter le header en un seul palier.

---

## 6. Animations et micro-interactions

| Animation | Déclencheur | Élément | Effet | Fonction | Risque UX |
|---|---|---|---|---|---|
| Arrivée | Chargement | Page | Aucun préloader | — | Aucun |
| Compaction header | Scroll > ~100 px | `.mega-menu` 132 → ≈63 px | Réduction, médaillon seul (hypothèse 0.3–0.4 s ease-in-out) | Libérer 69 px | Saut si non animé |
| Claims tournants | Temporisé | Phrases 28 px | Fondu croisé (2 phrases superposées capturées ; hypothèse 0.4–0.5 s) | Marque, rythme | Illisible pendant le fondu, pas de pause |
| Piliers tournants | Temporisé | Titres 24 px | Idem (hypothèse) | Expliquer | Idem |
| Reveal images superposées | Entrée viewport | `.overlappingImage__intro.explora-animation--fadeRtL` (opacité 0 au chargement) | Fondu + translation droite→gauche (nom de classe) ; tr 3–5 mesurés | Orienter le regard | Invisible si JS échoue |
| Carrousels | Chevrons / drag | Swiper (font `swiper-icons`, `--swiper-theme-color`) | Translation, barre de progression | Choisir | Mobile : 2e carte visible à ~10 % |
| Hover nav | Survol | `.mega-menu-acp__register-link--link` | `background-size 0.4s` (soulignement animé, hypothèse) | Feedback | — |
| Hover footer | Survol | `.mega-menu-acp__footer--link` | `background-color 0.2s ease-in-out` | Feedback | — |
| Hover cartes/CTA | Survol | Cartes, liens soulignés | **Aucun changement calculé** (11 éléments) | — | Pas de feedback |
| Mega-menu | Survol | Panneaux #f4f2ef pleine largeur | Apparition (hypothèse 0.2–0.3 s) ; Offers = liste + 2 cartes | Naviguer | Panneau ≈600 px |
| Menu mobile | Tap burger | `nav.mega-menu__nav` x=-394 → 0 ; panneaux x=394 → 0 | Glissement, drill-down « Back » | Naviguer | Non capturé |
| Vidéos | Autoplay | `<video muted loop>` + YouTube + film inline (Ocean State of Mind) | Non vérifié | Immersion | 15 à 82 Mo, souvent sans poster |
| Zoom photo / curseur / transitions de page | — | `cursor: auto`, `cursorEls []` | Non observés | — | — |
| Feedback formulaire | Saisie | Filtres | Loader `spin 1s linear` | Attente | — |
| Reduced motion | `prefers-reduced-motion` | 9 règles (home) / 2 (b2c), toutes YouTube | Aucune règle site ; `04-reduced-motion` = `01-hero` | — | Vidéos et fondus non désactivés |

Easings CSS : `cubic-bezier(0,0,.2,1)` ×307 (Material ; hypothèse Coveo/Tailwind), `(.05,0,0,1)` ×174 (hypothèse : composants maison), `(.215,.61,.355,1)` ×28 et `(.175,.885,.32,1)` ×24 sur les pages b2c (128 keyframes ; hypothèse animate.css). Durées : .3 s ×606, .4 s ×263.

**Interprétation** : couche utilitaire, non chorégraphiée (ni pin, ni scrub, ni curseur, ni zoom). Seule signature : le fondu des claims. Risque principal : aucun feedback au survol des éléments cliquables du catalogue.

---

## 7. Navigation et architecture de l'information

**Faits observés**
- 6 entrées (FIND A JOURNEY · DESTINATIONS · SHIPS · THE EXPLORA EXPERIENCE · OFFERS & FARES · STORIES) ; ≈50 liens dans les panneaux : 11 régions, 5 saisons (Summer 2026 → Summer 2028), 3 collections dont « Formula 1 Grand Prix de Monaco 2026 », Destination Experiences, Pre & Post ; 6 navires en vignettes ; 7 rubriques Life on Explora + Why / Inclusions / Awards / Sustainability / Club / Design ; 8 offres.
- Fil d'Ariane 52 px sous chaque hero intérieur ; mobile : « ‹ Suites ».
- « Reserve » navy 70×35 dans le header fixe desktop de toutes les pages → `/find-your-journey`. Mobile : burger, logo, compte, téléphone ; **pas de Reserve**, pas de barre basse ; « CONTACT US » 358×41 dans le panneau de menu.
- Recherche : loupe (desktop), `search-results.html?searchTerm=` (mobile) ; Find your journey : « Where to? / When? / Advanced », « 658 journeys available », PHOTO / MAP VIEW, tri « Date Closest », 12 par page, 55 pages. Collection Summer 2026 : moteur intégré pré-filtré « Where to? Summer 2026 · Occupancy: Multiple · 31 journeys available », pagination 1–3.
- Pied de page 4 colonnes + 24 marchés ; Manage your Reservation (`/access-center`), Brochures, Explora Club, FAQs, Travel Advisors.
- Croisière tarifée en **2 clics** (home → VIEW 658 JOURNEYS → carte) ; suite en 2 clics (Experience → Suites → LEARN MORE) mais sans prix.

**Interprétation** : IA à double entrée, *par destination/date* et *par produit* ; les suites sont rangées sous « The Explora Experience », trois niveaux sous les offres : le site ne vend pas d'abord une suite. Menu de compagnie plutôt que de boutique ; drill-down mobile cohérent mais non vérifié. Frustrations : « Reserve » ouvre une liste et non un moteur, « Contact Us » = `#`, téléphone prime sur réservation en mobile. Point fort : les 5 données de décision (départ, arrivée, dates, durée, prix) dès la carte.

**Enseignements réutilisables** : deux entrées qui convergent vers une même liste tarifée ; 5 données de décision par carte ; sur mobile, un CTA de conversion dans le header ou en barre basse.

---

## 8. Parcours de réservation et conversion

**Faits observés**
- Premier CTA : « VIEW 658 JOURNEYS » (y≈725). Puis « Reserve » (header), « Discover the offer », « Details » (cartes, 93×44), « Request a Quote » (footer, 258×44), téléphone 24 h, « Contact Us », « REQUEST A BROCHURE » (collection, 182×43, ancre `#brochure`).
- Verbes : découvrir = Explore / Learn More / Discover ; demander = Request a Quote (« Allow us to tailor and quote a Journey »), Request a Brochure, Contact Us ; réserver = Reserve / Details / View journeys. Aucun « Book now ».
- Widget : « Where to? » et « When? » seulement ; le nombre de voyageurs est dans « Advanced » (« Occupancy: Multiple » sur la collection). Cartes : « 09 Sep 2026 → 17 Sep 2026 · EXPLORA III · 8 Nights ».
- Prix : « Per guest, from: **$6,375** ~~$8,500~~ · $797 per night » ; pastilles « AN INVITATION TO CELEBRATE – LABOR DAY EDITION › », « MULTIPLE OFFERS AVAILABLE (2) ». Acomptes : « 10% reduced deposit » (Labor Day) ; « Full payment at the time of reservation » (Invitation to the Ocean, catégories GTY).
- Inclusions : encadré 10 puces répété ; tableau 4 colonnes × ≈25 lignes (Ocean Suites 35–39 m², Penthouses 43–69, Residences 65–149, Owner's 280) ; réservation des restaurants 75 / 90 / 120 / 180 jours avant départ selon la catégorie.
- Additionnels : 2 516 excursions payantes (dès 145 $, 4 catégories, niveau d'activité, durée, langue, âge minimum), Pre & Post Journey Additions, Additional Epicurean Experiences, Explora Club.
- Contact humain : « Talk to an Explora Ambassador » + numéro dans la barre ; « We aim to respond within 24 hours » ; collection : « Need help booking your journey? Contact one of our Ambassadors at the Explora Experience Centre » ; Travel Advisors.
- Preuve : 3 lauriers (home), 11 (Awards), 3 (Dining) ; **aucun avis ni note client**.
- Offres : 7 mécaniques datées (« Reserve by 8 September 2026 », « by 29 September 2026 », « for a limited time »). Page Offers : barre basse fixe « Sign up for Exclusive Offers / SIGN UP » 133×41. Page Early Booking : section `find-your-journey` de 500 px vide (widget non rendu).
- Ruptures : aucun changement de domaine ni de charte jusqu'aux résultats ; « Details » et paiement non atteints ; `/access-center` non audité.

**Interprétation** : **parcours à étapes** (destination/date → croisière → suite) avec prix visibles dès la liste, doublé d'une forte incitation au **devis humain**. Les offres sont le vrai moteur : 2e écran de la home, panneau de menu, page dédiée, barre sticky, pastilles sur chaque carte, rappel de date limite sur la collection. « Per guest » suppose un couple ; le solo est traité comme une offre. Les inclusions justifient 741–2 341 $ par nuit ; les exceptions sont documentées tard. Réassurance forte sur l'institution, faible sur l'humain.

**Enseignements réutilisables** : prix barré + par nuit dès la carte ; offres en pastille rattachées aux produits, avec date limite ; trois verbes distincts (Explore / Request / Reserve) ; devis humain 24 h assumé quand le panier dépasse 10 000 $.

---

## 9. Pages chambres / propriétés

**Objet vendu** : une croisière datée (7 à 28 nuits, 128 jours pour le World Journey) tarifée par personne ; la suite est une *catégorie* choisie après l'itinéraire. Les pages Suites ne portent ni prix ni disponibilité.

### Liste des suites — https://explorajourneys.com/us/en/suites (desktop, 7 980 px)

- Hero vidéo 1440×550 (2,4 Mo), H1 « OUR SUITES », H4 34 px « Serene, spacious sanctuaries at sea… ».
- 4 blocs 595×402 (Owner's Residence, Ocean Residences, Ocean Penthouses, Ocean Suites) : image ou vidéo + titre 21 px + paragraphe 15 px + « LEARN MORE » 185×42. Ordre du plus cher au moins cher.
- « ALL SUITES FEATURE: » 16 puces en 2 colonnes (fenêtres sol-plafond, terrasse avec coin repas, dressing, Dyson, sol chauffant, prises B/F, USB, minibar, espresso, gourde, Mandala Blue, jumelles).
- « Benefits Overview » puis tableau 3 416 px sur #ede9e4 : 4 colonnes avec vignette, nom, surface ; ≈25 lignes cochées (bar complet en suite, Technogym kit, laundry illimité, Residence Manager pour l'Owner's).
- 535 requêtes, **440 Mo** (Grand-Penthouse-video-D.mp4 ≈82 Mo demandé 4 fois), load 24,8 s, FCP 2,9 s ; 1 042 mots.

**Interprétation** : un *comparateur* (surfaces + bénéfices) plutôt qu'une galerie ; le désir est délégué aux vidéos.

### Owner's Residence — https://explorajourneys.com/us/en/suites/owners-residence

- Desktop (3 598 px) : H1 « OWNER'S RESIDENCES » sur salon aux murs sculptés ; fil d'Ariane ; H4 « The pinnacle of ocean living, spanning the ship's full beam… » ; 2 variantes 595×402 (« Owner's Residence », « Owner's Residence by Patricia Urquiola » sur EXPLORA III et IV) avec « EXPLORE MORE » 185×42 ; carrousel « Explore Our Suites… » 3 cartes 340×470 avec « EXPLORE » 100×36 ; flux Instagram non rendu ; newsletter. **Absents** : galerie, plan, capacité, surface (280 m² seulement dans le tableau), prix, disponibilité, CTA de réservation. 316 mots, 0 vidéo.
- Mobile (3 645 px) : hero 390×500, H1 32 px, « ‹ Suites », H4 24/33 px, image 340×210, « EXPLORE MORE » 213×47, cartes « EXPLORE » 200×36, Subscribe 310×47 ; TTFB 509 ms, FCP 1 104 ms, 230 requêtes / 8,7 Mo.

**Interprétation** : page de *gamme* (deux variantes, un designer) et non fiche produit ; la projection passe par un seul visuel, la réassurance par le nom Urquiola, les alternatives par le carrousel. Hiérarchie mobile respectée (32 → 24 → 15 px), cibles ≥ 47 px, mais l'unique CTA reste « EXPLORE MORE ».

### Collection Summer 2026 — https://explorajourneys.com/us/en/collection-cruises/summer-2026-cruises (7 627 px)

- Hero vidéo 1440×594 (ILTM-16x9.mp4 72 Mo ×2) avec poster, 2 H1 (« SUMMER 2026 » 39 px + « Introducing Spectacular New Firsts » 18 px), 2 boutons navy « DISCOVER OUR JOURNEYS » 204×43 et « REQUEST A BROCHURE » 182×43.
- « EXPLORA III, the newest addition to our fleet » en images superposées ; 3 régions en carrés 417 px (H3 24 px « Where nature unveils its most surreal landscapes ») ; « Reserve a Journey — Reserve by 29 September 2026 » ; moteur intégré : 31 croisières, cartes identiques à Find your journey (5 550 à 32 775 $), pagination 1–3 ; « Need help booking your journey? » ; 6 piliers (Curated Journeys, Complimentary Experiences, Suites, Culinary and Beverage, Pools, The perfect hosts) ; « All Journeys Include » ; 3 lauriers ; e-brochure. 940 mots, 181 Mo.

**Interprétation** : la collection est la vraie « page produit » d'Explora : elle enchaîne nouveauté (navire), territoire (régions), date limite, liste tarifée, aide humaine, inclusions, preuve, brochure — l'ordre exact d'un argumentaire de vente.

**Enseignements réutilisables** : quand l'unité vendue est un itinéraire, présenter les hébergements en tableau comparatif et réserver les pages détail aux signatures ; ajouter surface et « voir les croisières avec cette suite » sur le détail ; construire les pages saison comme des argumentaires complets avec moteur pré-filtré.

---

## 10. Copywriting

**Faits observés**
- Mécanisme « Maybe » : 6 phrases commençant par « *Maybe* » (italique) suivies d'une inversion d'évidence (« the best hotel isn't a hotel », « luxury travel doesn't need to follow the usual rules »).
- Néologismes : « Ocean State of Mind » (page dédiée, 5 occurrences sur Wellness), « Journey » (jamais « cruise » dans les titres), « Explora Ambassador », « Residence Host », « Mandala Blue » (parfum « curated with master perfumer Alberto Morillas »).
- Titres : H1 capitales courtes (« OUR SUITES », « DINING », « EXCLUSIVE OFFERS ») ; H4 34 px en phrase complète ; H3 24 px en binômes nom/promesse (« Energy — A promise of strength and resurgence as natural as the ocean's vitality »).
- Listes techniques : « Plug types B and F », « USB-A and USB-C », « Technogym Case Kit », « 3 Hrs 30 Min », « Minimum Age Requirement: 3 ».
- CTA : Explore, Learn More (×10 sur Dining), Discover the offer, Details, Request a Quote, View all journeys, Reserve.
- Offres en format invitation (« An Invitation to Celebrate », « A Journey of One », « The Gift of Sharing ») + sous-titre chiffré.
- Longueurs : home 805 mots, suites 1 042, Dining 1 007, globe 1 310, excursions 1 362, collection 940, awards 887, Find your journey 625, Ocean State of Mind 385, Owner's Residence 316.

**Interprétation** : deux registres cohabitent — *manifeste* (Maybe, State of Mind, sensations) dans les titres et claims, *catalogue* (puces, surfaces, délais, prix) dans le corps ; la hiérarchie typographique reproduit celle du discours. Le luxe est dit par les inclusions (« unlimited », « complimentary », « exclusive access ») plus que par les adjectifs. La prestation devient expérience par les noms propres (Anthology, Sakura, Fil Rouge, Mandala Blue) et les cinq « Gifts of Ocean Wellness » (Energy, Relaxation, Immunity, Sleep, Mindfulness). Les CTA sont neutres et répétitifs.

**Enseignements réutilisables** : claim en « Maybe + inversion » ; nommer chaque prestation ; offres titrées comme des invitations et chiffrées en sous-titre ; technique en listes à 2 colonnes.

---

## 11. Photographie et vidéo

**Faits observés**
- Sujets : navire dans un paysage (hero, offres, destinations, Journal : 9 occurrences) ; personnages **de dos** face à la mer (jumelles, foulard, trois robes du soir, piscine à débordement) ; détails de service (assiette, café versé, bol tibétain, flacon sur marbre) ; intérieurs en lumière ambre (suites, restaurants, spa, salle de sport).
- Lumière : heure dorée dominante ; extérieurs de destinations désaturés (sépia caraïbe, ocre du désert, vert amazonien).
- Humains : anonymes (le chef Franck Garanger est le seul portrait de face) ; enfants sur la page Offers.
- Ratios : 1,8 / 0,8 / 1,44 / 2,62 / 1,0 (excursions, régions de collection) / 0,73.
- Vidéos : 4 (home), 3 (suites), 1 hero sur Dining, Wellness, Offers, Excursions, Awards, Collection, Ocean State of Mind (+ film inline), 3 (globe). `preload="none"` hors hero, `#t=0.001` sur mobile (hypothèse : forcer la première image sur iOS). Poids : 4 à 82 Mo. YouTube 1340×754 titré.
- Home : 6 visuels de destination, 5 de navire, 4 d'intérieur/service, 4 de personnages.

**Interprétation** : l'image vend d'abord la *position du navire dans le monde*, puis le *point de vue depuis le bord*, enfin le *soin*. Les personnages de dos sont des substituts du visiteur. La cohérence chromatique ambre + bleu-vert désaturé unifie ≈200 images. Les vidéos sont nombreuses mais leur rôle n'est pas vérifiable et leur poids trahit des masters non compressés.

**Shot list** : (1) le produit petit dans un grand paysage à l'heure dorée, 8–10 plans ; (2) point de vue depuis le produit avec horizon, 6 ; (3) personnage de dos en tenue claire, 5 dont un aux jumelles ; (4) détails de service à 45°, 8 ; (5) intérieurs tamisés, 10 ; (6) portrait de face d'un expert, 3 ; (7) textures naturelles pour bandeaux, 4 ; (8) boucles vidéo 8–12 s ≤ 5 Mo avec poster, 4–6 ; (9) un film manifeste 60–90 s hébergé ; (10) vignettes carrées pour catalogues et cartes 1,48 pour listes.

---

## 12. Mobile

**Faits observés (390×844)**
- Header 81 px fixe : burger, médaillon + wordmark centrés, compte, téléphone ; au scroll ≈56 px avec médaillon seul.
- Hero : vidéo 390×430 (4 Mo), puis sur fond sable claim serif ≈30 px sur 2 lignes, sous-titre 20 px, deux sélecteurs 148×40 (rayon 6, bordure or), bouton or 310×42, « Explore more ˅ ».
- Titres : Journal 36 px ; sections 28 ×2, 24 ×3, 20 ×10 ; corps 15–16 ; nav 16. Owner's Residence : H1 32, H4 24.
- Rythme : carrousels 1 carte + ~10 % de la suivante (offres, destinations, life onboard, highlights) avec barres 2 à 11 segments ; YouTube 390×219 ; encadré inclusions pleine largeur ; awards empilés ; footer en accordéons. docHeight 7 229 px (8 519 desktop).
- Animations : mêmes attributs (`reveal` 8, `sticky` 22, `horizontal` 5, `parallax` 2), `anims []`, rien d'ajouté ni de retiré ; vidéos secondaires `preload="none"`.
- Boutons : 310×42, 310×47, 213×47, 200×36, 358×41 (menu) ; pastilles de carrousel 9×9 px.
- Moteur : widget hero seulement ; pas de « Reserve » ni de barre basse.
- Vitesse : TTFB 1 109 ms, FCP 2 148 ms, load 9,8 s ; 205 requêtes, 46 Mo dont 33,8 Mo de média (Ocean-wellness-pool-2.mp4 15 Mo servi sur mobile). Owner's Residence : FCP 1,1 s, 8,7 Mo.
- Lisibilité : corps 15–16 px sur sable (≈15:1) ; nav or 16 px (≈4,4:1). `viewport user-scalable=0, maximum-scale=1` : **zoom bloqué**.
- Menu non capturé ; DOM : `nav.mega-menu__nav` 390×764 à x=-394, 5 panneaux à x=394 (drill-down « Back »), z-index 9 999 999.

**Interprétation** : transposition fidèle et lisible (une colonne, mêmes gabarits), cibles principales conformes mais pastilles trop petites, vidéo de 15 Mo inutile, zoom bloqué. Différence pertinente : la conversion mobile repose sur le **téléphone**, pas sur « Reserve ».

**Enseignements réutilisables** : carrousels 1 + 10 % avec barre de progression ; claim sous l'image plutôt que dessus ; ne jamais bloquer le zoom ; vidéos mobiles < 3 Mo ou images.

---

## 13. Performance, accessibilité, SEO

**Faits observés**
- Home desktop : TTFB 306 ms, FCP 596 ms, DCL 2,13 s, load 7,5 s ; 366 requêtes, **89,2 Mo** (média 56,5 Mo / 8 requêtes, images 16,9 Mo / 101, scripts 12,6 Mo / 108, CSS 1,9 Mo). Plus lourds : Ocean-wellness-pool-2.mp4 15 Mo ×2, Cover-Magazine.jpg 13,3 Mo, Video-cover-4 8,9 Mo, Sakura 5,7 Mo, clientlib-coveo.js 1 Mo.
- Autres pages : suites 440 Mo / load 24,8 s ; collection 181 Mo ; awards 132 Mo ; globe 108 Mo / 707 requêtes / load 20,8 s ; excursions 98 Mo ; Ocean State of Mind 78 Mo ; Dining DCL 19,2 s (héros vidéo demandés deux fois à chaque fois).
- Lazy loading : 1 image sur la home, 0 ailleurs ; `srcset` 0 ; `preload="none"` hors héros ; héros home et suites sans `poster`.
- Tiers : 15 domaines (YouTube 21 requêtes, google 16, New Relic 14, LinkedIn 8, DoubleClick 7, Bing 7, Contentsquare 7, Didomi 6, Teads, SaleCycle, accessiBe). CSS 1,9 / 3,6 Mo.
- Contrastes estimés : #222222/#f4f2ef ≈ 15:1 ; blanc/#0c2340 ≈ 15,8:1 ; #866d4b/#f4f2ef ≈ 4,4:1 (nav 12 px capitales : sous AA texte normal) ; blanc/#866d4b ≈ 4,9:1 ; #5d5d5d/#f4f2ef ≈ 6:1.
- Clavier : `focusOutlineNone` 200 (plafond de la sonde) partout ; `tabindex=-1` 17 (home), 60 (collection) ; pas de skip link (accessiBe fournit « Option+1 »).
- Landmarks : `main` 0 sur la home (1 ailleurs), `footer` 0 partout. Images sans alt : 37/82 (home), 48/93 (Dining), 32 + 70 alt vides (globe). Liens sans nom 7–10 ; iframes sans titre 2–3 ; champs newsletter et recherche sans label.
- Reduced motion : 9 règles, toutes YouTube ; aucune règle site ; autoplay non conditionné. `viewport user-scalable=0`.
- SEO : `h1count` **0** sur la home et Ocean State of Mind, 4 sur Dining, 2 sur la collection ; title/description/og/canonical corrects ; 45 hreflang ; JSON-LD Organization + BreadcrumbList ; 805 mots (home) ; bandeau de liens régions en pied ; contact redirigé vers la home.

**Interprétation** : l'immersion vidéo et la couverture analytique priment sur le poids (89 Mo pour une home, 440 Mo pour les suites à cause d'un master de 82 Mo rechargé quatre fois). L'accessibilité est déléguée à un overlay tiers alors que les fondamentaux (alt, labels, focus, zoom, landmarks) ne sont pas tenus. Le SEO technique est soigné (hreflang, JSON-LD, maillage) mais le H1 manque sur la home.

**Enseignements réutilisables** : vidéos de section ≤ 5 Mo avec poster et `preload="none"` ; `srcset` généré par le DAM ; pas d'overlay d'accessibilité en substitut ; un H1 sur la home même si le titre est un claim.

---

## 14. Conclusion

### 15 meilleurs éléments
1. Widget « Where to? / When? » + « VIEW 658 JOURNEYS » dans le hero.
2. Cartes de croisière complètes : ports, dates, navire, nuits, prix barré, prix par nuit, pastille d'offre, Details, Map.
3. Encadré « All Journeys Include » (10 puces, médaillon, bordure or) réutilisé sur home, suites, offres, collection.
4. Tableau comparatif 4 catégories × ≈25 bénéfices avec surfaces (35–39 / 43–69 / 65–149 / 280 m²).
5. Claims « Maybe… » en fondu entre filets or.
6. Header 132 → 63 px avec téléphone 24 h, Contact Us et Reserve toujours visibles.
7. Palette sable / navy / bronze, navy réservé à l'action.
8. Trois polices à rôles distincts (Monarch Nova / SangBleu / Shapiro).
9. Grille asymétrique 874/391 des offres et highlights.
10. Panneau Destinations par régions **et** par saisons (Summer 2026 → Summer 2028).
11. Offres titrées en invitation, chiffrées en sous-titre, datées (« Reserve by 29 September 2026 »).
12. Cinq « Gifts of Ocean Wellness » en binômes bénéfice/promesse.
13. Catalogue d'excursions à 6 filtres avec niveau d'activité, durée, langue, âge, prix.
14. Page collection = argumentaire complet (nouveau navire → régions → date limite → liste tarifée → aide humaine → inclusions → preuve → brochure).
15. Mobile : claim sous la vidéo, cibles ≥ 42 px, drill-down avec « Back ».

### 5 faiblesses / limites
1. Poids : 89 Mo (home), 440 Mo (suites), 181 Mo (collection), 132 Mo (awards) ; aucun `srcset` ; masters mp4 de 57 à 82 Mo.
2. Accessibilité : zoom bloqué, `outline:none` ×200, 37 images sans alt, champs sans label, H1 absent sur la home, overlay accessiBe en substitut.
3. Pages suites sans prix, sans surface (hors tableau), sans galerie ni CTA vers les croisières ; ordre du plus cher au moins cher.
4. Aucune preuve client (avis, notes, témoignages) ; preuve institutionnelle seulement.
5. Aucun feedback au survol des cartes ; « Contact Us » en `#` ; page contact redirigée ; pas de CTA de réservation dans le header mobile.

### 10 principes réutilisables
1. Home-moteur : où / quand / compteur de résultats au-dessus du pli.
2. Prix par personne **et** par nuit dès la liste, barré si remise.
3. Un composant « ce qui est inclus » unique, répété sur chaque page de vente.
4. Tableau comparatif d'hébergements avec surfaces et bénéfices cochés.
5. Nommer chaque prestation pour la rendre expérience.
6. Claims courts « Maybe + inversion », italique sur le mot-attitude.
7. Navy = action, bronze = marque, sable = fond.
8. Rupture de gabarit plutôt que mouvement pour rythmer un catalogue.
9. Offres en invitation, chiffrées, datées, rattachées en pastille aux produits.
10. Contact humain 24 h visible en permanence au-delà de 5 000 $ de panier.

### Éléments propres à la marque à ne PAS copier
Le médaillon rosace et le wordmark ; « Ocean State of Mind », « Explora Ambassador », « Mandala Blue », les noms de restaurants ; la série « Maybe… » ; les personnages de dos aux jumelles ; le partenariat Jannik Sinner ; la nomenclature EXPLORA I–VI.

### Ce que ce site apporte que les sites « quiet luxury » (FORESTIS, Seagate, Le Collectionist) n'apportent pas
- **Tarification assumée** : prix barrés, prix par nuit, acomptes réduits, dates limites — là où le quiet luxury cache le prix jusqu'au moteur.
- **Résolution d'une combinatoire** : 658 départs × 11 régions × 5 saisons × 6 navires × 4 catégories, par un widget à deux champs, des cartes normalisées et des pages saison à moteur pré-filtré.
- **Tableau d'inclusions comparatif** comme argument de luxe (le luxe = ce qui n'est plus à payer), exceptions documentées (excursions dès 145 $).
- **Rythme catalogue** : carrousels à barres de progression, gabarits répétés, texte tournant comme seule signature animée, pas de pin ni de parallaxe.
- **Couche de service B2B/B2C** : agents, brochures, espace client, club, 24 marchés, 11 lauriers.

### Notes /10

| Critère | Note | Justification |
|---|---|---|
| Branding | 7,5 | Système verbal fort (« Maybe », « Ocean State of Mind », noms propres), 11 lauriers ; mais ton corporate (MSC, Foundation) et aucune voix client. |
| Direction artistique | 7,5 | Palette #f4f2ef / #0c2340 / #866d4b cohérente, 3 polices à rôles clairs, grille 874/391 ; mais cartes de résultats de style OTA et 0 `srcset`. |
| Animations | 5 | Fondus de claims et reveals mesurés (tr 4–5 sur Wellness), header compact ; aucun hover sur les cartes, aucune règle reduced-motion propre, vidéos non conditionnées. |
| UX | 7 | Croisière tarifée en 2 clics, cartes complètes, fil d'Ariane, menu régions + saisons ; mais « Reserve » = liste, « Contact Us » = `#`, zoom bloqué, occupancy caché dans « Advanced ». |
| Conversion | 7,5 | Prix et offres omniprésents, inclusions répétées, devis 24 h, barre « Sign up for Exclusive Offers », pages saison en argumentaire ; mais tunnel de paiement non atteint, pas d'avis, suites sans prix. |
| Mobile | 6,5 | Hero lisible, boutons 310×42–47, drill-down ; mais 46 Mo, FCP 2,1 s, vidéo 15 Mo, pastilles 9 px, pas de Reserve dans le header. |

**Note globale : 7 / 10.** Explora Journeys résout une offre combinatoire avec une home-moteur, des cartes de croisière exemplaires et un dispositif d'inclusions qui transforme le prix en argument ; la direction artistique sable/navy/bronze et le système « Maybe… » tiennent la marque au-dessus du catalogue. Le site perd des points sur le poids (89 à 440 Mo), les fondamentaux d'accessibilité, l'absence de preuve client et des pages suites qui n'aboutissent pas à une réservation.

---

## Observations clés à conserver pour la phase comparative

- Hero home = vidéo 1440×719 + widget 2 champs + bouton or 250×68 « VIEW 658 JOURNEYS » à y≈725 ; mobile : vidéo 390×430, claim ≈30 px sous l'image, bouton 310×42.
- Header fixe 132 px (tél 36 + nav 96) → ≈63 px au scroll ; mobile 81 → ≈56 px ; « Reserve » 70×35 navy → `/find-your-journey` (pas de moteur externe).
- Palette : fond #f4f2ef, sable #e7e1da, tableau #ede9e4, texte #222222, bronze #866d4b (≈4,4:1 sur sable), navy #0c2340 (15,8:1 avec blanc) ; rayon 5 px sur tous les boutons.
- Typo : WT Monarch Nova 39/32 px capitales lettrage 1,95/1,6 (H1 seulement) ; SangBleu 44/34/28/24/15 px ; Shapiro 15/14/12 px ; Helvetica Neue 10–14 px sur boutons.
- Cartes de croisière : région, image + « Map », ports + dates, navire + nuits, pastille offre, « Per guest, from: $6,375 ~~$8,500~~ · $797 per night », « Details » 93×44 ; 658 résultats, 12/page, 55 pages ; page 1 : 5 550–32 775 $ pp, 741–2 341 $/nuit ; collection Summer 2026 : 31 résultats pré-filtrés.
- Suites : 4 catégories 35–39 / 43–69 / 65–149 / 280 m², tableau 4 × ≈25 bénéfices sur #ede9e4 (3 416 px) ; 16 équipements communs ; page Owner's Residence : 316 mots, ni surface ni prix ni CTA de réservation.
- Inclusions : encadré 10 puces répété sur 4 gabarits ; 9 restaurants inclus, Anthology / Chef's Table / cave en supplément ; 2 516 excursions payantes dès 145–170 $ avec 6 filtres.
- Offres : 7 mécaniques (−35 % + acompte 10 %, jusqu'à 5 500 $ pp paiement intégral, −5 %, −20 %, solo, famille, −10 %) avec dates limites ; barre basse fixe « Sign up for Exclusive Offers » sur Offers.
- Animation : 0 lib de scroll ; fondu croisé des claims ; reveals `explora-animation--fadeRtL` (opacité 0 par défaut) mesurés tr 4–5 / op 1–4 sur Wellness, 0 sur home/suites ; hover cartes = aucun changement ; reduced-motion = 9 règles YouTube.
- Vidéos : 4 (home), 3 (suites), 1–3 par page intérieure ; 4 / 15 / 8,9 / 5,7 Mo (home), 82 et 31 Mo (suites), 72 Mo (collection), 57 Mo (awards), 39 Mo (excursions) ; `preload="none"` + `#t=0.001` sur mobile.
- Perf : home 366 req / 89 Mo / TTFB 306 / FCP 596 ms ; mobile 205 req / 46 Mo / FCP 2 148 ms ; suites 440 Mo / load 24,8 s ; globe 707 req / 108 Mo ; 0 `srcset`, 1 image lazy.
- A11y/SEO : H1 = 0 (home, Ocean State of Mind), 4 (Dining), 2 (collection) ; 37 alt manquants (home) ; `outline:none` ×200 ; `user-scalable=0` ; 45 hreflang ; JSON-LD Organization + BreadcrumbList ; 805 mots (home) ; contact → home.
- Navigation : 6 entrées ; Destinations = 11 régions + 5 saisons + 3 collections ; 6 navires en vignettes ; suites sous « The Explora Experience » ; croisière tarifée en 2 clics.
- Preuve : 3 lauriers (home) / 11 (Awards, accordéon 2023–2026) ; 0 avis client ; ambassadeur Jannik Sinner en pied de page.
- Stack (faits) : Adobe AEM (`etc.clientlibs`, `aem-GridColumn`, `_jcr_content`), Adobe Dynamic Media (`/is/image`, `/is/content`), jQuery, Swiper (CSS), Coveo (`clientlib-coveo` 1 Mo, vars Tailwind), YouTube, FontAwesome, Didomi, accessiBe, Contentsquare, New Relic, SaleCycle.
