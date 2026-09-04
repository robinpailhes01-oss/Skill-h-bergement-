# Fiche d'audit — FORESTIS Dolomites

Clé : `forestis` · Analyse du 2026-09-04 · Chromium headless via Playwright, 1440×900 (desktop) et 390×844 DPR 2 (mobile).

---

## 0. En-tête

**Nom** : FORESTIS Dolomites (Palmschoß 22, 39042 Brixen, Tyrol du Sud, Italie). **URL de départ** : https://www.forestis.it/en/. Positionnement affiché : « Boutique Wellness Hotel », adultes uniquement dès 14 ans, Small Luxury Hotels of the World, clé Michelin 2024.

### Pages étudiées

| Label | URL | Desktop | Mobile |
|---|---|---|---|
| home | https://www.forestis.it/en/ | oui | oui |
| rooms (= page « Request », formulaire de demande) | https://www.forestis.it/en/luxury-boutique-hotel-dolomites-suite/forestis-dolomites-spa-hotel-bookings/ | oui | non |
| suites (liste des hébergements) | https://www.forestis.it/en/luxury-boutique-hotel-dolomites-suite/ | oui | oui |
| suite-detail (Tower Suite) | https://www.forestis.it/en/luxury-boutique-hotel-dolomites-suite/tower-suite/ | oui | oui |
| hideaway (lieu, hôtes, histoire) | https://www.forestis.it/en/hideaway/ | oui | non |
| villa | https://www.forestis.it/en/villa/ | oui | oui |
| spa | https://www.forestis.it/en/luxury-spa-dolomites/ | oui | non |
| dining | https://www.forestis.it/en/restaurant-forestis-dolomites/ | oui | non |
| experiences | https://www.forestis.it/en/things-to-do-in-the-dolomites/ | oui | non |
| contact | https://www.forestis.it/en/corporate/contact-arrival/ | oui | non |
| engine (SynXis, moteur externe) | https://be.synxis.com/?chain=22402&hotel=30944&locale=en-US | oui (entrée + étape Checkout atteinte par le clic de sonde, rien saisi ni validé) | non |
| booking (seconde visite de la home) | https://www.forestis.it/en/ | oui | non |
| room-detail | URL mal formée (`…/[`) → 404 | non exploitable | — |

### Limites de l'observation

- Aucune balise `<video>` sur les 12 pages auditées (`VIDEOS []`, `videosNet []`) alors que `video.js 7` (472 Ko) et `dash.js` (227 Ko) sont chargés. **Hypothèse** : vidéos en galerie ou en pop-in, non auditées ; en headless elles ne se rendraient de toute façon pas.
- Les captures pleine page desktop (`home-02-full`, `villa-02-full`) montrent des zones vides de 1 000 à 1 500 px là où le DOM contient du texte (« Forest Cuisine », « Your hosts ») ; ces blocs apparaissent sur les captures mobiles. **Hypothèse** : révélation à l'entrée du viewport (`jquery.viewportchecker` chargé) non déclenchée par la capture. Le flux Instagram « #forestisdolomites » ne s'est pas rendu (home : 8 427 px à la première visite, 6 887 px à la seconde).
- Comportement de la barre supérieure au scroll contradictoire entre captures (rubrique 6).
- Non mesurables : transitions de page, curseur tactile, LCP (`null`), Lighthouse, rendu mobile de SynXis.

---

## 1. Positionnement de marque

**Faits observés**
- Title home : « Forestis Dolomites | Boutique Wellness Hotel in Brixen » ; description : « …offers a spa, yoga and wellness packages ».
- H1 hero « The art of simplicity » ; second H1 « Peace as a new luxury » ; H2 « Villa », « A regenerating flow », « Forest Cuisine », « Follow the inspiration #forestisdolomites ».
- Menu (9 entrées) : Hideaway · Suites · Villa · Spa · YERA · Forest Cuisine · Experiences · Voucher · Gallery — le lieu et les hôtes avant les chambres.
- Citation des hôtes en 30 px sur la home (quatre éléments naturels + architecture), signée « Hosts — Teresa & Stefan ».
- Experiences : « Our four elements » (Water / Air / Sun / Climate) puis « The perfect day » par saison. Spa : « wisdom of the Celts », « Wyda Room », « Silence Rooms ». Hideaway : sanatorium de 1912, Otto Wagner, 1 800 m.
- Badges en pied de toutes les pages : 14+, Small Luxury Hotels, Odles Lodge, Michelin 2024, YERA.
- Villa : « can only be booked exclusively », « starting from € 25,000 a night », 2 nuits minimum, concierge + majordome + chef (recadrage de `villa-mobile-02-full` vérifié). Moteur : Room 35 m² à 1 300 €/nuit B&B, 1 425 € en demi-pension.

**Interprétation**
- Refuge de bien-être en altitude, adultes uniquement, où l'on vend le silence, le temps et la nature — pas la chambre. Gamme ultra-luxe (1 300 € la plus petite catégorie) jamais énoncée : aucun prix sur les pages de marque, « luxury » réservé aux balises SEO.
- Cible : couples aisés internationaux (EN/DE/IT, « Mr./Ms. », 2 personnes par défaut dans toutes les catégories), sensibles au design minimal et à la santé.
- Territoire émotionnel : contemplatif, tellurique (écorce, roche, eau, fossile, herbier). Personnalité discrète, presque monacale. Valeurs lisibles sans être nommées : nature, lenteur, privauté, artisanat, ancrage historique.
- Différence avec un site hôtelier générique : navigation qui commence par le lieu, zéro bouton coloré, zéro promotion, zéro étoile ; hébergements décrits en une phrase et trois chiffres.
- Le site vend une expérience : 4 des 5 blocs de la home parlent nature/spa/cuisine/villa ; le seul bloc « suites » parle de la vue, pas du lit.
- Cohérence offre/mots/images/interactions très élevée ; la rupture se situe au moteur SynXis (rubrique 8).

**Enseignements réutilisables** : placer lieu et hôtes avant les chambres quand on vend un refuge ; formuler la promesse en opposition (« Peace as a new luxury ») plutôt qu'en superlatif ; réserver les prix au moteur et à la villa.

---

## 2. Première impression (5 premières secondes)

