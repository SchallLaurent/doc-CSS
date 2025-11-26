# Container Fluid Utility

> Conteneurs responsives avec largeur maximale et padding adaptatif pour un contenu parfaitement centré

## 📋 Description

**Container Fluid** est un utilitaire CSS qui crée des conteneurs intelligents avec une largeur maximale et des paddings adaptatifs. Le conteneur s'ajuste automatiquement à la taille de l'écran, offrant une expérience optimale sur tous les devices sans débordement ni espaces vides inutiles.

### ✨ Caractéristiques principales

- 📏 **Max-width personnalisable** : Contrôle précis de la largeur maximale du contenu
- 📱 **Padding adaptatif** : Espacement qui s'ajuste selon la taille d'écran
- 🎯 **Centrage automatique** : Contenu parfaitement centré
- 🔧 **Variables CSS** : Personnalisation sans modification du code
- ⚡ **Performance** : CSS natif léger et rapide
- 🎨 **Variantes prédéfinies** : Tailles SM, MD, LG, XL, 2XL
- 🔄 **Fluide par défaut** : Utilise clamp() pour un responsive parfait

## 🚀 Installation

### Code SCSS

```scss
// _container-fluid.scss

// Échelle de largeurs maximales
$container-sizes: (
  "sm": 640px,
  "md": 768px,
  "lg": 1024px,
  "xl": 1280px,
  "2xl": 1536px,
  "full": 100%,
);

// Échelle de paddings
$container-paddings: (
  "none": 0,
  "sm": 1rem,
  "md": 1.5rem,
  "lg": 2rem,
  "xl": 3rem,
);

.container-fluid {
  // Variables par défaut
  --max-width: 1200px; // Largeur maximale du contenu
  --padding: clamp(1rem, 5vw, 3rem); // Padding adaptatif (fluide)
  --padding-inline: var(--padding); // Padding horizontal
  --padding-block: 0; // Padding vertical (optionnel)

  width: 100%;
  max-width: var(--max-width);
  margin-inline: auto; // Centrage horizontal
  padding-inline: var(--padding-inline);
  padding-block: var(--padding-block);

  // Sécurité pour éviter le débordement
  box-sizing: border-box;
}

// Variantes de taille prédéfinies
.container-fluid--sm {
  --max-width: 640px;
}

.container-fluid--md {
  --max-width: 768px;
}

.container-fluid--lg {
  --max-width: 1024px;
}

.container-fluid--xl {
  --max-width: 1280px;
}

.container-fluid--2xl {
  --max-width: 1536px;
}

.container-fluid--full {
  --max-width: 100%;
}

// Variantes de padding
.container-fluid--tight {
  --padding: clamp(0.5rem, 2vw, 1rem);
}

.container-fluid--normal {
  --padding: clamp(1rem, 5vw, 3rem); // Défaut
}

.container-fluid--loose {
  --padding: clamp(2rem, 8vw, 5rem);
}

.container-fluid--none {
  --padding: 0;
}

// Padding fixe (non-fluide)
.container-fluid--fixed-sm {
  --padding: 1rem;
}

.container-fluid--fixed-md {
  --padding: 1.5rem;
}

.container-fluid--fixed-lg {
  --padding: 2rem;
}

.container-fluid--fixed-xl {
  --padding: 3rem;
}

// Padding vertical
.container-fluid--py-sm {
  --padding-block: 1rem;
}

.container-fluid--py-md {
  --padding-block: 2rem;
}

.container-fluid--py-lg {
  --padding-block: 3rem;
}

.container-fluid--py-xl {
  --padding-block: 4rem;
}

// Variantes d'alignement de contenu
.container-fluid--left {
  margin-inline: 0 auto;
}

.container-fluid--right {
  margin-inline: auto 0;
}

// Container avec effet de dégradé sur les bords
.container-fluid--fade-edges {
  position: relative;

  &::before,
  &::after {
    content: "";
    position: absolute;
    top: 0;
    bottom: 0;
    width: var(--padding-inline);
    pointer-events: none;
  }

  &::before {
    left: 0;
    background: linear-gradient(to right, var(--bg-color, white), transparent);
  }

  &::after {
    right: 0;
    background: linear-gradient(to left, var(--bg-color, white), transparent);
  }
}

// Container avec breakout (permet aux enfants de déborder)
.container-fluid--breakout {
  --breakout: calc((100vw - var(--max-width)) / 2);

  > .full-width {
    width: 100vw;
    margin-left: calc(-1 * var(--padding-inline));
    margin-right: calc(-1 * var(--padding-inline));
  }

  > .breakout-left {
    margin-left: calc(-1 * var(--breakout) - var(--padding-inline));
  }

  > .breakout-right {
    margin-right: calc(-1 * var(--breakout) - var(--padding-inline));
  }
}
```

