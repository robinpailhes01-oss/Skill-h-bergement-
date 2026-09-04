# UX, parcours de réservation et conversion — hébergement premium

> Objectif : conduire le visiteur de l'émotion à l'action sans friction, en respectant le mode de conversion de l'établissement (transactionnel, conversationnel, hybride). Niveaux : Indispensable / Recommandé / Signature premium. Chaque règle précise le contexte et le risque évité.

## 0. Ce que fait le benchmark (faits, 2026-09-04)

| Site | Mode | Premier CTA | Formulations | Moteur | Persistance | Réassurance visible | Points de rupture |
|---|---|---|---|---|---|---|---|
| FORESTIS | hybride (« Request » interne + « Book » externe) | header : « Request » et « Book » (texte, pas de bouton) | Request / Book / Discover more ; « Contact & Arrival » en footer | SynXis (be.synxis.com), nouvel onglet ; page « Request » interne avec formulaire | header transparent ; barre de menu au scroll vers le haut ; mobile : barre basse tel / mail / localisation | labels Small Luxury Hotels, Michelin 2024, « 14+ » en footer ; citation des hôtes | changement de domaine et d'identité visuelle dans SynXis ; aucun prix sur les pages suites ; 2 CTA de même poids |
| Hotel Corazón | transactionnel (eZee / ipms247) | bandeau « BOOK NOW » 1 020×78 sous le header, sur la home et chaque page chambre | BOOK NOW + « CHECK AVAILABILITY » en micro-texte ; SHOW ALL ROOMS ; RESTAURANT (site séparé), EVENTS (Odoo) | externe, nouvel onglet ; identité différente | header fixe 128 px avec menu ; pas de sticky CTA | aucune preuve sociale ; aucun prix ; aucune politique visible | 3 domaines différents (site, restaurant, événements, boutique) ; pas de prix avant le moteur |
| Borgo Egnazia | transactionnel (moteur propriétaire booking.borgoegnazia.com) | onglet vertical fixe « BOOK » à droite + « BOOKING » dans le menu (URL pré-remplie arrival/departure/adults=2) | BOOK / Check availability / LOOK INSIDE / YOUR BORGO EXPERIENCE | modale « CHECK AVAILABILITY » (check-in, check-out, adults, children) puis moteur : liste des chambres avec « Last room left », description, galerie, tarifs (Advance purchase non remboursable / Best available rate avec annulation gratuite jusqu'à 7 jours), prix moyen par nuit, « BOOK NOW » | onglet fixe sur toutes les pages | logos LHW, Virtuoso, etc. en footer ; page « Accolades » | intro vidéo bloquante avec « SKIP » ; menu de 20 entrées mélangeant marque, filiales et B2B |
| The Seagate | transactionnel (Marriott) | bouton plein « RESERVE » dans le header fixe + widget CHECK IN / CHECK OUT / GUESTS / RESERVE fixe à droite du hero | RESERVE / DISCOVER / ROOM TYPES / RESERVE YOUR STAY | marriott.com, nouvel onglet (accès refusé aux automates) | header fixe 112 px + widget fixe | 157 chambres annoncées ; logos Turnberry + Marriott Bonvoy ; « spa-inspired bathrooms » | passage à Marriott (identité totalement différente) ; pas de prix sur le site ; pas de page par chambre |
| Le Collectionist | recherche + demande (conversationnel assisté) | barre de recherche Destination / Arrivée → Départ / Voyageurs / RECHERCHER dans le hero ; « S'INSPIRER » | RECHERCHER / RÉSERVEZ VOS VACANCES / EXPLOREZ / ÉCHANGER AVEC UN CONSEILLER / CONTACTEZ-NOUS / PLANIFIER UN APPEL / RÉSERVER / FAIRE UNE DEMANDE | interne : page propriété avec encart sticky (dates, total pour 7 nuits, « Réserver », « Faire une demande », téléphone) ; « Prix et disponibilités » par semaine ; conditions de réservation en FAQ | header 72 px ; encart de réservation sticky sur la page villa ; téléphone permanent | avis clients 4,8/5, « Leurs souvenirs », presse (Ideat, AD, Elle…), 2 300 propriétés, 10 bureaux locaux, Condé Nast | prompt « Sign in with Google » sur mobile ; bandeau cookies Axeptio ; densité élevée |

### Série 2

| Site | Mode | Premier CTA | Prix visible | Moteur / demande | Persistance | Réassurance | Ruptures et erreurs |
|---|---|---|---|---|---|---|---|
| Hotel Odisej | transactionnel | pills « Book now » + « Online Check-in » dans le header | non | book-secure (groupe) en nouvel onglet, dates codées 2023, aucun champ sur le site | header fixe ; CTA pré-footer | citation presse ; 0 avis | interstitiel anti-bot, dates périmées |
| Mas Girbau | conversationnel (maison entière) | « Reservar » corail fixe ; barre mobile 64 px | non | iframe BookingMood (calendrier 2 mois, « Send booking Request ») | oui, desktop et mobile | 12 inclusions ; 0 avis, 0 condition | formulaire en anglais sur site ES, onglets saison cachés |
| Our Habitas | transactionnel par lieu | « BOOK » → tiroir « Select Property » (9) | non | SynXis par hôtel, devises imposées, dates codées, `nights=4` | header ; BOOK absent des pages de marque | Dis-loyalty 35/20/10 %, inclusions ; 0 avis | mailto pour les expériences, OpenTable |
| Aethos | transactionnel + adhésion | « BOOK NOW » ; club « ENQUIRE » 218×47 | non (hôtels) ; oui (club 650 / 1 800 / 2 500 €/an) | hotelchamp IBE same-domain ; devis retraites | header ; pop-up promo bloquant | presse, journal daté ; 0 avis | « BOOK » ambigu sur la home de collection |
| White Desert | conversationnel qualifié | « Enquire » + « Rates » ; onglet « How it works » | oui : 8 cartes $16 500 → $115 500, variantes côte à côte | `/enquire?itinerary=` : formulaire en cartes (saison, mois, intérêts) + 7 champs, promesse 24 h, HubSpot meetings | nav fixe ; onglet ; chat | IAATO, CarbonNeutral, prix, presse, scientifique nommé, « How it works » 6 étapes | inputs sans label ; chat + cookies sur mobile |
| Explora Journeys | transactionnel à étapes | widget « Where to ? / When ? » + « VIEW 658 JOURNEYS » | oui : prix barrés, par nuit, offres datées, acompte 10 % | interne : 658 résultats, 12/page, filtres | header 132 → 63 px ; « Reserve » 70×35 | 3 lauriers, Awards, inclusions ; 0 avis | pages suites sans prix ni CTA ; « Contact » → home |
| Experimental Group | transactionnel multi-lieux | pilule « BOOK NOW » → tiroir Rooms / Tables / Wellness / Events | oui dans le moteur : calendrier €610–1 190/nuit ; offres £70–95 | Namastay overlay ; SevenRooms, Pure, Resy/Tock | header exclusion ; barre mobile 65 px | JSON-LD typés ; 0 avis | chambres sans m², capacité, prix ; chapitres vides |
| Soneva | transactionnel | « Book » (route hash muette) ; « Check availability » 139×49 sur villa | non | moteur azds non atteint ; formulaire 8 champs ; WhatsApp, WeChat, directeurs nommés | bandeau épinglé dans l'image de clôture | Best Price Guarantee, offres à pastilles ; 0 avis | « Book » ne navigue pas |
| Vipp Guesthouses | hybride via partenaire | aucun CTA sur liste / header ; « Book now » 333×52 sur la page maison à 2,7–3,6 viewports | oui : « From AUD $970 per night, 2 adults », « From EUR 400 per night » | Lodgify (même onglet) ou Planyo (nouvel onglet) selon la maison ; e-mail par maison | non | architecte, chiffres ; 0 avis | moteurs et devises hétérogènes ; pop-in sur la colonne prix |
| Pelorus Travel | conversationnel qualifié | « ENQUIRE » orange fixe sur 16/16 pages | oui sur cartes : « MAY-OCT • £125,000 PP » ; filtre budget | formulaire 10 champs (8 obligatoires, budget dès 40 000 £), 2 téléphones, Calendly ; 0 moteur | nav fixe ; disparaît au scroll interne | process 6 étapes, why 7 raisons, ~20 témoignages signés, 9 badges | pop-in + cookies non fermables ; pas d'humain nommé ni délai sur /enquire |

Enseignements série 2 : (1) les offres datées (expédition, croisière, sur mesure) affichent le prix et une méthode, les hôtels non ; (2) la demande qualifiée fonctionne quand elle est pré-remplie, en cartes, avec délai et humain ; (3) les erreurs mécaniques (dates codées, devises, moteurs différents, « Book » muet) détruisent la confiance plus que l'absence d'animation.

Enseignements : (1) le seul site où le prix est visible avant le moteur est la plateforme (Le Collectionist) ; les hôtels renvoient tous vers un moteur externe sans prix indicatif, ce qui est une perte de conversion évitable ; (2) l'onglet fixe (Borgo) et le widget fixe (Seagate) rendent la réservation toujours atteignable ; (3) le CTA « Request » (FORESTIS) crée une voie humaine parallèle au moteur ; (4) les ruptures d'identité vers SynXis / Marriott / eZee sont la faiblesse commune.

## 1. Choisir le mode de conversion (Indispensable)

| Mode | Quand | Action principale | Action secondaire | Ce que le site doit montrer avant le clic |
|---|---|---|---|---|
| **Transactionnel** | hôtel avec moteur, nuits vendables en ligne | Réserver (dates → chambres → paiement) | Demander / Appeler | prix « à partir de » par type, politique d'annulation, bénéfices directs |
| **Conversationnel** | villa, maison d'hôtes, domaine, séjours complexes, tarifs sur devis | Demander (formulaire court, WhatsApp, appel) | Voir les disponibilités (calendrier indicatif) | fourchette de prix, saisons, délai de réponse, qui répond |
| **Hybride** | chalet, wellness, collection, hôtels avec expériences sur mesure | Réserver ET Demander, hiérarchisés selon la page | — | idem transactionnel + conseiller nommé |

Règle : une seule action en bouton plein par écran ; l'autre en contour ou lien ; le verbe correspond à ce qui se passe après le clic.

## 2. Parcours et points de contrôle

| Parcours | Étapes | Contrôles (Indispensable) |
|---|---|---|
| A. Réservation | Accueil → Hébergements → Page hébergement → Moteur (dates, occupants) → Chambres/tarifs → Paiement → Confirmation | 3 clics max jusqu'à la page hébergement ; moteur pré-rempli (type, dates si saisies) ; conditions visibles avant paiement ; retour au site possible |
| B. Demande | Accueil → Hébergement ou Expérience → Formulaire court (dates, souplesse, personnes, message) ou canal direct → Accusé de réception avec délai et prénom | 4 à 6 champs max ; confirmation immédiate ; e-mail de suivi ; option d'appel |
| C. Inspiration | Destination / Expérience / Journal → Hébergement recommandé → A ou B | chaque page inspirante renvoie vers un hébergement et un CTA |
| D. Retour / fidélité | Offres → Bénéfices directs → Moteur avec code | offres datées, conditions claires |
| E. Cadeau | Bon cadeau → montant ou expérience → paiement | hors moteur principal, simple |

Mesurer : clics sur CTA par section, entrée dans le moteur, abandon par étape, part mobile, demandes qualifiées.

## 3. Emplacement et hiérarchie des CTA (Indispensable)

- **Header** : bouton plein « Réserver » (ou « Demander ») toujours visible ; sur mobile, bouton court ou barre basse.
- **Hero** : moteur (transactionnel) ou CTA principal + secondaire humain (« Écrire à Marie »).
- **Après les hébergements** : « Voir toutes les chambres » + « Vérifier les disponibilités ».
- **Page hébergement** : CTA sticky (desktop : encart latéral ; mobile : barre basse) avec prix.
- **Fin de page** : rappel de l'action + contact humain.
- **Onglet ou barre fixe** (Recommandé) : Borgo (onglet vertical), FORESTIS mobile (barre contact) ; ne jamais cumuler deux éléments fixes concurrents.

## 4. Formulations

| Contexte | À utiliser | À éviter |
|---|---|---|
| Explorer | Découvrir la suite, Voir les maisons, Explorer les expériences | En savoir plus, Cliquez ici |
| Vérifier | Voir les disponibilités, Vérifier les dates | Réserver (si le clic n'ouvre qu'un calendrier) |
| Réserver | Réserver, Réserver cette suite, Réserver du 12 au 15 mars | Booking, Go |
| Demander | Demander un séjour, Faire une demande, Échanger avec un conseiller, Planifier un appel | Contact (trop vague pour une demande de séjour) |
| Sans engagement | Sans frais, Annulation gratuite jusqu'au …, Réponse sous 24 h | Offre limitée, Dernière chance |

## 5. Sélection des dates et des voyageurs (Indispensable)

- Calendrier : 2 mois desktop, 1 mois mobile ; dates indisponibles grisées ; durée minimale indiquée ; prix par nuit dans les cases (Signature premium) ; sélection en 2 taps ; départ impossible avant arrivée.
- Voyageurs : adultes / enfants (âges), lits bébé ; « + / − » de 44 px ; total affiché.
- Villa / semaine : sélection par semaine (samedi à samedi) avec tableau des saisons (Le Collectionist : prix par semaine par période).
- Souplesse : « ± 3 jours » pour les modèles conversationnels.
- Vides : message + alternative (autres dates, autre hébergement, contact).

## 6. Accès aux chambres et informations disponibles

- Depuis la home : section hébergements avec 3 mises en avant + « toutes les chambres ».
- Depuis le menu : « Hébergements » ouvre la liste, pas un sous-menu de 12 entrées (Corazón liste 12 chambres dans un sous-menu caché : à éviter).
- Chaque hébergement : voir `accommodation-pages.md`. Minimum : nom, promesse, galerie, m², capacité, lits, vue, équipements groupés, prix « à partir de », conditions, CTA.
- Le moteur ne doit apporter que les dates, la disponibilité, le tarif exact et le paiement : tout le reste est sur le site.

## 7. Transparence et réassurance (Indispensable)

- Prix : « à partir de X € / nuit » par type, taxes et frais mentionnés ; saisons expliquées ; pour les villas, prix par semaine + frais (ménage, caution).
- Conditions : acompte, annulation, arrivée/départ, enfants, animaux, accessibilité PMR, parking.
- Bénéfices directs : 3 maximum, concrets (meilleur tarif, petit-déjeuner, surclassement selon disponibilité, annulation souple, accueil personnalisé) ; affichés à côté du CTA et dans le moteur.
- Preuve sociale : note + nombre d'avis + source + date ; 2–3 verbatims ; presse ; distinctions avec année.
- Sécurité : paiement sécurisé, données protégées, moteur officiel (mention « site officiel » utile quand des OTA reprennent le nom).
- Contact humain : prénom, photo, téléphone, WhatsApp, délai de réponse, horaires.

## 7 bis. Transparence tarifaire et méthode pour les offres complexes (série 2)

- **Cartes de produit daté** (Indispensable pour expéditions, croisières, retraites, sur mesure) : nom, saison ou dates, durée, « from » par personne ou par nuit, variante (camp, cabine), pastille d'offre, CTA « Détails » ; prix barré et prix par nuit si l'offre est remisée (Explora).
- **Grille tarifaire filtrable** (Recommandé) : par saison ou par année, variantes côte à côte, boutons « Dates », « En savoir plus », « Commencer à planifier » pré-rempli (White Desert `/enquire?itinerary=`).
- **« Comment ça marche »** (Indispensable pour toute offre > 5 000 € ou à logistique) : 4–6 étapes numérotées (demande, conseil, acompte, préparation, assurance, départ), accessible depuis toutes les pages d'offre (onglet ou lien fixe).
- **Auto-qualification** (Recommandé) : filtre par budget, budget obligatoire au formulaire quand le ticket est élevé (Pelorus : 40 000 £ ; Le Collectionist : 10 000 €/semaine), ticket d'entrée annoncé avant le formulaire.
- **Formulaire en cartes** (Recommandé) : saison, mois, intérêts en cartes cliquables puis coordonnées ; ≤ 10 champs ; humain nommé + délai (manquent chez Pelorus) ; reCAPTCHA invisible.
- **Adhésion comme conversion** (contexte club / communauté) : tarifs publics, contenu inclus, portail membres, CTA « Enquire » distinct de « Book » (Aethos).
- **Inclusions et exceptions** (Indispensable) : encadré « tout est inclus » répété + liste honnête des suppléments (Explora : 2 516 excursions payantes).

## 8. Services additionnels, conciergerie, offres

- Proposer les extras au bon moment : sur la page hébergement (« Ajoutez : transfert, chef, soin ») et dans le moteur (upsell), jamais en pop-up.
- Conciergerie : page dédiée + bloc sur chaque page hébergement ; périmètre réel, exemples, délai.
- Offres : page « Séjours » avec 3–6 offres datées, prix, inclus, CTA vers le moteur avec le code ; ne pas multiplier les bandeaux.
- Cadeaux : bon cadeau en 3 étapes ; visible dans le footer et le menu secondaire.

## 9. Moteur externe : traiter la rupture (Indispensable)

- Choisir un moteur personnalisable (logo, couleurs, police, textes) et l'aligner sur les tokens ; ajouter le lien « Retour au site ».
- Ouvrir dans le même onglet si le moteur est aligné ; sinon nouvel onglet avec mention « Le moteur de réservation sécurisé s'ouvre dans un nouvel onglet ».
- Passer les paramètres (dates, occupants, type, langue, devise, code) dans l'URL.
- Précharger la connexion (`preconnect`) ; tester la vitesse du moteur sur mobile.
- Mettre sur le site tout ce que le moteur affiche mal : photos, descriptions, conditions.
- Vérifier régulièrement que le moteur répond (le Marriott de Seagate refuse certains accès automatisés ; les clients derrière des proxys d'entreprise peuvent subir le même blocage).

## 10. Formulaires (demande, contact, newsletter)

- 4 à 6 champs : dates, personnes, hébergement souhaité (pré-rempli), message, e-mail, téléphone optionnel ; consentement RGPD ; pas de captcha visible (invisible ou honeypot).
- Label visible, aide, erreurs en ligne, bouton explicite (« Envoyer ma demande »), confirmation avec délai et prochaine étape, e-mail automatique.
- Mobile : champs 48–56 px, clavier adapté (`inputmode`), autocomplétion.

## 11. Mesure et optimisation

- Événements : clic CTA (par emplacement), ouverture du moteur, dates saisies, étape atteinte, demande envoyée, appel/WhatsApp.
- Tests A/B raisonnables : libellé du CTA, position du prix, ordre des hébergements, présence du bloc humain.
- Revue trimestrielle : abandon par étape, part mobile, pages d'entrée, recherche interne (collection).

## 11 bis. Erreurs mécaniques observées dans la série 2 (à contrôler en recette)

Dates, nuits ou devises codés en dur dans les liens vers le moteur (Odisej 2023, Habitas 2023–2024) ; « Book » qui ne navigue pas (Soneva) ; « Contact » qui renvoie à la home (Explora) ; moteur différent par maison avec onglets et devises hétérogènes (Vipp) ; formulaire de demande en anglais sur un site en espagnol (Mas Girbau) ; pop-up promo qui fige le scroll (Aethos) ; pop-in marketing sur la colonne de prix (Vipp) ; BOOK absent des pages de marque (Habitas) ; lien de staging dans le menu (Habitas) ; lien `?preview=yes` (Seagate).

## 12. Erreurs qui tuent la conversion (à bannir)

Pop-up à l'arrivée ; bandeau cookies plein écran ; deux CTA principaux de même poids ; « Réserver » qui ouvre un formulaire ; aucun prix avant le moteur ; moteur non responsive ; sous-menu de 12 chambres ; liens externes non signalés (boutique, restaurant sur d'autres domaines) ; menu de 20 entrées ; compte à rebours ; chat bot qui s'ouvre seul ; formulaire de 12 champs ; captcha visible ; absence de confirmation.
