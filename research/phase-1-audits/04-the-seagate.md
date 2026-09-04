# Fiche d'audit — The Seagate, Delray Beach (Autograph Collection / Marriott)

## 0. En-tête

- **Nom** : The Seagate Hotel, Golf & Beach Club — Autograph Collection Hotels (Marriott), opéré par Turnberry (logos Turnberry + Marriott Bonvoy en footer).
- **URL de départ** : https://www.seagatedelray.com/ — **Date** : 2026-09-04 (captures 16:40 → 16:51 UTC).
- **Environnement** : Chromium headless via Playwright, 1440×900 (desktop) et 390×844 DPR 2 (mobile). Clé : `seagate`.

| Label | URL | Desktop | Mobile |
|---|---|---|---|
| home | https://www.seagatedelray.com/ | oui | oui |
| rooms (Rooms & Suites) | https://www.seagatedelray.com/rooms-suites/ | oui | oui (flow-mobile-rooms-full) |
| experiences (Events & Experiences) | https://www.seagatedelray.com/events-experiences/ | oui | non |
| dining | https://www.seagatedelray.com/dining/ | oui | non |
| spa (Wellness) | https://www.seagatedelray.com/wellness/ | oui | non |
| about | https://www.seagatedelray.com/about/ | oui | non |
| contact | https://www.seagatedelray.com/contact/ | oui | non |
| membership | https://www.seagatedelray.com/membership/ | oui | oui |
| engine (page hôtel Marriott) | https://www.marriott.com/en-us/hotels/pbidb-the-seagate-hotel-and-spa/overview/ | « Access Denied » | — |
| booking (clic RESERVE) | https://www.marriott.com/search/availabilityCalendar.mi?isRateCalendar=false&propertyCode=PBIDB&isSearch=true | « Access Denied » | — |

**Limites de l'observation**
1. Le hero de la home est une vidéo HTML5 (`SeagateHomepageVideo_030326.mp4` ≈13,9 Mo en requête partielle 206 ; variante `The-Seagate-Hero-Video_Mobile.mp4` ≈10 Mo ; `autoplay muted loop playsinline`, `preload="metadata"`, **sans `poster`**). En headless elle reste `paused` : **le hero apparaît comme un aplat crème de 864 px avec le titre « Coastal Luxe Style Meets Private Club Living » en blanc quasi invisible**. Idem pour les heros vidéo d'About (vagues, ≈11 Mo) et Membership (nage sous-marine, ≈23 Mo). Cadrage, rythme et lisibilité réelle du titre blanc n'ont pas pu être vérifiés.
2. Le moteur Marriott (page hôtel et calendrier) renvoie « Access Denied » (Akamai) à l'automate : **l'étape 1 de réservation n'est pas vérifiable**. Seuls l'URL cible, `propertyCode=PBIDB` et l'ouverture en `target="_blank"` sont prouvés.
3. Les captures pleine page (`*-02-full.png`) contiennent un artefact : la navigation plein écran (`nav.fullscreen-nav`, `top:-900px`) est « cousue » dans la capture et fait apparaître un faux bloc de menu au milieu des pages. Ce n'est pas un défaut du site.
4. Les flux `flow-checkin-open`, `flow-guests-open`, `flow-room-click` ont échoué (timeout sur les inputs date natifs) : calendrier, sélecteur d'invités et accordéons « ROOM TYPES » / « DETAILS » n'ont pas été vus ouverts.
5. Pas de Lighthouse ; perf = mesures Playwright. Hovers mesurés par différence de styles calculés. Transitions de page et curseur tactile non observés.

---

## 1. Positionnement de marque

**Faits observés**
- Meta description : « a luxury resort offering a private beach and beach club, 18-hole golf, world-class dining, tennis, pickleball, spa, and club memberships ». Title : « The Seagate | Official Website | Delray Beach Hotels ».
- Titre hero (H2, 34 px, blanc, interlettrage 4,08 px) : « Coastal Luxe Style Meets Private Club Living ». Logo header : wordmark serif + lockup « Autograph Collection Hotels » ; logo footer différent : emblème coquillage/palmier + « Hotel, Golf & Beach Club ».
- Le menu plein écran met « Stay / Dine / Events & Experiences / Wellness » en grand bas de casse, puis sous un filet « MEMBERSHIP / ABOUT » en petites capitales. La page Membership (473 mots, la plus longue) décrit trois formules (Beach Club, Resort, Sport & Social). Sur la home, la section « AMID GREEN AND BLUE » (membership) précède les événements et le spa ; Contact liste Golf Club, Yacht Club, Racquets Club, Beach Club.
- JSON-LD `@type: Hotel` avec géolocalisation ; 157 chambres annoncées dans le premier paragraphe.
- Intertitres chambres (H3 16 px capitales) : « RARITY & CEREMONY », « SERENITY & TACTILITY », « OPENING TO THE HORIZON », « CALM AND BREATH ».