### Import dans votre projet

```scss
// Dans styles.scss
@import "utilities/container-fluid";
```

## 💡 Utilisation de base

### Exemple 1 : Container simple (défaut)

```html
<div class="container-fluid">
  <h1>Bienvenue</h1>
  <p>Contenu centré avec largeur maximale de 1200px et padding adaptatif</p>
</div>
```

### Exemple 2 : Container avec taille personnalisée

```html
<!-- Container de 900px max -->
<div class="container-fluid" style="--max-width: 900px">
  <article>
    <h1>Article de blog</h1>
    <p>Largeur optimale pour la lecture...</p>
  </article>
</div>
```

### Exemple 3 : Container étroit (lecture)

```html
<div class="container-fluid container-fluid--md">
  <article>
    <h1>Article long</h1>
    <p>Largeur optimale de 768px pour une lecture confortable</p>
  </article>
</div>
```

### Exemple 4 : Container avec padding personnalisé

```html
<!-- Padding de 1rem min, 3vw dynamique, 2rem max -->
<div class="container-fluid" style="--padding: clamp(1rem, 3vw, 2rem)">
  <h1>Contenu</h1>
</div>
```

## 📊 Paramètres

| Variable           | Type   | Défaut                   | Description                  |
| ------------------ | ------ | ------------------------ | ---------------------------- |
| `--max-width`      | length | `1200px`                 | Largeur maximale du contenu  |
| `--padding`        | length | `clamp(1rem, 5vw, 3rem)` | Padding horizontal adaptatif |
| `--padding-inline` | length | `var(--padding)`         | Padding gauche/droite        |
| `--padding-block`  | length | `0`                      | Padding haut/bas             |

### Tailles de conteneur prédéfinies

| Classe   | Max-width | Usage                            |
| -------- | --------- | -------------------------------- |
| `--sm`   | 640px     | Formulaires, contenu très étroit |
| `--md`   | 768px     | Articles, lecture optimale       |
| `--lg`   | 1024px    | Contenu standard                 |
| `--xl`   | 1280px    | Large contenu (défaut: 1200px)   |
| `--2xl`  | 1536px    | Très large contenu               |
| `--full` | 100%      | Pleine largeur                   |

### Valeurs courantes pour `--max-width`

```css
/* Tailles prédéfinies */
--max-width: 640px; /* Small - Formulaires */
--max-width: 768px; /* Medium - Articles */
--max-width: 1024px; /* Large - Contenu standard */
--max-width: 1200px; /* XL - Défaut */
--max-width: 1280px; /* 2XL - Large dashboard */
--max-width: 1536px; /* 3XL - Très large */

/* Largeurs personnalisées */
--max-width: 900px; /* Lecture blog */
--max-width: 65ch; /* Basé sur caractères (optimal pour texte) */
--max-width: 90%; /* Pourcentage */
```

### Valeurs courantes pour `--padding`

```css
/* Padding fluide (responsive) */
--padding: clamp(1rem, 5vw, 3rem); /* Standard */
--padding: clamp(0.5rem, 2vw, 1rem); /* Serré */
--padding: clamp(2rem, 8vw, 5rem); /* Large */

/* Padding fixe */
--padding: 1rem; /* 16px */
--padding: 1.5rem; /* 24px */
--padding: 2rem; /* 32px */
--padding: 3rem; /* 48px */

/* Padding asymétrique */
--padding-inline: 2rem; /* Horizontal */
--padding-block: 4rem; /* Vertical */
```

