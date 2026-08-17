# VF Immobilier — site one-pager

**Client :** Vanessa Fournier inc. — courtier immobilier, Royal LePage Urbain
**Livré par :** V pour Design — août 2026

## Contenu

```
DESIGN.md      ← source de vérité du design system (tokens, typo, composants, interdits)
index.html     ← le site complet, autonome, aucune dépendance de build
assets/
  logo-vf.svg           lockup complet, thème pâle (contours vectorisés)
  logo-vf-dark.svg      lockup complet, thème foncé
  logo-vf-mono.svg      lockup en currentColor (recolorable en CSS)
  logo-vf-mark.svg      VF + IMMOBILIER seuls — en-tête, favicon
  favicon.svg
  vanessa-1400.webp     photo détourée, desktop
  vanessa-900.webp      photo détourée, mobile
  vanessa-900.jpg       fallback (composité sur crème)
  og-vf-immobilier.jpg  image de partage 1200×630
  rlp-urbain-agence.png Royal LePage Urbain + mention d'agence (détouré)
  rlp-urbain.png        Royal LePage Urbain seul (détouré)
  fonts/                Playfair Display, Jost, Inter — woff2 auto-hébergés
```

## Mise en ligne

Aucun build. Déposer le dossier tel quel sur n'importe quel hébergeur statique
(Netlify, Cloudflare Pages, OVH, o2switch). Point d'entrée : `index.html`.

## Ce qui reste à faire

1. **Logos Royal LePage Commercial** — placeholder en pointillé dans le pied de page.
   Remplacer `.brokerage__pending` par un `<img>` dès réception des fichiers.
2. **Version foncée** — les tokens existent déjà (`[data-theme="dark"]`, déjà utilisé
   sur la section Évaluation). Basculer tout le site = poser `data-theme="dark"` sur
   `<html>`. Rien d'autre à toucher : aucune couleur n'est écrite en dur.
3. **Contenu à valider avec Vanessa** — les chiffres de la section preuve (3 secteurs,
   2 bannières, 24 h) et les textes de services sont des propositions.
4. **Formulaire** — le CTA Évaluation ouvre un `mailto:`. À brancher sur un vrai
   formulaire (Formspree, Netlify Forms) si on veut du tracking.
5. **Analytics + Search Console** avant mise en ligne.

## Notes techniques

- Polices auto-hébergées (aucun appel Google Fonts) — RGPD/Loi 25 propre.
- GSAP + ScrollTrigger + Lenis via CDN, avec dégradation gracieuse : si les scripts
  ne chargent pas, le contenu s'affiche quand même.
- `prefers-reduced-motion` respecté.
- Données structurées `RealEstateAgent` (schema.org) dans le `<head>`.
- Poids total du site : ~1,1 Mo (dont 640 Ko de polices et d'images).
