# Mobile, accessibilité, performance et SEO — sites d'hébergement premium

> Ces quatre sujets décident si l'impression haut de gamme survit au téléphone, à une connexion moyenne, à un lecteur d'écran et à Google. Chaque règle porte un niveau (Indispensable / Recommandé / Signature premium), un contexte et un risque.

## 0. Faits observés dans le benchmark (2026-09-04, Chromium headless, sans Lighthouse)

| Site | TTFB / FCP / load (desktop) | Requêtes / poids | Vidéos | Lazy / alt | Reduced motion | H1 | Méta |
|---|---|---|---|---|---|---|---|
| FORESTIS | 545 ms / 1,2 s / 2,7 s (home) ; Villa : load 12,8 s | 171 req., ≈ 8,4 Mo dont 6,4 Mo de scripts (tiers : tag manager, Bing, Facebook, Cookiebot, relay, getsitecontrol, dash.js 227 Ko, video.js 472 Ko, Maps sur toutes les pages) | aucune balise vidéo sur 12 pages | 9/25 images lazy ; 0 srcset ; 5 sans alt ; alt « opens in a new window » ×7 ; 86–116 éléments sans focus ; 0 landmark ; zoom bloqué | 0 règle CSS ; 5 éléments animés | 2 H1 sur la home (4 en mobile), 0 sur Dining | title + description + og + canonical + hreflang en/de/it/x-default ; 0 JSON-LD |
| Hotel Corazón | 808 ms / 1,0 s / 2,5 s ; page chambre 858 Ko (350 Ko mobile) | 115 req., ≈ 42 Mo dont ≈ 39,8 Mo de flux vidéo Vimeo (chunks jusqu'à 4,7 Mo) ; front très léger (main.css 33,9 Ko) | iframe Vimeo autoplay loop muted (« Player error » en headless) | 0 lazy sur la home ; 0 srcset ; 12 alt vides sur 14 ; contraste corps brun/rouge ≈ 3,2:1 (échec AA) ; 32–45 éléments sans focus | 6 règles (réinitialisation globale) | 0 H1 sur home/rooms/about | title, description, og ; pas de canonical, hreflang ni JSON-LD ; anglais seul |
| Borgo Egnazia | 154 ms / 0,8 s / 3,8 s (home) ; rooms 13,2 s ; La Corte mobile 13,9 s | 179 req., ≈ 28 Mo dont ≈ 18,5 Mo de vidéo mp4 ; offers 30,1 Mo (JPEG de 6,3 et 5,5 Mo) ; 73 scripts, 28 CSS | mp4 plein écran fixe, autoplay muted, sans loop ni poster ni playsinline ; 5 vidéos de tuiles non muettes | 0 lazy ; 0 srcset ; 9–12 images sans alt par page ; 13 textes < 12 px ; paragraphes à 2,47–3,43:1 ; formulaire de 7 champs sans label ; zoom bloqué | 23 règles (Bootstrap, inopérantes) | 0 H1 sur 5 pages/10 | title identique partout ; description vide ; og en italien ; JSON-LD WebSite seul ; skip link présent |
| The Seagate | 270–652 ms / 1,0–1,3 s / 1,1–1,6 s | 228–278 req. ; home 164,6 Mo transférés (media 138 Mo desktop / 70,7 Mo mobile) ; 73 scripts (Bing, Google Ads, Floodlight, Pinterest, Meta) | 4 mp4 autoplay sans poster (hero desktop 13,9 Mo + mobile 10 Mo chargées sur les deux breakpoints ; vignettes de 14 et 32,9 Mo rendues en 303×150) | 0 lazy ; 3 srcset / 30 ; jpg jusqu'à 3,27 Mo ; 0 `main` ; 54–81 éléments sans focus ; 3 iframes sans titre | 1 règle (formulaire) | 5 H1 sur la home | title 55 c., description 165 c., JSON-LD Hotel + géo ; og:image absent ; canonical sans www ; 0 hreflang |
| Le Collectionist | 377 ms / 0,7 s / 1,4 s | 527 req. ; ≈ 21 Mo dont 9,8 Mo de scripts (348 fichiers Nuxt) ; images 1,5 Mo | vidéo hero ≈ 4,3 Mo, autoplay muted loop playsinline, sans poster | 60/66 images lazy ; 53 srcset ; 0 alt manquant ; 178 éléments sans focus ; 5 boutons sans nom | 3 règles (transitions de vue) | voir fiche | title + description ; pages destination et thématiques riches en texte (SEO) |

Interprétation : même les meilleurs sites du secteur portent 8 à 40 Mo par page d'accueil à cause des vidéos et des scripts tiers ; le hero vidéo est la première cause de lenteur perçue. Les alt et la structure H1 sont négligés. La marge de progression « invisible » (perf, a11y, SEO) est un avantage compétitif réel.

## 1. Responsive et mobile

### 1.1 Breakpoints et grille (Indispensable)
- Tester : 360, 390, 414, 768, 1024, 1280, 1440, 1920 px. Concevoir mobile d'abord pour les pages hébergement et le moteur.
- Marges : 20–24 px mobile, 40–64 px tablette, 64–120 px desktop. Largeur max de contenu texte : 640–720 px ; largeur max de page : 1 280–1 440 px (FORESTIS : contenu centré ≈ 864 px sur 1 440 ; Corazón : 1 080–1 200 px).

### 1.2 Hero mobile (Indispensable)
- Hauteur 70–90 svh (jamais 100 vh fixe à cause des barres de navigateur) ; titre 32–40 px ; sous-titre 16–18 px ; CTA visible sans scroll.
- Vidéo : version verticale dédiée (9:16 ou 4:5) ≤ 3 Mo, ou image ; poster obligatoire ; ne pas autoplay sous `Save-Data`.
- Menu : burger à gauche ou à droite selon la position du logo ; CTA Réserver visible dans le header (Seagate : bouton pleine largeur sous le logo) ou en barre basse fixe.

### 1.3 Barre d'action basse (Recommandé, Indispensable sur pages hébergement)
- 56–64 px de haut, fond opaque ou flouté, prix « à partir de » + bouton principal ; apparaît après le hero, disparaît quand le moteur est visible.
- Variante contact (FORESTIS : barre basse fixe avec 3 icônes téléphone / e-mail / localisation) pour les modèles conversationnels.

### 1.4 Typographie et cibles (Indispensable)
- Corps ≥ 16 px (17–18 px pour les descriptions longues) ; interligne 1,5–1,65 ; titres 28–40 px ; jamais de texte tout en capitales au-dessous de 13 px avec interlettrage (illisible) ; largeur de ligne 45–75 caractères.
- Cibles tactiles ≥ 44×44 px ; espacement ≥ 8 px entre cibles.

### 1.5 Composants mobiles (Recommandé)
- Galerie : défilement horizontal avec compteur « 3/12 », swipe natif, plein écran au tap.
- Équipements : accordéons ; description : 3 lignes puis « lire la suite ».
- Moteur : champs empilés, calendrier plein écran, sélecteur de voyageurs avec +/−, bouton pleine largeur.
- Cartes hébergements : 1 colonne, image 4:5 ou 3:2, nom + capacité + prix + CTA.
- Tableaux : transformés en listes ou en cartes ; jamais de scroll horizontal sur un tableau de tarifs.

### 1.6 Ce qu'il faut supprimer sur mobile
- Parallaxe, sticky narratif, curseur personnalisé, hover-only, préloader, vidéos secondaires en autoplay, marquee.

## 2. Accessibilité (WCAG 2.2 AA comme plancher)

| Règle | Niveau | Détail | Risque évité |
|---|---|---|---|
| Contrastes | Indispensable | texte ≥ 4,5:1, grands titres et composants ≥ 3:1. Attention aux textes blancs sur photos (ajouter un dégradé 0 → 40 % noir ou un scrim) et aux gris clairs sur crème (FORESTIS : #333 sur #f2f1eb ≈ 11:1, bon ; textes gris 9 px chez Borgo : à proscrire) | illisibilité au soleil, refus légal |
| Clavier | Indispensable | tout est atteignable au Tab ; focus visible (jamais `outline: none` sans remplacement — 43 à 45 éléments sans outline observés sur deux sites) ; ordre logique ; menu et modales pièges de focus avec Escape | exclusion, échec d'audit |
| Skip link | Recommandé | « Aller au contenu » visible au focus (Borgo en a un) | — |
| Alt | Indispensable | descriptifs pour les photos informatives (« Chambre Tower Suite, lit face aux Dolomites au lever du soleil »), vides (`alt=""`) pour les décoratives ; jamais « opens in a new window » ou nom de fichier | lecteurs d'écran, SEO image |
| Vidéos | Indispensable | muettes et décoratives : `aria-hidden` + bouton pause ; informatives : sous-titres et transcription | WCAG 1.2, 2.2.2 |
| Formulaires | Indispensable | label visible (pas seulement placeholder), erreurs textuelles liées au champ (`aria-describedby`), autocomplete, validation non bloquante, confirmation | abandon, exclusion |
| Landmarks et titres | Indispensable | header/nav/main/footer ; un seul H1 par page ; hiérarchie sans saut ; titres de sections réels (pas des paragraphes stylés) | navigation par titres impossible |
| Reduced motion | Indispensable | voir `motion-guidelines.md` §6 | vertiges, abandon |
| Langue | Indispensable | `lang` correct sur html ; changement de langue balisé ; sélecteur de langue accessible | mauvaise prononciation |
| Iframes | Recommandé | `title` sur chaque iframe (vidéo, carte, moteur) | — |
| Taille de texte et zoom | Indispensable | pas de `maximum-scale=1` / `user-scalable=0` (observé chez FORESTIS et Borgo : à proscrire) | zoom impossible pour les malvoyants |
| Cookies | Recommandé | bandeau non bloquant, accessible, sans pièger la lecture ; refuser aussi facile qu'accepter | — |

Test minimal : navigation clavier complète de la home, d'une page hébergement et du moteur ; lecteur d'écran (VoiceOver / NVDA) sur ces trois pages ; axe DevTools sans erreur critique ; contraste vérifié sur 10 couples texte/fond.

## 3. SEO

### 3.1 Technique (Indispensable)
- Title unique ≤ 60 caractères : `<Nom de l'hébergement ou de la page> | <Établissement> — <Lieu>` ; meta description ≤ 155 caractères, orientée bénéfice + lieu (FORESTIS : « boutique wellness hotel in the Dolomites… spa, yoga and wellness packages »).
- Un H1 par page, portant le nom ou la promesse (pas « Bienvenue ») ; H2 pour chaque section.
- Canonical ; hreflang pour chaque langue + x-default (FORESTIS : en/de/it/x-default) ; sitemap XML ; robots ; 404 utile ; redirections 301 de l'ancien site.
- Données structurées : `Hotel` / `LodgingBusiness` / `Resort` / `VacationRental` (nom, adresse, géo, téléphone, étoiles, `amenityFeature`, `checkinTime`, `priceRange`), `HotelRoom` / `Accommodation` par page hébergement, `Offer`, `FAQPage`, `BreadcrumbList`, `Organization` avec logo et réseaux. Borgo n'expose qu'un `WebSite` : insuffisant.
- OG et Twitter : image 1200×630 spécifique par page clé.
- Contenu indexable : le texte doit être dans le HTML, pas uniquement dans les images ou les vidéos. Cibles : home ≥ 300 mots réels (Borgo : 94 mots ; Corazón : 207), page hébergement ≥ 250 mots, page destination ≥ 600 mots.

### 3.2 Contenu (Recommandé)
- Pages destination / alentours / saisons (« que faire à … en hiver ») : le levier SEO le plus rentable pour un hébergement indépendant ; Le Collectionist construit tout son maillage sur des pages destination et des pages thématiques (« chalets avec piscine », « villas animaux acceptés »).
- Pages expériences avec texte réel, pas seulement une galerie.
- Journal / carnet : 1 à 2 articles par mois, liés aux hébergements.
- Nommer les hébergements avec des noms propres mais garder le type dans le title (« Tower Suite — suite 55 m² vue Dolomites »).
- Avis : afficher des extraits réels avec source et date ; schema `AggregateRating` uniquement si les avis sont collectés sur le site.

### 3.3 International (Recommandé)
- Un dossier par langue (`/fr/`, `/en/`), traductions humaines, devises et formats de dates localisés, téléphone avec indicatif adapté (Le Collectionist affiche un numéro US en locale en-US et FR en locale fr).

## 4. Performance

### 4.1 Cibles (Indispensable)
| Métrique (mobile, 4G simulée) | Cible | Pourquoi |
|---|---|---|
| LCP | < 2,5 s | le hero doit apparaître avant que l'utilisateur doute |
| CLS | < 0,1 | pas de saut quand les images ou le moteur chargent |
| INP | < 200 ms | menu, calendrier, galerie réactifs |
| Poids home hors vidéo | < 3 Mo | — |
| Vidéo hero | ≤ 6 Mo desktop, ≤ 3 Mo mobile, 10–15 s, 24–30 fps, H.264 + WebM/AV1 | Seagate ≈ 14 Mo et Borgo ≈ 9 Mo par segment sont au-dessus |
| Scripts tiers | ≤ 5 domaines, ≤ 500 Ko | FORESTIS charge ≈ 6,4 Mo de scripts, majoritairement tiers |
| Requêtes | < 80 | — |
| Polices | ≤ 2 familles, ≤ 4 fichiers, woff2, `font-display: swap` ou `optional`, préchargées | FORESTIS charge un seul fichier de police (bonne pratique) |

### 4.2 Méthodes (Recommandé)
- Images : AVIF/WebP avec fallback, `srcset` + `sizes`, dimensions déclarées, `loading="lazy"` hors hero, `fetchpriority="high"` sur l'image LCP, CDN avec redimensionnement.
- Vidéo : `preload="metadata"` ou `none` + poster, chargement différé quand hors écran, arrêt quand non visible, formats multiples, pas de vidéo en boucle dans une page de liste.
- CSS et JS : critique en ligne, reste différé ; supprimer les bibliothèques redondantes (Borgo charge Bootstrap + Bootswatch + animate.css + fancybox + datepicker + jQuery + FontAwesome ; FORESTIS charge video.js et dash.js sans vidéo sur la home).
- Consentement : charger les tiers marketing après consentement ; le bandeau ne doit pas être le LCP.
- Moteur externe : précharger la connexion (`preconnect`) ; ouvrir dans le même onglet avec retour clair, ou dans un onglet dédié si le moteur ne peut pas être intégré.
- Fonts : sous-ensembles latin, `unicode-range`.
- Caching : HTML court, assets longs avec empreinte ; HTTP/2 ou 3.

### 4.3 Stabilité visuelle (Indispensable)
- Réserver l'espace du hero, du moteur, des bandeaux cookies, des galeries ; éviter les polices qui changent de métrique (`size-adjust`).

### 4.4 Équilibre immersion / performance
- Règle : une seule vidéo autoplay par page, le reste en image ou en vidéo au clic.
- Le préloader n'est acceptable que s'il masque un chargement réel < 800 ms ; sinon il ajoute de la lenteur perçue.
- Mesurer avant/après chaque ajout d'animation ; l'immersion se joue sur les 3 premières secondes : le hero doit être visible, net, contrasté, avec un titre lisible même si la vidéo n'est pas encore là (fond de secours de la couleur dominante).

## 5. Checklist rapide (à recopier dans le cahier des charges)

- [ ] Breakpoints testés ; hero ≤ 90 svh ; CTA visible sans scroll sur mobile.
- [ ] Barre CTA basse sur pages hébergement ; cibles ≥ 44 px ; corps ≥ 16 px.
- [ ] Vidéo hero : 2 versions, poster, ≤ 6/3 Mo, pause, pas d'autoplay en reduced motion / Save-Data.
- [ ] Contrastes AA ; focus visible ; skip link ; alt ; labels ; un H1 ; `lang` ; zoom autorisé.
- [ ] LCP < 2,5 s, CLS < 0,1, INP < 200 ms ; poids < 3 Mo hors vidéo ; tiers ≤ 5.
- [ ] Title/description uniques ; schema Hotel + HotelRoom + Offer + FAQ + Breadcrumb ; hreflang ; sitemap ; 301.
