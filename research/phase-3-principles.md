# Phase 3 — Bibliothèque de principes de haute qualité

Extraite des audits (Phase 1) et de la comparaison (Phase 2). Niveaux : **[I]** Indispensable · **[R]** Recommandé · **[S]** Signature premium. Chaque principe dit quoi faire, pourquoi, dans quel contexte, et quel risque il évite. Les mentions « (F) (C) (B) (S) (L) » renvoient aux sites du benchmark où le mécanisme a été observé.

## 1. Les 30 principes fondamentaux d'un site d'hébergement premium

1. **[I] La promesse en cinq secondes.** Hero = un média signature + un titre de 2 à 8 mots + le lieu + une action. Pourquoi : la décision d'explorer se prend avant le premier scroll. Contexte : tous. Risque : hero « beau » mais muet (F ne nomme pas le lieu ; S est illisible sans vidéo).
2. **[I] Vendre l'expérience avant la chambre, mais rendre l'offre concrète avant le troisième écran.** F attend 3 003 px : trop tard pour un visiteur qui compare. Placer les hébergements au plus tard en 3e section.
3. **[I] Un système visuel minimal tenu partout.** 2–3 couleurs, 1–2 familles typographiques, rayon unique, mêmes composants sur la home, les pages, le moteur (F, S, L). Risque : moteur ou restaurant hors charte (C, S).
4. **[I] Le vide est un matériau.** Respirations de 96–160 px desktop, 64–96 px mobile ; largeur de texte 640–720 px (F : 713 px). Risque : densité de plateforme sans hiérarchie (page villa L : 236 occurrences de 14 px).
5. **[I] La photographie porte la gamme.** Un traitement colorimétrique unique, trois échelles (large / usage / détail), présence humaine crédible (mains, dos, gestes). Risque : patchwork (L), intérieurs vides (C home).
6. **[S] Les matières et objets signatures remplacent les icônes.** Coquillages (S), écorce et herbier (F), dentelle et artisan (B). Risque : pictogrammes génériques.
7. **[I] Nommer.** Hébergements à noms propres (Baba Royale, Tower Suite, La Corte Magnifica, Villa Blue), personnes nommées (hôtes F, équipe C, conseiller L), signature de marque (« Nowhere Else »). Risque : « Chambre Supérieure ».
8. **[I] Une ligne de faits sous chaque nom.** « 55 m² · 2 personnes · 1 chambre » (F), « 10 voyageurs · 5 chambres · 5 sdb · 630 m² » (L). Pourquoi : qualifier en une seconde.
9. **[I] Le prix ou le moyen d'obtenir un prix est visible avant le moteur.** Seul L le fait (total 7 nuits). Risque : abandon vers les OTA qui, elles, affichent le prix.
10. **[I] Un CTA principal persistant, un seul.** Onglet (B), bouton header (S), barre basse mobile (L). Risque : deux CTA texte de même poids (F), aucun rappel (C).
11. **[I] Le verbe du CTA dit ce qui se passe.** Découvrir / Vérifier les disponibilités / Demander / Réserver. Risque : « Réserver » qui ouvre un formulaire, « Book » qui change de domaine sans prévenir.
12. **[I] Une voie humaine à côté du moteur.** « Request » (F), conseiller avec photo et horaires (L), téléphone permanent (L). Risque : 0 téléphone (C).
13. **[I] La preuve près de l'action.** Avis datés avec source, distinctions avec année, chiffres vérifiables (L). Risque : 0 avis (F, C, B, S).
14. **[I] Le moteur porte la marque.** SynXis rethématisé (F), moteur propriétaire (B) ; à l'inverse eZee gris (C) et Marriott (S). Risque : rupture de confiance au moment de payer.
15. **[R] Le menu suit le parcours, pas l'organigramme.** 5–7 entrées (S : 4 + 2 ; F : 9), commencer par le lieu ou les hébergements. Risque : annuaire de 20 entrées dont 11 externes (B), sous-menu de 12 chambres (C).
16. **[I] Une page par type d'hébergement.** Risque : page unique sans galerie ni surface (S) ; tuiles sans information (B).
17. **[I] Toute page produit propose une alternative.** 2–3 hébergements similaires avec prix (L). Risque : cul-de-sac (F, C, S).
18. **[R] Le manifeste dit ce que l'on refuse.** « Pas de TV : des vues » (C), « peace as a new luxury » (F). Pourquoi : la négation positionne mieux qu'un superlatif.
19. **[I] Jamais le mot « luxe » sans preuve.** F, S et C évitent le mot dans le corps ; le luxe se dit par la précision (matière, heure, prénom).
20. **[I] Le mobile est le cas principal.** Hero ≤ 90 svh, titres 30–40 px (C garde 56 px : erreur), corps ≥ 16 px, cibles ≥ 44 px (B : 24–30 px ; L : 35 px), barre basse prix + CTA (L).
21. **[I] Une seule vidéo autoplay par page, avec poster, pause, ≤ 6 Mo desktop et ≤ 3 Mo mobile (ou image).** Aucun site du panel ne respecte les quatre conditions.
22. **[I] Le hero doit être lisible sans sa vidéo.** Fond de la couleur dominante + poster. Risque : titre blanc sur crème (S).
23. **[R] Le mouvement est une signature, pas un catalogue.** Une seule idée (zoom lent 40 s chez B, brightness 0,8 chez C, scale 1,1 chez L) déclinée partout ; durées 200–900 ms ; easings out.
24. **[I] Le scroll reste natif.** Pas de hijack, pas de préloader bloquant (B), pas de snap sur la page entière (F déclare onepage-scroll sans effet).
25. **[I] Reduced motion et zoom respectés.** Kill-switch minimal (C) ou règles ciblées ; jamais `maximum-scale=1` (F, B, L).
26. **[I] Contrastes AA, focus visible, landmarks, alt, un H1.** Les cinq sites échouent sur au moins trois de ces points.
27. **[I] Le poids se décide au brief.** Budget : < 3 Mo hors vidéo, ≤ 5 tiers. Les cinq sites portent 8 à 165 Mo, majoritairement en vidéo et scripts marketing.
28. **[R] Les pages destination et expériences sont des pages SEO à part entière.** L construit son trafic sur des pages destination et thématiques ; F a une page « Things to do in the Dolomites ».
29. **[R] Les interruptions sont interdites.** Pop-up newsletter, One Tap, smart banner, bandeau cookies plein écran (L, B) : chaque interruption contredit la promesse de calme.
30. **[S] Le site fait ressentir une journée.** Rituels (petit-déjeuner, bain, feu), moments (matin, heure bleue), gestes : la section « une journée ici » est l'espace que personne n'occupe dans le panel.

