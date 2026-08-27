---
version: 2.0
name: VF-Immobilier-design-system
client: Vanessa Fournier inc. — courtier immobilier, Royal LePage Urbain / Royal LePage Commercial
source: "Papeterie FINALE approuvée, août 2026 : pancarte résidentielle, pancarte commerciale, carte de visite (PDF)."
description: "Duo-ton strict. Un crème #F1EFEC et un noir #000, rien d'autre. La hiérarchie se joue par le contraste de graisse d'une seule famille géométrique (VANESSA léger / FOURNIER noir) et par l'inversion des champs, jamais par la couleur. Aucun accent chromatique, aucune ombre, aucun dégradé, aucun coin arrondi. Le rouge Royal LePage n'existe que dans le logo."

themes: [pale, fonce]

colors:
  # --- Thème PÂLE (pancarte résidentielle, carte de visite) ---
  canvas: "#F1EFEC"          # fond crème, échantillonné dans les deux pancartes
  surface-1: "#FFFFFF"       # cartouche blanc du logo Royal LePage, cartes
  surface-2: "#E7E4DF"       # bande calme
  ink-strong: "#000000"      # nom, téléphone, gros titres — noir pur imprimé
  ink: "#312F30"             # texte courant — l'encre de la carte de visite
  ink-muted: "#6B6866"
  hairline: "#D6D2CD"
  hairline-strong: "#B6B1AB"
  inverse-canvas: "#F1EFEC"  # NE SE SURCHARGE JAMAIS
  inverse-ink: "#000000"     # NE SE SURCHARGE JAMAIS
  # --- Thème FONCÉ (pancarte commerciale) ---
  dark-canvas: "#000000"
  dark-surface-1: "#0D0C0C"
  dark-ink-strong: "#F1EFEC"  # crème sur noir, jamais blanc pur
  dark-ink: "#D9D5D0"
  dark-ink-muted: "#A5A09B"
  dark-hairline: "#2B2928"
  # --- Marque partenaire (logo uniquement, jamais en UI) ---
  rlp-red: "#FF0000"

typography:
  families:
    display: Montserrat        # substitut libre de Gotham (pancartes) ; Montserrat est déjà dans le PDF de la carte
    body: Inter                # substitut de Roboto, le petit texte de la papeterie
  name-given:                  # « VANESSA »
    fontFamily: Montserrat
    fontWeight: 300
    fontSize: clamp(25px, 3.5vw, 47px)
    letterSpacing: 0.10em
    textTransform: uppercase
  name-family:                 # « FOURNIER »
    fontFamily: Montserrat
    fontWeight: 800
    fontSize: clamp(37px, 5.6vw, 76px)
    letterSpacing: -0.025em
    textTransform: uppercase
  display:                     # titres de section
    fontFamily: Montserrat
    fontWeight: 300            # la partie accentuée passe à 800
    fontSize: clamp(27px, 3.2vw, 44px)
    lineHeight: 1.16
  label:
    fontFamily: Montserrat
    fontWeight: 500
    fontSize: 10.5px
    textTransform: uppercase
    letterSpacing: 0.22em
  numeric:                     # téléphone, versement, chiffres de preuve
    fontFamily: Montserrat
    fontWeight: 800
    letterSpacing: -0.02em
  body:
    fontFamily: Inter
    fontWeight: 300
    fontSize: 17px
    lineHeight: 1.7

spacing:
  unit: 8px
  section-y: clamp(88px, 11vw, 176px)
  gutter: clamp(24px, 5vw, 80px)
  max-width: 1280px
  measure: 62ch

radii:
  default: 0px      # RÈGLE : l'UI est à angles vifs

motion:
  easing: cubic-bezier(0.22, 1, 0.36, 1)
  duration-fast: 280ms
  duration: 620ms
  reveal: "opacity 0→1 + translateY 24px→0"
  section: "le fond de chaque champ noir se déploie de haut en bas au défilement (clip-path, GSAP ScrollTrigger, scrub)"
  respect: prefers-reduced-motion
---

# VF Immobilier — DESIGN.md v2.0

Système extrait de la **papeterie finale approuvée** (août 2026) : pancarte
résidentielle, pancarte commerciale, carte de visite.