## 📚 Exemples détaillés

### Exemple 1 : Page d'accueil

```html
<!DOCTYPE html>
<html lang="fr">
  <head>
    <title>Accueil</title>
  </head>
  <body>
    <!-- Hero section - Full width -->
    <section
      class="hero"
      style="background: linear-gradient(135deg, #667eea 0%, #764ba2 100%)"
    >
      <div class="container-fluid container-fluid--xl">
        <h1>Bienvenue sur notre site</h1>
        <p>Découvrez nos solutions innovantes</p>
        <button class="btn-primary">En savoir plus</button>
      </div>
    </section>

    <!-- Content section - Standard width -->
    <section class="container-fluid container-fluid--lg container-fluid--py-lg">
      <h2>Nos services</h2>
      <div class="services-grid">
        <!-- Services content -->
      </div>
    </section>

    <!-- Article section - Narrow for reading -->
    <article class="container-fluid container-fluid--md container-fluid--py-xl">
      <h2>Notre histoire</h2>
      <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit...</p>
    </article>
  </body>
</html>

<style>
  .hero {
    color: white;
    padding: 4rem 0;
  }

  .hero h1 {
    font-size: 3rem;
    margin-bottom: 1rem;
  }
</style>
```

### Exemple 2 : Blog layout

```html
<main>
  <!-- Article header - Wide -->
  <header class="container-fluid container-fluid--xl container-fluid--py-lg">
    <span class="category">Technologie</span>
    <h1>Le futur du développement web</h1>
    <div class="author-info">
      <img src="author.jpg" alt="Auteur" />
      <div>
        <strong>Jean Dupont</strong>
        <time>15 janvier 2024</time>
      </div>
    </div>
  </header>

  <!-- Article content - Narrow for optimal reading -->
  <article class="container-fluid container-fluid--md container-fluid--py-xl">
    <p class="lead">Introduction de l'article en plus grand...</p>

    <h2>Première section</h2>
    <p>
      Contenu de l'article avec une largeur optimale pour la lecture (768px
      max).
    </p>

    <blockquote>"Une citation importante du texte"</blockquote>

    <h2>Deuxième section</h2>
    <p>Suite du contenu...</p>
  </article>

  <!-- Comments - Medium width -->
  <section class="container-fluid container-fluid--lg container-fluid--py-lg">
    <h3>Commentaires (12)</h3>
    <div class="comments-list">
      <!-- Comments -->
    </div>
  </section>
</main>

<style>
  .lead {
    font-size: 1.25rem;
    line-height: 1.6;
    color: #6b7280;
  }

  blockquote {
    border-left: 4px solid #3b82f6;
    padding-left: 1.5rem;
    font-style: italic;
    color: #4b5563;
    margin: 2rem 0;
  }
</style>
```

### Exemple 3 : Dashboard avec sidebar

```html
<div class="dashboard">
  <!-- Top navigation - Full width background -->
  <nav class="topnav">
    <div class="container-fluid container-fluid--2xl">
      <div class="nav-content">
        <div class="logo">Dashboard</div>
        <div class="nav-items">
          <a href="#">Accueil</a>
          <a href="#">Analytics</a>
          <a href="#">Settings</a>
        </div>
      </div>
    </div>
  </nav>

  <!-- Main content - Extra wide -->
  <main class="container-fluid container-fluid--2xl container-fluid--py-lg">
    <h1>Tableau de bord</h1>

    <!-- Stats grid -->
    <div class="stats-grid">
      <div class="stat-card">
        <h3>Ventes</h3>
        <p class="stat-value">12,543</p>
      </div>
      <div class="stat-card">
        <h3>Utilisateurs</h3>
        <p class="stat-value">3,891</p>
      </div>
      <div class="stat-card">
        <h3>Revenus</h3>
        <p class="stat-value">89,432 €</p>
      </div>
    </div>
  </main>
</div>

<style>
  .topnav {
    background: #1f2937;
    color: white;
    padding: 1rem 0;
  }

  .nav-content {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .stats-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 1.5rem;
    margin-top: 2rem;
  }

  .stat-card {
    background: white;
    padding: 1.5rem;
    border-radius: 0.5rem;
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
  }

  .stat-value {
    font-size: 2rem;
    font-weight: 700;
    color: #3b82f6;
  }
</style>
```

