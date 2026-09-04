# Checklists qualité — principes classés et contrôles

> Version opérationnelle de la bibliothèque de principes (Phase 3 de la recherche). Niveaux : **[I]** Indispensable · **[R]** Recommandé · **[S]** Signature premium. Utiliser pour : cadrer un projet (avant), auditer un site existant (pendant), valider avant publication (après, avec `templates/final-website-audit.md`).

## A. Les 30 principes fondamentaux (résumé)

1. [I] Promesse en 5 secondes (média + titre 2–8 mots + lieu + action).
2. [I] Offre concrète au plus tard en 3e section.
3. [I] Système visuel minimal tenu partout, moteur compris.
4. [I] Le vide est un matériau (respirations 96–160 px, texte 640–720 px).
5. [I] La photographie porte la gamme (traitement unique, trois échelles, humains crédibles).
6. [S] Objets et matières signatures à la place des icônes.
7. [I] Nommer (hébergements, personnes, signature).
8. [I] Ligne de faits sous chaque nom.
9. [I] Prix ou moyen d'obtenir un prix avant le moteur.
10. [I] Un seul CTA principal persistant.
11. [I] Le verbe du CTA dit ce qui se passe.
12. [I] Une voie humaine à côté du moteur.
13. [I] Preuve près de l'action (avis datés, distinctions, chiffres).
14. [I] Le moteur porte la marque.
15. [R] Le menu suit le parcours (5–7 entrées).
16. [I] Une page par type d'hébergement.
17. [I] Toute page produit propose des alternatives.
18. [R] Le manifeste dit ce que l'on refuse.
19. [I] Jamais « luxe » sans preuve.
20. [I] Le mobile est le cas principal.
21. [I] Une seule vidéo autoplay, avec poster, pause, ≤ 6 / 3 Mo.
22. [I] Hero lisible sans vidéo.
23. [R] Le mouvement est une signature unique.
24. [I] Scroll natif, pas de préloader bloquant.
25. [I] Reduced motion et zoom respectés.
26. [I] Contrastes, focus, landmarks, alt, un H1.
27. [I] Budget de poids décidé au brief (< 3 Mo hors vidéo, ≤ 5 tiers).
28. [R] Pages destination et expériences = pages SEO.
29. [R] Aucune interruption (pop-up, One Tap, bannière).
30. [S] Faire ressentir une journée.

