# Text Balance Utility

> Équilibrez automatiquement vos titres et textes courts pour une typographie harmonieuse et professionnelle

## 📋 Description

**Text Balance** est un utilitaire CSS moderne qui équilibre automatiquement les lignes de texte pour éviter les "orphelins" (mots seuls sur la dernière ligne) et créer des blocs de texte visuellement harmonieux. Particulièrement efficace pour les titres, sous-titres et citations où l'équilibre visuel est crucial.

### ✨ Caractéristiques principales

- ⚖️ **Équilibrage automatique** : Répartition intelligente des mots sur les lignes
- 🎯 **Optimisé pour les titres** : Idéal pour h1, h2, h3 et textes courts
- 📐 **Contrôle de largeur** : Limite la largeur pour une meilleure lisibilité
- 🔧 **Variables CSS** : Personnalisation de la largeur maximale
- ⚡ **Performance** : CSS natif, pas de JavaScript
- 📱 **Responsive** : Fonctionne sur tous les écrans
- 🎨 **Améliore le design** : Titres plus professionnels automatiquement

## 🚀 Installation

### Code SCSS

```scss
// _text-balance.scss

.text-balance {
  // Variables par défaut
  --max-width: 50ch; // Largeur maximale en caractères
  --text-align: left; // Alignement du texte

  // Propriété moderne pour équilibrer le texte
  text-wrap: balance;

  // Largeur maximale pour optimal balance
  max-inline-size: var(--max-width);

  // Alignement
  text-align: var(--text-align);

  // Fallback pour navigateurs non-compatibles
  @supports not (text-wrap: balance) {
    // On peut ajouter des ajustements si nécessaire
    // Par défaut, le texte s'affichera normalement
  }
}

// Variantes de largeur prédéfinies
.text-balance--narrow {
  --max-width: 30ch; // Titres courts
}

.text-balance--normal {
  --max-width: 50ch; // Standard (défaut)
}

.text-balance--wide {
  --max-width: 70ch; // Titres longs
}

.text-balance--full {
  --max-width: 100%; // Pleine largeur
}

// Variantes d'alignement
.text-balance--left {
  --text-align: left;
}

.text-balance--center {
  --text-align: center;
}

.text-balance--right {
  --text-align: right;
}

// Variantes par élément
.text-balance--heading {
  --max-width: 40ch;
  font-weight: 700;
  line-height: 1.2;
}

.text-balance--subheading {
  --max-width: 50ch;
  font-weight: 600;
  line-height: 1.4;
}

.text-balance--quote {
  --max-width: 60ch;
  font-style: italic;
  line-height: 1.6;
}

// Utilitaire pour désactiver le balance
.text-balance--off {
  text-wrap: wrap; // Retour au comportement normal
  max-inline-size: none;
}

// Version pour texte multiligne avec balance
.text-balance--multi {
  text-wrap: balance;
  max-inline-size: var(--max-width, 65ch);
  line-height: 1.6;
}
```

### Import dans votre projet

```scss
// Dans styles.scss
@import "utilities/text-balance";
```

## 💡 Utilisation de base

### Exemple 1 : Titre simple

```html
<h1 class="text-balance">
  Transformez votre business avec nos solutions innovantes
</h1>
```

**Sans text-balance** :

```
Transformez votre business avec nos solutions
innovantes
```

☹️ Mot orphelin "innovantes"

**Avec text-balance** :

```
Transformez votre business avec
nos solutions innovantes
```

✅ Équilibré visuellement

### Exemple 2 : Titre centré

```html
<h1 class="text-balance text-balance--center">
  Découvrez le futur du développement web moderne
</h1>
```

### Exemple 3 : Sous-titre avec largeur personnalisée

```html
<h2 class="text-balance" style="--max-width: 45ch">
  Solutions complètes pour entreprises ambitieuses
</h2>
```

### Exemple 4 : Citation

```html
<blockquote class="text-balance text-balance--quote">
  "Le design n'est pas seulement ce à quoi ça ressemble et ce que ça fait. Le
  design, c'est comment ça fonctionne."
</blockquote>
```

## 📊 Paramètres

| Variable       | Type    | Défaut | Description               |
| -------------- | ------- | ------ | ------------------------- |
| `--max-width`  | length  | `50ch` | Largeur maximale du texte |
| `--text-align` | keyword | `left` | Alignement du texte       |

### Valeurs courantes pour `--max-width`