**Interprétation**
- Positionnement : resort côtier upper-upscale à double lecture — hôtel de 157 clés sous enseigne Marriott Autograph **et** club privé (plage, golf, raquettes, yacht club). La promesse centrale est l'accès temporaire à un univers normalement réservé aux membres.
- Cible (hypothèse) : voyageurs loisirs aisés de Floride / côte Est, couples et familles (enfants en piscine, « KIDS GOLF, TENNIS AND BEACH PROGRAMS »), organisateurs d'événements (250 invités), résidents prospects membres.
- Territoire émotionnel : calme, lumière, lenteur (« unhurried mornings », « slow your pace »). Personnalité posée, littéraire, légèrement cérémonieuse. Valeurs : héritage floridien (About « A Coastal Legacy », photo d'archive), design, hospitalité privée.
- Différence avec un site hôtelier générique : icônes coquillages pour désigner les catégories de chambres ; menu qui traite le membership comme une offre à part entière ; absence totale de prix, promotions et badges « meilleur tarif ».
- Cohérence : forte entre mots et images (palette crème/marine reprise dans textiles, parasols, fauteuils). Plus faible côté interactions : site quasi statique et réservation sortante vers marriott.com, ce qui rompt l'univers « club privé » au moment décisif.

**Enseignements réutilisables**
- Faire coexister séjour et adhésion dans un même menu en jouant sur deux niveaux typographiques plutôt que sur des sous-menus.
- Nommer chaque catégorie de chambre par une qualité ressentie, le nom technique restant un niveau en dessous.

---

## 2. Première impression (5 premières secondes)

**Faits observés**
- `home-00-initial.png` : header fixe 112 px `#f2f1ec`, hamburger à gauche, logo centré (≈270 px), bouton « RESERVE » `#203a4d` 119×40 px à droite. Sous le header, à droite, widget fixe (248×242 px, x=1192 y=112, fond `#f2f1ec` à 70 %, z 995) : CHECK IN / CHECK OUT (inputs date natifs, placeholder « Select date »), GUESTS (select 1–8), RESERVE (202×44, bordure 1 px `#203a4d`, texte `#0f2c3c`).
- Bannière CookieYes en bas à gauche (≈440×220 px, CUSTOMIZE / REJECT ALL / ACCEPT ALL en marine plein). Pas de pop-up, pas de préloader (`preloader []`), aucune erreur.
- Hero y=101→965 (864 px) ; H2 blanc aux deux tiers (y≈640), centré ; illisible en headless (blanc sur crème ≈1,06:1).
- Mobile (`home-mobile-01-hero.png`) : header 97 px, puis **barre RESERVE pleine largeur** (358×32 px, `#203a4d`, 16 px weight 300) ; hero 358×514 (ratio ≈0,7) ; titre sur deux lignes (23 px) à y≈830.

**Interprétation**
- On voit un cadre clair, un logo institutionnel et deux invitations à réserver avant d'avoir vu l'hôtel. En navigateur réel (hypothèse), la vidéo occupe tout l'espace sous le header, le widget se superpose avec sa transparence.
- On comprend « hôtel de bord de mer, réservable tout de suite ». Le message « coastal luxe × private club » arrive bas dans le hero, en bas du viewport sur mobile.
- On ressent sobriété et propreté, peu de chaleur tant que la vidéo ne joue pas : tout le pouvoir émotionnel de l'arrivée repose sur 13,9 Mo sans poster.
- Distractions : la bannière cookies (≈30 % de la largeur) et le doublon RESERVE ; aucune modale.
- Raison de continuer : le titre annonce un croisement que rien ne montre encore ; il faut scroller.

**Enseignements réutilisables**
- Toujours fournir un `poster` à une vidéo hero de 10–14 Mo ; sinon les premières secondes sont un aplat avec un titre blanc.
- Un widget en colonne verticale à droite du hero libère la composition centrale et peut rester fixe sur toutes les pages.

---

## 3. Direction artistique

**Faits observés**
- Palette (JSON) : fond `#f2f1ec` (1131 occurrences home), encre/boutons `#203a4d` (53 textes), footer `#163041` (45 fonds), texte bouton bordé `#0f2c3c`, gris-bleu `#627582` (labels du widget — hypothèse), blanc (52 textes sur marine), hover liens `#333638`. **Aucune couleur d'accent chaude** : l'orangé/doré vient uniquement des photos.
- Typographie : une seule famille, **Owners** (5 `.otf` auto-hébergés Light/Regular/Medium/Bold/Bold Italic, 788 Ko). Le logo est une image serif (hypothèse : police propriétaire non chargée en webfont). Aucune serif dans le texte.
- Échelle desktop : H1 48 px / 52,8 (1,1), weight 300, **capitales, interlettrage 13 px** ; H2 34 / 37,4, weight 300, bas de casse, 4,08 px ; H3 16 / 22,4, weight 400, capitales, 3 px ; H4 12 / 16,8, capitales, 2 px ; corps 16 / 22,4, weight 300, `#203a4d`, centré, 890 px de large ; boutons 12 px weight 500 capitales 3 px. Mobile : H1 32 / 35,2 (7 px), H2 20 / 22 (2,4 px), H3 14, H4 12 (3 px), corps 14 / 19,6, hero H2 23 px.
- Grille : conteneurs 1136 et 1340 px (home), 1144 (rooms, spa, contact), 890 (intros), 796 (texte chambre), 690 (dining, formulaire membership) ; marges 32 px desktop (images bleed 1376 px), 16 px mobile ; gouttières ≈16 px (445 + 16 + 915).
- Composants : **rayon 0 px partout** ; boutons pleins 119×40, 127×40 (DISCOVER), 219×40 (MAKE A RESERVATION), 365×40 (membership) ; bordé 202×44 (widget) ; liens soulignés 12 px (« DISCOVER », « RESERVE YOUR STAY », « DETAILS » 80×17) ; champs 202×46 bordure 1 px avec icône calendrier/chevron ; transitions 0,3 s.
- Iconographie : quatre packshots de coquillages sur fond crème (conque = Suites, spirale = Classic, pétoncle = Balcony View, dollar des sables = Pool View), 520×520 rendus 305 (home) et 528 rendus 344 (Rooms). Icônes sociales grises dans le menu. Pas d'illustration, de texture ni de motif hors photos.
- Ratios d'images : bannières 2,14–2,15 (2560×1196), paires 0,69 + 1,42, triptyques 0,75 (608×811), chambres 1,62 (2048×1264), carrés 1,0, mosaïque spa 1,08 / 1,12, cartes membership 0,85.
- Vidéos : 4 sur la home (2 heros + 2 vignettes 303×150 « palmiers » 14 Mo et « golf aérien » 32,9 Mo), 1 par hero About / Membership ; toutes sans poster, contrôles ni aria.
- Symétrie : tout centré, sauf modules 2 colonnes sur Rooms / Dining / Wellness / About (icône + texte gauche, photo droite, ou inverse).

| Token approximatif | Valeur |
|---|---|
| Fond principal | `#f2f1ec` |
| Encre / boutons / titres | `#203a4d` |
| Fond footer | `#163041` |
| Texte bouton bordé | `#0f2c3c` |
| Secondaire (labels, hover footer) | `#627582` |
| Hover liens | `#333638` |
| Famille | Owners 300 / 400 / 500 / 700 |
| H1 | 48 → 32 px, caps, ls 13 → 7 px, lh 1,1 |
| H2 | 34 → 20 px, ls 4,08 → 2,4 px |
| H3 / H4 | 16 / 12 px, caps, ls 3 / 2 px |
| Corps | 16 / 22,4 → 14 / 19,6, weight 300 |
| Largeur contenu | 1376 (bleed) / 1136–1144 / 890 (intro) / 690 |
| Marge / gouttière | 32 px (16 mobile) / ≈16 px |
| Rayon | 0 px |
| Boutons | 40 px plein, 44–46 widget, 32 barre mobile |
| Header | 112 px desktop, 97 mobile, fixe |
| Durées | 0,3 s (60 règles), 0,2 s (10), 0,4 s (5) ; aucun cubic-bezier |

**Interprétation**
- Trois décisions portent la DA : une encre sur un fond, une grotesque géométrique en graisse légère, des capitales très interlettrées pour les H1. L'effet « club » vient de cette retenue ; l'effet « côtier » vient uniquement des photos et des coquillages.
- Rayon 0 et filets 1 px donnent une rigueur éditoriale ; les boutons pleins marine sont les seuls aplats et se voient sans autre accent.
- Le vide est structurel : sections de texte de 218–344 px entre des blocs photo de 674 à 1302 px ; la page respire par alternance, pas par de grands blancs internes.
- Faiblesses : hero mobile bien pensé (portrait 0,7) mais titre blanc 23 px sur vidéo non vérifiable ; absence de seconde police alors que le logo serif en appelle une.

**Enseignements réutilisables**
- Un système bichrome tient un site entier si les photos apportent la chaleur ; les budgéter comme la couleur d'accent.
- « H1 capitales ultra-interlettrées weight 300 » + « H2 bas de casse 34 px » = deux registres (institutionnel / narratif) sans changer de police.
- Des objets packshot comme icônes de catégories rendent une grille mémorisable ; ils ne remplacent pas les photos, qui suivent immédiatement.

---

## 4. Architecture de la page d'accueil

Reconstruite à partir de `sections` (desktop 6944 px ; mobile 8797 px) et des captures pleine page.

| Position (y, h) | Section | Objectif | Contenu | Interaction | CTA | Émotion créée |
|---|---|---|---|---|---|---|
| 0–112 (fixe) | Header | Orientation + réservation | Hamburger, logo Autograph, RESERVE | Menu plein écran | RESERVE → marriott.com (nouvel onglet) | Cadre institutionnel |
| 112–354 (fixe, droite) | Widget booking-box | Conversion | CHECK IN / CHECK OUT / GUESTS / RESERVE | Dates natives, select 1–8 | RESERVE | Disponibilité immédiate |
| 101–965 (864) | Hero vidéo | Immersion | Vidéo muette + H2 blanc | Aucune (pas d'indicateur de scroll) | — | Attente |
| 965–1309 (344) | STAY | Annoncer les chambres | H1 + paragraphe (157 chambres) | — | DISCOVER (lien) | Réassurance factuelle |
| 1309–1743 (434) | Grille coquillages | Segmenter | 4 packshots + SUITES / CLASSIC / BALCONY VIEW / POOL VIEW | Hover texte → `#333638` | 4 liens | Curiosité, signature |
| 1743–3045 (1302) | Photo-grid chambres | Prouver | Tête de lit 2,14 + balcon 0,69 / salon 1,42 | — | — | Projection |
| 3045–3389 (344) | WHERE TASTE MEETS TABLE | Restauration | H1 + paragraphe (Mr. Seas, Bourbon Steak by Michael Mina) | — | DISCOVER | Appétit, caution chef |
| 3389–4063 (674) | Photo-grid dining | Prouver | Assiette 0,66 + steak/cocktails 1,36 | — | — | Gourmandise |
| 4063–4407 (344) | AMID GREEN AND BLUE | Membership | H1 + paragraphe (golf + plage) | — | DISCOVER | Exclusivité |
| 4407–4557 (150) | Bande vidéo | Ambiance | 2 vidéos 303×150 + 4 img | Autoplay muet | — | Rythme (si lu) |
| 4557–4775 (218) | PRIVATE EVENTS | Événementiel | H1 + paragraphe (250 invités) | — | aucun | Projection mariage |
| 4775–5360 (585) | Triptyque | Segmenter | 3 portraits 0,75 : WEDDINGS / GATHERINGS / CELEBRATIONS | Hover texte | 3 libellés | Émotion humaine |
| 5360–5657 (298) | BALANCE FROM INSIDE OUT | Spa / fitness | H1 + paragraphe | — | aucun | Détente |
| 5657–6631 (974) | Mosaïque spa | Prouver | 1,08 + 2 × 1,12 : SPA / YOGA & FITNESS / CLUB SERVICES | — | libellés | Corps, lumière du soir |
| 6631–6944 (312) | Footer `#163041` | Confiance / légal | Logo club, adresse, e-mail, tél., liens, Turnberry + Bonvoy | Hover → `#627582` | — | Appartenance |

**Logique narrative**
- Début : la vidéo doit accrocher seule (aucun texte d'accueil hors H2). L'offre devient concrète dès le deuxième écran (« STAY », 157 chambres) : le site commence par la chambre au lieu de faire monter le désir.
- Construction : chaque univers suit le même motif — H1 capitales → paragraphe centré 2–3 lignes → grille photo — répété cinq fois (Stay, Dine, Membership, Events, Wellness). Prévisible mais lisible.
- Preuve : aucune preuve sociale (avis, presse, récompenses) ; seules cautions : « Chef Michael Mina », Autograph, Turnberry, Bonvoy.
- Réservation : aucun CTA de réservation dans le corps ; tout repose sur header et widget fixes. Events et Wellness n'ont même pas de DISCOVER (`links 0`).
- Fin : le footer marine est le seul changement de fond ; pas de newsletter, pas de bloc « réservation directe ».
- Mobile : même ordre en colonne unique ; les 4 coquillages empilés font 1379 px, le triptyque 1287 px.

**Enseignements réutilisables**
- Un motif unique répété est facile à maintenir en CMS ; le casser au moins une fois avant 3000 px (ici la bande vidéo arrive à 4400 px).
- Prévoir une variante 2×2 des icônes de catégories sur mobile.

---

## 5. Scroll et storytelling

**Faits observés**
- Sonde de scroll (15 positions, 0–6044 px) : header toujours fixe, **aucun élément épinglé, aucune transform ni opacité en cours** (`tr 0 op 0` dès y=1295). `animAttrs` : aos / dataScroll / reveal / parallax / marquee / splitText / sticky = 0 ; horizontal = 1 (hypothèse : slider Slick des « ROOM TYPES »).
- CSS : 400 Ko, 2 keyframes (`spin`, `blink`, propres à Contact Form 7), 17 `clip-path`, 3 `position: sticky` inactifs, 0 `scroll-snap`, 0 `will-change`, 0 `scroll-timeline`.
- Un seul changement de fond (crème → marine au footer). Alternance stricte texte / grille sur la home ; alternance gauche/droite sur Dining et About.
- Longueurs : home 6944, dining 6465, membership 6968, rooms 4514, experiences 5432, spa 4266, about 4838, contact 1542 px.

**Interprétation**
- Storytelling purement éditorial : ni parallaxe, ni révélation, ni sticky, ni scroll horizontal actif. Le rythme vient des proportions d'images. Fonctions couvertes : orienter (titre centré → image large), expliquer (paragraphe court), marque (motif répété). Rien n'est dédié à l'émotion par le mouvement, hors vidéos.
- Les vidéos secondaires (14 et 32,9 Mo) rendues à 303×150 px ont un coût réseau démesuré pour leur taille (hypothèse : affichées plus grandes dans un slider en navigateur réel).
- L'envie de poursuivre tient à la qualité constante des photos, pas à une tension narrative : dès le deuxième écran on sait ce que l'on verra.

**Enseignements réutilisables**
- Sans animation de scroll, c'est la variation des ratios (2,14 → 0,69 + 1,42 → 0,75 ×3 → 1,08 + 1,12) qui crée le rythme.
- Ne pas confier le seul moment de mouvement à des vidéos de 33 Mo affichées en 300 px.

---

## 6. Animations et micro-interactions

| Animation | Déclencheur | Élément | Effet | Fonction | Risque UX |
|---|---|---|---|---|---|
| Arrivée de page | Chargement | Aucune (`preloader []`, `page-intro` opacité 1) | Aucun | — | Hero vide tant que la vidéo n'a pas décodé |
| Vidéo hero | Autoplay muet loop | `section.video-hero` 1376×864 / 358×514 | Lecture continue (non vérifiée) | Émotion | 13,9 + 10 Mo, pas de poster ni pause |
| Titres / images | Scroll | H1, photo-grid | Aucun (pas de reveal ; `lazy 0`) | — | Poids initial |
| Zoom photo | Hover | Cartes | Non détecté | — | — |
| Transition de page | Clic | — | Non observée (hypothèse : rechargement WordPress) | — | — |
| Curseur | — | `cursor: auto`, 0 élément custom | Aucun | — | — |
| Hover bouton plein | Hover | RESERVE 119×40 | `transition 0.3s`, changement non capturé | Feedback | Faible |
| Hover liens texte | Hover | SUITES, CLASSIC, WEDDINGS, RESERVE (widget) | `#203a4d` → `#333638` (`transition: all`) | Feedback | Quasi imperceptible |
| Hover liens footer | Hover | Careers, Press… | Blanc → `#627582` en 0,3 s | Feedback | 2,9:1 sur `#163041` |
| Carrousel / accordéon | Clic « ROOM TYPES » / « DETAILS » | Slick 1.8.1 + jQuery | Hypothèse : slider des 13 types | Expliquer | Contenu replié par défaut |
| Menu | Clic hamburger | `nav#fullscreenNav` 1440×900, `#f2f1ec`, depuis `top:-900px` | Glissement vertical (hypothèse) ; `body overflow hidden` mobile | Orientation | CONTACT invisible desktop 900 px |
| Vidéo plein écran | — | — | Pas de lightbox | — | — |
| Feedback formulaire | — | Aucun formulaire natif (CF7 chargé, `forms []`) | — | — | — |
| Reduced motion | `prefers-reduced-motion` | 1 règle : spinner CF7 | Rien pour vidéos ni transitions | — | Vidéos autoplay non coupées |

Durées détectées : 0,3 s (60), 0,2 s (10), 0,4 s (5), 0,15 / 0,25 / 0,35 s (3 chacune), 1 s, 2000 ms ; **aucun `cubic-bezier`** (easing `ease` par défaut, hypothèse) ; 43–57 éléments avec transition par page.

**Interprétation** : site sans motion design, par choix ou contrainte. Cela sert la vitesse de lecture et la robustesse, mais laisse toute la charge émotionnelle aux vidéos et prive les interactions clés (coquillages, cartes événements) d'un feedback visible : `#203a4d` → `#333638` est une variation de luminance de quelques pour cent.

**Enseignements** : si l'on renonce aux animations de scroll, garder au minimum un hover lisible (soulignement animé, zoom 1,03, inversion de bouton) et un poster par vidéo ; sinon la page paraît « figée » plutôt que « calme ».

---

## 7. Navigation et architecture de l'information

**Faits observés**
- Header fixe partout (112 / 97 px, z 1000) : hamburger, logo (lien home), RESERVE (`_blank` vers marriott.com).
- Menu plein écran (`home-05-menu-open.png`) : Stay / Dine / Events & Experiences / Wellness (≈34 px, espacés d'≈100 px), filet, MEMBERSHIP / ABOUT (16 px capitales), 4 icônes sociales. **À 900 px de haut, « CONTACT » n'apparaît pas dans la capture desktop** (lien présent dans le DOM à y=-131 ; hypothèse : rejeté sous la ligne de flottaison de l'overlay) ; visible sur mobile. Croix à la place du hamburger ; RESERVE reste visible menu ouvert.
- Hiérarchie : 4 univers + 2–3 pages institutionnelles + footer (Careers, Press, Sitemap, Privacy, Terms). Pas de sous-menu, fil d'Ariane, recherche ni langue (`hreflang []`).
- Infos essentielles : adresse, `info@seagatedelray.com`, téléphone dans chaque footer ; page Contact à 14 entrées (front desk, concierge, ventes, room service, 2 restaurants, 4 clubs, spa, membership, presse), sans formulaire.
- Widget de réservation fixe sur **toutes les pages desktop** ; **absent sur mobile** (`dateInputs []`), remplacé par la barre RESERVE.
- Étapes vers une offre : Home → Stay (1 clic) → « ROOM TYPES » (1 clic, révèle 13 types) → « RESERVE YOUR STAY » (1 clic, nouvel onglet marriott.com/rooms). Restauration : Dine → « MAKE A RESERVATION » (SevenRooms) pour Bourbon Steak ; les autres venues renvoient à un téléphone ou « DISCOVER ».

**Interprétation**
- IA plate et courte, adaptée à 8 pages ; en contrepartie, impossible d'atteindre une chambre précise depuis le menu ou de voir un tarif sans quitter le site.
- La navigation mobile est plus complète que la desktop (CONTACT), signe d'un overlay calibré pour des écrans plus hauts (hypothèse).
- Frustrations probables : nouvel onglet systématique, pas de « à partir de », widget desktop qui recouvre du contenu à droite (photo de suite sur Rooms, colonne de contacts sur Contact jusqu'à y≈354).

**Enseignements réutilisables**
- Séparer « univers » (grand, bas de casse) et « institutionnel » (petit, capitales) donne une hiérarchie sans sous-niveaux.
- Tester un widget fixe en colonne sur chaque gabarit interne : ici il masque du contenu utile.

---

## 8. Parcours de réservation et conversion

**Faits observés**
- Premier CTA : RESERVE header (y=36, 119×40, plein) et RESERVE widget (y=296, 202×44, bordé) — deux CTA above the fold desktop, un (358×32) sur mobile.
- Formulations : « RESERVE » (séjour), « RESERVE YOUR STAY » (liens 12 px sous chaque catégorie, ×4), « MAKE A RESERVATION » (restaurant), « DISCOVER », « DETAILS », « CONTACT US » (mailto ventes), « CONTACT US FOR MEMBERSHIP OPTIONS », « PURCHASE AN E-GIFT CARD », « EXPLORE OUR SERVICES ». La distinction découvrir / demander / réserver est nette.
- Dates et voyageurs : 2 inputs `type=date` natifs + `select` 1–8 (select2 chargé) ; pas de nombre de chambres, d'enfants ni de code promo. Le RESERVE du widget pointe sur `#`, l'URL Marriott étant construite par `themes/seagate/js/booking.js` (hypothèse).
- Chambres : page unique, 4 catégories, 13 types révélés par « ROOM TYPES » (Terrace / Venetian / Presidential suites ; Classic interior king studio, Classic king, Classic interior king ; ADA deluxe king with balcony, Deluxe queen with balcony, Deluxe king, Deluxe king with balcony, ADA deluxe queen with balcony ; Premium queen / king pool view), chacun avec une ligne « 1 KING BED — SLEEPS 2-4 » ou « 2 QUEEN BEDS — SLEEPS 4 ».
- Transparence : aucun prix, disponibilité, politique d'annulation, taxe ou resort fee. Réassurance : lockup Autograph, Turnberry et Bonvoy en footer, lien création de compte Bonvoy.
- Avis, preuve sociale, distinctions : **aucun** sur les 8 pages. Bénéfices réservation directe, offres, packages : **aucun** (pas de page Offers).
- Services additionnels : spa (e-gift card), restaurants (SevenRooms + téléphones), conciergerie (561-665-4990), événements (mailto SGSalesTeam@turnberry.com), membership (formulaire join.seagatedelray.com).
- Points de rupture : domaine tiers (marriott.com) ; nouvel onglet ; changement total d'identité (structurel, non observable ici) ; sur Membership, l'URL du CTA contient `?preview=yes` (lien de prévisualisation en production, hypothèse) ; `href="#"` du widget dépendant de JS.

**Interprétation**
- C'est un « brand site » : la conversion est assumée chez Marriott (Bonvoy, tarifs, disponibilités) et le site se concentre sur l'envie. Cohérent pour une franchise Autograph, mais sans aucun argument pour retenir la réservation en direct.
- Widget réduit à l'essentiel : lisible, mais sans compteur de chambres ni d'enfants alors que la cible inclut des familles.
- L'absence de preuve sociale est la lacune de conversion majeure : un visiteur qui ne connaît pas l'hôtel n'a que le mot « luxury » de la meta description.

**Enseignements réutilisables**
- Faire atterrir le lien de chaque catégorie directement sur la liste de chambres du moteur, pas sur sa home.
- Un widget à 3 champs est acceptable si le moteur reprend les valeurs ; vérifier qu'il n'a pas de `href="#"` inerte sans JS.

---

## 9. Pages chambres / propriétés

Il n'existe **pas de page détail par chambre** : tout est sur https://www.seagatedelray.com/rooms-suites/ (title « Rooms & Suites - Seagate », 252 mots).

**Faits observés — desktop** (`rooms-01-hero.png`, `rooms-02-full.png`)
- Pas de hero photo : H1 « COASTAL STAYS » (48 px, y≈190) + paragraphe 890 px (157 chambres, salles de bain d'inspiration spa, douches à l'italienne).
- Module `rooms-module` de 3415 px = 4 blocs de ≈874 px (y=348, 1221, 2095, 2969) : colonne gauche 344 px avec coquillage 344×344, H2 (« Suites », « Classic », « Balcony », « Pool View », 34 px) et H3 émotionnel (« RARITY & CEREMONY », 16 px capitales) ; à droite, photo 1032×637 (1,62 : salon de suite, tête de lit brodée, chambre deux lits avec balcon, chambre vue piscine) ; sous la photo, paragraphe 796 px aligné à gauche (2 lignes) terminé par le lien souligné « RESERVE YOUR STAY » ; puis « ROOM TYPES › » (144×40, 16 px capitales) qui déplie la liste des types (H3 nom + H4 lits / capacité).
- Ordre : icône → nom → promesse → photo → description sensorielle → CTA → technique replié. Après un divider de 193 px : H1 « IN-ROOM AMENITIES », 8 H4 12 px (Wi-Fi, douche, mini-bar, coffre, Nespresso, peignoirs, TV 65", balcons privés).
- Absents : prix, surface, galerie (1 photo par catégorie), plan, avis, chambres complémentaires, onglet vue/étage. Réassurance : mention ADA dans deux noms de types.
- Le widget fixe chevauche la photo de la suite entre y=112 et 354.

**Faits observés — mobile** (`flow-mobile-rooms-full.png`, ≈4773 px CSS)
- Même ordre en colonne : coquillage centré (≈120 px), H2 20 px, H3 14 px, photo pleine largeur (358 px, ratio ≈1,5), paragraphe 14 px avec « RESERVE YOUR STAY » en fin de paragraphe (cible ≈164×16 px), « ROOM TYPES › ». Les 4 blocs s'enchaînent sans séparation forte ; amenities en liste verticale de 8 lignes ; footer 756 px.

**Interprétation**
- La page vend quatre atmosphères plutôt que treize produits : bonne stratégie de désir (stillness, light, breath) mais tout le comparatif (surface, vue, lit, prix) est reporté sur marriott.com. Le site officiel n'apporte que le nombre de lits et la capacité.
- Une photo par catégorie : la projection repose sur sa qualité (lumière naturelle, textiles bleus), pas sur la profondeur (la salle de bain « spa-inspired » annoncée n'est jamais montrée).
- Mobile : la hiérarchie tient, mais les CTA sont des liens texte de 16 px de haut noyés dans le paragraphe.

**Enseignements réutilisables**
- L'ordre « icône → nom → promesse → photo → sensoriel → CTA → technique replié » est bon pour un site vitrine ; le compléter d'une galerie de 4–6 photos et d'une ligne de faits (surface, vue, lit, occupation) visible sans clic.
- Faire du CTA de chambre un bouton ≥ 44 px, surtout sur mobile.

---

## 10. Copywriting

**Faits observés**
- Volume : 208 à 473 mots par page (home 233, rooms 252, dining 341, experiences 247, wellness 293, about 390, membership 473, contact 208). Paragraphes de 2–4 lignes, centrés, 16 px weight 300.
- H1 à structure binaire ou verbale : « WHERE TASTE MEETS TABLE », « AMID GREEN AND BLUE », « BALANCE FROM INSIDE OUT », « DINE, SAVOR, REPEAT », « WELLNESS AND RENEWAL », « A COASTAL LEGACY ». Seuls « STAY », « CONTACT », « GETTING HERE » sont fonctionnels.
- H3 de chambres en diptyques abstraits (« RARITY & CEREMONY », « SERENITY & TACTILITY ») ; noms de restaurants en H2 bas de casse (« Mr. Seas », « The Gate »).
- Champ lexical : calme / lenteur (unhurried, stillness, settle, quiet, slow your pace, breathe easier), lumière et horizon (open to the sky, coastline, light), rituel et intention (ceremonial, intention, considered, curated, tailored, shaped by), textures (soft textures, thoughtful materials, calming palette).
- « Luxury » n'apparaît que dans la meta description et une fois sur Membership (« quiet luxury ») ; le luxe est suggéré par rare, private, exclusive, effortless, impeccable.
- Technique relégué aux H4 12 px capitales (amenities, lits, capacités, avantages membership) ; le corps ne contient que « 157 rooms and suites », « 250 guests », « 20 miles, approximately a 22-25 minute drive ».
- Prestation → expérience : la vue piscine devient « the movement of water brings a natural sense of balance » ; le balcon « the quiet pleasure of stepping into the light ».
- CTA : impératifs courts en capitales (RESERVE, DISCOVER, DETAILS, CONTACT US) et quelques CTA phrases (« Begin Your Planning Today », « Journey Through Our Spaces »).

**Interprétation**
- Ton littéraire, troisième personne, sans humour ; phrases binaires reliées par « and », « with », « where », cadence de balancement en accord avec le thème « rhythm of the coast ».
- Force : cohérence lexicale totale entre pages. Limite : abstraction élevée — un lecteur pressé n'apprend ni tarifs, ni vue exacte, ni horaires ; et rien n'explique concrètement ce que l'hôte non-membre obtient du club.

**Enseignements réutilisables**
- Mécanisme « titre binaire + paragraphe de balancement + liste technique en petites capitales » : le corps reste sensoriel, les faits restent scannables.
- Remplacer « luxury » par des adjectifs de rareté et de calme est transférable.

---

## 11. Photographie et vidéo

**Faits observés**
- Volume : 30 images home (16 jpg, 12 png, 1 svg), 14 Rooms, 22 Dining, 18 Experiences. Jpg jusqu'à 3,27 Mo (branzino), 2,78 Mo (steak & cocktails), 2,57 Mo (salon de suite), 2,44 Mo (chambre queen balcon), 2,38 Mo (yoga plage). Aucun WebP/AVIF, `srcset` sur 3 images, `loading="lazy"` sur 0.
- Types de plans : intérieurs de chambres en lumière naturelle avec ciel par les baies (salon à plafond marine, tête de lit brodée, balcon aux fauteuils cordés bleus) ; packshots zénithaux de coquillages ; natures mortes culinaires vues de dessus (assiette, steak, cocktails ambrés) ; portraits serrés (femme au chapeau de dos entre deux parasols rayés, yogi mains jointes, mère et enfant en piscine, couple sur la plage, main + flûte devant l'océan) ; vues aériennes (padel, golf, piscine du beach club) ; couchers de soleil (silhouettes en course) ; photo d'archive délavée (pont, van VW) sur About.
- Lumière naturelle, chaude en fin de journée pour les scènes de vie, claire pour les chambres, contrastée pour la food. Couleurs bleu marine / crème / bois / sable, accents corail-ambre venant des plats.
- Présence humaine forte sur Experiences, Wellness, Membership ; nulle sur Rooms ; partielle sur Dining (mains, femme au café).
- Vidéos : hero home (non vu), About « ocean waves crashing » (≈11 Mo), Membership « pool underwater swim » (≈23 Mo), vignettes « palm trees ocean breeze » (14 Mo) et « golf course aerial » (32,9 Mo). Toutes en boucle muette.
- Proportion estimée home : ≈45 % lieu, ≈40 % expérience humaine, ≈15 % signes (coquillages).

**Interprétation**
- La photographie fait le travail que la DA graphique refuse : couleur, chaleur, corps, destination. La cohérence (mêmes bleus dans textiles, parasols, fauteuils, plafonds) suggère une charte appliquée jusqu'à l'ameublement.
- Point faible technique : jpg de 2–3 Mo non lazy-loadés, sans variantes responsives, servis aussi au mobile (9,99 Mo d'images sur la home mobile).
- Les vidéos (noms de fichiers) racontent la destination (vagues, palmiers, golf, piscine), pas le service : ambiance sans narration (hypothèse).

**Shot list pour reproduire ce niveau**
1. Vidéo hero 16:9 **et** 9:16, 10–15 s, muette (arrivée, eau, intérieur) + poster JPEG.
2. Vidéo d'ambiance courte (vagues / végétation) pour « À propos », ≤ 8 Mo.
3. 4 packshots « objets signatures » en vue zénithale sur le fond du site, 1:1, ≥ 1000 px.
4. Par catégorie de chambre : 1 photo 1,6:1 en lumière naturelle avec vue ; idéalement 4–6 de plus (salle de bain, balcon, détail textile, vue).
5. Bannière 2,14:1 « détail matière » (tête de lit) + paire portrait 0,69 / paysage 1,42 (balcon / salon).
6. Restauration : plat vu de dessus (0,66), table dressée avec cocktails (1,36), cocktail seul (0,7), plat signature (1,43), scène client (café + croissant, burger tenu).
7. Événements : triptyque 0,75 (couple sur la plage, détail déco, main + flûte) ; arche de cérémonie face mer (1,07), tables sous tente sur golf, terrasse restaurant (1,11).
8. Bien-être : portrait de dos entre deux parasols (1,77), massage aux pierres chaudes (0,84), aériennes des courts et de la piscine (0,95).
9. Scènes de vie au coucher du soleil (silhouettes, famille en piscine), cible 300 Ko en WebP.
10. 1 photo d'archive pour l'héritage ; vue aérienne des fairways au soleil rasant ; façade du club-house avec palmiers.

---

## 12. Mobile (390×844)

**Faits observés**
- Header 97 px fixe ; sous le logo, barre « RESERVE » 358×32 px, `#203a4d`, 16 px weight 300 — **32 px, sous les 44 px recommandés**. Pas de widget de dates (`dateInputs []`) ; clic direct vers le calendrier Marriott.
- Hero 358×514 (0,7), variante mobile 10 Mo chargée… **mais la vidéo desktop de 13,9 Mo est aussi demandée** (videosNet mobile : 13 892 + 9 961 + 32 861 + 13 978 Ko = 70,7 Mo de média ; 147 requêtes, 83,8 Mo au total).
- Titres : H1 32 px / 35,2, interlettrage 7 px (2 lignes) ; hero H2 23 px ; corps 14 / 19,6 ; H4 12 px capitales 3 px (listes membership de 10–13 lignes).
- Rythme : home 8797 px (×1,27 vs desktop) ; coquillages empilés (1379 px), triptyque 1287 px, footer 756 px.
- Menu plein écran 390×844 avec CONTACT et icônes sociales 40 px ; `body overflow: hidden` à l'ouverture.
- Boutons : RESERVE header 119×32 (également dans le DOM), CONTACT US FOR MEMBERSHIP OPTIONS 358×40 / 350×40, liens « DISCOVER » / « RESERVE YOUR STAY » 12 px (~16 px de haut).
- Perf : TTFB 473 ms, FCP 1036 ms, DOMContentLoaded 1086 ms, load 1238 ms, 136 ressources ; images 9,99 Mo (39), scripts 2,3 Mo (38), fontes 394 Ko (5). Mêmes jpg 2–3 Mo qu'en desktop.
- Animations : identiques (aucune). Lisibilité : corps 14 px marine sur crème (≈10,5:1) confortable ; H4 12 px denses sur Membership.

**Interprétation**
- Réduction fidèle et propre, avec une bonne idée (barre RESERVE sous le logo) mal calibrée (32 px). Supprimer le widget simplifie mais envoie vers Marriott sans pré-remplissage.
- Le double chargement des heros et des vignettes (≈70 Mo potentiels sur cellulaire, sans poster ni lazy) est le problème mobile le plus coûteux.
- Frictions de parcours : CTA de chambres en lien 12 px et colonne de coquillages de 1379 px.

**Enseignements réutilisables**
- Garder la barre CTA pleine largeur sous le logo, à 44–48 px, sticky au scroll.
- Une seule source vidéo par breakpoint (`<source media>` ou injection JS) et un poster ; jamais deux `<video autoplay>` dans le DOM.

---

## 13. Performance, accessibilité, SEO

**Performance**
- Home desktop : TTFB 270 ms, FCP 968 ms, DOMContentLoaded 1084 ms, load 1632 ms ; 278 requêtes, 164,6 Mo transférés (media 138 Mo sur 8 requêtes partielles — chaque vidéo demandée deux fois ; images 20,4 Mo / 78 req ; scripts 4,57 Mo / 73 ; CSS 678 Ko / 16 ; fontes 788 Ko / 10).
- Autres pages : Rooms 22,5 Mo (images 16,4), Dining 39,8 Mo (images 33,7, 66 req), Experiences 27,3, Wellness 22,7, About 46,6 (vidéo 21,9), Membership 77,6 (vidéo 46), Contact 5,3 Mo. TTFB 418–652 ms, FCP 1076–1252 ms.
- Tiers : bat.bing.com (20), google.com (20), googletagmanager (16), cookieyes (14), jsdelivr (10 : Slick + select2), doubleclick (15), google-analytics (8), pinterest (12), facebook (14), googleadservices (4). Libs : WordPress, jQuery 3.7.1 + migrate, Slick 1.8.1, select2 4.1.0-rc.0, Contact Form 7 6.1.7, GA, Facebook Pixel.
- Lazy loading : 0 image. Stabilité : pas de préloader ni reflow détecté (sections à hauteur fixe), mais jpg sans dimensions responsives et vidéo sans poster sont des sources probables de LCP/CLS dégradés (hypothèse ; LCP non mesuré).

**Accessibilité**
- Landmarks : header 1, nav 2, footer 1, **main 0** ; pas de skip link ; `outline: none` sur 54–81 éléments par page sans style de focus alternatif détecté (hypothèse : focus invisible) ; `tabindex="-1"` 2–5 ; 3 iframes sans titre (Floodlight) ; `missingAlt` 0, `emptyAlt` 2–3 (logos), alts parfois imprécis (« Photo of shell » ×4, « Resport » [sic]).
- Contrastes estimés : `#203a4d` sur `#f2f1ec` ≈ **10,5:1** ; blanc sur `#163041` ≈ 13,7:1 ; blanc sur `#203a4d` ≈ 10:1 ; `#627582` sur `#f2f1ec` ≈ **4,2:1** (labels 12 px du widget, sous 4,5:1) ; `#627582` sur `#163041` ≈ **2,9:1** (hover footer) ; H2 blanc sur vidéo non mesurable, illisible sur fallback crème.
- Formulaires : widget avec labels visibles mais association `label/for` non vérifiée ; Contact sans formulaire ; membership externalisé.
- Vidéos autoplay sans pause, piste ni aria. `prefers-reduced-motion` : 1 règle (spinner CF7), rien pour vidéos ou transitions.

**SEO**
- Title 55 caractères, description 165, `robots` index/follow `max-image-preview:large`, `og:title` / `og:description` présents, **pas d'`og:image` ni `twitter:*`** dans les meta relevées.
- Canonical incohérent : home `https://seagatedelray.com/` (sans www) pour une URL servie en www ; Contact `https://seagatedelray.com/contact` (sans www ni slash) ; les autres pages en www avec slash. Pas de hreflang (monolingue). JSON-LD `Hotel` (nom, géo, téléphone) + graphe `WebPage` (hypothèse : plugin SEO type Yoast).
- Titres : **5 H1 sur la home**, 2–4 sur les pages internes ; le titre hero est un H2. Contenu indexable 208–473 mots ; 13 types de chambres dans le DOM mais repliés ; titles internes génériques (« Dining - Seagate ») sauf Contact.

**Interprétation**
- L'équilibre penche vers l'immersion : 138 Mo de média potentiels, 0 lazy, jpg 2–3 Mo. TTFB et FCP corrects parce que le HTML est léger ; le coût arrive sur le LCP et la bande passante.
- La pile publicitaire (Bing, Google Ads, Floodlight, Pinterest, Meta) pèse ≈73 scripts et 3 iframes sans titre : disproportionné pour un site vitrine.
- Contrastes principaux excellents, mais focus, `main`, vidéos sans contrôle et gris à 4,2:1 sont des non-conformités AA probables. SEO : H1 multiples, canonicals mal alignés et og:image absent sont faciles à corriger ; le texte est trop court pour se positionner hors marque.

**Enseignements réutilisables**
- Une paire encre/fond ≥ 10:1 règle 80 % des contrastes ; ne pas la dégrader par des gris sur les petits libellés.
- Pile média luxe = poster, `preload="none"` hors viewport, une source par breakpoint, WebP + `srcset`, lazy sous la ligne de flottaison.
- Un H1 par page (le hero), canonical strictement égal à l'URL servie, og:image obligatoire.

---

## 14. Conclusion

**15 meilleurs éléments**
1. Système bichrome `#f2f1ec` / `#203a4d` appliqué sans exception à 8 pages, boutons compris.
2. Contraste ≈10,5:1 sur tout le corps de texte.
3. Grille de 4 coquillages packshot (520×520) comme signature des catégories, reprise sur Rooms.
4. H1 48 px capitales interlettrées 13 px weight 300, registre immédiatement reconnaissable.
5. Menu plein écran à deux niveaux typographiques sans sous-menus.
6. Widget de réservation fixe en colonne (248×242, 70 % d'opacité) sur toutes les pages desktop.
7. Barre « RESERVE » pleine largeur sous le logo sur mobile.
8. Bloc chambre : icône → nom → promesse → photo → sensoriel → CTA → technique replié.
9. Intertitres émotionnels doublés d'un nom technique et d'une ligne lits/capacité.
10. Champ lexical unique (calm, rhythm, coastal, considered) sans le mot « luxury ».
11. Photographie alignée sur la palette (textiles, parasols, plafonds marine), forte présence humaine sur Events / Wellness.
12. Variation des ratios d'images qui crée le rythme sans animation.
13. Liens « RESERVE YOUR STAY » qui atterrissent sur la liste de chambres du moteur (`/rooms/`).
14. Page About avec photo d'archive et module « Getting Here » à 4 aéroports.
15. Page Contact exhaustive (14 lignes, chaque venue et club avec son numéro).

**5 faiblesses / limites**
1. Poids média : 138 Mo de vidéos potentiels sur la home (4 `<video autoplay>`, sources desktop **et** mobile chargées sur les deux breakpoints), jpg 2–3 Mo, 0 lazy, 3 `srcset` / 30 images.
2. Aucune preuve sociale, offre ou bénéfice direct : conversion entièrement déléguée à marriott.com en nouvel onglet.
3. Aucun motion design ni feedback visible ; vidéos hero sans poster : premières secondes vides si la vidéo tarde.
4. Accessibilité : `main` absent, 54+ `outline:none`, vidéos sans pause, labels 4,2:1, hover footer 2,9:1, iframes sans titre, CONTACT invisible dans le menu desktop à 900 px.
5. Chambres sans galerie, surface ni prix ; CTA de chambre en lien 12–16 px ; barre mobile de 32 px ; lien membership `?preview=yes`.

**10 principes réutilisables**
1. Une encre, un fond, une police : la variété vient des graisses, casses et interlettrages.
2. Les photos sont la couleur d'accent ; les budgéter et les compresser comme telles.
3. Un objet-signature par catégorie, en packshot sur le fond du site.
4. Un motif de section répété est acceptable si les ratios d'images changent à chaque fois.
5. Menu plein écran : univers en grand, institutionnel en petit, CTA de réservation visible menu ouvert.
6. Widget fixe minimal (dates + invités) en colonne, testé sur chaque gabarit interne.
7. Sur mobile, CTA pleine largeur sous le logo, ≥ 44 px, sticky.
8. Nommer l'émotion avant le produit, en gardant le produit à un clic et indexable.
9. Jamais de vidéo autoplay sans poster, source par breakpoint et règle `prefers-reduced-motion`.
10. Un H1, canonical = URL, og:image, alts descriptifs non répétés.

**Éléments propres à la marque à ne PAS copier**
- Les coquillages (conque, spirale, pétoncle, dollar des sables) et l'équivalence coquillage = catégorie de chambre.
- « Coastal Luxe Style Meets Private Club Living » et les diptyques « Rarity & Ceremony », « Serenity & Tactility », « Opening to the Horizon », « Calm and Breath ».
- Les H1 « Where Taste Meets Table », « Amid Green and Blue », « Balance From Inside Out », « Dine, Savor, Repeat ».
- Le wordmark serif et son lockup Autograph ; le logo footer « Hotel, Golf & Beach Club » avec emblème.
- Les trois formules de membership et leurs listes d'avantages ; la police Owners (licence commerciale, hypothèse).

**Notes /10**
- **Branding : 8/10.** Cohérence lexicale et chromatique sur 8 pages ; signature coquillages ; hôtel + club lisible dans le menu et la home. Retenu : le club n'est jamais expliqué pour l'hôte non-membre ; l'identité disparaît au moment de réserver.
- **Direction artistique : 8/10.** Tokens rigoureux (rayon 0, 1 police, 2 couleurs, 10,5:1), échelle 48/34/16/12 claire, photos alignées sur la palette. Retenu : hero illisible sans vidéo, pas de contrepoint typographique hors logo, widget qui chevauche du contenu.
- **Animations : 3/10.** Aucune animation de scroll, 0 cubic-bezier, hover imperceptible (`#203a4d` → `#333638`), vidéos sans poster ni pause, 1 règle reduced-motion. Ce qui sauve la note : aucun bug ni jank, transitions 0,3 s homogènes.
- **UX : 6/10.** IA plate et lisible, menu efficace, contact exhaustif, chambres structurées. Retenu : CONTACT absent du menu desktop 900 px, CTA chambres en liens texte, pas de galerie, `main` absent, focus invisible, contenu recouvert par le widget.
- **Conversion : 4/10.** Deux CTA above the fold, liens directs vers `/rooms/` Marriott, formulations différenciées. Retenu : 0 avis, 0 offre, 0 argument direct, 0 prix, sortie en nouvel onglet vers un domaine tiers, moteur non vérifiable, lien `preview=yes`.
- **Mobile : 5/10.** Hero portrait dédié, barre RESERVE pleine largeur, menu complet, corps 14 px lisible. Retenu : barre de 32 px, ≈70 Mo de média (sources desktop + mobile), jpg non responsives, colonne d'icônes de 1379 px, CTA chambres 16 px de haut.

**Note globale : 5,7/10** (moyenne simple 5,67). Vitrine de marque très maîtrisée graphiquement et éditorialement — l'un des systèmes bichromes les plus cohérents du corpus — qui s'arrête là où commence la conversion : pas de preuve, pas d'offre, pas de moteur intégré, et une dette média (138 Mo potentiels, 0 lazy) qui contredit la promesse de calme dès le premier écran si la vidéo tarde. Pour la phase comparative : référence « DA minimale + copy sensoriel », pas référence « parcours de réservation ».

---

## Observations clés à conserver pour la phase comparative

- Palette 2 couleurs : fond `#f2f1ec` (1131 occ. home), encre/boutons `#203a4d`, footer `#163041` ; contraste corps ≈10,5:1 ; rayon 0 px sur 100 % des composants.
- Une seule famille (Owners, 5 `.otf`, 788 Ko) ; H1 48 px capitales interlettrage 13 px weight 300 → 32 px / 7 px mobile ; H2 34 → 20 px ; corps 16/22,4 → 14/19,6 weight 300.
- Header fixe 112 px (97 mobile) : hamburger / logo centré / RESERVE 119×40 ; widget fixe 248×242 à 70 % d'opacité sur toutes les pages desktop, absent sur mobile (barre 358×32).
- Menu plein écran crème : 4 univers en 34 px bas de casse + MEMBERSHIP/ABOUT en capitales ; CONTACT visible sur mobile seulement à 900 px de haut.
- Home 6944 px desktop / 8797 mobile, 5 H1 de section ; motif « titre / 2 lignes / grille » ×5 ; un seul changement de fond (footer).
- Hero vidéo 864 px sans poster : 13,9 Mo desktop + 10 Mo mobile, **les deux chargées sur les deux breakpoints** ; vignettes 14 Mo et 32,9 Mo rendues 303×150 ; media home = 138 Mo desktop / 70,7 Mo mobile.
- 0 image lazy, 3 `srcset` / 30 images, jpg jusqu'à 3,27 Mo ; Dining 33,7 Mo d'images ; Membership 77,6 Mo au total.
- TTFB 270–652 ms, FCP 968–1252 ms, load 1,1–1,6 s ; 228–278 requêtes ; 73 scripts (4,57 Mo) dont Bing/Google Ads/Floodlight/Pinterest/Meta ; WordPress, jQuery 3.7.1, Slick 1.8.1, select2, CF7, CookieYes.
- Aucune animation de scroll (aos/parallax/sticky/reveal = 0), 0 cubic-bezier, 60 transitions à 0,3 s, hover `#203a4d` → `#333638`, footer blanc → `#627582` (2,9:1) ; 1 règle reduced-motion (CF7).
- Rooms : page unique, 4 catégories (coquillage 344×344 + photo 1032×637 ratio 1,62 + H3 émotionnel + « RESERVE YOUR STAY » lien 12 px + « ROOM TYPES » repliant 13 types avec lits/capacité) ; 0 prix, 0 galerie, 0 surface ; 8 amenities H4 12 px.
- Conversion : RESERVE → marriott.com `availabilityCalendar.mi?propertyCode=PBIDB` en `_blank` (Access Denied pour l'automate) ; « RESERVE YOUR STAY » → `/rooms/` Marriott ; Bourbon Steak → SevenRooms ; membership → join.seagatedelray.com `?preview=yes` ; 0 avis, 0 offre, 0 argument direct.
- Copy : 208–473 mots/page ; H1 binaires ; diptyques de chambre ; « luxury » absent du corps ; technique en H4 12 px capitales.
- Photo : jpg 2–3 Mo, ratios 2,14 / 0,69+1,42 / 0,75×3 / 1,62 / 1,0 ; humains sur Events-Wellness-Membership, aucun sur Rooms ; 4 packshots coquillages.
- A11y : `main` 0, skip link non, `outline:none` 54–81, 3 iframes sans titre, alt « Photo of shell » ×4, labels widget ≈4,2:1, vidéos autoplay sans pause.
- SEO : title 55 c., description 165 c., JSON-LD Hotel + géo, og:image absent, canonical home sans www (≠ URL servie), Contact sans slash, hreflang 0, 5 H1 home.
