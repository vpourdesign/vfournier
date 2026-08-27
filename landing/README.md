# VF Immobilier — landing page

**Client :** Vanessa Fournier inc., courtier immobilier, Royal LePage Urbain
**Livré par :** V pour Design, août 2026
**Source de vérité :** `DESIGN.md` **v2.0**, réextrait de la papeterie FINALE approuvée
(pancarte résidentielle, pancarte commerciale, carte de visite — PDF, août 2026).

## Contenu

```
DESIGN.md      design system (tokens, typo, composants, interdits)
index.html     la landing page complète, autonome, sans build, sans CDN
assets/        logos, portraits, bannière RLP (+ version crème pour les champs noirs), OG image, polices woff2, icônes SVG
               vanessa-1400/900      veston pâle, détouré (hero, crème)
               vanessa-robe-*        robe noire détourée depuis _O2A9447-blanc.jpg (Approche, crème)
               vanessa-noir-*        robe noire sur noir pur depuis _O2A9447.jpg (Évaluation, noir)
               fonts/                Montserrat 300/400/500/700/800 + Inter 300/400/500, auto-hébergés
```

## Alignement sur la papeterie finale

Les valeurs sont échantillonnées dans les PDF d'impression, pas approximées :

| | avant (maquettes) | maintenant (finales) |
|---|---|---|
| Crème | `#F7F3EE` | **`#F1EFEC`** |
| Accent | taupe `#A59D95` | **aucun** — duo-ton strict |
| Titres | Playfair Display | **Montserrat 300 / 800** (Gotham à l'impression) |
| Capitales | Jost | **Montserrat 500** |
| Hiérarchie | par le tracking | **par le contraste de graisse** |
| Titres sur noir | taupe | **crème `#F1EFEC`** |

**Lockup nom** : `VANESSA` en 300 au-dessus de `FOURNIER` en 800, collés, `inc.` en 400 —
la composition exacte des deux pancartes, rejouée dans chaque titre de section
(partie légère + partie en 800).

**Bandeau** : bande crème posée dans un champ noir, capitales noires centrées à `.34em` —
le « À VENDRE » de la pancarte commerciale. Deux usages : en-tête de la section Évaluation,
et `VFIMMOBILIER.COM` qui ferme la page, comme le bas des deux pancartes.

## Rythme duo-ton

Hero (crème) · En bref (noir) · Approche + portrait robe noire (crème) · Services (noir) ·
Calculatrice (crème) · Processus (bande `surface-2`) · Évaluation + formulaire + portrait (noir) ·
FAQ, Contact (crème) · Pied de page (noir) · bandeau de clôture (crème).

## Animation

- Transition entre sections : le fond de chaque section noire (et de la bande Processus) se déploie de haut en bas
  au défilement, `clip-path` piloté par **GSAP ScrollTrigger** (scrub, CDN cdnjs, `defer`). Sans GSAP ou sous
  `prefers-reduced-motion`, les fonds sont simplement pleins.
- L'en-tête bascule en noir (logo crème) quand il survole un champ noir.
- Révélations opacité + 24 px en IntersectionObserver, une seule fois, easing du système.
- Pas de three.js : rien à afficher en 3D ici, et la lib pèse ~600 Ko pour une page qui vise le SEO. Voir note de livraison.

## SEO / GEO

- `<title>`, meta description, canonical, OG/Twitter, `lang="fr-CA"`, `robots max-snippet`.
- JSON-LD `@graph` : `RealEstateAgent` + `Person` (BDC, knowsAbout, sameAs vers le profil Royal LePage) +
  `WebSite` + `WebPage` (`speakable`) + `FAQPage` (6 Q/R identiques au HTML).
- Bloc « En bref » et FAQ écrits en réponses courtes et factuelles, citables par les moteurs génératifs.
- Une seule `h1`, hiérarchie h2/h3 propre, texte réel dans le HTML (rien injecté par JS).
- Zéro dépendance externe : polices auto-hébergées, aucun CDN, aucun tracker (Loi 25). Reveal en IntersectionObserver.
- Portrait en `webp` préchargé, `fetchpriority="high"`, dimensions déclarées (pas de CLS).

## Calculatrice hypothécaire

Règle canadienne (composition semestrielle), fréquences mensuel / 2 semaines / 2 semaines accéléré / hebdo accéléré,
prime d'assurance prêt (4,00 % / 3,10 % / 2,80 % selon la mise de fonds), mise de fonds minimale (5 % / 10 % / 20 %),
plafond 25 ans sous 20 % de mise de fonds. Estimation seulement, avertissement affiché.

## Formulaire

Compatible **Netlify Forms** tel quel (`data-netlify`, honeypot `entreprise`, `action="/merci"`).
Sur un autre hébergeur : remplacer `action` par un endpoint (Formspree, Basin…). Si l'envoi échoue
(ex. ouverture locale), repli automatique sur un `mailto:` pré-rempli. Case de consentement obligatoire.

## Ce qui reste à faire

1. Créer la page `/merci` (ou changer `action`) selon l'hébergeur.
2. Logo Royal LePage Commercial : placeholder en pointillé dans le pied de page.
3. Valider avec Vanessa : territoires listés, chiffres (10 ans BDC, 24 h, 48 h), textes de FAQ.
5. **Polices** : Gotham (pancartes) et Garet / Boston Angel / Cormorant SC (carte) sont sous licence.
   Le web utilise Montserrat, substitut libre de Gotham — et déjà présent dans le PDF de la carte.
   Si Vanessa détient une licence web Gotham, la substitution se fait dans `@font-face` seul.
6. **Royal LePage Commercial** : le logo apparaît dans les PDF d'impression mais n'a jamais été
   fourni en fichier vectoriel isolé. À réclamer pour remplacer le placeholder du pied de page.
4. Analytics + Search Console (sans cookie tiers si possible) avant mise en ligne.
