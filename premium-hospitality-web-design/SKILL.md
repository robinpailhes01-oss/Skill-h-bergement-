---
name: premium-hospitality-web-design
description: Concevoir des sites d'hébergement premium (hôtels indépendants, boutique-hôtels, 5 étoiles, chalets, villas, hébergements insolites, resorts wellness, domaines, maisons d'hôtes, conciergeries et collections) qui produisent une impression haut de gamme, immersive et mémorable ET qui convertissent en réservations directes ou demandes qualifiées. Utiliser dès qu'un projet concerne un site d'hôtel, de location de vacances, de spa/resort, de refuge ou de conciergerie d'hébergement : création, refonte, audit, brief créatif, page chambre, parcours de réservation, direction artistique, animations, contenus photo/vidéo, copywriting hôtelier. Fondé sur l'audit approfondi (2026-09) de FORESTIS, Hotel Corazón, Borgo Egnazia, The Seagate et Le Collectionist.
---

# Premium Hospitality Web Design

Compétence de conception de sites d'hébergement haut de gamme. Elle transforme une marque, un lieu et une offre en un site qui fait ressentir l'expérience avant l'arrivée, puis conduit sans friction à la réservation ou à la demande.

Ce fichier est le mode d'emploi. Les connaissances détaillées sont dans `references/` et les documents de travail dans `templates/`. Ne pas charger toutes les références d'un coup : lire celles que l'étape en cours demande (tableau en fin de fichier).

## 1. Quand utiliser cette compétence

- Créer ou refondre le site d'un hôtel indépendant, boutique-hôtel, hôtel 5 étoiles, chalet ou hôtel de montagne, villa ou maison de vacances, hébergement insolite (cabane, dôme, lodge, bateau), resort ou retraite wellness, domaine, maison d'hôtes, lieu d'expérience, conciergerie ou collection d'hébergements.
- Concevoir une page précise de ce type de site : accueil, hébergement, expériences, table, spa, histoire, contact, parcours de réservation.
- Auditer un site existant, produire un brief créatif, une direction artistique, un système de mouvement, une shot list photo/vidéo, un cahier des charges designer/développeur.
- Ne pas utiliser pour : sites de chaînes purement transactionnels sans marque propre, comparateurs, sites non liés à l'hébergement (pour ces cas, préférer une compétence de design web générale).

## 2. Posture et règles non négociables

1. **Vendre une expérience, pas une chambre.** Chaque page raconte ce que l'on vit ; les faits (m², lits, équipements) viennent ensuite, groupés et complets.
2. **Chaque décision est justifiée** : ce qu'il faut faire, pourquoi, dans quel contexte, pour quel type d'établissement, quel résultat, quel risque évité. Jamais de « beau », « élégant », « premium » sans explication.
3. **Le mobile n'est pas une adaptation, c'est le cas principal** (souvent plus de 60 % du trafic hospitality). Toute recommandation précise le comportement mobile.
4. **Le mouvement sert, il ne décore pas.** Une signature de mouvement par site, des durées courtes, `prefers-reduced-motion` respecté, jamais de blocage de la lecture.
5. **La conversion est une conséquence de la clarté** : promesse en 5 secondes, hébergement en 3 clics, moteur en 1 clic, prix ou moyen d'obtenir un prix toujours visible, réassurance près du CTA.
6. **Ne jamais copier une identité existante.** Les sites de référence servent à comprendre des mécanismes, pas à reproduire des palettes, polices, mises en page ou textes.
7. **Pas de luxe froid par défaut.** Chercher la chaleur (personnes, matières, lumière, rituels) plutôt que le vide corporate, sauf si la marque le demande explicitement.
8. **Séparer faits, interprétation et recommandation** dans les audits ; utiliser « hypothèse » quand ce n'est pas prouvé.

## 3. Informations à obtenir du client avant de concevoir

