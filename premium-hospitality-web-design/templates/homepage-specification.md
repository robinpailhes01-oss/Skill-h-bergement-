# Template — Spécification de la page d'accueil

> Une ligne par section, dans l'ordre d'affichage. Chaque section a un objectif unique, un contenu, une interaction, un CTA (ou aucun, volontairement) et une émotion cible. Renseigner desktop ET mobile. Voir `references/homepage-blueprints.md` pour l'ordre recommandé par modèle et `references/motion-guidelines.md` pour les valeurs d'animation.

## 0. Cadre

- Modèle d'hébergement : 
- Mode de conversion : transactionnel / conversationnel / hybride
- Promesse en une phrase (sera le message du hero) :
- Objectif de la page : 
- KPI : taux de clic vers Hébergements, vers Réserver ; profondeur de scroll ; taux de rebond mobile.

## 1. Header persistant

| Élément | Desktop | Mobile | Comportement au scroll | Notes |
|---|---|---|---|---|
| Logo | | | | |
| Menu | | burger | | |
| CTA Réserver / Demander | | bouton ou barre basse | | |
| Langue / téléphone | | | | |
| Hauteur, fond, transparence sur hero, transition | | | | |

## 2. Sections

| # | Section | Objectif | Contenu (texte, médias) | Interaction / animation | CTA | Émotion cible | Desktop (layout) | Mobile (layout) | Source du contenu |
|---|---|---|---|---|---|---|---|---|---|
| 1 | Hero | Poser la promesse en 5 s | Titre ≤ 8 mots, sous-titre ≤ 20 mots, vidéo/photo, moteur ou CTA | | | | | | |
| 2 | Manifeste / intro | Dire pourquoi ce lieu | 40–80 mots + 1–3 images | | | | | | |
| 3 | Hébergements | Rendre l'offre concrète | 3–6 cartes : nom, promesse, capacité, prix « à partir de » | | | | | | |
| 4 | Expériences signature | Prouver l'expérience | 3–4 blocs image + titre + 20 mots | | | | | | |
| 5 | Table / Spa | Étendre le désir | image large + accroche | | | | | | |
| 6 | Preuve | Rassurer | avis, presse, récompenses, chiffres | | | | | | |
| 7 | Destination / accès | Ancrer dans le lieu | carte, temps de trajet, saisons | | | | | | |
| 8 | Offres / bénéfices directs | Déclencher | 2–3 offres, avantages directs | | | | | | |
| 9 | Contact humain | Ouvrir un canal | hôte, téléphone, WhatsApp, délai de réponse | | | | | | |
| 10 | Newsletter / journal | Retenir | 1 champ, promesse de contenu | | | | | | |
| 11 | Footer | Clore et orienter | plan, coordonnées, légal, réseaux, labels | | | | | | |

Règles : supprimer toute section sans objectif distinct ; jamais deux sections consécutives de même structure ; alterner pleine largeur et contenu centré ; une respiration (vide ≥ 120 px desktop / 72 px mobile) avant chaque changement de thème.

## 3. Textes (à livrer)

| Zone | Texte | Nombre de mots | Statut |
|---|---|---|---|
| Titre hero | | | |
| Sous-titre hero | | | |
| CTA hero | | | |
| Titre + texte manifeste | | | |
| Titres de sections | | | |
| Accroches hébergements (une par carte) | | | |
| CTA de chaque section | | | |
| Bloc preuve (3 verbatims ≤ 25 mots) | | | |

## 4. Médias (à livrer)

| Zone | Type | Ratio | Résolution min | Poids max | Alt | Statut |
|---|---|---|---|---|---|---|
| Hero desktop | vidéo mp4/webm + poster | 16:9 | 1920×1080 | 6 Mo (10 s) | | |
| Hero mobile | vidéo verticale ou photo | 9:16 / 4:5 | 1080×1920 | 3 Mo | | |
| Cartes hébergements | photo | 4:5 ou 3:2 | 1600 px | 250 Ko | | |
| Expériences | photo | 3:2 / 1:1 | 1600 px | 250 Ko | | |

## 5. Animations (résumé, détail dans motion-guidelines)

| Élément | Déclencheur | Effet | Durée | Easing | Mobile | Reduced motion |
|---|---|---|---|---|---|---|
| Hero titre | chargement | fondu + translation 16 px | 700 ms | ease-out expo | identique | opacité seule |
| Sections | entrée viewport 15 % | fondu + translation 24 px | 600 ms | ease-out | translation 12 px | aucun |
| Images | entrée viewport | révélation (clip ou scale 1.05→1) | 900 ms | ease-out | scale seul | aucun |
| Boutons | hover | fond/couleur | 250 ms | ease | tap state | identique |

## 6. Réservation

- Position du moteur (hero / sticky / modal / page dédiée) et champs (arrivée, départ, adultes, enfants, code).
- Pré-remplissage, calendrier, message d'indisponibilité, bénéfices directs affichés à côté du bouton.
- Rupture avec moteur externe : transition, cohérence visuelle, nouvel onglet ou non.

## 7. SEO

- Title (≤ 60 car.), meta description (≤ 155 car.), H1 unique, structure H2, données structurées (Hotel / LodgingBusiness, Offer, FAQ), canonical, hreflang, OG image.

## 8. Critères d'acceptation

- LCP mobile < 2,5 s ; CLS < 0,1 ; hero visible sans JS ; navigation clavier complète ; contrastes AA ; reduced motion respecté ; tous les CTA mesurés (événements analytics).