### Exemple 4 : Landing page avec sections alternées

```html
<!-- Hero - Large -->
<section class="hero">
  <div class="container-fluid container-fluid--xl container-fluid--py-xl">
    <h1>Transformez votre business</h1>
    <p>Solutions innovantes pour entreprises modernes</p>
    <button>Démarrer gratuitement</button>
  </div>
</section>

<!-- Features - Standard -->
<section class="container-fluid container-fluid--lg container-fluid--py-xl">
  <h2>Nos fonctionnalités</h2>
  <div class="features-grid">
    <div class="feature">
      <h3>Rapide</h3>
      <p>Performance optimale</p>
    </div>
    <div class="feature">
      <h3>Sécurisé</h3>
      <p>Protection des données</p>
    </div>
    <div class="feature">
      <h3>Évolutif</h3>
      <p>Grandit avec vous</p>
    </div>
  </div>
</section>

<!-- Testimonial - Narrow -->
<section class="testimonial-section">
  <div class="container-fluid container-fluid--md container-fluid--py-xl">
    <blockquote>
      <p>
        "Cette solution a transformé notre façon de travailler. Incroyable!"
      </p>
      <footer>
        <strong>Marie Martin</strong>
        <span>CEO, TechCorp</span>
      </footer>
    </blockquote>
  </div>
</section>

<!-- CTA - Large -->
<section class="cta-section">
  <div class="container-fluid container-fluid--xl container-fluid--py-xl">
    <h2>Prêt à commencer ?</h2>
    <p>Rejoignez plus de 10,000 entreprises satisfaites</p>
    <button class="btn-cta">Essai gratuit</button>
  </div>
</section>

<style>
  .hero {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
    text-align: center;
  }

  .features-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 2rem;
    margin-top: 2rem;
  }

  .testimonial-section {
    background: #f9fafb;
  }

  .testimonial-section blockquote {
    text-align: center;
    font-size: 1.5rem;
    line-height: 1.6;
  }

  .cta-section {
    background: #1f2937;
    color: white;
    text-align: center;
  }
</style>
```

### Exemple 5 : Form page

```html
<main class="form-page">
  <!-- Header - Wide -->
  <header class="container-fluid container-fluid--lg container-fluid--py-md">
    <h1>Créer un compte</h1>
    <p>Rejoignez notre communauté</p>
  </header>

  <!-- Form - Narrow -->
  <div class="container-fluid container-fluid--sm container-fluid--py-lg">
    <form class="signup-form">
      <div class="form-group">
        <label for="name">Nom complet</label>
        <input type="text" id="name" required />
      </div>

      <div class="form-group">
        <label for="email">Email</label>
        <input type="email" id="email" required />
      </div>

      <div class="form-group">
        <label for="password">Mot de passe</label>
        <input type="password" id="password" required />
      </div>

      <button type="submit" class="btn-submit">S'inscrire</button>

      <p class="form-footer">Déjà membre ? <a href="#">Se connecter</a></p>
    </form>
  </div>
</main>

<style>
  .form-page {
    min-height: 100vh;
    background: #f9fafb;
  }

  .signup-form {
    background: white;
    padding: 2rem;
    border-radius: 0.5rem;
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
  }

  .form-group {
    margin-bottom: 1.5rem;
  }

  label {
    display: block;
    margin-bottom: 0.5rem;
    font-weight: 500;
  }

  input {
    width: 100%;
    padding: 0.75rem;
    border: 1px solid #d1d5db;
    border-radius: 0.375rem;
  }

  .btn-submit {
    width: 100%;
    padding: 0.75rem;
    background: #3b82f6;
    color: white;
    border: none;
    border-radius: 0.375rem;
    font-weight: 600;
    cursor: pointer;
  }

  .form-footer {
    text-align: center;
    margin-top: 1rem;
    color: #6b7280;
  }
</style>
```

## 🎨 Personnalisation avancée

### Container avec largeur basée sur caractères