Utiliser `templates/client-discovery.md`. Bloquants : type d'établissement, localisation et accès, liste des hébergements avec capacité et prix, saisonnalité, cibles, promesse, moteur de réservation ou mode de demande, politique d'annulation, contenus photo/vidéo disponibles, objectif n°1 et KPI, langues.

Si ces informations manquent et que l'utilisateur veut avancer : produire le travail sous hypothèses explicites, listées en tête du livrable, et indiquer ce qui changerait si l'hypothèse tombait.

## 4. Processus (20 livrables)

Quand la compétence sert à créer un site, elle produit dans cet ordre. Chaque livrable peut être rendu séparément si l'utilisateur ne demande qu'une étape.

| # | Livrable | Comment faire | Référence à lire |
|---|---|---|---|
| 1 | Résumé stratégique | 10 lignes : établissement, problème, objectif, mode de conversion (transactionnel / conversationnel / hybride), contraintes | `brand-strategy.md` §1 |
| 2 | Analyse de la cible | 2 à 3 personas avec intention, freins, preuve attendue, page d'entrée probable | `brand-strategy.md` §2 |
| 3 | Promesse et positionnement | Positionnement en une phrase, promesse côté client, preuves vérifiables, territoire émotionnel, personnalité (adjectifs / anti-adjectifs) | `brand-strategy.md` §3–5 |
| 4 | Trois directions créatives | Trois concepts réellement différents (idée, sensation, mise en page, palette, typo, photo, mouvement, risque) | `brand-strategy.md` §6, `visual-design-system.md` |
| 5 | Recommandation | Choix argumenté selon cible, contenus disponibles, faisabilité ; ce que l'on garde des autres | `brand-strategy.md` §6 |
| 6 | Sitemap | Selon le blueprint du modèle ; une page = un objectif | `homepage-blueprints.md`, `templates/sitemap-template.md` |
| 7 | Parcours utilisateur | Parcours A (réservation), B (demande), C (inspiration), D (retour) avec points de contrôle | `ux-booking-conversion.md` §1–2 |
| 8 | Structure de chaque page | Tableau section par section : objectif, contenu, interaction, CTA, émotion, desktop, mobile | `homepage-blueprints.md`, `accommodation-pages.md`, `templates/homepage-specification.md`, `templates/room-page-specification.md` |
| 9 | Copywriting | Titres, accroches, descriptions, CTA, microcopies, FAQ ; mécanismes sensoriels, longueurs | `copywriting-hospitality.md` |
| 10 | Direction artistique | Palette, typographie, grille, formes, iconographie, traitement photo, place du vide | `visual-design-system.md` §1–7 |
| 11 | Design tokens | Couleurs, échelle typographique, espacements, rayons, ombres, durées, easings sous forme de tableau ou de variables CSS | `visual-design-system.md` §8, `motion-guidelines.md` §4 |
| 12 | Bibliothèque de composants | Header, navigation, hero, moteur, carte hébergement, galerie, expérience, destination, témoignages, récompenses, services, conciergerie, FAQ, contact, footer, CTA sticky, bandeau d'offre, newsletter | `visual-design-system.md` §9 |
| 13 | Spécifications d'animation | Signature de mouvement, entrées, scroll, révélations, hover, transitions, durées, easings, limites, mobile, reduced motion | `motion-guidelines.md` |
| 14 | Comportement responsive | Breakpoints, hero mobile, menu, barre CTA basse, galeries, tailles de texte et de cibles | `mobile-accessibility-performance.md` §1 |
| 15 | Réservation et conversion | Emplacement des CTA, formulations, moteur, réassurance, bénéfices directs, rupture moteur externe, formulaires | `ux-booking-conversion.md` |
| 16 | Besoins photo et vidéo | Shot list par page, ratios, lumière, présence humaine, vidéos (hero 16:9 + 9:16), poids cibles | `photography-video.md` |
| 17 | Recommandations SEO | Titles, descriptions, H1, données structurées, pages destination, hreflang, contenu indexable | `mobile-accessibility-performance.md` §3 |
| 18 | Contrôle accessibilité et performance | Contrastes, clavier, alt, formulaires, reduced motion, LCP/CLS/INP, poids, tiers | `mobile-accessibility-performance.md` §2, §4 |
| 19 | Cahier des charges designer / développeur | Compilation des livrables 6 à 18 en spécifications vérifiables + critères d'acceptation | `templates/homepage-specification.md`, `templates/room-page-specification.md` |
| 20 | Checklist finale | Audit avant publication avec notes justifiées | `templates/final-website-audit.md`, `quality-checklists.md` |

