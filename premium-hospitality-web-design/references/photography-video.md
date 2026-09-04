# Photographie et vidéo — sites d'hébergement premium

> La photographie est le premier signal de gamme : avant le texte, avant l'animation. Ce document fixe les règles de cadrage, de lumière, de contenu, la proportion lieu / expérience, le rôle de la vidéo et la shot list nécessaire pour un nouveau projet. Niveaux : Indispensable / Recommandé / Signature premium.

## 0. Ce que montre le benchmark (2026-09-04)

| Site | Types de plans dominants | Lumière / couleurs | Présence humaine | Proportion lieu / expérience | Vidéo |
|---|---|---|---|---|---|
| FORESTIS | Paysage large (Dolomites à l'heure dorée), vue aérienne des toits dans la forêt, textures (bois coupé, écorce), intérieurs sombres avec une lampe, détails de rituels (main tenant des éléments naturels, silhouette entrant dans le sauna), nature morte de branches | Tons chauds sur fond crème ; contrastes forts (noir/or) ; peu de saturation | Rare, en silhouette ou fragment (main, dos), jamais de visage | ≈ 50 / 50 : le lieu est l'expérience | Aucune sur la home ; vidéo hypothétique ailleurs (video.js chargé) |
| Hotel Corazón | Intérieurs de chambres cadrés frontalement, fenêtre ouverte sur la montagne, lumière naturelle diffuse, mobilier et textiles colorés ; images en 3:2 (≈ 500×330) sous un voile rouge | Chaud, saturé, ambiance « film argentique » ; le fond rouge unifie tout | Absente sur la home et la page chambre observées | ≈ 80 / 20 (lieu dominant) mais le texte porte l'expérience | Vimeo hero (non lue en headless) |
| Borgo Egnazia | Vidéo d'ouverture ; tuiles plein écran (bougainvillier, ruelles blanches de nuit, artisanat/dentelle) avec zoom lent | Nuit et crépuscule, pierres blanches, végétation ; scrim sombre 60 % | Mains d'artisan ; foule de fête (photo « festa in piazza ») | expérience et atmosphère avant les chambres | mp4 plein écran 2024, ≈ 9 Mo/segment, sans loop, « SKIP » |
| The Seagate | Coquillages en nature morte comme icônes de catégories ; chambres lumineuses (tête de lit à motifs bleus, lampes allumées) ; plats en gros plan ; scène de mariage sur la plage ; femme en peignoir face à la mer ; surfeurs au coucher du soleil | Crème, bleu, sable ; lumière de jour ; saturation modérée | Présente dans les expériences (mariage, spa, plage) | ≈ 60 / 40 | Hero vidéo desktop + mobile (≈ 14 / 10 Mo) + 2 vidéos secondaires |
| Le Collectionist | Chalets en extérieur (neige, bois), salles à manger avec vue, villa vue aérienne avec piscine, mosaïque de 9 à 12 photos par propriété ; portraits de conseillers ; images d'inspiration verticales (cavalier dans le désert, ski, voile) | Jour, saturation naturelle, cohérence limitée (multiples photographes) | Dans l'inspiration et les conseillers ; peu dans les villas | ≈ 70 / 30 | Vidéo hero courte 4,3 Mo |

### Série 2

| Site | Types de plans dominants | Lumière / couleurs | Présence humaine | Vidéo |
|---|---|---|---|---|
| Hotel Odisej | aérien de la baie, forêt, intérieurs balcon, coins arrondis ; photos d'un autre hôtel du groupe réutilisées (à éviter) | jour, palette accordée aux fonds olive/bleu | ≈ 3 images | aucune |
| Mas Girbau | drone à l'heure dorée, matières en vidéos portrait (682×900), tables dressées dehors, salles voûtées | dorée dominante, crème/vert | 1 personne de dos ; 0 groupe | hero MP4 22 Mo + WebM 18 Mo ; 7 vidéos |
| Our Habitas | groupes autour du feu, tablées, rituels, drone, rendus 3D des projets | golden hour, chaud | ≈ 60 % des images | Vimeo hero sans poster (bloqué en headless) |
| Aethos | drone (3 Mo), gens en action (vélo, yacht), t-shirt manifeste, arche clip-path | papier, contrastes doux | fréquente, jeune, en mouvement | Vimeo hero sans poster |
| White Desert | glace, camps de nuit, dôme, intérieurs de pod, cartes, coordonnées en overlay | bleu / blanc / orange d'action | guides, invités en tenue polaire | Cloudflare Stream 4–8 Mo, aussi en mobile ; vidéo inline camp 5,3 Mo |
| Explora Journeys | navires, suites par catégorie, ports, plats | sable / navy | modérée | 4 vidéos home (4–15 Mo), suites 82 + 31 Mo |
| Experimental Group | intérieurs colorés, bars, plages, vidéos par lieu | variée, couleur par niveau | forte (bars, plages) | webm + mp4 chargés ensemble, poster vide |
| Soneva | instants (enfants en contre-jour, sous-marin), villas, hôtes nommés, posters 245–688 Ko | linen / blue hour / golden ember | forte et nommée | Gumlet HLS 1600×900 ×4 |
| Vipp Guesthouses | architecture à l'heure bleue, cuisines, coordonnées GPS, archives 1939 | sombre / sable | 0 sur la liste et Tunnel (hors architecte) ; 4 scènes sur Farmhouse | 10–13 vidéos `preload="auto"` par page (200 Mo) |
| Pelorus Travel | paysages extrêmes, yachts, enfants (campagne), employés en vidéo | saturation naturelle | forte dans les campagnes | 21–61 Mo par page, servies en mobile |

Enseignements série 2 : les scènes de communauté (Habitas, Aethos, Soneva) et les personnes nommées (Soneva, Pelorus, White Desert) font passer d'un catalogue à une expérience ; le langage cartographique (coordonnées, cartes, heures) est une photographie de la logistique ; le poids vidéo est le défaut universel (65–440 Mo).

Enseignements : (1) le lieu vend, mais la présence humaine crédible (mains, silhouettes, gestes) fait passer de « catalogue » à « expérience » ; (2) un traitement colorimétrique homogène compte plus que la qualité individuelle des images ; (3) les vidéos hero sont systématiquement trop lourdes ; (4) les icônes photographiques (coquillages Seagate, nature morte FORESTIS) remplacent avantageusement des pictogrammes.

## 1. Règles photographiques

| Règle | Niveau | Détail | Contexte | Risque évité |
|---|---|---|---|---|
| Lumière naturelle, heure choisie | Indispensable | matin tôt ou fin d'après-midi ; intérieurs avec lumière de fenêtre + lampes allumées ; jamais de flash frontal ni de HDR | tous | rendu « agence immobilière » |
| Un traitement colorimétrique unique | Indispensable | même température, même contraste, même grain sur toutes les images ; profil défini dans la DA (chaud/crème, froid/bleu, argentique) | tous | patchwork de photographes |
| Trois échelles par sujet | Indispensable | large (contexte), moyen (usage), détail (matière) pour chaque hébergement et chaque espace | tous | pages avec 8 photos identiques |
| Présence humaine crédible | Recommandé (Indispensable en wellness, villa famille, collection) | mains, silhouettes, dos, gestes réels ; visages seulement pour les hôtes/équipe ; pas de mannequins souriants face caméra | boutique, wellness, villa | froideur ou « stock » |
| Cadrages assumés | Recommandé | frontal et symétrique pour l'architecture, plongée pour les tables et les piscines, contre-plongée interdite sur les chambres | tous | déformations grand-angle |
| Détails-signatures | Signature premium | 5 à 10 objets/matières qui n'existent que là (poêle en faïence, tuile, linge, savon, outil) photographiés en nature morte | tous | site interchangeable |
| Destination | Indispensable | 3 à 5 images du territoire (sans le bâtiment) à chaque saison vendue | montagne, mer, campagne | promesse de lieu non prouvée |
| Moments de vie | Recommandé | petit-déjeuner servi, feu allumé, table dressée, peignoir sur le lit, chaussures de ski à la porte | tous | chambres « vides d'histoire » |
| Formats | Indispensable | livrer chaque image clé en 3:2, 4:5 et 1:1 ; hero en 16:9 et 9:16 ; résolution ≥ 2 400 px grand côté | tous | recadrages destructeurs |
| Nettoyage du réel | Recommandé | retirer câbles, panneaux, poubelles ; ne jamais retoucher l'espace (m², vues) | tous | déception à l'arrivée, avis négatifs |

## 2. Proportion lieu / expérience (cible par modèle)

| Modèle | Lieu (architecture, chambres) | Expérience (gestes, personnes, table, activités) | Destination |
|---|---|---|---|
| Boutique-hôtel | 45 % | 40 % | 15 % |
| 5 étoiles | 40 % | 45 % | 15 % |
| Chalet / montagne | 40 % | 30 % | 30 % |
| Villa | 55 % | 25 % | 20 % |
| Insolite | 50 % | 25 % | 25 % |
| Wellness | 30 % | 55 % | 15 % |
| Collection | 55 % (par maison) | 25 % (conciergerie, inspiration) | 20 % |

## 3. Vidéo

| Règle | Niveau | Détail |
|---|---|---|
| Hero : une seule vidéo autoplay | Recommandé | 10–15 s, boucle sans coupure visible, muette, sans texte incrusté, 3 à 5 plans lents (mouvement de caméra ≤ 1 plan fixe/3 s), premières images = plan le plus fort |
| Deux versions | Indispensable si vidéo | 16:9 desktop ≤ 6 Mo (1920×1080, H.264 CRF 23–26 + WebM/AV1) ; 9:16 mobile ≤ 3 Mo ou image ; poster JPG/AVIF de la première image |
| Poster et fond | Indispensable | l'image de secours est aussi belle que la vidéo ; fond de la couleur dominante pour éviter l'écran blanc |
| Contrôles | Indispensable | bouton pause visible ; pas de son ; `playsinline` ; pas d'autoplay en reduced motion / Save-Data |
| Vidéos secondaires | Recommandé | au clic (lightbox) : visite d'une suite (45–90 s), rituel spa, chef, saison ; hébergées sur CDN ou plateforme avec lecteur léger |
| Vidéo d'introduction bloquante | À éviter | si la marque l'impose (Borgo) : ≤ 8 s, « Passer » visible dès la première seconde, une fois par session |
| Contenus verticaux | Recommandé | réutiliser les 9:16 pour les réseaux ; cohérence de traitement |
| Drone | Recommandé (montagne, villa, resort) | 2 à 3 plans max, lents, à l'heure dorée ; jamais tout le hero en drone |
| Budget par page | Indispensable | ≤ 10 Mo de vidéo toutes sources ; une source par device (jamais webm + mp4 chargés ensemble, jamais master + mobile) ; `preload="none"` ou `metadata` ; un seul autoplay ; la série 2 va de 65 à 440 Mo par page : c'est le premier chantier de performance |

## 4. Shot list type pour un nouveau projet

Adapter les quantités au modèle ; les astérisques (*) marquent l'indispensable.

**Marque et lieu**
1. * Façade / arrivée à l'heure dorée (large, 16:9 + 4:5).
2. * Vue depuis le lieu (ce que voit le client) à 2 moments (matin, soir).
3. * 3 à 5 images du territoire sans le bâtiment (par saison vendue).
4. * 5 à 10 détails-signatures en nature morte (fond neutre ou in situ).
5. Portrait des hôtes / équipe (2 : au travail, dans le lieu).
6. Plan aérien (1 à 2) si le site est isolé ou remarquable.

**Par hébergement (8 à 15 images)**
7. * Vue d'ensemble depuis l'entrée (3:2).
8. * Lit avec lumière naturelle (3:2 + 4:5).
9. * Salle de bain (4:5) + détail (robinetterie, savon).
10. * Vue depuis la fenêtre / terrasse (16:9).
11. * Coin de vie (fauteuil, bureau, cheminée) avec un signe d'usage (livre, plateau).
12. Détail matière (mur, textile, bois) (1:1).
13. * Extérieur privé (terrasse, jardin, bain) si existant.
14. Moment de vie : petit-déjeuner en chambre, peignoir, feu.
15. Plan ou vue de nuit (optionnel).

**Expériences et services (par expérience, 3 à 5 images)**
16. * Le geste (mains, préparation) ; * le moment (personne de dos, en action) ; * le résultat (table, soin, sommet) ; le lieu de l'expérience ; le détail (outil, ingrédient).

**Table**
17. * Plat signature en plongée ; salle avec lumière ; chef/produit ; terrasse à l'heure du repas ; petit-déjeuner.

**Spa / wellness**
18. * Bassin ou sauna vide avec lumière ; soin en cours (mains) ; espace repos avec personne de dos ; produits ; extérieur (bain, vue).

**Vidéo**
19. * Hero 16:9 (10–15 s) ; * hero 9:16 ; 1 visite d'hébergement (60 s) ; 1 vidéo d'expérience ; 3 à 5 plans B-roll par saison.

**Preuve**
20. Distinctions (logos vectoriels), presse (logos), photo des avis manuscrits ou du livre d'or (optionnel).

## 5. Livraison et intégration

- Nommage : `etablissement-espace-sujet-format.jpg` ; alt rédigés à la prise de vue.
- Export web : AVIF + WebP + JPG de secours ; 5 largeurs (480, 768, 1200, 1600, 2400) ; qualité 75–82.
- Droits : cession pour web, réseaux, presse, durée ; crédits photographes si demandé.
- Planning : deux sessions (été/hiver ou jour/nuit) plutôt qu'une seule longue.

## 6. Erreurs qui font bas de gamme

Photos de banque ; grand-angle déformant ; HDR ; ciel remplacé ; mannequins qui posent ; chambre avec télévision allumée ; images de tailles et de traitements différents dans une même grille ; vidéo hero avec texte incrusté, musique ou plans trop rapides ; logo animé en intro.
