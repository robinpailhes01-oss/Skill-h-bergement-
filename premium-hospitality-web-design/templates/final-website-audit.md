# Template — Audit final avant publication

> Cocher chaque point ; toute case non cochée doit avoir une justification écrite ou un ticket. Notes /10 justifiées par au moins deux faits. Voir `references/quality-checklists.md` pour la version détaillée.

## Identité du site

| Champ | Valeur |
|---|---|
| Établissement / URL de préproduction | |
| Date de l'audit / auditeur | |
| Navigateurs testés (desktop, iOS Safari, Android Chrome) | |
| Outils utilisés (Lighthouse, axe, lecteur d'écran, throttling 4G) | |

## A. Marque et première impression

- [ ] En 5 secondes sur la home, on comprend : où, quoi, pour qui, pourquoi c'est unique.
- [ ] Le hero porte une promesse (pas un slogan générique) et un CTA lisible.
- [ ] Logo, typographie, couleurs, ton et photos racontent la même chose.
- [ ] Aucun élément « bas de gamme » : photos de banque, bandeau promotionnel agressif, pop-up à l'arrivée, compte à rebours, icônes dépareillées, texte justifié, capitales illisibles.

## B. Architecture et navigation

- [ ] Menu ≤ 7 entrées ; CTA Réserver/Demander accessible depuis toute page.
- [ ] Une chambre atteignable en ≤ 3 clics ; le moteur en 1 clic.
- [ ] Fil d'Ariane sur les niveaux 2–3 ; liens croisés entre hébergements / expériences.
- [ ] Menu mobile : ouverture < 300 ms, fermeture évidente, focus piégé, scroll de la page bloqué.

## C. Pages hébergements

- [ ] Nom propre, promesse, galerie ≥ 8 images, faits groupés, prix indicatif ou tarifs, conditions, CTA sticky mobile, hébergements complémentaires.
- [ ] Aucune info indispensable uniquement dans le moteur externe.

## D. Réservation et conversion

- [ ] Distinction claire découvrir / demander / réserver.
- [ ] Moteur pré-rempli depuis la page hébergement ; dates + occupants en ≤ 3 interactions.
- [ ] Bénéfices de la réservation directe visibles près du CTA.
- [ ] Réassurance : avis, récompenses, politique d'annulation, contact humain avec délai de réponse.
- [ ] Rupture avec le moteur externe traitée (cohérence visuelle, pas de perte de contexte, retour possible).
- [ ] Formulaires : labels visibles, erreurs explicites, confirmation, RGPD.

## E. Copywriting

- [ ] Titres ≤ 8 mots ; paragraphes ≤ 90 mots ; aucune formule creuse (« luxe », « élégant », « exceptionnel » sans preuve).
- [ ] Vocabulaire sensoriel et concret ; caractéristiques techniques présentes mais secondaires.
- [ ] CTA formulés en verbes d'action cohérents avec le mode de conversion.
- [ ] Orthographe, traductions, cohérence des noms d'hébergements partout.

## F. Photo et vidéo

- [ ] Ratio lieu / expérience équilibré ; présence humaine crédible ; lumière naturelle ; pas de HDR excessif.
- [ ] Vidéo hero : ≤ 6 Mo desktop, version mobile dédiée ou image, poster, muted, playsinline, pas de son automatique, pause possible.
- [ ] Images : formats modernes (AVIF/WebP), srcset, dimensions réservées, lazy loading hors hero.

## G. Mouvement

- [ ] Signature de mouvement unique et cohérente ; durées 200–900 ms ; easings out.
- [ ] Rien ne bloque la lecture (pas de scroll hijack, pas d'animation > 1,2 s avant contenu).
- [ ] `prefers-reduced-motion` : parallaxe, autoplay, animations d'entrée désactivés ou réduits.
- [ ] Mobile : animations allégées, aucune animation dépendante du hover.

## H. Responsive

- [ ] Breakpoints testés : 360, 390, 768, 1024, 1280, 1440, 1920.
- [ ] Titres mobiles 28–40 px ; texte ≥ 16 px ; cibles tactiles ≥ 44 px.
- [ ] Aucune capitalisation illisible ; aucun débordement horizontal ; barre CTA fixe basse sur pages hébergement.

## I. Performance (mobile, 4G simulée)

| Métrique | Cible | Mesuré | OK |
|---|---|---|---|
| LCP | < 2,5 s | | |
| CLS | < 0,1 | | |
| INP | < 200 ms | | |
| Poids page home | < 3 Mo (hors vidéo) | | |
| Requêtes | < 80 | | |
| Scripts tiers | listés et justifiés | | |

## J. Accessibilité (WCAG 2.2 AA)

- [ ] Contrastes ≥ 4,5:1 (texte) et 3:1 (grands titres, composants).
- [ ] Navigation clavier complète, focus visible, ordre logique, skip link.
- [ ] Alt descriptifs ; vidéos décoratives marquées ; iframes titrées.
- [ ] Formulaires étiquetés ; erreurs annoncées ; langue déclarée.
- [ ] Test lecteur d'écran sur home + page hébergement + moteur.

## K. SEO

- [ ] Title/description uniques ; H1 unique ; hiérarchie H2/H3 ; canonical ; hreflang ; sitemap ; robots.
- [ ] Données structurées (Hotel/LodgingBusiness, Offer, FAQ, BreadcrumbList) validées.
- [ ] Contenu indexable (texte réel, pas uniquement dans des images/vidéos) ; pages destination/expériences riches.
- [ ] OG/Twitter images ; favicon ; 404 utile ; redirections de l'ancien site.

## L. Juridique et confiance

- [ ] Mentions légales, CGV, confidentialité, cookies (consentement conforme, non bloquant), accessibilité.
- [ ] Prix affichés avec taxes et frais ; politique d'annulation lisible avant paiement.

## Notes

| Domaine | Note /10 | Justification (≥ 2 faits) |
|---|---|---|
| Branding | | |
| Direction artistique | | |
| Animations | | |
| UX | | |
| Conversion | | |
| Mobile | | |
| Performance / accessibilité / SEO | | |
| **Globale** | | |

## Décision

- [ ] Publier
- [ ] Publier avec réserves (liste) 
- [ ] Ne pas publier (bloquants)
