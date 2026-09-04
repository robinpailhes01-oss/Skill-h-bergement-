# Fiche d'audit — Pelorus Travel

Clé : `pelorus` · Analyse du 2026-09-04 · Chromium headless via Playwright, 1440×900 (desktop) et 390×844 DPR 2 (mobile).

---

## 0. En-tête

**Nom** : Pelorus Travel (PelorusX Ltd, Londres ; groupe Pelorus = Travel + Yachting + Aviation + Foundation). **URL de départ** : https://pelorustravel.com/. Objet vendu : un **voyage sur mesure** (itinéraire privé conçu par un « Travel Designer »), pas une nuit ni une chambre. Title home : « Pelorus Luxury Travel | Luxury Holidays 2026 / 2027 ».

### Pages étudiées

| Label | URL | Desktop | Mobile |
|---|---|---|---|
| home | https://pelorustravel.com/ | oui (+ balayage `home-sweep` en 15 paliers) | oui |
| experiences (catalogue filtrable) | https://pelorustravel.com/experiences | oui | non |
| dining (= page destination **Svalbard**, mal étiquetée) | https://pelorustravel.com/svalbard | oui | non |
| spa (= page destination **Espagne**, mal étiquetée) | https://pelorustravel.com/spain | oui | non |
| offers (= page destination **Émirats**, mal étiquetée) | https://pelorustravel.com/united-arab-emirates | oui | non |
| about | https://pelorustravel.com/about | oui | non |
| contact (= formulaire **/enquire**) | https://pelorustravel.com/enquire | oui | non |
| destinations (index) | https://pelorustravel.com/destinations | oui | non |
| destination (Antarctica) | https://pelorustravel.com/antarctica | oui | non |
| process | https://pelorustravel.com/about/process | oui | non |
| why (Why Pelorus) | https://pelorustravel.com/about/why-pelorus | oui | non |
| testimonials | https://pelorustravel.com/about/client-testimonials | oui | non |
| contact v2 (page Contact, sans formulaire) | https://pelorustravel.com/contact | oui (a écrasé les fichiers `contact-*` de /enquire ; les données /enquire avaient été extraites avant) | non |
| curious (Curious Minds) | https://pelorustravel.com/curious-minds | oui | non |
| campaign | https://pelorustravel.com/campaigns/what-does-adventure-mean-to-you | oui | non |
| booking (sonde CTA sur Antarctica, seconde visite) | https://pelorustravel.com/antarctica | oui (sonde : « no obvious booking CTA visible ») | non |

### Limites de l'observation

