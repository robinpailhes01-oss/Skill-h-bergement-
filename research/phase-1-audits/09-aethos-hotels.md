# Fiche d'audit — Aethos Hotels (collection hôtels + clubs + retraites)

Clé : `aethos` · Analyse du 2026-09-04 · Chromium headless via Playwright, 1440×900 (desktop) et 390×844 DPR 2 (mobile). Série 2 « au-delà du quiet luxury » : choisi pour son branding nouvelle génération, sa direction éditoriale et l'organisation d'une collection hôtels + clubs + retraites.

---

## 0. En-tête

**Nom** : Aethos (Aethos Hotels & Resorts, siège LinkedIn « originalhospitality », Suisse). **URL de départ** : https://www.aethos.com/. Title home : « Aethos | Luxury Boutique Hotels, Community Clubs & Wellness Retreats ». Huit destinations : Ericeira, Sardaigne, Majorque, Monterosa, Saragano, Milan, Londres Shoreditch, Lisbonne (« coming soon »).

### Pages étudiées

| Label outil | Page réelle | URL | Desktop | Mobile |
|---|---|---|---|---|
| home | Accueil | https://www.aethos.com/ | oui (+ sweep 15 paliers) | oui |
| destinations / experiences (mal étiqueté) | Liste des destinations | https://www.aethos.com/destinations | oui (2 passes identiques) | non |
| destination | Hôtel Aethos Ericeira | https://www.aethos.com/destinations/ericeira | oui (pop-up promo sur toutes les captures) | non |
| spa (mal étiqueté) | Hôtel Aethos Mallorca | https://www.aethos.com/destinations/mallorca | oui | non |
| club | Club de membres | https://www.aethos.com/club | oui | non |
| retreats / dining (mal étiqueté) | Retraites | https://www.aethos.com/retreats | oui (pop-up promo) | non |
| wellness | Wellness | https://www.aethos.com/wellness | oui | non |
| experience | Expériences | https://www.aethos.com/experience | oui | non |
| journal | Journal | https://www.aethos.com/journal | oui | non |
| about | À propos | https://www.aethos.com/about | oui | non |
| contact | Contact | https://www.aethos.com/contact | oui | non |
| booking | Sonde CTA sur la page Ericeira → moteur hotelchamp | https://www.aethos.com/destinations/ericeira?p=base&c=search&lg=en-US | oui (étape 1 non visible, voir limites) | non |

### Limites de l'observation

- **Vidéo hero** : iframe Vimeo (`player.vimeo.com/video/1216151776`, `background=1&muted=1&loop=1`) affichant « Player error » en headless (`home-01-hero`) ; sur `home-04-reduced-motion` et mobile, seul un dégradé sombre est visible. Le rendu vidéo réel n'est **pas vérifiable** ; le réseau prouve toutefois le chargement des segments (xhr Vimeo 1 858 + 3 505 + 3 595 + 4 245 Ko sur la home).
- **ScrollSmoother** (GSAP) : le `div#smooth-wrapper` est `fixed` 1440×900 ; les captures `02-full` sont blanches/vides et n'ont pas été utilisées. Le lissage du scroll lui-même n'est pas vérifiable.
- **Header invisible** sur toutes les captures desktop « normales » de la home (`home-01-hero`, `home-sweep-*`) alors que le DOM le contient (`site-header`, 78 px, texte « MENU CLOSE EN BOOK NOW ») et qu'il apparaît correctement sur `home-04-reduced-motion` et sur les pages secondaires (wellness, journal, Mallorca). **Hypothèse** : animation d'entrée GSAP (`anim-load-hero_parent`) non résolue en headless. Le header est traité comme présent.
- **Pop-up promotionnel** « Return to Wholeness Autumn Retreat » (`div.promopop-holder`, `fixed`, z-index 1000, fond flouté) recouvre **toutes** les captures d'Ericeira et de Retreats, bloque le scroll (les 15 paliers d'Ericeira restent à y=10127 ; les 6 captures `dining-03-scroll*` ont exactement la même taille de fichier). La structure de la page hôtel est donc lue dans le DOM d'Ericeira et vue sur les captures de Majorque (`spa-*`).
- **Sonde réservation** : l'heuristique a cliqué deux fois sur le lien « Facebook » du footer (home → page de login Facebook, `home-06-booking-step1`). Sur Ericeira, l'URL finale `?p=base&c=search&lg=en-US` et les iframes `ws.hotelchamp.com/storage-relay` + Stripe v3 prouvent que le moteur hotelchamp s'est ouvert en overlay sur le même domaine, mais l'étape 1 est cachée par le pop-up promo : **non visible**.
- **Menu ouvert** : aucune capture `05-menu-open` (desktop `menu: None`, mobile « no burger found » : le bouton est un `div` sans rôle). Structure du menu lue dans les 46 `navLinks` cachés.
- Pas de capture mobile des sous-pages ; LCP `null` ; Lighthouse indisponible ; curseur tactile, transitions de page et preloader Lottie (`.site-loader`, `opacity: 0` au moment de la capture) non observables.

---

## 1. Positionnement de marque

**Faits observés**
- Meta description home : « Join a community of conscious explorers… design-led luxury boutique hotels and wellness retreats across Europe ». H1 home « THE RULES ARE DIFFERENT HERE » (72 px, capitales serif, blanc sur vidéo). Page club : « A COMMUNITY FOR MORE-SEEKERS » puis H1 « MORE CONNECTION. MORE EXPERIENCES. INFINITE POSSIBILITIES. ».
- Architecture de marque lisible dans le menu (46 liens) : **Destinations** (8 hôtels, chacun « Aethos + lieu, pays »), puis une entrée manifeste « Different rules » (`/therulesaredifferenthere`), **membership** (`/club`), Wellness, Experiences, Retreats, Shop (aethosshop.com, externe), Gift cards, Journal, about us ; sélecteur 5 langues (EN/IT/PT/ES/FR via Weglot) ; lien portail membres `portal.aethos.com`.
- La home hiérarchise : promesse (hero) → manifeste (« places to stay, engage, and connect… a new community ») → carrousel des 7 hôtels ouverts → Expériences → Wellness → Communauté/club (seule section sombre, « 50+ countries ») → Retraites → Journal.
- Pages hôtels : sous-navigation propre à chaque hôtel (STAY · DINE · EXPERIENCE · WELLNESS · HAPPENINGS · RETREATS · PROMOTIONS · VOUCHERS · EVENT SPACES · GALLERY · CONTACT (+ MEMBERSHIP à Majorque)) et **accent couleur par destination** : footer et bouton BOOK NOW passent de #2a2826 (marque) à #72818b bleu-gris pour Ericeira et Majorque ; le club est sur #1e1d1b.
- Club : trois formules tarifées publiquement (Connect 650 €/an, 6 visites par club ; One 175 €/mois · 1 800 €/an ; Unlimited 240 €/mois · 2 500 €/an, « all memberships are annual »). Aucun prix de chambre sur les pages hôtels ; « Best rates direct » n'apparaît que dans la meta description d'Ericeira.
- About : « library of destinations that celebrate the curiosities of culture », valeurs BODY / CONSCIOUSNESS / EMOTIONS, étymologie grecque d'« Ethos », fondateurs nommés, 8 dirigeants avec photo. Journal : 20 articles récents (juillet 2026 → hiver 2025), catégories Hotels, Brand, Trends, Promotions, Design, Sustainability, Culture… Presse : Vogue, Lux.pt, Saber Viver (Ericeira), Condé Nast Traveler (Majorque), clé Michelin citée dans le journal.