### Principes additionnels (série 2 du benchmark)
31. [S] La couleur comme structure narrative (3–5 fonds pleins, contrastes vérifiés).
32. [S] La typographie à l'échelle du lieu (display 80–256 px desktop, −60 % mobile ; trois voix à rôles).
33. [R] Texte qui se remplit ou se révèle au scroll : ≤ 2 par page, jamais informatif, reduced motion.
34. [S] Une seule séquence épinglée par page (horizontale, sticky + rideau), avec « passer » et version mobile empilée.
35. [I] Le manifeste est un produit nommé, répété, suivi d'une offre concrète.
36. [I] Transparence tarifaire : prix « from », grilles comparatives, prix barrés/par nuit, calendrier de prix.
37. [I] « Comment ça marche » pour toute offre complexe (étapes, acompte, assurance, préparation).
38. [R] Formulaire de demande qualifiant (cartes cliquables, budget si ticket élevé, pré-remplissage) avec humain nommé et délai.
39. [R] Multi-entités : invariants (header, cartes, sous-nav) + marqueurs (couleur, logo, fil d'Ariane, JSON-LD) + sélecteur de lieu.
40. [S] Modèle curateur : la marque raconte et affiche le prix, le partenaire vend ; page shoppable ; un moteur cohérent.

## A bis. Contrôles spécifiques série 2

- [ ] Aucune date, devise ou nombre de nuits codés en dur dans les liens vers le moteur.
- [ ] Le « Book » d'une home de collection ouvre un sélecteur de lieu ; « Book » navigue toujours ; « Contact » ne renvoie jamais à la home.
- [ ] Un seul moteur par marque, thématisé ; pas de moteur différent par maison.
- [ ] Budget vidéo ≤ 10 Mo par page toutes sources ; une source par device ; jamais `preload="auto"` sur plusieurs vidéos ; poster présent.
- [ ] Aucun pop-in marketing (Sleeknote, promo) ni chat proactif ; bannière cookies fermable.
- [ ] Display réduit d'au moins 60 % sur mobile ; barre CTA basse conservée ; séquence épinglée empilée.
- [ ] Prix visible avant le moteur (« from », cartes, grille) ; « comment ça marche » accessible depuis toute page d'offre complexe.
- [ ] Preuve sociale signée (prénom, type de séjour, date) et non seulement des logos.

## B. Erreurs qui font bas de gamme (contrôle négatif)

- [ ] Aucune photo de banque, HDR, grand-angle déformant, mannequin posé.
- [ ] Aucun pop-up à l'arrivée, compte à rebours, bandeau criard, chat bot auto-ouvert.
- [ ] Aucune capitale < 13 px ; aucun texte justifié ; ≤ 2 familles typographiques.
- [ ] Aucun bouton « SaaS » (rayon fort + ombre + dégradé) ; une seule bibliothèque d'icônes.
- [ ] Aucune animation bounce / particules / clignotement / préloader > 800 ms / curseur global.
- [ ] Aucun nom de chambre générique ; aucune description dupliquée ; aucun adjectif empilé.
- [ ] Prix visible ; pas de « Sold Out » par défaut ; pas de moteur gris hors charte.
- [ ] Menu ≤ 7 entrées principales ; externes signalés ; footer ≥ 13 px.
- [ ] Hero jamais blanc ; images dimensionnées ; pas de carrousel de slides automatique.
- [ ] Cookies non bloquants ; un seul élément fixe en bas sur mobile ; zoom libre.

## C. Page d'accueil

- [ ] [I] Header persistant + CTA ; [I] hero (média, titre, lieu, action) ; [I] manifeste 40–90 mots.
- [ ] [I] Hébergements (3 + tous) avec faits + prix « à partir de » ; [I] expériences (3–4).
- [ ] [R] Table / spa / services ; [I] preuve (avis datés, distinctions, chiffres).
- [ ] [R] Destination & accès (temps de trajet) ; [R] offres + bénéfices directs.
- [ ] [I] Contact humain nommé ; [R] newsletter sans pop-up ; [I] footer complet.
- [ ] [S] Section « une journée ici » ou sticky narratif unique.
- [ ] Ordre narratif respecté ; aucune section sans objectif ; jamais deux structures identiques consécutives.

## D. Page hébergement

- [ ] [I] Nom propre + type ; promesse ≤ 15 mots ; ligne de faits.
- [ ] [I] Galerie ≥ 8 images ordonnées, lightbox, clavier, compteur mobile.
- [ ] [I] Description 60–150 mots sensorielle ; faits groupés complets.
- [ ] [R] Inclus / à la carte ; [R] plan (villa, chalet).
- [ ] [I] Prix « à partir de » + conditions ; CTA sticky (barre basse mobile).
- [ ] [I] Réassurance (avis, humain) ; 2–3 alternatives avec prix ; [R] expériences liées.
- [ ] [S] « Une journée ici » / vidéo 45–60 s.
- [ ] Schema HotelRoom / Accommodation + Offer.

## E. Page expérience

- [ ] [I] Titre-sensation + sur-titre ; image large + geste / moment / résultat.
- [ ] [I] Déroulé (quand, durée, avec qui, pour qui) ; ressenti 40–100 mots.
- [ ] [I] Pratique (inclus, prix, réservation, saison, niveau) ; CTA.
- [ ] [R] Hébergement recommandé ; autres expériences ; [S] personne qui accompagne.

## F. Parcours de réservation

- [ ] [I] CTA persistant ; dates + voyageurs ≤ 3 interactions ; calendrier tactile ; indisponibilités visibles.
- [ ] [I] Type pré-rempli ; prix, taxes, conditions avant paiement ; bénéfices directs ≤ 3.
- [ ] [I] Moteur à la charte + retour au site ; voie humaine ; confirmation écran + e-mail.
- [ ] [R] Upsell discret ; message d'indisponibilité avec alternatives ; [S] prix dans le calendrier.
- [ ] Rupture moteur externe traitée (même onglet ou mention, `preconnect`, paramètres dans l'URL).

## G. Menu

- [ ] [I] 5–7 entrées dans l'ordre du parcours ; CTA dans le header partout ; externes signalés ; page active.
- [ ] [I] Mobile : plein écran / panneau, < 450 ms, Escape, focus piégé, scroll bloqué, fermeture évidente.
- [ ] [R] Sous-menus ≤ 6 ; jamais la liste complète des chambres ; téléphone et langue visibles.
- [ ] [S] Aperçu image au survol.

## H. Copywriting

- [ ] [I] Une voix ; titres 2–8 mots ; paragraphes ≤ 90 mots ; phrases 8–18 mots.
- [ ] [I] Concret et sensoriel ; aucun « luxe / élégant / exceptionnel » sans preuve.
- [ ] [I] Promesse avant caractéristiques ; ligne de faits ; CTA en verbes distincts.
- [ ] [R] Négation d'un attendu ; personnes nommées ; chiffres vrais.
- [ ] [S] Lexique de marque 30–50 mots réutilisé (alt, e-mails, moteur).

## I. Photo

- [ ] [I] Lumière naturelle ; traitement unique ; trois échelles ; formats 3:2, 4:5, 1:1, 16:9, 9:16 ; ≥ 2 400 px.
- [ ] [I] Destination sans le bâtiment (3–5 / saison) ; [R] humains crédibles ; moments de vie.
- [ ] [S] 5–10 natures mortes signatures ; [I] zéro banque d'images.

## J. Vidéo

- [ ] [I] Une autoplay max ; muette ; loop propre ; 10–15 s ; poster ; pause ; playsinline.
- [ ] [I] 16:9 ≤ 6 Mo ; 9:16 ≤ 3 Mo ou image ; pas d'autoplay en reduced motion / Save-Data ; hero lisible sans vidéo.
- [ ] [R] Secondaires au clic ; drone ≤ 3 plans ; [Éviter] intro bloquante.

## K. Animation

- [ ] [I] Signature unique ; durées 150–250 / 400–700 / 700–1 000 ms / 20–60 s ; easings out ; transform + opacity.
- [ ] [I] Contenu sans JS ; reduced motion (opacité simple, autoplay coupé, parallaxe et zoom désactivés).
- [ ] [R] Amplitudes 16–32 px (8–16 mobile) ; scale ≤ 1,08 ; un mouvement permanent par viewport.
- [ ] [S] Sticky narratif unique desktop ; [Interdit] scroll hijack, préloader long, bounce.

## L. Responsive

- [ ] [I] 360/390/768/1024/1280/1440 testés ; hero 70–90 svh ; CTA visible sans scroll.
- [ ] [I] Titres 28–40 px ; corps ≥ 16 px ; cibles ≥ 44 px ; capitales ≥ 13 px.
- [ ] [I] Barre basse prix + CTA sur hébergements ; un seul fixe en bas ; galeries horizontales ; accordéons ; zoom libre.
- [ ] [Interdit] widget desktop qui masque ; tableaux à scroll ; header > 64 px mobile.

## M. Performance

- [ ] [I] LCP < 2,5 s ; CLS < 0,1 ; INP < 200 ms (mobile 4G).
- [ ] [I] < 3 Mo hors vidéo ; < 80 requêtes ; ≤ 5 tiers ; marketing après consentement.
- [ ] [I] AVIF/WebP + srcset + dimensions + lazy hors hero + fetchpriority LCP.
- [ ] [I] Vidéo : preload metadata, poster, versions, arrêt hors écran ; polices ≤ 4 woff2.
- [ ] [R] Pas de bibliothèques redondantes ; preconnect moteur.

## N. Accessibilité

- [ ] [I] Contrastes 4,5:1 / 3:1 ; scrim sur photos ; focus visible ; skip link ; Escape ; pièges de focus.
- [ ] [I] Landmarks ; un H1 ; hiérarchie ; alt ; iframes titrées ; labels ; erreurs liées ; autocomplete.
- [ ] [I] Vidéos avec pause ; `lang` ; zoom libre.
- [ ] [R] Test lecteur d'écran (home, hébergement, moteur) ; cookies accessibles.

## O. Conversion

- [ ] [I] Mode défini ; un CTA plein par écran ; prix avant moteur ; preuve près du CTA ; bénéfices ≤ 3.
- [ ] [I] Humain nommé + délai ; moteur à la charte pré-rempli ; alternatives ; formulaires 4–6 champs + confirmation ; mesure par emplacement.
- [ ] [R] Offres datées ; upsell contextuel ; [Interdit] pop-ups, compte à rebours, « Sold Out » par défaut, captcha visible.

## P. SEO

- [ ] [I] Title/description uniques ; H1 unique ; canonical ; hreflang + x-default ; sitemap ; 301 ; 404 utile.
- [ ] [I] Schema Hotel / LodgingBusiness / VacationRental + HotelRoom + Offer + FAQ + Breadcrumb + Organization.
- [ ] [I] Texte réel : home ≥ 300 mots, hébergement ≥ 250, destination ≥ 600 ; OG image par page clé.
- [ ] [R] Pages destination, saisons, thématiques ; journal ; alt descriptifs.

## Q. Notation d'un audit (rappel)

Six notes /10 (branding, direction artistique, animations, UX, conversion, mobile) + note globale ; chaque note justifiée par au moins deux faits mesurés (valeurs, URL, captures) ; séparer faits / interprétation / recommandation ; marquer « hypothèse » ce qui n'est pas prouvé ; lister ce qui n'a pas pu être vérifié.