- **La modale cookies (CookieScript, 800×235 px, voile #111111 à 50 %) n'a jamais été fermée** : présente sur toutes les captures (`00-initial` = `01-hero`), elle masque le centre de chaque viewport ; les descriptions s'appuient sur les JSON et les zones visibles.
- Une **pop-in newsletter Sleeknote** (~360×470 px, bas droite) apparaît dès ~2 300 px desktop et **plein écran sur mobile** : `home-mobile-05-menu-open` montre cette pop-in, **pas le menu** ; le menu mobile est déduit des 47 `navLinks` du DOM.
- Vidéos `autoplay muted loop playsinline` en `paused` : lecture non vérifiable ; les captures montrent le poster 1920×1080.
- Header capturé dans deux états : nav complète (134 px) sur le balayage home ; **masquée, pastille hamburger flottante 56 px** sur les `03-scroll` des pages internes ; déclencheur (direction du scroll ?) non mesuré.
- Hover mesuré sur `.btn` seulement (`{}`) ; LCP `null` ; Lighthouse indisponible ; transitions de page et curseur tactile non observables.
- Pages destination, process, why, testimonials, curious, campaign et contact observées en desktop uniquement ; le mobile n'est vérifié que sur la home.

---

## 1. Positionnement de marque

**Faits observés**
- Meta description home : « private luxury travel experiences that seek to transform our perspective of the world and our impact on the planet ». JSON-LD `Organization` + `TravelAgency` (`@id` `#site-owner`, `alternateName` « Pelorus »).
- Trois H1 sur la home : « EXPERIENCES THAT MOVE YOU » (Berlingske Serif 16 px), « JOURNEYS WITHOUT LIMITS OR BOUNDARIES » (MFred 30 px, capitales, interlettrage 3 px), « Rooted in sustainability » (Berlingske 20 px).
- Bloc d'introduction (y = 900 px) : deux lignes Montserrat 600 capitales 14 px (« Luxury travel & yachting experiences designed with unrivalled creativity » / « In a world full of off-the-shelf itineraries, Pelorus thinks differently ») puis un paragraphe Berlingske 16 px qui pose l'origine (« two former British Army captains », « military-grade precision », accès « across air, land, and sea »).
- Architecture de marque visible sur la home et l'about : grille « Areas of expertise » à trois entrées **Travel / Yachting / Aviation** (about : **Land / Sea / Air** = Pelorus Travel / Pelorus Yachting / Pelorus Aviation) ; pied de page « Pelorus Group » à cinq entrées (Group, Travel, Yachting, Aviation, Foundation).
- Bandeau presse (10 logos : Robb Report, Financial Times, Elite Traveler…) et 9 badges en pied de page (AECO, IAATO, IATA, Royal Geographical Society, Serandipians, T+L A-List 2026, B Corp, CN Traveller 2025, Pelorus Foundation).
- Menu principal : Experiences · Destinations · When to Go · Business · Stories · About ; entrée « Enquire » orange fixe. Sous-menus : Experience Types (Adventure, Conservation, Ski, Safari, Beach, Wildlife, Culinary) et Traveller Type (Family, Group & Celebrations, Honeymoons, Couples, Solo) ; Destinations par 9 continents/régions.
- Catalogue `/experiences` : 186 expériences, cartes avec **saison + prix par personne** (« MAY-OCT • £125,000 PP », « ALL YEAR ROUND • £23,000 PP », « MAY-SEP • £20,000 PP »), filtre « Price ». Page Espagne : « Dec-Mar £26,000 PP 4 Guests ». Formulaire /enquire : budget total obligatoire (première tranche visible « £40,000 »).

**Interprétation**
- Positionnement : **agence de voyages d'aventure sur mesure, ultra-haut de gamme, à narration expéditionnaire** et à discours d'impact ; gamme assumée par les chiffres (prix, badges, presse) plus que par la DA (magazine outdoor, pas palace). « Luxury » sature les titles (SEO) mais la promesse écrite est « transformer sa perspective ».
- Cible : familles fortunées et groupes (les deux grilles de profil FAMILY / GROUP CELEBRATIONS / COUPLES, « Pelorus Junior »), marché UK/US (sélecteur United Kingdom / United States, deux numéros de téléphone), clientèle yachting (témoignages « Pelorus Yachting Client », « Charter Guest »), et **agents de voyages** (la pop-in newsletter demande « Are you a travel agent? »).
- Territoire émotionnel : exploration, adrénaline maîtrisée (« military-grade precision »), curiosité, transmission (enfants, fondation). Personnalité : directe, capitales condensées, orange « signal ». Valeurs lisibles : accès rare, précision, conservation, impact.
- Différence avec un site hôtelier générique : il n'y a **aucune chambre** ; l'unité vendue est un itinéraire à 20 000–125 000 £ par personne, et le site accepte d'afficher ces prix en vitrine, ce que les hôtels « quiet luxury » évitent.
- Cohérence : offre (sur mesure) ↔ mots (« without limits or templates ») ↔ images (hélicoptères, yachts dans la glace, buggies) ↔ interactions (un seul verbe d'action : ENQUIRE). Rupture : la pop-in newsletter et la modale cookies contredisent l'idée d'accès privé et calme.

**Enseignements réutilisables** : trois portes d'entrée (destination / expérience / profil) plutôt que des chambres ; prix par personne assumé sur les cartes (auto-qualification) ; marque ombrelle + sous-marques par élément ; preuve par badges sectoriels plutôt que par étoiles.

---

## 2. Première impression (5 premières secondes)

**Faits observés**
- Desktop 1440×900 : header blanc en deux barres (84 px + 50 px = 134 px, `fixed inset-x-0 top-0 z-[999]`) : téléphone, drapeau UK, loupe à gauche ; logo PELORUS centré (rose des vents dans le O) ; bouton **ENQUIRE** orange #f38b00 117–144×42 px à droite ; hamburger. Deuxième barre : 6 entrées Montserrat 12–13 px capitales avec chevrons.
- Hero plein écran (900 px, `hero-full-screen h-screen`) : vidéo Vimeo 1080p (21,4 Mo téléchargés en `206`) avec poster désert au coucher du soleil (buggy soulevant la poussière, à droite). Titres alignés **à gauche**, blancs, MFred capitales : « EXPERIENCES THAT MOVE YOU » sur deux lignes (~60 px rendus), sous-titre « JOURNEYS WITHOUT LIMITS OR BOUNDARIES » (30 px), « Rooted in sustainability » en serif 20 px.
- Modale cookies centrée (800×235) avec bouton vert #6aa84f « ACCEPT ALL » (r = 30 px, Open Sans) — **le seul élément arrondi et le seul vert du site**.
- Mobile 390×844 : header 84 px (logo à gauche, ENQUIRE orange 234×82 px CSS ≈ 117×41 px, hamburger) ; vidéo 390×844 (ratio 0,46) ; le titre est masqué par la modale cookies (371×225 px).
- Premier CTA visible : ENQUIRE (nav, y = 21). Deuxième : « ENQUIRE NOW » (y = 1 180–1 260, sous l'intro).

**Interprétation**
- On comprend en une seconde « voyages d'aventure de luxe » (poster désert + « move » + « journeys ») ; le message est double, émotion et rupture avec le catalogue, la durabilité servant de caution.
- Menu lourd (134 px = 15 % du viewport) mais lisible ; l'orange est le seul point de couleur.
- Distractions fortes : modale cookies bloquante + (dès 2 300 px) pop-in Sleeknote qui occupe 25 % de la largeur ; sur mobile la pop-in prend tout l'écran. **Deux interruptions avant tout contenu = point noir de la première impression.**
- Raison de continuer : l'accès rare et les trois univers ; aucun ancrage transactionnel (ni prix ni date) sur le hero.

**Enseignements réutilisables** : hero titre à gauche + vidéo pleine largeur + CTA unique dans le header fonctionne pour une agence ; ne jamais cumuler bannière cookies modale et pop-in newsletter sur la même session.

---

## 3. Direction artistique

**Faits observés (JSON home + captures)**
- Fonds : #ffffff (740), #000000 (93, overlays), #f5f5f5 (88), #535353 (footer), #ebe9e6 (sous-nav, blocs about), **#063657 marine** (bloc yachting), #191919. Accent unique **#f38b00** (`--color-brand-primary`).
- Textes : #000000 (385), #6f6f6f (210), #ffffff (155), #2d2d2d (105), #f38b00 (38, liens « Read more », « Explore », prix), #66665d (fil d'Ariane).
- Typographies (`@font-face`) : **MFred** (display condensé, un poids), **Berlingske Serif Text** (Thin/Light/Regular), **Montserrat** 300–700 (labels, nav, boutons, eyebrows), CupCakes (script), Open Sans (cookies) ; 10–16 fichiers, 462–674 Ko.
- Échelle des titres desktop : H1 pages internes **96 px** MFred (interlettrage 9,6 px = 10 %), H1 about **128 px** (12,8 px), H2 section « ADVENTURE AGENDA » 72 px, cartes de grille 48–60 px, H2 « eyebrow » **18 px Montserrat 600 capitales interlettrage 7,2 px (40 %)**, H3 cartes 16 px Montserrat 600 (0,8 px). Mobile : H2 72 → 36 px, H1 30 px inchangé, cartes 48 px conservées.
- Corps : Berlingske 16/24 px, 18/28 px pour les intros centrées (896 px), Montserrat 600 caps 14/20 px pour les accroches ; distribution home 11 px ×58, 12 px ×40, 14 px ×37, 16 px ×29 — **le 11–12 px domine**.
- Conteneurs : 1 280 px (×16), 896 px (intro texte), 600 px, 768 px. Grilles à 3 colonnes de 477×480 px (ratio 0,99) et cartes articles 364×236 (1,54).
- Boutons : rectangle **r = 0**, 42 px de haut, Montserrat 12 px 600 capitales interlettrage 3,6 px (30 %), padding horizontal 64 px ; plein orange/blanc (primaire) ou contour orange 1 px/texte orange (secondaire « btn-reverse »). Flèches de carrousel : cercles 48 px r = 9999 px, contour blanc 1 px ou noir.
- Images : 86 `<img>` sur la home, 0 `srcset`, 1 seul `loading="lazy"`, formats jpg 64 / png 7 / jpeg 6 / svg 9 ; natifs 2250×1750, 1200×675, 1080×1080, affichés en `object-fit: cover`. Photos hero de pages internes 1536×760 recadrées en 1440×640 (2,25).
- Cartes de grille : photo assombrie (fond #000000 à opacité partielle, hypothèse `bg-opacity`) + titre MFred blanc centré 48–60 px + « Find Out More » ; cartes catalogue : idem + bandeau noir plein avec « saison • prix » en Montserrat 11 px interlettré.
- Textures : fond kraft + doodles + titre script pour « Curious Minds » (seul élément illustré) ; photos superposées en décalé (492×492 / 328×328) sur « We care ».

### Tableau de tokens approximatifs

| Token | Valeur observée |
|---|---|
| Fond principal / secondaire | #ffffff / #f5f5f5, #ebe9e6 (sable) |
| Fond sombre | #535353 (footer), #191919, #000000 (overlays), #063657 (bloc yachting) |
| Accent | #f38b00 (orange) — seul accent, boutons + liens + prix |
| Texte | #000000, #2d2d2d, #6f6f6f (secondaire), #66665d (breadcrumb) |
| Display | MFred, capitales, 96–128 px (H1), 48–72 px (H2/cartes), tracking 10 % |
| Eyebrow | Montserrat 600, 18 px, capitales, tracking 40 % |
| Corps | Berlingske Serif Text 300/400, 16–18 px, interligne 1,5–1,55 |
| UI/labels | Montserrat 500/600, 11–14 px |
| Script | CupCakes (campagne Curious Minds) |
| Bouton | 42 px, r 0, 12 px caps tracking 30 %, padding 64 px, orange plein ou contour |
| Rond | 48 px r 9999 (flèches), pastilles 115 px |
| Largeur contenu | 1 280 px ; texte centré 896 px |
| Ratios images | 1,6 (hero home), 2,25 (hero interne), 0,99 (grille), 1,54 (articles), 1,78 (accommodation 656×369 `contain`) |
| Header | 134 px desktop (84 + 50) ; 84 px mobile |
| Transition | 0,15 s cubic-bezier(.4,0,.2,1) sur `.btn` ; 0,5 s (×28), 2 s (×33) sur reveals |

**Interprétation**
- La DA est un **hybride magazine d'aventure / brutalisme typographique** : titres condensés en capitales géantes sur photo, serif fine pour le récit, orange saturé pour l'action. Pas de dorure ni de beige : le luxe est signifié par la rareté des lieux, pas par la palette.
- Le contraste MFred (industriel) / Berlingske (éditorial) crée la tension « précision militaire / récit ». L'eyebrow Montserrat 18 px à 40 % d'interlettrage est le motif de section le plus répété (10+ sur la home).
- Angles droits systématiques (r = 0) sauf cercles de navigation ; l'asymétrie vient des photos décalées et des cartes blanches flottantes des témoignages.
- Faiblesse : profusion de 11–12 px (98 occurrences) et pas de `srcset` alors que les fichiers natifs vont jusqu'à 5,7 Mo (`hero-kenya-job-role-(1).png`, chargé sur **toutes** les pages via la pop-in Sleeknote).

**Enseignements réutilisables** : une seule couleur d'accent saturée réservée à l'action ; eyebrow interlettré + H2 display condensé ; cartes photo assombries avec titre centré pour les portes d'entrée ; bandeau « saison • prix » sur fond noir plein pour les cartes catalogue.

---

## 4. Architecture de la page d'accueil

Hauteur totale 7 331 px desktop (8,1 écrans), 10 898 px mobile (12,9 écrans). Reconstruction à partir des `sections` (y desktop) et des captures `home-sweep-00..14`.

| Position (y) | Section | Objectif | Contenu | Interaction | CTA | Émotion créée |
|---|---|---|---|---|---|---|
| 0–900 | Hero vidéo plein écran | Poser l'univers | Vidéo désert (poster), 3 H1 alignés à gauche | Autoplay muet (non vérifié), reveal | aucun dans le hero ; ENQUIRE nav | Mouvement, horizon |
| 900–1 270 | Intro manifeste | Dire la différence | 2 accroches caps 14 px + paragraphe fondateurs (896 px) | reveal | ENQUIRE NOW (orange, 264×42) | Confiance, précision |
| 1 302–1 581 | Bandeau presse | Preuve | 10 logos gris (Robb Report, FT…) | Swiper (défilement, hypothèse autoplay) | — | Légitimité |
| 1 629–2 231 | Areas of expertise | Architecture de marque | 3 cartes 477×480 : TRAVEL / YACHTING / AVIATION | hover (non mesuré) | « Find Out More » ×3 | Ampleur (terre/mer/air) |
| 2 295–2 783 | Why Pelorus | Argumentaire | 4 pastilles reliées : sans templates, créativité/précision, accès privé, impact | reveal | — | Méthode |
| 2 783–3 309 | Slider campagne | Désir + agenda | Slides « Curious Minds » (kraft + script), « What does adventure mean to you? » (mosaïque + vidéo 720p), « Adventure Agenda 2026 » (72 px) | Swiper, flèches 48 px | « Where will curiosity take them? », « Find your adventure », « Dive in » | Curiosité |
| 3 373–4 347 | What our clients say | Preuve sociale | Photo plage plein écran, 3 cartes blanches (citation serif italique 20 px, libellé orange par type de voyage) | Swiper 3 visibles | — | Réassurance |
| 4 395–4 879 | Profil voyageur | Segmentation | 3 cartes : FAMILY / GROUP CELEBRATIONS / COUPLES | — | cartes cliquables | Projection |
| 4 927–5 587 | We care about our planet | Valeurs | 2 photos rangers décalées (parallaxe, attribut `parallax` ×1) + texte | parallaxe (hypothèse) | « Read our CSR » | Sens |
| 5 683–6 576 | Popular articles | SEO + inspiration | 12 cartes articles 364×236 (H3 16 px caps + chapô + « Read more ») | Swiper 3 visibles | « All stories » | Expertise |
| 6 576–7 331 | Footer | Contact & preuve | 4 colonnes (Quick links, Pelorus Group, Contact, Sign up), 6 réseaux, 9 badges, mentions IATA | formulaire email | « Submit », « Enquiry Form », « Contact Us » | Sérieux |

**Logique narrative** : promesse (hero) → différence (manifeste + fondateurs) → preuve externe (presse) → **structure de l'offre (terre/mer/air)** → méthode (Why) → désir et actualité (slider campagne / agenda 2026) → preuve client → **porte d'entrée par profil** → valeurs → contenus → contact. L'offre ne devient jamais « concrète » (prix, dates) sur la home : la concrétisation est déléguée à `/experiences` (cartes chiffrées) et aux pages destination. Les 3 + 3 cartes de portes d'entrée tiennent le rôle des « chambres » ; la « réservation » est remplacée par trois ENQUIRE (nav, y = 1 180, footer).

**Enseignements réutilisables** : ordre « promesse → différence → preuve → structure → méthode → désir → preuve client → profil → valeurs » ; garder les chiffres pour les pages de niveau 2 ; slider campagne en position centrale pour la saisonnalité (agenda annuel).

---

## 5. Scroll et storytelling

**Faits observés**
- Libs : Swiper + Alpine.js (preuve) ; **GSAP, ScrollTrigger, Lenis, Locomotive, Webflow, Lottie : absents** (`home-sweep.json`). `animAttrs` : reveal 48, parallax 1, horizontal 4, sticky 0 ; `positionSticky` 1 dans le CSS, `scrollSnap` 9 (Swiper), `willChange` 3.
- Balayage 15 paliers (459 px) : transforms 2 → 2 → 2 → 2 → 2 → **6 → 7 → 14 → 10** → 3 → 2 → 2 → 4 → 4 → 2 ; opacités partielles 2–3 puis **7 → 7 → 9** entre 2 297 et 3 216 px (zone slider campagne + témoignages), puis 2–3. `clipPath` 0, `pinned` [] partout.
- Header : `position: static` dans le conteneur mais `nav` en `fixed` 134 px ; deuxième `div fixed top-0 z-50 hidden` de 84 px (barre compacte) ; sur les pages internes en scroll, seule une pastille ronde hamburger (56 px, fond #c1c1c1 à 80 %, `backdrop` 16 règles) reste visible.
- Transitions CSS mesurées : 2 s (×33), 0,5 s (×28), 0,18 s (×20), 0,15 s (×14) ; easing unique en calcul : cubic-bezier(0.4,0,0.2,1) (×32) ; CSS source : `.4,0,.2,1` ×23, `0,0,.2,1` ×22, `.4,0,.6,1` ×22, plus un ressort `.54,1.5,.38,1.11` ×1. 5 keyframes, 1 règle `prefers-reduced-motion` (no-preference sur `.btn`).
- Alternances : vidéo → texte → logos → 3 photos → icônes → slider → **photo plein écran** (témoignages) → 3 photos → texte + photos → cartes → footer gris ; fond blanc constant, seules ruptures : photos, footer #535353, et sur Svalbard un bloc marine #063657 (456 px) + un overlay plein écran 600 px. Respirations : sections vides de 48–96 px.

**Interprétation**
- Le storytelling est **à défilement classique** : reveals à l'entrée du viewport (translation + fondu 0,5–2 s, hypothèse `translateY` ≈ 20–40 px d'après les transforms comptés), sans pin ni scrub. Le pic de 14 transforms à 3 216 px correspond au Swiper témoignages (3 slides + doublons en boucle) et au slider campagne, pas à une chorégraphie.
- La « parallaxe » (1 attribut) sur « We care » est le seul effet lié à la position de scroll ; non vérifiable en headless, hypothèse translation lente des deux photos.
- Rythme régulier (~500–600 px par bloc, texte 896 px puis grille 1 280) ; la photo plein écran des témoignages (974 px) est le seul temps fort ; sans sticky ni pin, l'envie de poursuivre vient du contenu (2 417 mots), pas du mouvement.
- Fonction de chaque effet : reveal = orienter le regard vers chaque bloc (rythme) ; Swiper = densité de contenu sans allonger la page (12 articles, 5 slides campagne, 6 témoignages) ; overlay noir sur cartes = lisibilité des titres blancs ; parallaxe = marque (valeurs) ; aucune animation n'est au service de l'action (le CTA ne bouge pas, ne colle pas).

**Enseignements réutilisables** : reveals sobres (≤ 0,5 s) + Swiper pour la densité ; une seule section plein écran photo comme respiration ; respirations vides de 48–96 px entre sections ; ne pas compter sur la parallaxe pour la conversion.

---

## 6. Animations et micro-interactions

| Animation | Déclencheur | Élément | Effet (estimation) | Fonction | Risque UX |
|---|---|---|---|---|---|
| Arrivée | chargement | hero | aucun préloader ; poster puis vidéo (non vérifié) | rapidité | LCP lourd (poster + 21 Mo) |
| Reveal sections | entrée viewport | 48 éléments `reveal` | fondu + translation, 0,5–2 s, ease cubic-bezier(.4,0,.2,1) (hypothèse `translateY`) | rythme | texte invisible si JS lent ; 2 s est long |
| Titres / images | idem | H1-H2, cartes | même reveal ; SplitText 0, clip-path 0 | rythme | — |
| Zoom photo au hover | hover | cartes `group … transform` | hypothèse scale léger, non mesuré | marque | — |
| Hover boutons | hover | `.btn` | transition 0,15 s ; **aucune différence calculée relevée** (`{}`) | feedback | feedback quasi nul (hypothèse inversion plein/contour non déclenchée) |
| Hover nav | hover | EXPERIENCES, DESTINATIONS | mega-menu ; `group-hover:w-full` = soulignement animé (preuve CSS) | orientation | 47 liens |
| Carrousels | flèches / autoplay (hypothèse logos) | 4 Swipers home | translation, `scrollSnap` 9 | densité | flèches 48 px sans nom |
| Menu mobile | tap hamburger | overlay (non capturé) | inconnu | navigation | non vérifié |
| Vidéo plein écran | autoplay | hero 1080p loop + slide campagne 720p | `preload="none"` / `metadata` | émotion | 21,4 Mo, même 1080p servie au mobile |
| Parallaxe | scroll | section « We care » (`parallax` ×1) | translation lente (hypothèse) | marque | — |
| Header au scroll | scroll | nav 134 px → pastille 56 px | disparition + bouton flottant (`backdrop-filter`) | espace écran | perte du CTA ENQUIRE (rubrique 7) |
| Feedback formulaire | submit | /enquire | Turnstile + redirection `_redirect` (hypothèse page merci) | conversion | non testé |
| Reduced motion | media query | `.btn` uniquement | 1 règle `no-preference` | a11y | reveals et Swipers non couverts ; `04-reduced-motion` = `01-hero` |
| Ressort | inconnu | easing `.54,1.5,.38,1.11` ×1 | overshoot (hypothèse accordéon) | feedback | — |

**Interprétation** : animation **utilitaire et peu risquée** mais peu signifiante : pas de curseur, pas de transition de page, pas de scroll horizontal réel (les 4 `horizontal` sont des Swipers) ; seuls gestes de marque : soulignement `group-hover:w-full` et pastille à backdrop. L'absence de retour mesurable sur l'unique CTA est un manque.

**Enseignements réutilisables** : Swiper + Alpine suffisent pour un site éditorial ; prévoir une règle `prefers-reduced-motion: reduce` qui neutralise les reveals ; donner un hover mesurable au CTA principal (inversion plein/contour).

---

## 7. Navigation et architecture de l'information

**Faits observés**
- Nav desktop : 6 entrées + ENQUIRE + téléphone + drapeau UK/US + recherche + hamburger. Mega-menus : **Experiences** (7 types, 5 profils, 3 cartes éditoriales), **Destinations** (9 régions + carte Iceland), When to Go (par mois, hypothèse), Business, Stories, About ; 47 liens de nav, 39 en pied de page.
- Fil d'Ariane sur toutes les pages internes (50 px, bordures #ebe9e6) : « Home › Arctic & Antarctica › Luxury Svalbard Holidays ».
- Pages destination : **sous-navigation à 3 onglets** « OVERVIEW · EXPERIENCES · ACCOMMODATION » (72 px, fond #ebe9e6, onglet actif blanc) sous le hero.
- Catalogue `/experiences` : « FILTERS (186 Experiences) », 3 selects (Destinations avec ~70 pays, Type, Price), grille 3×4, pagination « 1 OF 16 ».
- CTA persistant : ENQUIRE dans la nav fixe (y = 21) ; sur les pages internes au scroll, la nav se replie en pastille hamburger (captures `experiences-03-scroll1`, `dining-03-scroll2`) → **le bouton ENQUIRE n'est plus visible**. Sur /enquire, badge Calendly « Schedule a Call » fixe en bas à droite (163×45).
- Mobile : header 84 px, ENQUIRE conservé, hamburger ; menu non capturé (pop-in à la place).
- Étapes vers une offre chiffrée : home → Experiences (1 clic) → carte avec saison + prix (visible sans clic) → page expérience (2 clics) → ENQUIRE (3). Via destination : home → Destinations → région → pays (3 clics) → « Our top experience » avec prix (Svalbard : « Mar-May £20,000 PP 4 Nights ») → Read more.

**Interprétation**
- IA **triple-entrée** (destination / expérience / profil), redondante à dessein : la même expérience est atteignable par Asie, par Family et par le catalogue — excellent pour le SEO (186 fiches, ~70 pays) au prix d'un menu dense. Hiérarchie nav (6) → mega-menu → onglets de page → cartes ; téléphone et marchés dans la barre haute.
- Frustrations : nav de 134 px ; disparition du CTA au scroll sur les pages internes ; page Émirats quasi vide (3 paragraphes, aucune expérience ni hébergement, 2 263 px) alors que la sous-nav promet EXPERIENCES et ACCOMMODATION ; 16 boutons sans nom accessible (flèches, filtres).
- La vraie difficulté n'est pas de trouver une « chambre » mais de comprendre qu'on ne réserve pas : le verbe unique ENQUIRE le dit.

**Enseignements réutilisables** : sous-navigation d'ancrage à 3 onglets sur les pages destination ; cartes catalogue avec saison + prix « pp » lisibles sans clic ; garder le CTA visible dans l'état replié du header ; ne pas publier une page destination sans au moins une expérience chiffrée.

---

## 8. Parcours de réservation et conversion

**Faits observés**
- **Aucun moteur transactionnel** : la sonde CTA sur /antarctica (première et seconde visite) répond « no obvious booking CTA visible » ; aucun input de date (`dateInputs` = cases cookies uniquement), aucun domaine externe de réservation. Le modèle est **demande / devis** : formulaire Statamic `/!/forms/enquiry_form_duplicate_backup` sur /enquire, téléphone, Calendly.
- Premier CTA : ENQUIRE dans la nav fixe (y = 21, 117–144×42 px, orange plein), présent sur les 16 pages auditées. Second : ENQUIRE NOW sous l'intro (home y = 1 180 ; Antarctica y = 1 186 après 4 paragraphes) ; troisième : bloc de fin « NEED HELP PLANNING YOUR LUXURY HOLIDAY IN [PAYS]? » + ENQUIRE NOW (Antarctica y = 5 526 ; Svalbard 4 430 ; Espagne ~2 700). Sur why/testimonials, le bouton final est « ENQUIRE » 213×42 en contour orange.
- Verbes : *Enquire / Enquire now / Submit* (demander) ; *Find out more / Explore / Read more / Discover* (découvrir) ; *Find your adventure / Dive in / Where will curiosity take them?* (campagne). Jamais « Book ».
- Formulaire /enquire (H1 « TRAVEL ENQUIRY FORM » 48 px, docHeight 2 389, formulaire 995 px de haut) : intro « If you would like to speak to a member of our team immediately, call us today: +44 203 848 5424 / +1 800 659 0217 » puis « Complete the form below and we'll contact you, or **click here** to schedule a call » (Calendly). Deux groupes : **Travel plans** — « Where would you like to travel? » (texte, placeholder « Countries, regions, cities, national parks, islands… »), « Tell us about your plans » (textarea, placeholder « Number of people, type of travel and preferred dates »), « What is your total budget for the trip? » (select `budget_uk_gbp`, tranches à partir de « £40,000 ») ; **Contact details** — prénom, nom, téléphone (indicatif +1 par défaut, placeholder « (201) 555-0123 »), email, « Where are you based? » (select pays), « How did you hear about Pelorus? » (select). 8 champs obligatoires (*), case newsletter, Turnstile « Verify you are human », SUBMIT contour orange 200×42. Champs gris #ebe9e6 sans bordure, libellés 12 px sans `<label>` ; badge Calendly « Schedule a Call » fixe (163×45, arrondi).
- Promesse de réponse : « we'll contact you » — **aucun délai** annoncé, **aucun humain nommé** sur /enquire ; les Travel Designers sont nommés ailleurs (why : « Meet the team » ; campagne : Geordie Mackay-Lewis co-fondateur, Laura Watson Travel Designer, Charlie Drinkwater Head of Operations, Michelle Hemmings Sales Manager, avec vidéo par personne).
- /contact (3 549 px) : ENQUIRE NOW, bloc gris « CONTACT DETAILS » (« The best way to speak to our team is to call us »), « BECOME A PARTNER », adresse SW6 avec photo de Londres, 6 cartes réseaux ; pas de formulaire.
- Prix : cartes catalogue « saison • £ pp » (de 20 000 £ à 125 000 £ pp ; « £115,000 » sans pp pour l'expérience privatisée écossaise), filtre Price par tranches (« £20,000 - £25,000 pp », « £25,000 - £30,000 pp », « £30,000… ») sur /experiences, /curious-minds (12 expériences famille) et la campagne (9 expériences). Fiche Svalbard « Top experience » : **Mar-May · £20,000 PP · 4 Nights**. Antarctica : aucune valeur chiffrée (Read more seulement). Inclusions, acomptes, conditions : **absents** de toutes les pages auditées.
- Réassurance : 9 badges, 10 logos presse (home + testimonials), page process en 6 étapes (« It all starts with a phone call » → Research → Proposal « multiple options, each with varying levels of luxury, action, adventure » → Fine-tuning → Pre-departure → « 24/7 support »), page why en 7 raisons (« The Pelorus 'black book' opens doors »), ~20 témoignages signés par type de voyage. Aucun argument « meilleur prix ». Services : yachting (3 yachts par page polaire → pelorusyachting.com), aviation, Pelorus Junior, fondation ; pas de chat.
- Points de rupture : Calendly (domaine tiers, non capturé) ; pelorusyachting.com (nouveau domaine, hypothèse même charte) ; Turnstile ; redirection `_redirect` après envoi (page de remerciement non observée).

**Interprétation**
- Le parcours est **découvrir → se qualifier (prix pp, budget obligatoire) → demander → être rappelé**. Le formulaire est court (3 questions de voyage + identité), formulé en langage naturel et avec placeholders qui guident (« Number of people, type of travel and preferred dates »), ce qui remplace un moteur date/voyageurs par une phrase libre : cohérent avec le sur-mesure.
- Le **budget obligatoire dès 40 000 £** (hypothèse : tranche la plus basse) est une auto-sélection assumée, cohérente avec les prix vitrine.
- La conversion est **sous-humanisée** au moment décisif : pas de portrait ni de prénom sur /enquire, pas de délai de réponse, pas de récapitulatif de la méthode (les 6 étapes vivent sur une autre page). L'alternative téléphone est mise en avant deux fois, ce qui signale que la vente réelle est orale.
- Inclusions et acomptes absents (normal en sur-mesure) mais les prix « pp » sans « from » ni base restent ambigus ; Svalbard fait mieux (prix + durée + saison). Trois widgets tiers (Calendly arrondi, cookies vert, Sleeknote) cassent la charte.

**Enseignements réutilisables** : formulaire de demande en deux blocs (projet / identité) avec placeholders-exemples ; select budget obligatoire ; téléphone bi-marché en tête de formulaire ; ajouter (ce que Pelorus ne fait pas) un portrait de designer nommé + délai de réponse + rappel des étapes sur la page de demande.

---

## 9. Page destination (unité vendue : le voyage)

**Objet vendu** : une expédition privée sur mesure de plusieurs nuits ; la page destination est un **hub éditorial** exposant « top experiences » et « accommodations » comme composants d'un itinéraire à construire, jamais comme produits réservables. Page détaillée **/antarctica** (6 419 px, 2 281 mots) ; comparaison /svalbard (5 323 px), /spain (3 618 px), /united-arab-emirates (2 263 px). Mobile non capturé.

**Faits observés — structure Antarctica (y desktop)**
1. 0–640 : hero demi-écran (1440×640, image 2250×1750 recadrée, hélicoptère jaune en vol au-dessus d'un skieur) + H1 « LUXURY ANTARCTICA HOLIDAYS » 96 px centré sur deux lignes.
2. 640–712 : sous-nav OVERVIEW · EXPERIENCES · ACCOMMODATION (fond #ebe9e6, onglet actif blanc, 72 px).
3. 712–762 : fil d'Ariane Home › Arctic & Antarctica › Luxury Antarctica Holidays.
4. 762–1 276 : eyebrow « ONCE-IN-A-LIFETIME POLAR EXPEDITIONS » + 4 paragraphes 18/28 px centrés (896 px) mentionnant Pelorus Yachting (lien orange), lodges/eco-camps, « pioneers » ; **ENQUIRE NOW plein orange à y = 1 186**.
5. 1 276–1 826 : « OUR TOP EXPERIENCE IN ANTARCTICA » : photo 768×432 à gauche, titre eyebrow 18 px « PIONEERING LUXURY ADVENTURE IN ANTARCTICA », 3 lignes, « Read more » orange. Sans prix ni durée (Svalbard équivalent : « Mar-May · £20,000 PP · 4 Nights »).
6. 1 858–2 400 : « EXPLORE BY LAND » : slider texte + image 656×369 de 4 activités H3 MFred 30 px (kayak, héli-ski, submersible, faune + science), liens « Enquire Now » / « Find out more » **vers /enquire**, barre de progression orange.
7. 2 400–2 812 : « CONSERVATION AT THE CORE » (IAATO, Dr Mercedes Santos, biologiste).
8. 2 812–3 351 : « ANTARCTICA LUXURY CAMPS » : slider 2 camps (Whichaway « cream domes », Echo), 4–5 lignes de paysage, « Explore » ; ni capacité, ni équipement, ni prix.
9. 3 383–4 750 : bloc marine **#063657** « WHY CHARTER A YACHT IN ANTARCTICA? » + « WHO IS PELORUS YACHTING? », puis 3 cartes de yachts (La Datcha, Octopus, Sherakhan) → pelorusyachting.com.
10. 4 750–5 190 : FAQ accordéon 5 questions (période, vol, hôtels, environnement, faune), balisées H2 16 px.
11. 5 190–5 664 : « NEED HELP PLANNING YOUR LUXURY HOLIDAY IN **ANTARCTICA**? » 48 px (pays en orange) + ENQUIRE NOW.
- CTA vers /enquire : 7 sur la page (nav, y = 1 186, 4 liens de slider, y = 5 526) + footer. `horizontal` 6 (six Swipers), `reveal` 39, `ariaHidden` 11 (slides dupliquées).
- Saison : FAQ et cartes catalogue seulement ; pas de calendrier, de carte ni de « jour 1 / jour 2 ». Svalbard : mêmes blocs avec top experience chiffrée, 1 camp, overlay Norvège 600 px. Espagne : slider 3 expériences (« Dec-Mar £26,000 PP 4 Guests ») + 2 hébergements, sans yachting. Émirats : intro seule + CTA (coquille). Index /destinations (4 079 px) : grille 9 cartes photo (959×480 et 477×480) + « START PLANNING YOUR EXPERIENCE ».

**Interprétation**
- La page vend **l'accès et la méthode**, pas un produit : chiffres rares, aucune date ni inclusion ; ordre cohérent pour une agence (intro SEO → expérience phare → activités → conservation → hébergement → yachting → FAQ → demande).
- Projection par les titres en verbe (« Plunge to the underwater world in a submersible ») et les camps décrits par le paysage ; réassurance par IAATO, scientifique et yachts nommés.
- Manques : pas de prix sur la page polaire phare, pas de saison synthétique, pas de carte ni d'itinéraire jour par jour, hébergements sans capacité, « Enquire now » sans pré-remplissage (aucun paramètre d'URL observé). Mobile non vérifié (extrapolation : ~9 000–10 000 px, 7 CTA).

**Enseignements réutilisables** : sous-nav Overview/Experiences/Accommodation ; « top experience » chiffrée (saison · prix pp · nuits) en première section ; slider d'activités avec barre de progression ; FAQ accordéon SEO en fin de page ; H2 final personnalisé au pays avant le CTA. À ajouter sur un nouveau projet : carte, calendrier saisonnier, itinéraire type, pré-remplissage du formulaire.

---

## 10. Copywriting

**Faits observés**
- Volume : 1 568 (Émirats) à 2 792 mots (Curious Minds) par page ; 2 417 sur la home.
- Titres : capitales systématiques, structure « LUXURY [PAYS] HOLIDAYS » (H1 SEO) ; H2 eyebrow en question ou en promesse : « WHY CHARTER A YACHT IN SVALBARD? », « NEED HELP PLANNING YOUR LUXURY HOLIDAY IN SVALBARD? » (le nom du pays en orange dans le H2 final, 48 px).
- Manifeste : phrases binaires « In a world full of X, Pelorus thinks differently » ; répétée mot pour mot sur la page Espagne (« Hyper-personalised… »).
- Vocabulaire : *bespoke, hyper-personalised, private, remote, off-limits, untouched, expedition, unlock, access, precision, perspective* ; registre militaire (« military-grade », « mission awaits », « Assignment ») mêlé à celui de la curiosité (« Five minds. Five ways of seeing. »).
- Sensoriel et précis : « 81 degrees north », « BBQ overlooking the pack ice », « glide across the glacial landscape in silent search of the king of the Arctic », « driveway … fields studded with almond trees ».
- Cartes catalogue : titres de type **mission** (« Step inside a real-life Traitors experience in a Scottish castle », « Tackle the UK's three peaks », « Go beyond the 4×4 safari in Botswana ») + ligne factuelle « APR-OCT • £115,000 ».
- Témoignages : citations en serif italique 20 px, signature = **type de voyage** (« Group trip to the Maldives », « Couples trip to Bhutan », « Indonesia, Charter Guest ») plutôt que nom de personne.
- CTA : ENQUIRE / ENQUIRE NOW / SUBMIT, « Find your adventure », « Dive in », « Explore », « Read more ». Caractéristiques techniques (saison, prix pp, nuits) sur une ligne en 11–14 px, jamais dans les paragraphes.

**Interprétation**
- Mécanisme central : **titre-mission + ligne de faits** : le désir est dans le verbe d'action (tackle, step inside, go beyond), la crédibilité dans la ligne chiffrée. C'est l'inverse du quiet luxury (pas de chiffres).
- Deuxième mécanisme : **question adressée au lecteur en H2** avant chaque CTA (« Need help planning…? »), avec le nom du pays coloré = personnalisation perçue à coût nul.
- Troisième : la preuve se présente par le **profil du voyage** dans la signature du témoignage, ce qui sert la segmentation famille/couple/groupe.
- Le luxe se dit par l'accès (« as far north as is humanly possible ») et l'expertise, jamais par le confort ; les hébergements sont décrits par le paysage, sans équipements.
- Limites : « luxury » 2–3 fois par title, manifeste répété, coquilles (« Journey's », « shear amount »).

**Enseignements réutilisables** : titres en verbe d'action + ligne « saison • prix • durée » ; H2 interrogatif localisé avant le CTA ; signer les témoignages par le type de voyage ; réserver le mot « luxury » aux balises.

---

## 11. Photographie et vidéo

**Faits observés**
- Types de plans : aériens, machines en action (hélicoptère sur yacht, buggies, motos), animaux à courte distance (ours polaire depuis un zodiac, raie manta), groupes de dos face au paysage, rangers avec faune, enfants pieds nus, dîners aux flambeaux. Ratio lieu/expérience estimé **30/70**.
- Lumière : golden hour (désert, Inde), lumière polaire plate (Svalbard), nuit (lanternes, aurores). Couleurs naturelles saturées, pas de filtre unifié.
- Hero internes : Svalbard = montage navire + ours (1536×760) ; Espagne = Alhambra à travers une arche ; about = hélicoptère jaune dans la neige.
- Vidéos : hero 1080p Vimeo (21,4 Mo, loop, poster), slide campagne 720p (1,8 Mo, sans poster), about : vidéo fondateurs **61,3 Mo** avec `controls` ; campagne : 6 vidéos, Curious Minds : 5. Aucune image de chambre ; hébergements vus de l'extérieur.

**Interprétation** : la photographie vend le **faire** et l'**échelle** ; humains anonymes de dos = projection ; zéro intérieur/lit, cohérent avec l'objet vendu. Vidéo immersive au hero, documentaire sur l'about (contrôles = visionnage volontaire).

**Shot list pour reproduire ce niveau (voyage sur mesure)**
1. Plan aérien large avec un véhicule/bateau minuscule (échelle).
2. Véhicule en action de face avec poussière/embruns (hero).
3. Faune à courte distance depuis un point de vue passager (zodiac, 4×4).
4. Groupe de 3–5 personnes de dos face à un panorama, golden hour.
5. Portrait de guide/ranger local avec un animal ou un outil (valeurs).
6. Enfant en pleine action (famille).
7. Table de dîner en extérieur de nuit (célébrations).
8. Hébergement vu de loin dans son paysage (camp, hacienda), jamais l'intérieur seul.
9. Une vidéo hero 15–30 s muette (≤ 8 Mo, avec poster) et une vidéo équipe avec contrôles ; portraits et mosaïque pour les campagnes.

---

## 12. Mobile (390×844, DPR 2)

**Faits observés**
- Header 84 px : logo gauche, ENQUIRE orange 117×41 px CSS, hamburger 24×35 px (cible sous 44 px en hauteur pour le hamburger). Vidéo hero 390×844 (ratio 0,46) avec poster desktop 1920×1080 recadré.
- Hauteur 10 898 px ; sections : hero 844, intro 506, logos 191, grille expertise **1 578 px (3 cartes empilées de 480 px)**, Why 1 174 (4 pastilles empilées), campagne 538, témoignages 1 076, profils 1 460, planet 940, articles 893.
- Titres : H2 72 → 36 px, cartes 48 px conservés (« GROUP CELEBRATIONS » sur deux lignes), H1 30 px, eyebrow 18 px inchangé (7,2 px d'interlettrage sur 358 px = retours à la ligne) ; paragraphes 16/24 px.
- Boutons : ENQUIRE NOW 264×42, « Where will curiosity take them? » 358×58 (pleine largeur), flèches 48 px.
- Animations conservées (`reveal` 48, `horizontal` 4, transforms 4–6 vers 4 000–5 000 px). Pop-in Sleeknote **plein écran** (titre 28 px, radio « travel agent », email, SUBSCRIBE) par-dessus la modale cookies → deux couches à fermer.
- Perf mobile : 183 requêtes, **60,7 Mo** (dont 23,2 Mo média : la vidéo 1080p desktop est servie au mobile, 21,4 Mo), 33 Mo d'images (0 `srcset`, image 5,7 Mo chargée). TTFB 600 ms, FCP 1 096 ms, load 7,2 s.
- 48 éléments < 12 px ; formulaire /enquire non capturé en mobile (hypothèse champs pleine largeur d'après `w-full … sm:w-auto` sur SUBMIT).

**Interprétation** : empilement fidèle du desktop (grilles 3 → 1, display réduit de moitié) sans réécriture : la grille d'expertise occupe deux écrans. Lisibilité bonne (16/24 px) mais poids (60 Mo, vidéo desktop) et double interruption dégradent l'entrée ; ENQUIRE reste dans le header.

**Enseignements réutilisables** : servir une rendition vidéo mobile (≤ 3 Mo, 720p) ou l'image seule ; passer les grilles 3 cartes en carrousel horizontal sur mobile ; interdire les pop-ins plein écran avant le premier scroll ; ajuster l'interlettrage des eyebrows sous 400 px.

---

## 13. Performance, accessibilité, SEO

**Faits observés**
- Temps (desktop) : TTFB 412 ms (curious) à **2 885 ms (Espagne)**, 769 ms home ; FCP 0,9–3,7 s ; load 3,2–15 s ; LCP non mesuré.
- Poids : home **120,9 Mo** / 339 requêtes (images 66,5 Mo sur 180, vidéos 46,5 Mo demandées deux fois), pages destination 46–54 Mo, about **176 Mo** (vidéo 61 Mo ×2), campagne 352 Mo. Scripts 57–71 fichiers / 5 Mo (Pardot, Clarity, GTM, Sleeknote, Turnstile, VWO, Facebook, Google Ads) ; polices 674 Ko.
- Images : 86 sur la home, `lazy` 1, `srcset` 0, 18 alt vides, alts longs orientés SEO ailleurs ; PNG de 5,7 Mo (pop-in Sleeknote) chargé sur toutes les pages.
- Contrastes estimés : blanc/orange #f38b00 (boutons 12 px) et orange/blanc (liens, prix) ≈ **2,5:1 (échec AA)** ; #6f6f6f/blanc ≈ 5,0:1 ; noir/#ebe9e6 ≈ 17:1 ; blanc/#063657 ≈ 12:1.
- Clavier/a11y : `outline: none` **200**, skip link absent, landmarks présents, 16 boutons et 8 liens sans nom, 2 iframes sans titre, 10 inputs sans `<label>` ; reduced motion : 1 règle, vidéos toujours `autoplay`.
- Structure : h1count **3** sur home et Espagne (noms d'hôtels balisés H1), 0 sur Curious Minds, 1 ailleurs. Métadonnées : title/description/og sur chaque page, canonical exact, **hreflang x-default / en-GB / en-US**, JSON-LD Organization + TravelAgency, pas d'og:image détecté.
- Contenu indexable : 1 515–2 792 mots par page, 186 fiches, ~70 pays, 12 articles en home.

**Interprétation** : équilibre immersion/performance **défavorable** (120 Mo, aucune image responsive, 10 fournisseurs de tracking, vidéo 1080p au mobile) ; SEO technique soigné ; accessibilité moyenne-faible (orange 2,5:1, focus supprimé, 16 contrôles muets).

**Enseignements réutilisables** : garder le socle SEO (hreflang bi-marché, JSON-LD TravelAgency, titles datés « 2026/2027 ») ; corriger avant copie : `srcset` + WebP, vidéo mobile dédiée, pop-in sans PNG de 5,7 Mo, foncer l'orange (ex. #c96f00 ≈ 4,5:1) pour les textes 12 px, un seul H1.

---

## 14. Conclusion

### 15 meilleurs éléments
1. Triple porte d'entrée destination / expérience / profil, redondante dans le mega-menu, la home et le catalogue.
2. Cartes catalogue « titre-mission + saison • prix pp » lisibles sans clic (186 expériences, filtre Price).
3. Verbe unique ENQUIRE, orange #f38b00, fixe dans la nav de 16/16 pages, jamais « Book ».
4. Architecture Land / Sea / Air + Foundation, répétée en grille sur home, about, why.
5. Page process en 6 étapes numérotées avec sommaire et visuel par étape.
6. Page why en 7 raisons numérotées, ponctuée par presse puis clients.
7. Sous-navigation Overview / Experiences / Accommodation sur les pages destination.
8. H2 final « Need help planning your luxury holiday in [PAYS]? » avec le pays en orange avant chaque CTA.
9. Formulaire de demande court en langage naturel avec placeholders-exemples et budget obligatoire.
10. Campagne « What does adventure mean to you? » : 4 collaborateurs nommés avec vidéo et citation sur fonds illustrés.
11. « Curious Minds » : 5 archétypes d'enfant sur fond kraft #efeae4, script CupCakes, formulaire dédié.
12. Témoignages signés par type de voyage (« Group trip to the Maldives ») = preuve segmentée.
13. Bloc yachting marine #063657 + cartes de yachts nommés sur les pages polaires (cross-sell interne au groupe).
14. Socle SEO : titles datés, hreflang en-GB/en-US, JSON-LD TravelAgency, FAQ accordéon, 1 500–2 800 mots par page.
15. Preuve par badges sectoriels (IAATO, AECO, IATA, B Corp…) et 10 logos presse.

### 5 faiblesses / limites
1. Deux interruptions superposées (modale cookies bloquante + Sleeknote plein écran mobile / 25 % desktop) avant tout contenu.
2. Poids : 120,9 Mo (home desktop), 60,7 Mo (home mobile avec vidéo 1080p desktop), 176 Mo (about), 352 Mo (campagne, 24 médias) ; 0 `srcset`, PNG de 5,7 Mo chargé sur toutes les pages.
3. Accessibilité : orange à ≈ 2,5:1 pour boutons 12 px, prix et liens ; 200 `outline: none` ; 16 boutons sans nom ; 3 H1 sur home et Espagne.
4. Conversion sous-humanisée : /enquire sans portrait, sans délai de réponse ; CTA ENQUIRE disparaît au scroll sur les pages internes (pastille hamburger seule).
5. Inégalité des pages destination (Antarctica 6 419 px riche vs Émirats 2 263 px vide) et prix absents sur la page polaire phare.

### 10 principes réutilisables
1. Vendre le voyage par trois entrées (où / quoi / qui) et jamais par la chambre.
2. Afficher saison + prix pp + durée sur chaque unité dès la carte.
3. Un seul accent saturé réservé à l'action ; le reste en noir/blanc/sable.
4. Display condensé capitales 96–128 px pour les H1, eyebrow 18 px interlettré 40 % pour les sections, serif 16–18 px pour le récit.
5. Ordonner la home : promesse → différence → preuve → structure → méthode → désir → clients → profils → valeurs.
6. Page méthode numérotée (6 étapes) + page « pourquoi nous » numérotée (7 raisons) : deux pages de réassurance distinctes.
7. Formulaire de demande = 3 questions de projet + identité + budget obligatoire ; téléphone bi-marché au-dessus.
8. Sous-nav d'ancrage à 3 onglets et FAQ accordéon sur chaque page destination.
9. Témoignages signés par type de voyage plutôt que par nom.
10. Campagnes éditoriales incarnées (équipe nommée, vidéo, illustrations) comme contenu de milieu de home.

### Éléments propres à la marque à ne PAS copier
- Le récit « deux anciens capitaines de l'armée britannique » et le lexique militaire (mission, assignment, military-grade).
- La police MFred et le logo-boussole ; le script CupCakes de Curious Minds.
- L'orange #f38b00 comme signature (et son contraste insuffisant).
- Les archétypes d'enfants adossés à David Attenborough et la citation en ouverture de /curious-minds.
- Les noms de yachts, camps et partenaires (Whichaway, La Datcha, Octopus) et les badges IAATO/AECO propres au polaire.

### Notes /10
| Axe | Note | Justification (faits) |
|---|---|---|
| Branding | **8/10** | Architecture Land/Sea/Air + Foundation lisible sur 4 pages ; manifeste « without limits or templates » repris mot pour mot sur home/Espagne/process ; 9 badges + 10 logos presse ; campagnes incarnées (4 employés nommés, 5 archétypes). Retiré : « luxury » martelé dans tous les titles, coquilles dans le DOM. |
| Direction artistique | **7/10** | Système typographique net (MFred 96–128 px / Montserrat eyebrow 40 % / Berlingske 16–18 px), r = 0 partout, un accent ; blocs marine et sable qui rythment ; illustrations sur les campagnes. Retiré : 98 occurrences de 11–12 px, widgets tiers hors charte (vert cookies, Calendly arrondi), photos sans `srcset`. |
| Animations | **5/10** | Swiper + Alpine seulement, 36–48 reveals par page, easing unique cubic-bezier(.4,0,.2,1), pas de pin ni de scrub ; hover boutons non mesurable ; 1 règle reduced-motion sur `.btn`. Sobre mais sans signature ; le bouton flottant à backdrop est le seul geste. |
| UX | **6/10** | Triple entrée, sous-nav destination, fil d'Ariane, 186 fiches filtrables, FAQ. Retiré : nav 134 px, CTA perdu au scroll interne, 16 contrôles sans nom, 200 outlines supprimés, pop-in plein écran mobile, page Émirats vide. |
| Conversion | **6/10** | ENQUIRE persistant 16/16 pages, 7 CTA sur une page destination, formulaire court + budget + téléphone + Calendly, prix pp vitrine qui qualifient. Retiré : aucun humain ni délai sur /enquire, pas de pré-remplissage, prix absents sur Antarctica, contraste 2,5:1 du bouton. |
| Mobile | **5/10** | Header 84 px avec ENQUIRE conservé, texte 16/24 px lisible, grilles empilées propres. Retiré : 60,7 Mo dont vidéo 1080p desktop, 10 898 px de long (grille expertise 1 578 px), pop-in Sleeknote plein écran + cookies, hamburger 24×35 px, menu non vérifié. |

**Note globale : 6,5/10.** Référence pour la **structure de vente d'un voyage sur mesure** (entrées multiples, prix vitrine, méthode et raisons numérotées, campagnes incarnées) et pour le socle SEO ; pénalisé par une exécution lourde (120 Mo, pas de `srcset`, dix trackers), une accessibilité faible et une page de demande qui n'exploite pas l'humain. UX et mobile plafonnent tant que la double interruption cookies + newsletter subsiste.

### Ce que ce site apporte que les sites « quiet luxury » (FORESTIS, Seagate, Le Collectionist) n'apportent pas
- **Prix et saison en vitrine** sur des cartes (20 000–125 000 £ pp), filtre par tranche de budget, budget obligatoire au formulaire : l'auto-qualification remplace le silence tarifaire.
- **Découverte par intention** (type d'expérience, profil du voyageur, mois « When to go ») en plus de la géographie ; les quiet luxury n'ont qu'un lieu et des chambres.
- **Méthode explicitée** (6 étapes numérotées, « it all starts with a phone call », 24/7) et **7 raisons numérotées** : la réassurance est argumentée, pas suggérée.
- **Narration d'expédition** : yachts nommés dans la glace, hélicoptères, submersible, science embarquée (IAATO, biologiste nommée), FAQ pratique ; l'aventure est le produit.
- **Rythme et couleur** : orange saturé, capitales condensées géantes, bloc marine, kraft et illustrations de campagne, cartes photo assombries en grille ; la tension typographique remplace le beige.
- **Communauté et transmission** : campagnes avec employés nommés en vidéo, archétypes d'enfants, Pelorus Junior, fondation, B Corp, newsletter qui segmente les agents de voyages.
- **Écosystème de marques** (Travel / Yachting / Aviation / Foundation) avec cross-sell interne sur les pages destination.

---

## Observations clés à conserver pour la phase comparative

- Objet vendu : voyage sur mesure ; **0 moteur**, 1 formulaire (10 champs, 8 obligatoires, budget dès 40 000 £), 2 téléphones UK/US, Calendly ; sonde « no obvious booking CTA ».
- ENQUIRE orange #f38b00, 117–144×42 px, r = 0, présent en nav fixe sur 16/16 pages ; 7 CTA vers /enquire sur /antarctica ; disparaît au scroll interne (pastille hamburger 56 px).
- 186 expériences filtrables (Destinations ~70 pays / Type / Price), cartes « saison • £ pp » de 20 000 à 125 000 £ ; Svalbard « Mar-May · £20,000 PP · 4 Nights » ; Antarctica sans prix.
- Typo : MFred H1 96 px (128 px about/process), interlettrage 10 % ; eyebrow Montserrat 18 px 600 tracking 7,2 px ; Berlingske 16/24 et 18/28 ; 98 éléments en 11–12 px sur la home.
- Palette : #ffffff, #f5f5f5, #ebe9e6, #535353, #191919, #063657, accent #f38b00 (≈ 2,5:1 sur blanc) ; cookies vert #6aa84f hors charte.
- Header 134 px desktop (84 + 50), 84 px mobile ; conteneur 1 280 px, texte 896 px ; grilles 477×480 (0,99), articles 364×236 (1,54), hero interne 1440×640 (2,25).
- Home 7 331 px / 11 sections / 2 417 mots ; mobile 10 898 px ; 4 Swipers ; 48 reveals, 1 parallax, 0 sticky, GSAP/Lenis absents ; easing cubic-bezier(.4,0,.2,1), durées 0,15 s / 0,5 s / 2 s.
- Poids : home 120,9 Mo / 339 req (vidéo 21,4 Mo ×2, images 66,5 Mo, 0 srcset) ; mobile 60,7 Mo ; about 176 Mo (vidéo 61 Mo ×2) ; campagne 352,5 Mo (24 médias) ; curious 290 Mo.
- Perf : TTFB 0,6–2,9 s, FCP 0,9–3,7 s, load 3,2–15 s ; 57–71 scripts (Pardot, Clarity, GTM, Sleeknote, VWO, FB, Google Ads, Turnstile).
- A11y : `outline:none` 200, 16 boutons sans nom, 8 liens sans nom, skip link absent, 1 règle reduced-motion, h1count 3 (home, Espagne).
- SEO : titles « Luxury [X] Holidays 2026/2027 », hreflang x-default/en-GB/en-US, JSON-LD Organization + TravelAgency, canonical exact, FAQ accordéon, 1 515–2 792 mots/page.
- Interruptions : modale cookies 800×235 (z 999 997) jamais fermée + pop-in Sleeknote (« Are you a travel agent? ») dès ~2 300 px desktop, plein écran mobile ; la capture « menu-open » mobile est la pop-in.
- Pages de réassurance dédiées : process (6 étapes, 6 151 px), why (7 raisons, 7 852 px), testimonials (6 854 px, ~10 citations signées par type de voyage), contact (adresse SW6, 6 cartes réseaux).
- Campagnes : « What does adventure mean to you? » (4 employés nommés, 6 vidéos, 9 expériences) ; « Curious Minds » (5 archétypes, 5 vidéos 342×410, formulaire enfant, 12 expériences famille, 16 034 px).
- Architecture de marque : Travel / Yachting / Aviation (+ Foundation, Group) ; cross-sell 3 yachts nommés par page polaire vers pelorusyachting.com.