> **Ce qui a changé depuis la v1.0.** La v1.0 avait été extraite de maquettes de
> travail. Les finales approuvées tranchent autrement, et c'est elles qui font foi :
>
> | | v1.0 (maquettes) | v2.0 (finales approuvées) |
> |---|---|---|
> | Crème | `#F7F3EE` | **`#F1EFEC`** |
> | Accent | taupe `#A59D95` | **aucun** — le système est strictement duo-ton |
> | Titres | Playfair Display | **Montserrat 300 / 800** (Gotham à l'impression) |
> | Capitales | Jost | **Montserrat 500** |
> | Hiérarchie | par le tracking | **par le contraste de graisse** |
> | Sur fond noir | titres taupe | **titres crème `#F1EFEC`** |
>
> Le serif ne survit que dans le monogramme VF de la carte de visite
> (Cormorant SC à l'impression), livré en SVG vectorisé : aucune police à charger.

## Le principe

Deux couleurs, une famille, deux graisses. C'est tout.

1. **L'inversion.** Le crème et le noir alternent en champs pleins. Un champ noir
   n'est pas une « section foncée » décorative : c'est la pancarte commerciale.
2. **La graisse.** `VANESSA` léger au-dessus de `FOURNIER` noir. Ce contraste,
   et lui seul, porte la hiérarchie — dans le lockup, dans les titres, dans les
   chiffres. Jamais par la couleur.
3. **Le bandeau.** Une bande crème posée dans un champ noir, capitales noires très
   trackées et centrées — le « À VENDRE » de la pancarte commerciale, et le
   `VFIMMOBILIER.COM` qui ferme les deux pancartes.

## Composants

### `name-lockup` — le lockup nom
Deux lignes collées (`line-height: .92`) : le prénom en 300 légèrement rentré,
le patronyme en 800 à fleur de marge, `inc.` en 400 taille .26em collé au `R`.
Sous le lockup, le titre professionnel en capitales trackées, puis un filet 1px
pleine largeur. C'est la composition des deux pancartes.

### `band` — le bandeau
Fond `--inverse-canvas`, texte `--inverse-ink`, Montserrat 500, `letter-spacing: .34em`,
centré. Ne s'emploie **que** posé dans un champ noir, jamais sur crème (il y
disparaîtrait). Deux usages : en-tête d'un champ noir, et clôture de page.

### `btn`
- **Primaire** : fond `--ink-strong`, texte **blanc** `--surface-1`. Survol : fond `--ink`.
- **Fantôme** : filet 1px `--ink`. Survol : se remplit d'encre, texte blanc.
- Sur champ noir, le primaire s'inverse en `--inverse-canvas` / `--inverse-ink`.
- Zone tactile minimale 48px. Libellés en Montserrat 600, `.22em`.

### `phone` — le numéro
Montserrat 800, `-.02em`, `tabular-nums`. C'est le deuxième plus gros élément de
la page après le lockup, comme sur la pancarte. Toujours cliquable (`tel:`).

### `card`
Fond `--surface-1`, angles vifs, aucune ombre. Les gouttières 1px de la grille sur
fond `--hairline` **sont** les séparateurs. Survol : `translateY(-4px)`, rien d'autre.

## Grille & mise en page

Conteneur 1280px, gouttières `clamp(24px, 5vw, 80px)`, rythme vertical `section-y`
sans exception, mesure de lecture 62ch.

**Composition signature** : texte à gauche, portrait détouré à droite débordant le
bas de la section. C'est la pancarte, rejouée en hero.

## Photographie

Deux portraits, appariés au champ :

| Champ | Portrait | Fichier |
|---|---|---|
| Crème | veston pâle, détouré | `vanessa-1400/900.webp` |
| Crème | robe noire, détourée | `vanessa-robe-1400/900.webp` |
| Noir | robe noire sur noir pur | `vanessa-noir-1400/900.webp` |

Jamais de cadre, jamais de médaillon rond, aucun filtre, aucune vignette.
La photo touche le bord bas de sa section.

## Marque partenaire — Royal LePage

Bannière obligatoire au pied de page, hauteur ≥ 64px : **Royal LePage Urbain** avec
la mention « Agence immobilière · Franchisée indépendante et autonome », puis un
filet vertical, puis **Royal LePage Commercial**. Sur champ noir, utiliser
`rlp-urbain-agence-blanc.png` (neutres inversés en crème, rouge intact).

Le rouge `#FF0000` reste **strictement dans le logo**. Jamais un bouton, un lien,
une bordure ni un fond.

> ⚠️ **En attente client** : les fichiers Royal LePage Commercial n'ont toujours pas
> été fournis en vectoriel. Ils apparaissent dans les PDF d'impression mais pas en
> fichier isolé. Placeholder en pointillé dans le pied de page.

## Interdits

- Aucun accent chromatique. Le système a **deux** couleurs.
- Aucune ombre portée, aucun `box-shadow`, aucun dégradé, aucune texture.
- Aucun coin arrondi dans l'UI.
- Aucun serif hors du monogramme VF.
- Aucune graisse intermédiaire pour créer de la hiérarchie : 300 ou 800, pas 600.
- Aucune puce décorative, aucun emoji, aucun chevron ornemental.
- Aucun superlatif non prouvable (« le meilleur », « n°1 »).
- Blanc pur `#FFF` et noir pur `#000` : le noir est permis (c'est celui de la
  pancarte), le blanc ne sert que de surface de carte et de texte sur bouton noir.

## Contenu

Français du Québec (`fr-CA`), « je » pour Vanessa, « vous » pour le client, jamais
« nous ». Ton direct, factuel, phrases courtes. Titres en casse de phrase terminés
par un point. Espaces insécables devant `?`, `!`, `:`, `;` et dans les nombres.

- Nom : Vanessa Fournier inc.
- Titre exact (pancarte) : **Courtier immobilier commercial et résidentiel**
- Positionnement : **Investir. Acheter. Vendre. Avec stratégie.**
- Téléphone : 514 816-5798 · Courriel : info@vfimmobilier.com · Site : vfimmobilier.com
- Bannière : Royal LePage Urbain, agence immobilière franchisée indépendante et autonome

## Accessibilité

WCAG 2.1 AA. Focus visible : contour 2px `--ink-strong`, offset 3px. Toute animation
coupée sous `prefers-reduced-motion`. Langue `fr-CA`. Le passage des libellés du
taupe `#A59D95` (2.2:1) au neutre `#6B6866` (5.4:1) fait gagner le système en
lisibilité au passage de la v1.0 à la v2.0.

---

*Extrait de la papeterie finale VF Immobilier (août 2026) par V pour Design.
Source de vérité du design — toute page ou visuel VF se génère à partir de ce fichier.*
