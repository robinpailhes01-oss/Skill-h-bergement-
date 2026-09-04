# Fiche d'audit — Mas Girbau (clé `masgirbau`)

## 0. En-tête

- **Nom** : Mas Girbau — masía de 1596 louée en exclusivité (6 chambres, 14 personnes, 30 ha de forêt), Granera, à 50 km de Barcelone.
- **URL de départ** : https://www.masgirbau.com/ — **Date** : 2026-09-04 (17:32 UTC home, 17:40–17:44 UTC galerie, version EN et sonde réservation).
- **Environnement** : Chromium headless / Playwright, 1440×900 (desktop) et 390×844 DPR 2 (mobile). Balayage complémentaire `home-sweep.json` en 15 paliers de 1 139 px.

| Label | URL | Desktop | Mobile |
|---|---|---|---|
| home (one-page ES) | https://www.masgirbau.com/ | oui | oui |
| home-en | https://www.masgirbau.com/en | oui | oui |
| gallery | https://www.masgirbau.com/galeria | oui | oui |
| booking (sonde du CTA depuis la home) | https://www.masgirbau.com/ → lien sortant ouvert : https://www.facebook.com/people/Mas-Girbau/61553745852800/ | oui | non |
| home-sweep (15 paliers, 0 → 15 943 px) | https://www.masgirbau.com/ | oui | — |

**Limites de l'observation**

- 7 balises `<video>` (hero drone + 3 vidéos « Piedra / Fuego / Madera » en double) sont `autoplay muted loop playsinline` : les fichiers ont bien été téléchargés (§13) mais la **lecture, la boucle et le rendu des frames ne sont pas vérifiables** en headless ; les captures montrent une image figée.
- Le script `681152aa…_lenis-scroll-mas.girbau.txt` est chargé (fichier .txt servi comme script) mais aucun global `Lenis` n'est détecté par le balayage : **le lissage du scroll n'est pas vérifiable**. Les easings GSAP (`CustomEase` chargé) ne sont pas lisibles depuis le CSS : seules les courbes CSS sont mesurées.
- Le menu mobile n'a pas pu être ouvert (erreur Playwright « element outside viewport » sur le burger) : **aucune capture du menu mobile ouvert**.
- La sonde « booking » a suivi un lien sortant (Facebook, mur de connexion) au lieu du CTA « Reservar », dont les `href` sont des ancres (`#`, `#Reserva`). Le vrai moteur est un iframe BookingMood intégré dans la home ; il a été capturé en desktop (calendrier + formulaire) mais **aucune demande n'a été envoyée** et l'étape « prix / temporadas » n'a pas été vue.
- Hovers mesurés par styles calculés ; tactile non vérifiable ; Lighthouse indisponible (pas de LCP/CLS). Les captures pleine page (16 843 px) ne rendent pas le contenu de l'iframe.
- Le préloader (`.loader` fixed, `.loader-number`) était déjà à `opacity: 0` sur la première capture : son animation (compteur ?) est une hypothèse.

---

## 1. Positionnement de marque

**Faits observés**

- `<title>` : « Mas Girbau - Lujo rural a 50 km de Barcelona » ; meta description : masía historique, « herencia del tiempo », paix, « experiencia única ». Hero : H1 en deux lignes « Paz, historia » / « y silencio » (80 px, la seconde en italique), sous-titre italique « Lujo rural a sólo 50 km de Barcelona ».
- Objet vendu : **la maison entière** (« Nuestras 6 habitaciones pueden acoger cómodamente hasta 14 personas »), avec 3 compteurs en prologue (14 personas / 6 habitaciones / 10 camas) et une liste « Tu estancia en Mas Girbau incluye » de 12 items (6 dormitorios, 4 baños, 2 terrazas, 30 hectáreas de bosque, horno de leña, cafetera Nespresso…).
- Structure de la one-page : PRÓLOGO → LA CASA → galerie → ESENCIA (année 1596, « restaurada… respeto a la estructura original ») → slider « Piedra / Fuego / Madera » → SERVICIOS (01/ Escapadas en grupo … 06/ Residencia de artistas) → ENTORNO (El lago, El bosque, El silencio) → ACTIVIDADES → PETICIÓN DE RESERVA.
- Trois langues (hreflang x-default/es/ca/en) ; la version EN conserve la meta description en espagnol et contient des restes de traduction automatique (« 08183 Barn, Barcelona » pour Granera, « El silence » en mobile).
- Aucun prix visible sur la home ; trois onglets « Temporada baja Enero-Abril / alta Mayo-Agosto / alta Sept-Dic » existent dans le DOM (`visible: false`) : hypothèse d'une grille tarifaire saisonnière non affichée au chargement.

**Interprétation**

- Positionnement : **maison de famille historique en location exclusive**, luxe rural sans hôtel — pas de réception, pas de restaurant, pas de spa ; la promesse est le silence et l'histoire à une heure de Barcelone. Cible : groupes (familles élargies, amis, retraites de yoga, team building, résidences d'artistes), Barcelone et internationaux ; le curseur de gamme est donné par le mot « lujo » répété (titre, H2 « Desconexión y lujo rural ») et par des détails (lit Olot du XVIIIe, Nespresso) plutôt que par un prix.
- Territoire émotionnel : lumière dorée, pierre, feu, bois, brume ; personnalité de « conteur de maison » (prologue, essence, matières). Valeurs : patrimoine, lenteur, nature.
- Différence avec un site hôtelier générique : **il n'y a pas de liste de chambres à réserver** mais une seule unité ; les chambres servent de preuve de capacité, pas de choix. Le site vend un séjour de groupe comme on présenterait une maison à vendre : matériaux, distribution, entourage.
- Cohérence offre / mots / images : forte (photos de pierre et de forêt, vidéos de matières, texte sur le silence). Cohérence avec les interactions : forte aussi (le mouvement est lent, scrubbé, jamais ludique). Point de rupture : le moteur BookingMood (Inter, vert `#067f54`, bouton « Send booking Request » en anglais) et le lien « Ver más instalaciones » vers un PDF Google Drive.

**Enseignements réutilisables**

- Pour une location exclusive, remplacer la grille de chambres par **compteurs + distribution des lits + inclusions** : trois blocs suffisent à qualifier le groupe.
- Un « prologue » nommé comme tel (label PRÓLOGO) place le visiteur dans un récit avant l'inventaire.
- Nommer les matières (Piedra, Fuego, Madera) est un chapitre de marque à part entière, transposable à toute maison ancienne.

---

## 2. Première impression (5 premières secondes)

**Faits observés**