```css
/* Basé sur caractères (recommandé) */
--max-width: 30ch; /* Titre court, punchy */
--max-width: 40ch; /* Titre standard h1 */
--max-width: 50ch; /* Titre long ou h2 */
--max-width: 60ch; /* Citation, lead paragraph */
--max-width: 70ch; /* Texte descriptif */

/* Basé sur pixels */
--max-width: 400px; /* Petit */
--max-width: 600px; /* Moyen */
--max-width: 800px; /* Large */

/* Pourcentage */
--max-width: 80%; /* Relatif au container */
--max-width: 100%; /* Pleine largeur */

/* Responsive */
--max-width: clamp(30ch, 50vw, 60ch); /* Fluide */
```

### Pourquoi utiliser "ch" (caractères) ?

```css
/* ✅ Recommandé : Basé sur caractères */
--max-width: 50ch;
/* Plus prévisible pour le texte */
/* 50ch ≈ 50 caractères de largeur */

/* ❌ Moins optimal : Basé sur pixels */
--max-width: 600px;
/* Peut être trop large ou trop étroit selon la taille de police */
```

## 📚 Exemples détaillés

### Exemple 1 : Hero section

```html
<section class="hero">
  <div class="container-fluid">
    <h1 class="text-balance text-balance--center text-balance--heading">
      Créez des expériences digitales exceptionnelles
    </h1>
    <p class="text-balance text-balance--center" style="--max-width: 60ch">
      Plateforme tout-en-un pour designers et développeurs modernes
    </p>
    <button class="btn-primary">Commencer gratuitement</button>
  </div>
</section>

<style>
  .hero {
    padding: 6rem 2rem;
    text-align: center;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
  }

  .hero h1 {
    font-size: clamp(2rem, 5vw, 4rem);
    margin-bottom: 1.5rem;
  }

  .hero p {
    font-size: 1.25rem;
    margin-bottom: 2rem;
    color: rgba(255, 255, 255, 0.9);
  }
</style>
```

### Exemple 2 : Section avec sous-titres

```html
<section class="features">
  <div class="container-fluid container-fluid--lg">
    <h2 class="text-balance text-balance--center text-balance--heading">
      Pourquoi choisir notre plateforme ?
    </h2>

    <div class="features-grid">
      <div class="feature-card">
        <div class="icon">⚡</div>
        <h3 class="text-balance">Performance exceptionnelle garantie</h3>
        <p>Optimisé pour la vitesse et l'efficacité maximale</p>
      </div>

      <div class="feature-card">
        <div class="icon">🔒</div>
        <h3 class="text-balance">Sécurité de niveau entreprise</h3>
        <p>Protection des données avec chiffrement de bout en bout</p>
      </div>

      <div class="feature-card">
        <div class="icon">📈</div>
        <h3 class="text-balance">Évolutivité sans limites</h3>
        <p>Grandit avec votre business, de startup à entreprise</p>
      </div>
    </div>
  </div>
</section>

<style>
  .features {
    padding: 6rem 2rem;
  }

  .features h2 {
    font-size: 2.5rem;
    margin-bottom: 4rem;
  }

  .features-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 3rem;
  }

  .feature-card {
    text-align: center;
  }

  .icon {
    font-size: 3rem;
    margin-bottom: 1rem;
  }

  .feature-card h3 {
    font-size: 1.5rem;
    margin-bottom: 1rem;
  }
</style>
```

### Exemple 3 : Témoignages / Citations

