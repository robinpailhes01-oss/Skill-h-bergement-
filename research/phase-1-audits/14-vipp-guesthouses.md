# Fiche d'audit — Vipp Guesthouses (vipp.com, marque de design danoise qui héberge)

## 0. En-tête

- **Nom** : Vipp Guesthouses — programme d'hébergement de Vipp A/S (Copenhague), marque de design (poubelle à pédale de 1939, cuisines, mobilier, bains). Clé : `vipp`.
- **URL de départ** : https://vipp.com/en/world-of-vipp/our-guesthouses — **Date** : 2026-09-04 (captures 17:40 → 18:00 UTC).
- **Environnement** : Chromium headless via Playwright, 1440×900 (desktop) et 390×844 DPR 2 (mobile).

| Label | URL | Desktop | Mobile |
|---|---|---|---|
| home (liste des guesthouses) | https://vipp.com/en/world-of-vipp/our-guesthouses | oui | oui |
| rooms (filtre « All ») | https://vipp.com/en/world-of-vipp/our-guesthouses?cat=all | oui (même gabarit) | non (fichier absent) |
| room-detail (filtre « Solitude ») | https://vipp.com/en/world-of-vipp/our-guesthouses?cat=Solitude | oui | oui |
| spa (= page récit « Vipp Guesthouses », ancien site) | https://vipp.com/world-of-vipp/inspiration/spaces/vipp-guesthouses/ | oui | non |
| about | doublon de rooms | oui | non |
| contact | https://vipp.com/en/contact | oui | non |
| guesthouse-detail (Vipp Tunnel) | https://vipp.com/en/world-of-vipp/our-guesthouses/vipp-tunnel | oui | oui |
| guesthouse-farmhouse | https://vipp.com/en/world-of-vipp/our-guesthouses/vipp-farmhouse | oui | oui |
| story (heritage) | https://vipp.com/en/world-of-vipp/our-story/heritage/from-marie-to-moma-and-beyond | oui | oui |
| shop-home (boutique) | https://vipp.com/en | oui | oui |
| booking (sonde CTA, page Tunnel) | cible : https://checkout.lodgify.com/tunneltasmania/647164/reservation/ | page rechargée, moteur non ouvert | — |