**Interprétation**
- Marque ombrelle lifestyle qui vend une **appartenance** (club, « more-seekers ») et un **état** (wellness, retraites) avant des chambres. Gamme luxe boutique (« 5 star », « luxury » dans les titles) mais discours anti-codes (« rules are different », « Escape ordinary life »). Cible : 28-45 ans urbains, créatifs/entrepreneurs européens, sensibles au design, au sport doux et à la sociabilité.
- Territoire émotionnel : énergie, soleil, corps en mouvement, fête discrète ; valeurs : connexion, curiosité, bien-être, liberté ; personnalité assurée, directe, tutoyante.
- Différence avec un site hôtelier générique : le club tarifé au même niveau que les hôtels ; un manifeste ; un journal daté ; la même trame Wellness / Experiences / Retreats (blocs alternés → citation → highlights → destinations), qui fait de chaque thème un produit transversal.
- Cohérence élevée : photos de gens en action (vélo, surf, yacht, brunch, club), CTA « Explore », boutons filaires sans rayon et serif en capitales portent le côté manifeste.

**Enseignements réutilisables** : ranger une collection en trois entités (lieux / club / programmes) et donner à chaque programme sa page-gabarit ; teinter chaque lieu par un accent couleur unique sur un socle commun ; afficher les prix là où l'offre est un abonnement (club), les cacher là où la réservation passe par le moteur.

---

## 2. Première impression (5 premières secondes)