```html
<!-- Optimal pour le texte : 65-75 caractères par ligne -->
<div class="container-fluid" style="--max-width: 65ch">
  <article>
    <p>Texte avec largeur optimale pour la lisibilité...</p>
  </article>
</div>
```

### Padding différent par breakpoint

```html
<div class="container-fluid responsive-padding">
  <h1>Contenu</h1>
</div>

<style>
  .responsive-padding {
    --padding: 1rem;
  }

  @media (min-width: 640px) {
    .responsive-padding {
      --padding: 1.5rem;
    }
  }

  @media (min-width: 1024px) {
    .responsive-padding {
      --padding: 2rem;
    }
  }

  @media (min-width: 1280px) {
    .responsive-padding {
      --padding: 3rem;
    }
  }
</style>
```

### Container avec breakout (débordement contrôlé)

```html
<div class="container-fluid container-fluid--breakout">
  <p>Contenu normal dans le container...</p>

  <!-- Cette image déborde du container pour être pleine largeur -->
  <img class="full-width" src="wide-image.jpg" alt="Wide image" />

  <p>Retour au contenu normal...</p>
</div>

<style>
  .full-width {
    width: 100vw;
    margin-left: calc(-1 * var(--padding-inline));
    margin-right: calc(-1 * var(--padding-inline));
  }
</style>
```

### Container avec effet de fondu sur les bords

```html
<div
  class="container-fluid container-fluid--fade-edges"
  style="--bg-color: #f9fafb"
>
  <div class="horizontal-scroll">
    <!-- Contenu qui scroll horizontalement -->
    <div class="item">Item 1</div>
    <div class="item">Item 2</div>
    <div class="item">Item 3</div>
  </div>
</div>

<style>
  .horizontal-scroll {
    display: flex;
    gap: 1rem;
    overflow-x: auto;
    -webkit-overflow-scrolling: touch;
  }

  .item {
    flex: 0 0 300px;
    height: 200px;
    background: white;
    border-radius: 0.5rem;
  }
</style>
```

## 🎯 Cas d'usage courants

### 1. Page d'article / Blog

```html
<!-- Largeur optimale pour la lecture -->
<article class="container-fluid container-fluid--md container-fluid--py-xl">
  <h1>Titre de l'article</h1>
  <p>Contenu...</p>
</article>
```

### 2. Dashboard / Admin

```html
<!-- Large pour afficher beaucoup d'informations -->
<main class="container-fluid container-fluid--2xl">
  <!-- Contenu dashboard -->
</main>
```

### 3. Formulaires

```html
<!-- Étroit pour focus sur le formulaire -->
<div class="container-fluid container-fluid--sm">
  <form><!-- Formulaire --></form>
</div>
```

### 4. Landing page hero

```html
<!-- Large avec padding généreux -->
<section class="container-fluid container-fluid--xl container-fluid--py-xl">
  <h1>Hero Title</h1>
</section>
```

### 5. Documentation

```html
<!-- Medium-large pour code et contenu -->
<main class="container-fluid container-fluid--lg">
  <article><!-- Documentation --></article>
</main>
```

### 6. E-commerce product grid

```html
<!-- Extra large pour afficher beaucoup de produits -->
<div class="container-fluid container-fluid--2xl">
  <div class="products-grid">
    <!-- Produits -->
  </div>
</div>
```

## 🔧 Combinaison avec autres utilitaires

### Avec Gap Wrapper

```html
<div class="container-fluid container-fluid--lg">
  <div class="gap-wrapper gap-wrapper--column gap-wrapper--xl">
    <section>Section 1</section>
    <section>Section 2</section>
    <section>Section 3</section>
  </div>
</div>
```

### Avec Grid Wrapper

```html
<div class="container-fluid container-fluid--2xl">
  <div class="grid-wrapper" style="--cols: 4; --gap: 2rem">
    <div class="card">Card 1</div>
    <div class="card">Card 2</div>
    <div class="card">Card 3</div>
    <div class="card">Card 4</div>
  </div>
</div>
```

### Avec Split Screen

```html
<div class="container-fluid container-fluid--xl">
  <div class="split split--sidebar">
    <aside>Sidebar</aside>
    <main>Content</main>
  </div>
</div>
```