```html
<section class="testimonials">
  <div class="container-fluid container-fluid--lg">
    <h2 class="text-balance text-balance--center">Ce que disent nos clients</h2>

    <div class="testimonial-grid">
      <blockquote class="testimonial">
        <p class="text-balance text-balance--quote">
          "Cette plateforme a complètement transformé notre façon de travailler.
          L'efficacité et la simplicité sont incroyables."
        </p>
        <footer>
          <img src="avatar1.jpg" alt="Sophie Martin" />
          <div>
            <strong>Sophie Martin</strong>
            <span>CEO, TechCorp</span>
          </div>
        </footer>
      </blockquote>

      <blockquote class="testimonial">
        <p class="text-balance text-balance--quote">
          "Un outil indispensable pour toute équipe moderne qui veut rester
          compétitive et innovante."
        </p>
        <footer>
          <img src="avatar2.jpg" alt="Thomas Leroux" />
          <div>
            <strong>Thomas Leroux</strong>
            <span>CTO, StartupXYZ</span>
          </div>
        </footer>
      </blockquote>

      <blockquote class="testimonial">
        <p class="text-balance text-balance--quote">
          "Le meilleur investissement que nous ayons fait cette année. ROI
          positif dès le premier mois."
        </p>
        <footer>
          <img src="avatar3.jpg" alt="Marie Dubois" />
          <div>
            <strong>Marie Dubois</strong>
            <span>Directrice Marketing</span>
          </div>
        </footer>
      </blockquote>
    </div>
  </div>
</section>

<style>
  .testimonials {
    padding: 6rem 2rem;
    background: #f9fafb;
  }

  .testimonials h2 {
    font-size: 2.5rem;
    margin-bottom: 4rem;
  }

  .testimonial-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2rem;
  }

  .testimonial {
    background: white;
    padding: 2rem;
    border-radius: 0.5rem;
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
  }

  .testimonial p {
    font-size: 1.125rem;
    line-height: 1.7;
    margin-bottom: 1.5rem;
  }

  .testimonial footer {
    display: flex;
    align-items: center;
    gap: 1rem;
  }

  .testimonial img {
    width: 48px;
    height: 48px;
    border-radius: 50%;
  }
</style>
```

### Exemple 4 : Blog post titles

```html
<div class="blog-posts">
  <article class="post-card">
    <img src="post1.jpg" alt="Post" />
    <div class="post-content">
      <span class="category">Technologie</span>
      <h3 class="text-balance">
        Comment l'intelligence artificielle transforme le développement web
      </h3>
      <p class="excerpt">
        Découvrez les dernières avancées en IA et leur impact...
      </p>
      <a href="#" class="read-more">Lire la suite →</a>
    </div>
  </article>

  <article class="post-card">
    <img src="post2.jpg" alt="Post" />
    <div class="post-content">
      <span class="category">Design</span>
      <h3 class="text-balance">
        Les principes du design system pour équipes distribuées
      </h3>
      <p class="excerpt">Créez et maintenez un design system cohérent...</p>
      <a href="#" class="read-more">Lire la suite →</a>
    </div>
  </article>

  <article class="post-card">
    <img src="post3.jpg" alt="Post" />
    <div class="post-content">
      <span class="category">Business</span>
      <h3 class="text-balance">
        Stratégies de croissance pour startups en phase d'accélération
      </h3>
      <p class="excerpt">Guide complet pour scaler votre entreprise...</p>
      <a href="#" class="read-more">Lire la suite →</a>
    </div>
  </article>
</div>

<style>
  .blog-posts {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2rem;
  }

  .post-card {
    background: white;
    border-radius: 0.5rem;
    overflow: hidden;
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
    transition: transform 0.3s;
  }

  .post-card:hover {
    transform: translateY(-4px);
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
  }

  .post-card img {
    width: 100%;
    height: 200px;
    object-fit: cover;
  }

  .post-content {
    padding: 1.5rem;
  }

  .category {
    display: inline-block;
    padding: 0.25rem 0.75rem;
    background: #dbeafe;
    color: #1e40af;
    border-radius: 9999px;
    font-size: 0.875rem;
    font-weight: 500;
    margin-bottom: 1rem;
  }

  .post-card h3 {
    font-size: 1.25rem;
    line-height: 1.4;
    margin-bottom: 0.75rem;
  }

  .excerpt {
    color: #6b7280;
    margin-bottom: 1rem;
  }

  .read-more {
    color: #3b82f6;
    font-weight: 500;
    text-decoration: none;
  }
</style>
```

### Exemple 5 : Pricing cards

