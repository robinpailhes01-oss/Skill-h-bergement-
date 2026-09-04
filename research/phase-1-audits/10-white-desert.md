# Fiche d'audit — White Desert Antarctica

Clé : `whitedesert` · Analyse du 2026-09-04 · Chromium headless via Playwright, 1440×900 (desktop) et 390×844 DPR 2 (mobile). Série 2 « au-delà du quiet luxury » : référence du tourisme d'expédition (camps, itinéraires, vols, tarifs affichés).

---

## 0. En-tête

**Nom** : White Desert (opérateur d'expéditions de luxe en Antarctique, base logistique au Cap, piste « Wolf's Fang Runway », trois camps : Whichaway, Echo, Explorer). **URL de départ** : https://white-desert.com/. Title home : « Luxury Adventures in Antarctica | White Desert ». Meta description : « the world's leading luxury Antarctic expedition company… South Pole and Emperor Penguins ».

### Pages étudiées

| Label | URL | Desktop | Mobile |
|---|---|---|---|
| home | https://white-desert.com/ | oui (+ balayage 15 paliers `home-sweep`) | oui |
| camps (hub) | https://white-desert.com/camps | oui | oui |
| camp-detail (Echo Base) | https://white-desert.com/camps/echo-base | oui | oui |
| room-detail (Whichaway Camp, passe 1) | https://white-desert.com/stay/camps/whichaway-camp | oui | oui (hero + menu) |
| itineraries (hub) | https://white-desert.com/itineraries | oui | oui |
| itinerary-detail (Discovery Week) | https://white-desert.com/itineraries/discovery-week | oui | oui |
| rooms / experiences (= itinéraire « The Long Stay », choisi par l'heuristique) | https://white-desert.com/itineraries/the-long-stay | oui | non |
| antarctica (hub régions → « The Mountains ») | https://white-desert.com/antarctica (canonical : /antarctica/wolfs-fang-runway-mountains) | oui | oui |
| prices / offers | https://white-desert.com/prices | oui (2 passes) | oui |
| enquire / contact | https://white-desert.com/enquire | oui (2 passes) | oui |
| founders / about | https://white-desert.com/about/founders | oui (2 passes) | non |

### Limites de l'observation

- Vidéos Cloudflare Stream (`customer-…cloudflarestream.com/…/downloads/default.mp4`) : `autoplay muted loop playsinline`, mais `paused: true` en headless. Le hero de la home est donc gris uni sur les captures (`home-01-hero`) ; le rendu réel (film plein écran, poster) n'est pas vérifiable. Même chose pour la vidéo inline d'Echo Base (330×675) et le bouton « Watch Film ».
- La capture `home-02-full` mesure 5 640 px de large (le wrapper de scroll horizontal se déplie) ; l'analyse s'appuie sur `home-sweep-00…14` et `home-03-scrollN`.
- Curseur personnalisé (`div.custom-cursor`, 4×4 px, z 10001) visible comme un point orange ; états de survol et tactile non mesurables.
- Scroll horizontal, scrub sticky et tracé de carte mesurés par paliers, pas en continu : durées et easings JS restent des hypothèses. Aucune lib d'animation détectée (`gsap`, `ScrollTrigger`, `Lenis`, `Locomotive`, `webflow`, `lottie` = false).
- Les pop-ins « Trip Dates » et « More info » de la page tarifs et le panneau « MORE INFORMATION » n'ont pas été ouverts ; la prise de rendez-vous HubSpot (`meetings-eu1.hubspot.com/meghan-sales/booktime`) et le formulaire n'ont pas été soumis.
- TTFB très variable (369 ms puis 11 594 ms sur /prices ; 11 539 ms sur Long Stay ; 11 860 ms sur /camps mobile) : rendu serveur Next.js (`_next/static`, `dpl=`) ou proxy, hypothèse. LCP `null`, Lighthouse indisponible.
- `/antarctica` rend la région « The Mountains » (canonical `/antarctica/wolfs-fang-runway-mountains`) ; pas de hub observable.

---

## 1. Positionnement de marque

**Faits observés**
- JSON-LD `Organization` : « world's leading luxury Antarctic expedition company… South Pole, Emperor Penguin colonies, and remote ice camps ». Accroche hero : « Luxury and adventure in the most remote place on Earth » (serif italique, coin supérieur gauche), H1 « ANTARCTICA » en condensé 256 px.
- Architecture de marque (menu et méga-footer) : **Itineraries** (6), **Camps** (Whichaway, Echo, Explorer), **Antarctica** (5 régions + Aviation), **About** (Our Story, Dr Jones, Foundation, Sustainability). Nav en trois onglets « Experience / Operation / About » + « Rates / Enquire ».
- Chaque camp porte ses coordonnées GPS en Oswald (« [ 70º 48' 00" S, 11º 23' 00" E ] »…) et une phrase de positionnement distincte : Whichaway « original camp, newly reimagined », Echo « Inspired by astronauts, used by explorers », Explorer « Polar adventure meets chalet-style ».
- Preuves : badges IAATO, CarbonNeutral, Global Vision Awards 2024, Condé Nast Traveler, TripAdvisor, « 20 Years » ; citations presse CN Traveler, Travel + Leisure (page Echo), Vogue (page enquire) ; citation client (Long Stay) ; signature SVG du cofondateur sur la home.
- Prix affichés partout : de US $16 500 (journée) à US $115 500 (South Pole & Penguins), « per person, sharing ». Discovery Week à $45 000 dont « 65 % of the trip price is a donation » à la White Desert Foundation (déductible 501(c)(3) / Gift Aid).
- Home : 1 060 mots ; Long Stay : 1 425 mots ; Discovery Week : 923 mots.

**Interprétation**
- Positionnement : expédition de luxe **opérée en propre** (piste, avions Airbus/Basler/Twin Otter, camps, 100 personnes au sol), pas une agence. Le site vend d'abord le continent (H1 « ANTARCTICA », pas le nom de la marque), puis les itinéraires, puis les camps — l'hébergement est un moyen, l'unité vendue est une semaine à date fixe.
- Cible : « bucket list » fortunée, familles en exclusivité, solos, plus un segment philanthropique/scientifique (Discovery Week). Territoire émotionnel : immensité, rareté (« fewer than 500 people each year »), exploration spatiale (Echo), sécurité opérationnelle (« over 100 on the ground »). Personnalité : explorateur-ingénieur (coordonnées, « 05:30 HRS », « 4 220 KM », « -5 °C »), tempérée par le serif italique. Valeurs : exploration vraie, science, durabilité, contrôle logistique.
- Différence avec un site hôtelier : aucun « book now », aucune nuitée ; tout mène à un formulaire de planification et à un appel. Les prix sur les cartes dès la home sont l'inverse du quiet luxury. Cohérence forte : vol (carte Cap → Wolf's Fang, « CPT – WFR » 320 px) et coordonnées irriguent typographie, cartes et itinéraires.

**Enseignements réutilisables**
- Faire du lieu (destination) le H1, et de la marque une signature de bas de page (wordmark géant « WHITE DESERT » dans le footer).
- Donner à chaque unité vendue une donnée « dure » (coordonnées, altitude, temps de trajet) comme ornement typographique.
- Superposer trois niveaux de preuve : institutionnelle (IAATO, CarbonNeutral), éditoriale (CN Traveler, Vogue, T+L), humaine (signature du fondateur, citation client).

---

## 2. Première impression (5 premières secondes)

**Faits observés**
- Desktop `home-00-initial` : nav fixe 80 px transparente, cinq boutons pilule 120×40 (fond rgba(31,42,68,.2), rayon 2 px) : « Experience / Operation / About » à gauche, logo blanc centré (silhouette de montagne + « WHITE DESERT »), « Rates / Enquire » à droite. Vidéo non rendue → aplat gris ; H1 « ANTARCTICA » Oswald 256 px calé en bas du viewport (y ≈ 650–860) ; accroche serif italique à gauche (y ≈ 438) ; « Watch Film ▸ » à droite (188×44, bordures fines) ; grille verticale d'arrière-plan (`grid-overlay`, 8 lignes, `mix-blend-mode: difference`, z 2).
- Bannière cookies HubSpot en bas à droite (Accept / Reject) ; après acceptation, un point orange de 4 px (curseur custom) est visible. Le chat HubSpot (bulle 100×96 bleu nuit, z 2 147 483 647) apparaît après le hero.
- Mobile `home-mobile-01-hero` : « Menu » à gauche, logo centré, bouton **orange plein** « Enquire » 80×40 (#ff7e15) à droite ; accroche centrée en serif 2 lignes ; H1 « ANTARCTICA » 80 px coupé par la bannière cookies (360×119, blanc à 80 %) **et** par le message proactif du chat (« Interested in Antarctica but not sure where to begin? I'm happy to help. » 266×304) — deux overlays simultanés sur 40 % de l'écran.
- Premier CTA : « Enquire » dans la nav (y = 20) ; premier CTA de contenu : « Learn More » sur les cartes de voyages (y ≈ 4 476 desktop).

**Interprétation**
- Ce que l'on comprend : une destination, un ton d'explorateur (condensé, majuscules), une promesse (« Luxury and adventure ») et un chemin clair vers les tarifs. Le logo est discret ; le mot ANTARCTICA fait office de logo de page.
- Ce que l'on ressent (navigateur réel, hypothèse) : plein écran vidéo, texte minimal. En headless, l'aplat gris montre que tout le hero repose sur la vidéo. Distractions : cookies + chat proactif cumulés sur mobile.
- Raison de continuer : le titre géant coupé en bas d'écran (descendants hors cadre) et l'accroche invitent au scroll ; le bouton « Rates » promet une réponse rapide à la question du prix.

**Enseignements réutilisables**
- Placer le titre géant en bas du viewport, tronqué, comme signal de scroll.
- Prévoir un poster/fallback pour la vidéo (ici `poster: ''` sur la home) : le hero ne doit jamais dépendre exclusivement d'un flux.
- Ne pas cumuler bannière cookies et chat proactif au chargement mobile.

---

## 3. Direction artistique

**Faits observés**
- Variables CSS : `--bg:#fff`, `--quote-accent: #1f2a44` (« WD_Dark-Blue »), `--primary:#6aa5ff`, `--primary-contrast:#0b0c0f`, `--dark-bg:#090b10`, `--font-sans: "Inter Tight"`, `--font-display: "Cardinal Classic Long"`, `--font-condensed: "Oswald"`.
- Fonds mesurés : #ffffff (dominant), #090b10 (bloc carte/globe), #0e1118 (sections « SAMPLE ITINERARY », « HOW IT WORKS »), #323640 (cartes d'étapes), #e9e7e1 (footer), #f3f1ec (boutons secondaires), #f2f2f2 (page tarifs), #f5f5f5 (amenities), overlays rgba(0,0,0,.2/.5/.6), rgba(31,42,68,.05/.15/.2) (verre bleuté). Textes : #ffffff, #1f2a44, #535353 (footer), #ff7e15 (liens/CTA orange). Tracé de vol cyan (proche de `--primary`, hypothèse).
- Polices chargées : Inter Tight variable (corps, 500), Cardinal Classic Long/Mid (Regular, Medium, Medium Italic — fichier `CardinalClassicLongWeb-SemiBoldItalic-Trial.woff2` : version d'essai en production, à noter), Oswald variable (condensé).
- Échelle desktop → mobile : H1 home 256 → 80 px ; « CPT – WFR » 320/288 → 200/180 px ; H1 des hubs 118 → 52 px ; H2 « OUR CAMPS » 140 → 60 px ; H1 des pages détail 60 → 32 px ; H3 60 → 32 px ; H3 42 → 26 px ; sous-titres 32 px ; labels Oswald 18 px 500 majuscules (interlettrage 9 px sur « THREE UNIQUE OUTPOSTS ») ; corps 14 px / 21 px (colonne 472 px) et 16 px / 22,4 px sur cartes ; 12 px et 10 px en pied. Titres d'itinéraires en serif italique 42 px sur toutes les cartes (identique mobile).
- Grille : conteneurs 1 416 px (marges 12 px) et 1 320 px ; overlay de 8 colonnes (lignes à 60, 248, 484, 720, 956, 1 192, 1 380 px) ; blocs éditoriaux en `col-4` (472 px) + `col-8` (944 px), images 708×715 (ratio 0,99) en regard de texte 472 px décalé (`offset-4`).
- Composants : boutons rayon 2 px (nav 120×40, secondaires 239×60 #f3f1ec, « Start planning » 261×60 orange, « Get in touch » 160×50 bordure rgba(255,255,255,.2)), cartes camps rayon 6 px, « Submit Form » 693×140 rayon 4 px, onglet « How it works » 60×200, chips de camps bleu nuit, tuiles footer 222×110.
- Iconographie : « sparkle » à quatre branches (orange, bleu, blanc selon le fond), flèches fines, « scribble » SVG sous les titres de chapitre, signature SVG, silhouette de montagne (logo, reprise dans le footer).
- Images : ratios 1,6 (plein écran), 1,07 (1440×1350), 0,94 (cartes 720×765), 1,25 (506×404 tarifs), 0,59 (472×800 étapes), 0,49 (330×675 tuiles) ; `object-fit: cover`, `/_next/image` + srcset (28/29 images).
- Place du vide : sections blanches de 786 à 1 355 px à une seule colonne ; 500 px vides au-dessus du wordmark du footer.

### Tokens approximatifs

| Token | Valeur |
|---|---|
| Bleu nuit (texte, chips, quote) | #1f2a44 |
| Orange action | #ff7e15 (hover CTA → #1f2a44 ; hover nav → #ff7e15) |
| Noir profond (carte, itinéraires) | #090b10 / #0e1118 |
| Gris ardoise (cartes d'étapes) | #323640 |
| Beige footer / crème boutons | #e9e7e1 / #f3f1ec |
| Gris clairs | #f2f2f2, #f5f5f5, #efefef |
| Verre bleuté | rgba(31,42,68,.05–.2) + backdrop (20 règles) |
| Display serif | Cardinal Classic Long 400/500, italique pour titres d'itinéraires |
| Display condensé | Oswald 400/500, majuscules, 18 px → 320 px |
| Corps | Inter Tight 500, 14/21 px et 16/22,4 px |
| Rayons | 2 px (boutons), 4 px (formulaire, onglet), 6 px (cartes camps) |
| Header | 80 px fixe transparent, sans backdrop |
| Conteneurs | 1 416 / 1 320 px ; colonnes 472 / 944 px |
| Transition standard | 0,3 s cubic-bezier(.5,1,.89,1) |

**Interprétation**
- Trois voix typographiques assignées à trois rôles : Oswald = données et lieux (coordonnées, « CPT – WFR », labels), Cardinal serif = émotion et noms d'itinéraires (italique), Inter Tight = information. Cette répartition rend la page lisible sans hiérarchie de couleurs.
- Palette quasi monochrome (blanc, bleu nuit, noir) où l'orange n'est utilisé que pour l'action (CTA, onglet, curseur, « Enquire » mobile) et le cyan pour la donnée (tracé de vol) : la couleur est fonctionnelle, pas décorative. Le « chaud » vient des photos (roche ocre, lumière rasante).
- Le rayon 2 px et les bordures à 20 % d'opacité donnent des composants « instrument » plutôt que « boutique ».

**Enseignements réutilisables**
- Réserver une couleur vive à l'action et une seconde à la donnée ; laisser le reste aux photos.
- Utiliser un condensé pour les données chiffrées : elles deviennent des titres.
- Grille visible (overlay) comme texture de marque, à condition de la passer en `mix-blend-mode` pour qu'elle survive aux photos.

---

## 4. Architecture de la page d'accueil

Hauteur documentée : 20 782 px desktop (23 viewports), 19 244 px mobile.

| Position (y desktop) | Section | Objectif | Contenu | Interaction | CTA | Émotion créée |
|---|---|---|---|---|---|---|
| 0 – 1 800 | `hero-banner` (sticky) | Immersion | Vidéo Cloudflare plein écran, H1 « ANTARCTICA » 256 px, accroche italique, grille | Vidéo autoplay (non vérifiée), hero épinglé pendant 900 px puis transition « brume » (`mist-transition_image-container` épinglée à y ≈ 936–1 420, images « Mist transition », « Clouds overlay ») | « Watch Film » | Vertige, silence |
| 1 800 – 2 586 | `home-section` « The Last Continent » | Poser la promesse | H3 serif majuscules 42 px sur 2 colonnes décalées (« VAST, MAJESTIC AND UNIMAGINABLY BEAUTIFUL… ») | Révélation à l'entrée (keyframe reveal 1,4 s, hypothèse d'application) | — | Solennité |
| 2 586 – 3 936 | `wd-mnt` « OUR SEASON » | Expliquer le cadre | Photo montagne 1440×1350, paragraphe 14 px colonne 236 px (nov.–févr., vols depuis Le Cap, 12 guests par camp, équipe > 100) | Image fixe, texte en colonne étroite | — | Confiance opérationnelle |
| 3 936 – 4 476 | « OUR TRIPS » | Titre de chapitre | H3 serif 60 px + scribble SVG | — | — | Respiration |
| 4 476 – 5 241 | `card-flick` (5 cartes 720×765) | Vendre les itinéraires | Nom en italique 42 px, prix (US $75 250 → $16 500), saison, description 16 px, « Learn More ✦ » ; cartes rétrécies en bandes floutées à côté de la carte active | Hover : image scale 1,05 (`matrix(1.05…)`), transition `all` ; carte active dépliée | « Learn More » (5 liens) | Choix, désir |
| 5 241 – 6 196 | Citation fondateur | Preuve humaine | Citation serif italique + signature SVG + « Patrick Woodhead, Co-Founder & CEO » | — | — | Intimité |
| 6 196 – 19 841 | `horizontal-scroll_outer` (13 645 px de piste, wrapper sticky 900 px) | Séquence camps → presse → vol | « OUR CAMPS » 140 px sur triptyque photo/glace ; « POLAR COMFORT » ; trois cartes camps 720×540 verre bleuté (nom serif 42 px, coordonnées Oswald, « Learn More ») ; citation CN Traveler ; « CPT – WFR » 320 px ; carte globe #090b10 (Cape Town → Wolf's Fang, tracé cyan, point pulsé) + « 05:30 HRS / 4 220 KM / -5 °C » | Scroll vertical converti en horizontal (paliers 5 681 → 15 622, 5–6 transforms actifs), seconde brume à 15 622 | « Learn More » ×3, « Watch Film » | Rythme, échelle, technicité |
| ≈ 18 941 – 19 841 | `basic-banner` « START PLANNING YOUR ADVENTURE » | Conversion | Photo plein écran + H3 42 px + bouton | — | « Get in touch » (160×50) | Passage à l'acte |
| ≈ 19 841 – 20 782 | Footer #e9e7e1 | Réassurance + maillage | 4 colonnes (Guests/Trade/Other enquiries, Itineraries, Antarctica, Camps, About, Social), tuiles « Watch Film », « Dates & Rates », « Enquire now », « Newsletter Signup », badges, citation Shackleton, wordmark « WHITE DESERT » ~320 px | Hover liens : opacité .5 → 1, couleur #535353 → #1f2a44 | « Enquire now », « Dates & Rates », « Schedule a call » | Ancrage de marque |

**Logique narrative** : début = le continent ; désir = promesse + saison + preuves logistiques ; l'offre devient concrète à la 5e section (cartes avec prix à 4 476 px, 21 % de la page) ; « chambres » = camps dans la séquence horizontale, après les voyages ; preuve = fondateur puis presse ; carte du vol pour répondre à « comment y va-t-on ? » juste avant la bannière « Start planning » ; fin = wordmark et citation Shackleton.

---

## 5. Scroll et storytelling

**Faits observés**
- `animAttrs` home : `sticky` 14, `horizontal` 39, `parallax` 2, `dataScroll` 4 ; `positionSticky` 6 règles, `willChange` 10, `clipPath` 9, `backdrop` 20, `mixBlend` 6, `scrollSnap` 0, `scrollTimeline` 0.
- Balayage 15 paliers : éléments épinglés = `flyout_container` (toujours), `mist-transition_image-container.visible` à y = 1 420 et 15 622, `horizontal-scroll_wrapper` de 5 681 à 15 622 (≈ 10 000 px de scroll vertical pour ≈ 4 200 px de déplacement horizontal, hypothèse d'après la largeur 5 640 px de la capture pleine page). Transforms actifs : 3 à 9 par palier ; clip-path : 1 à 4 ; opacités partielles : 1 à 6 (35 dans le footer = liens à .5).
- Mobile : la séquence horizontale existe aussi (`horizontal-scroll_wrapper` sticky de 8 192 à 17 132 px, 8 940 px de piste) et un bloc `globe-sticky_wrap` de 632 px épingle la carte avec les stats.
- Changements de fond : blanc → photo → blanc → verre bleuté rgba(31,42,68,.05) (cartes camps, paliers 9 357–13 100) → #090b10 (carte) → photo → beige. Pages itinéraires et tarifs : bloc noir #0e1118 de 9 660 à 13 575 px avec colonne gauche sticky (`itinerary-sticky col-4`) et « scrub » central (`itinerary-scrub_wrap col-8`, z 2) où chaque étape (fond #323640) passe de faible opacité à pleine (opacités partielles 3 à 10 par palier).
- Page About : `about-scrub_component` 3 600 px épinglé, photos d'archives qui glissent latéralement sous une phrase en serif majuscules (« WHITE DESERT WAS BORN FROM REAL EXPLORATION… »).
- Hubs (camps, itineraries) : hero 1 800 px sticky + brume, puis liste verticale classique sans épinglage.

**Interprétation (fonction de chaque effet)**
- Hero épinglé + brume blanche : transition « nuage » entre vidéo et page blanche → **émotion** (on traverse le ciel) et **marque**.
- Cartes « flick » : accordéon où les cartes inactives deviennent des bandes floutées de ~180 px → **orienter le regard** vers une offre à la fois.
- Section horizontale : un chapitre long (camps + presse + vol) en travelling → **rythme** ; le fond noir de la carte marque le passage émotion → **explication**.
- Carte de vol (point `pulsed 2s ease-out`) et stats → **expliquer**, rassurer.
- Scrub d'itinéraire : colonne sticky de contexte + montée d'opacité comme curseur de lecture → **expliquer / orienter**.
- Respirations : sections blanches de 786–1 355 px ; densité ≈ 50 mots par viewport (1 060 mots / 23 viewports).
- Envie de poursuivre : titres tronqués en bas d'écran, sous-nav de section fixée en bas qui annonce le plan.

**Enseignements réutilisables**
- Une seule séquence horizontale, longue (10 000 px) et placée au cœur de la page, plutôt que plusieurs petites.
- Ancrer chaque changement de registre par un changement de fond (blanc → verre → noir).
- Sous-navigation de page fixée en bas (pilules) comme table des matières visible.

---

## 6. Animations et micro-interactions

Mesures CSS : transitions 0,3 s ×126 (mobile ×115), 0,6 s ×5, 0,45 s ×4 ; easings `cubic-bezier(.5,1,.89,1)` ×62 (sortie douce type easeOutQuad), `(.4,0,.2,1)` ×5 (standard Material), `(.76,0,.24,1)` ×1 (in-out quart, onglet flyout), `(.16,1,.3,1)` (expo-out, keyframe reveal), `(.25,1,.5,1)` ; keyframes : 6 sur desktop (dont `pulsed 2s ease-out` et `reveal-opacity/reveal-transform 1.4s`), 14 sur mobile (dont `(.86,0,.07,1)` et `(.49,.78,.46,1.34)` avec rebond — hypothèse : CSS du widget HubSpot « trellis », pas du site). `splitText` : 108 attributs sur /prices, 30 sur Long Stay, 26 sur Discovery Week (titres découpés, hypothèse : reveal mot à mot). `prefers-reduced-motion` : **0 règle**.

| Animation | Déclencheur | Élément | Effet | Fonction | Risque UX |
|---|---|---|---|---|---|
| Arrivée hero | chargement | vidéo + H1 + accroche | keyframe reveal 1,4 s (opacité + translate, expo-out), hypothèse d'application | émotion | vide si la vidéo ne charge pas (poster absent) |
| Préloader | — | aucun détecté | — | — | — |
| Brume de transition | scroll ≈ 936–1 420 px | `mist-transition_image-container` (épinglée, h 462 → 844) | image de nuages en fondu/clip-path au-dessus du hero | marque, transition | coût d'images 1080×675 + 1080×412 |
| Révélation des titres | entrée viewport | H3 serif (splitText) | opacité/translation par mot, 1,4 s (hypothèse) | rythme | 0 règle reduced-motion |
| Zoom photo | hover | `card-flick_item` img | `scale(1.05)`, transition `all` | action | `transition: all` coûteux |
| Accordéon cartes | hover/clic | `card-flick_item` | carte active 720 px, autres réduites à ~180 px floutées | orienter | sur mobile, cartes empilées 366×717 (pas d'accordéon) |
| Transition de page | navigation | ? | non mesurée | — | — |
| Curseur | mousemove | `div.custom-cursor` 4×4 fixed z 10001 | point orange ; état hover non mesuré | marque | invisible sur tactile ; peut gêner la lisibilité si grossi |
| Hover boutons nav | hover | `.btn-tab`, `.btn-cta` | fond rgba(31,42,68,.2) → #ff7e15, bordure → orange, 0,3 s (.5,1,.89,1) | action | contraste blanc/orange 2,6:1 |
| Hover CTA orange | hover | `.btn-orange.hover-blue` | #ff7e15 → #1f2a44, 0,3 s | action | — |
| Hover liens footer | hover | `.footer-link.is-faded` | opacité .5 → 1, couleur #535353 → #1f2a44 | action | état repos peu contrasté |
| Carrousels | clic flèches | `gallery-slider` (12 images 1440×900), vignettes 506×404 (tarifs) | slides + vignettes + légende | expliquer | flèches 60×28 |
| Menu mobile | tap « Menu » | overlay blanc plein écran | liste Home/Experience/Operation/About avec sparkles, « Close » orange, `body overflow: clip` | action | sous-menus repliés : 2 taps minimum |
| Onglet « How it works » | clic | `flyout_container` (fixed, z 10000, 1440×900) | panneau latéral 0,45 s (.76,0,.24,1), onglet 60×200 rayon haut | expliquer | recouvre tout le viewport ; absent sur mobile |
| Vidéo plein écran | clic « Watch Film » | ? | non vérifiée (lightbox, hypothèse) | émotion | — |
| Scroll horizontal | scroll | `horizontal-scroll_wrapper` sticky 900 px | translateX piloté par le scroll (hypothèse JS) | rythme | 10 000 px de scroll pour un chapitre ; conservé sur mobile |
| Carte de vol | scroll | tracé SVG + point `pulsed 2s ease-out` | tracé qui se dessine (hypothèse), point pulsant | expliquer | fond noir abrupt |
| Scrub d'étapes | scroll | `itinerary-scrub_wrap` | opacité des étapes 01→07 | orienter | colonne sticky masque du contenu sur 13 575 px |
| Feedback formulaire | clic | boutons-cartes blancs (radio/checkbox) | état sélectionné non mesuré | action | inputs sans `<label>` (hasLabel false) |
| Reduced motion | media query | — | aucune règle ; `reducedMotion.animatedElements` 4, `transitionElements` 136 | — | non conforme WCAG 2.3.3 |

**Enseignements réutilisables** : un seul easing de sortie (.5,1,.89,1) à 0,3 s pour tous les états, un easing in-out réservé aux panneaux ; garder les animations de scroll pilotées par la position (scrub) plutôt que par le temps ; ajouter systématiquement un bloc `prefers-reduced-motion`.

---

## 7. Navigation et architecture de l'information

**Faits observés**
- Nav desktop : 3 onglets (« Experience », « Operation », « About ») + « Rates » + « Enquire », logo central. Les onglets ouvrent des panneaux (non capturés en desktop) ; le menu mobile liste « Home » puis les 3 rubriques avec sparkles (sous-menus repliés) et, d'après `menu.links`, expose ensuite les 6 itinéraires avec prix, les 3 camps, les 6 régions, About, contacts.
- Header : 80 px, `position: fixed`, fond transparent, sans `backdrop-filter`, aucun changement mesuré au scroll. Sur /prices (fond #f2f2f2), les boutons de nav restent en blanc sur verre bleuté clair : lisibilité faible (`offers-03-scroll1`).
- Sous-navigations de page : pilules fixées en bas (`cta-nav_wrap`, y 820, h 80) sur les itinéraires (« Intro / South Pole / Our Camps / Itinerary / Other Trips » ; « Overview / Curriculum / Itinerary / More Info »), sur About (« Our Story / Foundation / Sustainability ») et sur les régions (5 pilules). Sur mobile elles restent fixées (y 764).
- CTA persistant : « Enquire » dans la nav (120×40 desktop, 80×40 orange mobile) sur toutes les pages ; onglet orange « How it works » à droite (home, Long Stay, enquire) ; bulle de chat HubSpot en bas à droite.
- Chemin vers une offre : home → carte de voyage (« Learn More ») → page itinéraire (prix dans le hero) → « Get in touch » → /enquire : 3 clics. Depuis « Rates » : 1 clic vers la grille complète des prix, puis « Start planning » pré-renseigne l'itinéraire (`/enquire?itinerary=south-pole-and-penguins`).
- Footer complet partout : e-mails par public (travel@, reservations@ trade, press@, careers@, info@), deux téléphones, « Schedule a call » (HubSpot meetings), liens légaux.
- Frustrations : « Learn More » 94×21 px sur mobile ; `/antarctica` qui rend une région ; Whichaway sous `/stay/camps/…` alors que le menu pointe vers `/camps/…`.

**Interprétation**
- L'IA est celle d'un tour-opérateur : « Experience » (itinéraires + camps), « Operation » (régions, aviation, comment ça marche), « About ». L'utilisateur choisit un **voyage**, pas une chambre ; les camps sont des arguments dans le voyage.
- La double persistance (nav + sous-nav en bas) donne à chaque page longue (19 000–23 000 px) une table des matières ; c'est ce qui rend supportables des pages de 25 viewports.

**Enseignements réutilisables** : sous-nav de page en pilules fixée en bas ; CTA unique « Enquire » partout, orange sur mobile seulement ; pré-remplissage du formulaire par paramètre d'URL depuis la grille tarifaire.

---

## 8. Parcours de réservation et conversion

**Faits observés — type de parcours** : **demande / devis**, pas de moteur transactionnel. Formulaire natif (`action: https://white-desert.com/enquire`, reCAPTCHA), prise de rendez-vous HubSpot meetings (« Schedule a call », « book a call directly » dans le flyout), chat HubSpot, e-mails et téléphones. Aucun changement de domaine avant le rendez-vous HubSpot (nouvel onglet non mesuré, `target` absent sur « Enquire »).

**Page /prices (« DATES & RATES »)**
- Hero 585 px : H1 60 px + paragraphe 16 px centré 640 px : dates fixes, prix « per person, sharing », solos bienvenus, familles en exclusivité.
- Filtre `date-price-filter` : « Select your season : 2026 – 2027 / 2027 – 2028 » (toggle).
- 8 cartes blanches (1 320 px de large, 476 px de haut, fond #f2f2f2 autour) : vignette carrousel 506×404 avec flèches 60×28, chips de camps (« Whichaway Camp » + « Echo Base », ou « Explorer Camp »), prix serif 42 px aligné à droite, titre italique 42 px, description 14 px/455 px, trois boutons pleine largeur de colonne : « Trip Dates » et « More info » (239×60, #f3f1ec) et « Start planning » (261×60, orange → bleu au hover, lien `/enquire?itinerary=…`).
- Grille : Baby Penguins & Blue Tunnels $75 250 (Whichaway + Echo) / $65 000 (Explorer) ; South Pole & Penguins $115 500 / $95 000 (Explorer) ; South Pole & Blue Rivers $115 500 ; The Long Stay $110 500 ; Antarctica in a Day $16 500 ; Discovery Week $45 000 (19–26 janvier 2027). Le même itinéraire en deux niveaux de camp : le prix explique le produit.
- Sous la grille : « HOW IT WORKS » (#0e1118) en scrub sticky de 6 étapes (01 Consultation → 02 Confirmation : acompte, assurance, contrôle médical sous 30 jours → 03 Planning : Le Cap J-2/J+2, flotte BMW électrique → 04 On-Boarding → 05 Safety Briefing → 06 Departure), illustré. Flyout « MORE INFORMATION ». Mobile : 3 boutons 330×60 empilés, docHeight 12 604.
- Non vérifié : pop-ins « Trip Dates » / « More info », montant de l'acompte, inclusions détaillées.

**Page /enquire (« START PLANNING »)**
- Hero 585 px (photo coucher de soleil, `fixed-banner_bg is-true-fixed`), promesse : réponse de la « Guest Relations team » sous 24 h.
- Formulaire dans un panneau verre sombre rgba(0,0,0,.6), 1 176 px de large, 2 852 px de haut, 4 groupes titrés 22 px : saison (2 cartes-radio Nov 2026–Feb 2027 / Nov 2027–Feb 2028) ; mois (5 cartes : November, December, January, Not sure, Day trip from Cape Town + rappel du calendrier hebdomadaire) ; intérêts (6 cases : Baby Penguins, South Pole, Ice Tunnels, Blue Rivers, Science Week, Not sure) ; contact (Name*, Surname*, Email*, Country, City/Zip/Time Zone, indicatif + téléphone, textarea « number of travellers, celebrations, aspirations »). « Submit Form » blanc 693×140, puis logo Vogue + citation dans le même panneau.
- Cartes de choix 336×100 (desktop) / 326 px (mobile) ; inputs `hasLabel: false` ; reCAPTCHA ; onglet « How it works » présent. Mobile : docHeight 6 210 ; chat proactif et cookies superposés au premier groupe.

**Réassurance et preuve** : réponse sous 24 h, « How it works » depuis toute page, badges, presse, citation client, équipe > 100, 20 ans. Services additionnels : transferts BMW électriques, séjour au Cap, safaris. Pas d'avis agrégés (TripAdvisor en badge). Bénéfices « direct » non formulés. La Discovery Week (philanthropique, date unique) tient lieu d'offre spéciale.

**Points de rupture** : sortie vers `meetings-eu1.hubspot.com` pour l'appel ; chat « Spam protection enabled » ; formulaire de ≈ 3 000 px sans indicateur d'étape ; le paramètre `?itinerary=` n'a pas d'effet visible dans le hero du formulaire.

**Enseignements réutilisables** : afficher les prix avec les variantes de camp côte à côte ; formulaire en cartes cliquables plutôt qu'en champs, avec « Not sure » systématique ; « How it works » en 6 étapes chiffrées (acompte, assurance, délai médical) comme contenu de réassurance réutilisable en flyout.

---

## 9. Pages « chambres » : camp et itinéraire

**Objet vendu** : une **expédition à date fixe** (5 à 8 jours, ou 1 jour), tarifée par personne en partage, et non une nuit. Le camp est une composante ; la page camp n'affiche **aucun prix** et renvoie vers les voyages.

### Page camp — Echo Base (desktop, docHeight 12 368 ; mobile 18 696)
- Hero 900 px : H1 « ECHO BASE » 60 px (mobile 32 px), phrase de promesse 16 px centrée 502 px, coordonnées Oswald, vignette vidéo « Watch Film » en bas à droite (168×50).
- `glass-center-banner` 1 350 px : photo intérieure (salon du dôme, verre) plein cadre.
- Éditorial 715 px : image 708×715 + colonne 472 px, label Oswald « ECHO BASE », 3 paragraphes (genèse avec Buzz Aldrin, « golden age of space exploration », baies vitrées, douche privée).
- « Echo Pod Amenities » (fond #f5f5f5, 763 px) : titre italique 32 px + liste (pod chauffé, couvertures électriques et bouillottes, salle d'eau privative, machine à café Nova…).
- Citation Travel + Leisure (982 px) : « one of the world's most audacious eco-luxury projects… ».
- « A Closer Look » : galerie 8 images 1440×900 avec légendes (« Sleeping pods with endless views », « The bar with an Anthony James sculpture », « The dining room », « Showers with floor-to-ceiling windows »).
- « HIGHLIGHTS » sur #090b10 (4 842 px) : quatre tuiles 330×675 (WELLNESS, DINING « fresh ingredients flown in weekly », etc., dont une vidéo inline 5,3 Mo), puis « Daily Activities » : 10 H3 42 px majuscules (ICE CLIMBING → SAUNA) avec image 472×315.
- Puis « OUR TRIPS », bannière « START PLANNING » + « Get in touch », footer. La capacité (« six suites per camp », « 12 guests ») n'apparaît que sur la home et le hub.
- Mobile : même ordre, tuiles 390×760, activités 26 px, « Watch Film » 159×40 ; 657 mots.

### Page itinéraire — The Long Stay (desktop, docHeight 23 255) et Discovery Week (19 161 ; mobile 17 468)
- Hero 900 px : titre italique 60 px, ligne « US $110 500 | Late Season » (Discovery : « $45 000 | 19 – 26 JANUARY 2027 »), description 16 px, sous-nav en bas, vignette « Watch Film ».
- Chapitres plein écran en serif 60 px (« THE BEST OF BOTH », « THE SOUTH POLE 90.0000° S », « A GLOBAL PERSPECTIVE ») alternés avec éditoriaux 1 355 px (labels Oswald « WHY CHOOSE? », « AT THE HEART OF THE CLIMATE SYSTEM » avec un scientifique nommé) et une citation sur photo 1 350 px ; galerie 900 px à légendes narratives (« Stand at the South Pole »).
- « SAMPLE ITINERARY » (#0e1118, 13 575 px) : **jour par jour numéroté** 01 → 07 en trois colonnes — gauche sticky (« THE LONG STAY / DAY-TO-DAY » + « A Note About Weather… Antarctica's the dealer » ; Discovery Week : « Tax deduction & donation », 65 %), centre : cartes #323640 avec numéro italique 60 px, titre d'étape italique 18 px (« Return and Camp Transition », « Ice Sheets & Landscape History — Glaciology & Geology », « Departure »), paragraphe 14 px ; droite : images 472×800 empilées.
- Puis « OUR CAMPS » (3 blocs 900 px), « OTHER TRIPS », « START PLANNING », footer. Long Stay : 1 425 mots (page la plus dense). Mobile (Discovery Week) : sous-nav fixe à y 764, itinéraire 7 501 px, H1 32 px, 915 mots.

**Interprétation** : la page itinéraire fait le travail d'une page « suite », mais l'unité de projection est le **jour** ; la page camp garantit le confort (amenities, dining, wellness) sans concurrencer l'itinéraire sur le prix. Réassurance intégrée : note météo, fiscalité du don, sous-nav.

**Enseignements réutilisables** : hero de produit = nom + prix + saison/date sur une ligne ; itinéraire en scrub trois colonnes (contexte sticky / étapes / images) ; légendes de galerie écrites comme des promesses d'action.

---

## 10. Copywriting

**Faits observés**
- Ton : déclaratif, court, sans exclamation (sauf la citation client). Phrases nominales en majuscules serif pour les chapitres ; paragraphes de 40 à 70 mots en 14 px.
- Mécanismes repérés : (1) **superlatifs factuels** empruntés à la géographie (« coldest, driest, highest, windiest »), (2) **chiffres de rareté** (« fewer than 500 people each year », « only six suites », « 12 guests », « over 100 on the ground », « 24-hours of continuous sunshine », « 3 km runway »), (3) **métaphore spatiale** pour Echo (« as close as you can get to leaving Earth without stepping off the planet », Buzz Aldrin, « golden age of space exploration »), (4) **données comme titres** (« 05:30 HRS », « 90.0000° S », coordonnées), (5) **noms d'itinéraires en binômes** « X & Y » (South Pole & Penguins, Baby Penguins & Blue Tunnels), (6) **franchise opérationnelle** (« A Note About Weather… Antarctica's the dealer », acompte, contrôle médical à 30 jours), (7) **voix du fondateur** (« After two decades of White Desert, it still inspires me… », signature), (8) **preuve éditoriale** placée là où le doute survient (Vogue après le formulaire, T+L sur la page camp, CN Traveler après les camps).
- Champ lexical : ice, glacier, blue, pole, remote, continent, wilderness, rite of passage, sanctuary, oasis, outposts, base, runway, season ; le luxe est dit par les objets (sculpture Anthony James, gourmet chefs, wines, BMW électriques, business class) plus que par l'adjectif « luxury » (title et accroche seulement). Caractéristiques techniques reléguées dans « Amenities » et « How it works ».
- CTA : « Enquire », « Get in touch », « Start planning », « Learn More », « Watch Film », « Trip Dates », « More info », « Schedule a call », « Submit Form ». Aucun « Book ».

**Interprétation** : la prestation devient expérience par la **projection dans le temps** (jour 01… 07 : se réveiller, voler, célébrer) et par la **rareté chiffrée** ; le luxe est une conséquence de la logistique, pas un registre lexical.

**Enseignements réutilisables** : écrire un chiffre de rareté par section ; nommer les offres par binômes d'expériences ; rédiger une note de franchise (météo, délais) comme élément de marque ; garder « Enquire »/« Start planning » plutôt que « Book ».

---

## 11. Photographie et vidéo

**Faits observés**
- Plans : aériens très larges (nunataks ocre sur plateau blanc, glace turquoise craquelée, Airbus sur la piste), plans moyens de camps (dômes Whichaway, pod vitré Echo), intérieurs (salon-verre, lit avec vue, vin versé), détails (fauteuil et flûte sur la glace, manchots), humains en silhouettes minuscules (marcheur orange, groupe de 12) ou en portraits d'action (photographe, grimpeur), archives des fondateurs.
- Lumière : soleil rasant permanent (ombres longues), ciel pâle ou bleu profond ; palette blanc / turquoise / ocre / bleu nuit. Aucune image de nuit.
- Ratios : 1,6 plein écran, 1,07 hautes, 0,94 cartes verticales, 0,49 tuiles portrait, 0,59 images d'étapes, 1,25 vignettes tarifs. Proportion lieu/expérience estimée sur la home : ≈ 60 % paysage, 25 % camp, 15 % activité humaine ; sur les pages itinéraires : ≈ 50 % activité.
- Vidéos : hero home (mp4 4,3 Mo, téléchargé par plages, 19,8 Mo de média cumulés sur la home desktop), Echo Base (5,3 Mo ×2), Whichaway mobile (8,25 Mo) ; « Watch Film » sur home, camps, itinéraires, footer (tuile 454×110). Rôle : immersion plein écran et preuve « on l'a filmé ». Rendu non vérifié.
- Cohérence : traitement uniforme (pas de filtre, contraste naturel), bandeaux « Clouds overlay » pour les transitions.

**Shot list pour reproduire ce niveau**
1. Aérien large de la destination à lumière rasante (hero, 16:9 + version 9:16).
2. Aérien vertical d'une texture naturelle (glace/eau/sable) pour fonds de séquence horizontale.
3. Le lieu d'hébergement de loin, à échelle humaine minuscule.
4. L'unité d'hébergement de près, extérieur, trois quarts.
5. Intérieur avec la vue (lit ou salon face à la baie).
6. Détail « luxe » posé dans l'environnement hostile (fauteuil, flûte, plaid).
7. Repas : geste (vin versé), table dressée, produit.
8. Activités : une image par activité (10 ici), cadrage moyen, tenue de marque.
9. Groupe de clients en marche vus de dos (projection).
10. Portrait souriant en action (photographe, grimpeur).
11. Transport : avion/bateau/4×4 au sol et depuis le hublot.
12. Faune emblématique de près et de loin.
13. Archives des fondateurs.
14. Vignettes 1:1 et 4:3 par itinéraire pour cartes et grilles de prix.
15. Film hero 20–30 s muet, boucle, avec poster ; film long « Watch Film ».

---

## 12. Mobile

**Faits observés**
- Header 80 px : « Menu » (80×40, texte) + logo + **« Enquire » orange plein 80×40** (seul CTA persistant, contraste blanc/orange ≈ 2,6:1).
- Hero : accroche serif centrée 2 lignes, H1 80 px en bas ; vidéo 390×844 (4,3 Mo chargée aussi sur mobile). Bannière cookies 360×119 (y 709) + chat proactif 266×304 (y 540) + bulle 100×96 : trois overlays fixes sur toutes les pages capturées (home, camps, prices, enquire, itinéraires).
- Menu : overlay blanc, « Close ✦ » orange, items 40 px environ (Home, Experience, Operation, About avec sparkle), `body overflow: clip` ; sous-menus non déployés sur la capture.
- Titres : H1 hubs 52 px, H1 détail 32 px, H2 « OUR CAMPS » 60 px, H3 26–32 px, titres d'itinéraires italiques **42 px conservés** (2 lignes), « CPT WFR » 200 px, corps 14/21 px (colonne 272–366 px) ; 7 occurrences de textes < 12 px sur la home (`fontSizeSmall`).
- Rythme : docHeight 19 244 (home), 12 187 (camps), 18 696 (Echo), 17 468 (Discovery Week), 12 604 (prices), 6 210 (enquire). Cartes de voyages 366×717 empilées (plus d'accordéon) ; séquence horizontale **conservée** (sticky 8 940 px, cartes camps 350×438) ; carte de vol conservée (`globe-sticky_wrap` 632 px) ; brume conservée.
- Boutons : « Learn More » 94×21 et 270×21 (hauteur < 44 px), flèches de galerie 60×28, « Trip Dates / More info / Start planning » 330×60, « Submit Form » 326×140, tuiles footer 178×100 / 366×100, « Get in touch » 160×50.
- Formulaire : cartes de choix 2 colonnes (≈ 150×80), champs 326 px, même ordre que desktop ; pas d'étapes.
- Vitesse : home mobile 175 requêtes, 15,2 Mo (media 4,3 Mo, scripts 5 Mo, CSS 656 Ko dont HubSpot 418 Ko), TTFB 216 ms, FCP 660 ms, load 2,7 s ; Echo mobile 16,4 Mo, load 17,9 s ; Whichaway mobile 17,8 Mo ; camps mobile TTFB 11,9 s (variance serveur).
- Lisibilité : texte blanc sur cartes verre clair (carte Explorer sur neige) et texte 14 px sur photos claires (paliers home-mobile-03-scroll4) faibles ; coordonnées Oswald 12 px.
- Absent sur mobile : onglet « How it works » (flyout non détecté dans `fixed`), curseur.

**Interprétation** : le mobile conserve presque toute la mise en scène desktop au prix de pages de 12 à 19 000 px et de 15–18 Mo, en dégradant les cibles secondaires ; l'essentiel (prix, formulaire, CTA orange) reste accessible. Différences : CTA orange mobile seulement, cartes empilées, flyout supprimé, chat plus intrusif.

---

## 13. Performance, accessibilité, SEO

**Faits observés**
- Home desktop : 462 requêtes, 43,9 Mo (media 19,8 Mo, scripts 12,9 Mo/145 fichiers, images 6,1 Mo/92, fonts 1,8 Mo/22, CSS 1,4 Mo/74), TTFB 459 ms, FCP 1 404 ms, DOMContentLoaded 1 462 ms, load 6 412 ms. Plus gros fichiers : mp4 hero 4,3 Mo (×4 plages), `visitor.js` HubSpot 1,35 Mo (×2), image Sanity 484 Ko (×3 — doublons), reCAPTCHA 344 Ko.
- Autres pages desktop : prices 326 req / 11,9 Mo, load 806 ms (passe 1) puis TTFB 11,6 s (passe 2) ; enquire 278 req / 12,2 Mo, load 1,0 s ; camps 284 req / 13,2 Mo, TTFB 939 ms, load 2,4 s ; Echo 317 req / 24,3 Mo (media 10,6 Mo), TTFB 2,6 s, load 15,2 s ; Discovery Week 326 req / 13,9 Mo, load 3,5 s ; Long Stay 355 req / 16 Mo, TTFB 11,5 s ; about 317 req / 11,3 Mo, load 814 ms.
- Tiers : google (37 req), hsappstatic (22), clarity (20+), gstatic (15), GTM (12), bing (10), cloudflarestream (8), doubleclick (7), facebook (12), metricool (6), hubspot/hsforms (11). Lazy : 23/29 images (home), 39/49 (prices) ; srcset quasi systématique ; `/_next/image` (WebP/AVIF, hypothèse). Sections à hauteur fixe ; hero sans poster ; woff2 auto-hébergés.
- Contrastes estimés : #1f2a44 sur #fff ≈ 13,4:1 (excellent) ; #535353 sur #e9e7e1 ≈ 6,0:1 mais liens à opacité .5 ≈ 2,5:1 (échec) ; blanc sur #ff7e15 ≈ 2,6:1 (échec AA pour 16 px) ; blanc sur #323640 ≈ 10:1 ; texte d'étapes gris clair sur #323640 ≈ 4–5:1 ; blanc sur cartes verre claires sur neige < 3:1 (échec) ; nav blanche sur fond clair de /prices < 3:1.
- Clavier : `focusOutlineNone` 86 (home), 106 (prices), 69 (enquire) ; `skipLink: false` ; landmarks `main` 1, `nav` 1, `header` 0, `footer` 0 ; `linksNoName` 2–3 ; `ariaHidden` 7–22 ; iframe sans titre 1 (enquire) ; `tabindex -1` ×2 (enquire) ; inputs radio/checkbox sans `<label>` associé (`hasLabel: false`) ; vidéo sans attribut ARIA ; `alt` présents partout (missingAlt 0, emptyAlt 4–16 sur images décoratives).
- Reduced motion : 0 règle CSS ; vidéo autoplay non désactivée.
- Structure : h1 = 1 sur toutes les pages ; hiérarchie H1 → H3 (H2 rares, utilisés pour le sur-titre « Regions »/« About » en 32 px avant le H1 : ordre inversé) ; H4 en labels 18 px.
- Métadonnées : title et description spécifiques par page ; og:title/description/image (og:image générique `og-default-image.jpg` sur itineraries, Long Stay, Discovery Week, about) ; canonical présent (mais /antarctica → /antarctica/wolfs-fang-runway-mountains) ; `hreflang` : aucun ; `lang="en"` ; JSON-LD `Organization` avec logo ; pas de JSON-LD `Product`/`Trip`/`Offer` malgré les prix affichés.
- Contenu indexable : 1 060 mots (home), 819 (prices), 711 (enquire), 657 (Echo), 457 (camps), 438 (itineraries), 1 425 (Long Stay), 923 (Discovery Week), 664 (Mountains), 435 (founders). CSS total 136 Ko (site) + 418 Ko HubSpot theme sur mobile.

**Interprétation** : l'immersion (vidéos multiples, 145 scripts dont 7 outils de tracking) coûte 12 à 44 Mo par page ; le perçu reste correct grâce au lazy loading, sauf avec vidéos inline (Echo : 15 s). Accessibilité : manques structurels. SEO technique propre, balisage des offres absent.

**Enseignements réutilisables** : poster obligatoire sur les vidéos et une seule vidéo par page ; dédupliquer les requêtes d'images ; conserver un focus visible ; ajouter JSON-LD `Product`/`Offer` quand les prix sont publics ; og:image spécifique par itinéraire.

---

## 14. Conclusion

### 15 meilleurs éléments
1. H1 « ANTARCTICA » 256 px en Oswald calé en bas du viewport : la destination comme logo.
2. Trois polices à trois rôles (donnée / émotion / information) sans confusion.
3. Prix affichés dès les cartes de la home et dans le hero de chaque itinéraire (« US $110 500 | Late Season »).
4. Page tarifs en cartes comparables (chips de camp, 3 actions par carte, pré-remplissage `?itinerary=`).
5. Formulaire en cartes cliquables avec « Not sure » et promesse de réponse en 24 h.
6. « How it works » en 6 étapes numérotées, disponible en onglet fixe et en section scrub.
7. Itinéraire jour par jour en trois colonnes (contexte sticky / étapes / images).
8. Note de franchise (« A Note About Weather ») intégrée au produit.
9. Coordonnées GPS et stats de vol comme ornements typographiques.
10. Carte de vol animée sur fond noir avec temps / distance / température.
11. Séquence horizontale unique de 10 000 px regroupant camps, presse et vol.
12. Transition « brume » entre vidéo et page blanche.
13. Système de couleur : orange = action, cyan = donnée, tout le reste neutre.
14. Sous-navigation de page en pilules fixée en bas, conservée sur mobile.
15. Footer-signature : wordmark géant, badges, citation Shackleton, e-mails par public (guests / trade / press).

### 5 faiblesses / limites
1. Overlays cumulés sur mobile (cookies + chat proactif + bulle) recouvrant 40 % du hero.
2. Aucune règle `prefers-reduced-motion`, focus supprimé (86–106 règles), formulaires sans labels.
3. Poids : 44 Mo sur la home desktop, vidéos de 4 à 8 Mo aussi sur mobile, 15 s de chargement sur Echo ; TTFB instable (jusqu'à 11,9 s).
4. Contrastes : blanc sur orange, liens footer à 50 %, nav blanche sur fond clair de /prices, texte sur cartes verre claires.
5. Cibles tactiles « Learn More » 94×21 px et flèches 60×28 ; double arborescence `/camps/` vs `/stay/camps/` ; police « Trial » en production.

### 10 principes réutilisables
1. Vendre une unité de temps (semaine, jour) avant l'unité de lieu (chambre).
2. Prix visibles partout, avec variantes de gamme côte à côte.
3. Un chiffre de rareté par section.
4. Données dures en display condensé.
5. Une seule couleur d'action, réservée.
6. Parcours de demande en cartes cliquables, jamais en champs texte d'abord.
7. Réassurance en étapes numérotées, accessible depuis toute page.
8. Storytelling par scrub scroll (position) plutôt que par animations temporelles.
9. Table des matières de page fixée en bas.
10. Preuve éditoriale placée au point de doute (formulaire, page produit).

### À ne pas copier (propre à la marque)
- Le mot « ANTARCTICA » et le registre polaire/spatial (Echo, Buzz Aldrin), les coordonnées réelles, la carte Cap → Wolf's Fang, la signature Woodhead, les badges IAATO/CarbonNeutral, les citations presse nominatives, la palette glace turquoise/ocre, le nom des itinéraires.

### Ce que ce site apporte que les sites « quiet luxury » (FORESTIS, Seagate, Le Collectionist) n'apportent pas
- **Tarifs publics et comparables** avec variantes de camp, dès la home.
- **Narration d'expédition jour par jour** avec scrub sticky et note météo.
- **Cartographie et données** (carte de vol, coordonnées, stats) comme langage graphique.
- **Couleur d'action franche** (orange) et typographie condensée géante, là où le quiet luxury reste en serif fin et tons neutres.
- **Séquence horizontale** et transitions « brume » : un rythme de film plutôt qu'un catalogue.
- **Preuve d'opérateur** (100 personnes, piste, flotte, 20 ans, fondation) plutôt que preuve d'ambiance.

### Notes /10
- **Branding : 9** — destination en H1, architecture Experience/Operation/About cohérente, coordonnées et stats comme signature, preuves à trois niveaux ; retenue : logo discret et font « Trial ».
- **Direction artistique : 8,5** — système typographique à trois voix, tokens clairs (2 px, 0,3 s, orange unique), photos uniformes ; retenue : contrastes blanc/orange et cartes verre claires.
- **Animations : 8** — scrub, brume, séquence horizontale, carte pulsée, easings cohérents ; retenue : 0 règle reduced-motion, vidéo sans poster, non vérifiable en headless.
- **UX : 7** — sous-nav fixée, chemin de 3 clics vers le formulaire, « How it works » partout ; retenue : pages de 20 000+ px, overlays mobiles, cibles 21 px, hub /antarctica ambigu.
- **Conversion : 8** — prix transparents, formulaire en cartes, 24 h, rendez-vous HubSpot, pré-remplissage ; retenue : formulaire long sans étapes, pop-ins « Trip Dates » non vérifiées, sortie vers HubSpot.
- **Mobile : 6,5** — CTA orange persistant, séquence et carte conservées, formulaire lisible ; retenue : 15–18 Mo, chat + cookies superposés, « Learn More » 94×21, textes 12 px.
- **Note globale : 8/10** — référence du tourisme expérientiel pour la transparence tarifaire, la narration d'itinéraire et le langage cartographique ; pénalisée par le poids, l'accessibilité et l'intrusivité mobile des outils tiers.

---

## Observations clés à conserver pour la phase comparative

- H1 destination « ANTARCTICA » 256 px desktop / 80 px mobile (Oswald), calé en bas du hero vidéo 1 800 px sticky ; « CPT – WFR » 320 px ; wordmark footer ≈ 320 px.
- Trois familles : Cardinal Classic Long (serif, italique pour noms de voyages 42 px sur tous supports), Inter Tight 500 (14/21 et 16/22,4 px), Oswald (labels 18 px, coordonnées, stats) ; fichier « Trial » chargé.
- Palette : #1f2a44, #ff7e15 (action seulement), #090b10/#0e1118, #323640, #e9e7e1, #f3f1ec, verre rgba(31,42,68,.05–.2) ; rayons 2/4/6 px ; transition 0,3 s cubic-bezier(.5,1,.89,1) ×126.
- Home 20 782 px desktop / 19 244 mobile ; séquence horizontale épinglée de y 5 681 à 15 622 (≈ 10 000 px) ; brume épinglée à 1 420 et 15 622 ; 14 attributs sticky, 39 « horizontal » ; aucune lib d'animation détectée ; 0 règle reduced-motion.
- Prix publics : $16 500 (jour) → $115 500 ; même itinéraire décliné Whichaway+Echo / Explorer ($75 250 vs $65 000, $115 500 vs $95 000) ; Discovery Week $45 000 dont 65 % de don ; « per person, sharing ».
- Page /prices : 8 cartes 1 320×476, vignette 506×404, 3 boutons (Trip Dates / More info 239×60 crème, Start planning 261×60 orange → `/enquire?itinerary=`), filtre de saison 2026–27 / 2027–28, « How it works » 6 étapes (acompte, assurance, examen médical 30 j, Le Cap J-2/J+2).
- /enquire : formulaire natif 4 groupes (saison 2 cartes, mois 5, intérêts 6, contact 7 champs), « Submit Form » 693×140, promesse 24 h, reCAPTCHA, citation Vogue ; inputs sans label ; docHeight 4 583 desktop / 6 210 mobile.
- Itinéraire Long Stay : 23 255 px, 1 425 mots, hero « US $110 500 | Late Season », sous-nav 5 pilules fixée à y 820, bloc « SAMPLE ITINERARY » 13 575 px sur #0e1118 avec colonne sticky 472 px + étapes #323640 + images 472×800 ; Discovery Week : 7 jours numérotés, sous-nav Overview/Curriculum/Itinerary/More Info.
- Page camp Echo : 12 368 px, pas de prix, hero + intérieur 1 350 px + éditorial 708×715 / 472 px + amenities #f5f5f5 + citation T+L + galerie 8 + « HIGHLIGHTS » #090b10 4 842 px avec 10 activités en 42 px ; vidéo inline 5,3 Mo.
- Nav : 80 px fixe transparente sans backdrop, 5 pilules 120×40, hover → orange ; mobile « Menu » + « Enquire » orange 80×40 ; onglet « How it works » 60×200 (desktop seulement) ; chat HubSpot proactif 266×304 + cookies 360×119 superposés sur mobile.
- Perf : home desktop 462 req / 43,9 Mo (media 19,8 Mo, mp4 4,3 Mo, visitor.js 1,35 Mo), FCP 1,4 s, load 6,4 s ; mobile 175 req / 15,2 Mo, FCP 0,66 s, load 2,7 s ; Echo desktop 24,3 Mo, load 15,2 s ; TTFB de 216 ms à 11,9 s selon passes ; 7 tiers de tracking (GA, GTM, Clarity, FB, Bing, Metricool, HubSpot).
- A11y : focusOutlineNone 69–106, skipLink absent, landmarks header/footer absents, labels absents sur radios/checkboxes, alt présents (0 manquant), h1 unique partout, H2 de sur-titre avant H1.
- SEO : titles/descriptions spécifiques, canonical, JSON-LD Organization seulement (pas d'Offer), og:image générique sur itinéraires, hreflang absent, /antarctica canonical vers « wolfs-fang-runway-mountains », double chemin /camps/ vs /stay/camps/.
- Preuves : IAATO, CarbonNeutral, Global Vision Awards 2024, CN Traveler (citation Stanley Stewart), T+L, Vogue (Nick Remsen), TripAdvisor, « 20 Years », signature du cofondateur, citation client « F.G. Guest », scientifique nommé (Prof. Steven Chown).
- Mécanismes de copy : superlatifs géographiques, rareté chiffrée (« fewer than 500 », « six suites », « 12 guests », « over 100 »), métaphore spatiale, binômes « X & Y », note de franchise météo, CTA « Enquire / Start planning / Get in touch », jamais « Book ».