## 5. Comment identifier le modèle d'hébergement

Poser trois questions : (a) vend-on des nuits dans un lieu unique ou des séjours dans plusieurs maisons ? (b) le client achète-t-il en ligne (dates + paiement) ou demande-t-il (devis, conciergerie) ? (c) l'expérience est-elle portée par le lieu (architecture, nature), par les services (spa, table, club) ou par les personnes (hôtes, chef, guide) ?

| Modèle | Signal | Mode de conversion dominant | Blueprint |
|---|---|---|---|
| Boutique-hôtel | 8 à 40 chambres, forte personnalité, hôtes identifiables | transactionnel + humain | `homepage-blueprints.md` §A |
| Hôtel 5 étoiles / palace | services multiples, équipes, marques partenaires, événements | transactionnel (moteur robuste), offres | §B |
| Chalet / montagne | saison, vue, ski, feu, altitude, locations à la semaine | hybride (dates + demande) | §C |
| Villa / maison de vacances | une ou quelques maisons, capacité familiale, semaine | conversationnel ou hybride | §D |
| Hébergement insolite | lieu atypique, nuits courtes, forte curiosité, contraintes d'accès | transactionnel simple + réassurance pratique | §E |
| Resort / retraite wellness | programmes, durée, praticiens, transformation | hybride (programmes + dates) | §F |
| Collection / conciergerie | dizaines de maisons, destinations, recherche, favoris, conseillers | recherche + demande (conversationnel assisté) | §G |
| Domaine / maison d'hôtes / lieu d'expérience | peu de chambres, événements, table, ateliers | conversationnel + événements | §A adapté (voir notes §H) |

## 6. Comment analyser la marque et construire le positionnement

1. Extraire l'histoire fondatrice, le lieu, les personnes et les rituels (découverte client).
2. Formuler la promesse côté client (« ici, vous … »), puis lister les preuves vérifiables.
3. Définir le territoire émotionnel dans l'ordre du parcours (ex. calme → curiosité → appartenance).
4. Définir la personnalité en 4 adjectifs et 4 anti-adjectifs ; en déduire ton, palette, typographie, mouvement.
5. Vérifier la cohérence offre / mots / images / interactions : un mot du positionnement doit être visible dans le hero, dans les photos, dans une interaction.
Détail : `references/brand-strategy.md`.

## 7. Comment proposer trois concepts et en choisir un

Les trois directions doivent différer sur au moins trois axes (structure de page, palette, typographie, traitement photo, niveau de mouvement, ton). Évaluer chaque direction sur : justesse par rapport à la cible, fidélité à la promesse, faisabilité avec les contenus disponibles, potentiel de conversion, distinctivité dans le marché local. Recommander une direction et expliquer ce qui est conservé des deux autres. Ne pas proposer trois variations d'une même idée.

## 8. Comment construire la page d'accueil

Ordre narratif de référence (à adapter par blueprint) : promesse (hero) → pourquoi ce lieu (manifeste court) → offre concrète (hébergements) → preuve de l'expérience (expériences, table, spa) → preuve sociale et distinctions → destination et accès → offres et bénéfices directs → contact humain → newsletter → footer. Le moteur ou le CTA principal est accessible dès le hero et reste persistant. Chaque section a un objectif unique, une interaction et une émotion cible. Utiliser `templates/homepage-specification.md`.