**Faits observés**
- `home-00-initial` : modal Usercentrics centré 625×305 px (logo æthos, « Privacy Settings », boutons **Deny** et **Accept All** de taille égale 280×42, fond sombre #2a2826) sur voile gris ; derrière, le hero sombre avec le H1 grisé. Pas de préloader visible (`.site-loader` `opacity: 0` ; Lottie chargé).
- `home-01-hero` : hero **en retrait** de 32 px sur les quatre côtés (1376×794 px, y=78→872) sur fond crème #f9f4ef, contenant l'iframe Vimeo (« Player error » en headless) ; H1 « THE RULES ARE DIFFERENT HERE » sur deux lignes, 72 px / 80 px d'interligne, Amerigo BT 500, capitales, blanc, centré, calé en bas du cadre (y≈660-800). Icône bouclier (préférences cookies) fixe en bas à gauche, 44 px.
- Header (visible sur `home-04-reduced-motion`) : 78 px, transparent sur crème ; à gauche burger 3 traits + « MENU » (12 px, capitales) ; logo « æthos » centré (bas-de-casse, ligature æ, ≈125×40 px) ; à droite « EN » puis **BOOK NOW** rempli #2a2826, texte blanc 10 px capitales, ≈104×38 px, rayon 0.
- Mobile `home-mobile-01-hero` : header 78 px (burger sans libellé, logo centré, bouton **BOOK** 58×27 px CSS rempli), hero 358×770 px inset 16 px, H1 40/48 px centré en bas.
- Aucun CTA dans le hero ; premier lien cliquable après le header : « OUR PHILOSOPHY » à y≈1 100 (desktop).

**Interprétation**
- On voit un cadre sombre vivant posé sur du papier, un slogan-manifeste, un seul bouton sombre. On comprend « marque » avant « hôtel » ; rien n'indique une destination, un prix ni une date. On ressent une posture plus qu'un lieu.
- Le modal cookies (voile + modal) est la distraction majeure, atténuée par l'égalité Deny/Accept. L'erreur Vimeo révèle un vrai risque : **aucune image de repli** derrière la vidéo (dégradé nu sur reduced-motion et mobile).
- Raison de continuer : le slogan pose une question que la section suivante (« places to stay, engage, and connect ») résout.

**Enseignements réutilisables** : hero en retrait (cadre) plutôt que plein écran pour signaler une marque éditoriale ; un seul bouton rempli dans tout le header ; prévoir un poster de repli derrière toute vidéo hébergée.

---

## 3. Direction artistique

**Faits observés**
- Variables CSS Webflow : `--color--page-bg: var(--color--cream--medium)` = **#f9f4ef** (1 613 occurrences home), `--cream--light #fcfaf7`, `--charcoal--dark #2a2826` (corps, boutons, section communauté, footer), `--charcoal--medium #5e5b58`, `--charcoal--light #7d7873`, `--leaf--dark #648b8b`. Mesurés en plus : gris #f4f4f4, #eaeae7 (blocs Company retreats, valeurs), #d9d9d6 (titres inactifs), accroches serif **#ac9e91** (beige-gris), accents destination **#72818b** / **#a3afb8**, club **#1e1d1b**, texte footer atténué #c6c6c3. Le brief annonçait #f7f3ee : la valeur réelle est #f9f4ef.
- Typographies chargées : **Amerigo BT** 400/500 (serif à empattements triangulaires, chargée en woff2 anonymes) et **Fakt** 400/600 (sans grotesque, `Fakt-Normal.woff`, `Fakt-SemiBold.woff`). Fallback `"Amerigo BT", Georgia, sans-serif` / `Fakt, sans-serif`. Polices commerciales (hypothèse : licences Bitstream/OurType).
- Échelle desktop (variables `--font-size--fs-120` 7.5rem → `fs-10`) : display 120,5 px / 126 (« WELLNESS FOR ALL SENSES »), 100 / 108 (« EXPERIENCES TO REMEMBER »), 122 px (« JOURNAL »), H1 72 / 80, sections 48 / 56, 40 / 48, 32 / 40, 24 / 32 ; H3 cartes Fakt 600 20 / 28 capitales #5e5b58 ; corps Fakt 16 / 24 ; descriptions 14 / 20 ; labels et boutons 10–12 px capitales interlettrées (`letter-spacing` 1.28 px mesuré sur « EXPLORE AND INDULGE » 16 px). Titres serif sans interlettrage, capitales ; H1 des pages-gabarits (Destinations, Wellness, Experience, Retreats, About) en **bas-de-casse 40 px, -0.8 px** : deux registres de titres.
- Mobile : H1 40 / 48, H2 28 / 36 et 24 / 32, display 57 px, H3 16 / 24, corps 14 / 20, cartes 12 / 16 sur 240 px, labels 10 px (36 occurrences), 8 px (2).
- Grille : marges 32 px (desktop) / 16 px (mobile) ; conteneurs de texte 320, 437, 512 (intro centrée), 555, 672, 704 et 800 px (club) ; largeur utile 1 376 px ; journal 1 291 px. Hypothèse : 12 colonnes Webflow (3 = 320, 4 = 437, 5 = 555, 6 = 672).
- Boutons : `button primary` = filaire 1 px #2a2826, fond transparent, **rayon 0**, ≈220×48 px, libellé 10–11 px capitales + flèche → à droite (`OUR PHILOSOPHY`, `EXPLORE ALL DESTINATIONS`, `EXPLORE WELLNESS`) ; `quaternary reservenow` = rempli ; `tertiary` (club) filaire blanc ; mobile 140–198×45 px, texte centré sans flèche. Aucun composant arrondi hors pastille cookies et carte-map ; formulaire newsletter en champs soulignés.
- Images : ratios mesurés 0.77 (555×721), 0.75 (469×622), 0.71 (322×451), 1:1 (512, 437, 370), 1.3–1.35 (672×498), 1.91–2.12 pleine largeur (1376×650-744). Masque **en arche** sur l'image d'intro (home et pages hôtels, classe `anim-arch-short`). Deux images de « texture » (marbre/lin) sous les photos décalées (sections Experiences et Wellness). Photos en `object-fit: cover`, AVIF (44/51 sur la home), pas d'image de fond CSS (`bgImages 0`).
- Vidéo : iframe Vimeo hero home (1412×794) et hero des pages hôtels (1376×774), `controls=0`, muet, boucle.
- Iconographie : flèche fine →, croix ×, « + » pour filtres/accordéons, pastille bouclier. Pas d'illustration ; carte Leaflet-like sur Contact (hypothèse : OpenStreetMap) avec pastilles rouge/vert.

**Tableau de tokens approximatifs**

| Token | Valeur |
|---|---|
| Fond page | #f9f4ef ; fond clair #fcfaf7 ; blocs gris #eaeae7 / #f4f4f4 |
| Texte | #2a2826 ; secondaire #5e5b58 ; tertiaire #7d7873 ; accroche serif #ac9e91 |
| Sombre | #2a2826 (communauté, footer) ; club #1e1d1b |
| Accents lieu | Ericeira/Majorque #72818b (hover #8a98a2), #a3afb8 |
| Titres | Amerigo BT 500 caps 120 / 100 / 72 / 48 / 40 / 32 / 24 ; bas-de-casse 40 px -0.8 px |
| Corps | Fakt 400 16/24 ; 14/20 ; labels 10–12 caps, +1.28 px |
| Boutons | 220×48 filaire 1 px, rayon 0, 10 px caps + flèche ; BOOK NOW rempli 104×38 |
| Marges / conteneurs | 32 px (16 mobile) ; 320 / 437 / 512 / 555 / 672 / 704 |
| Ratios images | 0.77 · 0.75 · 1:1 · 1.3 · 2:1 |
| Transitions | 0.35 s cubic-bezier(0.25,1,0.5,1) boutons ; 0.3–0.8 s cubic-bezier(0.77,0,0.175,1) reveals |

**Interprétation**
- Deux voix : capitales serif massives (jusqu'à 120 px) pour les titres de section, sans grotesque menue (10–14 px) pour le fonctionnel ; le beige-gris #ac9e91 des accroches ajoute un troisième niveau volontairement en retrait (2,4:1, rubrique 13).
- Composition asymétrique systématique (titre à gauche, image décalée à droite, paragraphe en bas à droite, image secondaire sur texture) ; le vide de 600–900 px est un choix, confirmé par le mobile où les blocs se réempilent sans trou.
- L'arche est le seul motif doux ; tout le reste est orthogonal, rayon 0, traits 1 px : registre magazine.

**Enseignements réutilisables** : deux tailles extrêmes de titres (120 px et 10 px) plutôt qu'une échelle régulière ; un fond papier unique + un seul bloc sombre par page ; accents par lieu sur le bouton de réservation et le footer ; textures neutres sous les photos décalées.

---

## 4. Architecture de la page d'accueil

Desktop : 8 sections + footer, 11 127 px (12,4 écrans). Mobile : 9 089 px.

| Position (px) | Section | Objectif | Contenu | Interaction | CTA | Émotion créée |
|---|---|---|---|---|---|---|
| 78–904 (826) | Hero cadré | Poser le manifeste | Vidéo Vimeo, H1 72 px | SplitText (hypothèse), clip-path 1 au palier 0 | aucun (BOOK NOW header) | Défi, énergie |
| 904–1 495 (913) | Intro « places to stay, engage, and connect » | Expliquer la promesse | H2 48 px bicolore (fin de phrase en #ac9e91), image arche 555×721, paragraphe 320 px | 3 opacités partielles + 2 clip-path au palier 731 (révélation en cours) | OUR PHILOSOPHY | Compréhension |
| 1 495–2 554 (1 059) | Destination highlights | Montrer la collection | Carrousel Splide 7 cartes 469×622 (nom Fakt 600 20 px + 2 lignes 14 px centrées), barre de progression fine | drag/flèches (Splide 4.1.4) | EXPLORE ALL DESTINATIONS | Choix, désir de lieu |
| 2 554–4 624 (2 069) | Experiences to remember | Vendre l'activité | Titre 100 px, accroche serif #ac9e91, 3 photos décalées (randonneurs 437×665, vélos 320×432, panoramique 1376×720) + texture | 2 parallaxes déclarées, reveals | EXPLORE EXPERIENCES | Envie de bouger |
| 4 624–6 176 (1 552) | Wellness for all senses | Vendre le soin | Titre 120 px, accroche serif, chambre en arche 555×721, piscine 1:1 sur texture, paragraphe 437 px | reveals | EXPLORE WELLNESS | Apaisement |
| 6 176–7 592 (1 417, fond #2a2826) | Our community | Vendre le club | Titre 72 px blanc, 2 colonnes de texte (« 50+ countries »), photo yacht 1376×744 | changement de fond | AETHOS MEMBERSHIP | Appartenance, désir social |
| 7 592–9 401 (1 809) | Retreats | Vendre le programme | Titre 72 px, photo « MAKE DIFFERENT RULES » 672×622, plage 1376×698, 2 paragraphes | reveals | EXPLORE RETREATS | Transformation |
| 9 401–10 135 (734) | Aethos Journal | Prouver la vie de la marque | Carrousel 8 articles datés (370×370, titre 14 px) | drag | EXPLORE JOURNAL | Actualité, confiance |
| 10 135–11 127 | Footer sombre | Convertir à la newsletter, naviguer | Formulaire 3 champs soulignés, logo 600 px, 4 colonnes de liens | hover opacité 0.6 | Subscribe | Clôture |

**Logique narrative** : début par une posture (pas un lieu) ; construction du désir en trois « verbes » (explore / wellness / community) ; l'offre devient concrète dès la 3ᵉ section (7 hôtels nommés avec pays), mais **aucune chambre n'est présentée sur la home** ; la preuve est éditoriale (journal daté, « 50+ countries ») et non sociale (aucun avis) ; la réservation reste confinée au bouton header ; la fin ouvre sur la newsletter. Le seul changement de fond (section club) marque le pivot commercial de la marque : l'abonnement.

---

## 5. Scroll et storytelling

**Faits observés**
- Libs prouvées : GSAP 3.12.5, ScrollTrigger (**25 triggers** actifs), ScrollSmoother, SplitText (**17 éléments** desktop, 5 mobile), Flip, Splide 4.1.4, Lottie, Webflow interactions (`wfAnim` 1 sur la home, 5–6 sur Wellness/Experience/Retreats). Attributs : `reveal` 61 (49 mobile), `parallax` 2, `sticky` 1 (5–6 sur About/Journal). Classes lues : `anim_fade-up_target/_self/_trigger`, `anim-stagger-in_sect/_item`, `anim-arch-short_trigger`, `anim-load-hero_parent`.
- Sweep desktop (15 paliers de 731 px) : transforms en cours 1–3 par palier, `partialOpacity` 3 au palier 731 (intro), 1 au footer ; `clipPath` 1–2 sur les 3 premiers paliers ; `pinned` = uniquement `div.smooth-wrapper` (aucune section épinglée). Fond central : crème sur 12 paliers, #2a2826 aux paliers 6 575–7 305 (club) et 10 227 (footer).
- Mobile (11 paliers de 825 px) : transforms 1–9, opacités partielles jusqu'à 9 (palier 7 421, section Retreats) : révélations plus nombreuses en cours au moment des captures. Header `fixed` à partir du palier 825 (desktop : `relative`, translaté par GSAP à chaque palier — hypothèse ScrollTrigger pin).
- Aucune section sticky, aucun scroll horizontal (`horizontal 0`, `scrollSnap 0`), aucun marquee. Les deux carrousels (destinations, journal) sont les seuls déplacements horizontaux.
- Rythme desktop : hero 0,9 écran → intro 1 écran → carrousel 1,2 → Experiences **2,3 écrans** (vides compris) → Wellness 1,7 → Communauté 1,6 → Retreats 2 → Journal 0,8.
- Pages hôtels : trois grands titres 72 px (ROOMS / EAT + DRINK / EXPERIENCES) alternés gauche/droite avec des images de tailles très différentes (672×498 ; 1205×… ; vignette 200×250), puis un bloc « HAPPENING » avec image typographiée (« BOTTOM LESS BRUNCH » en lettres découpées sur la photo), WELLNESS, OUR COMMUNITY (photo noir et blanc pleine largeur sur fond sombre), Journal, Presse.

**Interprétation, fonction de chaque effet**
- Cadre inset (32 px) du hero et du footer : rythme et marque — la page est un objet posé sur du papier.
- Fade-up + clip-path en arche : orienter le regard vers l'image d'intro (émotion).
- Titre 100–120 px → accroche serif atténuée → paragraphe sans : expliquer en trois temps.
- Vides de 600–900 px sous les titres : respiration et, hypothèse, zone de parallaxe (2 déclarées, non vérifiable).
- Passage crème → charbon une seule fois : pivot club, pas décoration.
- Carrousels : 7 hôtels et 8 articles tenus sur un écran chacun.
- Densité faible (644 mots pour 11 127 px, ≈ 58 mots/écran) ; l'envie de poursuivre tient à l'alternance stricte titre → image → texte → bouton, identique sur 6 sections.

**Enseignements réutilisables** : un seul pivot chromatique par page ; alternance de trois tailles d'images par section (grande, moyenne, vignette) ; carrousels pour les listes longues, empilement pour tout le reste ; aucune section épinglée : le mouvement est dans les entrées, pas dans le maintien.

---

## 6. Animations et micro-interactions

| Animation | Déclencheur | Élément | Effet (estimation) | Fonction | Risque UX |
|---|---|---|---|---|---|
| Préloader | chargement | `.site-loader` (Lottie + `img-clip left/right/top`) | hypothèse : logo Lottie puis ouverture en volets (3 clips) ; `opacity 0` à la capture | marque | délai perçu ; non observé |
| Entrée hero | chargement | `anim-load-hero_parent`, header | hypothèse : fondu/translation ; le header n'apparaît pas en headless | marque | header invisible si JS échoue |
| Titres découpés | entrée viewport | 17 éléments SplitText | hypothèse : mots/lignes en fade-up décalé ; durées CSS observées 0.6–0.8 s, easing cubic-bezier(0.77,0,0.175,1) | orienter, rythme | texte absent avant déclenchement (nécessite fallback) |
| Reveal fade-up | scroll | 61 éléments `reveal` / `anim_fade-up` | opacité 0→1 + translation (3 opacités partielles mesurées à y=731) ; 0.5–0.8 s | rythme | contenu invisible pour lecteurs rapides |
| Arche | scroll | `anim-arch-short_trigger` (image intro) | clip-path (6 règles CSS) : masque arche qui s'ouvre | émotion, marque | aucun majeur |
| Parallaxe | scroll | 2 éléments `parallax` | amplitude non mesurée (aucun transform capté hors reveals) | profondeur | non vérifiable |
| Hover bouton filaire | survol | `button primary` | fond transparent → #2a2826, texte → blanc, **0.35 s cubic-bezier(0.25,1,0.5,1)** | feedback | aucun |
| Hover BOOK NOW | survol | `quaternary reservenow` | #2a2826 → #5e5b58 ; Majorque #72818b → #8a98a2 ; même courbe | feedback | faible contraste de changement |
| Hover club | survol | `tertiary` / MEMBER LOGIN | filaire blanc → fond blanc texte sombre ; login blanc → #7d7873 (0.3 s) | feedback | aucun |
| Hover liens footer | survol | `footer_link` | opacité 1 → 0.6, 0.3 s cubic-bezier(0.77,0,0.175,1) | feedback | aucun |
| Hover cartes | survol | `c-carousel-card` | aucun changement mesuré (`{}`) | — | manque d'affordance |
| Carrousels | drag / flèches | Splide 4.1.4 | barre de progression 1 px sous les cartes | navigation | flèches non vues sur captures |
| Lignes de destinations (Retreats/Wellness) | survol | rangées 1376×187 avec `filter 0.2s cubic-bezier(0.25,0.46,0.45,0.94)` | hypothèse : image de rangée en filtre/apparition | orienter | — |
| Valeurs About | scroll (sticky 5) | BODY / CONSCIOUSNESS / EMOTIONS 56 px | titre actif #2a2826, inactifs #d9d9d6 ; changement par section | expliquer | contraste 1,17 des inactifs |
| Accordéon | clic | « MEMBERSHIP BENEFITS » (+) | ouverture ; durées 0.3–0.4 s (hypothèse) | expliquer | — |
| Menu | clic burger | overlay (46 liens, 5 langues) | non capturé | navigation | bouton `div` sans rôle ni nom |
| Pop-up promo | chargement (Ericeira, Retreats) | `.promopop-holder` | fond flouté (backdrop, 12 règles), carte 800×468 (image + texte + JOIN) | action | bloque la page entière, scroll figé |
| Reduced motion | `prefers-reduced-motion` | 5 règles CSS, toutes issues d'un module tiers (`LikeButton_module`) | **aucune désactivation** des animations GSAP/Webflow ; capture identique | — | non conforme WCAG 2.3.3 |

Durées CSS globales : 0.2 s ×35, 250 ms ×22, 0.3 s ×21, 0.4 s ×18, 1 s ×7 ; courbes : cubic-bezier(.77,0,.175,1) ×30 (in-out quart), (.165,.84,.44,1) ×5 (out quart), (.18,.89,.32,1.2) et (.34,1.2,.64,1) ×2 (léger rebond), 35 keyframes déclarés, `will-change` 1. Aucun curseur personnalisé (`cursor: auto`, 2 règles `cursor: none` non appliquées au body).

**Interprétation** : orchestration GSAP dense mais classique (fade-up, split, arche) ; la signature tient à l'arche et au cadre inset plus qu'à un effet spectaculaire. Les hovers sont uniformes (une courbe, 0.35 s) : cohérence. Faiblesses : aucune prise en charge de reduced-motion, header et titres dépendants du JS.

---

## 7. Navigation et architecture de l'information

**Faits observés**
- Header global 78 px : MENU (burger) · logo centré · EN · BOOK NOW. Pages hôtels : header **152 px** avec deuxième ligne « AETHOS ERICEIRA » + 11 onglets ancrés ; page club : **144 px** avec MEMBER LOGIN (rempli blanc) + MEMBERSHIP · LOCATIONS · ABOUT · CONTACT.
- Menu overlay (non capturé) : Destinations (8 entrées « Aethos X, Pays », Lisbon « coming soon », « Explore Destinations »), Different rules, membership, Wellness, Experiences, Retreats, Shop (externe), Gift cards, Journal, about us, Instagram/Facebook/LinkedIn, 5 langues. Footer : 4 colonnes (Socials, Destinations ×8, What we offer ×4, More info ×4) + Press · Contact · Jobs (externe aethosjobs.com).
- Liste des destinations : filtres Area (City / Country / Coast), Locations (Italy / Portugal / Spain / United Kingdom), Facility (3 cases) via Finsweet cmsfilter ; grille 2 colonnes de carrés 512 px, nom Fakt 600 24 px, pays 12 px, description 16 px #7d7873. Contact : liste des 8 lieux + carte interactive (+/−) + « hello@aethos.com », « 24 hours a day, 7 days a week », presse et jobs.
- Chemin vers une chambre : Home → Destinations (menu ou carrousel) → page hôtel → section ROOMS → « EXPLORE ROOMS » → page chambres (non auditée) : **3 clics minimum** avant la première chambre, 1 clic vers le moteur (BOOK NOW persistant).
- Bouton de réservation persistant : oui, header, desktop comme mobile (BOOK 58×27 px CSS sur mobile, à la limite des 44 px recommandés en hauteur). Sur le club, il est remplacé par MEMBER LOGIN et ENQUIRE (`/club/enquire`, 218×47 px, présent 2 fois + 3 boutons de formules).
- Frustrations mesurées : pop-up promo bloquant sur les pages Ericeira et Retreats ; burger sans rôle (`menu: no burger found`) ; 68 liens sans nom accessible sur la home (144 sur Ericeira) ; libellé mobile « BOOK » ambigu sur une home de collection (réserver quoi ?).

**Interprétation** : IA en trois axes claire, mais la home ne dit pas quel hôtel BOOK NOW va ouvrir (hypothèse : sélecteur dans l'overlay hotelchamp, non vérifié). La sous-navigation de 11 onglets est la vraie home de chaque lieu ; elle double le header (152 px, 17 % de l'écran).

**Enseignements réutilisables** : sous-navigation ancrée par lieu ; menu de collection listant chaque lieu avec son pays ; filtres par type de lieu (ville / campagne / côte) plutôt que par équipement.

---

## 8. Parcours de réservation et conversion

**Faits observés**
- **Moteur transactionnel** : hotelchamp IBE (`ibe.hotelchamp.io/pub/v0.0.657`, script 1 256 Ko chargé sur toutes les pages, y compris la home mobile), iframe `ws.hotelchamp.com/storage-relay`, Stripe v3 (240 Ko à 1 061 Ko selon la page) ; ouverture en overlay sur le même domaine (`?p=base&c=search&lg=en-US`), pas de nouvel onglet. Étape 1 non visible (pop-up promo). Aucun champ date/voyageurs sur les pages de marque (`dateInputs []` partout sauf Retreats).
- **Demande / devis** : page Retreats, formulaire « GET YOUR INDIVIDUAL PROPOSAL » : prénom, nom, email, mobile, radio « Corporate Retreats NO / YES », select destination, **date picker arrivée/départ** (calendrier septembre 2026), message. Club : `/club/enquire` (non audité) + `members@aethos.com`. Contact : email 24/7, pas de téléphone visible sur la page contact (`wordCount 124`).
- **Prix** : uniquement les formules club (650 / 1 800 / 2 500 €/an). Pages hôtels : aucun prix, aucune mention « à partir de », aucune disponibilité. Retraite promue : « five days », pas de prix dans le pop-up (bouton JOIN).
- **Réassurance / preuve** : logos presse (Vogue, Lux.pt, Saber Viver, Condé Nast Traveler), journal daté, « Best rates direct » en meta uniquement, aucun avis client, aucune note, aucune garantie affichée ; distinctions (clé Michelin) citées dans un titre d'article seulement.
- **Services additionnels** : Vouchers / Gift cards, Shop externe (aethosshop.com), Event spaces, Promotions (onglet hôtel), Happenings (Bottomless Brunch, bouton EXPLORE). Newsletter sur toutes les pages (3 champs, Cloudflare Turnstile).
- Distinction découvrir / demander / réserver : « EXPLORE … » (14 boutons) vs « ENQUIRE » (club) vs « BOOK NOW » (header) : vocabulaire cohérent. Sondes : 2 clics erronés sur « Facebook » (limite de l'heuristique, pas du site).

**Interprétation** : média de marque dont la conversion hôtelière est déléguée à l'overlay hotelchamp sans étape intermédiaire (ni dates ni sélection d'hôtel visibles). Rupture principale : le pop-up promo qui recouvre la page hôtel dès l'arrivée. L'absence de prix chambre contraste avec la transparence tarifaire du club.

**Enseignements réutilisables** : overlay same-domain plutôt que redirection ; devis avec date picker natif pour les programmes ; jamais de promo par-dessus le chemin de réservation.

---

## 9. Pages hôtels (objet vendu : une nuit dans un hôtel de la collection)

Page Aethos Ericeira (DOM) et Aethos Mallorca (captures), desktop uniquement.

**Faits observés**
- Nom et promesse : H1 « A LUXURY HOTEL ON PORTUGAL'S SURF COAST » (48 / 56 px, blanc sur vidéo Vimeo `1196285408` 1376×774 inset) ; Majorque « A DIFFERENT KIND OF SANCTUARY IN MALLORCA ». Meta : « 5 star boutique hotel… Best rates direct ».
- Ordre des informations (Ericeira, 11 027 px) : hero vidéo (738) → intro (1 823) : H2 48 px (« secluded property… gazing over the Atlantic from a cliff »), paragraphe 512 px centré, image arche 672×498 + 2 photos (555², 320²), 4 liens (BOOK NOW, EAT + DRINK, EXPERIENCES, RETREATS) et label « EXPLORE AND INDULGE » → bloc `sections-active` (7 618 px) : **ROOMS** 72 px (« designers have crafted spaces… », paragraphe 555 px, bouton EXPLORE ROOMS, 2 photos) → **EAT + DRINK** (paragraphe 437 px, vignette 200×250) → **EXPERIENCES** (accroche serif 32 px, photo surf, image 1:1) → **RETREATS AT ERICEIRA** / HAPPENING (Majorque : Bottomless Brunch, image typographiée) → **WELLNESS** (photos massage / pins) → **OUR COMMUNITY** (fond #2a2826, photo N&B 1376×652) → **AETHOS JOURNAL** (8 cartes) → **RECENT PRESS** (3 cartes : média en Fakt 600 18 px + titre 16 px) → footer #72818b.
- Galerie : onglet GALLERY dans la sous-nav (non audité) ; 58 images sur la page (53 alt vides), 45 AVIF, poids max 1 167 Ko (Junior Suite Ocean View) et 898 Ko (surf).
- Capacité, équipements, services, prix, disponibilité : **absents** de la page hôtel ; renvoyés à EXPLORE ROOMS et au moteur. Aucun hébergement complémentaire suggéré ; en revanche 7 autres hôtels dans le journal/menu.
- Éléments de projection : vidéo, verbes à la 2ᵉ personne (« waking up to a salt breeze on the balcony… counting waves as you fall asleep »), programmes (retraite d'automne, brunch dominical), presse locale en portugais/polonais/espagnol.
- Accent couleur : footer, BOOK NOW et bouton JOIN en #72818b ; fonds #a3afb8 (contraste blanc 2,24:1).
- Mobile : non capturé (limite).

**Interprétation** : page de destination éditoriale calquée sur la home ; la chambre est un chapitre parmi sept, sans donnée factuelle. Cela vend l'expérience et l'appartenance, mais un visiteur qui compare ne trouve ni surface, ni vue, ni prix, ni note sans quitter la page ; le pop-up promo aggrave la friction.

**Enseignements réutilisables** : gabarit home/hôtel identique avec sous-nav ancrée ; presse locale multilingue en preuve ; image typographiée pour les événements récurrents ; teinte par lieu. À ajouter dans un projet : un bloc « faits » (catégories, prix d'appel, capacité) sous ROOMS.

---

## 10. Copywriting

**Faits observés**
- Volumes : home 644 mots, Ericeira 665, Majorque 594, club 513, retreats 698, about 793, experience 473, wellness 391, journal 373, destinations 302, contact 124.
- Titres : capitales serif courtes, structure « [NOM] TO/FOR [ÉTAT] » (« Experiences to remember », « Wellness for all senses ») ; slogans en opposition (« The rules are different here », « Escape ordinary life », « A different kind of sanctuary ») ; triades (« Stay, engage, and connect », « More connection. More experiences. Infinite possibilities. », « Work, move, recharge ») ; H1 des pages-gabarits en phrase complète avec point (« Restore your physical, mental, and spiritual well-being. »).
- Vocabulaire : community, connect, conscious explorers, more-seekers, curated, sanctuary, ritual, reconnect, wholeness ; néologisme de cible (« more-seekers ») ; « luxury » présent dans les titles et cartes (« luxury boutique hotel »), rare dans les corps de texte.
- Sensoriel : « salt breeze on the balcony », « counting waves as you fall asleep », « Soak in the steam and let the warm water envelop you » ; brunch : « Sundays. We've got them sorted. » (registre parlé).
- CTA : 100 % « EXPLORE + objet » (destinations, experiences, wellness, retreats, journal, rooms, membership locations), sauf ENQUIRE, JOIN, BOOK NOW, LOAD MORE, CLEAR ALL. Labels de sur-titre en petites capitales (RELAXATION, MOVEMENT, OCEAN, SNOW, HAPPENING).
- Caractéristiques techniques : aucune sur les pages de marque ; les seuls chiffres sont « 50+ countries », « 5 star », « 6 visits per year », prix club, « 2000m » (journal), « 4k Glacier Hiking ».
- Citations : Jim Rohn (wellness), citations maison en capitales 32–40 px centrées sur About/Experience/Retreats.
- Multilingue : Weglot (5 langues), texte source anglais.

**Interprétation** : ton direct, deuxième personne, phrases courtes, promesse d'état plutôt que de service ; le luxe est nommé pour le SEO et remplacé par « different / more / conscious » dans le discours ; la transformation prestation → expérience passe par des verbes d'action et des rituels (brunch du dimanche, run club), jamais par des listes d'équipements.

**Enseignements réutilisables** : un verbe unique pour les CTA de découverte ; sur-titre catégoriel + titre serif + phrase sensorielle + bouton ; un néologisme de cible ; chiffres réservés à l'abonnement et à la communauté.

---

## 11. Photographie et vidéo

**Faits observés**
- Types de plans (captures home, hôtels, club, journal) : drone d'architecture (Monterosa bois/piscine, DJI_0694-3.jpg 2 993 Ko), paysages avec deux personnes de dos (randonnée, vélo), scènes de vie en groupe (brunch vu du ciel, terrasse, dîner de club, soirée), portraits d'action (femme sous les éclaboussures avec t-shirt « MAKE DIFFERENT RULES »), détails (brochettes de gambas, panier de cueillette, peignoir en arche), intérieurs lumineux (chambre arche, salle de bain sur mer, salon yacht), noir et blanc pour la communauté et le journal (marche en montagne, danse).
- Lumière : fin de journée dorée dominante (yacht, piscine à débordement, plage), quelques scènes nocturnes de club ; couleurs chaudes, grain léger (rendu argentique sur yacht et piscine) ; palette accordée au crème du site.
- Présence humaine : forte (≈ 2/3 des visuels de la home montrent des personnes), souvent de dos ou en mouvement, jeunes, en groupe ; club : visages de face, soirée.
- Proportion lieu / expérience sur la home : 4 photos d'architecture/intérieur vs 9 d'activité ou de vie. Pages hôtels : équilibre (chambres, cuisine, activités, soins).
- Vidéos : 1 par hero (home et hôtels), Vimeo background, sans contrôle ; poids réseau home ≈ 13,2 Mo de segments (xhr), Ericeira ≈ 17,7 Mo ; aucune vidéo dans le corps de page ; **aucune vidéo chargée sur mobile** (`videosNet []`, 0 iframe Vimeo active), le hero mobile reste un dégradé sombre (hypothèse : vidéo désactivée sous 768 px sans poster).
- Images : 51 sur la home (42 lazy, 39 avec srcset, 44 AVIF), alt vides sur 49 ; 58 sur Ericeira (58 lazy) ; quelques JPEG lourds non convertis (2 993 Ko, 1 167 Ko, 898 Ko, 873 Ko).

**Interprétation** : la photographie vend le corps en mouvement et la sociabilité ; l'architecture est montrée par le drone (échelle) et par des cadrages serrés d'intérieur (matières). Le noir et blanc isole la « communauté » comme un registre à part. Cohérence chromatique forte avec la DA.

**Shot list pour reproduire ce niveau**
1. Vidéo hero 15–30 s, 1920×1080, muette, fin de journée, lieu + personnes en action ; poster de repli.
2. Drone d'architecture en contexte, 1 par lieu, ratio 2:1.
3. Deux personnes de dos dans le paysage (randonnée, vélo), 3:4.
4. Scène de groupe vue du ciel (brunch, terrasse).
5. Portrait d'action à contre-jour (eau, t-shirt manifeste).
6. Intérieur cadré dans une arche (chambre, peignoir), lumière naturelle ; baignoire avec vue 1:1.
7. Détail culinaire 1:1, produits crus.
8. Photo « typographiée » d'événement récurrent.
9. Série noir et blanc de la communauté ; soirée club en lumière chaude, visages de face.
10. Vignettes 3:4 isolées (yoga sous voûte, surfeur sur plage vide) et textures neutres (lin, marbre) pour les compositions décalées ; portraits d'équipe 1:1.

---

## 12. Mobile (390×844, home uniquement)

**Faits observés**
- Header 78 px : burger sans libellé (contrairement au desktop « MENU »), logo centré ≈ 92×27 px, bouton **BOOK** rempli **58×27 px CSS** (texte 10 px). Header `fixed` dès 825 px de scroll (mesuré), `transparent` sans backdrop.
- Hero 358×770 px inset 16 px, dégradé sombre sans vidéo (0 requête Vimeo), H1 40 / 48 px centré en bas ; 2 modals cookies empilés (Accept All puis Deny, pleine largeur 366×70 px chacun).
- Titres : H2 intro 28 / 36 ; « DESTINATION HIGHLIGHTS » 24 / 32 ; display 57 px (« EXPERIENCES TO REMEMBER », « WELLNESS FOR ALL SENSES » sur deux lignes) ; « OUR COMMUNITY » 40 px ; H3 cartes 16 / 24 ; corps 14 / 20 centré ; descriptions 12 / 16 sur 240 px ; 36 occurrences de 10 px et 2 de 8 px.
- Boutons : filaires centrés sans flèche, OUR PHILOSOPHY 140×45 px, EXPLORE ALL DESTINATIONS 198×45, EXPLORE WELLNESS 154×45, AETHOS MEMBERSHIP 164×45 (blanc sur sombre).
- Rythme : 9 089 px (10,8 écrans) ; sections 770 / 1 017 / 695 / 1 644 / 1 568 / 667 / 1 136 / 552 + footer ; les compositions décalées deviennent des piles pleine largeur (358 px), images 0.77–1.56 ; carrousel destinations en cartes 272 px avec débord droit (affordance de défilement).
- Animations conservées : 49 `reveal`, 2 parallaxes, 5 SplitText (vs 17), transitions 0.3 s ×49, 0.4 s ×34 ; opacités partielles jusqu'à 9 par palier : les révélations sont plus visibles qu'en desktop au moment des captures (contenu encore à 0 d'opacité).
- Moteur : script hotelchamp 1 256 Ko et Stripe chargés sur la home mobile ; BOOK ouvre l'overlay (hypothèse, non testé).
- Vitesse : TTFB 335 ms, FCP 1 136 ms, DCL 1 551 ms, load 2 607 ms ; 197 requêtes, **10,98 Mo** dont images 5,4 Mo (DJI_0694-3.jpg 2 993 Ko chargé aussi sur mobile), scripts 4 Mo (69).
- Footer : formulaire 2 lignes, logo 716 px de large, 4 colonnes en 2×2, Press · Contact · Jobs.

**Interprétation** : adaptation propre et lisible (piles, carrousel débordant, corps 14 px, titres 24–57 px). Points faibles : BOOK de 27 px de haut, libellés 8–10 px, hero de 770 px sans vidéo ni poster, JPEG drone non redimensionné, animations non réduites.

**Différences pertinentes avec le desktop** : pas de vidéo ; boutons sans flèche ; header `fixed` (vs translaté GSAP) ; burger sans libellé ; interlignes serrés (12 / 14 px sur les titres d'articles).

---

## 13. Performance, accessibilité, SEO

**Faits observés**
- Temps (desktop) : home TTFB 462 ms, FCP 1 708 ms, DCL 2 612 ms, load 6 733 ms, 399 requêtes, **38,8 Mo** (xhr Vimeo 13,2 Mo, images 13,9 Mo/112, scripts 8,2 Mo/134, documents 2,2 Mo/18) ; Ericeira 457 requêtes, 42,5 Mo, load **14,9 s**, FCP 2 764 ms ; club FCP 3 232 ms, DCL 6 009 ms, load 10,9 s, 13 Mo ; destinations 294 req / 17,3 Mo / load 6,1 s ; about 306 req / 20,4 Mo ; wellness TTFB 925 ms. Mobile home : 197 req, 11 Mo, load 2,6 s. LCP non mesuré.
- Tiers : cdn.prod.website-files.com (80 req), jsdelivr (32, Finsweet ×8 + Splide + GSAP plugins), Cloudflare Turnstile (32, 3 iframes de 241–252 Ko), TikTok pixel (22), hotelchamp (19), Usercentrics (18 + 15), GTM (18), Google (18), doubleclick, Facebook pixel (450 Ko), Hotjar (`_hjSafeContext` sur Majorque), Stripe. Polices 8 requêtes / 375 Ko (4 fichiers ×2). CSS 718 Ko (Webflow shared 365 Ko).
- Images : lazy 42/51 (home), 58/58 (Ericeira) ; AVIF majoritaire ; 3 JPEG > 800 Ko ; alt vides 49/51 (home), 53/58 (Ericeira), 39/40 (club) ; `missingAlt 0` (attribut présent mais vide).
- Stabilité : `will-change` 1, hero inset à dimensions fixes ; révélations JS → contenu à opacité 0 avant déclenchement (risque de page vide si JS lent, observé sur le header).
- Contrastes calculés : #2a2826/#f9f4ef **13,4:1** ; #5e5b58/#f9f4ef 6,2 ; #7d7873/#f9f4ef **4,0** (limite AA pour le 16 px des cartes destinations) ; #ac9e91/#f9f4ef **2,4** (accroches serif 32–40 px : sous AA large 3:1) ; blanc/#2a2826 14,7 ; blanc/#72818b 4,0 (footer hôtels) ; blanc/#a3afb8 **2,2** (bouton hover Majorque) ; #d9d9d6/#eaeae7 **1,2** (valeurs inactives About) ; #c6c6c3/#2a2826 8,6.
- Clavier / ARIA : `skipLink false` ; `focusOutlineNone` 124 (home) à 200 (Ericeira, journal) ; `tabindex -1` 26–34 ; `linksNoName` 68 (home), 144 (Ericeira), 140 (Majorque), 64 (journal) ; `buttonsNoName 0` ; burger sans rôle ; `iframesNoTitle` 2–5 ; landmarks : main 1, header 1, nav 5–7, **footer 0** ; `aria-hidden` 16. Formulaires : aucun `<label>` (placeholders seuls) sauf radios Retreats.
- Reduced motion : 5 règles, toutes d'un module tiers ; 112–192 éléments avec transitions ; capture `04-reduced-motion` identique (hero sombre, header visible).
- Structure : 1 H1 par page ; hiérarchie H1 → H2 sections → H3 cartes respectée ; anomalies : journal H1 « JOURNAL » 122 px puis 20 H3 sans H2 ; Ericeira/Majorque : titres d'articles de presse en H2 16 px sous des H3 18 px (inversion) ; club : H2 « OUR MEMBERSHIPS ‍ ALL MEMBERSHIPS ARE ANNUAL » contient un caractère invisible.
- Métadonnées : title et description présents sauf **journal (pas de description)** ; og:title/description/image présents ; canonical sur chaque page ; `hreflang []` malgré 5 langues Weglot ; `jsonld []` (aucune donnée structurée Hotel/Organization) ; `lang="en"` ; robots non vu.
- Contenu indexable : 302–793 mots par page ; textes dans le DOM (SplitText côté client).

**Interprétation** : immersion payée cher sur desktop (39–43 Mo, 400–460 requêtes, load 7–15 s) : vidéo Vimeo adaptative, JPEG drone de 3 Mo répété sur 5 pages, 8 scripts Finsweet, pile marketing (TikTok, Meta, GTM, Hotjar, Turnstile). Mobile mieux tenu (11 Mo) mais avec le même JPEG. Accessibilité faible sur tous les axes mesurés ; SEO de base correct (title, canonical, og, 1 H1) mais sans hreflang ni JSON-LD, surprenant pour une collection en 5 langues.

**Enseignements réutilisables** : poster et variante mobile pour toute vidéo ; drones en AVIF ≤ 400 Ko ; révélations JS ≤ 0.8 s avec `prefers-reduced-motion` ; aria-label sur les liens image ; hreflang + JSON-LD Organization/Hotel.

---

## 14. Conclusion

### 15 meilleurs éléments
1. Slogan-manifeste en H1 (« The rules are different here ») répété sur un t-shirt en photo : cohérence mots/images.
2. Hero et footer en **cadre inset 32 px** sur fond papier #f9f4ef : signature immédiate.
3. Deux extrêmes typographiques (Amerigo BT 120 px / Fakt 10 px) sans échelle intermédiaire surchargée.
4. Accroches serif en #ac9e91 comme troisième niveau de lecture.
5. Masque en arche sur l'image d'intro (home et hôtels).
6. Un seul bloc sombre par page, réservé au club : le pivot commercial est chromatique.
7. Architecture lieux / club / programmes avec le **même gabarit** (bloc alterné → citation → highlights → destinations → triple image).
8. Sous-navigation d'hôtel à 11 ancres et header 152 px : chaque lieu devient un mini-site.
9. Accent couleur par destination sur le bouton de réservation et le footer (#72818b).
10. Prix du club affichés (650 / 1 800 / 2 500 €) avec accordéon de bénéfices.
11. Journal daté (20 articles) + presse locale multilingue : preuve éditoriale.
12. Boutons filaires rayon 0 + flèche, hover uniforme 0.35 s cubic-bezier(0.25,1,0.5,1).
13. Photographie de corps en mouvement, lumière dorée, grain argentique ; N&B réservé à la communauté.
14. Formulaire de devis retraites avec date picker, radio corporate et sélecteur de destination.
15. Carte interactive des 8 lieux sur la page Contact et liste avec pays.

### 5 faiblesses / limites
1. Pop-up promo bloquant (scroll figé) sur les pages hôtel et retraites.
2. Aucune information factuelle ni prix sur les pages hôtels ; « BOOK » ambigu sur la home de collection.
3. Poids : 39–43 Mo desktop, 400–460 requêtes, load jusqu'à 15 s ; JPEG drone 3 Mo sur 5 pages ; 8 scripts Finsweet ; pixels TikTok/Meta.
4. Accessibilité : focus supprimé (124–200), 68–144 liens sans nom, alt vides, pas de skip link, burger sans rôle, aucun reduced-motion.
5. Dépendance au JS pour le header et les titres (header absent en headless) et hero vidéo sans poster (écran vide sur mobile).

### 10 principes réutilisables
1. Cadrer le hero plutôt que le mettre plein écran quand la marque prime sur le lieu.
2. Un fond papier, un bloc sombre, un accent par lieu.
3. Titre géant → accroche atténuée → paragraphe court → bouton filaire : une seule grammaire de section.
4. « EXPLORE + objet » pour découvrir, un verbe distinct pour réserver/demander.
5. Gabarit unique pour les programmes transversaux (wellness, expériences, retraites).
6. Sous-nav ancrée par lieu, avec BOOK NOW dans la couleur du lieu.
7. Afficher les prix des offres d'abonnement, laisser le moteur gérer les chambres — mais donner au moins un prix d'appel.
8. Journal daté + presse locale comme preuve, à défaut d'avis.
9. Overlay de réservation same-domain, jamais de promo par-dessus.
10. Carrousels pour les listes (hôtels, articles), piles pour le récit ; aucune section épinglée.

### Éléments propres à la marque à ne pas copier
Le logotype « æthos » et sa ligature ; le slogan « The rules are different here » et l'entrée de menu « Different rules » ; le néologisme « more-seekers » ; la trilogie BODY / CONSCIOUSNESS / EMOTIONS ; l'association Amerigo BT + Fakt ; les photos « MAKE DIFFERENT RULES » ; la structure tarifaire Connect / One / Unlimited.

### Notes /10
- **Branding : 9** — manifeste porté par le H1, le menu (« Different rules »), le t-shirt photographié et le journal ; architecture lieux / club / programmes explicite (46 liens, 8 lieux avec pays, 3 formules tarifées). Retenue : « luxury » réservé au SEO mais « 5 star » dans les titles crée une légère dissonance.
- **Direction artistique : 8** — tokens cohérents (#f9f4ef / #2a2826 / #ac9e91, Amerigo 120→24 px, Fakt 10–16 px), cadre inset, arche, accents par lieu ; retenue pour les contrastes 2,4:1 (accroches) et 2,2:1 (hover Majorque) et pour l'inversion H2/H3 de la presse.
- **Animations : 7** — GSAP 3.12.5 + ScrollTrigger (25) + SplitText (17) + arche clip-path, hovers uniformes 0.35 s ; mais aucun reduced-motion réel (5 règles tierces), header et titres dépendants du JS, parallaxe et smooth scroll non vérifiables.
- **UX : 6** — IA claire et sous-nav d'hôtel efficace ; pénalisé par le pop-up bloquant, 3 clics avant une chambre, burger sans rôle, 68–144 liens sans nom, focus supprimé.
- **Conversion : 5** — BOOK NOW persistant et overlay same-domain, devis retraites avec date picker, prix club publics ; mais aucun prix ni fait sur les pages hôtels, pas d'avis, pas de dates/voyageurs avant l'overlay, « BOOK » sans hôtel sur la home, promo par-dessus le parcours.
- **Mobile : 7** — adaptation propre (piles, carrousel débordant, 14 px corps, FCP 1,1 s, 11 Mo) ; pénalisé par le hero vide (pas de vidéo ni poster), BOOK 58×27 px, labels 8–10 px, JPEG 3 Mo.

**Note globale : 7 / 10.** Référence forte pour l'expression de marque d'une collection (gabarits, accents par lieu, club tarifé, journal) ; en retrait sur la conversion hôtelière, la performance desktop et l'accessibilité.

### Ce que ce site apporte que les sites « quiet luxury » (FORESTIS, Seagate, Le Collectionist) n'apportent pas
- Une **communauté tarifée** au cœur de la home (section sombre, « 50+ countries », 3 formules 650–2 500 €/an, portail membres, login) : la conversion n'est plus seulement la nuit mais l'abonnement.
- Un **rythme typographique violent** (120 px capitales serif sur fond papier) et des slogans en opposition, là où le quiet luxury murmure en bas-de-casse.
- Des **gabarits de programmes transversaux** (Wellness / Experiences / Retreats) partagés par 8 lieux, avec liste de destinations filtrable par type (ville / campagne / côte) et carte.
- Une **couleur d'accent par lieu** sur un socle de marque commun.
- Un **journal daté** et une presse locale multilingue comme preuve vivante, plus des événements récurrents (brunch, run club) photographiés en typographie.
- Des photos de **groupes, de fête et de corps en mouvement**, en couleur chaude et grain argentique, et le noir et blanc comme registre de communauté.

---

## Observations clés à conserver pour la phase comparative

- Fond #f9f4ef (pas #f7f3ee) + charbon #2a2826 ; accroches #ac9e91 (2,4:1) ; accents lieu #72818b / #a3afb8 ; club #1e1d1b ; polices Amerigo BT 400/500 + Fakt 400/600, 375 Ko / 8 requêtes.
- Échelle : display 120,5 / 100 / 72 / 48 / 40 / 32 / 24 px (caps serif, interlettrage 0) ; H1 gabarits 40 px bas-de-casse -0.8 px ; corps 16/24 ; labels 10–12 px caps +1.28 px ; mobile H1 40, display 57, corps 14/20, 36 occurrences de 10 px.
- Hero cadré 1376×794 inset 32 px (mobile 358×770 inset 16) ; vidéo Vimeo background (13,2 Mo de segments desktop, 0 sur mobile, « Player error » headless, pas de poster).
- Header 78 px (MENU / logo / EN / BOOK NOW 104×38) ; hôtels 152 px avec 11 ancres ; club 144 px ; mobile BOOK 58×27 px ; header desktop translaté par GSAP, mobile `fixed` dès 825 px.
- Home 11 127 px / 8 sections / 644 mots ; mobile 9 089 px ; un seul bloc sombre (club, 1 417 px) ; 2 carrousels Splide ; aucune section sticky ni scroll horizontal.
- GSAP 3.12.5 + ScrollTrigger 25 + ScrollSmoother + SplitText 17 (5 mobile) + Flip + Lottie ; 61 reveal (49 mobile), 2 parallaxes, clip-path arche ; hover 0.35 s cubic-bezier(0.25,1,0.5,1) ; reveals cubic-bezier(0.77,0,0.175,1) 0.3–0.8 s ; reduced-motion : 0 règle propre.
- Boutons filaires 220×48, rayon 0, 10 px caps + flèche → fond #2a2826 au survol ; mobile 140–198×45 sans flèche.
- Club : Connect 650 €/an (6 visites/club), One 175 €/mois · 1 800 €/an, Unlimited 240 €/mois · 2 500 €/an ; ENQUIRE 218×47 ; MEMBER LOGIN → portal.aethos.com.
- Pages hôtels : intro arche 672×498 + ROOMS / EAT + DRINK / EXPERIENCES 72 px / HAPPENING / WELLNESS / COMMUNITY / JOURNAL / PRESS ; 0 prix, 0 capacité ; pop-up promo `promopop-holder` z-1000 bloquant le scroll.
- Moteur hotelchamp IBE v0.0.657 (1 256 Ko sur toutes les pages, Stripe v3), overlay same-domain `?p=base&c=search` ; devis retraites avec date picker natif ; contact 24/7 par email, pas de téléphone.
- Perf desktop : home 399 req / 38,8 Mo / FCP 1,7 s / load 6,7 s ; Ericeira 457 req / 42,5 Mo / load 14,9 s ; club FCP 3,2 s ; JPEG DJI_0694-3 2 993 Ko sur 5 pages ; mobile 197 req / 11 Mo / FCP 1,1 s.
- A11y : skip link 0, focus none 124–200, liens sans nom 68–144, alt vides 49/51, footer landmark 0, burger sans rôle, formulaires sans labels.
- SEO : 1 H1/page, canonical ok, og ok, 0 hreflang (5 langues Weglot), 0 JSON-LD, journal sans description, inversion H2/H3 presse.
- Preuves : presse Vogue / Lux.pt / Saber Viver / Condé Nast Traveler ; journal 20 articles (9 juillet 2026 → hiver 2025) ; « 50+ countries » ; 0 avis client.
- Filtres destinations : Area (City/Country/Coast), Locations (IT/PT/ES/UK), Facility ; grille 2×512 px ; 8 lieux dont Lisbonne « coming soon » ; carte interactive sur Contact.