- `home-00-initial.png` (juste après chargement) : vidéo drone figée (colline, masía, brume dorée), titre en cours de révélation — « Paz, hist » et « y silenc » avec les caractères suivants coupés en biais —, wordmark « MAS GIRBAU » fantôme derrière le titre (~30 % d'opacité), aucune navigation encore visible, pilule « Reservar » déjà en place. `home-01-hero.png` : nav en capitales Inter 12 px espacées, logo « MAS GIRBAU » centré (deux lignes serif), globe + « ES » à droite, titre complet, sous-titre, pilule corail `#ff906d` 129×63 px, rayon 100 px, à y = 627.
- Pas de bannière cookies, pas de pop-up (`cookie: None`). Préloader `.loader` en `position: fixed` déjà invisible.
- Header 58 px transparent au chargement ; dès le premier palier de scroll (`936 px`), bande `#121602` avec monogramme « G », lien de section actif en corail, bloc « Reservar » corail 131×58 px collé à droite (rayon 0).
- Poids : la vidéo drone est demandée en MP4 (22,3 Mo, deux fois) et en WebM (18,2 Mo). FCP 2 052 ms, TTFB 1 128 ms, `load` 8 541 ms.

**Interprétation**

- Ce que l'on comprend : une maison isolée sur une colline, « paix, histoire, silence », 50 km de Barcelone, un bouton pour réserver. Le message tient en 3 mots + 1 distance : c'est le hero le plus lisible de la série.
- La révélation caractère par caractère avec coupe en biais (capture 00) est un vrai moment de marque : l'entrée du titre est lente et « typographique » ; le wordmark fantôme suggère un préloader logo qui se fond dans la vidéo (hypothèse : préloader avec compteur `.loader-number` puis fondu du logo).
- Distraction : aucune. Risque : le hero repose sur une vidéo de 18–22 Mo ; sur connexion moyenne le titre s'anime sur une image fixe ou un fond crème.
- Raison de continuer : le pull de l'italique (« y silencio ») et l'absence de tout autre élément — on descend pour voir la maison.

**Enseignements réutilisables**

- Hero = 3 mots + distance + un CTA. Aucun autre lien dans la zone.
- Révélation typographique du H1 par caractères masqués : signature à 0 coût média.
- Le passage transparent → bande sombre avec CTA carré collé à droite est une façon simple de rendre le bouton persistant sans le sortir de la grille.

---

## 3. Direction artistique

**Faits observés**

- Fonds mesurés : `#fff8eb` (2 491 éléments, crème), `#242c04` (443, vert très sombre — section Entorno), `#e1e7dd` (196, sauge — Actividades), `#252b15` (194, vert profond — Prólogo, `--parallex-color`), `#121602` (135, quasi-noir — header scrollé, footer, galerie), `#ff906d` (CTA). Textes : `#242c04` (773), `#fffcf5` (178), `#ffffff` (53). Variables CSS supplémentaires venant de l'iframe BookingMood : `--color-primary: #067f54`, `--color-available: #bbf7d0`, `--color-booked: #fecaca`, `--color-tentative: #fde68a`.
- Polices : « Editors » (fichiers `Editor'sNote-Hairline / Thin / Extralight / Light-Italic…`, 411 occurrences ; fonte commerciale, fonderie non prouvée) pour tous les titres et paragraphes éditoriaux ; Inter (Google Fonts, 9 graisses chargées, 80 occurrences) pour labels, descriptions de chambres, footer. `Editors-Text` et `NeueSwiss` déclarés en `@font-face` mais non utilisés.
- Échelle desktop : 160 px (« Piedra », graisse 100, interligne 1.0) / 80 px (H1 hero graisse 300 ; H2 graisse 200, interligne 90 px) / 64 px (H1 prologue, 70,4 px) / 40 px (H3, H4 noms de chambre italiques, 50 px) / 32 px (« Distribución… ») / 24 px (paragraphes Editors 200, interligne 32,7 px) / 20,8 px (paragraphe prologue, 31,2 px) / 16 px (Inter, 24 px) / 12 px (labels Inter, capitales, interlettrage ≈ 3 px). Occurrences : 80 px ×229, 40 px ×120, 32 px ×39.
- Échelle mobile : 100 / 56 / 52,8 / 40 (46 px) / 24 / 22,4 / 22 (28–30 px) / 16 (20–24 px) / 12.
- Italique utilisé comme accent à l'intérieur des titres (« masia histórica », « tiempo y la paz », « lujo rural », « pasado y presente », « tranquilidad », « naturaleza », « que te esperan cerca », « Reserva »).
- Grille : conteneurs 1 360 px (marges 40 px) et 940 px ; hero et images de section en pleine largeur ; colonnes texte 525–680 px ; blocs 2 colonnes asymétriques (texte 525 px / image 636×854 px en Esencia ; image 668 px / liste numérotée en Servicios).
- Formes : pilules (rayon 100 px) pour « Reservar » hero (129×63) et « Contacta con nosotros » (306×84, contour 1 px `#242c04`), cercles 40 px pour les onglets 1–6, cercles 290 px pour les activités, **arches** (masque `Arcs-Dark.svg`, 1 360×208 px) sur les 3 images du prologue et sur l'image de la section réservation ; bouton header sans rayon ; cartes de chambre bordées 1 px sans rayon.
- Iconographie : pictogrammes filaires 1 px (lit, baignoire, terrasse, sapin, four) ; monogramme « G » filaire dans le prologue ; fond de la section Entorno = **courbes de niveau topographiques** en trait fin sur vert sombre.
- Photos : 121 images (28 WebP, 91 SVG, 2 PNG), ratios 1,49 (1 210×810 galerie horizontale), 0,74 (636×854 Esencia), 0,69 (cartes Entorno), 6,55 (bandeau arche). Galerie : sources 1 900×2 500 et 2 500×1 700 sans `srcset`.
- Vidéos : hero 1 440×900 ; 3 vidéos matières 682×900 (moitié gauche de l'écran).

**Tableau de tokens approximatifs**

| Token | Valeur |
|---|---|
| Fond principal | `#fff8eb` |
| Fond profond 1 / 2 / 3 | `#252b15` / `#242c04` / `#121602` |
| Fond secondaire clair | `#e1e7dd` |
| Texte principal / inversé | `#242c04` / `#fffcf5` |
| Accent CTA | `#ff906d` (texte `#242c04`) |
| Serif éditoriale | Editors (Editor's Note), graisses 100–400 + italiques |
| Sans UI | Inter 400–500, 12–16 px |
| Titres | 160 / 80 / 64 / 40 / 32 px desktop ; 100 / 56 / 40 / 24 px mobile |
| Corps | 24 px Editors 200 (lh 1,36) ; 16 px Inter (lh 1,5) |
| Label | 12 px Inter capitales, ≈ 3 px d'interlettrage |
| Conteneur | 1 360 px, marges 40 px ; colonnes texte 525–680 px |
| Rayons | 100 px (pilules), 100 % (cercles), 0 (cartes, header CTA), arche SVG |
| Header | 58 px desktop, 48 px mobile |
| Transitions CSS | 0,1 s ×84, 0,2 s ×29, 0,4 s ×9 ; `cubic-bezier(.77,0,.175,1)` ×4, `(.165,.84,.44,1)` ×2, `(.6,.04,.98,.335)` ×1 (CTA) |

**Interprétation**

- Le système tient sur **une serif à contraste élevé en graisses très fines + trois verts + un corail**. Les graisses 100–200 à 80–160 px donnent un dessin de lettre presque filaire qui dialogue avec les pictogrammes 1 px et les courbes de niveau : c'est ce qui rend l'ensemble cohérent, pas la palette.
- Le corail `#ff906d` n'apparaît que sur trois objets (CTA, lien de nav actif, astérisques du formulaire) : c'est une couleur d'action, jamais décorative. C'est la première référence de la série à utiliser une couleur chaude saturée sans casser le registre calme.
- L'arche est le motif architectural (portail de pierre en plein cintre dans la vidéo « Piedra ») répercuté en masque d'image : un lien direct lieu → forme.
- Le vide est généreux (section La casa : 2 126 px pour un texte de 60 mots + carrousel + distribution) mais la section Facilities passe à une grille dense 4×3 : le site sait alterner.
- Faiblesse : deux systèmes de bouton coexistent (pilule Editors 200 / bloc Inter 400 dans le header / lien souligné Inter 24 px « Ver más instalaciones ») ; et le formulaire BookingMood importe une palette étrangère (vert `#067f54`, cases vert/rouge).

**Enseignements réutilisables**

- Graisse ultra-fine + très grand corps + italique d'accent = hiérarchie sans gras.
- Un motif géométrique tiré de l'architecture (ici l'arche) suffit comme signature de masque.
- Réserver la couleur chaude aux seuls objets d'action.

---

## 4. Architecture de la page d'accueil

Desktop 1440 px, hauteur totale 16 843 px (≈ 18,7 écrans) ; mobile 17 927 px.

| Position (px) | Section | Objectif | Contenu | Interaction | CTA | Émotion créée |
|---|---|---|---|---|---|---|
| 0–900 | Hero | Poser lieu, promesse, distance | Vidéo drone, H1 2 lignes, sous-titre italique | Révélation du titre par caractères ; nav qui apparaît ensuite | « Reservar » pilule → `#Reserva` | Calme, altitude |
| 900–2 246 | Prólogo (`#252b15`) | Résumer l'offre | Monogramme G, label, H1 64 px avec italiques, 3 compteurs, paragraphe centré, 3 photos en arche | Reveal `clip-path` des arches (5 clip-path au palier 1 139) ; split-text | — | Entrée dans un récit |
| 2 246–4 372 | La casa (`#Casa`) | Prouver capacité et caractère | H2, paragraphe, H3 « 6 habitaciones… 14 personas », onglets 1–6, carte chambre (nom italique, capacité, description Inter, photo 950 px, flèches), « Distribución de las habitaciones » 6 colonnes | Onglets Webflow + flèches ; compteur 1/6 | — | Curiosité, projection dans une chambre nommée |
| 4 372–5 182 | Galerie déplaçable | Montrer l'extérieur | Bande d'images 1 210×810 en défilement horizontal | Drag (Dragdealer chargé) ; bouton « Ver galería » flottant (sticky 64 px en mobile) | « Ver galería » → /galeria | Envie de voir plus |
| 5 182–6 773 | Esencia (`#Esencia`) | Raconter l'histoire | H2 2 lignes, paragraphe 24 px (1596, restauration), photo cour 636×854, petite photo vache + légende Inter | Reveal texte (4 transforms) | — | Authenticité |
| 6 773–7 673 | Slider matières | Donner une texture à la maison | 3 slides « Piedra / Fuego / Madera » : vidéo à gauche, numéro 1/3 géant, H1 160 px italique chevauchant l'image, paragraphe, 3 icônes-boutons | Slider (Swiper 8) ; 7 transforms + 3 opacités partielles | — | Sensorialité |
| 7 673–9 258 | Servicios (`#Servicios`) | Ouvrir aux usages de groupe | H2, paragraphe centré, photo pique-nique, liste 01/–06/ avec filets | Hover/liste statique (non mesuré) | « Contacta con nosotros » (pilule contour, `href="#"`) | Possibilités |
| 9 258–10 188 | Facilities | Rassurer sur l'équipement | H2 « Tu estancia… incluye », 12 icônes + libellés, lien souligné, paragraphe de contact | — | « Ver más instalaciones » → PDF Google Drive ; « ponerse en contacto » | Concret |
| 10 188–12 683 | Entorno (`#Entorno`, sticky) | Vendre le territoire | Fond `#242c04` topographique, H2 80 px, paragraphe 100 mots, 3 cartes verticales El lago / El bosque / El silencio | Section épinglée ; 77–85 transforms simultanés ; rideau qui découvre la photo pinnée | — | Immersion, respiration |
| 12 683–13 583 | Photo rivière | Respiration | Photo pleine largeur (élément sticky 900 px révélé) | Parallaxe / pin | — | Silence |
| 13 583–14 945 | Actividades (`#Actividades`, `#e1e7dd`) | Étendre le séjour | H2 centré, carrousel de cercles 290 px (Golf, Paseos a caballo, Senderismo, Cultura, Patrimonio, Gastronomía, Historia, Festividades) | Carrousel horizontal (Flickity chargé) | — | Légèreté |
| 14 945–16 430 | Petición de reserva (`#Reserva`) | Convertir | Label, H2 « *Reserva* Mas Girbau », texte « nos pondremos en contacto… », iframe BookingMood 656×794 (calendrier 2 mois + formulaire), photo en arche | Calendrier, champs | « Send booking Request » | Passage à l'acte |
| 16 430–16 843 | Footer (`#121602`) | Contact | Logo, adresse + « Cómo llegar », téléphone, e-mail, Instagram/Facebook | — | — | Clôture |

**Logique narrative**

- Début : promesse en 3 mots, puis un « prologue » qui donne les chiffres clés — le site annonce dès 900 px qu'il s'agit d'une maison pour 14.
- Construction du désir : la maison (chambres nommées) → l'extérieur (galerie) → l'histoire (1596) → la matière (pierre, feu, bois). Le désir est construit **par le patrimoine**, pas par le service.
- Moment où l'offre devient concrète : Facilities (10 188 px, 60 % de la page) avec la liste des 12 inclusions ; c'est tard, mais cohérent avec une location exclusive où l'on vend d'abord le lieu.
- Preuve : aucune preuve sociale (ni avis, ni presse, ni distinctions) ; la preuve est documentaire (année, matières, distribution des lits).
- Réservation : une seule zone, en bas, atteinte par ancre depuis les deux « Reservar ».
- Fin : footer minimal, sans mentions légales ni newsletter.

**Enseignements réutilisables**

- Ordre « promesse → chiffres → chambres → extérieur → histoire → matières → usages → inclusions → territoire → activités → réservation » convient à une maison unique.
- Placer les compteurs (personnes / chambres / lits) dans les 1 000 premiers pixels évite la question « c'est pour combien ? ».

---

## 5. Scroll et storytelling

**Faits observés**

- Rythme des fonds sur 16 843 px : crème (hero vidéo) → vert profond `#252b15` (900–2 246) → crème (2 246–6 773) → quasi-noir de la slide matières (6 773–7 673, panneau droit) → crème (7 673–10 188) → vert sombre `#242c04` (10 188–12 683) → photo (12 683–13 583) → sauge `#e1e7dd` (13 583–14 945) → crème → noir footer. `body-main` change effectivement de couleur aux paliers 936, 6 550, 10 293 et 13 100 (mesures `SCROLL`).
- Balayage GSAP : 24 ScrollTriggers ; transforms actifs par palier : 1 / 5 (+5 clip-path) / 1 / 0 / 0 / 2 / 7 (+3 opacités) / 4 / 1 / **77 / 80 / 17** / 1 / 0 / 0. Éléments épinglés à 10 249–12 527 : `div.sticky-element` (900 px) et `div.home-environment-section` (2 045 px). Attributs : 439 éléments split-text, 14 reveal, 5 parallaxe, 8 sticky, 99 `data-w-id` (interactions Webflow), 0 marquee, 0 scroll horizontal natif.
- Section Entorno (pic de 77–85 transforms) : dans `home-sweep-09/10` et `home-03-scroll5`, on voit successivement le H2 seul sur les courbes de niveau (le paragraphe n'est pas encore rendu), puis le H2 + paragraphe complet aligné à droite, puis les 3 cartes ; en `home-sweep-11`, le bloc vert sombre se termine en bande de 150 px au-dessus de la photo de rivière, qui occupe le reste du viewport. Le paragraphe fait ≈ 100 mots ; le H2 ≈ 10 mots.
- Mobile : mêmes pics (77 à 10 525 px, 79 à 11 840 px, 28 à 13 156 px) avec un seul élément épinglé (`div.sticky-element h=844`).
- Slider matières : vidéos 682×900 à y = 6 773 et 7 673 (3 balises visibles, 3 dupliquées à 0×0), compteur « 1 /3 », icônes latérales.
- Galerie déplaçable : `section.draggable-parallax` 810 px, 15 images ; bouton « Ver galería » (pilule translucide + icône 9 points) fixé en bas à droite de la bande sur desktop, cercle sticky 64×64 px à gauche sur mobile.

**Interprétation (fonction de chaque effet)**

- **Révélation du H1 par caractères masqués** (hero) : marque + rythme. Elle impose un tempo lent avant le premier scroll.
- **Arches en clip-path** (prologue, 5 clip-path au palier 1 139) : orienter le regard + marque. Les trois photos « s'ouvrent » comme des portails.
- **Split-text sur les titres** (439 éléments) : hypothèse confirmée visuellement pour le hero (coupe en biais des caractères) ; pour les H2 de section, les captures les montrent complets, donc le mode (mots ou lignes) reste une hypothèse. Fonction : rythme, chaque section « s'écrit » à l'arrivée.
- **Section Entorno épinglée avec 77–85 transforms** : c'est le cœur animé du site. Lecture la plus probable : le H2 et le paragraphe de ≈ 110 mots sont découpés en mots (split-text) et translatés/révélés au fil du scroll pendant que la section reste épinglée sur 2 045 px, soit environ 80 nœuds animés simultanément — ce qui correspond au nombre de mots visibles. Le nombre chute à 17 (palier 12 527) quand le texte est en place et que seules les cartes et les courbes bougent encore. Fonction : expliquer (le texte le plus long du site est lu mot à mot) + émotion (le vert sombre et les courbes de niveau évoquent une carte de randonnée nocturne).
- **Rideau vert → photo de rivière** : la section Entorno (z-index 1) glisse au-dessus de `div.sticky-element` (photo, z auto) qui reste épinglée ; puis `home-bg-section` (900 px, transparent) laisse la photo à découvert. Fonction : respiration + orienter le regard vers le paysage après un pavé de texte. C'est la transition la plus forte de la page.
- **Vidéos de matières** : émotion / texture ; en headless elles sont des photos fixes, l'effet réel (pierre, flammes, bois en mouvement) est une hypothèse.
- **Galerie déplaçable** : action (rejoindre la galerie) + rythme (rupture horizontale entre deux blocs verticaux).
- **Carrousel de cercles** (Actividades) : rythme, légèreté après le bloc sombre.
- Densité : 932 mots pour 16 843 px (≈ 55 mots/1 000 px), avec une respiration de 900 px (photo rivière) et une autre de 810 px (galerie). Envie de poursuivre : soutenue jusqu'à la section Entorno ; la partie Facilities → Actividades est plus plate.

**Enseignements réutilisables**

- Un seul bloc « à 80 transforms » sur toute la page, placé aux 2/3, suffit à donner une impression de site très animé ; le reste est calme.
- Enchaîner texte long épinglé → rideau → photo pleine largeur crée une pause que l'on ressent physiquement.
- Les changements de fond ne sont pas des dégradés continus mais des paliers nets alignés sur les chapitres : plus lisible qu'un fond qui glisse.

---

## 6. Animations et micro-interactions

Libs prouvées : GSAP 3.10.4 + CustomEase + ScrollTrigger (24 triggers), split-type (chargé deux fois : jsDelivr gh + unpkg), ukiyo.js 4.1.2 (parallaxe), Swiper 8 (home) et Swiper 10 (galerie), Flickity 2, Dragdealer 0.9.9, jQuery 3.5.1, Webflow (99 `data-w-id`). CSS : 18 `@keyframes`, 3 `clip-path`, 4 `will-change`, 9 `position: sticky`, 8 `scroll-snap`, 3 `backdrop-filter`.

| Animation | Déclencheur | Élément | Effet | Fonction | Risque UX |
|---|---|---|---|---|---|
| Préloader | Chargement | `.loader` fixed, `.loader-number` | Hypothèse : compteur numérique puis fondu (déjà à opacity 0 à la capture) | Marque | Attente sur 18–22 Mo de vidéo |
| Révélation du H1 | Chargement | H1 hero (split-text caractères) | Caractères révélés en séquence avec coupe en biais (masque + rotation, capture 00) ; wordmark fantôme derrière | Marque, rythme | Titre illisible ~1 s ; pas de version reduced-motion |
| Apparition de la nav | Chargement (après le H1) | `.header` | Nav absente en capture 00, présente en 01 | Hiérarchie | — |
| Header scrollé | Scroll > ~60 px | `.header` | Transparent → bande `#121602` 58 px, logo → monogramme G, lien actif corail (scroll-spy) | Orientation | — |
| Hover CTA | Survol | `.button-reserve` | Icône translatée de 2,4 px en X, 0,2 s `cubic-bezier(.6,.04,.98,.335)` (ease-in agressif) | Feedback | Très discret |
| Arches | Scroll (palier 1 139) | 3 images prologue | 5 `clip-path` actifs : ouverture en arche | Regard, marque | — |
| Split-text des titres | Scroll (ScrollTrigger) | 439 nœuds | Hypothèse : lignes/mots translatés + opacité | Rythme | Coût CPU sur mobile |
| Carrousel chambres | Clic onglets 1–6 / flèches | Webflow Tabs + Swiper | Changement de carte, compteur 1/6 | Explorer | Pas de swipe vérifié ; onglets 40 px |
| Galerie déplaçable | Drag | `.draggable-parallax` (Dragdealer) | Défilement horizontal des 15 images | Explorer | Drag non découvrable au clavier |
| Parallaxe | Scroll | 5 éléments `data-*parallax` (ukiyo) | Hypothèse : décalage de fond | Profondeur | — |
| Slider matières | Flèches / icônes | Swiper 8 | Vidéo + H1 160 px + texte ; 7 transforms + 3 opacités partielles | Sensoriel | Autoplay des 3 vidéos non vérifiable |
| Section Entorno | Scroll (pin 2 045 px) | H2 + paragraphe + cartes | 77–85 transforms simultanés, 2 clip-path | Expliquer, immersion | Longueur de pin (2,3 écrans) ; lecture forcée |
| Rideau rivière | Scroll | `.sticky-element` (900 px) sous la section | Photo découverte par le départ de la section | Respiration | — |
| Cercles activités | Drag / flèches | Flickity | Défilement horizontal | Légèreté | Pas de flèches visibles en capture |
| Rotation du X | Survol | `.link-block-12` (galerie) | `matrix(0,1,-1,0)` = rotation 90° | Feedback | — |
| Transitions galerie | Navigation | Swiper 10 | 0,8 s ×324 éléments | Fluidité | 0,8 s ressenti lent pour 88 images |
| Reduced motion | `prefers-reduced-motion` | — | 1 seule règle (Tailwind `.motion-reduce\:transition-none`, importée par l'iframe) ; 0 élément animé CSS, 85 transitions actives, 7 vidéos toujours en autoplay | — | Aucune prise en compte réelle |

**Durées/easings** : CSS mesurés 0,1 s (×84), 0,2 s (×29), 0,4 s (×9), 0,8 s (×3), 1,3 s (×1), 2 s (×1) ; courbes `cubic-bezier(.77,0,.175,1)` (ease-in-out marqué, ×4), `(.165,.84,.44,1)` (ease-out, ×2), `(.137,.637,.355,1)`. Les tweens GSAP (durées, `CustomEase`) ne sont pas lisibles : hypothèse de durées 0,8–1,3 s pour les reveals de texte d'après les valeurs CSS présentes.

**Interprétation** : le site combine trois moteurs (Webflow Interactions, GSAP/ScrollTrigger, sliders tiers) — c'est visible dans la duplication des scripts (split-type ×2, Swiper ×2 versions, Flickity + Swiper + Dragdealer pour trois carrousels). Le résultat visuel est cohérent, mais le coût technique est élevé (113 scripts, 4,97 Mo).

**Enseignements réutilisables** : un seul carrousel lib ; split-text limité aux H1/H2 ; ajouter une règle `prefers-reduced-motion` qui désactive le pin et les vidéos.

---

## 7. Navigation et architecture de l'information

**Faits observés**

- Desktop : nav de 6 ancres (LA CASA `#Casa`, ESENCIA, SERVICIOS, ENTORNO, ACTIVIDADES) + GALERÍA (/galeria, flèche ↗) réparties de part et d'autre du logo ; sélecteur de langue globe + « ES » (Ca/En en liens cachés) ; « Reservar » (`href="#"` dans le header, `#Reserva` dans le hero). Lien actif en corail au scroll.
- Mobile : header 48 px `#121602` masqué au chargement (`translateY(-48px)`), affiché dès 1 316 px ; burger à gauche, monogramme G, « ES » globe ; **barre « Reservar » fixe en bas, 390×64 px, `#ff906d`** (`a.hero-btn-mobile`, ancre `#Reserva`), présente sur toutes les captures de scroll. Menu ouvert non capturé.
- Galerie : page à part (`/galeria`), fond `#121602`, 3 onglets (HABITACIONES / ESPACIOS COMUNES / ENTORNO, Inter 12 px capitales, interlettrage 3,2 px), Swiper centré avec aperçus latéraux, légende « Habitación Los Santos », croix de fermeture en haut à droite ; 88 images, 31 mots, `h1count 0`, `title` « Galeria ».
- Infos essentielles : distance (hero), capacité (prologue à 900 px), distribution des lits (≈ 3 900 px), inclusions (≈ 9 500 px), adresse/téléphone/e-mail (footer + « Cómo llegar » Google Maps). Prix : absents.
- Étapes pour atteindre l'offre : 1 clic (« Reservar » → ancre `#Reserva`) ; pour une chambre : 1 scroll + 1 clic d'onglet.

**Interprétation**

- One-page à ancres : l'IA est le sommaire du récit, pas un catalogue. Avec 6 sections et une seule unité vendue, c'est justifié.
- Le CTA persistant existe sur les deux supports (bloc header desktop, barre basse mobile) : c'est le meilleur dispositif de conversion de la série sur mobile.
- Frustrations : « Contacta con nosotros » a `href="#"` (aucune destination mesurée) ; « Ver más instalaciones » quitte le site vers un PDF Google Drive ; « Actividades » du menu caché pointe vers `#` ; la galerie n'a pas de lien retour explicite hormis la croix.

**Enseignements réutilisables**

- Sur mobile, une barre CTA basse pleine largeur de 64 px vaut mieux qu'un bouton dans le header.
- Un lien « Galería ↗ » signale visuellement la sortie de la one-page.

---

## 8. Parcours de réservation et conversion

**Faits observés**

- Premier CTA : « Reservar » pilule au centre du hero (y = 627, 129×63 px), puis bloc header dès 936 px, et barre basse en mobile dès 0 px.
- Formulations : « Reservar » (×2), « Contacta con nosotros », « Ver más instalaciones », « ponerse en contacto », « Cómo llegar ». Aucune distinction découvrir / demander / réserver dans les libellés ; la section s'appelle pourtant « PETICIÓN DE RESERVA » et son texte annonce une prise de contact après réception de la demande.
- Moteur : iframe BookingMood (`bookingmood.com/embed/6ae328b0…`, 656×794 px desktop, 350×842 mobile, sans attribut `title`) : calendrier deux mois (septembre/octobre 2026, cases vertes disponibles, rouges réservées, demi-cases pour les jours de transition ; libellés « September / October, Mo Tu We » en anglais), champs Nombre / Correo Electrónico* / Teléfono*, bouton « Send booking Request » (en anglais, état désactivé corail pâle). Requêtes vers `api.frankfurter.dev` (taux de change ; hypothèse : conversion de devise du moteur). Onglets « Temporada baja / alta » présents mais invisibles.
- Aucun `<form>` natif détecté hors iframe, aucun `dateInputs`. Pas de prix, pas d'acompte, pas de conditions, pas d'avis, pas de badges, pas de bénéfice réservation directe, pas de packages ; les services (yoga, team building, résidences) sont listés sans tarif ni formulaire dédié.
- Contact humain : téléphone et e-mail dans le footer ; la sonde a ouvert Facebook (page « Not yet rated (1 Review) », 10 abonnés).
- Points de rupture : même page (pas de nouvel onglet), mais changement d'identité dans l'iframe (Inter, vert `#067f54`, cases vert/rouge, anglais), et « Ver más instalaciones » vers Google Drive.

**Interprétation**

- Le parcours est un **parcours de demande** (dates + coordonnées → confirmation par l'hôte), pas un moteur transactionnel. Le libellé « Reservar » survend légèrement ce que fait la section, mais « Petición de reserva » corrige au moment d'agir.
- L'absence de prix, de capacité minimale et de conditions (séjour minimum, ménage, acompte) laisse le visiteur sans repère pour une location à 14 ; les onglets « Temporada » cachés suggèrent que la grille existe et n'est pas montrée — c'est la principale perte de conversion.
- Le mélange de langues dans l'iframe (mois, bouton) casse le soin apporté au reste.

**Enseignements réutilisables**

- Pour une maison exclusive, afficher au moins « à partir de … / nuit, séjour minimum … » près du calendrier.
- Nommer la section « Demande de réservation » et le bouton « Enviar solicitud » : la promesse et l'action concordent.
- Vérifier la localisation de l'iframe tiers (mois, boutons, devise).

---

## 9. Pages chambres / unité vendue

L'unité vendue est **la maison entière pour une durée à définir** ; il n'existe pas de page chambre. L'analyse porte sur la section « La casa » (home, `#Casa`, desktop et mobile) et sur la galerie.

**Faits observés (desktop)**

- H2 « Desconexión y *lujo rural* » 80 px, paragraphe 24 px (60 mots), H3 « Nuestras 6 habitaciones pueden acoger cómodamente hasta 14 personas: » 40 px.
- Onglets 1–6 (cercles 40 px, actif `#242c04`) ; carte bordée 1 px : compteur « 1 / 6 », nom en italique 40 px (« Los Santos »), « Capacidad 2 pax » 24 px, description Inter 16 px (≈ 55 mots, lit de style Olot du XVIIIe), photo 950×380 px, flèches rondes.
- « Distribución de las habitaciones: » 32 px puis 6 colonnes séparées par des filets : pictos lits, nom (Editors 24 px), « 2 PAX » (Inter 12 px capitales), configuration (1 cama doble / 1 cama doble + 1 terraza privada / 3 camas individuales / 1 cama doble + 1 cama individual + 1 baño privado / 2 camas individuales / 1 cama doble). Noms : Los Santos, El Inglés, La Tribu, El heredero, La Isabel, El Rey.
- Galerie : onglet HABITACIONES, 1 image centrée 720×504 (source 2 500×1 700), aperçus latéraux estompés, légende.

**Faits observés (mobile)**

- H2 40 px, H3 24 px, onglets 1–6 sur une ligne (cercle actif 40 px, chiffres 16 px), carte : nom italique 24 px + « Capacidad 2 pax » sur la même ligne, description Inter 16 px (interligne 20 px), photo dessous ; distribution en 2 colonnes ×3 lignes ; barre « Reservar » 64 px toujours visible.
- Galerie mobile : onglets empilés en haut à gauche, image portrait 508×844, flèches, légende 24 px.

**Interprétation**

- Ordre des informations : caractère (nom, italique) → capacité → récit de la chambre → photo → distribution. La chambre n'est pas vendue pour elle-même : la fiche sert à **rassurer sur la répartition d'un groupe** (qui dort où), d'où la distribution en tableau, plus utile ici qu'une page par chambre.
- Manques : pas de plan d'étage, pas de surface, pas de photo de salle de bain, pas de mention des chambres avec/sans bain privé sauf « El heredero ». Pas d'accès direct depuis un onglet vers les photos de galerie de la même chambre.
- La galerie compense (88 images) mais sans hiérarchie chambre par chambre (une seule légende visible à la fois).

**Enseignements réutilisables**

- Pour une location entière : carte chambre courte + **tableau de distribution des lits** avec pictos, sur la home, avant la galerie.
- Lier chaque onglet chambre à la galerie filtrée correspondante.

---

## 10. Copywriting

**Faits observés**

- 932 mots indexables (home ES), 912 en mobile, 888 en EN ; 31 mots sur la galerie.
- Labels de section en capitales Inter 12 px, à valeur de chapitre : PRÓLOGO, LA CASA, ESENCIA, SERVICIOS, ENTORNO, ACTIVIDADES, PETICIÓN DE RESERVA.
- Titres construits sur le binôme nom + italique : « Paz, historia / *y silencio* », « Desconexión y *lujo rural* », « Un encuentro entre *pasado y presente* », « Un refugio de *tranquilidad* en plena armonía con la *naturaleza* », « *Reserva* Mas Girbau ». Les mots en italique sont toujours le mot-clé émotionnel.
- Champ lexical : paz, silencio, historia, herencia, tiempo, refugio, tranquilidad, naturaleza, calma, ritmo pausado, testimonio histórico, legado, respeto a la estructura original ; matières : piedra, fuego, madera. Sensoriel : « sonidos de la naturaleza », « la paz te abraza en cada rincón », « cada amanecer pintando el cielo », « un abrazo suave » (lac).
- Tutoiement (« Descubre », « Te damos la bienvenida », « Ven y siente ») sauf dans les zones de service (« Su comodidad… », « nos pondremos en contacto ») où le vouvoiement revient.
- Caractéristiques techniques traitées en listes courtes (12 inclusions, 6 distributions) séparées du récit ; les services de groupe sont une liste numérotée 01/–06/ sans description.
- Titres des cartes territoire en un ou deux mots : El lago, El bosque, El silencio ; activités en un mot (Golf, Cultura, Historia).
- Coquilles : un accent grave parasite en fin de paragraphe Servicios (« actividades.` »), traductions automatiques en EN.

**Interprétation**

- Mécanisme principal : **chapitrage** (prologue → essence → matières) qui fait lire la page comme un livre de maison ; les italiques indiquent où l'émotion doit se poser.
- Le luxe est dit une fois (« lujo rural ») et prouvé par des détails (lit Olot XVIIIe, 30 ha, 1596), jamais par des adjectifs de service.
- Transformation prestation → expérience : la cheminée, le four à bois, le lac ne sont pas des équipements mais des « moments » (El silencio est une carte à part entière).
- CTA : neutres (« Reservar », « Contacta con nosotros ») ; l'univers n'est pas prolongé dans les boutons.
- Faiblesse : deux voix (tu/usted) et un ton uniforme sur 900 mots ; le paragraphe Entorno (≈ 100 mots) reprend les mêmes formules que le prologue.

**Enseignements réutilisables**

- Chapitrer avec des labels de livre (Prologue, Essence) ; italiser le mot-clé.
- Nommer les lieux naturels comme des pièces de la maison (le lac, la forêt, le silence).
- Isoler les faits en listes numérotées ou à pictos ; garder la prose pour le lieu.

---

## 11. Photographie et vidéo

**Faits observés**

- Vidéos : drone hero (colline, brume, lumière rasante ; MP4 22,3 Mo / WebM 18,2 Mo), 3 vidéos matières en format portrait 682×900 (piedra 1,8–2,4 Mo ; fuego 0,7–1,4 Mo ; madera 0,5–1,3 Mo). Lecture non vérifiable.
- Photos (home) : masía vue de la vallée (bandeau 1 360 px), chambre Los Santos (lit jaune safran, tête de lit peinte, porte en bois), cour aux jarres et pierre, vache dans un pré, arbres à contre-jour au soleil couchant, terrasse en pierre sur la vallée, jeune femme assise dans l'herbe (seule présence humaine visible sur la home), pique-nique dressé sur l'herbe (lanternes, agrumes), lac de Rubió, chemin forestier, masía au crépuscule, rivière et pinède, cercles d'activités (golf, cavalière de dos, randonneuse de dos, mains tressant de l'osier, village de pierre), masía sous ciel de cumulus (arche).
- Lumière : quasi exclusivement dorée / fin de journée ; teintes ambre, safran, vert olive, pierre blonde. Cadrages : plans larges de paysage, plans moyens d'architecture, très peu de gros plans hors matières.
- Galerie : 88 images, 78 WebP + 3 JPG lourds (3,07 Mo, 2,69 Mo, 2,13 Mo), sources 1 900×2 500 / 2 500×1 700, 0 `srcset`, 7 lazy.
- Proportion : sur la home, ≈ 60 % lieu/architecture, 30 % paysage, 10 % vie (pique-nique, personnage) ; personnes toujours de dos ou sans visage.

**Interprétation**

- La photo raconte une maison dans son paysage à l'heure dorée ; les vidéos de matières (pierre, feu, bois) sont l'idée la plus réutilisable : elles donnent une texture au lieu sans montrer une prestation.
- Peu de présence humaine et pas de scènes de groupe alors que la cible est un groupe de 14 : c'est un manque pour la projection (tablée, salon, terrasse occupée).
- Cohérence chromatique très forte (ambre / olive / crème) — elle explique la palette du site.

**Shot list pour reproduire ce niveau**

1. Drone à l'aube ou au coucher, approche lente de la maison sur sa colline (20–30 s, boucle).
2. Trois clips portrait de matières en plan fixe : mur de pierre avec porte, feu de cheminée ou four, poutres/bois (10 s chacun, boucle).
3. Façade et cour intérieure sous lumière rasante, cadrage frontal pour les masques en arche.
4. Chaque chambre : un plan large depuis la porte + un détail (tête de lit, textile) ; une salle de bain.
5. Terrasse avec vue, table dressée, pique-nique ou petit-déjeuner dans l'herbe.
6. Trois paysages « nommés » (eau, forêt, vue) en format vertical 2:3.
7. Deux scènes de vie de groupe sans visage (tablée, silhouettes sur la terrasse au crépuscule).
8. Série d'activités en carré pour cercles (7–8 sujets), même traitement colorimétrique.
9. Animaux et détails ruraux (bétail, jarres, poterie) pour les respirations.

---

## 12. Mobile (390×844, DPR 2)

**Faits observés**

- Hero : vidéo pleine hauteur 844 px, burger + logo deux lignes + globe « ES » sur fond transparent, H1 56 px / 52,8 px italique, sous-titre 28,8 px sur 2 lignes, **barre « Reservar » fixe en bas 390×64 px `#ff906d`** (texte 16 px Editors 200). Header 48 px `#121602` apparaît au scroll (translateY −48 → 0).
- Titres : H2 40 px (interligne 46 px), H3 24 px, « Piedra » 100 px, paragraphes 22 px Editors (interligne 28–30 px), descriptions Inter 16 px / 20 px.
- Rythme : hauteur totale 17 927 px (≈ 21 écrans) ; sections en une colonne ; distribution des lits en 2 colonnes ; slider matières empilé (photo 422 px au-dessus, panneau sombre avec flèches, icônes et texte) ; carrousel de cercles avec le 2e cercle rogné à droite (signale le défilement) ; galerie déplaçable avec bouton rond sticky « Ver galería » 64 px.
- Animations : conservées — 77 et 79 transforms aux paliers 10 525 / 11 840, `sticky-element` 844 px épinglé, courbes de niveau et rideau rivière présents (scroll4/scroll5).
- Boutons : « Reservar » 390×64 px ; « Contacta con nosotros » 350×58 px ; onglets 40×40 px ; galerie mobile : flèches ≈ 100×60 px.
- Moteur : iframe 350×842 px (calendrier + formulaire empilés).
- Perf mobile : TTFB 1 020 ms, FCP 1 712 ms, DCL 2 698 ms, load 3 978 ms ; **206 requêtes, 69,0 Mo** dont 56,6 Mo de média (la même vidéo drone en MP4 22,3 Mo et WebM 18,2 Mo est demandée). Galerie mobile : DCL 11 684 ms, 28,2 Mo d'images.
- Lisibilité : paragraphes 22 px sur 350 px de large ≈ 38 caractères/ligne ; les textes Inter 16 px sur fond sombre (cartes Entorno) restent lisibles ; les titres 40 px en graisse 200 sur crème gardent un contraste élevé.
- Problèmes : menu non ouvrable par l'outil (burger hors viewport au moment du clic : hypothèse d'un header masqué jusqu'au premier scroll) ; vidéo de 18–22 Mo sur mobile ; bouton « Ver más instalaciones » 200×30 px (zone tactile < 44 px) ; l'onglet 6 du carrousel touche le bord droit.

**Interprétation**

- Le mobile est une vraie version, pas un repli : les mécanismes de scroll sont conservés, le CTA est plus présent qu'en desktop, la typographie descend à 56 px sans perdre le dessin.
- Le coût est le poids : 69 Mo pour une home mobile, dont 40 Mo de la seule vidéo hero en double encodage — le point faible le plus concret du site.

**Enseignements réutilisables**

- Barre CTA basse 64 px + header masqué en haut de page = hero plein écran sans concurrence.
- Servir une vidéo hero mobile distincte (< 3 Mo) et un seul format.

---

## 13. Performance, accessibilité, SEO

**Faits observés**

- Desktop home : TTFB 1 128 ms, FCP 2 052 ms, DCL 5 953 ms, load 8 541 ms ; **401 requêtes, 104,5 Mo** (média 74,9 Mo / 13 fichiers ; images 22,7 Mo / 226 ; scripts 5,0 Mo / 113 ; fonts 0,66 Mo / 20 ; CSS 0,68 Mo). EN : load 7 385 ms. Galerie desktop : load 4 521 ms, 222 requêtes, 56,5 Mo (168 images, 54,3 Mo).
- Plus gros fichiers : drone MP4 22,3 Mo (×2) et WebM 18,2 Mo, piedra WebM 2,4 Mo, image `BG9G6240-min (1).webp` 963 Ko ; galerie : `entorno-088.jpg` 3,07 Mo, `slide 3.jpg` 2,69 Mo, `Frame-1.jpg` 2,13 Mo.
- Lazy loading : 104/121 images `loading="lazy"` sur la home, 27 avec `srcset` ; galerie 7/88 lazy, 0 `srcset`. Vidéos `preload="metadata"`.
- Tiers : website-files.com (275 req.), bookingmood.com (86), unpkg (12), cdnjs (8), jsDelivr (4), cloudfront (4), fonts (6), frankfurter.dev (2).
- Contrastes estimés : `#242c04` sur `#fff8eb` ≈ 13,6:1 ; `#fffcf5` sur `#242c04` ≈ 13,4:1 ; `#242c04` sur `#ff906d` ≈ 6,6:1 ; `#ff906d` sur `#121602` (lien actif) ≈ 8,3:1 ; label 12 px `#242c04` sur `#e1e7dd` ≈ 11:1. Graisse 100–200 à 24 px : contraste de trait faible malgré le ratio de couleur.
- Clavier / ARIA : `focusOutlineNone` 81, `tabindex="-1"` 57, `aria-hidden` 167, 33 liens sans nom, 1 iframe sans `title`, 0 bouton sans nom, pas de skip link ; landmarks main 1 / nav 5 / header 3 / footer 0. Alt : 119 images sur 121 avec `alt=""` (2 alt renseignés : « Cama », « Horno de piedra para pizzas ») ; galerie 88/88 vides.
- Reduced motion : 1 règle CSS (Tailwind, iframe) ; 0 animation CSS désactivée, 85 transitions actives, 7 vidéos en autoplay ; capture `home-04-reduced-motion` identique au hero normal.
- Structure : `h1count 9` (hero ×2, prologue, « Piedra » 160 px et, hypothèse, « Fuego »/« Madera » + EN) ; H2 → H3 → H4 cohérents à l'intérieur des sections ; H2 « Tu estancia… » au même niveau que les titres de section.
- Métadonnées : `title` et `description` présents (identiques en EN, non traduits) ; `og:title`, `og:description` ; **pas de canonical, pas de JSON-LD, pas d'`og:image` détecté** ; hreflang x-default/es/ca/en ; `lang` correct par version. Galerie : `title` « Galeria », pas de description, 31 mots.
- Contenu indexable : 932 mots ES / 888 EN, 100 % en HTML (les split-text restent du texte).
- Stabilité visuelle : non mesurée (pas de CLS) ; les fonts sont 6 fichiers Editor's Note woff2 + Inter ; risque de FOUT limité par `webfont.js`.

**Interprétation**

- Le site immersif paie son immersion en octets : ~100 Mo desktop / 69 Mo mobile est 5 à 10 fois au-dessus des références de la série, principalement à cause d'un double encodage de la vidéo hero chargé en entier (`status 206` mais 22 Mo transférés) et de JPG non compressés en galerie.
- L'accessibilité est celle d'un Webflow animé : contrastes excellents, mais focus supprimé, 57 `tabindex=-1` (sliders), alt vides et aucune prise en compte de reduced-motion.
- SEO : bases correctes (hreflang, title, description) mais 9 H1, pas de canonical ni de données structurées (LodgingBusiness), description non traduite en EN.

**Enseignements réutilisables**

- Un seul format vidéo par device, poster image, `preload="none"` hors viewport.
- Compresser toute image de galerie < 400 Ko et fournir `srcset`.
- Un H1 par page ; JSON-LD `LodgingBusiness` avec capacité et adresse.

---

## 14. Conclusion

**15 meilleurs éléments**

1. Hero en 3 mots + distance + CTA unique, sans bannière ni pop-up.
2. Révélation du H1 par caractères masqués avec coupe en biais et wordmark fantôme (capture 00).
3. Header transparent → bande `#121602` avec monogramme, scroll-spy en corail et CTA carré collé à droite.
4. Barre « Reservar » fixe en bas de l'écran mobile (390×64 px).
5. Section « Prólogo » : label de chapitre, compteurs 14 / 6 / 10, italiques d'accent.
6. Masques en arche tirés de l'architecture, révélés en clip-path.
7. Tableau « Distribución de las habitaciones » à 6 colonnes avec pictos lits.
8. Chapitre « Piedra / Fuego / Madera » : vidéo portrait + numéral 160 px graisse 100 + texte.
9. Section Entorno épinglée sur fond topographique avec 77–85 transforms (texte lu mot à mot).
10. Rideau vert sombre découvrant la photo de rivière épinglée (respiration de 900 px).
11. Paliers de fond nets (crème / vert profond / sauge / noir) alignés sur les chapitres.
12. Serif Editor's Note en graisses 100–300 à 80–160 px + Inter 12 px pour les labels.
13. Corail `#ff906d` réservé à l'action (CTA, lien actif, astérisques).
14. Liste numérotée 01/–06/ des usages de groupe (yoga, team building, résidence d'artistes).
15. Galerie en page dédiée plein écran, à onglets, avec aperçus latéraux estompés.

**5 faiblesses / limites**

1. Poids : 104,5 Mo desktop, 69 Mo mobile (vidéo hero MP4 + WebM 40 Mo, JPG de galerie 2–3 Mo).
2. Aucun prix, aucune condition, aucune preuve sociale ; onglets « Temporada » cachés.
3. Iframe BookingMood non localisé (mois et bouton en anglais), palette étrangère, pas de `title`.
4. Accessibilité : 81 `outline: none`, 119 alt vides, 0 prise en compte de reduced-motion, 9 H1, pas de canonical/JSON-LD.
5. Empilement technique (Swiper 8 + 10, Flickity, Dragdealer, split-type ×2, 113 scripts) et liens morts (`href="#"` sur « Contacta con nosotros »), PDF Google Drive externe.

**10 principes réutilisables**

1. Une unité vendue = compteurs + distribution des lits + inclusions, pas de grille de chambres.
2. Chapitrer la page (Prologue, Essence, Matières) et italiser le mot-clé de chaque titre.
3. Un seul bloc très animé, épinglé aux 2/3 de la page ; le reste en reveals simples.
4. Texte long → rideau → photo pleine largeur épinglée = respiration.
5. Motif géométrique tiré du bâtiment (arche) comme masque d'image.
6. Couleur chaude uniquement pour l'action.
7. CTA persistant adapté au support : bloc header desktop, barre basse mobile.
8. Nommer les éléments naturels comme des pièces (El lago, El bosque, El silencio).
9. Vidéos de matières en portrait, courtes, en boucle, à la place d'une vidéo de service.
10. Fond par paliers nets synchronisés avec les chapitres plutôt que dégradés continus.

**Éléments propres à la marque à ne pas copier** : le nom des chambres (Los Santos, El Inglés, La Tribu, El heredero, La Isabel, El Rey), la triade Piedra / Fuego / Madera telle quelle, l'année 1596, le monogramme « G », les textes du prologue et de l'Entorno, la photo de la masía sur sa colline.

**Ce que ce site apporte que les sites « quiet luxury » (FORESTIS, Seagate, Le Collectionist) n'apportent pas**

- **Rythme chromatique par chapitres** : cinq fonds distincts (crème, vert profond, sauge, quasi-noir, photo) là où le quiet luxury reste sur un ou deux blancs cassés.
- **Storytelling matériel** : un chapitre entier sur les matériaux de la maison (vidéo + numéral géant + texte), plutôt qu'une liste de services.
- **Section scrubbée épinglée sur 2 045 px** avec 80 nœuds animés et fond cartographique : le mouvement sert la lecture d'un texte, pas seulement l'apparition d'images.
- **Barre CTA basse mobile** et **scroll-spy coloré** : une conversion plus visible que sur les références minimalistes.
- **Vente d'une maison entière** avec tableau de distribution des lits — un format que les hôtels n'ont pas.

**Notes /10**

- **Branding : 8/10** — promesse en 3 mots + distance, chapitrage (Prólogo/Esencia/matières), italiques d'accent et corail d'action cohérents ; pénalisé par la traduction EN automatique et l'iframe non brandé.
- **Direction artistique : 8,5/10** — serif fine 80–160 px, cinq fonds par paliers, arches, courbes de niveau, photo à l'heure dorée ; deux systèmes de bouton et le vert `#067f54` du moteur retirent le demi-point.
- **Animations : 8/10** — 24 ScrollTriggers, révélation du H1 par caractères, section épinglée à 77–85 transforms, rideau rivière, arches en clip-path ; aucune règle reduced-motion, easing GSAP non vérifiable, trois libs de carrousel.
- **UX : 6,5/10** — one-page à ancres claire, CTA persistant sur les deux supports, tableau de distribution ; liens `href="#"`, PDF externe, menu mobile non ouvrable par l'outil, focus supprimé.
- **Conversion : 5,5/10** — CTA visible dès 0 px et demande intégrée en page ; mais aucun prix, aucune condition, aucune preuve, iframe en anglais, onglets tarifaires cachés.
- **Mobile : 7/10** — barre « Reservar » 64 px, animations conservées (77–79 transforms), typographie 56/40/22 px lisible ; 69 Mo de transfert et une vidéo de 40 Mo en double encodage.

**Note globale : 7,3/10.** Mas Girbau est la référence de la série pour le **récit par chapitres et le mouvement scrubbé** (section Entorno, matières, arches) et pour le CTA mobile ; il est freiné par un moteur de demande sans prix ni localisation et par un poids de page hors norme. À copier : la structure narrative et la mécanique de scroll ; à ne pas reproduire : la chaîne média (vidéo double, JPG 3 Mo) et l'absence de repères tarifaires.

---

## Observations clés à conserver pour la phase comparative

- One-page de 16 843 px desktop / 17 927 px mobile, 13 sections, 932 mots, 6 ancres de nav + galerie séparée ; header 58 px (48 px mobile).
- Libs prouvées : GSAP 3.10.4 + CustomEase + ScrollTrigger (24 triggers), split-type, ukiyo.js, Swiper 8/10, Flickity 2, Dragdealer, Webflow (99 `data-w-id`), 439 nœuds split-text, 8 sticky, 5 parallaxe ; Lenis chargé mais non détecté.
- Pic d'animation : 77 → 85 → 80 → 17 transforms entre 10 249 et 12 527 px (section Entorno épinglée 2 045 px + `sticky-element` 900 px) ; pic identique en mobile (77/79).
- Hero : H1 80 px Editor's Note graisse 300, ligne 2 italique ; révélation par caractères masqués visible en capture 00 ; CTA pilule 129×63 px rayon 100 px `#ff906d`.
- Palette : `#fff8eb` / `#252b15` / `#242c04` / `#121602` / `#e1e7dd` / `#ff906d` / `#fffcf5` ; contraste texte/fond ≈ 13:1, CTA ≈ 6,6:1.
- Échelle type desktop 160/80/64/40/32/24/20,8/16/12 ; mobile 100/56/40/24/22/16/12 ; Inter 12 px capitales pour labels.
- Unité vendue : maison entière (6 chambres, 14 pers., 10 lits, 30 ha) ; tableau de distribution 6 colonnes ; 12 inclusions ; 0 prix, onglets « Temporada » cachés.
- Réservation : iframe BookingMood 656×794 (calendrier 2 mois + 3 champs + « Send booking Request » en anglais), section « Petición de reserva » en bas de page ; CTA mobile fixe 390×64 px ; sonde outil dévoyée vers Facebook.
- Poids : 104,5 Mo / 401 requêtes desktop, 69,0 Mo / 206 requêtes mobile ; vidéo drone MP4 22,3 Mo + WebM 18,2 Mo ; galerie 56,5 Mo (JPG 3,07 / 2,69 / 2,13 Mo, 0 srcset).
- Perf : TTFB 1 128 ms, FCP 2 052 ms, load 8 541 ms desktop ; FCP 1 712 ms, load 3 978 ms mobile ; galerie mobile DCL 11 684 ms.
- A11y : 81 `outline:none`, 57 `tabindex=-1`, 167 `aria-hidden`, 119/121 alt vides, iframe sans title, 1 règle reduced-motion (tiers), 7 vidéos autoplay.
- SEO : 9 H1, hreflang x-default/es/ca/en, pas de canonical, pas de JSON-LD, description EN non traduite ; galerie `title` « Galeria » sans description.
- Motifs de marque : arches SVG (masque 1 360×208), courbes de niveau, monogramme G, pictos 1 px, cercles 290 px, numérotation 01/–06/.
- Photographie : lumière dorée dominante, 3 vidéos portrait de matières 682×900, une seule présence humaine (de dos) sur la home, 0 scène de groupe.