```html
<section class="pricing">
  <div class="container-fluid container-fluid--lg">
    <h2 class="text-balance text-balance--center">
      Des tarifs simples et transparents pour tous
    </h2>
    <p class="text-balance text-balance--center" style="--max-width: 60ch">
      Choisissez le plan qui correspond à vos besoins et évoluez à votre rythme
    </p>

    <div class="pricing-grid">
      <div class="pricing-card">
        <h3 class="text-balance">Starter</h3>
        <div class="price">
          <span class="amount">29€</span>
          <span class="period">/mois</span>
        </div>
        <p class="text-balance">Parfait pour freelances et petites équipes</p>
        <ul class="features">
          <li>✓ 5 projets</li>
          <li>✓ 10 Go stockage</li>
          <li>✓ Support email</li>
        </ul>
        <button class="btn">Commencer</button>
      </div>

      <div class="pricing-card pricing-card--featured">
        <div class="badge">Populaire</div>
        <h3 class="text-balance">Professional</h3>
        <div class="price">
          <span class="amount">79€</span>
          <span class="period">/mois</span>
        </div>
        <p class="text-balance">Idéal pour équipes en croissance et PME</p>
        <ul class="features">
          <li>✓ Projets illimités</li>
          <li>✓ 100 Go stockage</li>
          <li>✓ Support prioritaire</li>
        </ul>
        <button class="btn btn--primary">Commencer</button>
      </div>

      <div class="pricing-card">
        <h3 class="text-balance">Enterprise</h3>
        <div class="price">
          <span class="amount">Custom</span>
        </div>
        <p class="text-balance">Solution sur mesure pour grandes entreprises</p>
        <ul class="features">
          <li>✓ Tout illimité</li>
          <li>✓ SLA garanti</li>
          <li>✓ Support dédié 24/7</li>
        </ul>
        <button class="btn">Nous contacter</button>
      </div>
    </div>
  </div>
</section>

<style>
  .pricing {
    padding: 6rem 2rem;
  }

  .pricing h2 {
    font-size: 2.5rem;
    margin-bottom: 1rem;
  }

  .pricing > p {
    font-size: 1.125rem;
    color: #6b7280;
    margin-bottom: 4rem;
  }

  .pricing-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 2rem;
    max-width: 1200px;
    margin: 0 auto;
  }

  .pricing-card {
    position: relative;
    background: white;
    padding: 2rem;
    border: 2px solid #e5e7eb;
    border-radius: 0.5rem;
    text-align: center;
  }

  .pricing-card--featured {
    border-color: #3b82f6;
    transform: scale(1.05);
  }

  .badge {
    position: absolute;
    top: -12px;
    left: 50%;
    transform: translateX(-50%);
    background: #3b82f6;
    color: white;
    padding: 0.25rem 1rem;
    border-radius: 9999px;
    font-size: 0.875rem;
    font-weight: 600;
  }

  .pricing-card h3 {
    font-size: 1.5rem;
    margin-bottom: 1rem;
  }

  .price {
    margin-bottom: 1rem;
  }

  .amount {
    font-size: 3rem;
    font-weight: 700;
    color: #111827;
  }

  .period {
    color: #6b7280;
  }
</style>
```

## 🎨 Personnalisation avancée

### Largeur responsive

```html
<h1 class="text-balance responsive-title">
  Titre qui s'adapte à la taille d'écran
</h1>

<style>
  .responsive-title {
    --max-width: 30ch;
  }

  @media (min-width: 768px) {
    .responsive-title {
      --max-width: 45ch;
    }
  }

  @media (min-width: 1024px) {
    .responsive-title {
      --max-width: 60ch;
    }
  }
</style>
```

### Largeur fluide avec clamp

```html
<h1 class="text-balance" style="--max-width: clamp(30ch, 50vw, 60ch)">
  Titre avec largeur fluide
</h1>
```

### Balance avec line-clamp (texte tronqué)

```html
<h3 class="text-balance title-clamp">
  Titre très long qui pourrait prendre plusieurs lignes mais sera limité à 2
  lignes maximum
</h3>

<style>
  .title-clamp {
    display: -webkit-box;
    -webkit-line-clamp: 2;
    -webkit-box-orient: vertical;
    overflow: hidden;
  }
</style>
```

### Différents styles selon le contexte

```scss
// Titres de hero
.hero .text-balance {
  --max-width: 20ch;
  font-size: clamp(2rem, 5vw, 4rem);
  line-height: 1.1;
}

// Titres de section
.section .text-balance {
  --max-width: 40ch;
  font-size: clamp(1.5rem, 3vw, 2.5rem);
  line-height: 1.2;
}

// Titres de cards
.card .text-balance {
  --max-width: 30ch;
  font-size: 1.25rem;
  line-height: 1.3;
}
```

## 🎯 Cas d'usage courants

### 1. Titres de hero (h1)

```html
<h1 class="text-balance text-balance--center" style="--max-width: 40ch">
  Transformez votre vision en réalité
</h1>
```

### 2. Sous-titres (h2, h3)

```html
<h2 class="text-balance" style="--max-width: 50ch">
  Découvrez nos solutions innovantes
</h2>
```

### 3. Citations

```html
<blockquote class="text-balance text-balance--quote">
  "Le design c'est l'intelligence rendue visible"
</blockquote>
```

### 4. Descriptions courtes (lead)