**Faits observés**
- `home-00-initial` : bannière Cookiebot en bas (≈ 310 px, fond #f2f1eb, boutons Allow all / Allow selection / Deny) sur une image plein écran de crêtes au crépuscule. Pas de préloader.
- `home-01-hero` : image 1920×1080 en `cover` (affichée 1512×945, y=-22, légèrement surdimensionnée), H1 40 px blanc centré (y≈450), logotype centré (le « T » est une flèche/sapin), « Menu » à x=75, « Request » 71×27 px et « Book » 44×27 px à droite, « Scroll ˅ » à y≈843.
- Aucun `<button>` sur le site : tous les CTA sont du texte 20 px sans fond ni bordure. Aucune vidéo, pop-up ou erreur. Panneau menu hors écran (y=-224).
- Mobile : image recadrée 585×1022 (ratio 0,57), H1 30 px, « Menu » + « Book » seulement (« Request » disparaît), barre fixe inférieure 50 px (téléphone, mail, localisation) qui masque le titre « Peace as a new luxury » au chargement.
- TTFB 545 ms / FCP 1 228 ms desktop ; 627 / 1 124 ms mobile.

**Interprétation**
- On voit un paysage, un slogan, un logo ; on comprend « montagne, minimal, cher » ; on ressent le calme et une certaine froideur (aucun humain, aucun intérieur au premier écran).
- Le message est purement attitudinal : ni où, ni quoi. « Dolomites » n'apparaît qu'au scroll.
- Premier CTA « Book » à 44×27 px, non différencié du « Request » voisin : deux verbes sans hiérarchie.
- Distraction : la bannière cookies couvre 34 % du viewport et cache l'indicateur Scroll. Raison de continuer : la curiosité, le hero n'explique rien.

**Enseignements réutilisables** : un hero « attitude » exige un logo très identifiable et accepte de perdre ceux qui cherchent « où / combien » ; hiérarchiser deux CTA texte voisins (soulignement, poids) ; ne rien placer d'essentiel à moins de 300 px du bas du hero.

---

## 3. Direction artistique

**Faits observés**
- Fonds : `#f2f1eb` (1 245 éléments), `#000000` (130, conteneurs d'images), une bande gris moyen sur Spa (« Retreats ») et Dining (chef) dont le hex n'est pas capté — seule variable grise déclarée : `--psk-gallery-bg:#70716c` (**hypothèse** : même valeur). Moteur : `#f2f1eb` + `#e6e4da`.
- Textes : `#333333` (166), `#ffffff` (9, hero et bandes), `#999999` (placeholders), `#808080` (mobile).
- Typographie : une seule famille chargée, **BrandonTextLight** 400 (`Brandon-Text-Web-Light.woff`, MyFonts), 46 éléments ; trois `@font-face` déclarés mais un seul utilisé ; SynXis bascule sur BrandonGrotesqueWeb-Light.
- Échelle desktop : H1 40/56 px (interlettrage 1,5 px), H2 30/42 (1 px), H3 26/36,4 (0,75 px), citation 30/42, corps 20/32, menu/CTA 20. Casse : aucune capitale forcée hors logotype. Mobile : H1 30,06/42,08 (interlettrage normal), H2 21,96/30,74, corps 18/28,8.
- Grille : paragraphes centrés 713 px ; conteneur 864 px ; images pleine largeur 1080 px (marges 180) ; mosaïques 2×530 px, gouttière 20 ; mosaïque 3 : 713 + 2×346. Mobile : 330 px, colonnes 162.
- Ratios (`largeImages`) : hero 1,6 (1920×1080) ; 1,78 (1440×810) ; 1,57 (slider suite 1440×918) ; 1,33 (706×530) ; 0,8 (706×883) ; 0,62 (706×1130) ; 1:1 (951, 461) ; cartes Experiences 1,66 et 1,33 ; mobile 0,57 et 1,77 (495×279). Toutes en `format=webp` avec `width/height` en query string, 0 `srcset`.
- Composants : rayon 0 partout ; champs 1 px de bordure rectangulaires ; liens CTA soulignés ; aucune icône dans le contenu hors footer (4 réseaux) et barre mobile (3 pictos filaires) ; pas d'illustration, de dégradé, de texture ; liseré 1 px sous header et sous-nav.
- Espacements ≈ 200 px entre bloc image et titre suivant, ≈ 100 px entre paragraphe et image. Header 150 px desktop (logo à y≈93), 100 px mobile. Tout est centré ; seules les mosaïques sont asymétriques.
- Photos : lumière rasante (aube/crépuscule), tons brun-ocre-gris désaturés, forte part de gros plans de matières, bois sombre, une silhouette humaine sur la home.

### Tokens approximatifs

| Token | Valeur |
|---|---|
| `--bg` / `--bg-alt` / `--bg-engine-alt` | #f2f1eb / ≈ #70716c (hyp.) / #e6e4da |
| `--text` / `--text-inverse` / `--text-muted` | #333333 / #ffffff / #999999 |
| `--border` | ≈ #d9d7cf, 1 px (estimé) |
| `--font` | BrandonTextLight 400 (moteur : BrandonGrotesqueWeb-Light) |
| `--h1` / `--h2` / `--h3` / `--body` | 40/56 · 30/42 · 26/36,4 · 20/32 px (mobile 30 · 22 · 22 · 18) |
| `--measure` / `--content-max` / `--gutter` | 713 px (mobile 330) / 1080 px images, 864 px conteneur / 20 px |
| `--radius` | 0 |
| `--header-h` / `--menu-panel-h` | 150 px (mobile 100) / 219–224 px (mobile plein écran) |
| `--cta` | texte 20 px souligné, 71×27 et 44×27 px |
| `--transition` / easings | 0,25 s · 0,4 s · 0,5 s / cubic-bezier(.645,.045,.355,1), cubic-bezier(.23,1,.32,1) |

**Interprétation** : trois décisions radicales — une couleur de fond, une police en une graisse, zéro bouton — tenues sans dérive de la home au contact. La hiérarchie ne tient que par la taille et l'espace ; le vide est le matériau principal, les images les seuls pleins. Faiblesse : les CTA en Light 20 px sur crème sont peu saillants et ne tiennent que par le soulignement.

**Enseignements réutilisables** : deux valeurs + une police Light suffisent si les photos apportent couleur et profondeur ; standardiser 5 ratios d'images et les combiner en mosaïques 2/3 ; rayon 0 + soulignement comme signature, y compris dans le moteur.

---

## 4. Architecture de la page d'accueil

Reconstruite d'après `sections`, `largeImages`, `headings` et les captures. Hauteur 8 427 px desktop, 5 015 px mobile.

| Position (px) | Section | Objectif | Contenu | Interaction | CTA | Émotion créée |
|---|---|---|---|---|---|---|
| 0–900 | Hero | Poser l'univers | Image 1920×1080, H1 « The art of simplicity », header transparent, « Scroll ˅ » | transition 6 s (hyp. lent zoom) | Request, Book | Calme, altitude |
| 1 102–1 350 | Manifeste | Expliquer la promesse | H1 « Peace as a new luxury » + paragraphe 713 px | — | — | Adhésion |
| 1 360–2 440 | Mosaïque 4 images | Montrer sans décrire | Hôtel + piscine vus du ciel (0,8), forêt zénithale (1,33), bûches (1,33), bougie (0,8) | hover opacité 0,8 / 0,25 s | — | Curiosité, matière |
| 2 560–2 850 | Citation | Humaniser | Citation 30 px, « Hosts — Teresa & Stefan » | — | — | Confiance |
| 3 003–3 611 | Suites | Première offre | Image 1440×810 (chambre, vue), paragraphe sur la vue | — | Discover more → /suites | Projection |
| 4 020–4 700 | Villa | Offre exclusive | Image 1440×810 (chalet), H2, paragraphe (10 pers., spa privé) | — | Discover more → /villa | Exclusivité |
| 5 146–5 860 | Mosaïque 3 images | Introduire le spa | Femme de dos en couloir béton (1:1 713 px), fossile, main + pierres (1:1) | hover | — | Sensualité, rituel |
| ≈5 900–6 200 | Spa texte | Philosophie | H2 « A regenerating flow », paragraphe (Celtes) | — | Discover more → /spa | Confiance |
| 6 347–7 195 | Diptyque | Introduire la cuisine | Écorce + herbier (0,62) | hover | — | Naturalité |
| ≈7 200–7 500 | Cuisine texte | — | H2 « Forest Cuisine » + paragraphe — non rendu dans la capture desktop | — | Discover more → /restaurant | — |
| ≈7 500–7 830 | Social | Preuve | H2 « Follow the inspiration #forestisdolomites », flux non rendu | — | — | (non observable) |
| 7 837–8 427 | Footer | Réassurance | 4 réseaux, 7 liens, EN/DE/IT, adresse, tél, mail, 5 badges | hover | Contact & Arrival | Crédibilité |

**Logique narrative** : début par le paysage et un slogan sans localisation ; désir construit par un manifeste, des matières, puis une voix humaine ; l'offre ne devient concrète qu'à 3 003 px (3,3 écrans), par une image de chambre avec vue, sans nom ni prix ; la villa a plus de place que les suites ; preuve = citation interne + badges, aucun avis ; réservation uniquement dans le header ; fin sur Instagram et footer, sans rappel de réservation.

**Interprétation** : la home est un magazine, pas une landing page ; chaque « Discover more » mène à une page de marque, jamais au moteur. **Enseignement** : alterner strictement image → titre court → paragraphe centré → lien souligné, et limiter la home à 4 thèmes.

---

## 5. Scroll et storytelling

**Faits observés**
- 6 blocs image / 6 blocs texte en alternance stricte ; blocs image de 608 à 1 080 px, blocs texte de 250 à 300 px.
- Fond constant après le hero (`centerBg` rgb(242,241,235) à toutes les positions). Spa et Dining : une bande grise pleine largeur, texte blanc (Retreats, chef). Experiences : image plein écran 1440×900 (« The perfect day ») au milieu.
- Aucun parallaxe, élément épinglé (`pinned []`, `transforms 0`), scroll horizontal ou `position: sticky` CSS (0). `sticky-kit` chargé : la sous-nav Suites (« Penthouse · Tower Suite · Suite · Room · FAQ ») suit sous le header à la position suivante (`suites-03-scroll2`).
- `scroll-snap` : 7 règles, aucun snap observé (positions libres 428 / 855 / 1 283 px). **Hypothèse** : règles Swiper.
- Révélations : `reveal` 3 sur Request, 1 sur Tower Suite ; `fadeInUp 1s cubic-bezier(.645,.045,.355,1)`. Zones vides des captures desktop : révélation présumée sur la home aussi.
- Densité : home 261 mots, suites 150, Tower Suite 147, villa 933, spa 540, experiences 1 436. Indicateur « Scroll ˅ » sur chaque hero (900 px desktop, 681 mobile).

**Interprétation par effet**
- Alternance à fond constant : rythme + marque ; oriente le regard vers les images puisque rien d'autre ne contraste.
- Bande grise unique par page : orienter le regard vers un contenu d'une autre nature (programme, portrait) et signaler un chapitre.
- Image plein écran au milieu d'Experiences : émotion, retour à la montagne après une liste.
- Sous-nav qui suit : action, accès aux 4 catégories.
- Aucune mécanique spectaculaire : le storytelling repose sur l'ordre des contenus. Les 200 px de respiration donnent l'envie de poursuivre mais allongent (9,4 écrans pour 261 mots).

**Enseignements** : un scroll « plat » peut être plus cohérent qu'un scroll animé pour une marque du silence, à condition d'un rythme strict ; une seule rupture de fond par page ; une sous-nav qui suit vaut mieux qu'un CTA flottant sur un catalogue.

---

## 6. Animations et micro-interactions

| Animation | Déclencheur | Élément | Effet | Fonction | Risque UX |
|---|---|---|---|---|---|
| Arrivée / préloader | chargement | corps | aucun ; `app_fadeIn 0.8s ease` sur SynXis seulement | vitesse perçue | aucun |
| Hero | chargement | image 1512×945 (y=-22) | transition 6 s (×1 desktop, ×3 mobile) — **hyp.** lent zoom, invisible en capture | émotion | CPU mobile |
| Titres / blocs | entrée viewport | Request, Tower Suite, probablement home | `fadeInUp 1s cubic-bezier(.645,.045,.355,1)` | rythme | contenu invisible si JS lent (zones vides observées) |
| Révélation d'images | entrée viewport | 9/25 images lazy (home), 26/41 (Experiences), 0 (Suites, fiche) | apparition sans transition | perf | aucun CLS (dimensions fournies) |
| Zoom photo au hover | — | aucun | pas de `scale` mesuré | — | — |
| Transitions de page | clic | — | non mesurables ; `onepage-scroll.js` chargé sans effet observé | — | — |
| Curseur | — | — | natif (`cursorEls []`) | — | aucun |
| Hover liens / cartes | survol | `<a>` | `opacity 1→0.8` + `color`, 0,25 s `ease` | feedback | trop faible sur texte Light |
| Carrousels | flèches / tirets | Swiper (Suites 1080×608 ; Tower Suite 5 slides 1080×689, flèches blanches, 5 tirets) ; flexslider, fancybox chargés | glissement ; `cubic-bezier(.23,1,.32,1)` ×2 (**hyp.** Swiper) | expliquer | flèches blanches sur mur beige (`suite-detail-03-scroll1`) |
| Menu desktop | clic « Menu » | `#main-menu` fixed 1440×219–224, #f2f1eb, z 2, y=-224 | translation verticale (**hyp.**, 0,4–0,5 s) ; « Menu » → « × » | action | panneau de 224 px : se lit comme une barre de plus |
| Menu mobile | tap | `#main-menu` 390×844, z -1 au repos | plein écran, 9 liens 22 px espacés ≈ 98 px, « EN ˅ », barre 3 icônes conservée | action | dépend du JS (`no burger found`) |
| Barre supérieure | scroll | `#main-top` | visible en haut, fond crème, dans toutes les captures `03-scrollN` ; **absente** dans `flow-scrollup-bar.png` ; non listée `fixed` ; `flows.json` : aucune différence bas/haut pour `#main-menu` | action (Book permanent) | comportement non concluant (**hyp.** : fixe avec masquage en remontée, ou artefact) |
| Sous-navigation | scroll | `.sub-nav` (Suites, Tower Suite, Spa, Hideaway) | suit sous le header ; mobile : `<select>` 330×50 px | action | style natif en mobile |
| Vidéo | — | aucune balise | — | — | ≈ 700 Ko de JS vidéo inutiles |
| Feedback formulaire | focus | Umbraco Forms / flatpickr | non testé ; `focusOutlineNone` 86 | — | pas de focus visible |
| Loader | — | `stretchdelay 1.2s ease-in-out` ×5 | barres étirées (**hyp.** spinner de widget) | feedback | — |
| Reduced motion | media query | — | **0 règle** ; 5 éléments animés + 49 en transition ; capture `home-04-reduced-motion` identique | — | zoom 6 s et fadeInUp subis |

**Interprétation** : site presque sans animation — hovers 0,25 s, fadeInUp 1 s, un carrousel. Cohérent, mais deux angles morts : feedback de hover trop faible, et aucun respect de `prefers-reduced-motion` alors qu'il n'y a presque rien à désactiver.

**Enseignement** : trois durées (0,25 / 0,4–0,5 / 1 s) et deux easings (in-out cubic, out quint) suffisent à un site entier ; les documenter comme tokens.

---

## 7. Navigation et architecture de l'information

**Faits observés**
- Header : « Menu », logotype centré, « Request » + « Book ». Sur Villa, « Book » est retiré (`main-top` : « Menu Forestis Request ») — la villa se réserve sur demande.
- Menu déplié desktop : 9 entrées sur une ligne, 20 px, sans sous-menus ni images ; sélecteur DE/EN/IT. Mobile : plein écran, « Request » absent du header, remplacé par la barre fixe (tel / mail / localisation, 3 cellules de 130×50 px).
- Sous-navigations : Suites (Penthouse · Tower Suite · Suite · Room · FAQ, 74 px), Spa (Treatments · Movement), Hideaway (Terms · Teresa & Stefan · Alois), Villa (ancres Accommodation · Culinary · Spa · Garden).
- Footer : 7 liens corporate, langue, adresse, tél, e-mail. Contact : GPS, plus code, distances aéroports (Bolzano 50 km, Innsbruck 90, Verona 195, Munich 260, Venice 326, Milan 377), transferts Tesla X (5 places) et minibus (8). Annulation et horaires uniquement dans le moteur.
- Étapes jusqu'à une offre : Home → Menu → Suites → Tower Suite = 3 clics ; + « Request » ou « Book » (SynXis, nouvel onglet) = 4. « Book » header = 1 clic mais hors domaine.
- Frustrations : `linksNoName` 5 (icônes sociales dont l'alt est « opens in a new window »), `tabindexNeg` 9 à 111, `focusOutlineNone` 86 à 116, 0 landmark, pas de skip link ; title de Request « Book your stay in Alto Adige » alors que la page ne réserve pas.

**Interprétation** : architecture plate et lisible mais qui mélange lieux (Hideaway, Villa), produits (Suites, Spa, Cuisine), marque (YERA, opaque), commerce (Voucher) et média (Gallery, Experiences). Trouver une chambre suppose de savoir que « Suites » contient « Room » ; trouver un prix suppose SynXis. Réservation persistante : oui en desktop (sous réserve de la rubrique 6), en texte 44×27 px ; en mobile 40×25 px, la barre fixe étant dédiée au contact.

**Enseignements** : retirer « Book » sur les produits sur demande ; une barre mobile fixe « appeler / écrire / y aller » convient à un hôtel de destination, une 4e cellule « Book » serait le compromis conversion ; une sous-nav par section catalogue remplace les méga-menus.

---

## 8. Parcours de réservation et conversion

**Faits observés**
- Premier CTA : « Book » header, y=79, 44×27 px, `target=_blank`, `https://be.synxis.com/?chain=22402&hotel=30944&locale=en-US&src=24C&filter=HOTEL&adult=2`. « Request » 71×27 px, page interne.
- Formulations : Request / Book (header), Discover more (home, suites), Request (fiche), Request Villa, Submit (formulaire), Send (contact). Découvrir / demander / réserver : distinction nette et constante.
- Page Request : H1 « Reservation request », intro avec téléphone et e-mail cliquables ; formulaire Umbraco en 2 groupes — Arrival, Departure (flatpickr), adultes 1–4, Suite type (Penthouse / Room / Suite / Tower Suite), Board (Breakfast / Half board) ; Salutation, Surname, Given name, Email, Phone, Message, newsletter, privacy. Champs 355×36 px, rayon 0, labels au-dessus ; Submit = lien souligné. Pas d'enfants (14+), pas de nombre de chambres.
- Fiche Tower Suite : ni prix, ni disponibilité, ni calendrier ; CTA unique « Request » en bas (y=1618 desktop, 999 mobile).
- SynXis (entrée) : bandeau photo, adresse/tél/site, encart « Adults only from 14 years », cases Guests / Check-in / Check-out de 78 px, double calendrier, « Special Codes or Rates », panier « 0 Items ». Liste : « Room — Only 2 rooms left — 1 King bed — Sleeps 2 — 35 sq m », pictos (desk, pets allowed, wifi, shower, safe), 2 tarifs (B&B 1 300 €, HB 1 425 €, « Including taxes and fees », « Deposit Required »), boutons « Book Now » 157×52 px #e6e4da. Checkout : Guest Info, Address, Special Requests, Payment (« €390.00 deposit due now », 8 logos cartes), Policies (check-in 15 h, check-out 11 h, acompte 30 %, 29→11 jours : 50 %, ≤ 10 jours : 100 %), « Continue ». Panier fixe 407×719 px.
- Réassurance : badges du footer sur toutes les pages y compris SynXis ; tél et mail à chaque étape ; aucun avis, aucune note, aucun « meilleur tarif garanti », aucun bénéfice direct.
- Offres : Experiences liste des séjours datés (Cooking Class, Celtic New Year Ritual…) sans prix ni bouton, « Read more » seulement ; « Voucher » non audité. Upsell SynXis : « Add A Room » uniquement.
- Ruptures : domaine be.synxis.com, nouvel onglet, police BrandonGrotesqueWeb-Light, header différent (Rooms / About / My Bookings / EUR / English-US / panier), TTFB 1 005 ms, 8 893 Ko (HTML 1 085 Ko), `adult=2` transmis mais « 1 adult » affiché.

**Interprétation** : deux parcours francs — demande humaine (très présente, cohérente avec le luxe de service) et réservation en ligne externalisée — mais deux verbes de même poids à 25 px l'un de l'autre. Transparence nulle sur le site, totale dans le moteur : qui veut « juste le prix » doit quitter le site. L'identité est maintenue à ≈ 80 % dans SynXis (fond, gris, Brandon, rayon 0, logo, badges) ; la rupture est typographique et de densité. Manques : preuve sociale, bénéfice direct, « à partir de » sur les fiches, enfants/animaux dans Request alors que SynXis affiche « Pets Allowed ».

**Enseignements** : garder demander/réserver mais hiérarchiser par catégorie ; paramétrer le moteur avec palette, fond et badges ; afficher au minimum « à partir de » ou un lien « prix et disponibilités » avec la catégorie pré-sélectionnée.

---

## 9. Pages chambres / propriétés

### Liste « Suites »

**Faits observés** : hero 900 px sans titre (`header.text: "Scroll"`), H1 « Suites » après ; sous-nav 74 px ; paragraphe de 3 phrases ; carrousel Swiper 1080×608 avec onglets internes « Penthouse · Tower Suite · Suite · Room » superposés en bas de l'image ; H2 sous l'image, ligne « 200 m² – 2 persons – 1 bedroom – Rooftop with pool », « Discover more ». Une catégorie visible à la fois ; page de 3 184 px, 150 mots ; 4 catégories toutes « 2 persons ». Mobile : hero 681 px, sous-nav → `<select>` « Suites ˅ » 330×50, carrousel 330×186, barre fixe en bas.

### Fiche « Tower Suite »

**Faits observés**
- Title « Luxury Hotel Suites in South Tyrol | Forestis Dolomites » (générique) ; description : vues, dressing, douche pluie, lit king.
- Pas de hero : header 150 px, sous-nav 74 px, H1 40 px à y≈426.
- Ordre : H1 → carrousel 5 images 1080×689 (chambre/rideau, salle de bains béton ciré, terrasse avec silhouette…) → H3 « 55 m² – 2 persons – 1 bedroom » 26 px → un paragraphe ≈ 90 mots (lit boxspring king, climatisation, baies vitrées, dressing avec coffre, TV, minibar, bureau, poêle en faïence, baignoire + douche pluie, WC séparés avec bidet, « all the FORESTIS amenities ») → « Request » → footer. 2 440 px, 147 mots.
- Absents : prix, disponibilité, plan, équipements structurés, inclusions, avis, autres suites (hors sous-nav), « Book » contextuel, vidéo.
- Mobile : `<select>` « Tower Suite ˅ », H1 30 px, carrousel 330×186 (1,57 → 1,77 : la silhouette sur la terrasse est coupée), corps 18 px, « Request » 64×25 px ; 1 924 px ; dernière ligne de chaque écran masquée par la barre fixe.

**Interprétation** : la fiche vend la vue et les matières (poêle en faïence, béton ciré, lin) — éléments de projection sensoriels — en un seul bloc que rien ne hiérarchise : « direct view of the Dolomites » au même niveau que « bidet ». La liste montre une catégorie à la fois : cohérent avec « simplicity », mais empêche la comparaison qu'attend un acheteur à 1 300 €+. Aucune réassurance, aucun cross-sell.

**Enseignements** : conserver la ligne « m² – personnes – chambres – atout » ; scinder le paragraphe en « ce que vous voyez / ce que vous avez / ce qui est inclus » ; recadrages portrait dédiés en mobile.

---

## 10. Copywriting

**Faits observés**
- Ton déclaratif, troisième personne (« FORESTIS regards itself as… », « The villa can only be booked exclusively… ») ; « you » réservé aux formulaires et au contact.
- Titres de 1 à 4 mots (« Suites », « Regeneration », « A regenerating flow », « Peace as a new luxury ») ; titres longs de type magazine sur Experiences (« The art of letting go – A ritual for winter »).
- Paragraphes de 40 à 90 mots ; pages de 147 à 1 436 mots ; mesure 713 px (≈ 75 caractères).
- Champ lexical : nature (forest, treetops, spring-water, elements, Celts, herbs), temps (regeneration, sleep, « time can once again be sensed »), privauté (sheltered, secluded, absolute privacy), matière (stone, larch, Swiss stone pine, tiled stove).
- Sensoriel : « Drenched in sunlight all day », « Nothing obstructs the view », « The restaurant is step shaped… each table offers the desired privacy ».
- Le luxe par soustraction et rareté (« only », « exclusively », « secluded », « adults only ») ; « luxury » n'apparaît que dans les titles et dans « Peace as a new luxury ».
- Technique : cantonnée à la ligne de chiffres et au paragraphe de fiche ; « 1,800 m » revient sur 4 pages.
- Prestation → expérience : le spa décrit par ses sources avant ses installations, la cuisine par la cueillette avant le restaurant, les suites par la vue avant le lit.
- CTA : verbes nus (Request, Book, Discover more, Read more, Submit, Send), sauf « Request Villa ». Guillemets allemands » « pour la citation, prénoms sans nom.

**Interprétation** : quatre mécanismes — titre-substantif court + paragraphe qui commence par le lieu ; une phrase d'histoire par page (1912, Otto Wagner) ; « only / exclusively » à la place de « luxe » ; le chiffre comme preuve (1 800 m, 200 m², 4 éléments, 14+). Faiblesses : CTA nus qui n'annoncent pas la suite (« Book » ouvre un autre site), « you » absent des pages d'inspiration, title de Request contradictoire.

**Enseignements** : écrire nature → lieu → offre ; remplacer « luxe » par « seulement / exclusivement / à l'abri » ; donner un objet aux CTA.

---

## 11. Photographie et vidéo

**Faits observés**
- Home : 1 paysage grand-angle, 1 aérienne oblique (hôtel + piscine, brume), 1 forêt zénithale, 4 gros plans de matière (bûches, écorce, fossile, herbier), 1 intérieur sombre (bougie), 1 chambre avec vue, 1 villa dans les sapins, 1 silhouette de dos en maillot, 1 main tenant des pierres.
- Autres pages : chambre à contre-jour, salle de bains béton ciré (Suites) ; soin à l'huile en plongée, piscine avec reflet, pierre monumentale, raquettes (Spa) ; champignon, mains, salle en gradins, chef en pied sur bande grise, cocktail (Dining) ; fenêtre en ogive, canapé au soleil, rai de lumière sur lit, escalier bois, portrait du chef de villa (Villa) ; portrait des hôtes en couple, hôtel en été, 5 archives noir et blanc du sanatorium (Hideaway) ; cabanes sous la neige, cartes eau/air/soleil/climat (Experiences).
- Lumière rasante dorée (heure bleue, heure dorée), intérieurs volontairement sombres, ombres de fenêtres comme motif ; brun, ocre, gris chaud, vert sapin ; blanc pur seulement sur l'herbier et la neige.
- Présence humaine rare et anonyme (dos, mains), sauf portraits d'équipe regard caméra.
- Alt en série (« Forestis Dolomites Luxury Hotel8385 »), crédit dans l'alt du hero (« FORESTIS Charlotte Lapalus »), 5 images sans alt, 32 alt vides (tuiles Maps).
- Poids : plus grosses images mesurées Spa 307 Ko (hero) et 238 Ko, Villa 185 Ko, SynXis 496 Ko (jpg non optimisé) ; home desktop 1 595 Ko / 57 requêtes, Spa 2 834 Ko / 65, Villa 1 881 Ko / 61 ; home mobile 288 Ko / 29.
- Vidéo : aucune balise sur les pages auditées ; video.js + dash.js chargés (**hyp.** galerie ou pop-in).
- Proportion home : 4 images de matière, 3 de nature, 3 d'architecture, 2 de corps — l'expérience l'emporte sur le lieu.

**Interprétation** : la photographie dit le luxe (béton ciré, lin, faïence) que le copy refuse de nommer. Les gros plans de matière sont la signature et le liant entre pages ; ils sont interchangeables, ce qui unifie mais peut lasser. Les archives de 1912 sont l'élément le plus distinctif. Cohérence totale de lumière et de désaturation, portraits compris.

### Shot list pour reproduire ce niveau

1. Hero paysage grand-angle à l'heure dorée, ciel libre dans le tiers supérieur (16:9 + 9:16).
2. Aérienne oblique du bâtiment dans son site, avec eau ou brume.
3. Zénithale de la nature environnante, sans bâtiment.
4. Six gros plans de matières locales (bois, pierre, textile, végétal, eau, métal) en 4:5 et 3:4.
5. Intérieur sombre avec source lumineuse unique.
6. Chambre depuis le lit vers la vue, contre-jour (16:9 + 9:16).
7. Salle de bains en lumière naturelle, produits de la maison visibles.
8. Silhouette anonyme dans l'architecture (dos, marche) ; main + élément naturel en macro.
9. Portraits des hôtes / du chef, regard caméra, fond neutre ou bâtiment.
10. Cuisine : mains + ingrédient brut, assiette dressée, salle vide au matin.
11. Spa : soin en plongée, bassin avec reflet du paysage, pièce de silence vide.
12. Nature morte des éléments du lieu sur fond clair (visuel-signature).
13. Archives ou documents historiques du lieu (à défaut : plans, objets).
14. Même point de vue aux quatre saisons.
15. Vidéo si budget : 3 plans fixes de 10 s (paysage, matière, eau), sans mouvement de caméra.

---

## 12. Mobile

**Faits observés**
- Viewport `initial-scale=1.0, user-scalable=0, maximum-scale=1.0` : zoom bloqué.
- Hero 681 px (81 % de l'écran), image 585×1022, H1 30 px, header 100 px (« Menu », logo, « Book » 40×25 px) ; pas de « Request ».
- `#footer-mobile` fixed 390×50 px, y=794, z 3, 3 cellules pictos sans libellé ; masque les 50 derniers pixels de chaque écran (titre « Peace as a new luxury » sur `home-mobile-01-hero`, une ligne de paragraphe sur `suite-detail-mobile-02-full`).
- Menu : plein écran, 9 liens 22 px espacés ≈ 98 px, « EN ˅ », « × », « Book » conservé.
- Titres : H1 30,06/42,08, H2 21,96/30,74, H3 21,96, corps 18/28,8, citation 21,96 ; mesure 330 px. Mosaïques en 2 colonnes de 162 px ; images pleine largeur 330×186. Home 5 015 px (≈ 6 écrans).
- Animations identiques (0,25 s ×161 ; 6 s ×3 — hero dupliqué 3 fois dans le DOM, d'où `h1count 4`), aucune réduction.
- Cibles : « Book » 40×25, « Request » 64×25, « Discover more » ≈ 225×30, « Contact & Arrival » 134×25, cellules fixes 130×50, `<select>` 330×50.
- Vitesse : 90 requêtes, 3 874 Ko (scripts 3 421, images 288), TTFB 627, FCP 1 124, load 2 770 ms ; Villa 3 858 Ko / 2 500 ms ; Tower Suite 3 127 Ko / 2 580 ms.
- Lisibilité : 18 px Light sur crème ≈ 11:1 ; H1 blanc sur ciel gris clair 2,5–4:1 (**hyp.**). SynXis mobile non capturé.

**Interprétation** : réduction fidèle du desktop — mêmes contenus, mêmes proportions ; rien supprimé (pas même le zoom présumé), rien ajouté sauf la barre contact. Problèmes : zoom bloqué ; barre fixe sans `padding-bottom` compensatoire ; cibles de 25 px sous les 44 px recommandés ; 3,4 Mo de JS pour 288 Ko d'images ; recadrage 1,57 → 1,77 qui coupe les portraits ; `<select>` natif. Forces : hiérarchie conservée, menu très lisible, contact en un tap, aucune pop-up.

**Enseignements** : compenser toute barre fixe par un padding et y placer la réservation ; ne jamais bloquer `user-scalable` ; différer le JS, les images sont déjà bien réduites.

---

## 13. Performance, accessibilité, SEO

**Faits — performance**
- Home desktop : TTFB 545 ms, FCP 1 228, DCL 2 191, load 2 664 ms ; 171 requêtes, 8 383 Ko ; scripts 75 fichiers / 6 458 Ko (77 %), images 57 / 1 595 Ko, CSS 8 / 265 Ko.
- Plus gros : bundle Vite 606 Ko, `video.min.js` 472 Ko (aucune vidéo), Facebook pixel 443 Ko, Cookiebot 379 Ko, dash.js 227 Ko, gtag 182 Ko, GTM 159 Ko. Bibliothèques : jQuery 3.4.1, jQuery UI 1.12.1, flexslider, fancybox, sticky-kit, viewportchecker, imagesloaded, onepage-scroll, Swiper, flatpickr 4.6.13, Google Maps sur toutes les pages, relay-t.io, getsitecontrol, Bing UET, Cloudflare Insights.
- Villa load 12 771 ms (175 requêtes, 7 767 Ko — **hyp.** ressource tierce lente) ; Spa 8 721 Ko (images 2 834) ; Hideaway 236 requêtes et Contact 225 (Maps) ; SynXis 8 893 Ko, TTFB 1 005 ms, HTML 1 085 Ko.
- Lazy : 9/25 (home), 26/41 (Experiences), 0 (Suites, fiche, Request) ; 0 `srcset` ; webp via query string ; dimensions explicites, pas de CLS visible ; LCP non mesuré.

**Faits — accessibilité**
- Contrastes estimés : #333 sur #f2f1eb ≈ 11,2:1 ; #999 placeholders ≈ 2,5:1 (échec) ; blanc sur ≈ #70716c ≈ 4,9:1 ; blanc sur hero 2,5–4:1 (hyp.) ; #333 sur #e6e4da ≈ 9,9:1.
- `focusOutlineNone` 86–116, `tabindex=-1` 9 (111 sur Request, flatpickr), pas de skip link (présent sur SynXis), 0 landmark (SynXis : main 1, nav 1, header 2, footer 1).
- Alt : 5 manquants par page (logos partenaires, hyp.), « opens in a new window » ×7 sur les réseaux, 32 vides sur Maps (acceptable). Formulaires : labels présents, placeholders #999, non testés en erreur.
- Reduced motion : 0 règle ; comportement identique en `prefers-reduced-motion`. Zoom bloqué. Police 10 px sur les contrôles Maps.

**Faits — SEO**
- Titles distincts (home, suites, spa, restaurant, experiences) ; fiche Tower Suite = title générique de catégorie ; Hideaway et Contact courts ; Request trompeur.
- Description sur 7 pages, absente sur Hideaway et Contact ; og:title/description partout, og:image seulement sur Villa ; canonical auto-référent ; hreflang en/de/it/x-default ; `lang="en"`.
- JSON-LD : aucun. H1 : home 2 (mobile 4), Villa 2, Dining 0, autres 1 ; Experiences enchaîne H1 → H3 avant le premier H2. Mots : 136 à 1 436 ; fiche suite 147.
- Générateur non déclaré ; `umbraco-forms-field` → CMS Umbraco (**hyp.** forte).

**Interprétation** : visuellement léger, techniquement lourd — 6,5 Mo de JS pour un site sans animation ni vidéo rendue, empilement jQuery 2015–2019 à côté d'un bundle Vite (**hyp.** migration incomplète). Perception bonne (FCP ≈ 1,2 s) parce que le hero arrive tôt. L'accessibilité est le point faible principal alors que l'esthétique s'y prêterait. SEO : bases correctes, lacunes sur données structurées, og:image, H1 et volume texte des fiches. L'immersion ne coûte presque rien (288 Ko d'images en mobile) ; ce sont les tiers qui coûtent.

**Enseignements** : charger Maps et video.js seulement où nécessaire ; ajouter `focus-visible`, landmarks, skip link et une règle reduced-motion ; un H1 par page et un schema LodgingBusiness + Offer par catégorie.

---

## 14. Conclusion

### 15 meilleurs éléments
1. Une police, une graisse, une échelle 40/30/26/20 tenue sur toutes les pages.
2. Fond #f2f1eb + texte #333 (≈ 11:1) : lisibilité et signature.
3. Zéro bouton : CTA texte souligné, rayon 0, sans dérogation.
4. Menu qui commence par « Hideaway ».
5. Promesses en opposition : « Peace as a new luxury », « The art of simplicity ».
6. Citation des hôtes en 30 px, prénoms seuls.
7. Cinq ratios d'images en mosaïques 2 et 3, gouttière 20 px, marges 180 px.
8. Gros plans de matières comme liant entre spa, cuisine et lieu.
9. Archives 1912 et récit d'architecture sur Hideaway.
10. Ligne « 200 m² – 2 persons – 1 bedroom – Rooftop with pool » sous chaque catégorie.
11. Sous-nav par catégorie qui suit le scroll.
12. « Book » retiré du header sur la Villa.
13. Barre mobile fixe contact en 3 cellules de 130×50 px.
14. SynXis paramétré avec palette, logo et badges.
15. Page Contact exhaustive (GPS, plus code, 7 aéroports, transferts nommés).

### 5 faiblesses
1. Conversion : deux CTA texte de même poids (71×27 / 44×27), aucun prix ni disponibilité sur les fiches, aucun avis, aucun bénéfice direct.
2. Accessibilité : 86–116 éléments sans focus, 0 landmark, pas de skip link, zoom bloqué, 0 règle reduced-motion.
3. Poids : 6,5 Mo de JS (video.js, dash.js, Maps, jQuery UI partout), Villa à 12,8 s.
4. Mobile : barre fixe qui masque 50 px, cibles de 25 px, recadrage 1,57 → 1,77.
5. Structure/SEO : 2 H1 sur la home, 0 sur Dining, pas de JSON-LD, title trompeur sur Request, 147 mots sur une fiche à 1 300 €/nuit.

### 10 principes réutilisables
1. Une famille, une graisse, quatre tailles.
2. Le vide comme composant : 200 px entre blocs, 713 px de mesure.
3. Alternance stricte image → titre court → paragraphe centré → lien souligné.
4. Nature → lieu → offre dans chaque page.
5. Dire le luxe par « only / exclusively / secluded ».
6. Cinq ratios d'images fixes, recadrages mobiles dédiés.
7. Une rupture de fond par page.
8. Lieu et hôtes en tête de navigation ; prix dans le moteur.
9. Le CTA suit le mode de vente par catégorie.
10. Le moteur externe reprend fond, police, logo, badges.

### À ne PAS copier (propre à la marque)
Le logotype au « T »-flèche ; le récit des quatre éléments et la référence celte (Wyda) ; l'histoire du sanatorium 1912 / Otto Wagner et ses archives ; Teresa & Stefan, YERA, Odles Lodge ; « adults only 14+ » et « from € 25,000 » ; la palette exacte crème + Brandon Light, à réinterpréter plutôt qu'à reproduire.

### Notes /10

| Critère | Note | Justification |
|---|---|---|
| Branding | 9 | Promesse claire, navigation qui commence par le lieu, vocabulaire de soustraction sur 9 pages ; − hero sans localisation, « YERA » opaque, écart entre balises (« luxury ») et pages. |
| Direction artistique | 9 | 2 couleurs / 1 police / rayon 0 tenus partout ; mosaïques sur 5 ratios ; photo de matières homogène ; − gris de bande non tokenisé, CTA Light peu saillants. |
| Animations | 5 | Hover 0,25 s, fadeInUp 1 s, easings définis ; − 0 règle reduced-motion pour 5 éléments animés, barre supérieure au comportement non concluant, 700 Ko de JS vidéo sans vidéo, feedback à 0,8 d'opacité. |
| UX | 6 | Menu plat, sous-nav qui suit, contact en un tap, page Contact complète ; − une catégorie à la fois sur Suites, `<select>` natif, 0 landmark, zoom bloqué, barre fixe qui masque. |
| Conversion | 5 | Request/Book nets, moteur à la marque, transparence dans SynXis (TTC, acompte 30 %, annulation) ; − aucun prix sur le site, deux CTA de même poids, aucune preuve sociale, « Book » 44×27 px hors domaine. |
| Mobile | 6 | Hiérarchie 30/22/18 conservée, 288 Ko d'images, menu lisible, barre contact ; − 3,4 Mo de JS, cibles 25 px, zoom bloqué, contenu masqué, recadrages. |

**Note globale : 6,7 / 10.** FORESTIS est une référence de branding et de direction artistique : un système minimal qui tient sur toutes les pages et une écriture qui vend le silence sans dire « luxe ». Le site s'arrête là où commence la vente — aucun prix, aucune preuve, deux CTA identiques, un moteur externe — et porte 6,5 Mo de scripts hérités qui contredisent sa légèreté. L'accessibilité est le chantier le moins coûteux et le plus rentable. Modèle de DA à étudier ; contre-exemple de parcours de réservation.

---

## Observations clés à conserver pour la phase comparative

- Palette : fond #f2f1eb (1 245 éléments) + texte #333333 (166), blanc seulement sur hero/bandes ; contraste corps ≈ 11:1 ; SynXis conserve #f2f1eb + #e6e4da.
- Typo : une seule police chargée, BrandonTextLight 400 ; 40/30/26/20 px desktop (interlettrage 1,5 / 1 / 0,75), 30/22/22/18 mobile ; interligne 1,4.
- Zéro `<button>` : CTA = liens soulignés de 25–27 px de haut (« Book » 44×27 desktop, 40×25 mobile) ; rayon 0 partout.
- Grille : mesure 713 px, images 1080 (marges 180), mosaïques 2×530 + gouttière 20 ; mobile 330, colonnes 162.
- Ratios : 1,6 (hero 1920×1080), 1,78, 1,57, 1,33, 1:1, 0,8, 0,62 ; mobile 0,57 et 1,77 ; webp par query string, 0 `srcset`.
- Home : 8 427 px (9,4 écrans) pour 261 mots ; 6 blocs image / 6 blocs texte ; première offre à 3 003 px ; 0 CTA réservation dans le corps.
- Aucun parallaxe, sticky CSS, snap effectif ni curseur custom ; 0 règle reduced-motion ; transitions 0,25 s ×163 ; `fadeInUp 1s cubic-bezier(.645,.045,.355,1)` ; 6 s ×1 sur le hero.
- Menu desktop = panneau fixe 224 px, 9 entrées ; mobile plein écran ; barre mobile fixe 390×50 (tel / mail / localisation), sans Book.
- Parcours : Request (Umbraco, 11 champs, sans enfants) vs Book (SynXis, nouvel onglet, `adult=2`) ; fiche Tower Suite 5 images, 147 mots, 0 prix ; Room 35 m² 1 300 € B&B / 1 425 € HB, acompte 30 %, annulation 50 % à 29–11 j, 100 % ≤ 10 j ; villa « from € 25,000 a night », 2 nuits min.
- Preuve : 5 badges footer (14+, SLH, Odles Lodge, Michelin 2024, YERA), citation des hôtes ; 0 avis, 0 note, 0 bénéfice direct.
- Perf home desktop : 171 requêtes, 8 383 Ko dont 6 458 Ko de scripts (video.js 472, dash.js 227, FB 443, Cookiebot 379, Maps partout), TTFB 545, FCP 1 228, load 2 664 ms ; mobile 3 874 Ko (images 288) ; Villa load 12 771 ms ; SynXis 8 893 Ko, TTFB 1 005 ms.
- A11y : `focusOutlineNone` 86–116, 0 landmark, skip link absent (présent sur SynXis), `user-scalable=0`, 5 images sans alt, alt « opens in a new window » ×7.
- SEO : hreflang en/de/it/x-default, canonical OK, 0 JSON-LD, og:image seulement sur Villa ; H1 : 2 sur home (4 mobile), 0 sur Dining ; 136–1 436 mots.
- Vidéo : 0 balise sur 12 pages malgré video.js + dash.js ; hero = image fixe.
- Pile (preuves) : Swiper, jQuery 3.4.1 + UI 1.12.1, flexslider, fancybox, sticky-kit, viewportchecker, onepage-scroll, flatpickr 4.6.13, bundle Vite, Cloudflare, GTM/GA4/FB/Bing, Cookiebot ; Umbraco (hyp. forte) ; SynXis (React).
