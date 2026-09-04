# Système de mouvement — sites d'hébergement premium

> Objectif : définir des animations qui créent une émotion, orientent le regard, donnent du rythme et renforcent la marque, sans jamais ralentir la compréhension ni la réservation. Chaque règle indique le niveau (Indispensable / Recommandé / Signature premium), le contexte et le risque évité.

## 0. Ce que le benchmark enseigne (faits observés, 2026-09-04)

| Site | Mouvement observé | Enseignement |
|---|---|---|
| FORESTIS | Hero = image fixe (aucune balise vidéo sur 12 pages malgré video.js chargé) ; une seule animation d'entrée déclarée (`fadeInUp 1s cubic-bezier(.645,.045,.355,1)`) et une transition de 6 s sur le hero (hypothèse : zoom lent) ; 163 transitions de 0,25 s sur les liens (`opacity 0.25s, color 0.25s`) ; carrousels Swiper à flèches fines ; `scroll-snap` et `onepage-scroll` déclarés mais sans effet observé ; panneau de menu fixe de 224 px (9 entrées) ; 0 règle `prefers-reduced-motion` | L'impression de calme vient de l'absence de mouvement et du vide, pas d'effets. La sobriété est une signature à part entière ; elle n'exempte pas de traiter reduced motion. |
| Hotel Corazón | 0 animation au scroll (0 attribut, 0 transform, 0 sticky) ; trois micro-interactions seulement : hover des cartes = `brightness(0.8)` en 0,5 s, soulignement des liens de menu par `::after` de 69 px depuis le centre en 0,3 s, inversion brun/rouge du header au scroll (mécanisme non prouvé) ; règle `prefers-reduced-motion` globale qui ramène toutes les durées à 0,01 ms ; 32 keyframes déclarés (majoritairement Swiper/Vimeo) | Une micro-interaction unique et reconnaissable (assombrissement des cartes) suffit à donner de la réactivité. Le reduced motion global est simple et efficace. |
| Borgo Egnazia | Préloader plein écran (fond gris #888b8d, logo) puis vidéo fixe plein écran sans poster ni playsinline avec lien « SKIP » (102×41) ; `zoominimg 40s ease` (zoom lent Ken Burns, seule animation d'auteur) ; animate.css + WOW (`fadeIn 1s`) ; 0 hover sur les tuiles ; 5 vidéos de tuiles en boucle non muettes (1,1 à 3,95 Mo) ; onglet « BOOK » fixe ouvrant une modale | L'intro vidéo est immersive mais coûteuse (≈ 9 Mo par segment, non lue en headless) et retarde le contenu ; le zoom lent 40 s est une bonne échelle de temps pour un mouvement d'ambiance. Toujours offrir un « passer ». |
| The Seagate | Vidéo hero HTML5 sans poster (≈ 14 Mo desktop + ≈ 10 Mo mobile, les deux chargées sur les deux breakpoints) ; aucune animation de scroll (0 attribut, 0 cubic-bezier) ; 60 transitions à 0,3 s ; hover de liens `#203a4d` → `#333638` à peine perceptible ; navigation plein écran ; 1 règle reduced motion (formulaire) | Une vidéo hero par device est la bonne pratique, mais les poids observés dépassent les cibles ; prévoir compression et poster. |
| Le Collectionist | Vidéo hero courte (≈ 4,3 Mo, hauteur 458 px) ; `img-scale` : image scale 1,01 → 1,1 en 0,35 s ease-out au hover des cartes ; 6 attributs AOS et 8 classes reveal ; transitions 0,8 s ×54 et easing `cubic-bezier(.4,0,.2,1)` (Material) ; indicateur de chargement Nuxt 3 px ; onglets, favoris, encart de réservation sticky sur la page propriété | Sur une plateforme, le mouvement est au service de l'outil (filtres, onglets, favoris) : rapide, discret, sans mise en scène. |

Non vérifiable en headless : lecture effective des vidéos, transitions de page, comportement du curseur sur écran tactile.

## 1. Principes

1. **Une signature, pas un catalogue** (Indispensable). Choisir un mouvement identitaire (ex. révélation d'image par masque, titres qui montent ligne par ligne, fondu croisé de sections, image épinglée pendant que le texte défile) et le répéter. Risque évité : site « démo de bibliothèque », incohérent et lent.
2. **Le contenu d'abord** (Indispensable). Aucun élément essentiel (titre, CTA, prix, moteur) ne doit être invisible plus de 300 ms après son entrée dans le viewport. Les animations d'entrée démarrent avec une opacité initiale ≥ 0 mais le contenu est présent dans le DOM et lisible sans JS.
3. **Durées courtes, easings sortants** (Indispensable). Micro-interactions 150–300 ms ; entrées 400–700 ms ; révélations d'images 700–1 000 ms ; mouvements d'ambiance (zoom lent, dérive) 20–60 s. Easings : `cubic-bezier(0.22, 1, 0.36, 1)` (out-quint) pour les entrées, `cubic-bezier(0.65, 0, 0.35, 1)` (in-out) pour les transitions d'état, `ease` pour les hovers simples.
4. **Amplitudes faibles** (Recommandé). Translation d'entrée 16–32 px desktop, 8–16 px mobile ; scale 1,04–1,08 pour les images ; jamais de rotation décorative ; parallaxe ≤ 10 % de la hauteur de l'élément.
5. **Un seul élément en mouvement permanent par viewport** (Recommandé) : vidéo OU zoom lent OU marquee, jamais deux.
6. **Le scroll reste natif** (Indispensable). Pas de scroll hijacking, pas de smooth scroll forcé qui change l'inertie sur mobile ; le scroll-snap uniquement sur des galeries horizontales, jamais sur la page entière.
7. **Reduced motion** (Indispensable). Voir §6.
8. **Le mouvement dit quelque chose du lieu** (Signature premium). Montagne : lenteur, verticalité (titres qui montent, images qui se dévoilent du bas). Mer : dérive horizontale lente, fondu doux. Ville / club : transitions nettes, plus rapides. Wellness : fondus longs, respirations. Villa / famille : réactivité simple, peu de mise en scène.

## 2. Inventaire des animations autorisées

| Animation | Niveau | Déclencheur | Valeurs | Fonction | Contexte / établissement | Risque à éviter |
|---|---|---|---|---|---|---|
| Fondu + translation des titres | Indispensable | entrée viewport (seuil 15 %) | 500–700 ms, out-quint, 24 px → 0 | rythme, orienter le regard | tous | déclenchement trop bas (contenu invisible au fold) ; répéter à chaque passage (jouer une seule fois) |
| Révélation d'image par masque (clip-path ou surcouche) | Signature premium | entrée viewport | 800–1 000 ms, out-quint | émotion, marque | boutique, 5 étoiles, montagne, wellness | masquer les images LCP (le hero n'est jamais masqué) |
| Scale 1,06 → 1 sur image | Recommandé | entrée viewport | 900 ms, out-quint | émotion | tous | jank sur mobile bas de gamme : limiter à 2 images animées simultanément |
| Zoom lent d'ambiance (Ken Burns) | Recommandé | continu | 30–60 s, linear ou ease-in-out, scale 1 → 1,08 | émotion, vie | hero photo sans vidéo ; tuiles plein écran | oublier `will-change`/GPU ; combiner avec vidéo |
| Vidéo hero autoplay | Recommandé | chargement | muted, loop, playsinline, poster ; ≤ 6 Mo desktop (10–15 s), ≤ 3 Mo mobile ou image | émotion, preuve | 5 étoiles, resort, montagne, collection | pas de poster ; son ; pas de bouton pause ; vidéo unique pour tous les devices |
| Header qui se réduit ou change de fond au scroll | Indispensable | scroll > 80 px | 250–300 ms | orienter, action | tous | saut de mise en page (réserver la hauteur) |
| Barre de navigation qui réapparaît au scroll vers le haut | Recommandé | direction du scroll | 250 ms | action | sites longs, contenus immersifs | l'afficher sur chaque micro-mouvement (seuil 8–12 px) |
| Hover bouton : fond / couleur / soulignement | Indispensable | hover / focus | 200–250 ms | feedback | tous (desktop) | hover uniquement sur la couleur du texte à faible contraste ; oublier l'état focus |
| Hover carte : image scale 1,04 ou brightness 0,85, titre souligné | Recommandé | hover | 400–600 ms | feedback, orienter | listes d'hébergements, expériences | déplacer la carte (layout shift) ; effets qui cachent le texte |
| Carrousel / galerie | Indispensable | clic, drag, clavier, swipe | 400–600 ms, in-out | explorer | pages hébergement, expériences | autoplay sur galerie d'hébergement ; sans flèches ni compteur ; sans swipe mobile |
| Menu plein écran ou panneau | Indispensable | clic burger | 300–450 ms, out-quint ; items en cascade 40 ms | navigation | tous | animation > 500 ms ; pas de fermeture par Escape ; scroll de page non bloqué |
| Sticky de contenu (image fixe, texte qui défile) | Signature premium | scroll | position sticky, 1,5 à 2,5 hauteurs de viewport | expliquer, rythme | manifeste, expériences, wellness | sections trop longues (> 3 vh) ; sur mobile, préférer empiler |
| Scroll horizontal de galerie | Recommandé | scroll / drag | natif avec scroll-snap | explorer | expériences, destinations, collections | détourner la molette ; sans indicateur de progression |
| Compteur / chiffres qui montent | Recommandé | entrée viewport | 800–1 200 ms | preuve | resort, 5 étoiles, collection (nb de maisons) | chiffres non vérifiables |
| Préloader | Optionnel (Signature premium si court) | chargement initial | ≤ 800 ms, une seule fois par session | marque | 5 étoiles, resort, insolite | > 1,5 s ; à chaque page ; sans état de progression ; bloquer si les assets sont déjà en cache |
| Transitions de page (fondu, rideau) | Signature premium | navigation | 300–500 ms | continuité | sites à forte identité, SPA | casser le bouton retour, le focus, le scroll ; > 600 ms |
| Curseur personnalisé | Optionnel | mouvement souris | 100–150 ms de suivi | marque | galeries (« glisser »), sites d'art de vivre | remplacer le curseur partout ; masquer le curseur natif sur les formulaires ; oublier qu'il n'existe pas sur mobile |
| Feedback formulaire / moteur | Indispensable | soumission, erreur | 150–250 ms | rassurer | tous | erreurs sans message ; spinner sans texte ; succès sans confirmation |

## 3. Trois niveaux d'intensité

| Niveau | Pour qui | Ce qui est inclus | Ce qui est exclu |
|---|---|---|---|
| **Sobre** | villa unique, maison d'hôtes, insolite à petit budget, sites gérés en interne | fondus d'entrée, hovers, header au scroll, galerie | vidéo hero, sticky, préloader, transitions de page, curseur |
| **Mesuré** (défaut) | boutique-hôtel, chalet, wellness, collection | sobre + révélation d'images signature, vidéo hero (avec fallback), zoom lent, barre qui réapparaît, un sticky sur la home | préloader, curseur, transitions de page |
| **Signature** | 5 étoiles, resort, lieux d'expérience à forte marque | mesuré + un effet identitaire (sticky narratif, transitions de page, préloader court) | plus d'un effet identitaire ; scroll hijack |

## 4. Tokens de mouvement (à copier dans les design tokens)

```
--motion-fast: 150ms;      /* feedback, focus */
--motion-base: 250ms;      /* hover, header */
--motion-enter: 600ms;     /* titres, blocs */
--motion-reveal: 900ms;    /* images */
--motion-ambient: 40s;     /* zoom lent */
--ease-out: cubic-bezier(0.22, 1, 0.36, 1);
--ease-in-out: cubic-bezier(0.65, 0, 0.35, 1);
--ease-standard: ease;
--offset-enter: 24px;      /* 12px sur mobile */
--stagger: 60ms;           /* cascade de cartes, max 6 éléments */
```

## 5. Adaptations mobiles

- Réduire les translations de moitié, supprimer les parallaxes et les sticky narratifs (empiler), garder les fondus.
- Aucune animation dépendante du hover : prévoir un état actif au toucher (`:active`, 100 ms).
- Vidéo hero : version verticale dédiée ≤ 3 Mo ou image ; jamais d'autoplay si `Save-Data` ou connexion lente (hypothèse d'implémentation : `navigator.connection.saveData`).
- Menu : panneau plein écran, items en cascade limitée à 6, fermeture par tap hors zone et par bouton.
- Animer uniquement `transform` et `opacity` ; pas de `filter` animé sur les listes longues.