## 2. Les erreurs qui rendent immédiatement un site bas de gamme

- Photos de banque, HDR, grand-angle déformant, mannequins face caméra.
- Pop-up à l'arrivée, compte à rebours, bandeau promotionnel criard, chat bot qui s'ouvre seul.
- Titres en capitales sur mobile à moins de 13 px ou sans interlettrage ; texte justifié ; plus de deux polices.
- Boutons arrondis « SaaS » avec ombres, icônes Font Awesome multicolores, dégradés.
- Animations « bounce », particules, texte qui clignote, préloader de 3 s, curseur remplacé partout.
- Noms de chambres génériques ; descriptions copiées ; adjectifs empilés (« luxueux, élégant, exceptionnel »).
- Prix absent ou seulement dans un moteur gris d'un autre domaine ; « Sold Out » par défaut (C).
- Menu de 15 entrées, liens externes non signalés, footer plus riche que le menu, textes de 9 px (B).
- Hero vidéo qui reste blanc ; images qui sautent au chargement ; carrousel automatique de slides avec 5 messages.
- Cookies plein écran ; deux éléments fixes en bas de l'écran mobile ; zoom bloqué.

## 3. Éléments indispensables d'une page d'accueil

[I] Header persistant avec CTA · [I] Hero (média signature, titre, lieu, action) · [I] Manifeste de 40–90 mots · [I] Hébergements (3 mises en avant + tous) avec faits et prix « à partir de » · [I] Expériences ou rituels (3–4) · [R] Table / spa / services · [I] Preuve (avis datés, distinctions, chiffres) · [R] Destination et accès (temps de trajet) · [R] Offres et bénéfices directs · [I] Contact humain nommé · [R] Newsletter sans pop-up · [I] Footer complet (coordonnées, plan, labels, légal) · [S] Une section « une journée ici » ou un sticky narratif unique.

