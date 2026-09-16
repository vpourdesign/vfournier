# Notes — VFOURNIER

> Auto-classé par Claude depuis le chat Cowork du projet.
> Convention : `_AGENCY/CTO/conventions/project-notes.md`

## 📅 Échéances

*(vide pour l'instant — ajoute "vendredi il faut envoyer X" et je classe)*

## ✅ À faire

- [ ] Faire approuver par la cliente la liste avant/après des textes modifiés en SEO (title, meta description, placeholder du formulaire, légende photo) (2026-09-10)
- [ ] Après mise en ligne : soumettre le sitemap dans Google Search Console + Bing Webmaster, et vérifier la redirection www → vfimmobilier.com (2026-09-10)
- [ ] Demander à la cliente les heures d'ouverture et confirmer l'adresse exacte pour ajouter les coordonnées géographiques au JSON-LD (non inventées pour l'instant) (2026-09-10)
- [ ] Créer / réclamer la fiche Google Business Profile — plus gros levier de référencement local, hors site (2026-09-10)
- [ ] Faire confirmer par la cliente le retrait du « inc. » aussi dans les mentions légales (© et texte de consentement), pas seulement dans le logo (2026-09-09)
- [ ] Faire confirmer l'adresse d'agence affichée : Royal LePage St-Donat, 416 rue Principale — alors que la bande « Agence » dit Royal LePage Urbain et Royal LePage Commercial (2026-09-09)
- [ ] Demander les photos de bâtisses en haute résolution (l'exemple Word fait 1432 px de large, recadré à 1092 px) (2026-09-09)
- [ ] Déployer sur Netlify une fois les corrections approuvées (2026-09-09)
- [ ] Après mise en ligne, demander à la cliente de retester sur son téléphone (bogue du menu invisible corrigé) (2026-09-16)

## 💭 Long shots

*(vide pour l'instant — "un jour on pourrait explorer ..." finit ici)*

## 📝 Notes client

- La cliente aime son kit noir sur fond foncé : les photos de bâtisses ont donc été placées dans une section noire (entre les territoires et la calculatrice), pas dans le beige.
- Elle trouvait les deux sections du bas « beige longtemps » → la FAQ passe en beige plus foncé (#E7E4DF), le contact reste crème.

## 🔍 Précisions

*(vide pour l'instant — données factuelles, comptes, accès, contexte)*

## ✓ Fait

- [2026-09-16] Corrections du courriel client : slogan COMMERCIAL · INDUSTRIEL · RÉSIDENTIEL du logo de l'entête en vrai texte, plus gros et net; courriel de l'entête visible jusqu'à 981 px (Processus et Questions cachés à la place entre 981 et 1180 px); stats « 10+ / Ans d'expérience… », « 3 / Commercial Industriel Résidentiel », « 360° / Analyse Négociation Stratégie »; photo résidentielle déplacée sous le formulaire d'évaluation, à côté de la bâtisse commerciale (section photos seule supprimée); logo Royal LePage Commercial crème au pied de page; Grand Montréal retiré du hero et Montréal retiré de la FAQ (page + JSON-LD). Bogue mobile corrigé : le menu hamburger fermé restait affiché en transparence par-dessus toute la page sous 980 px et bloquait tous les clics.
- [2026-09-10] Suppression de la section contact crème, redondante avec la section évaluation noire. L'adresse de l'agence et le lien vers les inscriptions ont été repris dans la section noire ; les liens « Contact » du menu et « Contactez-moi » des territoires pointent maintenant vers #evaluation.
- [2026-09-10] Menu hamburger mobile (jusqu'à 980 px) : panneau noir plein écran, six entrées numérotées, bouton d'évaluation, téléphone, courriel et réseaux sociaux. Correction au passage d'un décalage de mise en page de 400 px causé par la photo de la section approche qui ne réservait pas sa place.
- [2026-09-10] Photo de bâtisse commerciale intégrée en débord dans la section évaluation (à la place de la 3e photo de Vanessa), photo résidentielle seule dans la section « Des projets qui créent de la valeur ». Passe SEO : title et meta description raccourcis et géolocalisés, complément de H1 pour les moteurs, alt des photos, robots.txt et sitemap.xml. JSON-LD schema.org complet (RealEstateAgent, Person, Services, ImageObject, WebSite, WebPage, FAQPage) pour le référencement local et génératif.
- [2026-09-10] Header en beige foncé (plus de bascule en noir), textes agrandis (cartes services, territoires, FAQ, processus), dégagement ajouté avant la section contact, et signature « Stratégie web + logo V pour Design » ajoutée au pied de page, comme sur daynak.ca.
- [2026-09-09] Corrections client (Word) appliquées sur landing/ : entête (logo avec COMMERCIAL · INDUSTRIEL · RÉSIDENTIEL, courriel dans la nav), bande « en bref » en beige foncé + nouveau contenu, retrait du « inc. », titre sans « industriel », lien Voir mes propriétés vers la fiche courtier, nouveaux textes hero / approche / stats, cartes services renommées (Commercial, Industriel, Résidentiel) + « propriétaire occupant », nouveaux territoires (Rive-Nord & Laval, Laurentides, Lanaudière), section photos de bâtisses, FAQ réécrite en beige foncé, contact réécrit + adresse St-Donat, logo Royal LePage en noir et blanc, liens Facebook/Instagram/LinkedIn au pied de page, données structurées mises à jour.