```html
<p class="lead text-balance" style="--max-width: 60ch">
  Plateforme complète pour créateurs modernes
</p>
```

### 5. Titres de cards

```html
<h3 class="text-balance" style="--max-width: 35ch">
  Performance exceptionnelle garantie
</h3>
```

### 6. Boutons avec texte long

```html
<button class="text-balance" style="--max-width: 20ch">
  Télécharger notre guide complet
</button>
```

## 🔧 Combinaison avec autres utilitaires

### Avec Container Fluid

```html
<div class="container-fluid container-fluid--lg">
  <h1 class="text-balance text-balance--center">
    Titre centré dans un container
  </h1>
</div>
```

### Avec Gap Wrapper

```html
<div class="gap-wrapper gap-wrapper--column gap-wrapper--lg">
  <h1 class="text-balance text-balance--center">Titre principal</h1>
  <p class="text-balance text-balance--center">Description équilibrée</p>
</div>
```

### Avec Grid Wrapper

```html
<div class="grid-wrapper" style="--cols: 3">
  <div class="card">
    <h3 class="text-balance">Titre card 1</h3>
    <p>Description...</p>
  </div>
  <div class="card">
    <h3 class="text-balance">Titre card 2</h3>
    <p>Description...</p>
  </div>
  <div class="card">
    <h3 class="text-balance">Titre card 3</h3>
    <p>Description...</p>
  </div>
</div>
```

## 📱 Comportement responsive

### Adaptation automatique

Le text-balance fonctionne automatiquement sur tous les écrans, mais vous pouvez affiner :

```scss
.text-balance {
  // Mobile : plus étroit
  --max-width: 30ch;

  @media (min-width: 640px) {
    --max-width: 40ch;
  }

  @media (min-width: 1024px) {
    --max-width: 50ch;
  }
}
```

### Désactiver sur mobile

```scss
.text-balance {
  text-wrap: balance;

  @media (max-width: 640px) {
    text-wrap: wrap; // Normal sur mobile
  }
}
```

## ⚡ Performance & Bonnes pratiques

### ✅ À faire

```html
<!-- Bon : Utiliser sur textes courts (titres, citations) -->
<h1 class="text-balance">Titre court et impactant</h1>

<!-- Bon : Limiter la largeur -->
<h2 class="text-balance" style="--max-width: 45ch">
  Titre avec largeur optimale
</h2>

<!-- Bon : Utiliser ch pour largeur -->
<div class="text-balance" style="--max-width: 50ch">
  <!-- Bon : Combiner avec bon line-height -->
  <h1 class="text-balance" style="line-height: 1.2">Titre équilibré</h1>
</div>
```

### ❌ À éviter

```html
<!-- Mauvais : Sur texte très long (performance) -->
<article class="text-balance">
  <p>Lorem ipsum dolor sit amet... (10 paragraphes)</p>
</article>

<!-- Mauvais : Largeur trop grande -->
<h1 class="text-balance" style="--max-width: 200ch">Titre</h1>

<!-- Mauvais : Sur contenu généré -->
<div class="text-balance">
  <!-- Contenu dynamique très variable -->
</div>

<!-- Mauvais : Largeur en px sans responsive -->
<h1 class="text-balance" style="--max-width: 800px">Titre</h1>
```

### Limites de text-wrap: balance

```scss
// ⚠️ text-wrap: balance a des limites :
// - Maximum ~10 lignes (au-delà, pas d'effet)
// - Peut avoir un léger impact performance sur gros volumes
// - Mieux sur textes courts (titres, citations)

// ✅ Utilisez-le principalement pour :
h1,
h2,
h3,
h4,
h5,
h6 {
  text-wrap: balance;
  max-inline-size: 50ch;
}

blockquote {
  text-wrap: balance;
  max-inline-size: 60ch;
}

.lead {
  text-wrap: balance;
  max-inline-size: 65ch;
}
```

## 🌐 Compatibilité navigateurs

| Navigateur | Version minimale | Support    |
| ---------- | ---------------- | ---------- |
| Chrome     | 114+             | ✅ Complet |
| Firefox    | 121+             | ✅ Complet |
| Safari     | 17.5+            | ✅ Complet |
| Edge       | 114+             | ✅ Complet |
| Opera      | 100+             | ✅ Complet |

### Support actuel

`text-wrap: balance` est une propriété **moderne** (2023-2024). Pour les navigateurs plus anciens, le texte s'affichera normalement sans équilibrage.

### Détection de support

