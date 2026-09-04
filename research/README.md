# Recherche — Sites d'hébergement et de voyage premium (2026-09-04)

Ce dossier contient la recherche qui a servi à construire la compétence `premium-hospitality-web-design/`. Les phases 1 à 5 sont conservées ici en intégralité ; la phase 6 est la compétence elle-même.

| Phase | Contenu | Emplacement |
|---|---|---|
| 1 — Audits individuels | Quinze fiches complètes (14 rubriques, faits / interprétation / enseignements, notes justifiées). Série 1 : FORESTIS, Hotel Corazón, Borgo Egnazia, The Seagate, Le Collectionist. Série 2 (diversification au-delà du quiet luxury) : Hotel Odisej, Mas Girbau, Our Habitas, Aethos, White Desert, Explora Journeys, Experimental Group, Soneva, Vipp Guesthouses, Pelorus Travel | `phase-1-audits/` |
| 2 — Analyse comparative | Matrice sur 16 critères (5 puis 15 sites), meilleur site par domaine, constats transversaux | `phase-2-comparative.md` (parties 1 et 2) |
| 3 — Principes de haute qualité | 30 principes, erreurs bas de gamme, éléments indispensables par page, règles (menu, copy, photo, vidéo, animation, responsive, performance, accessibilité, conversion) classés Indispensable / Recommandé / Signature premium, plus dix principes issus de la série 2 | `phase-3-principles.md` (version opérationnelle : `../premium-hospitality-web-design/references/quality-checklists.md`) |
| 4 — Blueprints | Onze modèles : boutique, 5 étoiles, chalet, villa, insolite, wellness, collection, domaine, groupe / marque-communauté, expédition / sur mesure, croisière / combinatoire, marque non hôtelière | `../premium-hospitality-web-design/references/homepage-blueprints.md` |
| 5 — Design system | Identité visuelle, tokens, système de mouvement, bibliothèque de 18 composants | `../premium-hospitality-web-design/references/visual-design-system.md` et `motion-guidelines.md` |
| 6 — Compétence | SKILL.md + 11 références + 6 templates | `../premium-hospitality-web-design/` |

## Méthode d'observation

- Chromium headless (Playwright) en 1440×900 (desktop) et 390×844 DPR 2 (iPhone), via le proxy de la session.
- Pour chaque page : captures au chargement, après cookies, page entière, viewports successifs, menu ouvert, reduced motion ; extraction des styles calculés (polices, tailles, casse, interlettrage, couleurs, fonds, boutons, rayons), des éléments fixes/sticky, des sections, des médias (vidéos, images, lazy, alt, srcset), des bibliothèques détectées, des transitions/easings/keyframes CSS, des règles `prefers-reduced-motion`, des métriques Performance API et du réseau (requêtes, poids, tiers), de l'accessibilité (focus, landmarks, labels), des métadonnées SEO.
- Scroll par paliers pour observer header, éléments épinglés, transforms et opacités en cours ; sondes de hover (comparaison de styles avant/après) ; flux d'interaction ciblés (menu, recherche, CTA de réservation, modale, moteur) sans aucune validation de formulaire ni réservation.
- Limites : vidéos autoplay non lues en headless, transitions de page non testées, Lighthouse indisponible, moteur Marriott inaccessible aux automates, anti-bot SiteGround sur Borgo Egnazia (pages recapturées en mobile via contexte partagé).

## Sites et URL de départ (série 2)

6. Hotel Odisej — https://hotelodisej.com/
7. Mas Girbau — https://www.masgirbau.com/
8. Our Habitas — https://www.ourhabitas.com/
9. Aethos Hotels — https://www.aethos.com/
10. White Desert — https://white-desert.com/
11. Explora Journeys — https://explorajourneys.com/us/en
12. Experimental Group — https://www.experimentalgroup.com/
13. Soneva — https://soneva.com/
14. Vipp Guesthouses — https://vipp.com/en/world-of-vipp/our-guesthouses
15. Pelorus Travel — https://pelorustravel.com/

Limites propres à la série 2 : lecteurs Vimeo bloqués ou en erreur en headless (Habitas, Aethos) ; captures pleine page inutilisables sur les sites à scroll lissé (Aethos) et à scroll horizontal (White Desert), remplacées par des balayages de viewports (`*-sweep-*.png`) ; moteur Soneva non atteint ; interstitiel anti-bot sur le moteur d'Odisej.

## Sites et URL de départ (série 1)

1. FORESTIS Dolomites — https://www.forestis.it/en/
2. Hotel Corazón — https://www.hotelcorazon.com/
3. Borgo Egnazia — https://www.borgoegnazia.com/
4. The Seagate — https://www.seagatedelray.com/
5. Le Collectionist — https://www.lecollectionist.com/fr/
