# Template — Spécification d'une page hébergement (chambre, suite, villa, chalet, cabane)

> Une page par type d'hébergement. La page doit permettre de se projeter (émotion), de vérifier (faits), et d'agir (réserver ou demander) sans quitter la page. Voir `references/accommodation-pages.md`.

## 0. Identité

| Champ | Valeur |
|---|---|
| Nom de l'hébergement (nom propre, pas « Chambre Standard ») | |
| Type / catégorie | |
| Promesse en une phrase (ce que l'on y vit) | |
| Surface, capacité, lits, étage, vue, extérieur | |
| Prix indicatif (« à partir de », par nuit/semaine, saison) | |
| Disponibilité / saisons | |
| URL | |

## 1. Ordre des sections

| # | Section | Contenu | Interaction | CTA | Desktop | Mobile |
|---|---|---|---|---|---|---|
| 1 | Hero | image ou vidéo signature de cet hébergement + nom + promesse + capacité/surface/prix | | Réserver / Demander (sticky) | | |
| 2 | Galerie | 8 à 15 images : vue d'ensemble, lit, salle de bain, détail matière, vue extérieure, moment de vie ; légendes | lightbox / défilement | | | |
| 3 | Description | 60 à 150 mots : atmosphère, lumière, matériaux, ce qui se passe le matin / le soir | | | | |
| 4 | Faits | surface, occupants, lits, vue, équipements groupés (confort / salle de bain / technologie / extérieur) | accordéons sur mobile | | | |
| 5 | Services inclus & sur demande | petit-déjeuner, ménage, conciergerie, chef, transferts | | | | |
| 6 | Tarifs & disponibilités | calendrier ou tableau saisonnier ; conditions (acompte, annulation, caution) | moteur pré-rempli | Réserver | | |
| 7 | Plan (villa/chalet) | plan des niveaux, orientation, distances | | | | |
| 8 | Réassurance | avis liés à cet hébergement, garanties, contact humain | | Contacter | | |
| 9 | Hébergements complémentaires | 2 à 3 types voisins (plus grand, plus intime, autre vue) | | Découvrir | | |
| 10 | Expériences liées | 2 à 3 expériences ou services proches | | | | |

## 2. Textes

| Zone | Texte | Mots | Statut |
|---|---|---|---|
| Nom | | | |
| Promesse | | ≤ 15 | |
| Description | | 60–150 | |
| Légendes galerie | | ≤ 12 chacune | |
| Liste équipements (groupée) | | | |
| Conditions | | | |
| CTA principal / secondaire | | | |

## 3. Médias

| Image | Sujet | Ratio | Ordre | Alt | Statut |
|---|---|---|---|---|---|
| 1 | Vue d'ensemble depuis l'entrée | 3:2 | hero | | |
| 2 | Lit, lumière du matin | 3:2 | | | |
| 3 | Salle de bain | 4:5 | | | |
| 4 | Détail matière / objet | 1:1 | | | |
| 5 | Vue depuis la fenêtre / terrasse | 16:9 | | | |
| 6 | Moment de vie (personne, geste) | 4:5 | | | |
| 7 | Extérieur / accès | 3:2 | | | |

## 4. Données structurées et SEO

- Title : « <Nom> — <type> <vue> | <Établissement> » ; H1 = nom ; description unique.
- Schema : `HotelRoom` / `Accommodation` (occupancy, floorSize, amenityFeature), `Offer` (priceRange).
- Liens internes : liste des hébergements, hébergements complémentaires, expériences.

## 5. Comportement mobile

- Barre d'action fixe en bas : prix « à partir de » + bouton Réserver/Demander (hauteur 56–64 px).
- Galerie en défilement horizontal avec compteur ; description repliable après 3 lignes ; équipements en accordéons ; calendrier plein écran.

## 6. Critères d'acceptation

- Prix ou moyen d'obtenir un prix visible sans scroll (desktop) et dans la barre fixe (mobile).
- Aucune information indispensable uniquement dans le moteur externe.
- Galerie accessible au clavier ; alt descriptifs ; LCP < 2,5 s ; pas de décalage de mise en page au chargement des images (dimensions réservées).
