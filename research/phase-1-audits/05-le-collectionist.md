# Fiche d'audit — Le Collectionist (`collectionist`)

## 0. En-tête

- **Nom** : Le Collectionist — plateforme de location de villas et chalets de luxe avec conciergerie (≈ 2 300 propriétés, 10 bureaux locaux, 50 destinations annoncés sur la home).
- **URL de départ** : https://www.lecollectionist.com/fr/
- **Date** : 2026-09-04 (captures 16:40 et 16:48 UTC), Chromium headless 1440×900 et 390×844 (DPR 2), Playwright.
- **Nature** : pas un hôtel. La rubrique 9 traite la **page propriété** (Villa Blue, Ibiza) et la **page destination / liste** (Ibiza).

| Label | URL | Desktop | Mobile |
|---|---|---|---|
| home | https://www.lecollectionist.com/fr/ | oui | oui |
| destination (liste Ibiza) | https://www.lecollectionist.com/fr/location-villas-luxe/ibiza (canonical rendu : `/ibiza/villa-animaux-acceptes`) | oui | oui |
| villa-detail | https://www.lecollectionist.com/fr/location-luxe/villa-blue-ibiza | oui | oui |
| collections | https://www.lecollectionist.com/fr/nos-collections | oui | oui |
| inspire (quiz) | https://www.lecollectionist.com/fr/s-inspirer | oui | oui |
| offers (conciergerie) | https://www.lecollectionist.com/fr/notre-conciergerie-de-luxe | oui | non |
| contact | https://www.lecollectionist.com/fr/contact | oui | non |
| listings SEO (mal classés par l'heuristique, cités comme exemples) | `/fr/immobilier-luxe-service`, `/fr/location-villas-luxe/france`, `/fr/location-chalets-luxe/chalet-piscine`, `/fr/location-villas-luxe/barcelone-et-la-catalogne`, `/fr/location-villas-luxe/espagne` | oui | partiel |

**Limites de l'observation**
- **Vidéo hero** `video-reverse.mp4` (autoplay, muted, loop, playsinline, preload=metadata) reste `paused` en headless : les captures montrent la première frame ; boucle, fluidité et comportement sous `prefers-reduced-motion` non observés.
- **Flux de recherche** : ouverture du champ Destination, du calendrier et recherche vide ont échoué (timeout 3 s) ; aucune capture `flow-search-*`. La liste Ibiza a été analysée par accès direct.
- **Réservation** : « RÉSERVER » non activé ; seule l'étape 1 de « FAIRE UNE DEMANDE » a été ouverte, sans soumission.
- **Cookies** : la bannière Axeptio est restée visible sur toutes les captures scrollées (≈ 420×260 px en bas à gauche desktop, un tiers bas des écrans mobiles).
- **Menu desktop ouvert** non capturé (décrit via le DOM : tiroir `fixed inset-y-0` de 395 px et capture mobile).
- **Hover cartes** : aucune variation mesurée sur `.home-house-card__img` et `.search__house-card` ; la règle `.img-scale:hover img{transform:scale(1.1)}` existe (hypothèse : zoom sur d'autres composants).
- **Lighthouse / LCP / CLS** non disponibles ; transitions de page non mesurées ; section « DERRIÈRE LES COLLECTIONS » rendue vide (lazy non déclenché) ; tactile réel non testé.

---

## 1. Positionnement de marque

**Faits observés**
- Title : « Le Collectionist : Location de Villas et Chalets de Luxe » ; description : villas et chalets d'exception à travers l'Europe, « notre conciergerie façonner votre séjour unique ».
- Hero : surtitre « PARTAGEZ », titre « L'EXTRAORDINAIRE » (Ayer 60 px), sous-titre en trois fragments nominaux (maisons / destinations / expériences).
- Manifeste sur fond #f7f7f7 : trois mots Ayer (« UNIQUES », « SUR-MESURE », « LOCALE ») avec surtitres et chiffres : 2 300 propriétés, 50 destinations, 10 bureaux locaux.
- Trois **collections** Essential ◇ / Signature ◇◇ / Iconic ◇◇◇ répétées sur home, collections, conciergerie, cartes de liste et page villa ; chaque palier = niveau de service (ménage 1×/semaine et concierge avant le séjour → 3×/semaine, concierge avant et pendant → 5×/semaine, transferts, courses, forfaits de ski).
- Preuves : logos presse (Ideat, AD, L'Officiel, Elle, Challenges), footer « Certifié et récompensé… Condé Nast Traveler » (2014, 2024), Trustpilot sur la villa, JSON-LD Organization (`foundingDate: 2014`, 65 rue de la Victoire, Paris).
- Deuxième audience dès la home : « LOUEZ VOTRE MAISON » / « REJOIGNEZ NOTRE PORTFOLIO », plus « ACHETER UNE MAISON » et « PARTENAIRES DE VOYAGE » dans le menu ; apps propriétaires en footer.
- Placeholder du contact : « Nos options de location commencent en général à 10 000 € la semaine… minimum de 7 jours ». Villa : « Total – 7 nuits 33 160 € », « prix à confirmer avec nos Travel Advisors ».

**Interprétation**
- Positionnement de **curateur-orchestrateur** (« sélectionnée pour son âme », conciergerie locale) plutôt que marketplace ; promesse centrale : des vacances de groupe (10–16 voyageurs sur les cartes) rendues fluides par un service humain.
- Cible : familles et groupes aisés, France et international (+33 / +1 646, hreflang fr/en, « Français – Eur »), ticket ≥ 10 000 €/semaine annoncé pour filtrer.
- Gamme : haut de gamme fonctionnel (grille, filtres, prix affichés), pas ultra-luxe confidentiel. Territoire : liberté, nature, moments partagés ; personnalité sobre, « conseiller » plus que « palace ».
- Différence avec un hôtel : pas d'unité chambre ; la vente combine maison (photos, capacité, m²), destination (compteurs de biens) et service (collections). L'expérience passe par la conciergerie (« Visite privée du Musée d'Orsay », « Michelin au sommet »).
- Cohérence : forte sur le fond (« maison », « conseiller », « collection » constants), moyenne sur la forme : univers éditorial (Ayer, GT Alpina, mosaïques) contre interface e-commerce standard (chips, skeletons, grille + carte).

**Enseignements réutilisables**
- Trois paliers de service nommés, avec pictogramme répété sur chaque carte, rendent une promesse de service tangible.
- Chiffrer la promesse (2 300 maisons, « 95 chalets à louer ») remplace les adjectifs.
- Annoncer le ticket d'entrée dans le formulaire qualifie les demandes.

---

## 2. Première impression (5 premières secondes)

**Faits observés — desktop**
- Header 72 px transparent, `position: static` sur la home (disparaît au scroll) : burger + logo blanc à gauche ; téléphone, « OBTENIR L'APP » (121×33, #0f0f0f à 70 %), cœur, compte à droite.
- Hero de **458 px** (51 % du viewport), ratio 3,14:1, vidéo avec voile rgba(32,32,32,0.3) ; l'onglet « NOS MAISONS » et trois cartes portrait 392×533 (chalets enneigés) sont déjà visibles sous la ligne de flottaison.
- Centrés dans le hero : surtitre, titre Ayer 60 px blanc, sous-titre 16 px Brown Light, barre de recherche blanche ≈ 560×52 (Destination | Arrivée → Départ | Voyageurs | RECHERCHER 132×52 #202020), pastille « Vous ne savez pas où partir ? S'INSPIRER ».
- Distractions : bannière Axeptio ; **modale newsletter** (« Abonnez-vous… », image + e-mail + JE M'ABONNE) au premier scroll (`home-03-scroll1`) ; barre Nuxt 3 px. Numéro variable selon session (+33 sur `00-initial`, +1 646 sur `01-hero`, via `api.ipregistry.co`).
- TTFB 377 ms, FCP 716 ms, DCL 1 274 ms, load 1 353 ms.

**Faits observés — mobile**
- Smart banner AppsFlyer 62 px (bouton bleu #007aff hors charte, texte anglais), header 72 px, hero **image** 390×387 (`VIDEOS []`), titre Ayer 48 px, formulaire empilé + RECHERCHER 358×44.
- Iframe « Sign in to Le Collectionist with Google » 390×144 fixée en bas (z 9999) et bannière cookies plein écran (z 20 930 940) : trois couches d'interruption.

**Interprétation**
- En deux secondes on comprend : maisons de luxe, où et quand. L'élément le plus contrasté est la barre de recherche : le message est l'outil, pas l'émotion. Logo petit (≈ 175 px), non centré.
- La vidéo est d'ambiance (mer, pin parasol, silhouette dans une piscine à débordement) ; sur mobile une photo de villa toscane la remplace : l'impression dépend du device.
- Raison de continuer : utilitaire (« Nos maisons » juste dessous) ; le quiz S'INSPIRER capte l'indécis. Sur mobile, l'empilement des surcouches est le premier frein.

**Enseignements réutilisables**
- Un « chemin de l'indécis » sous le moteur ; un hero à 50 % de viewport pour montrer la preuve produit tout de suite ; jamais trois interruptions superposées sur mobile.

---

## 3. Direction artistique

**Faits observés**
- Palette : #202020 (texte, boutons ; 596 occurrences home), #ffffff, #f7f7f7 (sections alternées, 184), #eaeaea (bordures, chips), #757575 / #4c4c4c (secondaire), #cacaca / #aaaaaa / #dddddd (désactivés), voile rgba(32,32,32,0.3), boutons translucides #0f0f0f à 70 %. **Aucun accent** ; seules couleurs : focus ring Tailwind #3b82f6, variables erreur #dc6869 / succès #479b9b, bleu du smart banner.
- Polices (`@font-face`, noms de fichiers : hypothèse sur les fonderies) : **Brown** Light/Regular (sans géométrique, 133 éléments home), **GT Alpina** Light (serif d'intro, 16), **Ayer** Medium (display serif condensé, 4 : hero + manifeste). Tiers : Rubik/Inter (Axeptio), Museo Sans (smart banner), Source Sans 3 (Trustpilot).
- Échelle desktop : 60 (H1 collections/conciergerie, Ayer) / 36 (H1 contact, quiz, H3 témoignages) / 32 (H2 home, H1 villa) / 24 (H3 cartes) / 20 (H2 cartes liste) / 18 (H2 villa) / 16 / 14 (236 occurrences sur la villa) / 12 / 10. Mobile : Ayer 48 px, H2 32 px inchangé, H1 quiz 32 px.
- Titres : Brown 400 **uppercase**, interlettrage 1 px, interligne 1,4 (32 → 44,8 px) ; surtitres d'étapes 16 px, ls 4,8 px, #757575. Body Brown 300 16/22,4 ; villa 14/19,6.
- Grille : container 1 280 px ; texte 1 024 / 896 / 608 px ; villa : 784 px contenu + carte sticky 488 px ; liste : 864 px + carte 576 px.
- Boutons : **rayon 0**, 14 px uppercase ls 1 px, padding 12/16, hauteur 44–52 px ; plein #202020 / contour / texte souligné ; icônes rondes 32–40 px (rayon 9999). Chips #f7f7f7 12 px ; champs bordure #eaeaea 1 px.
- Ratios d'images : hero 3,14 ; cartes home 0,74 (392×533) ; carrousel collections 1,43 (641×450) ; destinations 1,5 (404×269) ; mosaïque conciergerie 0,57 (336×594, décalées 4 543 / 4 595 / 4 641 / 4 703 px) ; hero villa 2,29 (1440×630) ; chambres 1,52 ; liste 1,5 (400×267) ; témoignages 1:1 (388×388). CDN : `q=50`, `func=crop`, `force_format=webp`.
- Iconographie filaire 1 px (piscine, pétanque, jumelles), losanges ◇, coches ✓, guillemet gris ornemental, tampon rond « Le Collectionist ». Ombres Tailwind (`shadow-lg`, `hover:shadow-[0_2px_36px…]`), 14 règles `backdrop-filter`.

| Token | Valeur observée |
|---|---|
| Texte / CTA | #202020 |
| Fonds | #ffffff / #f7f7f7 |
| Bordure, chip, skeleton | #eaeaea (#dddddd) |
| Secondaire / désactivé | #757575, #4c4c4c / #cacaca, #aaaaaa |
| Voiles | rgba(32,32,32,0.3) hero ; rgba(0,0,0,0.5) modales |
| Display | Ayer Medium 60 px (48 mobile), uppercase, ls 1 px |
| Titres | Brown 400, 32 / 24 / 20 / 18 px, uppercase, ls 1 px, lh 1,4 |
| Body | Brown 300 16/22,4 ; 14/19,6 sur produit ; GT Alpina 16–18 px pour l'intro |
| Rayons | 0 px partout ; 9999 px icônes |
| Header / container | 72 px / 1 280 px (texte 608–896) |
| Boutons | h 44–52, 14 px uppercase, padding 12×16 |
| Motion | 0,8 s ×54, 0,5 s, 0,35 s, 0,3 s ; ease-out, cubic-bezier(.4,0,.2,1) |

**Interprétation**
- DA « éditoriale noir et blanc » : contraste maximal, capitales à lettrage large, couleur entièrement déléguée aux photos (bleu piscine, neige, sable) — cohérent avec les logos presse.
- La signature est le trio Ayer (un seul mot par bloc) + Brown uppercase + GT Alpina de lecture. Rayon 0 et chips grises donnent une rigueur d'outil ; le vide est généreux sur la home (blocs de 550–900 px) mais la fiche villa est dense (37 éléments en 10 px).

**Enseignements réutilisables**
- Display serif réservée à 4–5 mots par page ; décalages verticaux statiques d'une rangée d'images ; une palette sans accent impose des photos très colorées (à prévoir en shot list).

---

## 4. Architecture de la page d'accueil

**Faits observés** (desktop 8 454 px ≈ 9,4 viewports ; mobile 10 878 px ≈ 12,9). Positions issues des sections, `largeImages` et sonde scroll.

| Position (y px) | Section | Objectif | Contenu | Interaction | CTA | Émotion |
|---|---|---|---|---|---|---|
| 0–72 | Header transparent | Outils | Burger, logo, tél., app, favoris, compte | Tiroir 395 px | OBTENIR L'APP | Disponibilité |
| 0–530 | Hero vidéo 3,14:1 | Rechercher | Surtitre, titre Ayer, 3 fragments, barre | 4 champs | RECHERCHER, S'INSPIRER | Évasion |
| 530–1 300 | « NOS MAISONS » | Prouver l'offre | 4 onglets (Chalets d'hiver / En famille / Soleil d'hiver / Haute montagne), 3 cartes 0,74 nom + station | Onglets | RÉSERVEZ VOS VACANCES (→ /fr/recherche) | Concret, saison |
| 1 300–1 640 (#f7f7f7) | Manifeste | Positionner | UNIQUES / SUR-MESURE / LOCALE + phrases chiffrées | — | — | Confiance |
| 1 640–2 150 | « VOTRE HIVER COMMENCE ICI » | Pousser la saison | Texte + salon chalet 688×512 | — | EXPLOREZ NOS CHALETS | Cocon |
| 2 150–2 700 | « NOS COLLECTIONS » | Expliquer les niveaux | 3 colonnes ◇/◇◇/◇◇◇ | — | EXPLOREZ NOS COLLECTIONS | Clarté |
| 2 700–3 350 | Carrousel 6 maisons 641×450 | Désir | Chalet Monza, The Lodge Verbier… + badge collection | Flèches, snap | cartes | Sélection |
| 3 350–3 900 (#f7f7f7) | « IMAGINONS VOS PROCHAINES VACANCES » | Contact humain | Plage aérienne 624×421 + texte | — | ÉCHANGER AVEC UN CONSEILLER / CONTACTEZ-NOUS | Accompagnement |
| 3 900–5 300 | « LA CONCIERGERIE AUTREMENT » | Vendre le service | 2 paragraphes chiffrés + 4 portraits décalés (cavalier, ski, plongée, voilier) | Reveals (3 → 9 transforms) | DÉCOUVRIR NOTRE CONCIERGERIE | Aventure |
| 5 300–6 200 | « DESTINATIONS EN VOGUE » | Orienter | 6 cartes 1,5 + compteurs (« 95 chalets », « 129 villas »), 12 au total | Grille | VOIR PLUS DE DESTINATIONS + | Abondance |
| 6 200–6 950 (#f7f7f7) | « LOUEZ VOTRE MAISON » | Recruter | Texte + portrait N&B | — | REJOIGNEZ NOTRE PORTFOLIO | Prestige |
| 6 950–7 250 | Presse + H1 SEO | Preuve | 5 logos ; H1 20 px « LOCATION DE VILLAS DE LUXE… » | — | — | Légitimité |
| 7 532–8 455 | Footer 923 px | Réassurance / SEO | Condé Nast, newsletter, colonnes, apps, FR-€ | Newsletter | S'INSCRIRE | Sérieux |

**Interprétation — logique narrative**
1. Début : outil + alternative (quiz). 2. Désir : dès 530 px par les cartes, avant le manifeste — la maison vend plus que le discours. 3. Offre concrète : noms de chalets dès le premier écran, compteurs à 5 300 px. 4. « Chambres » : remplacées par des cartes sans capacité ni prix. 5. Preuve : chiffres, presse, récompenses ; aucun témoignage sur la home (présents sur villa, liste, collections). 6. Réservation : deux voies parallèles tout du long, self-service et conseiller. 7. Fin : message propriétaires et H1 SEO, clôture émotionnelle faible.

**Enseignements réutilisables**
- Alterner blanc / #f7f7f7 tous les deux blocs ; doubler chaque CTA transactionnel d'un CTA humain ; compteurs « N villas à louer » par destination.

---

## 5. Scroll et storytelling

**Faits observés**
- Header non sticky sur home et villa (top −558 px dès le premier scroll) ; sticky sur la liste (z 1030) avec filtres sticky 150 px à 72 px et carte Mapbox `lg:top-[72px]` sur `calc(100dvh)`.
- Fonds : transparent → #f7f7f7 (y 1 117, 3 350, 6 142–6 700) → blanc ; un seul bloc sombre (photo N&B) « DES VACANCES INOUBLIABLES » sur villa et liste.
- Sonde scroll : `transforms` 1 / `opacityLow` 2 à y 3 909, 3 à 5 025, 9 à 5 584, 3 à 6 700 → reveals à l'entrée (`data-aos` ×6, reveal ×8 home, 49 liste). Parallaxe 0, marquee 0, split text 0, sticky narratif 0, scroll horizontal piloté 0 (`horizontal: 1` sur mobile = carrousel natif).
- Carrousels Swiper (`--swiper-*`), 14 règles `scroll-snap`, flèches rondes 32 px ; mobile : cartes 353×250 avec la suivante visible sur ≈ 40 px.
- Sur mobile, la sonde ne renvoie que le texte cookies dès y 4 712 : la bannière occupe le centre du viewport pendant tout le scroll.

**Interprétation**
- Rythme calme : un message par bloc, respirations larges, alternance texte centré → grille → texte + photo → carrousel → mosaïque → grille. Les reveals servent à orienter le regard et adoucir, pas à expliquer. Les images fixes reportent le récit sur la sélection photo ; le bloc sombre final joue la preuve.
- L'envie de poursuivre vient de la variété des sujets, non d'un dispositif de scroll.

**Enseignements réutilisables**
- Décalages statiques = rythme gratuit ; trois couches sticky sur une liste à condition de garder ≥ 60 % de largeur au contenu (864/1 440) ; traiter la bannière cookies avant toute animation mobile.

---

## 6. Animations et micro-interactions

**Faits observés** : 17 keyframes (23 sur villa/liste) ; transitions 0,8 s ×54, 0,5 s ×17, 0,35 s ×12, 0,3 s ×10 ; easings `ease-out` ×12, `cubic-bezier(0.4,0,0.2,1)` ×8 ; en CSS `(.4,0,.2,1)` ×21, `(0,0,.2,1)` ×6, `(.55,.085,.68,.53)`, `(.25,.46,.45,.94)`, `(.455,.03,.515,.955)` ×3 chacun, `(.6,-.28,.735,.045)` ×1. Pas de curseur custom, pas de préloader, 0 `will-change` sur la home.

| Animation | Déclencheur | Élément | Effet | Fonction | Risque UX |
|---|---|---|---|---|---|
| Barre de progression | Navigation Nuxt | 3 px #202020, z 999 999 | Progression | Feedback | Nul |
| Préloader / arrivée | — | aucun | — | — | — |
| Hero vidéo | Chargement | `<video>` 1440×458 autoplay muted loop | Boucle (hypothèse : plan fixe, « reverse ») | Émotion, marque | 8,5 Mo en 2 requêtes partielles ; ignorée par reduced-motion |
| Révélation blocs | Entrée viewport | AOS ×6, reveal ×8–49 | Fade + translation ≈ 0,8 s ease-out (hypothèse) | Orienter, rythme | Faible |
| Zoom photo | Hover | `.img-scale img` | scale 1.01 → 1.1, 0,35 s ease-out | Désir | Non mesuré sur les cartes |
| Hover boutons cookies | Hover | Axeptio | #202020 → #0f0f0f, 0,15 s | Feedback | Hors charte |
| Hover téléphone | Hover | header villa | blanc → 90 %, soulignement | Feedback | Très discret |
| Hover cartes | Hover | `.home-house-card__img`, `.search__house-card` | **aucun changement mesuré** | — | Manque d'affordance |
| Accordéons | Clic | `.lc-collapse-content` | `grid-template-rows 0fr → 1fr`, 0,5 s (.4,0,.2,1) | Expliquer | Nul |
| Tiroir menu | Burger | `fixed inset-y-0` 395/390 px | Translation x (durée : hypothèse 0,3–0,5 s) | Navigation | 27 % de la largeur desktop |
| Carrousels | Flèches / swipe | Swiper + snap | Glissement | Rythme | Pas de pagination desktop home |
| Skeletons | Chargement liste | 45 `Gradient 2s linear`, 4 `pulse 2s` | Shimmer #eaeaea | Feedback | Cartes grises visibles en capture |
| Smart banner | Chargement mobile | `.smart-banner` | `slideDown 0.6s ease-out` | Acquisition app | Interruption |
| Quiz | Chargement | 8 polaroids | `rotate-odd/even 1s`, `scale-in 1s` (mobile 1,5 s + fade) | Marque, jeu | 56 images sans alt |
| Modales dates / newsletter | Chargement liste / 1er scroll home | overlays 50 % | Apparition | Action / acquisition | Interstitiels |
| Focus | Clavier | 178 `outline:none` ; `focus:shadow-focus` #3b82f6 | Ring bleu (hypothèse) | A11y | Hors charte, non vérifié |
| Reduced motion | media query | 3 règles (`.view-enter-active {transition:none}`, `.motion-reduce`) | Coupe les transitions de page | A11y | Vidéo et reveals inchangés (capture `04` identique à `01`) |

**Interprétation**
- Site **peu animé** : mouvements fonctionnels propres, aucune signature motion (0 curseur, 0 transition de page visible, 0 scroll piloté). Bon pour la performance perçue, nul pour la différenciation. L'absence de retour hover sur les cartes est le manque le plus sensible sur une grille produit.

**Enseignements réutilisables**
- Accordéon `grid-template-rows 0fr → 1fr` ; skeleton shimmer sur blocs à ratio fixe ; une courbe et quatre durées (0,15 / 0,3 / 0,5 / 0,8 s) suffisent.

---

## 7. Navigation et architecture de l'information

**Faits observés**
- Tiroir gauche 395 px (390 mobile), blanc, z 1060, 124 liens : DESTINATIONS (accordéon par pays avec drapeaux), INSPIRATION, À PROPOS, COLLECTIONS, CONCIERGERIE, REJOIGNEZ NOTRE PORTFOLIO, ACHETER UNE MAISON, PARTENAIRES DE VOYAGE, bloc « Nos conseillers sont joignables au +33 1 73 03 02 02, tous les jours de 07h00 à 22h00 », Contactez-nous, « Français – Eur ». Items 18 px uppercase, 40–56 px (36–48 mobile).
- Pages internes : barre de recherche complète dans le header (RECHERCHER 132×46), téléphone en clair, OBTENIR L'APP, cœur (« Mes coups de cœur »), compte (Google / Apple / e-mail, « Agents de voyage »).
- Fil d'Ariane villa « Tout voir › Espagne › Îles des Baléares › Ibiza » (`/fr/recherche?destinationId=15/16/17`), répété en bas.
- Liste : TOUS LES FILTRES (compteur « 1 »), PIÈCES, BUDGET, COLLECTIONS ; tri « recommandées » ; grille/liste ; « Ajouter vos dates pour afficher les prix » ; 17 propriétés ; inserts « Vous ne trouvez pas… » (PLANIFIER UN APPEL) et « Quand souhaitez-vous partir ? » (INDIQUER MES DATES).
- Anomalies : `/location-villas-luxe/ibiza` sert canonical, title (« Villas de luxe de luxe animaux acceptés ») et H1 (« Villas animaux acceptés », 14 px) du filtre actif ; « +33 1 73 03 02 02 » avec `href="tel:+1 646 851 2321"` ; lien « Français – Eur » de 90×20 px sur mobile.
- Étapes vers une offre : home → carte = 1 clic ; home → recherche → villa = 2 ; menu → destination → villa = 3.
- Réservation persistante : **oui sur la villa** (carte sticky 488×487 desktop ; barre 390×95 mobile) ; **non sur la home** (header non sticky, aucun CTA fixe).
- `<main>` absent (sauf quiz), pas de skip link, 5–32 boutons sans nom.

**Interprétation**
- Hiérarchie lisible (Destinations / Inspiration / À propos) mais le tiroir mélange voyageurs, propriétaires, immobilier et agences : trois rubriques sur huit ne concernent pas le client. Trouver une maison est facile ; trouver une prestation exige le menu ou 3 900 px de scroll.
- Frustrations : interstitiel dates, home sans header sticky, état de filtre injecté dans l'URL générique.

**Enseignements réutilisables**
- Moteur compact dans le header interne (46 px) ; inserts d'aide humaine dans la grille toutes les 4–6 cartes ; séparer les audiences dans le menu.

---

## 8. Parcours de réservation et conversion

**Faits observés**
- Premier CTA : RECHERCHER (y ≈ 250–300) ; premier CTA « réserver » : « RÉSERVEZ VOS VACANCES » à y 1 222 desktop / 1 299 mobile, lié à `/fr/recherche` (une recherche, pas une réservation).
- Vocabulaire : *Rechercher, S'inspirer, Réservez vos vacances, Explorez, Échanger avec un conseiller, Contactez-nous, Découvrir, Faire une demande, Réserver, Planifier un appel, Sélectionner, Indiquer mes dates* — découvrir / demander / réserver sont distingués.
- Villa : dates pré-remplies 05-09 → 12-09-2026 (samedi → samedi), tableau « PRIX ET DISPONIBILITÉS » par semaine (« min. 5 nuits », « 33 160 € pour 7 nuits », SÉLECTIONNER), navigation par mois.
- Transparence : total visible avant clic ; « Taxe de séjour non incluse, prix à confirmer avec nos Travel Advisors » ; prix des alternatives aux mêmes dates (33 660 €, 24 685 €, 33 915 €) ; FAQ 5 questions (fonctionnement, paiement, caution, arrivée anticipée, annulation) + assurance « Koala Flex » ; licence ETV-1029-E ; check-in 16:00 / check-out 11:00.
- Réassurance : Trustpilot (iframe 260×30), « 4 sur 5 », 1 avis (sept. 2025), carrousel de 3 témoignages datés (déc. 2025–janv. 2026), portrait du conseiller + PLANIFIER UN APPEL, horaires 07h–22h dans la carte sticky, presse et Condé Nast.
- Services : « Services de la maison » (petit-déjeuner, Property Manager), « Services de la Collection Signature » (ménage 6×/semaine, concierge dédié, accueil, indispensables, restaurants), « Services à la carte » en accordéon ; guide externe `magazine.lecollectionist.com/fr/guide-ibiza…`.
- Étape 1 « FAIRE UNE DEMANDE » (`flow-villa-cta-step1`) : le formulaire remplace la carte sticky sans changer de page — RETOUR, « Compléter vos informations », « Un conseiller prendra contact avec vous », Prénom*, Nom*, E-mail*, Téléphone mobile* (indicatif 🇺🇸 par défaut), consentement, ENVOYER MA DEMANDE. Même domaine, même onglet, même identité.
- Contact : sélecteur « Comment pouvons-nous vous aider ? », « Savez-vous déjà où partir ? Oui/Non », zone au placeholder budgétaire, bouton gris désactivé.
- Aucun bénéfice de réservation directe, aucune offre promotionnelle ; angle saisonnier (« Votre hiver commence ici »).

**Interprétation**
- Tunnel **hybride** : self-service jusqu'au prix et au calendrier, puis conseiller (« prix à confirmer »). Quatre voies simultanées (RÉSERVER, FAIRE UNE DEMANDE, PLANIFIER UN APPEL, téléphone) rassurent à 33 000 € mais diluent. Transparence prix forte pour le segment.
- Ruptures : interstitiel dates et absence de prix sans dates sur la liste ; sous-domaine magazine ; indicatif US sur une page française.

**Enseignements réutilisables**
- Formulaire in-place remplaçant la carte sticky ; prix des alternatives aux mêmes dates ; tableau hebdomadaire plus lisible qu'un calendrier pour des locations à la semaine.

---

## 9. Pages propriété et destination (desktop et mobile)

### 9a. Villa Blue, Ibiza (`/fr/location-luxe/villa-blue-ibiza`)

**Faits observés — desktop (8 484 px, 2 190 mots)**
- Ordre : (1) photo 1440×630 + « VOIR TOUTES LES PHOTOS (56) » 261×44 ; (2) fil d'Ariane ; (3) H1 « VILLA BLUE » 32 px, lieu, « 10 voyageurs · 5 chambres · 5 salles de bain · 630 m² », cœur, partage ; (4) description tronquée à 3 lignes + « LIRE TOUTE LA DESCRIPTION + » (174×12 px) ; (5) « Collection Signature ◇◇◇ » + EN SAVOIR PLUS ; « Avis clients ★ 4 » ; (6) « LES INCONTOURNABLES » 8 pictos (piscine, vue mer/montagnes, climatisation partielle, pétanque, salle de sport, barbecue, jardin, réserve naturelle) ; (7) « DÉCOUVREZ LES CHAMBRES » carrousel 348×228, « 1 Lit double inséparable (200×200), dressing, TV, terrasse, coffre-fort… » + chips ; (8) accordéon « TOUS LES ÉQUIPEMENTS » (Extérieur / Intérieur) ; (9) « SERVICES INCLUS » ouvert, « SERVICES À LA CARTE » fermé ; (10) tableau prix ; (11) « APERÇU DE LA PROPRIÉTÉ » mosaïque 1 + 4 (784×324, 388×315) ; (12) « BON À SAVOIR » : tronçon non pavé, barbecue au gaz, employé de maison logé sur place, route sinueuse ; (13) encart #f7f7f7 « DES QUESTIONS À PROPOS DE VILLA BLUE ? » portrait rond + PLANIFIER UN APPEL ; (14) « LEURS SOUVENIRS » ; (15) « INFORMATIONS COMPLÉMENTAIRES » ; (16) « LES ALENTOURS » carte Leaflet/OSM 342×350 avec cercle de confidentialité, ENVIRONNEMENT (hors ville, sans voisinage, réserve naturelle) / À PROXIMITÉ (plage 11 min, restaurants 10 min, commerces 20 min en voiture) ; (17) « CHOISISSEZ L'EXTRAORDINAIRE » mosaïque + DÉCOUVRIR ; (18) FAQ ; (19) « RECOMMANDÉES POUR VOUS » 8 villas (dates, « +10 pers. ») ; (20) témoignages sur fond sombre ; (21) fil d'Ariane ; footer.
- Carte sticky 488×487 (`sticky top-6`, z 1020) : nom, collection, Dates, « Total – 7 nuits 33 160 € », RÉSERVER 438×44, FAIRE UNE DEMANDE, horaires + téléphone.
- Images 107 (62 lazy), **32 sans alt, 9 vides**, 39 SVG. JSON-LD `Accommodation` (occupancy 10, amenityFeature fitnessRoom, wineCellar, petanque…, Sant Joan de Labritja 07815).
- Perf : TTFB 222 ms, FCP 1 520 ms, DCL 2 022 ms ; 630 requêtes, 14,1 Mo (scripts 10,6 Mo / 415 requêtes).

**Faits observés — mobile (8 153 px)**
- Hero 390×340 avec « 1/56 » ; même ordre en une colonne ; chambres 356×237 ; carte pleine largeur ; portrait conseiller 140 px.
- Barre sticky 390×95 (y 749, z 1020) : « 33 160 € | du 05 au 12 sept. 2026 » + FAIRE UNE DEMANDE 179×35 contour + RÉSERVER 163×35 plein : **35 px** de haut. Liens « LIRE PLUS » 71×12, « EN SAVOIR PLUS » 90×14, « DÉCOUVRIR LES AVIS » 116×14.
- Smart banner 62 px + One Tap 144 px (y 700–844) partagent l'espace avec la barre sticky.

**Interprétation**
- Ordre commercial précis : émotion → faits → niveau de service → arguments → couchages (projection pour un groupe) → prix → photos → réserves honnêtes → humain → preuve → pratique → inspiration → conditions → alternatives. Le « Bon à savoir » est un marqueur de crédibilité rare.
- Projection par la logistique (lits, équipements par chambre) ; l'expérience est renvoyée à la conciergerie et au guide, tard dans la page (y > 5 800).
- Sur mobile, le bon pattern (prix persistant) est desservi par des cibles de 35 px et 12 px.

### 9b. Liste Ibiza (`/fr/location-villas-luxe/ibiza`)

**Faits observés**
- Desktop : header sticky (« Ibiza ✕ »), filtres sticky 150 px, colonne 864 px à 2 cartes 400×267 (H2 20 px uppercase, lieu, « 10 voyageurs · 5 chambres · 6 sdb », 2 chips, « Collection Essential ◇ », cœur, badge « NOUVEAUTÉ »), carte Mapbox sticky 576 px avec pins noirs ; inserts humains ; footer avec 4 valeurs (« À l'écoute & proactifs », « Sur le terrain », « Rien que le meilleur », « À votre (dé)mesure ») + témoignages. Modale « DÉCOUVREZ LES PROPRIÉTÉS DISPONIBLES À VOS DATES » (CHOISIR MES DATES / JE NE SAIS PAS ENCORE) sur overlay 50 % au chargement.
- Mobile : bande carte ≈ 350 px en haut, état vide « jumelles », recherche « Ibiza | Dates | Voyageurs » 358×48 + filtres sticky 111 px, cartes 390×260 à carrousel de 6 photos, prix absents sans dates.
- Skeletons gris sur plusieurs cartes des captures desktop. Perf : 896 requêtes, 26,4 Mo (scripts 22,5 Mo : bundle `C48NorBM.js` 1,69 Mo, worker Mapbox 717 Ko ×6, Algolia, Trustpilot ×19) ; mobile 585 requêtes, 17,8 Mo.

**Interprétation**
- Moteur de liste classique bien exécuté (carte sticky, filtres, inserts) mais page la plus lourde du site, avec une modale avant le premier résultat. La continuité « RECOMMANDÉES POUR VOUS » (dates et groupe repris) est solide.

**Enseignements réutilisables**
- Couchages exhaustifs par chambre ; « Bon à savoir » avant réservation ; carte sticky desktop + barre sticky mobile avec deux niveaux d'engagement.

---

## 10. Copywriting

**Faits observés**
- Titres 2–5 mots en capitales, injonctifs ou possessifs : « PARTAGEZ L'EXTRAORDINAIRE », « VOTRE HIVER COMMENCE ICI », « IMAGINONS VOS PROCHAINES VACANCES », « LEURS SOUVENIRS ».
- Structure surtitre + mot display : « DES MAISONS / UNIQUES », « L'ART DU / SUR-MESURE », « UNE CONCIERGERIE / LOCALE ».
- Paragraphes d'1–2 phrases, centrés, avec un chiffre (2 300, 10 bureaux, 50 destinations, « 95 chalets à louer »).
- Lexique : *maison* (jamais « bien »), *conseiller / Travel Advisors / concierge*, *collection / portfolio*, *sur-mesure*, *âme, singularité, extraordinaire, inoubliable, secrets, portes, escapade*.
- Sensoriel : concentré dans les descriptions de villas (jardin méditerranéen, pins, cyprès, tons crème) ; les pages marque restent abstraites.
- « Luxe » absent des H2 de la home (réservé au title, au H1 de bas de page, à « Luxe intemporel ») ; on dit « extraordinaire », « sur-mesure », « niveau de service ».
- Technique : dense sur la villa (m², 200×200, ménage 6×/semaine, 16:00, 11 min), absente de la home.
- Services nommés comme un menu (« Chef à domicile », « Baby-sitter ») ; expériences titrées comme des films (« Sur les traces du Parrain », « Michelin au sommet »).
- Témoignages titrés (« DIX ANS DE MARIAGE », « COMPLIMENTS AU CHEF », « DIFFICILE DE PARTIR »), signés « Mr D. — MAS PRADAU, PROVENCE ».
- Micro-textes de qualification : placeholder 10 000 €, « prix à confirmer », horaires 07h–22h. Bugs : « de luxe de luxe », smart banner en anglais, « A PROXIMITÉ ».

**Interprétation**
- Ton sobre, « nous » institutionnel, impératif de politesse ; le luxe est signifié par la retenue et la précision. Les titres de témoignages transforment un avis en récit : mécanisme le plus distinctif. CTA longs et descriptifs, au détriment de la concision.

**Enseignements réutilisables**
- Surtitre en petites capitales + un mot display ; titrer chaque témoignage ; un chiffre par paragraphe de marque ; expériences nommées comme des films, services comme un menu.

---

## 11. Photographie et vidéo

**Faits observés**
- Hero : mer, piscine à débordement, pin parasol en contre-jour, silhouette de femme de dos, voile 30 %, pas de poster ; mobile : villa ocre aux volets verts, enfants et table dressée (1,01:1).
- Cartes maisons : chalets sous neige et intérieurs bois/lumière chaude, cadrages frontaux, sans personnes (0,74 home, 1,43–1,5 listes).
- Conciergerie (home) : 4 portraits d'action (cavalier en rouge dans le désert, skieur hors-piste vu du ciel, apnéiste, voilier). Page conciergerie : triptyque de mains (bouquet, homard, citrons) en 0,82 ; expériences en N&B (horloge d'Orsay) ; vidéo 604×536 avec contrôles, poster WebP, 9,8 Mo.
- Collections : collages de 3–4 photos avec le mot « SIGNATURE » / « ICONIC » en image, humains présents (tennis, femme en blanc, chef). Propriétaires : portrait N&B, femme et chien. Destinations : paysages 1,5 sans humains (crêtes, pistes, cabanes ostréicoles, Es Vedrà).
- Villa Blue : 56 photos, drone en ouverture, extérieurs, chambres claires, détails, lumière dure de midi. Témoignages : ciel, soleil orangé en 1:1.
- Proportion lieu/expérience : home ≈ 60/40 ; villa ≈ 95/5.

**Interprétation**
- Deux registres nets : **inventaire** (architecture droite, ciel bleu, vide) et **récit** (humains en action, mains, N&B), ce dernier réservé aux pages marque : on ne trompe pas sur la maison. La palette photo (bleu, blanc, bois, neige) compense l'absence de couleur d'interface. Vidéos : ambiance en hero (non vérifiée), manifeste lourd en page conciergerie.

**Shot list**
1. Vidéo hero 10–20 s, plan large lent, eau/paysage, silhouette de dos, boucle propre, poster, photo de repli mobile, < 3 Mo par version.
2. Drone d'ouverture par propriété (2,3:1).
3. Façades frontale et contre-plongée à la meilleure saison (3:2 et 3:4).
4. Pièce de vie avec fenêtre sur le paysage, lumière du matin (4:3).
5. Chaque chambre, lit fait, vue par la fenêtre (3:2).
6. Piscine/terrasse dressée sans personnes (3:2 et carré).
7. Détails « mains » (bouquet, produit local, verre) en 4:5, série de 3.
8. Expériences humaines plein cadre (sport, bateau, cheval, spa) en 9:16 pour mosaïques décalées.
9. Portraits ronds des conseillers ; portrait propriétaire N&B en situation.
10. Paysage par destination sans maison (3:2 + carré) ; images d'humeur carrées (ciel, soleil, eau) pour les témoignages.
11. Collage typographique avec le mot-clé de gamme en image.

---

## 12. Mobile

**Faits observés**
- Hero : image 390×387, titre Ayer 48 px, pastille S'INSPIRER 358 px, formulaire empilé + RECHERCHER 358×44.
- Menu : tiroir plein écran 390 px, items 342×36–48, 18 px uppercase.
- Titres : H2 32 px conservés (« DESTINATIONS EN VOGUE » sur deux lignes), H1 villa 32 px, cartes 24 px, liste 20 px.
- Rythme : home 10 878 px, villa 8 153, liste 9 326 + footer 1 820 ; carrousels horizontaux natifs (`horizontal: 1–2`).
- Animations conservées : reveals (12), skeletons, accordéons, `slideDown` du smart banner, quiz 1,5 s ; supprimées : vidéo hero, hovers.
- Boutons : RECHERCHER 358×44 ; RÉSERVEZ VOS VACANCES 223×44 centré ; CONTACTEZ-NOUS 358×46 ; barre villa 35 px ; filtres 35 px ; liens 12 px ; chips 12 px.
- Liste : smart banner 62 + header 72 + bloc sticky 111 = **245 px fixes en haut** (29 % du viewport) + One Tap 144 px en bas.
- Vitesse : home TTFB 367 ms, FCP 728 ms, DCL 893 ms, 280 requêtes, 7,9 Mo (scripts 5,5 Mo) ; villa FCP 1 336 ms, DCL 2 494 ms, 8,4 Mo ; liste 17,8 Mo.
- Lisibilité : body 16 px home, 14 px villa ; `maximum-scale=1` sur toutes les pages mobiles (zoom bloqué).
- Différences : téléphone seulement dans le tiroir ; loupe ajoutée sur la liste ; carte en bandeau haut ; état vide « jumelles ».

**Interprétation**
- Adaptation soignée de la structure (empilement, carrousels natifs, prix sticky, image à la place de la vidéo) mais écran utile amputé par trois surcouches et zoom bloqué ; tailles de cibles en contradiction avec le soin desktop.

**Enseignements réutilisables**
- Image mobile dédiée au lieu de la vidéo ; barre prix + deux CTA ≥ 44 px ; jamais smart banner + One Tap ; zoom autorisé.

---

## 13. Performance, accessibilité, SEO

**Faits — performance**
- Home desktop : TTFB 377 ms, FCP 716 ms, DCL 1 274 ms, load 1 353 ms ; **527 requêtes, 21,1 Mo** : média 8,5 Mo (vidéo 4 288 + 4 224 Ko en 2 requêtes 206), scripts 9,8 Mo sur **348 requêtes**, images 1,48 Mo (78), CSS 552 Ko (56 feuilles), fonts 215 Ko (13).
- Plus gros scripts : GTM 710 Ko (×2), Axeptio 696 Ko, gtag ×4 (594 / 472 / 461 / 418 Ko, dont `G-XXXXXXXXXX` non configuré), Google GSI 266 Ko, bundle Nuxt 212 Ko ; CSS total 308 Ko.
- Villa 630 requêtes / 14,1 Mo / FCP 1 520 ms ; liste 896 / 26,4 Mo ; conciergerie 21,7 Mo dont vidéo 9,8 Mo chargée partiellement sans lecture.
- Tiers : googlesyndication, Axeptio, Google accounts, GA, ipregistry, Trustpilot, Mapbox, Algolia, AppsFlyer, Bugsnag, tuiles OSM, unpkg (Leaflet), herokuapp.
- Lazy : 60/66 images home, 62/107 villa ; `srcset` 53/66 ; jpg majoritaire (43), 1 webp ; hero jpg `q=50`. Skeletons à ratio fixe ; `preload=metadata`.

**Faits — accessibilité**
- Contrastes : #202020/#ffffff 16,3:1 ; #757575/#ffffff 4,6:1 ; #757575/#f7f7f7 4,3:1 (sous AA texte normal) ; #4c4c4c/#f7f7f7 8,0:1 ; #cacaca/#ffffff 1,6:1 ; #aaaaaa/#ffffff 2,3:1 ; blanc sur voile 30 % non calculable.
- `outline: none` ×161–180 ; ring `focus:shadow-focus` déclaré (non vérifié). Landmarks : header 1, nav 1, footer 1, **main 0** (sauf quiz) ; pas de skip link ; `aria-hidden` ×12 (villa) / ×58 (liste).
- Boutons sans nom : 5 (home), 18 (villa), 32 (liste). Alt manquants : 0 / 32 (+9 vides) / 56 sur 56 (quiz) / 1 (liste).
- Formulaires : labels visibles, astérisques, consentement explicite, bouton désactivé #cacaca.
- Reduced motion : 3 règles ; observé : 4 éléments animés et 73 transitions inchangés, vidéo `autoplay` maintenue. Petites tailles : 4 (home), 29–32 (villa, 10 px ×37). `maximum-scale=1`.

**Faits — SEO**
- Home : title 71 caractères, description, og complet (image 600×315), canonical, hreflang fr / en / x-default, lang fr, 1 H1 (20 px, bas de page), wordCount 535, 138 liens internes / 18 externes.
- JSON-LD : Organization (@id, logo, 2014, adresse, tél., sameAs), ContactPoint (FR, French/English), TouristDestination (liste), Accommodation (villa).
- Villa : title « Villa Blue, Ibiza — 5 chambres pour 10 personnes », description = début de la description commerciale (300 caractères), 2 190 mots, H1 unique.
- Liste : title « de luxe de luxe », canonical vers `/villa-animaux-acceptes`, H1 14 px en bas, 1 141 mots. Satellites (`/france`, `/chalet-piscine`, `/espagne`) : mêmes gabarits, titles dupliqués « Villas animaux acceptés en … » ; page immobilier H1 16 px ls 4,8 px. Quiz : 69 mots, sans header/footer.

**Interprétation**
- TTFB/FCP bons (SSR Nuxt), mais poids et surtout nombre de scripts (348–619 requêtes JS) hors norme : la moitié du poids est mesure et consentement. Vidéo sans poster et double requête aggravent le cas des connexions lentes.
- A11y : fondations correctes (lang, labels, contraste principal) ; défauts structurants : `<main>` et skip link absents, icônes muettes, zoom bloqué, reduced-motion inopérant.
- SEO très structuré ; faiblesse : l'état de filtre « animaux acceptés » propagé aux URL génériques (probable bug de session). L'immersion est modeste (une vidéo courte) : la lourdeur vient de la couche technique, le compromis est mal placé.

**Enseignements réutilisables**
- Vidéo avec `poster`, une source par device, coupée sous reduced-motion ; `aria-label` sur toute icône dès le composant de base ; ne jamais lier canonical/title à un filtre.

---

## 14. Conclusion

### 15 meilleurs éléments
1. Système ◇ / ◇◇ / ◇◇◇ répercuté sur chaque carte, page et service.
2. Formule surtitre + mot display Ayer (« UNIQUES », « SUR-MESURE », « LOCALE »).
3. Moteur à 4 champs intégré au header 72 px des pages internes.
4. Pastille « Vous ne savez pas où partir ? S'INSPIRER ».
5. Compteurs « 95 chalets à louer » sur les destinations.
6. Carte sticky desktop avec total 7 nuits, deux niveaux d'engagement, formulaire in-place avec RETOUR.
7. Barre sticky mobile prix + dates + FAIRE UNE DEMANDE / RÉSERVER.
8. Tableau « PRIX ET DISPONIBILITÉS » hebdomadaire avec minimum de nuits.
9. « DÉCOUVREZ LES CHAMBRES » avec couchages exacts (200×200, inséparable).
10. « BON À SAVOIR » listant les contraintes réelles.
11. Encart conseiller avec portrait, PLANIFIER UN APPEL, horaires 07h–22h répétés.
12. Inserts humains dans la grille de résultats.
13. Témoignages titrés comme des récits.
14. Mosaïque de quatre portraits décalés ; collages typographiques des collections.
15. SEO : hreflang, JSON-LD Organization + Accommodation + TouristDestination, H1 unique, 2 190 mots par fiche.

### 5 faiblesses / limites
1. Poids et requêtes (21–26 Mo, 527–896 requêtes, 348–619 scripts) dominés par GTM, gtag ×4, Axeptio, GSI, Mapbox ×6.
2. Interruptions empilées : cookies + newsletter (desktop), smart banner + One Tap + cookies (mobile), modale dates sur la liste.
3. Accessibilité : `<main>` absent, 5–32 boutons sans nom, 32 alt manquants sur la villa, `maximum-scale=1`, reduced-motion sans effet sur la vidéo.
4. Cibles mobiles : boutons 35 px, liens 12 px, 245 px fixes en haut de la liste.
5. Incohérences : « de luxe de luxe », canonical/H1 liés au filtre, numéro affiché ≠ `href tel:`, indicatif US, smart banner en anglais.

### 10 principes réutilisables
1. Pictogramme de niveau de service sur chaque carte plutôt qu'un paragraphe.
2. Display serif limitée à un mot par bloc ; sans uppercase à interlettrage 1 px ailleurs.
3. Header 72 px : logo, moteur compact, téléphone, favoris, compte — rien d'autre.
4. Deux voies permanentes : self-service et assisté.
5. Prix total sans clic sur la page produit ; alternatives aux mêmes dates en bas.
6. Couchages détaillés et « bon à savoir » avant réservation.
7. Alternance blanc / #f7f7f7 et rayon 0 pour une rigueur sans accent.
8. Décalages statiques et collages plutôt qu'animations lourdes.
9. Image dédiée sur mobile à la place de la vidéo.
10. Skeletons à ratio fixe sur toute grille de médias.

### À ne PAS copier (propre à la marque)
- Le nom et le concept « Collectionist / collections », le trio Essential / Signature / Iconic et les losanges ◇.
- Les polices Brown, GT Alpina, Ayer (licences ; hypothèse sur les fonderies).
- « Partagez l'extraordinaire » et les titres du manifeste.
- Les collages « SIGNATURE » / « ICONIC », le tampon « Présence locale », les visuels (cavalier rouge, homard, Es Vedrà) et les témoignages nommés.

### Notes /10

| Axe | Note | Justification |
|---|---|---|
| Branding | **8** | Promesse chiffrée (2 300 maisons, 10 bureaux, 50 destinations), collections sur 5 gabarits, presse / Condé Nast / Trustpilot ; mais home close sur un message propriétaires + H1 SEO, sans témoignage. |
| Direction artistique | **7,5** | Palette bichrome cohérente, trio typographique distinctif, ratios maîtrisés (0,74 / 1,43 / 1,5 / 0,57) ; fiche villa dense (14 px dominant, 37 éléments en 10 px), composants tiers hors charte. |
| Animations | **5** | 0 parallaxe, 0 curseur, 0 transition de page visible, 0 hover mesuré sur cartes ; l'existant est propre (accordéon 0,5 s, skeleton 2 s) mais reduced-motion inopérant. |
| UX | **7** | Moteur dans le header, fil d'Ariane, filtres et carte sticky, inserts humains, informations pratiques complètes ; interstitiel dates, header non sticky sur home/villa, menu à 3 audiences, `tel:` incohérent. |
| Conversion | **7,5** | Total visible avant clic, tableau hebdo, carte sticky + formulaire in-place, 4 voies de contact, FAQ, prix des alternatives ; RÉSERVER non vérifié, aucun avantage direct, modale newsletter et interstitiel. |
| Mobile | **6,5** | Empilement propre, image au lieu de vidéo, barre prix sticky, FCP 728 ms ; mais 62 + 144 px + cookies, boutons 35 px, liens 12 px, zoom bloqué, 245 px fixes sur la liste. |

**Note globale : 7 / 10.** Site de plateforme rigoureux : identité typographique nette, information produit la plus complète du panel (couchages, contraintes, prix hebdomadaires, conseiller nommé), SEO structuré. Il est pénalisé par une couche technique/marketing disproportionnée (≈ 10 Mo de scripts, 4 gtag, One Tap, smart banner) qui dégrade performance, accessibilité et calme visuel, et par l'absence de tout dispositif motion ou scroll capable de faire vivre la promesse « extraordinaire ».

---

## Observations clés à conserver pour la phase comparative

- Hero desktop 458 px (51 % du viewport), vidéo 3,14:1 sous voile 30 %, ≈ 8,5 Mo en 2 requêtes partielles, sans poster ; mobile : image 390×387, pas de vidéo.
- Header 72 px transparent, `static` sur home et villa, `sticky` sur la liste avec moteur intégré (Destination | Arrivée → Départ | Voyageurs | RECHERCHER 132×46).
- Typo : Brown (body 16/22,4 ; titres uppercase ls 1 px) + GT Alpina Light (intro 16–18 px) + Ayer Medium (display 60 / 48 px, 4 occurrences par page) ; échelle 60 / 36 / 32 / 24 / 20 / 18 / 16 / 14 / 12 / 10 ; H2 32 px identiques desktop et mobile ; villa dominée par le 14 px (236).
- Palette sans accent (#202020, #ffffff, #f7f7f7, #eaeaea, #757575) ; rayon 0 partout sauf icônes rondes 32–40 px ; boutons 44–52 px, 14 px uppercase.
- Container 1 280 px ; villa 784 + 488 px sticky `top-6` ; liste 864 + 576 px carte Mapbox `100dvh`.
- 3 collections ◇/◇◇/◇◇◇ = ménage 1× / 3× / 5× par semaine, visibles sur chaque carte.
- Villa : 56 photos, « 10 voyageurs · 5 chambres · 5 sdb · 630 m² », « 33 160 € / 7 nuits » avant clic, tableau hebdo (min. 5 nuits), couchages 200×200, « Bon à savoir » 4 contraintes, conseiller avec photo et horaires 07h–22h, JSON-LD Accommodation, 2 190 mots.
- Mobile villa : barre sticky 390×95 (prix + FAIRE UNE DEMANDE 179×35 + RÉSERVER 163×35) ; liens 12 px ; `maximum-scale=1`.
- Interruptions : Axeptio 696 Ko persistante, modale newsletter au 1er scroll, smart banner 62 px + One Tap 144 px mobile, modale dates sur la liste.
- Réseau : home 527 requêtes / 21,1 Mo (scripts 9,8 Mo sur 348 requêtes, GTM 710 Ko, gtag ×4 dont `G-XXXXXXXXXX`) ; liste 896 / 26,4 Mo (bundle 1,69 Mo, Mapbox worker 717 Ko ×6) ; villa 630 / 14,1 Mo ; TTFB 222–454 ms, FCP 580–1 520 ms.
- Motion : 17–23 keyframes, 0,8 s ×54, `cubic-bezier(.4,0,.2,1)` ×21, reveals ×6–49, hover image 1.01 → 1.1 en 0,35 s ; 0 parallaxe, 0 curseur, 0 sticky narratif, 0 hover cartes ; 3 règles reduced-motion sans effet sur la vidéo.
- A11y : `main` 0, skip link 0, `outline:none` ×161–180, boutons sans nom 5 / 18 / 32, alt manquants 0 / 32 / 56 ; #757575 sur #f7f7f7 = 4,3:1, #cacaca sur blanc = 1,6:1.
- SEO : hreflang fr/en/x-default, JSON-LD Organization (2014, Paris) + ContactPoint + TouristDestination + Accommodation ; H1 home 20 px en bas ; title « de luxe de luxe » et canonical/H1 liés au filtre « animaux acceptés ».
- Copy : titres 2–5 mots uppercase, un chiffre par paragraphe, témoignages titrés, expériences nommées comme des films, ticket « 10 000 €/semaine » dans le contact.
- Stack (preuves) : Nuxt (`_nuxt/`, `nuxt-loading-indicator`), Tailwind (`--tw-*`, `z-[1060]`), Swiper, Mapbox GL (liste) + Leaflet/OSM (villa), Algolia, Axeptio, GTM/GA4/Ads, AppsFlyer, Bugsnag, Trustpilot, Google Identity ; l'hypothèse Next.js/React est infirmée.
