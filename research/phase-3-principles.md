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

---

# Complément série 2 — principes additionnels (dix références « au-delà du quiet luxury »)

Sources : fiches 06 à 15. Sites cités : Odisej (O), Mas Girbau (MG), Our Habitas (H), Aethos (A), White Desert (WD), Explora (E), Experimental (X), Soneva (SO), Vipp (V), Pelorus (P).

## 16. Dix principes supplémentaires

31. **[S] La couleur comme structure narrative.** Alterner 3 à 5 fonds pleins issus du paysage ou de la matière (O : crème, olive, bleu nuit ; MG : crème, vert profond, sauge, noir ; X : une couleur par niveau d'entité). Pourquoi : la page se lit sans texte, le rythme devient visible. Contexte : hôtels de destination, maisons à récit, groupes. Risque : contrastes insuffisants (O : 1,1–1,5 avant révélation), monotonie inverse si toutes les sections sont saturées.
32. **[S] La typographie prend l'échelle du lieu.** Display 80–256 px pour un mot-territoire (WD : « ANTARCTICA » 256 px ; O : statements 80 px ; A : capitales serif 120 px) et trois voix typographiques à rôles distincts (WD : donnée / émotion / information). Risque : mobile illisible si l'échelle n'est pas réduite de 60 % ; poids des polices.
33. **[R] Le texte qui se remplit au scroll cadence la lecture.** Statements de 80 px avec remplissage progressif (O) ou paragraphes scrubbés mot à mot en section épinglée (MG). Fonction : rythme et émotion. Limite : une ou deux occurrences par page, jamais pour du texte informatif, reduced motion obligatoire.
34. **[S] Une séquence épinglée unique raconte la logistique ou le lieu.** Séquence horizontale camps → presse → carte animée (WD, ≈ 10 000 px), section environnement épinglée avec rideau vers une image (MG), story épinglée (H). Fonction : expliquer et donner du rythme. Risque : perte de repères ; prévoir indicateur de progression et « passer » ; empiler sur mobile ou réduire l'amplitude.
35. **[I] Le manifeste est un produit.** Piliers (H), règles (A), manifesto (X), posture (V), signature de clôture (SO) : le manifeste est nommé, répété dans le menu, sur les objets, en fin de page. Risque : manifeste sans offre concrète derrière (H : 0 chambre sur la home).
36. **[I] La transparence tarifaire est un argument de luxe.** Cartes « saison • prix par personne » (P), grilles filtrables avec variantes côte à côte (WD), prix barrés et par nuit (E), « From … per night » avant le bouton (V), calendrier de prix dans le moteur (X). Risque : perte de confiance quand le prix n'apparaît qu'au paiement (10 sites sur 15).
37. **[I] « Comment ça marche » est une page indispensable pour toute offre complexe.** Étapes numérotées (WD : 6 ; P : 6 étapes + 7 raisons), acompte, assurance, préparation, délais ; accessible depuis toutes les pages (onglet fixe chez WD). Contexte : expéditions, sur mesure, croisières, retraites, villas. Risque : formulaire de demande sans méthode visible.
38. **[R] Le formulaire de demande qualifie sans effrayer.** Cartes cliquables (saison, mois, intérêts) puis coordonnées (WD) ; budget obligatoire quand le ticket d'entrée est élevé (P, Le Collectionist) ; pré-remplissage depuis l'itinéraire (`?itinerary=`). Toujours avec humain nommé et délai (manque chez P).
39. **[R] L'entité multiple exige des invariants et des marqueurs.** Header commun, cartes normalisées, sous-navigation d'entité, couleur ou logotype par entité, fil d'Ariane, JSON-LD typé (X, SO) ; sélecteur de lieu avant tout moteur (H). Risque : one-pages d'entité de 25 000 px avec chapitres vides (X), pages de marque sans chemin vers la chambre (H, A).
40. **[S] Le modèle curateur et la page shoppable.** Une marque non hôtelière raconte, signe (architecte, chiffres, coordonnées) et affiche le prix, le partenaire vend la nuit (V) ; les objets du décor sont liés à la boutique ; boucle boutique ↔ séjour. Contexte : marques de design, vin, mode, architectes, chefs. Risque : moteurs hétérogènes par maison, absence de CTA sur la liste.

## 17. Compléments aux listes de règles

- **Menu (§7)** : pour un groupe, trois audiences (voyageurs, propriétaires, agents) ne partagent pas le même menu principal ; un mega-menu de destinations doit proposer trois portes (lieu, type, profil) comme P ; le « Book » d'une home de collection ouvre un sélecteur de lieu, jamais un moteur générique.
- **Copywriting (§8)** : rareté chiffrée (« fewer than 500 », « six suites », « 12 guests »), langage cartographique (coordonnées, heures, distances), note de franchise (météo, contraintes), moule de titre « impératif + lieu + italique » (X), possessif de communauté « Our » (H), signature de clôture identique sur toutes les pages (SO).
- **Photo / vidéo (§9–10)** : scènes de communauté à 60 % pour une marque-communauté (H) ; heure bleue et coordonnées GPS pour l'architecture (V, WD) ; le film scindé lieu | produit (V). Interdit : servir la vidéo desktop de 20–60 Mo au mobile (P, MG, V) ; `preload="auto"` sur 10 vidéos (V) ; un master de 82 Mo rechargé (E).
- **Animation (§11)** : GSAP ScrollTrigger et split-text autorisés au niveau signature avec trois limites : ≤ 1 section épinglée par page, ≤ 80 éléments animés simultanés, reduced motion effectif (0 site sur 15 ne l'a).
- **Responsive (§12)** : conserver la barre CTA basse (MG 64 px, X 65 px) ; réduire le display de 60 % (WD 256 → 80 px) ; supprimer chat proactif, pop-ins et bannières empilées (WD, V, P).
- **Performance (§13)** : budget vidéo par page ≤ 10 Mo toutes sources ; une seule source par device ; posters ; pas de `preload="auto"` ; images ≤ 400 Ko avec srcset (0 srcset sur 8 sites de la série 2).
- **Conversion (§15)** : ne jamais coder de dates ou de devises dans les liens moteur (O, H) ; un moteur par marque, pas par maison (V) ; « Book » doit naviguer (SO) ; « Contact » ne renvoie pas à la home (E) ; le club ou l'adhésion est une conversion à part entière avec ses tarifs publics (A).