## 6. Mode reduced motion

Indispensable. Sous `@media (prefers-reduced-motion: reduce)` :
- Entrées : remplacer translation/scale par une opacité simple (0 → 1 en 200 ms) ou aucune animation.
- Vidéos autoplay : ne pas lancer, afficher le poster, proposer un bouton lecture.
- Zoom lent, parallaxe, marquee, préloader animé, transitions de page : désactivés.
- Carrousels : pas d'autoplay ; transitions instantanées ou 150 ms.
- Conserver les feedbacks de focus et d'erreur (ils sont fonctionnels).
Exemple minimal observé chez Hotel Corazón (règle globale qui ramène `animation-duration` et `transition-duration` à 0,01 ms) : acceptable comme filet de sécurité, mais préférer des règles ciblées pour garder les feedbacks utiles.

## 7. Erreurs qui rendent un site bas de gamme

- Animations d'entrée sur chaque paragraphe, avec délais cumulés qui font attendre.
- Effets « bounce », « elastic », rotations, particules, texte qui clignote.
- Préloader long sur chaque page ; compteur de pourcentage.
- Scroll hijacking, sections à défilement horizontal forcé sur toute la page.
- Vidéo hero lourde sans poster qui laisse un écran vide (observé en headless chez The Seagate : hero crème avec titre blanc illisible tant que la vidéo n'est pas rendue ; Borgo et Le Collectionist n'ont pas de poster non plus) : toujours prévoir un poster ou un fond contrasté.
- Hover qui déplace la mise en page ; cartes qui « sautent ».
- Animations qui ne jouent pas sur mobile mais laissent le contenu invisible (opacité 0 sans fallback).

## 8. Comment spécifier une animation (format à réutiliser)

`Élément | Déclencheur | Propriétés animées | De → À | Durée | Délai | Easing | Une fois / à chaque fois | Mobile | Reduced motion | Fonction | Risque`
