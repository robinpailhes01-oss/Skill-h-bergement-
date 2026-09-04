# Template — Sitemap et parcours

> Adapter au blueprint du modèle d'hébergement (voir `references/homepage-blueprints.md`). Règle : chaque page a un objectif unique, un CTA principal, et l'accès au moteur/à la demande reste à un clic depuis n'importe où (header persistant).

## 1. Sitemap (arbre)

```
/ (Accueil)
├── /hebergements (liste)              ← objectif : choisir un hébergement
│   ├── /hebergements/<nom>            ← objectif : projeter + réserver ce type
│   └── … (1 page par type, jamais de page unique « Chambres » si > 3 types)
├── /experiences (liste)               ← objectif : prouver la promesse, vendre le lieu
│   └── /experiences/<nom>             ← optionnel : uniquement si l'expérience est réservable ou signature
├── /restaurant | /table | /bar        ← objectif : désir + réservation de table
├── /spa | /wellness                   ← objectif : désir + réservation de soin
├── /histoire | /maison | /a-propos    ← objectif : confiance, personnes, valeurs
├── /destination | /alentours          ← objectif : SEO + réassurance sur le lieu
├── /offres | /sejours                 ← objectif : conversion directe, packages
├── /evenements | /mariages | /seminaires ← optionnel selon activité
├── /galerie                           ← optionnel ; préférer des galeries dans chaque page
├── /journal | /carnet                 ← optionnel ; SEO et vie de la marque
├── /contact (+ accès, plan, FAQ)      ← objectif : contact humain, itinéraire
├── /cadeaux | /bons                   ← optionnel
├── /reservation (moteur intégré ou passerelle)
└── légal : /mentions-legales, /confidentialite, /cgv, /cookies, /accessibilite
```

Variante **collection / conciergerie** :
```
/ → /destinations/<destination> → /maisons/<maison> → /demande (ou panier)
/collections/<collection>  /conciergerie  /inspiration  /proprietaires  /agences  /a-propos  /contact
```

Variante **villa unique / chalet unique** : site en 5 à 7 pages ; la page « maison » est la page centrale (plans, pièces, saisons, tarifs, calendrier), pas la home.

## 2. Tableau des pages

| Page | URL | Objectif unique | Persona prioritaire | Contenu clé | CTA principal | CTA secondaire | Preuves | Priorité (P1/P2/P3) |
|---|---|---|---|---|---|---|---|---|
| Accueil | / | | | | | | | P1 |
| Hébergements | | | | | | | | P1 |
| Hébergement — type 1 | | | | | | | | P1 |
| Expériences | | | | | | | | P1 |
| Restaurant | | | | | | | | P2 |
| Spa | | | | | | | | P2 |
| Histoire | | | | | | | | P2 |
| Offres | | | | | | | | P1 |
| Contact & accès | | | | | | | | P1 |

## 3. Navigation

- **Menu principal** (5 à 7 entrées maximum, verbes ou noms courts, dans l'ordre du parcours : Hébergements → Expériences → Table → Spa → Maison → Offres → Contact).
- **Actions persistantes** (header) : Réserver (ou Demander), langue, téléphone/WhatsApp sur mobile.
- **Menu secondaire / footer** : presse, carrières, cadeaux, propriétaires, mentions, réseaux, newsletter.
- **Fil d'Ariane** sur les pages de niveau 2 et 3.

## 4. Parcours principaux

### Parcours A — Réservation directe (transactionnel)
Entrée (SEO / campagne / bouche à oreille) → Accueil (promesse en 5 s) → Hébergements (comparaison visuelle) → Page hébergement (projection + tarif indicatif + dates) → Moteur (dates, occupants, tarifs, conditions) → Confirmation.
Points de contrôle : 3 clics max jusqu'à la page hébergement ; moteur pré-rempli avec le type choisi ; conditions visibles avant paiement.

### Parcours B — Demande qualifiée (conversationnel)
Entrée → Accueil → Maison / Expériences → Page hébergement → Formulaire court (dates, personnes, message) ou WhatsApp/appel → Réponse humaine sous X h (promesse affichée).

### Parcours C — Inspiration → décision
Entrée sur une page destination / expérience / journal → preuve du lieu → hébergement recommandé → Parcours A ou B.

### Parcours D — Retour / fidélité
Offres → Bénéfices directs → Moteur avec code ou offre pré-sélectionnée.

## 5. Règles de profondeur

- Aucune page utile au-delà du niveau 3.
- Toute page « liste » propose un filtre ou un tri uniquement si > 6 éléments.
- Toute page de niveau 3 renvoie vers 2 à 3 pages sœurs (hébergements complémentaires, expériences liées).
