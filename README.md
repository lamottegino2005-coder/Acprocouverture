# AC Couvreur — site vitrine

Site statique, **un seul fichier HTML** (CSS, JS et photos en base64 inclus).
Aucune dépendance, aucun build, aucun `node_modules`.

## Contenu du dépôt

```
.
├── index.html      ← le site complet
├── og.jpg          ← image de partage (Open Graph, 1200x630)
├── robots.txt
├── sitemap.xml
├── vercel.json     ← réécriture des URLs + en-têtes de sécurité
└── README.md
```

## Déploiement Vercel

1. Créer un dépôt GitHub et y pousser ces fichiers.
2. Vercel → **Add New… → Project** → importer le dépôt.
3. Framework Preset : **Other**. Build Command : *(vide)*. Output Directory : *(vide)*.
4. **Deploy**.

Aucune variable d'environnement, aucune commande de build.
`vercel.json` renvoie toutes les routes vers `index.html` : les URLs
propres (`/couverture`, `/couvreur-la-chaume`…) fonctionnent en accès direct
et depuis les résultats Google.

## Après la mise en ligne

1. Remplacer le domaine dans `CONFIG.domain` (en haut du `<script>` de `index.html`),
   dans `robots.txt` et dans `sitemap.xml`.
2. Renseigner `CONFIG.formEndpoint` (Web3Forms, Formspree…) pour activer le formulaire.
   Tant qu'il est vide, le formulaire l'indique clairement au visiteur.
3. Renseigner `CONFIG.email`, `CONFIG.hours`, `CONFIG.gbp` (fiche Google),
   `CONFIG.insurer` et `CONFIG.policyNumber` (mentions légales).
4. Soumettre `sitemap.xml` dans la Google Search Console.

## Numéros de téléphone

- **Principal : 06 59 30 49 50** — porte tous les boutons d'appel du site
  (header, hero, barre mobile, page urgence, CTA, footer).
- Secondaire : 02 55 56 48 63 — affiché sur les pages contact, urgence et dans le footer.
- Autre ligne : 06 81 96 41 80 — page contact uniquement.
  Mettre `CONFIG.phoneAlt` à `""` pour la retirer du site.

Tout se change dans `CONFIG`, en haut du `<script>` de `index.html`.

## Horaires

Affichés : **6h – 20h** (site + footer + page contact).

⚠️ `CONFIG.hoursDays` est encore vide : les horaires sont visibles par les visiteurs
mais **pas déclarés à Google**. Renseigner l'un de ces trois codes pour activer
les données structurées `openingHoursSpecification` :

- `"Mo-Su"` → tous les jours
- `"Mo-Sa"` → du lundi au samedi
- `"Mo-Fr"` → du lundi au vendredi

Les horaires doivent être identiques sur la fiche Google Business Profile.

## Informations à confirmer avant publication

- Nom commercial : le logo indique « AC PRO COUVERTURE », le site affiche « AC Couvreur ».
- SIRET, forme juridique, responsable de publication, hébergeur (mentions légales).
- Marques produits : Guard Industrie, Soprema, Onduline/Velux à valider.
- Photos manquantes : peinture intérieure, peinture extérieure, prises de vue drone.

Toutes les données modifiables sont regroupées en haut du script :
`CONFIG`, `SERVICES`, `GALLERY`, `AREAS`, `LOCAL`, `FAQ`, `PRODUCTS`, `ARTICLES`, `REVIEWS`.