**Limites de l'observation**
1. Vidéos (`autoplay muted loop playsinline preload="auto"`, poster WebP) vues `paused: false` mais rendues en image fixe : montage du film de hero et changement de légende (« Salaca River, Latvia » seule vue) non vérifiables.
2. Menu mobile non capturé (`no burger found`) ; l'icône ≡ 48×48 px existe sur les captures (hypothèse : bouton sans nom accessible).
3. La sonde « booking » de la liste a suivi « Book a kitchen meeting » (footer) → `configurator.vipp.com` : pas un parcours d'hébergement. Relancée sur Vipp Tunnel, elle n'a pas cliqué « Book now » (`no obvious booking CTA visible`) : **l'étape 1 de Lodgify n'est pas capturée** ; seuls URL, `target` et libellé sont prouvés.
4. Un pop-up Sleeknote (« Let's keep in touch », 404×680 px, image 1,6 Mo) s'ouvre au 2e viewport desktop et reste fixe sur toutes les captures de scroll : comportement réel, mais il masque la colonne droite des textes.
5. Pas de Lighthouse ; perf = Playwright, avec forte variance entre chargements (FCP 3,1 s sur `home`, 6,6 s sur `rooms`). Hovers par différence de styles calculés ; transitions de page, curseur tactile, smooth scroll non vérifiés.
6. Libs (`gsap`, `ScrollTrigger`, `Lenis`, `webflow`, `lottie`) : négatives partout. Scripts `/_next/static/chunks/app/layout-…js` et polices `__vippNeue_cb73ae` (format `next/font`) → **Next.js App Router en hypothèse forte** ; médias sur `media.umbraco.io` → hypothèse Umbraco Heartcore.

---

## 1. Positionnement de marque

**Faits observés**
- Header de la boutique : « Products / Kitchens / Guesthouses / World of Vipp / Professionals », loupe, panier. « Guesthouses » est au même rang que « Kitchens ».
- Hero scindé : à gauche vue drone d'une maison en bois dans une pinède (Salaca River, Lettonie) ; à droite un îlot de cuisine Vipp anthracite avec torchon. Titre blanc « Vipp Guesthouses » (sans-serif ≈48 px, hypothèse) et sous-titre italique serif « Salaca River, Latvia ».
- Trois énoncés serif sable (43,2 px, `#ccbca2`, colonne droite) : « Vipp Guesthouses are unparalleled accommodations… », « Curated and furnished exclusively by Vipp… », « Not a hotel. Not a showroom. Not like any place you've ever stayed. » 280 mots sur la page.
- 15 maisons nommées « Vipp + typologie » (Pavilion, Montafon Haus, Lofoten, Cold Hawaii, Tunnel, Townhouse, Todos Santos, Salaca River, Shelter, Farmhouse, Palazzo Monti « Pop-up », Loft, Pencil Case, Chimney House) + un partenaire (« The Bolder », Lysefjorden). 11 pays. Filtres « All / Solitude / Tropical / Urban » (`?cat=`).
- Citation du dirigeant sur image plein cadre (Cold Hawaii) : « What started as a business idea gone wrong paved the way for 'Vipp Guesthouses'… » — « KASPER EGELUND, 3rd GENERATION VIPP OWNER » ; lien vers la page récit (866 mots) : eyebrow « ONE ROOM WONDERS », 2014, « a 55 sqm steel pod on the edge of a Swedish lake » (Vipp Shelter), échec de la vente de maisons « like the company's iconic bin », bascule vers la location ; intertitres « Where it all began », « One of a kind destination », « An upscaled product experience ».
- Bloc « Vipp Residences » (copropriété, lien externe `vippresidences.com`). Footer boutique : « Book a kitchen meeting », configurateurs cuisine/canapé/armoire, pCon, Image bank, Trade program, Store locator. Contact : accordéon « Guesthouses », e-mail dédié `stay@vipp.com`, showrooms « Vipp Spaces ».
- Page Tunnel : 6 liens vers des fiches produit dans le récit ; home boutique : module « Vipp Guesthouses — Discover our collection » (4 vignettes) + film Upstate plein écran.

**Interprétation**
- Architecture de marque : une marque produit avec une **ligne d'hébergement intégrée au même site, au même header et au même panier** ; pas de sous-marque (seule la copropriété a son domaine). Les maisons sont nommées comme des objets de collection, au même titre que « Open-Air Outdoor Collection » dans le méga-menu.
- Le produit devient hébergement par le récit (Shelter conçu pour être vendu, invendu, loué) et par la formule « an upscaled product experience » ; le hero scindé (paysage | cuisine) en est la traduction visuelle.
- Promesse : dormir dans un showroom habité qui n'en est pas un ; la triple négation est le pivot. Cible (hypothèse) : clientèle design/architecture déjà exposée à la marque via la boutique ou les prescripteurs.
- Gamme perçue haute, démontrée par l'architecture et les auteurs (photographes dans les `alt` : Eric Petschek, Richard Gaston, Rasmus Hjortshøj ; « Vipp x Studio KO ») plutôt que par le vocabulaire hôtelier ; aucun prix, étoile ou label sur la liste.
- Territoire : isolement, matière brute, heure bleue (« Solitude » est une catégorie). Personnalité sobre, factuelle, auto-ironique (« business idea gone wrong »).
- Différence avec un site hôtelier : pas de moteur, pas de « Book » persistant, pas de sections chambres/spa/restaurant, panier affiché. Cohérence forte entre mots, images et navigation-catalogue ; plus faible avec le footer et le pop-up, qui parlent cuisine.

**Enseignements réutilisables**
- « Marque + typologie + lieu » crée une collection lisible sans sous-marque ; une catégorisation par humeur remplace celle par nombre de chambres.
- Raconter l'origine comme un échec réorienté est une preuve d'authenticité qu'un manifeste ne fournit pas.

---

## 2. Première impression (5 premières secondes)

**Faits observés**
- `home-00-initial.png` : modale Cookiebot centrée (≈900×390 px, « Customize » bordure noire / « Allow all cookies » noir, 391×52 px) sur voile noir. Pas de préloader (`.main-navbar_curtain` fixe à opacité 0 : hypothèse rideau de transition).
- `home-01-hero.png` : barre blanche 44 px, logo « vipp » bas de casse (≈62×20 px), cinq liens 17 px, loupe, sac. Hero 856 px (44→900) en deux moitiés de 720 px. Titre centré à y≈470. **Aucun CTA** ; premier élément cliquable après le header : filtre « All » à y≈1 345.
- Hero `position: fixed`, z-index −1 : le bloc `#222325` glisse par-dessus (`home-sweep-01.png`).
- Mobile : header 48 px (logo, loupe, sac, ≡), hero 796 px scindé (cuisine sur les 2/3 droits), titre ≈40 px, sous-titre ≈26 px.
- 2e viewport desktop : pastille Sleeknote (330×54 px) puis panneau complet au 9e palier.

**Interprétation**
- On comprend « Vipp » et « Guesthouses » en une seconde, le concept (maison isolée + cuisine Vipp) en trois ; la légende de lieu en italique dit qu'il s'agit d'une vraie adresse. Le panier signale immédiatement une marque produit.
- Absence de CTA : pas de conversion immédiate visée ; la raison de continuer est la curiosité pour une liste que le hero n'annonce pas.
- Distractions : deux couches successives (Cookiebot, Sleeknote), la seconde persistante et posée sur la colonne de texte d'une page de 280 mots.

**Enseignements réutilisables**
- Un hero scindé « lieu | objet » raconte un positionnement hybride sans un mot ; un sous-titre de lieu en italique serif distingue « quoi » et « où ».
- À éviter : superposer un pop-up fixe à la colonne éditoriale.

---

## 3. Direction artistique

**Faits observés**
- Fonds : `#ffffff` (header, footer, section citation), `#222325` (corps de la liste, ≈9 300 px), `#000000` (arrière-plan hero), `#f4f3ec` (page récit), `#d6d0c5` (fiche « Information » des maisons), `#804a2e` (bloc Residences, boutique).
- Tokens CSS : `--primary-dark: 13,13,13`, `--primary-alto-gray: 214,214,214`, `--primary-silk: 186,178,168` (#bab2a8), `--primary-swirl: 214,208,197` (#d6d0c5), `--primary-pampas: 244,243,236`, `--invalid-color: #e42525`, `--primary-container-padding: 22px` (9 px sous 833 px).
- Textes sur sombre : `#ccbca2` (énoncés), `#bab2a8` (libellés de cartes, filtres inactifs, eyebrows), `#ffffff` (filtre actif, citations, corps des maisons). Sur clair : `#000000` / `#0d0d0d`.
- Polices : `__vippNeue_cb73ae` (`VippNeue-Regular.otf`, `VippNeue-DemiBold.otf`, 400/600/700), grotesque propriétaire (hypothèse : dessin exclusif) ; `ivypresto-headline` et `ivypresto-text` 400 + italique via Typekit ; `Arial` sur « Subscribe », « Country: US » et **« Book now »**.
- Échelle desktop : 43,2 px (énoncés serif, ≈1,5 d'interligne), 30 px (lede serif des maisons, titre « Vipp Residences », H2 « Information » 700, H2 Contact avec −0,3 px), 18 px (libellés de cartes, H3 récit à 26 px d'interligne), 17 px (nav), 16 px (corps), 14 px (footer, eyebrows, attributions en capitales), 13/12 px. Mobile : 22 px (énoncés), 30 px (citation), 18 px (H2 Information), 16, 14 px.
- Casse : bas de casse partout sauf attributions et eyebrows (« ONE ROOM WONDERS », « A COUNTRYSIDE ESCAPE »).
- Grille : marge et gouttière 22 px ; lignes de cartes 923 + 451 (ratios 1,43 / 0,70), 451 + 923, ou 451 × 3 ; colonne de texte 569 px à x≈730 ; citation centrée sur 923 px ; plein cadre 1 396×785 (1,78) sur les maisons ; aucun `max-width` (`containerWidths []`).
- Rayons : 0 partout. Boutons : « Book now » 333×52 px `#efefef`/noir 12 px ; « Subscribe » 333×46 px noir/blanc ; liens « › Learn more » 14 px avec chevron.
- Iconographie : loupe, sac, chevron, épingle ; aucune illustration ni texture. Photos : WebP via `?width=1080|640&format=webp&quality=80`, `object-fit: cover`, sans `srcset`. Vidéos muettes sans contrôle. Espaceurs `m3-spacer` de 90 px (84 mobile, 42–45 px en variante courte).

| Token | Valeur | Usage |
|---|---|---|
| bg-dark / bg-light / bg-pampas / bg-swirl | `#222325` / `#ffffff` / `#f4f3ec` / `#d6d0c5` | liste et maisons / header-footer / récit / fiche pratique |
| text-sand / text-silk / text-dark | `#ccbca2` / `#bab2a8` / `#0d0d0d` | énoncés / libellés / sur clair |
| accent | aucun | l'action est signalée par un chevron |
| font-sans / font-serif | Vipp Neue 400-600-700 / IvyPresto Headline 400 (+ italique) | tout / énoncés, ledes, citations |
| h-statement / lede / h-section / label / body / nav | 43,2 px (22 mobile) / 30 / 30 / 18 (16) / 16 / 17 | — |
| radius / gutter / spacer | 0 / 22 px (9) / 90 px (84) | — |
| easing / duration | `cubic-bezier(.4,0,.6,1)` ×44, `cubic-bezier(.165,.84,.44,1)` ×1 / 0,3 s ×41, 0,32 s (nav), 0,2 s | transitions |

**Interprétation**
- Le serif sable sur anthracite est le seul ornement ; il assure titre, introduction et conclusion. Le sans propriétaire reste utilitaire, ce qui évite de dupliquer l'expression typographique.
- Le passage blanc → anthracite → blanc marque la section hébergement comme une parenthèse sombre dans le site marchand ; la fiche pratique en `#d6d0c5` est un second changement de registre (du récit à la donnée).
- Sans rayon, sans accent et sans bouton plein sur la liste, la hiérarchie repose sur la taille des images et l'alternance des ratios : rythme de magazine d'architecture.
- Incohérences : Arial sur les contrôles de conversion, absence de `srcset`.

**Enseignements réutilisables**
- Trois neutres + un serif réservé aux énoncés suffisent à distinguer l'hébergement d'une boutique.
- Deux largeurs d'image (2/3, 1/3) et trois motifs de ligne évitent la grille uniforme.
- Changer de fond pour la fiche pratique signale le passage du récit à la donnée.

---

## 4. Architecture de la page d'accueil (liste)

| Position (y desktop / mobile) | Section | Objectif | Contenu | Interaction | CTA | Émotion créée |
|---|---|---|---|---|---|---|
| 0–44 / 0–48 | Barre | Rester dans la boutique | Logo, 5 entrées, loupe, panier | Sticky, méga-menu | — | Continuité marque |
| 44–900 / 48–844 | Hero vidéo scindé, fixe z −1 | Poser le concept | Film collection (29,9 Mo), titre + lieu italique | Le contenu glisse par-dessus | aucun | Curiosité, contraste nature/objet |
| 990–1254 / 928–1037 | Énoncé 1 | Définir | Serif sable 43,2 px, colonne droite | Opacité partielle au 1er palier | — | Assurance |
| 1344–6555 / 1122–4204 | Liste | Choisir | Filtres ; 15 cartes nom | lieu | Zoom ×1,05 au survol, filtres `?cat=` | 15 liens | Collection |
| 6645–6994 / 4289–4409 | Énoncé 2 | Légitimer | « Curated and furnished exclusively… » | — | — | Légitimité |
| 7084–7940 / 4493–5289 | Vidéo vagues | Respirer | Drone sur écume (8,3 Mo) | Autoplay muet | — | Calme |
| 8030–8247 / 5373–5452 | Énoncé 3 | Différencier | « Not a hotel… » | — | — | Distinction |
| 8337–9193 / 5537–6333 | Image + citation | Prouver | Cold Hawaii, citation du propriétaire | — | « › Learn how the idea… » | Sincérité |
| 9283–10237 / 6375–6847 | Vipp Residences | Vente croisée | 2 photos, titre 30 px, 1 phrase | — | « › Learn more » (externe) | Projection patrimoniale |
| 10237–10875 / 6847–7485 | Footer blanc | Services boutique | 3 colonnes, newsletter | — | « Book a kitchen meeting » | Retour au commerce |

**Logique narrative** : concept en image, définition en une phrase ; désir construit par accumulation (15 architectures, 11 pays) et non par le texte ; l'offre ne devient jamais concrète sur cette page (ni prix, ni capacité, ni dates : délégué aux maisons) ; preuve par la citation du dirigeant et le lien vers le récit ; réservation absente ; fin sur la copropriété puis le footer boutique, qui referme la parenthèse.

---

## 5. Scroll et storytelling

**Faits observés**
- Sweep (15 paliers de 713 px) : hero épinglé sur tous les paliers (fixe z −1) ; palier 713 = 3 éléments en opacité partielle + 1 `clip-path` ; paliers 1 425 → 5 700 = 1 transform constant (hypothèse : image de carte restée en survol, `matrix(1.049…)` relevé dans `hover`) ; 7 838 = 2 clip-paths + 1 transform ; ensuite 0.
- CSS : 7 règles `scroll-timeline`/`animation-timeline`, 10 `clip-path`, 7 `scroll-snap`, 11 `position: sticky`, 7 `will-change`, 12 `backdrop-filter`. `animAttrs` : `data-scroll` ×3, split-text ×1 (liste), ×20 (Tunnel), ×78 (récit) ; aucun parallaxe, marquee, horizontal.
- Alternance des fonds : noir → `#222325` (9 300 px) → blanc (856 px) → `#222325` → blanc. Deux médias plein cadre séparés de 1 253 px.
- Page récit : modules `m2-media-split-description` à colonne texte sticky (451 ou 333 px de large, 628–974 px de haut) pendant que l'image défile ; 5 vidéos (todos-santos 68,8 Mo, drone 4:5 26,5 Mo). Même module sur les maisons (2 par page).
- Document : 10 875 px desktop (12,1 viewports), 7 485 px mobile ; Tunnel 24 854 px (27,6 viewports).

**Interprétation, effet par effet**
- Hero épinglé derrière le flux (marque + orienter le regard) : le film reste visible pendant que la page sombre le recouvre ; coût nul, aucune bibliothèque.
- Opacités du 1er palier (rythme) : hypothèse de fondu d'entrée via `animation-timeline`, non vérifiable au-delà de la présence des règles.
- Zoom au survol (action) : seul retour interactif de la liste.
- Vidéo de vagues (respiration) : coupe la lecture catalogue après 5 200 px de cartes, avant les énoncés 2 et 3 → rythme ternaire énoncé / média / énoncé.
- Image + citation (expliquer, marque) : seule section à texte centré blanc ; rupture volontaire.
- Colonnes sticky (expliquer) : le texte reste à hauteur d'œil pendant 856–974 px d'images ; le vrai storytelling est là (866 mots) et sur les maisons (1 072 mots), pas sur la liste (≈26 mots par viewport).
- Envie de poursuivre : portée par la variété des architectures ; la liste n'annonce pas de fin.

**Enseignements réutilisables**
- Épingler le hero derrière le flux plutôt que devant ; réserver les blocs sticky texte/image aux pages de récit ; une vidéo sans texte entre deux énoncés donne un rythme lisible.

---

## 6. Animations et micro-interactions

| Animation | Déclencheur | Élément | Effet | Fonction | Risque UX |
|---|---|---|---|---|---|
| Rideau de navigation | Changement de page (hypothèse) | `.main-navbar_curtain` fixe, opacité 0 | Non observé | Transition | — |
| Fondu d'entrée | Scroll ≈700 px | 3 éléments + 1 clip-path (hypothèse : énoncé 1, filtres) | Opacité → 1 ; durée non mesurable (`animation-timeline`) | Rythme | 0 règle reduced-motion |
| Zoom carte | Survol | `img` de carte | `scale(1.05)`, transition `all` (hypothèse 0,3 s, `cubic-bezier(.4,0,.6,1)`) | Action | `all` coûteux ; pas de changement de libellé |
| Couleur nav | Survol | `main-navbar_link` | `#000` → `#222325`, 0,32 s | Feedback | Écart quasi invisible |
| Méga-menu | Survol « Products » | Panneau blanc 730 px | Apparition + `backdrop-filter` flou (`home-05-menu-open.png`) | Navigation | Couvre 81 % du viewport ; ramène au catalogue produit |
| Accordéon | Clic (Contact, Information) | `accordion_sweep` 0,2 s ease-in-out ×25 | Balayage | Explication | — |
| Stories produit | Automatique | `m7-product-story`, 8 images | Barre `foregroundWidth` 2,8 s linéaire par image (1,8 s sur Farmhouse) | Marque, vente croisée | Aucun contrôle détecté (hypothèse) |
| Pop-up Sleeknote | Temps / scroll | Panneau 404×680 px fixe | Pastille puis panneau | Capture e-mail | Recouvre texte, prix et bouton |
| Vidéos autoplay | Chargement | 2 (liste), 5 (récit), 10–13 (Tunnel) | Boucle muette | Émotion | 30 Mo ×3 sur la liste ; 200 Mo sur Tunnel |
| Skip-link | Focus | 183×43 px, `transform 0.2s` | Apparition | Accessibilité | Positif |
| Curseur / préloader / carrousel | — | `cursor: auto` ; aucun ; `swiper-icons` chargée sans carrousel | — | — | Police inutile |
| Reduced motion | `prefers-reduced-motion` | 0 règle ; 25–42 éléments animés ; vidéos toujours `autoplay` | `04-reduced-motion.png` identique | — | WCAG 2.3.3 non couvert |

**Interprétation**
- Site presque statique : 24 keyframes, un easing dominant (courbe symétrique « standard »), une seule courbe de sortie rapide (easeOutQuart) utilisée une fois. Cohérent avec l'e-commerce, mais la section hébergement n'a aucune signature de mouvement propre ; le module stories est le seul composant réellement animé.
- Les règles `scroll-timeline` sont la seule sophistication : animations natives sans JavaScript de scroll.

**Enseignements réutilisables**
- Un zoom ×1,05 et un fondu d'entrée suffisent à un catalogue de lieux ; préférer `animation-timeline` aux bibliothèques ; ajouter un bloc reduced-motion qui coupe l'autoplay.

---

## 7. Navigation et architecture de l'information

**Faits observés**
- Barre sticky 44 px, z-index 9999, fond blanc ; variante transparente à texte blanc sur le hero de Farmhouse et de la boutique (`main-navbar_withColor`, `--data-top-color`). Items : Products (méga-menu 12 catégories + 6 collections), Kitchens, Guesthouses, World of Vipp, Professionals ; loupe → `/en/search` ; panier.
- Sous-menu « Guesthouses » non capturé ouvert (hypothèse : liste des 15 maisons + 4 filtres, présents dans le dump `menu`). Fil d'Ariane : aucun. H1 : aucun. Filtres : 4 liens 14 px, barre 2 px sur l'actif ; pas de compteur.
- Profondeur : liste → maison = 1 clic (`/our-guesthouses/<slug>`) ; depuis la home boutique = 2. Bouton de réservation persistant : **non**, desktop ni mobile.
- Mobile : barre 48 px (logo, loupe, sac, ≡ 48×48 px) ; cartes en 1 colonne (372×248) puis 2 (177 px) ; **le lieu disparaît des libellés** (« Vipp Pavilion » sans « Upstate New York »).
- Contact : accordéons Customer service / Guesthouses / Sales representatives / Architects… / Press ; `stay@vipp.com` ; +45 4588 8800 ; showrooms avec horaires. Footer : 24 liens en 3 colonnes, newsletter, « Country: US ».

**Interprétation**
- L'essentiel pour un voyageur (où, combien de personnes, à partir de quel prix, comment réserver) est absent de la liste et du header ; la liste est un catalogue de collection, pas un outil de recherche.
- Friction « retour boutique » nulle (méga-menu, panier partout), friction « aller réserver » maximale (aucun raccourci).
- Sur mobile, la suppression du lieu retire la seule donnée factuelle des cartes ; sans compteur ni carte géographique, chercher « une maison en France » demande de tout parcourir.

**Enseignements réutilisables**
- Un item « Guesthouses » au premier niveau du header suffit à donner à l'hébergement le statut de gamme ; garder le lieu sur mobile ; prévoir un point d'entrée « Stay » dès que l'unité vendue est une nuit.

---

## 8. Parcours de réservation et conversion

**Faits observés**
- Aucun CTA de réservation sur la liste, le header, la boutique ou le récit ; le premier « Book now » est sur la page de maison.
- **Tunnel** : « From AUD $970 per night, 2 adults » (gras 16 px blanc, colonne droite) puis « Book now » 333×52 px, `#efefef`, texte noir 12 px Arial, rayon 0, transition fond 0,2 s ; href `checkout.lodgify.com/tunneltasmania/647164/reservation/`, `target="_self"` ; premier bouton à y=3 259 (≈3,6 viewports), répété à y=22 289 avant « Information ».
- **Farmhouse** : « From EUR 400 per night, m… » (tronqué par le pop-up ; hypothèse : séjour minimum) ; bouton identique (y=2 405, 14 946) ; href `planyo.com/booking.php?calendar=58811&mode=resource_list…`, `target="_blank"`.
- Contact par maison : `contact@tunneltasmania.com`, `adm@sollestedgaard.dk` (le domaine propriétaire) ; central : `stay@vipp.com`.
- Bloc « Information » (`#d6d0c5`, H2 30 px 700, 933–992 px) : 13 accordéons sur Tunnel (Check in and check out, Price, Contact, Address, Layout of the space, Sleeping, Cooking, Bathroom facilities, WiFi, Activities, Close by, Transportation, Terms and Conditions), 14 sur Farmhouse (+ Heating), fermés ; interrupteur « Open all » sur mobile ; contenu non capturé (hypothèse : rendu à l'ouverture).
- Aucun sélecteur de dates/voyageurs (`dateInputs []`), aucun avis, note, distinction, avantage direct, package, conciergerie. Devises différentes (AUD, EUR) sous un sélecteur « Country: US ».
- Vente croisée : 6 liens produit dans le récit Tunnel (`/kitchens/v3-kitchen/`, `/products/swivel-chair-452/`, `/products/swivel-chair-curly-edition/`, `/products/sculpture-table-lamp/`, `/products/coffee-tables-square/`, `/products/pedal-bin-14-l-4-gal/`) ; module stories ; 2 maisons suggérées en bas (Tunnel → Shelter, Todos Santos ; Farmhouse → Loft, Shelter). Home boutique : module 4 guesthouses (y=9 939), film Upstate, bloc « CO-OWN THIS HOUSE IN MALLORCA » sur `#804a2e`.

**Interprétation**
- Modèle **curateur / plateforme éditoriale** : Vipp signe, raconte et affiche le prix d'appel ; la nuit est vendue par le partenaire local avec son moteur (Lodgify, Planyo) et son e-mail. La transaction change de domaine, de devise et parfois d'onglet.
- Découvrir / réserver : « Learn » sur la liste, « Book now » sur la maison ; aucun « demander ». Le prix en clair avant le bouton est une donnée qu'aucune référence quiet luxury ne donne.
- Points de rupture : changement de domaine et d'identité (non vérifié), `target` incohérent, bouton gris clair en Arial 12 px moins contrasté que le corps, pop-up sur la colonne du prix.
- Réassurance portée par l'accordéon (adresse, transport, conditions) et par la crédibilité des auteurs ; aucune preuve sociale.
- La page de maison est une page produit déguisée (6 liens, stories) ; la boucle boutique ↔ hébergement est fermée dans les deux sens.

**Enseignements réutilisables**
- « From <devise> <prix> per night, <capacité> » en une ligne avant le bouton ; bouton répété avant la fiche pratique ; si le moteur est délégué, harmoniser `target` et annoncer partenaire et devise ; lier les objets visibles aux fiches produit.

---

## 9. Pages guesthouses (Vipp Tunnel, Vipp Farmhouse)

**Objet vendu** : une nuit dans une maison entière, sans types de chambres. Tunnel : « 2 adults », 160 m² + studio 35 m² ; Farmhouse : 3 chambres. Prix d'appel par nuit, réservation chez un tiers.

**Faits observés — Tunnel desktop**
- Title « Vipp Tunnel | Vipp », pas de H1 (seul heading : H2 « Information »), pas de description ni JSON-LD ; 1 072 mots ; document 24 854 px (27,6 viewports) ; 44 images, **10 `<video>`** ; 451 requêtes, 226 Mo dont 200 Mo de médias (`hero_guesthouse_web_01.mp4` 19,6 Mo, `video_webflow_05` 20 Mo…) ; TTFB 881 ms, FCP 2 816 ms, load 6 231 ms.
- Hero vidéo fixe 856 px (drone entre eucalyptus, cube vitré éclairé), légende « Vipp Tunnel, Tasmania » blanche ≈48 px en bas à droite (contenu sticky 790→900).
- Ordre : eyebrow serif capitales 14 px « A CONCRETE, OFF THE GRID TUNNEL… » + lede serif ≈30 px sable (Room11, Bruny Island, « 11th guesthouse ») → image 1 396×785 → deux médias (569×711, 687×941) + paragraphe blanc 16 px (160 m², 30 m, vitrage) + **prix + Book now** → vidéo plein cadre → citation de l'architecte en serif ≈43 px centré (« THOMAS BAILEY, ARCHITECT AIA, DIRECTOR ROOM11 ») → « Whereas Tasmania provides the exterior, Vipp supplies the interior » + 4 liens produit → image → « edge of the world » + vidéo → « LIGHT AT THE END OF THE TUNNEL » (puits de lumière colorés, Aurora Australis) + portrait de l'architecte 569×711 → vidéo → sticky « Sound of silence » (studio 35 m², plafonds 4 m) → « 300 metres sea stretch » + vidéo → salon en contrebas, lampe Sculpture + 4 liens produit → énoncés 43,2 px « Come for the cleanest air in the world… » / « …the lush flora and fauna… » / « Stay for the Vipp experience. » entrecoupés de vidéos → salle de bains (module Vipp) → sticky « Cosmic Dancers by Lin Utzon » → « A SUSTAINABLE HIDEAWAY » (façade solaire, eau de pluie, relevé des arbres) → vidéo → stories 8 images → Book now → Information → 2 maisons liées → footer.
- Présence humaine : un portrait de l'architecte ; aucune scène de séjour. Équipements en prose (cuisine V3 aluminium, chauffage au sol, climatisation, hors réseau) ; liste structurée seulement dans l'accordéon.

**Faits observés — Tunnel mobile**
- 16 202 px (19,2 écrans), 1 025 mots, **13 `<video>`** (159,6 Mo sur 168 Mo, hero mobile dédié 19,6 Mo), 195 requêtes ; TTFB 717 ms, FCP 1 772 ms, load 4 258 ms.
- Hero 796 px, légende bas-gauche ≈40 px ; prix puis bouton 309×52 px à y≈2 080 (2,5 écrans) ; vidéos secondaires réduites à 182×249 / 150×187 px ; sticky ramenés à 372×465 ; « Open all » ; H2 18 px.

**Faits observés — Farmhouse (desktop / mobile)**
- Hero vidéo 900 px dès y=0 (`hero_module_house_leaf.mp4`) avec **barre transparente à texte blanc**, légende « Vipp Farmhouse » centrée en bas ; 613 mots (566 mobile) ; 17 526 px (10 909) ; 65,5 Mo (39 Mo médias, 4 vidéos) ; TTFB 762 ms, FCP 1 904 ms (mobile 831 / 1 752 ms, 38 Mo).
- Même structure : eyebrow « A COUNTRYSIDE ESCAPE », lede (1 400 acres, Søllestedgaard, Lolland, ferme de 1775, « 4th guesthouse », « one-room-wonders »), deux médias + paragraphe (3 chambres) + prix + Book now (y=2 405, 2,7 viewports), citation, cuisine (produits du potager), sticky « Sleeping in the woods » (designer Julie Cloos Mølsgaard, propriétaire Ulrik Th. Jørgensen), **vue drone avec coordonnées GPS « 54°49'16"N 11°17'55.4"E » en surimpression**, « Come for the wilderness and starry nights… », « Stay for the Vipp experience. », sticky « Søllested Gods » (manoir de 1800), gastronomie locale, stories « Postcard from Vipp Farmhouse » (1,8 s / image), Book now, Information (14), maisons liées.
- Présence humaine : femme avec tasse dans un fauteuil d'extérieur Vipp, couple avec chien, mains tenant une tasse : seule page étudiée avec des scènes de vie.

**Interprétation**
- Un **long-form d'architecture** (27 viewports) qui ne devient page de vente qu'à deux endroits. Ordre d'article : contexte, auteur, matière, lumière, art, durabilité ; le pratique est relégué dans un accordéon fermé de couleur différente, comme une fiche technique en fin de catalogue.
- Projection par les auteurs (architecte cité et photographié, artiste, designer), les chiffres (m², mètres, 4 m sous plafond, 300 m de littoral, 1 400 acres, 1775) et la géolocalisation, plus que par l'expérience client ; Farmhouse corrige avec des personnes, Tunnel reste un bâtiment.
- Le module stories transpose un format Instagram ; seul composant réellement animé, sans contrôle détecté.
- Mobile : la structure survit, mais 13 vidéos en `preload="auto"` sur 16 000 px sont un coût réel ; réduites à 150 px, elles deviennent décoratives.

**Enseignements réutilisables**
- Ordre « auteur → matière → chiffres → art → durabilité → pratique » ; deux boutons identiques (après le premier argument, avant la fiche) ; coordonnées GPS sur la vue drone ; accordéon standardisé à 13–14 entrées entre maisons (ouvrir « Price » et « Sleeping » par défaut serait mieux).

---

## 10. Copywriting

**Faits observés**
- Volume : 280 mots (liste), 201 (mobile), 866 (récit), 1 072 (Tunnel), 613 (Farmhouse), 232 (contact). Aucun heading balisé sur la liste ; H3 numérotés sur le récit (« 01 Vipp Shelter, Sweden » … « 14 Vipp Lofoten, Norway »).
- Énoncés : une phrase déclarative, sujet « Vipp Guesthouses » ou participe passé, adjectifs d'absolu (« unparalleled », « distinct », « effortless », « enduring »), clôture par un lieu ou un état. Énoncé 3 : triple négation anaphorique en trois fragments.
- Maisons : eyebrow nominal en capitales, lede serif avec rang (« 11th », « 4th guesthouse »), auteur et lieu ; paragraphes chiffrés (160 m², 30 m, 35 m², 4 m, 300 m, 1 400 acres, 1775) ; couple récurrent « Come for … / Stay for the Vipp experience. » ; intertitres nominaux (« Sound of silence », « Sleeping in the woods », « A SUSTAINABLE HIDEAWAY »).
- Citations : propriétaire (liste, récit), architecte (Tunnel), designer (Farmhouse) ; attribution en capitales avec tiret cadratin et fonction.
- Libellés : nom + lieu, sans article ni verbe. Liens : « › Learn… » uniquement sur la liste ; « Book now » sur les maisons ; aucun « reserve », « stay », « discover ».
- Registre de luxe : jamais « luxury » ; « curated », « exclusively », « one-of-a-kind », « unparalleled ». Lexique dominant : produit (bin, showroom, furnished, product experience), architecture (steel pod, cantilevered, concrete cube, thatched roof), géographie.

**Interprétation**
- Le copy vend un point de vue (une marque de design qui habite ses produits) ; la transformation prestation → expérience passe par « product experience », qui reformule l'hébergement comme l'usage prolongé d'un objet.
- Les caractéristiques sont données en chiffres d'architecture dans le récit, jamais en liste d'équipements ; les données de séjour sont dans l'accordéon.
- Le ton auto-critique (« business idea gone wrong », « Reluctantly, Vipp made a U-turn ») sert de preuve : on n'invente pas un échec.

**Enseignements réutilisables**
- Une liste peut tenir en trois énoncés (définition, légitimité, différenciation) ; une maison en « eyebrow + lede + chiffres + citation d'auteur + Come for / Stay for » ; un seul verbe par type de lien.

---

## 11. Photographie et vidéo

**Faits observés**
- Liste : 15 visuels, 10 extérieurs (pavillon au bord d'un étang, chalet sous neige, cabine sur pilotis face à une falaise, maison basse dans les dunes, boîte vitrée entre eucalyptus au crépuscule, façade végétalisée avec 2CV, murs de pisé, maison en bois dans la pinède, toit de chaume en forêt d'automne, cheminée industrielle), 2 intérieurs (plafond à fresque, porte ouverte sur une cuisine), 3 vues urbaines de Copenhague. Heure bleue ou fin de journée sur 5, hiver plat (Montafon), plein soleil (Todos Santos, Lagrasse).
- Présence humaine : nulle sur la liste, le hero, les plein-cadres et Tunnel (hors portrait d'architecte) ; 4 scènes de vie sur Farmhouse ; portraits d'archives (1939) sur la page heritage.
- Produit : îlot de cuisine dans le hero, cuisine cannelée dans le pop-up, lampe Sculpture, module de bain, chaise Swivel dans les récits de maison.
- Ratios : 1,43 et 0,70 (liste), 1,68 et 1,78 (plein cadre), 0,73 / 0,80 (colonnes), 1,5 (mobile) ; tout en `object-fit: cover`. Alts = noms de fichiers avec photographes (« Vipp Upstate NY Eric Petschek 15 Hires Edit », « Vipp Cold Hawaii (Richard Gaston) 11 », « R Hjortshoj Vipp Shelter 3 »).
- Vidéos : film de collection (29,9 Mo, version mobile dédiée 29,9 Mo), vagues (8,3 Mo) ; récit : todos-santos 68,8 Mo, drone 4:5 26,5 Mo ; Tunnel : 10 fichiers de 4,6 à 20 Mo ; boutique : film Upstate. Proportion : ≈90 % architecture/paysage, ≈10 % objet, 0 % moments de vie sur la liste.

**Interprétation**
- Chaque maison est traitée comme une œuvre : plan large, bâtiment centré ou au tiers, ciel ou végétation dominants ; on vend la destination et la signature, pas le confort — cohérent avec l'absence de texte sur les services.
- L'absence de personnes est un réflexe de catalogue transposé à l'hébergement ; Farmhouse montre que la marque sait faire autrement.
- Les vidéos ont deux rôles : condenser la collection (hero) et respirer (vagues, drone) ; cohérence totale, au prix de poids extrêmes.

**Shot list**
1. Vue drone de chaque maison dans son paysage (1,43 et 0,70, heure bleue). 2. Façade en lumière rasante, bâtiment au tiers. 3. Un intérieur signature avec un objet de marque en usage et un textile. 4. Un détail matière en 0,8 (cannelure, pisé, chaume). 5. Un plan nature seule par destination, 8–15 s en boucle, < 10 Mo. 6. Film de collection 30–45 s en 16:9 et 9:16 avec légende de lieu. 7. Portrait de l'architecte ou du fondateur. 8. Vue drone verticale avec coordonnées GPS. 9. Deux scènes de vie par maison (repas, lecture, marche). 10. Crédits photographes stockés hors `alt`.

---

## 12. Mobile (390×844)

**Faits observés**
- Header 48 px (logo ≈118×32, loupe, sac, ≡ 48×48). Hero 796 px avec vidéo portrait dédiée, titre ≈40 px, sous-titre ≈26 px, fixe derrière le flux.
- Énoncés 22 px, colonne 372 px, 79–120 px de haut. Cartes 372×248 puis 2 × 177 px ; libellés 16 px sans lieu ; filtres sur une ligne. Citation ≈30 px sur 7 lignes.
- Boutons : « Subscribe » 372×46 ; « Book now » 309×52 ; liens footer 19 px de haut (cibles < 44 px). Aucun moteur.
- Perf liste : TTFB 852 ms, FCP 1 924 ms, load 4 545 ms ; 125 requêtes, 79,5 Mo dont 73,9 Mo de médias (film mobile téléchargé deux fois : 29,9 + 27,6 Mo) ; `?cat=Solitude` : 109 Mo (film ×3). Tunnel mobile : 168 Mo, 13 vidéos, prix et bouton à 2,5 écrans. Farmhouse mobile : 38 Mo.
- Animations : mêmes règles (0,3 s ×29, 0,24 s ×10) ; zoom au survol sans équivalent tactile ; `reducedMotion` non mesuré. Document 7 485 px (8,9 écrans) ; pop-up Sleeknote absent des captures mobiles ; Cookiebot non capturé (`00-initial` quasi vide).
- Lisibilité : `#ccbca2`/`#222325` 8,45:1 ; `#bab2a8` 7,51:1.

**Interprétation**
- Le mobile conserve l'essentiel (hero scindé, énoncés, grille, long-form des maisons) et le simplifie correctement ; la division par deux des énoncés garde 4 lignes.
- Trois pertes : le lieu dans les libellés, les cibles de 19 px, et surtout le poids (74–168 Mo) avec des films de 30 Mo en `preload="auto"` chargés avant toute interaction.
- Sans pop-up, l'expérience mobile est paradoxalement plus calme que le desktop (non prouvé).

**Enseignements réutilisables**
- Décliner le film en portrait (fait) mais en `preload="metadata"` ; empiler nom + lieu ; porter les liens de footer à 44 px.

---

## 13. Performance, accessibilité, SEO

**Faits observés**
- Liste desktop : TTFB 970 ms, FCP 3 092 ms, load 8 552 ms ; 449 requêtes, 125,6 Mo (médias 105,7 Mo, 106 scripts 8,9 Mo, images 7,8 Mo, 16 polices 571 Ko, 141 fetch 1,7 Mo). `rooms` : TTFB 2 397 ms, FCP 6 636 ms, load 19 927 ms. Contact : TTFB 3 462 ms, 16,3 Mo. Récit : 182,4 Mo (médias 164 Mo). Tunnel : 226,2 Mo (200,2 Mo de médias sur 15 requêtes, 126 scripts 10,4 Mo), FCP 2 816 ms. Farmhouse : 65,5 Mo, FCP 1 904 ms. Boutique : 184 Mo, TTFB 613 ms, FCP 1 460 ms, load 2 702 ms (la plus rapide malgré son poids ; hypothèse : cache serveur). Heritage : 98 Mo, FCP 2 072 ms.
- Film de hero présent trois fois dans `videosNet` (requêtes 206 ; hypothèse : deux `<video>` + rechargement au scroll).
- Tiers : media.umbraco.io (86), Sleeknote (30), Clarity, Pinterest, LinkedIn, Bing, Google Ads, Facebook, Cookiebot, Typekit ; GTM en first-party `load.tracking.vipp.com` (578 Ko).
- Images : 34–44 par page, 18–29 en lazy, 0 sans `alt`, 2 vides, 0 `srcset`, WebP par URL. Hero à hauteur fixe avec poster → pas de saut attendu ; police avec fallback déclaré (`__vippNeue_Fallback`).
- Contrastes : `#ccbca2`/`#222325` 8,45:1 ; `#bab2a8`/`#222325` 7,51:1 ; blanc/`#222325` 15,7:1 ; `#222325`/`#f4f3ec` 14,1:1 ; « Book now » noir/`#efefef` ≈17:1 mais 12 px.
- Clavier : skip-link fonctionnel ; **136–165 éléments `outline: none`** ; 6–8 `tabindex="-1"` ; 16–19 `aria-hidden` ; 1–3 iframes sans titre ; 0 bouton/lien sans nom sur la liste (2 sur le récit). Formulaires : newsletter avec labels ; aucun formulaire de réservation.
- Reduced motion : 0 règle ; vidéos non conditionnées.
- Titres : `h1count 0` sur les 12 pages ; aucun heading sur la liste ; un H2 sur les maisons. Métadonnées : `robots: index, follow`, `og:title`, `og:image` ; **`meta description` uniquement sur `/en`** (« …from the iconic pedal bin to full kitchens, furniture and guesthouses ») ; pas de `og:description`, pas de `hreflang` malgré « Country: US », canonical correct (sans `?cat=`), aucun JSON-LD (ni `LodgingBusiness`, ni `Product`).
- Indexable : 280 (liste), 1 072 (Tunnel), 613 (Farmhouse), 866 (récit), 628 (heritage), 396 (boutique) mots. CSS 307 Ko sur 8 feuilles ; seuil principal 833/834 px.

**Interprétation**
- Immersion/performance déséquilibrées : 84–88 % du poids est vidéo, en `preload="auto"` et téléchargements multiples ; le FCP desktop de 1,5 à 6,6 s tient au JavaScript (106–126 scripts) et au TTFB (0,6–3,5 s).
- Accessibilité structurelle correcte (landmarks, skip-link, alts, noms) mais outline supprimé partout et aucun H1.
- SEO : 15 hébergements dans 11 pays sans H1, description ni données structurées ; l'absence de hreflang sur un site multi-pays est un risque de duplication.

**Enseignements réutilisables**
- Plafonner le hero vidéo à 6–8 Mo en `preload="metadata"`, un seul `<video>` par point de rupture ; déclarer H1 + description + JSON-LD sur la collection et les maisons ; garder `:focus-visible`.

---

## 14. Conclusion

**15 meilleurs éléments**
1. « Guesthouses » au premier niveau du header d'une boutique, au rang de « Kitchens ».
2. Hero scindé lieu | objet qui énonce le positionnement hybride sans texte.
3. Hero épinglé à z-index −1 : le contenu recouvre le film sans bibliothèque.
4. Trois énoncés serif sable 43,2 px (définition, légitimité, différenciation) pour 280 mots.
5. Triple négation « Not a hotel. Not a showroom. Not like any place… ».
6. Nommage « Vipp + typologie + lieu » et catégories d'humeur (Solitude / Tropical / Urban).
7. Grille 923 / 451 px, trois motifs de ligne, 22 px, aucun rayon.
8. « From AUD $970 per night, 2 adults » en une ligne avant un bouton répété deux fois.
9. Pages de maison en long-form d'architecture (1 072 mots) avec architecte cité, photographié et signé.
10. Six liens produit dans le récit : la page d'hébergement est aussi une page catalogue.
11. Bloc « Information » standardisé à 13–14 accordéons sur fond `#d6d0c5`.
12. Coordonnées GPS en surimpression sur la vue drone (Farmhouse).
13. Récit d'origine assumant un échec commercial, en colonnes sticky.
14. Module stories à barres de progression (2,8 s / image).
15. Film de hero décliné en portrait pour mobile ; grille mobile 1 + 2 colonnes.

**5 faiblesses / limites**
1. Poids : 65–226 Mo par page, 10–13 `<video>` en `preload="auto"`, film de hero téléchargé jusqu'à trois fois, FCP desktop 1,5–6,6 s.
2. Réservation déléguée à des moteurs tiers hétérogènes (Lodgify, Planyo), `target` incohérent, devises différentes, aucun sélecteur de dates, aucune preuve sociale.
3. Pop-up Sleeknote fixe sur la colonne du texte et du prix ; méga-menu produit à 81 % du viewport depuis les pages guesthouses.
4. Fondamentaux SEO/a11y : aucun H1, pas de description hors `/en`, ni hreflang ni JSON-LD, 136–165 `outline: none`, 0 règle reduced-motion.
5. Mobile : lieux supprimés des cartes, cibles de footer de 19 px, 38–168 Mo de médias.

**10 principes réutilisables**
1. Traiter l'hébergement comme une collection : nom de gamme, noms d'objets, catégories d'humeur.
2. Réduire la liste à trois énoncés et laisser le récit aux pages de maison.
3. Serif réservé aux énoncés et citations ; sans pour tout le reste.
4. Trois neutres, zéro accent ; chevron pour l'action, italique pour le lieu.
5. Épingler le hero derrière le flux plutôt que d'animer le contenu.
6. Page de maison : auteur → matière → chiffres → art → durabilité → pratique.
7. Prix et capacité en une ligne avant le bouton ; bouton répété avant la fiche pratique.
8. Fiche pratique aux mêmes 13 intitulés partout.
9. Lier chaque objet visible à sa fiche produit quand la marque vend aussi des objets.
10. Un film de collection par point de rupture, `preload="metadata"`, poster, bloc reduced-motion.

**Éléments propres à la marque à ne pas copier**
- Panier et méga-menu produit sur des pages d'hébergement.
- Un système de réservation différent par maison (conséquence du modèle partenarial).
- Le pop-up Sleeknote et ses 30 requêtes ; les noms de photographes dans les `alt` ; le budget vidéo d'une marque de design.

**Notes /10**
- **Branding : 9/10.** Item de header au rang des gammes ; nommage collection + catégories d'humeur ; récit d'origine avec échec assumé ; boucle boutique ↔ hébergement fermée (module guesthouses sur la boutique, 6 liens produit sur Tunnel). Un point retiré pour le footer et le pop-up qui parlent cuisine sur les pages d'hébergement.
- **Direction artistique : 8/10.** Trois neutres en tokens CSS, serif/sans à rôles fixes, grille 923/451 à 22 px, rayon 0, photographie architecturale homogène (heure bleue, drone). Retenues : Arial sur les boutons dont « Book now », absence de `srcset`, hero mobile de la liste amputé de sa moitié gauche.
- **Animations : 4/10.** Un easing, zoom ×1,05, fondu via `animation-timeline`, stories à barres de progression ; aucune règle reduced-motion, vidéos non conditionnées, `transition: all`, pas de signature de mouvement propre à l'hébergement.
- **UX : 6/10.** 1 clic de la liste à la maison, filtres par URL, accordéon standardisé, « Open all » ; contre : ni H1 ni fil d'Ariane, lieux absents sur mobile, ni compteur ni carte, pop-up sur la colonne de lecture, méga-menu intrusif.
- **Conversion : 5/10.** Prix et capacité en clair, bouton répété, contact par maison ; contre : aucun CTA sur la liste ou le header, moteur tiers différent par maison avec `target` incohérent, aucune preuve sociale ni avantage direct, bouton gris en Arial 12 px, étape 1 non vérifiable.
- **Mobile : 6,5/10.** Films portrait dédiés, grille 1+2, énoncés 22 px, prix à 2,5 écrans, « Open all » ; contre : 38–168 Mo, 13 vidéos sur Tunnel, lieux supprimés, cibles de 19 px, burger sans nom.

**Note globale : 7/10.** Le site montre mieux que tout autre de la série comment une marque non hôtelière transforme un produit en hébergement : nommage, header, récit, liens produit et prix d'appel forment un système. La note est plafonnée par la conversion externalisée et hétérogène, par les fondamentaux techniques (poids, H1, reduced-motion) et par deux intrusions commerciales (pop-up, méga-menu) qui contredisent la retenue de la direction artistique.

**Ce que ce site apporte que les sites « quiet luxury » (FORESTIS, Seagate, Le Collectionist) n'apportent pas**
- Un **modèle de curateur** : la marque signe, raconte et fixe le prix d'appel ; la nuit est vendue par le partenaire local (Lodgify, Planyo) — catalogue de 15 maisons dans 11 pays sans opérateur unique.
- Un **prix affiché en clair dans le récit** (« From AUD $970 per night, 2 adults ») là où les références renvoient au moteur.
- La **preuve par les auteurs** (architecte, artiste, designer, photographes) et par les **chiffres d'architecture** (m², hauteurs, littoral, coordonnées GPS) au lieu de la preuve par les avis.
- La **page shoppable** : objets du décor liés à la boutique, module stories, home boutique qui renvoie vers les guesthouses.
- **Catégories d'humeur** et **nommage de collection** à la place des types de chambres ; **récit d'origine construit sur un échec**.

---

## Observations clés à conserver pour la phase comparative

- Header e-commerce commun (44 / 48 px, logo + 5 items + loupe + panier), « Guesthouses » au premier niveau ; aucun bouton de réservation persistant sur aucune des 12 pages.
- Liste : 15 maisons, 11 pays, 4 filtres `?cat=`, 280 mots, 0 heading, 10 875 px desktop / 7 485 px mobile ; libellés « nom | lieu » 18 px, lieu supprimé sur mobile.
- Hero scindé lieu | cuisine, film 29,9 Mo (desktop et mobile dédié), `position: fixed` z −1, 856 px ; téléchargé 2 à 3 fois.
- Palette : `#222325` corps, `#ffffff` header/footer, `#f4f3ec` récit, `#d6d0c5` fiche pratique, `#804a2e` Residences ; textes `#ccbca2` (8,45:1) et `#bab2a8` (7,51:1) ; tokens `--primary-silk/swirl/pampas` ; rayon 0.
- Typo : Vipp Neue propriétaire + IvyPresto Headline (Typekit) ; énoncés 43,2 / 22 px ; lede de maison ≈30 px ; corps 16 px ; boutons Arial 12 px.
- Grille : 22 px (9 mobile) ; cartes 923×644 et 451×644 ; plein cadre 1 396×785 ; pas de `max-width`.
- Mouvement : easing `cubic-bezier(.4,0,.6,1)` ×44, 0,3 s, zoom ×1,05, 7 règles `scroll-timeline`, 0 reduced-motion, aucune lib (Next.js en hypothèse forte).
- Maisons : 1 072 mots / 24 854 px (Tunnel), 613 / 17 526 (Farmhouse) ; 10–13 `<video>` ; 226 Mo (Tunnel desktop), 168 Mo (mobile), 65 Mo (Farmhouse).
- Conversion : « From AUD $970 per night, 2 adults » → « Book now » 333×52 `#efefef` → `checkout.lodgify.com` (`_self`) ; Farmhouse « From EUR 400 per night » → `planyo.com` (`_blank`) ; premier bouton à 3,6 / 2,7 viewports ; e-mails par maison + `stay@vipp.com`.
- Fiche pratique « Information » : 13–14 accordéons standardisés, fermés, « Open all » sur mobile, contenu non capturé.
- Vente croisée : 6 liens produit sur Tunnel ; stories 8 images à 2,8 s ; module 4 guesthouses + film Upstate + Residences sur la boutique.
- Intrusions : Cookiebot centrée ; Sleeknote 404×680 px fixe dès le 2e palier (30 requêtes, 1,6 Mo) ; méga-menu 730 px avec flou.
- Perf : TTFB 0,6–3,5 s ; FCP 1,5–6,6 s desktop, 1,8–2,1 s mobile ; 106–126 scripts (8,3–10,4 Mo) ; Clarity, Pinterest, LinkedIn, Bing, Google Ads, Facebook, GTM first-party.
- SEO : 0 H1 sur 12 pages ; description uniquement sur `/en` ; ni hreflang ni JSON-LD ; alts = noms de fichiers avec photographes.
- Photo : 0 personne sur la liste et Tunnel (hors architecte), 4 scènes de vie sur Farmhouse ; heure bleue dominante ; coordonnées GPS en overlay ; archives 1939 sur heritage.