## 4. Éléments indispensables d'une page chambre / propriété

[I] Nom propre + type · [I] Promesse ≤ 15 mots · [I] Ligne de faits · [I] Galerie ≥ 8 images ordonnées avec lightbox · [I] Description sensorielle 60–150 mots · [I] Faits groupés (confort / bain / techno / extérieur / accessibilité) · [R] Inclus vs à la carte · [I] Prix « à partir de » + conditions (acompte, annulation, arrivée/départ) · [I] CTA sticky (Réserver / Demander) · [R] Plan (villa, chalet) · [I] Réassurance (avis, humain) · [I] 2–3 alternatives avec prix · [R] Expériences liées · [S] « Une journée ici » ou vidéo de 45–60 s.

## 5. Éléments indispensables d'une page expérience

[I] Titre-sensation + sur-titre catégorie · [I] Image large + 2–3 images (geste, moment, résultat) · [I] Déroulé (quand, durée, avec qui, pour qui) · [I] Ce que l'on ressent (40–100 mots) · [I] Infos pratiques (inclus, prix, réservation, saison, niveau) · [I] CTA (Réserver l'expérience / Ajouter à mon séjour / Demander) · [R] Hébergement recommandé · [R] Autres expériences · [S] Personne qui accompagne (prénom, photo).

## 6. Éléments indispensables d'un parcours de réservation

[I] CTA persistant · [I] Dates + voyageurs en ≤ 3 interactions, calendrier tactile, indisponibilités visibles · [I] Type pré-rempli depuis la page hébergement · [I] Prix par nuit/semaine, taxes, conditions avant paiement · [I] Bénéfices directs (≤ 3) à côté du bouton · [I] Moteur à la charte (logo, couleurs, police) et retour au site · [I] Alternative humaine (téléphone, WhatsApp, demande) · [I] Confirmation claire (écran + e-mail) · [R] Upsell discret (transfert, petit-déjeuner, soin) · [R] Message d'indisponibilité avec alternatives · [S] Prix dans le calendrier.

## 7. Règles d'un bon menu

[I] 5–7 entrées principales dans l'ordre du parcours · [I] CTA dans le header sur toutes les pages · [I] Liens externes signalés et séparés · [I] Page active indiquée · [I] Menu mobile plein écran ou panneau, ouverture < 450 ms, Escape, focus piégé, scroll bloqué, fermeture évidente · [R] Sous-menus limités à 6 items ; jamais la liste complète des chambres · [R] Téléphone et langue visibles · [S] Aperçu image au survol de chaque entrée.

## 8. Règles de copywriting hôtelier

[I] Une voix (maison / nous / vous) · [I] Titres 2–8 mots, paragraphes ≤ 90 mots, phrases 8–18 mots · [I] Concret et sensoriel (matière, heure, geste) ; jamais « luxe », « élégant », « exceptionnel » sans preuve · [I] Promesse avant caractéristiques ; ligne de faits ensuite · [I] CTA en verbes distincts · [R] Négation d'un attendu dans le manifeste · [R] Personnes nommées · [R] Chiffres vrais (2 300 maisons, 157 chambres) · [S] Lexique de marque de 30–50 mots réutilisé partout (alt, e-mails, moteur).

## 9. Règles photographiques

[I] Lumière naturelle, heure choisie, lampes allumées · [I] Traitement colorimétrique unique · [I] Trois échelles par sujet · [I] Formats livrés 3:2, 4:5, 1:1, 16:9, 9:16 ; ≥ 2 400 px · [I] Destination sans le bâtiment (3–5 images par saison) · [R] Présence humaine crédible · [R] Moments de vie (table dressée, feu, peignoir) · [S] 5–10 natures mortes d'objets signatures · [I] Jamais de banque d'images, HDR, ciel remplacé.

