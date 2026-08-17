---
version: 1.0
name: VF-Immobilier-design-system
client: Vanessa Fournier inc. — courtier immobilier, Royal LePage Urbain / Royal LePage Commercial
description: "Système éditorial calme et haut de gamme construit sur un fond crème #F7F3EE, une encre gris chaud #4D4D4D et un unique accent taupe #A59D95. Le langage vient direct de la papeterie : un monogramme VF en didone (Playfair Display), des mots-clés en capitales très trackées flanqués de filets fins, et beaucoup de silence autour. Aucun aplat de couleur, aucune ombre portée, aucun dégradé. Le rouge Royal LePage n'existe que dans le logo de la bannière — jamais dans l'interface. La hiérarchie se joue par l'échelle typographique et le tracking, pas par le poids ni la couleur."

themes: [pale, fonce]

colors:
  # --- Thème PÂLE (défaut, web + carte d'affaires + pancarte) ---
  canvas: "#F7F3EE"          # fond principal — crème
  surface-1: "#FFFFFF"       # cartes, panneaux surélevés
  surface-2: "#F0EBE4"       # bandes alternées, zones calmes
  ink: "#4D4D4D"             # texte principal (VF, IMMOBILIER, titres)
  ink-strong: "#1A1A1A"      # noir de pancarte — chiffres, nom sur visuels imprimés
  ink-muted: "#6E6862"       # texte courant long
  accent: "#A59D95"          # texte secondaire, filets, labels — l'accent unique
  accent-deep: "#8A8078"     # accent sur fond clair quand AA est requis (texte < 18px)
  hairline: "#DCD5CC"        # traits de séparation 1px
  hairline-strong: "#C4BBB0"
  inverse-canvas: "#F7F3EE"  # NE SE SURCHARGE JAMAIS — bouton clair sur bloc foncé
  inverse-ink: "#1A1A1A"     # NE SE SURCHARGE JAMAIS — texte sur ce bouton
  # --- Thème FONCÉ (pancarte foncée, section contact, futur dark mode) ---
  dark-canvas: "#000000"
  dark-surface-1: "#141210"
  dark-ink: "#FFFFFF"
  dark-ink-muted: "#CFC8C0"
  dark-accent: "#A59D95"
  dark-hairline: "#2E2A26"
  # --- Marque partenaire (usage logo uniquement, jamais en UI) ---
  rlp-red: "#FF0000"

typography:
  monogram:
    fontFamily: Playfair Display
    fontWeight: 500
    letterSpacing: 0.02em
    usage: "Uniquement VF. Jamais pour du texte courant."
  display-xl:
    fontFamily: Playfair Display
    fontSize: clamp(44px, 6.2vw, 92px)
    fontWeight: 400
    lineHeight: 1.06
    letterSpacing: -0.015em
  display-lg:
    fontFamily: Playfair Display
    fontSize: clamp(32px, 4vw, 56px)
    fontWeight: 400
    lineHeight: 1.12
    letterSpacing: -0.01em
  headline:
    fontFamily: Playfair Display
    fontSize: clamp(24px, 2.4vw, 34px)
    fontWeight: 400
    lineHeight: 1.2
  label:
    fontFamily: Jost
    fontSize: 12px
    fontWeight: 400
    textTransform: uppercase
    letterSpacing: 0.28em
    usage: "Sur-titres de section, nav, tags. TOUJOURS flanqué ou suivi d'un filet."
  label-lg:
    fontFamily: Jost
    fontSize: clamp(15px, 1.6vw, 20px)
    fontWeight: 400
    textTransform: uppercase
    letterSpacing: 0.22em
    usage: "COURTIER IMMOBILIER · COMMERCIAL & RÉSIDENTIEL sous le nom."
  name-lockup:
    fontFamily: Inter
    fontSize: clamp(30px, 5vw, 64px)
    fontWeight: 300
    textTransform: uppercase
    letterSpacing: 0.14em
    usage: "VANESSA FOURNIER — le lockup nom, repris de la pancarte."
  body-lg:
    fontFamily: Inter
    fontSize: 19px
    fontWeight: 300
    lineHeight: 1.65
  body:
    fontFamily: Inter
    fontSize: 17px
    fontWeight: 300
    lineHeight: 1.7
  body-sm:
    fontFamily: Inter
    fontSize: 15px
    fontWeight: 400
    lineHeight: 1.6
  numeric:
    fontFamily: Inter
    fontWeight: 500
    letterSpacing: -0.01em
    usage: "Téléphone, chiffres de preuve. Le numéro est un élément de design, pas une note de bas de page."