## 📱 Comportement responsive

### Stratégies de padding responsive

```scss
// Option 1 : Clamp (recommandé)
.container-fluid {
  --padding: clamp(1rem, 5vw, 3rem);
  // Mobile: 1rem, Desktop: 3rem, entre les deux: 5vw
}

// Option 2 : Media queries
.container-fluid {
  --padding: 1rem;

  @media (min-width: 640px) {
    --padding: 1.5rem;
  }

  @media (min-width: 1024px) {
    --padding: 2rem;
  }

  @media (min-width: 1280px) {
    --padding: 3rem;
  }
}

// Option 3 : Calc dynamique
.container-fluid {
  --padding: calc(1rem + 2vw);
}
```

### Max-width responsive

```html
<div class="container-fluid responsive-width">
  <h1>Contenu</h1>
</div>

<style>
  .responsive-width {
    --max-width: 640px; /* Mobile/Tablet */
  }

  @media (min-width: 1024px) {
    .responsive-width {
      --max-width: 1200px; /* Desktop */
    }
  }
</style>
```

## ⚡ Performance & Bonnes pratiques

### ✅ À faire

```html
<!-- Bon : Utiliser clamp pour padding fluide -->
<div class="container-fluid" style="--padding: clamp(1rem, 5vw, 3rem)">
  <!-- Bon : Adapter la largeur au contenu -->
  <article class="container-fluid container-fluid--md">
    <!-- Article -->
    <main class="container-fluid container-fluid--2xl">
      <!-- Dashboard -->

      <!-- Bon : Padding cohérent avec le design system -->
      <div class="container-fluid container-fluid--normal">
        <!-- Bon : Box-sizing border-box -->
        <style>
          .container-fluid {
            box-sizing: border-box;
          }
        </style>
      </div>
    </main>
  </article>
</div>
```

### ❌ À éviter

```html
<!-- Mauvais : Max-width trop large (perte de lisibilité) -->
<article class="container-fluid" style="--max-width: 2000px">
  <!-- Mauvais : Padding trop petit sur mobile -->
  <div class="container-fluid" style="--padding: 0.25rem">
    <!-- Mauvais : Largeur en px fixes non responsive -->
    <div class="container-fluid" style="--padding: 50px">
      <!-- Mauvais : Multiples containers imbriqués -->
      <div class="container-fluid">
        <div class="container-fluid">
          <!-- ❌ Éviter l'imbrication -->
          <p>Contenu</p>
        </div>
      </div>
    </div>
  </div>
</article>
```

### Conseils de performance

```scss
// ✅ Utiliser des valeurs en rem
--max-width: 1200px;
--padding: 2rem;

// ✅ Éviter les calculs complexes
--padding: clamp(1rem, 5vw, 3rem); // Simple et efficace

// ❌ Éviter les calculs inutiles
--padding: calc(calc(1rem + 2vw) * calc(100vw / 1000)); // Trop complexe
```

## 🌐 Compatibilité navigateurs

| Navigateur | Version minimale | Support            |
| ---------- | ---------------- | ------------------ |
| Chrome     | 79+              | ✅ Complet (clamp) |
| Firefox    | 75+              | ✅ Complet (clamp) |
| Safari     | 13.1+            | ✅ Complet (clamp) |
| Edge       | 79+              | ✅ Complet (clamp) |
| Opera      | 66+              | ✅ Complet (clamp) |

### Fallback pour anciens navigateurs

```scss
.container-fluid {
  // Fallback padding fixe
  padding-inline: 1rem;

  @media (min-width: 640px) {
    padding-inline: 1.5rem;
  }

  @media (min-width: 1024px) {
    padding-inline: 2rem;
  }

  // Clamp si supporté (override le fallback)
  @supports (padding: clamp(1rem, 5vw, 3rem)) {
    padding-inline: var(--padding);
  }
}
```

## 🐛 Troubleshooting

### Problème : Débordement horizontal

**Solution** : Vérifiez box-sizing et width

```scss
.container-fluid {
  box-sizing: border-box; // Inclut padding dans width
  width: 100%; // Prend toute la largeur disponible
}

// Sur le body aussi
* {
  box-sizing: border-box;
}
```