```scss
.text-balance {
  // Styles de base
  max-inline-size: 50ch;

  // Appliquer balance si supporté
  @supports (text-wrap: balance) {
    text-wrap: balance;
  }

  // Fallback pour anciens navigateurs
  @supports not (text-wrap: balance) {
    // Le texte s'affiche normalement
    // Aucune action nécessaire
  }
}
```

### Progressive enhancement

```html
<!-- L'expérience se dégrade gracieusement -->
<h1 class="text-balance">
  Titre qui sera équilibré sur navigateurs modernes, et s'affichera normalement
  sur anciens navigateurs
</h1>
```

## 🐛 Troubleshooting

### Problème : Le texte ne s'équilibre pas

**Solution 1** : Vérifiez le support du navigateur

```javascript
// Test de support
if (CSS.supports("text-wrap", "balance")) {
  console.log("text-wrap: balance est supporté");
} else {
  console.log("text-wrap: balance NON supporté");
}
```

**Solution 2** : Vérifiez la largeur maximale

```css
/* Si la largeur est trop grande, l'équilibrage peut ne pas être visible */
.text-balance {
  --max-width: 50ch; /* Essayez une valeur plus petite */
}
```

### Problème : L'équilibrage semble bizarre

**Solution** : Ajustez la largeur maximale

```css
/* Trop large */
--max-width: 100ch; /* ❌ Trop de variations possibles */

/* Optimal */
--max-width: 45ch; /* ✅ Balance visible et naturel */
```

### Problème : Performance lente

**Solution** : N'utilisez pas sur gros volumes de texte

```css
/* ❌ Mauvais : Sur tout le contenu */
body {
  text-wrap: balance;
}

/* ✅ Bon : Seulement sur titres */
h1,
h2,
h3,
h4,
h5,
h6 {
  text-wrap: balance;
}
```

### Problème : Text-align ne fonctionne pas

**Solution** : Utilisez la variable CSS

```html
<!-- ❌ Mauvais -->
<h1 class="text-balance" style="text-align: center">
  <!-- ✅ Bon -->
  <h1 class="text-balance text-balance--center">
    <!-- ou -->
    <h1 class="text-balance" style="--text-align: center"></h1>
  </h1>
</h1>
```

## 📦 Classes complètes disponibles

```scss
// Classes de base
.text-balance {
  /* Base avec balance */
}

// Largeurs
.text-balance--narrow {
  --max-width: 30ch;
}
.text-balance--normal {
  --max-width: 50ch;
}
.text-balance--wide {
  --max-width: 70ch;
}
.text-balance--full {
  --max-width: 100%;
}

// Alignements
.text-balance--left {
  --text-align: left;
}
.text-balance--center {
  --text-align: center;
}
.text-balance--right {
  --text-align: right;
}

// Par type de contenu
.text-balance--heading {
  /* Optimisé pour h1-h3 */
}
.text-balance--subheading {
  /* Optimisé pour h4-h6 */
}
.text-balance--quote {
  /* Optimisé pour citations */
}

// Utilitaires
.text-balance--off {
  text-wrap: wrap;
}
.text-balance--multi {
  /* Multi-lignes */
}
```

## 📐 Guide de sélection de largeur

| Type de contenu    | Largeur recommandée | Exemple                             |
| ------------------ | ------------------- | ----------------------------------- |
| Titre hero (h1)    | 30-40ch             | "Transformez votre business"        |
| Titre section (h2) | 40-50ch             | "Pourquoi choisir notre solution ?" |
| Sous-titre (h3-h4) | 35-45ch             | "Features principales"              |
| Citation           | 50-60ch             | "Le design c'est..."                |
| Lead paragraph     | 60-70ch             | Description longue                  |
| Card title         | 25-35ch             | Titre court card                    |

## 🎓 Ressources complémentaires

- [CSS Text Module Level 4 - W3C](https://www.w3.org/TR/css-text-4/#text-wrap)
- [text-wrap: balance - MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/text-wrap)
- [Can I Use - text-wrap](https://caniuse.com/css-text-wrap-balance)
- [The ch unit - MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/length#ch)

## 📝 Changelog

- **v1.0** - Version initiale avec text-wrap: balance
- **v1.1** - Ajout des variantes de largeur (narrow, normal, wide)
- **v1.2** - Support des variantes d'alignement
- **v1.3** - Ajout des variantes par type (heading, quote, etc.)
- **v1.4** - Amélioration de la compatibilité avec @supports

---

**Made with ❤️ for beautiful typography**