spacing:
  unit: 8px
  scale: [4, 8, 12, 16, 24, 32, 48, 64, 96, 128, 176]
  section-y: clamp(88px, 11vw, 176px)
  gutter: clamp(24px, 5vw, 80px)
  max-width: 1280px
  measure: 62ch

radii:
  none: 0px
  sign: 18px        # coin de pancarte — usage visuel imprimé seulement
  pill: 999px
  default: 0px      # RÈGLE : l'UI est à angles vifs

motion:
  easing: cubic-bezier(0.22, 1, 0.36, 1)
  duration-fast: 240ms
  duration: 620ms
  reveal: "opacity 0→1 + translateY 24px→0, stagger 90ms"
  respect: prefers-reduced-motion
---

# VF Immobilier — DESIGN.md

Système de design de la marque **Vanessa Fournier inc.**, extrait de la papeterie
existante (carte d'affaires, pancarte résidentielle, pancarte commerciale) et
étendu au web.

## Le principe

> Une courtière qui vend du commercial et de l'industriel ne se vend pas comme
> une courtière résidentielle. Le système doit lire **conseil**, pas **vente**.

Trois leviers, et rien d'autre :

1. **Le silence.** Le blanc tournant est le composant le plus important. Aucune
   section ne dépasse 62ch de mesure de lecture.
2. **Le tracking.** La hiérarchie secondaire passe par l'espacement des lettres
   en capitales, jamais par le gras ni la couleur.
3. **Le filet.** Un trait de 1 à 2px, taupe, flanque ou souligne les libellés.
   C'est la seule ornementation autorisée du système.

## Tokens

Tous les tokens vivent en variables CSS sur `:root`. Le thème foncé est un
override de bloc (`[data-theme="dark"]`) — **aucune couleur n'est écrite en dur
dans un composant.** C'est ce qui rend la version foncée gratuite.

```css
:root {
  --canvas: #F7F3EE;  --surface-1: #FFFFFF;  --surface-2: #F0EBE4;
  --ink: #4D4D4D;     --ink-strong: #1A1A1A; --ink-muted: #6E6862;
  --accent: #A59D95;  --accent-deep: #8A8078;
  --hairline: #DCD5CC;
  --inverse-canvas: #F7F3EE; --inverse-ink: #1A1A1A;  /* jamais surchargés */
}
[data-theme="dark"] {
  --canvas: #000000;  --surface-1: #141210;  --surface-2: #0B0A09;
  --ink: #FFFFFF;     --ink-strong: #FFFFFF; --ink-muted: #CFC8C0;
  --accent: #A59D95;  --accent-deep: #A59D95;
  --hairline: #2E2A26;
}
```

### Règle de contraste (non négociable)

`#A59D95` sur `#F7F3EE` donne **~2.2:1** — insuffisant pour du texte. L'accent
taupe est autorisé pour : les filets, les capitales trackées ≥ 16px en usage
décoratif, et les icônes. Pour tout texte porteur d'information sur fond crème,
utiliser `--accent-deep` (#8A8078, ~3.4:1) minimum, ou `--ink`. Sur fond noir,
`#A59D95` passe à ~7:1 et redevient utilisable partout.

## Typographie

| Rôle | Famille | Pourquoi |
|---|---|---|
| Monogramme VF | **Playfair Display** 500 | Didone à fort contraste, calque du logo existant |
| Titres | **Playfair Display** 400 | Prolonge le monogramme sans le répéter |
| Capitales trackées | **Jost** 400 | Géométrique type Futura — c'est la typo de `IMMOBILIER` |
| Texte courant + nom | **Inter** 300/400 | Grotesque neutre, la typo de `VANESSA FOURNIER` sur pancarte |

Pas de quatrième famille. Pas d'italique. Pas de gras au-delà de 500.

## Composants

### `logo` — le lockup
Trois variantes livrées en SVG (contours vectorisés, aucune dépendance de police) :
`logo-vf.svg` (pâle), `logo-vf-dark.svg` (foncé), `logo-vf-mono.svg` (`currentColor`),
`logo-vf-mark.svg` (VF + IMMOBILIER seuls, pour l'en-tête et le favicon).
Zone de protection = la hauteur du `V`. Taille minimale du lockup complet : 180px de large.

### `eyebrow` — sur-titre de section
Capitale trackée `label` en `--accent-deep`, précédée d'un filet de 48px.
**Jamais de puce, de point, ni de pilule autour.**

### `rule` — le filet
1px `--hairline`. En version « flanquante » (comme dans le logo) : 2px `--accent`,
longueur fixe, aligné sur la médiane des capitales.

### `stat` — la preuve chiffrée
Nombre en `display-lg` Playfair, libellé en `label`. Séparés par un filet vertical.
Aucun cadre, aucun fond.

### `card-service`
Fond `--surface-1`, angles vifs, filet 1px `--hairline`. Au survol : le filet passe
à `--accent`, translation Y de -4px. Aucune ombre — jamais.

### `btn`
- **Primaire** : fond `--ink-strong`, texte `--canvas`, angles vifs, padding 18/40,
  `label` tracké. Survol : fond `--accent-deep`.
- **Secondaire** : transparent, filet 1px `--ink`, texte `--ink`.
- **Sur bloc `[data-theme="dark"]`** : le primaire s'inverse en `--inverse-canvas` /
  `--inverse-ink`. Ne jamais utiliser `--canvas` ici — il vaut #000 dans le thème
  foncé et le bouton disparaîtrait.
- Zone tactile minimale 48px.

### `phone` — le numéro
Le 514 816-5798 est traité comme un élément de design (voir pancarte) :
`Inter 500`, échelle `display-lg`, `--ink-strong`. Toujours cliquable (`tel:`).

## Grille & mise en page

- Conteneur 1280px, gouttières fluides `clamp(24px, 5vw, 80px)`.
- Grille 12 colonnes desktop / 6 tablette / 1 mobile.
- **Composition signature** : texte à gauche sur 6–7 colonnes, photo détourée à
  droite débordant le bas de la section. C'est la composition de la pancarte —
  on la rejoue en hero.
- Rythme vertical : `section-y` partout, sans exception.

## Photographie

Portraits **détourés sur crème**, jamais en cadre ni en médaillon rond. La photo
touche le bord bas de sa section (elle « se tient dans » la page). Aucun filtre,
aucune vignette. Assets : `vanessa-1400.webp` / `vanessa-900.webp` (+ fallback PNG),
alpha propre, décontaminés du halo blanc.

## Marque partenaire — Royal LePage

Obligation de bannière : le logo **Royal LePage Urbain** avec la mention
« Agence immobilière · Franchisée indépendante et autonome » apparaît dans le pied
de page, à hauteur ≥ 64px. Le logo **Royal LePage Commercial** se place à sa droite,
séparé par un filet vertical (c'est la disposition de la papeterie).

> ⚠️ **En attente client** : les fichiers Royal LePage Commercial n'ont pas encore
> été fournis. Placeholder en place dans le pied de page, à remplacer.

Le rouge `#FF0000` de la bannière reste **strictement dans le logo**. Il ne devient
jamais une couleur d'interface, de bouton, ni de lien.

## Interdits (règles anti-clutter)

- Aucune ombre portée, aucun `box-shadow`, aucun dégradé de fond.
- Aucun coin arrondi dans l'UI (le `radius: sign` est réservé aux visuels imprimés).
- Aucune puce décorative, aucun « chip » de branding, aucun sur-titre à point coloré.
- Aucun pied de page du type « VF IMMOBILIER — 2026 / VOTRE PARTENAIRE ».
- Aucune icône pleine — traits 1.25px uniquement.
- Pas plus d'un accent chromatique par écran.
- Pas de superlatif non prouvable dans le contenu (« le meilleur », « n°1 »).

## Accessibilité

Cible **WCAG 2.1 AA**. Focus visible : contour 2px `--ink-strong` avec offset 3px.
Toute animation est désactivée sous `prefers-reduced-motion`. Le numéro de téléphone
et le courriel sont des liens natifs. Langue du document : `fr-CA`.

## Contenu de référence

- Nom : Vanessa Fournier inc.
- Titre : Courtier immobilier — commercial & résidentiel
- Positionnement : **Investir. Acheter. Vendre. Avec stratégie.**
- Portée : Commercial · Industriel · Résidentiel
- Téléphone : 514 816-5798 · Courriel : info@vfimmobilier.com · Site : vfimmobilier.com
- Bannière : Royal LePage Urbain, agence immobilière franchisée indépendante et autonome

---

*Extrait de la papeterie VF Immobilier (avril 2026) par V pour Design. Format :
[DESIGN.md](https://stitch.withgoogle.com/docs/design-md/overview/). Source de
vérité du design — toute page ou visuel VF se génère à partir de ce fichier.*