## 9. Comment concevoir les pages hébergements

Une page par type, nom propre, promesse, galerie d'au moins huit images ordonnées, description sensorielle courte, faits groupés, services, tarifs ou moyen d'obtenir un prix, conditions, CTA persistant (barre basse mobile), hébergements complémentaires et expériences liées. Détail : `references/accommodation-pages.md` et `templates/room-page-specification.md`.

## 10. Comment rédiger, définir la direction artistique et les animations

- Textes : voix de la maison, phrases courtes, vocabulaire concret et sensoriel, promesse avant caractéristiques, CTA en verbes distincts (Découvrir / Demander / Réserver). `references/copywriting-hospitality.md`.
- Direction artistique : palette de 5 à 7 couleurs dont une seule d'accent, deux familles typographiques maximum, échelle de titres modérée, grille à largeur maximale définie, vide généreux, photos traitées de manière homogène. `references/visual-design-system.md`.
- Animations : choisir une signature (révélation d'images, titres qui montent, fondu de sections, sticky de contenu) et s'y tenir ; durées de 200 à 900 ms ; easings « out » ; version mobile allégée ; reduced motion. `references/motion-guidelines.md`.

## 11. Comment optimiser la réservation

Définir le mode de conversion, placer le CTA principal dans le hero et dans le header persistant, pré-remplir le moteur depuis la page hébergement, afficher les bénéfices directs et la politique d'annulation à côté du CTA, prévoir le contact humain (téléphone, WhatsApp, délai de réponse), traiter la rupture visuelle avec le moteur externe. `references/ux-booking-conversion.md`.

## 12. Comment vérifier mobile, SEO, performance et accessibilité

Passer `references/quality-checklists.md` puis `templates/final-website-audit.md` : breakpoints, hero mobile, barre CTA basse, tailles de texte et de cibles, LCP < 2,5 s, CLS < 0,1, vidéo hero ≤ 6 Mo avec version mobile, contrastes AA, clavier, alt, formulaires, reduced motion, H1 unique, données structurées, hreflang.

## 13. Fichiers de référence selon la mission

| Mission | Lire d'abord | Puis |
|---|---|---|
| Nouveau site complet | ce fichier, `brand-strategy.md`, `homepage-blueprints.md` | tout le reste dans l'ordre des livrables |
| Refonte / audit | `quality-checklists.md`, `benchmark-sites.md` | `ux-booking-conversion.md`, `mobile-accessibility-performance.md` |
| Brief créatif ou direction artistique | `brand-strategy.md`, `visual-design-system.md` | `photography-video.md`, `motion-guidelines.md` |
| Page d'accueil | `homepage-blueprints.md` | `copywriting-hospitality.md`, `motion-guidelines.md` |
| Page hébergement | `accommodation-pages.md` | `ux-booking-conversion.md`, `photography-video.md` |
| Parcours de réservation | `ux-booking-conversion.md` | `mobile-accessibility-performance.md` |
| Textes | `copywriting-hospitality.md` | `brand-strategy.md` |
| Animations | `motion-guidelines.md` | `mobile-accessibility-performance.md` |
| Contenus photo/vidéo | `photography-video.md` | `visual-design-system.md` |
| Comprendre ce que font les meilleurs | `benchmark-sites.md` | — |

## 14. Format des livrables

- Français par défaut (ou la langue de l'utilisateur), Markdown structuré, tableaux pour les structures de page et les tokens, listes pour les règles.
- Toujours indiquer le type d'établissement visé et le comportement mobile.
- Pour les audits : date, URL, faits observés / interprétation / recommandation, mention « hypothèse » quand nécessaire, notes justifiées.
- Ne pas produire de code sauf demande ; si du code est demandé, respecter les tokens et les règles de mouvement définies ici.