### Problème : Contenu ne se centre pas

**Solution** : Vérifiez margin-inline

```scss
.container-fluid {
  margin-inline: auto; // Centre horizontalement
  margin-left: auto; // Fallback
  margin-right: auto; // Fallback
}
```

### Problème : Padding trop grand sur mobile

**Solution** : Utilisez clamp avec min plus petit

```css
/* Au lieu de */
--padding: clamp(2rem, 5vw, 3rem); /* Min 2rem peut être trop */

/* Utilisez */
--padding: clamp(1rem, 5vw, 3rem); /* Min 1rem mieux pour mobile */
```

### Problème : Max-width ne fonctionne pas

**Solution** : Vérifiez qu'il n'y a pas de width fixe

```css
/* Mauvais */
.container-fluid {
  width: 1200px; /* Override max-width */
}

/* Bon */
.container-fluid {
  width: 100%;
  max-width: 1200px;
}
```

## 📦 Classes complètes disponibles

```scss
// Tailles de container
.container-fluid {
  --max-width: 1200px;
}
.container-fluid--sm {
  --max-width: 640px;
}
.container-fluid--md {
  --max-width: 768px;
}
.container-fluid--lg {
  --max-width: 1024px;
}
.container-fluid--xl {
  --max-width: 1280px;
}
.container-fluid--2xl {
  --max-width: 1536px;
}
.container-fluid--full {
  --max-width: 100%;
}

// Paddings fluides
.container-fluid--tight {
  --padding: clamp(0.5rem, 2vw, 1rem);
}
.container-fluid--normal {
  --padding: clamp(1rem, 5vw, 3rem);
}
.container-fluid--loose {
  --padding: clamp(2rem, 8vw, 5rem);
}
.container-fluid--none {
  --padding: 0;
}

// Paddings fixes
.container-fluid--fixed-sm {
  --padding: 1rem;
}
.container-fluid--fixed-md {
  --padding: 1.5rem;
}
.container-fluid--fixed-lg {
  --padding: 2rem;
}
.container-fluid--fixed-xl {
  --padding: 3rem;
}

// Paddings verticaux
.container-fluid--py-sm {
  --padding-block: 1rem;
}
.container-fluid--py-md {
  --padding-block: 2rem;
}
.container-fluid--py-lg {
  --padding-block: 3rem;
}
.container-fluid--py-xl {
  --padding-block: 4rem;
}

// Alignement
.container-fluid--left {
  margin-inline: 0 auto;
}
.container-fluid--right {
  margin-inline: auto 0;
}

// Effets spéciaux
.container-fluid--fade-edges {
  /* Dégradé sur bords */
}
.container-fluid--breakout {
  /* Permet débordement */
}
```

## 📐 Guide de sélection de taille

| Type de contenu | Taille recommandée | Raison             |
| --------------- | ------------------ | ------------------ |
| Article de blog | `--md` (768px)     | Lecture optimale   |
| Documentation   | `--lg` (1024px)    | Code + texte       |
| Formulaire      | `--sm` (640px)     | Focus              |
| Dashboard       | `--2xl` (1536px)   | Beaucoup d'infos   |
| Landing page    | `--xl` (1280px)    | Standard           |
| E-commerce      | `--2xl` (1536px)   | Grille de produits |
| Page de contact | `--md` (768px)     | Simple et direct   |

## 🎓 Ressources complémentaires

- [CSS Clamp() - MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/clamp)
- [Logical Properties - MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Logical_Properties)
- [Max-width - MDN](https://developer.mozilla.org/fr/docs/Web/CSS/max-width)
- [Container Queries - MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Container_Queries)

## 📝 Changelog

- **v1.0** - Version initiale avec max-width et padding de base
- **v1.1** - Ajout des variantes de taille (sm, md, lg, xl, 2xl)
- **v1.2** - Support de clamp() pour padding fluide
- **v1.3** - Ajout des paddings verticaux
- **v1.4** - Support du breakout pour débordement contrôlé
- **v1.5** - Amélioration de la compatibilité avec logical properties

---

**Made with ❤️ for perfect layouts**