## 10. Règles d'utilisation de la vidéo

[I] Une seule autoplay par page ; muette ; loop propre ; 10–15 s ; poster ; pause ; `playsinline` · [I] 16:9 ≤ 6 Mo desktop ; 9:16 ≤ 3 Mo mobile ou image · [I] Pas d'autoplay en reduced motion ni Save-Data · [I] Hero lisible sans la vidéo · [R] Vidéos secondaires au clic (visite 45–90 s) · [R] Drone ≤ 3 plans · [À éviter] Intro bloquante (si imposée : ≤ 8 s, « Passer » immédiat, une fois par session).

## 11. Règles d'animation

[I] Une signature de mouvement · [I] Durées : feedback 150–250 ms, entrées 400–700 ms, révélations 700–1 000 ms, ambiance 20–60 s · [I] Easings out (`cubic-bezier(.22,1,.36,1)`) · [I] Transform + opacity uniquement · [I] Contenu présent sans JS · [I] Reduced motion : entrées en opacité simple, autoplay coupé, parallaxe et zoom lent désactivés · [R] Amplitudes 16–32 px desktop, 8–16 px mobile ; scale ≤ 1,08 · [R] Un seul élément en mouvement permanent par viewport · [S] Sticky narratif unique (desktop seulement) · [Interdit] Scroll hijack, préloader long, bounce, particules.

## 12. Règles de responsive design

[I] Breakpoints 360/390/768/1024/1280/1440 · [I] Hero 70–90 svh, CTA visible sans scroll · [I] Titres 28–40 px, corps ≥ 16 px, cibles ≥ 44 px, jamais de capitales < 13 px · [I] Barre basse prix + CTA sur pages hébergement ; un seul élément fixe en bas · [I] Galeries en défilement horizontal avec compteur · [I] Accordéons pour faits et FAQ · [I] Zoom autorisé · [R] Vidéo remplacée par une image si nécessaire · [Interdit] Widget desktop qui masque le contenu, tableaux à scroll horizontal, header > 64 px.

## 13. Règles de performance

[I] LCP < 2,5 s, CLS < 0,1, INP < 200 ms (mobile 4G) · [I] < 3 Mo hors vidéo, < 80 requêtes, ≤ 5 tiers, tiers marketing après consentement · [I] AVIF/WebP + srcset + dimensions + lazy hors hero + `fetchpriority` sur le LCP · [I] Vidéo : preload metadata, poster, versions, arrêt hors écran · [I] ≤ 4 fichiers de police woff2, `font-display` · [R] Pas de bibliothèques redondantes (jQuery + Bootstrap + animate + fancybox + video.js + dash.js observés) · [R] Préconnexion au moteur.

## 14. Règles d'accessibilité

[I] Contrastes 4,5:1 / 3:1 ; scrim sur photos · [I] Focus visible, ordre logique, skip link, Escape, pièges de focus sur menu et modales · [I] Landmarks, un H1, hiérarchie · [I] Alt descriptifs ; décoratifs vides ; iframes titrées · [I] Labels visibles, erreurs liées, autocomplete · [I] Vidéos : pause, `aria-hidden` si décoratives · [I] `lang`, zoom libre · [R] Test lecteur d'écran sur home + hébergement + moteur · [R] Bandeau cookies accessible et non bloquant.

## 15. Règles de conversion

[I] Mode de conversion défini (transactionnel / conversationnel / hybride) · [I] Un CTA plein par écran ; hiérarchie verbe/action · [I] Prix avant le moteur · [I] Preuve près du CTA ; bénéfices directs ≤ 3 · [I] Humain nommé + délai de réponse · [I] Moteur à la charte, pré-rempli, retour possible · [I] Alternatives sur chaque page produit · [I] Formulaires 4–6 champs, confirmation · [I] Mesure des clics par emplacement · [R] Offres datées avec code · [R] Upsell contextuel · [Interdit] Pop-ups, compte à rebours, « Sold Out » par défaut, captcha visible.
