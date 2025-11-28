# Glass Effect Utility

> Créez des effets de verre dépoli modernes et élégants (glassmorphism) avec backdrop-filter

## 📋 Description

**Glass Effect** est un utilitaire CSS qui implémente le style "glassmorphism" - un effet de verre dépoli ou givré qui floute l'arrière-plan tout en conservant une certaine transparence. Cet effet est très populaire dans les designs modernes (macOS Big Sur, iOS, Windows 11) et apporte de la profondeur et du raffinement aux interfaces.

### ✨ Caractéristiques principales

- 🌫️ **Backdrop blur** : Flou de l'arrière-plan avec backdrop-filter
- 💎 **Transparence contrôlée** : Opacité ajustable pour l'effet de verre
- 🎨 **Variantes colorées** : Glass blanc, noir, ou coloré
- 🔧 **Variables CSS** : Personnalisation complète via variables
- ⚡ **Performance** : Utilise les propriétés natives du navigateur
- 🎭 **Bordures subtiles** : Effet de contour pour plus de réalisme
- 🌈 **Support saturate** : Accentuation des couleurs derrière

## 🚀 Installation

### Code SCSS

```scss
// _glass-effect.scss

.glass-effect {
  // Variables par défaut
  --glass-bg: 255, 255, 255; // Background color (RGB)
  --glass-opacity: 0.7; // Opacité du fond
  --glass-blur: 10px; // Intensité du flou
  --glass-saturate: 180%; // Saturation des couleurs
  --glass-border-opacity: 0.18; // Opacité de la bordure
  --glass-border-width: 1px; // Épaisseur de la bordure

  // Background semi-transparent
  background: rgba(var(--glass-bg), var(--glass-opacity));

  // Effet de flou sur l'arrière-plan
  backdrop-filter: blur(var(--glass-blur)) saturate(var(--glass-saturate));
  -webkit-backdrop-filter: blur(var(--glass-blur)) saturate(
      var(--glass-saturate)
    );

  // Bordure subtile pour plus de définition
  border: var(--glass-border-width) solid rgba(
      var(--glass-bg),
      var(--glass-border-opacity)
    );

  // Fallback pour navigateurs non compatibles
  @supports not (backdrop-filter: blur(1px)) {
    background: rgba(var(--glass-bg), calc(var(--glass-opacity) + 0.1));
  }
}

// Variantes de couleur prédéfinies
.glass-effect--light {
  --glass-bg: 255, 255, 255;
  --glass-opacity: 0.7;
}

.glass-effect--dark {
  --glass-bg: 0, 0, 0;
  --glass-opacity: 0.5;
  color: white;
}

.glass-effect--frosted {
  --glass-bg: 255, 255, 255;
  --glass-opacity: 0.25;
  --glass-blur: 16px;
}

// Variantes colorées
.glass-effect--blue {
  --glass-bg: 59, 130, 246; // Blue-500
  --glass-opacity: 0.3;
}

.glass-effect--purple {
  --glass-bg: 139, 92, 246; // Purple-500
  --glass-opacity: 0.3;
}

.glass-effect--pink {
  --glass-bg: 236, 72, 153; // Pink-500
  --glass-opacity: 0.3;
}

.glass-effect--green {
  --glass-bg: 34, 197, 94; // Green-500
  --glass-opacity: 0.3;
}

.glass-effect--orange {
  --glass-bg: 249, 115, 22; // Orange-500
  --glass-opacity: 0.3;
}

// Variantes d'intensité de flou
.glass-effect--blur-sm {
  --glass-blur: 4px;
}

.glass-effect--blur-md {
  --glass-blur: 10px; // Défaut
}

.glass-effect--blur-lg {
  --glass-blur: 16px;
}

.glass-effect--blur-xl {
  --glass-blur: 24px;
}

// Variantes d'opacité
.glass-effect--transparent {
  --glass-opacity: 0.4;
}

.glass-effect--semi {
  --glass-opacity: 0.6;
}

.glass-effect--opaque {
  --glass-opacity: 0.8;
}

// Sans bordure
.glass-effect--no-border {
  border: none;
}

// Bordure plus prononcée
.glass-effect--thick-border {
  --glass-border-width: 2px;
  --glass-border-opacity: 0.3;
}

// Effet de brillance (shine)
.glass-effect--shine {
  position: relative;
  overflow: hidden;

  &::before {
    content: "";
    position: absolute;
    top: 0;
    left: -100%;
    width: 50%;
    height: 100%;
    background: linear-gradient(
      90deg,
      transparent,
      rgba(255, 255, 255, 0.3),
      transparent
    );
    transition: left 0.5s;
  }

  &:hover::before {
    left: 100%;
  }
}

// Sans saturation
.glass-effect--no-saturate {
  --glass-saturate: 100%;
}

// Hyper saturation
.glass-effect--hyper-saturate {
  --glass-saturate: 200%;
}
```

### Import dans votre projet

```scss
// Dans styles.scss
@import "utilities/glass-effect";
```

## 💡 Utilisation de base

### Exemple 1 : Card simple avec effet verre

```html
<div class="glass-effect" style="padding: 2rem; border-radius: 1rem">
  <h3>Glass Card</h3>
  <p>Effet de verre dépoli moderne</p>
</div>
```

### Exemple 2 : Glass dark

```html
<div
  class="glass-effect glass-effect--dark"
  style="padding: 2rem; border-radius: 1rem"
>
  <h3>Dark Glass</h3>
  <p>Effet de verre sombre</p>
</div>
```

### Exemple 3 : Glass coloré

```html
<div
  class="glass-effect glass-effect--blue"
  style="padding: 2rem; border-radius: 1rem"
>
  <h3>Blue Glass</h3>
  <p>Effet de verre bleuté</p>
</div>
```

### Exemple 4 : Intensité de flou personnalisée

```html
<div
  class="glass-effect"
  style="--glass-blur: 20px; padding: 2rem; border-radius: 1rem"
>
  <h3>Custom Blur</h3>
  <p>Flou personnalisé à 20px</p>
</div>
```

## 📊 Paramètres

| Variable                 | Type             | Défaut          | Description             |
| ------------------------ | ---------------- | --------------- | ----------------------- |
| `--glass-bg`             | RGB (sans alpha) | `255, 255, 255` | Couleur de fond en RGB  |
| `--glass-opacity`        | number           | `0.7`           | Opacité du fond (0 à 1) |
| `--glass-blur`           | length           | `10px`          | Intensité du flou       |
| `--glass-saturate`       | percentage       | `180%`          | Saturation des couleurs |
| `--glass-border-opacity` | number           | `0.18`          | Opacité de la bordure   |
| `--glass-border-width`   | length           | `1px`           | Épaisseur de la bordure |

### Valeurs courantes pour `--glass-blur`

```css
/* Intensités de flou */
--glass-blur: 4px; /* Subtle - léger flou */
--glass-blur: 10px; /* Standard - flou moyen (défaut) */
--glass-blur: 16px; /* Strong - flou prononcé */
--glass-blur: 24px; /* Extreme - très flouté */
--glass-blur: 32px; /* Ultra - effet givré intense */
```

### Valeurs pour `--glass-opacity`

```css
--glass-opacity: 0.3; /* Très transparent */
--glass-opacity: 0.5; /* Semi-transparent */
--glass-opacity: 0.7; /* Opaque (défaut) */
--glass-opacity: 0.9; /* Presque opaque */
```

### Valeurs pour `--glass-saturate`

```css
--glass-saturate: 100%; /* Pas de boost */
--glass-saturate: 150%; /* Léger boost */
--glass-saturate: 180%; /* Standard (défaut) */
--glass-saturate: 200%; /* Fort boost */
```

## 📚 Exemples détaillés

### Exemple 1 : Navigation bar en glass

```html
<nav class="glass-navbar">
  <div class="container-fluid">
    <div class="navbar-content">
      <div class="logo">Brand</div>
      <div class="nav-links">
        <a href="#">Accueil</a>
        <a href="#">Produits</a>
        <a href="#">À propos</a>
        <a href="#">Contact</a>
      </div>
      <button class="glass-effect glass-effect--dark">Connexion</button>
    </div>
  </div>
</nav>

<style>
  .glass-navbar {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    z-index: 1000;
    padding: 1rem 0;
    background: rgba(255, 255, 255, 0.7);
    backdrop-filter: blur(10px) saturate(180%);
    -webkit-backdrop-filter: blur(10px) saturate(180%);
    border-bottom: 1px solid rgba(255, 255, 255, 0.18);
  }

  .navbar-content {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .logo {
    font-size: 1.5rem;
    font-weight: 700;
  }

  .nav-links {
    display: flex;
    gap: 2rem;
  }

  .nav-links a {
    text-decoration: none;
    color: #374151;
    font-weight: 500;
    transition: color 0.3s;
  }

  .nav-links a:hover {
    color: #3b82f6;
  }

  button {
    padding: 0.5rem 1.5rem;
    border: none;
    border-radius: 0.5rem;
    cursor: pointer;
    font-weight: 600;
  }
</style>
```

### Exemple 2 : Modal en glassmorphism

```html
<div class="modal-overlay">
  <div class="glass-modal glass-effect glass-effect--light">
    <header class="modal-header">
      <h2>Confirmer l'action</h2>
      <button class="close-btn">×</button>
    </header>

    <div class="modal-content">
      <p>Êtes-vous sûr de vouloir continuer cette action ?</p>
      <p>Cette opération est irréversible.</p>
    </div>

    <footer class="modal-footer">
      <button class="btn glass-effect glass-effect--transparent">
        Annuler
      </button>
      <button class="btn glass-effect glass-effect--blue">Confirmer</button>
    </footer>
  </div>
</div>

<style>
  .modal-overlay {
    position: fixed;
    inset: 0;
    background: rgba(0, 0, 0, 0.5);
    backdrop-filter: blur(4px);
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 2000;
  }

  .glass-modal {
    width: 90%;
    max-width: 500px;
    border-radius: 1rem;
    overflow: hidden;
  }

  .modal-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1.5rem;
    border-bottom: 1px solid rgba(255, 255, 255, 0.18);
  }

  .modal-header h2 {
    margin: 0;
  }

  .close-btn {
    font-size: 2rem;
    border: none;
    background: none;
    cursor: pointer;
    color: #6b7280;
    line-height: 1;
  }

  .modal-content {
    padding: 1.5rem;
  }

  .modal-footer {
    display: flex;
    justify-content: flex-end;
    gap: 0.75rem;
    padding: 1.5rem;
    border-top: 1px solid rgba(255, 255, 255, 0.18);
  }

  .btn {
    padding: 0.75rem 1.5rem;
    border: none;
    border-radius: 0.5rem;
    cursor: pointer;
    font-weight: 600;
  }
</style>
```

### Exemple 3 : Cards colorées en glass

```html
<div class="glass-cards-grid">
  <div class="glass-card glass-effect glass-effect--blue">
    <div class="icon">🚀</div>
    <h3>Performance</h3>
    <p>Vitesse optimale pour vos projets</p>
  </div>

  <div class="glass-card glass-effect glass-effect--purple">
    <div class="icon">🎨</div>
    <h3>Design</h3>
    <p>Interface moderne et élégante</p>
  </div>

  <div class="glass-card glass-effect glass-effect--green">
    <div class="icon">🔒</div>
    <h3>Sécurité</h3>
    <p>Protection des données garantie</p>
  </div>

  <div class="glass-card glass-effect glass-effect--orange">
    <div class="icon">📈</div>
    <h3>Analytics</h3>
    <p>Insights en temps réel</p>
  </div>
</div>

<style>
  body {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    min-height: 100vh;
    padding: 4rem 2rem;
  }

  .glass-cards-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 2rem;
    max-width: 1200px;
    margin: 0 auto;
  }

  .glass-card {
    padding: 2rem;
    border-radius: 1rem;
    text-align: center;
    color: white;
    transition: transform 0.3s ease;
  }

  .glass-card:hover {
    transform: translateY(-4px);
  }

  .icon {
    font-size: 3rem;
    margin-bottom: 1rem;
  }

  .glass-card h3 {
    margin: 0 0 0.5rem 0;
    font-size: 1.5rem;
  }

  .glass-card p {
    margin: 0;
    opacity: 0.9;
  }
</style>
```

### Exemple 4 : Dashboard sidebar

```html
<div class="dashboard-layout">
  <aside class="glass-sidebar glass-effect glass-effect--dark">
    <div class="sidebar-header">
      <h2>Dashboard</h2>
    </div>

    <nav class="sidebar-nav">
      <a href="#" class="nav-item active">
        <span class="icon">📊</span>
        <span>Overview</span>
      </a>
      <a href="#" class="nav-item">
        <span class="icon">📈</span>
        <span>Analytics</span>
      </a>
      <a href="#" class="nav-item">
        <span class="icon">👥</span>
        <span>Users</span>
      </a>
      <a href="#" class="nav-item">
        <span class="icon">⚙️</span>
        <span>Settings</span>
      </a>
    </nav>

    <div class="sidebar-footer">
      <div class="user-profile">
        <img src="avatar.jpg" alt="User" class="avatar" />
        <div>
          <strong>John Doe</strong>
          <p>john@example.com</p>
        </div>
      </div>
    </div>
  </aside>

  <main class="dashboard-content">
    <h1>Dashboard Content</h1>
    <div class="stats-grid">
      <!-- Content -->
    </div>
  </main>
</div>

<style>
  .dashboard-layout {
    display: flex;
    min-height: 100vh;
    background: linear-gradient(135deg, #1e3a8a 0%, #3b0764 100%);
  }

  .glass-sidebar {
    width: 280px;
    padding: 2rem 0;
    display: flex;
    flex-direction: column;
  }

  .sidebar-header {
    padding: 0 1.5rem 2rem;
    border-bottom: 1px solid rgba(255, 255, 255, 0.1);
  }

  .sidebar-header h2 {
    margin: 0;
    color: white;
  }

  .sidebar-nav {
    flex: 1;
    padding: 1rem 0;
  }

  .nav-item {
    display: flex;
    align-items: center;
    gap: 1rem;
    padding: 0.75rem 1.5rem;
    color: rgba(255, 255, 255, 0.7);
    text-decoration: none;
    transition: all 0.3s;
  }

  .nav-item:hover,
  .nav-item.active {
    background: rgba(255, 255, 255, 0.1);
    color: white;
  }

  .sidebar-footer {
    padding: 1.5rem;
    border-top: 1px solid rgba(255, 255, 255, 0.1);
  }

  .user-profile {
    display: flex;
    align-items: center;
    gap: 1rem;
    color: white;
  }

  .avatar {
    width: 40px;
    height: 40px;
    border-radius: 50%;
  }

  .user-profile p {
    margin: 0;
    font-size: 0.875rem;
    opacity: 0.7;
  }

  .dashboard-content {
    flex: 1;
    padding: 2rem;
    color: white;
  }
</style>
```

### Exemple 5 : Pricing cards avec glassmorphism

```html
<section class="pricing-section">
  <div class="container-fluid container-fluid--lg">
    <h2 class="section-title">Tarifs Transparents</h2>

    <div class="pricing-grid">
      <div class="pricing-card glass-effect glass-effect--frosted">
        <h3>Starter</h3>
        <div class="price">
          <span class="amount">29€</span>
          <span class="period">/mois</span>
        </div>
        <ul class="features">
          <li>✓ 5 projets</li>
          <li>✓ 10 Go stockage</li>
          <li>✓ Support email</li>
          <li>✓ 99.9% uptime</li>
        </ul>
        <button class="btn glass-effect glass-effect--dark">Choisir</button>
      </div>

      <div
        class="pricing-card pricing-card--featured glass-effect glass-effect--blue"
      >
        <div class="badge">Populaire</div>
        <h3>Professional</h3>
        <div class="price">
          <span class="amount">79€</span>
          <span class="period">/mois</span>
        </div>
        <ul class="features">
          <li>✓ Projets illimités</li>
          <li>✓ 100 Go stockage</li>
          <li>✓ Support prioritaire</li>
          <li>✓ 99.99% uptime</li>
        </ul>
        <button class="btn glass-effect glass-effect--light">Choisir</button>
      </div>

      <div class="pricing-card glass-effect glass-effect--frosted">
        <h3>Enterprise</h3>
        <div class="price">
          <span class="amount">Custom</span>
        </div>
        <ul class="features">
          <li>✓ Tout illimité</li>
          <li>✓ Storage illimité</li>
          <li>✓ Support dédié 24/7</li>
          <li>✓ SLA personnalisé</li>
        </ul>
        <button class="btn glass-effect glass-effect--dark">Contact</button>
      </div>
    </div>
  </div>
</section>

<style>
  .pricing-section {
    min-height: 100vh;
    padding: 6rem 2rem;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    display: flex;
    align-items: center;
  }

  .section-title {
    text-align: center;
    font-size: 3rem;
    color: white;
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
    padding: 2.5rem;
    border-radius: 1rem;
    color: white;
    position: relative;
    transition: transform 0.3s ease;
  }

  .pricing-card:hover {
    transform: translateY(-8px);
  }

  .pricing-card--featured {
    transform: scale(1.05);
  }

  .badge {
    position: absolute;
    top: -12px;
    right: 20px;
    background: rgba(255, 255, 255, 0.9);
    color: #3b82f6;
    padding: 0.25rem 1rem;
    border-radius: 9999px;
    font-size: 0.875rem;
    font-weight: 600;
  }

  .pricing-card h3 {
    margin: 0 0 1.5rem 0;
    font-size: 1.5rem;
  }

  .price {
    margin-bottom: 2rem;
  }

  .amount {
    font-size: 3rem;
    font-weight: 700;
  }

  .period {
    opacity: 0.7;
  }

  .features {
    list-style: none;
    padding: 0;
    margin: 0 0 2rem 0;
  }

  .features li {
    padding: 0.5rem 0;
    opacity: 0.9;
  }

  .btn {
    width: 100%;
    padding: 1rem;
    border: none;
    border-radius: 0.5rem;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.3s;
  }

  .btn:hover {
    transform: scale(1.02);
  }
</style>
```

### Exemple 6 : Toast notifications

```html
<div class="toast-container">
  <div class="toast glass-effect glass-effect--green">
    <span class="toast-icon">✓</span>
    <div class="toast-content">
      <strong>Succès!</strong>
      <p>Votre action a été effectuée avec succès</p>
    </div>
    <button class="toast-close">×</button>
  </div>

  <div class="toast glass-effect glass-effect--blue">
    <span class="toast-icon">ℹ</span>
    <div class="toast-content">
      <strong>Information</strong>
      <p>Une nouvelle mise à jour est disponible</p>
    </div>
    <button class="toast-close">×</button>
  </div>

  <div class="toast glass-effect glass-effect--orange">
    <span class="toast-icon">⚠</span>
    <div class="toast-content">
      <strong>Attention</strong>
      <p>Votre session expire dans 5 minutes</p>
    </div>
    <button class="toast-close">×</button>
  </div>
</div>

<style>
  .toast-container {
    position: fixed;
    top: 2rem;
    right: 2rem;
    display: flex;
    flex-direction: column;
    gap: 1rem;
    z-index: 3000;
  }

  .toast {
    display: flex;
    align-items: center;
    gap: 1rem;
    padding: 1rem 1.5rem;
    border-radius: 0.75rem;
    min-width: 350px;
    color: white;
    animation: slideIn 0.3s ease;
  }

  @keyframes slideIn {
    from {
      transform: translateX(400px);
      opacity: 0;
    }
    to {
      transform: translateX(0);
      opacity: 1;
    }
  }

  .toast-icon {
    font-size: 1.5rem;
    flex-shrink: 0;
  }

  .toast-content {
    flex: 1;
  }

  .toast-content strong {
    display: block;
    margin-bottom: 0.25rem;
  }

  .toast-content p {
    margin: 0;
    font-size: 0.875rem;
    opacity: 0.9;
  }

  .toast-close {
    font-size: 1.5rem;
    border: none;
    background: none;
    color: white;
    cursor: pointer;
    opacity: 0.7;
    transition: opacity 0.3s;
  }

  .toast-close:hover {
    opacity: 1;
  }
</style>
```

### Exemple 7 : Hero section avec glass

```html
<section class="hero-glass">
  <div class="hero-background"></div>

  <div class="hero-content glass-effect glass-effect--frosted">
    <h1>Bienvenue dans le futur</h1>
    <p class="lead">
      Découvrez nos solutions innovantes pour transformer votre business
    </p>
    <div class="hero-actions">
      <button class="btn-primary glass-effect glass-effect--blue">
        Commencer gratuitement
      </button>
      <button class="btn-secondary glass-effect glass-effect--transparent">
        En savoir plus
      </button>
    </div>
  </div>
</section>

<style>
  .hero-glass {
    position: relative;
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 2rem;
    overflow: hidden;
  }

  .hero-background {
    position: absolute;
    inset: 0;
    background: url("hero-bg.jpg") center/cover, linear-gradient(
        135deg,
        #667eea 0%,
        #764ba2 100%
      );
    filter: brightness(0.7);
  }

  .hero-content {
    position: relative;
    z-index: 1;
    max-width: 800px;
    padding: 4rem;
    border-radius: 2rem;
    text-align: center;
    color: white;
  }

  .hero-content h1 {
    font-size: clamp(2.5rem, 6vw, 4rem);
    margin: 0 0 1.5rem 0;
  }

  .lead {
    font-size: 1.25rem;
    margin: 0 0 2rem 0;
    opacity: 0.9;
  }

  .hero-actions {
    display: flex;
    gap: 1rem;
    justify-content: center;
    flex-wrap: wrap;
  }

  .btn-primary,
  .btn-secondary {
    padding: 1rem 2rem;
    border: none;
    border-radius: 0.75rem;
    font-size: 1.125rem;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.3s;
  }

  .btn-primary:hover,
  .btn-secondary:hover {
    transform: translateY(-2px);
  }
</style>
```

## 🎨 Personnalisation avancée

### Glass avec dégradé

```html
<div class="glass-gradient">
  <h3>Glass avec dégradé</h3>
</div>

<style>
  .glass-gradient {
    background: linear-gradient(
      135deg,
      rgba(255, 255, 255, 0.4),
      rgba(255, 255, 255, 0.1)
    );
    backdrop-filter: blur(10px) saturate(180%);
    border: 1px solid rgba(255, 255, 255, 0.18);
    padding: 2rem;
    border-radius: 1rem;
  }
</style>
```

### Glass avec animation

```html
<div class="glass-animated glass-effect">
  <h3>Animated Glass</h3>
</div>

<style>
  @keyframes glassShimmer {
    0%,
    100% {
      --glass-opacity: 0.6;
    }
    50% {
      --glass-opacity: 0.8;
    }
  }

  .glass-animated {
    animation: glassShimmer 3s ease-in-out infinite;
  }
</style>
```

### Glass responsive

```html
<div class="glass-responsive glass-effect">
  <h3>Responsive Glass</h3>
</div>

<style>
  .glass-responsive {
    /* Mobile : flou réduit (performance) */
    --glass-blur: 6px;
  }

  @media (min-width: 768px) {
    .glass-responsive {
      --glass-blur: 10px;
    }
  }

  @media (min-width: 1024px) {
    .glass-responsive {
      --glass-blur: 16px;
    }
  }
</style>
```

### Dark mode adaptatif

```scss
.glass-effect {
  --glass-bg: 255, 255, 255;
  --glass-opacity: 0.7;

  @media (prefers-color-scheme: dark) {
    --glass-bg: 0, 0, 0;
    --glass-opacity: 0.5;
    color: white;
  }
}
```

## 🎯 Cas d'usage courants

### 1. Navigation bars

```html
<nav class="glass-effect" style="position: fixed; top: 0; width: 100%">
  Navigation
</nav>
```

### 2. Modals / Dialogs

```html
<div class="modal glass-effect glass-effect--light">Modal content</div>
```

### 3. Cards flottantes

```html
<div class="card glass-effect glass-effect--frosted">Card content</div>
```

### 4. Sidebars

```html
<aside class="sidebar glass-effect glass-effect--dark">Sidebar</aside>
```

### 5. Tooltips / Popovers

```html
<div class="tooltip glass-effect glass-effect--dark">Tooltip</div>
```

### 6. Hero overlays

```html
<div class="hero-overlay glass-effect glass-effect--transparent">
  Hero content
</div>
```

### 7. Notifications / Toasts

```html
<div class="toast glass-effect glass-effect--green">Success!</div>
```

## 🔧 Combinaison avec autres utilitaires

### Avec Shadow Wrapper

```html
<div class="glass-effect glass-effect--light shadow-wrapper shadow-wrapper--xl">
  <h3>Glass + Shadow</h3>
  <p>Combinaison d'effets</p>
</div>
```

### Avec Container Fluid

```html
<section class="glass-effect">
  <div class="container-fluid container-fluid--lg">
    <h2>Section avec glass</h2>
  </div>
</section>
```

### Avec Gap Wrapper

```html
<div class="glass-effect">
  <div class="gap-wrapper gap-wrapper--column gap-wrapper--lg">
    <h3>Titre</h3>
    <p>Paragraphe</p>
    <button>Action</button>
  </div>
</div>
```

## 📱 Comportement responsive

### Performance sur mobile

```scss
// Réduire le flou sur mobile pour performance
@media (max-width: 640px) {
  .glass-effect {
    --glass-blur: 6px; // Au lieu de 10px
  }
}

// Désactiver backdrop-filter sur très vieux mobiles
@media (max-width: 480px) {
  .glass-effect {
    backdrop-filter: none;
    -webkit-backdrop-filter: none;
    --glass-opacity: 0.9; // Augmenter l'opacité
  }
}
```

### Stratégie progressive

```scss
.glass-effect {
  // Fallback de base
  background: rgba(255, 255, 255, 0.8);

  // Glass si supporté
  @supports (backdrop-filter: blur(10px)) {
    background: rgba(var(--glass-bg), var(--glass-opacity));
    backdrop-filter: blur(var(--glass-blur)) saturate(var(--glass-saturate));
  }
}
```

## ⚡ Performance & Bonnes pratiques

### ✅ À faire

```html
<!-- Bon : Utiliser backdrop-filter modérément -->
<div class="glass-effect" style="--glass-blur: 10px">
  <!-- Bon : Limiter la zone de flou -->
  <div class="glass-effect" style="width: fit-content">
    <!-- Bon : Utiliser will-change pour animations -->
    <div class="glass-effect" style="will-change: backdrop-filter">
      <!-- Bon : Background coloré derrière -->
      <body style="background: linear-gradient(...)">
        <div class="glass-effect">Content</div>
      </body>
    </div>
  </div>
</div>
```

### ❌ À éviter

```html
<!-- Mauvais : Flou trop intense (performance) -->
<div class="glass-effect" style="--glass-blur: 50px">
  <!-- Mauvais : Trop d'éléments glass imbriqués -->
  <div class="glass-effect">
    <div class="glass-effect">
      <div class="glass-effect">...</div>
    </div>
  </div>

  <!-- Mauvais : Glass sur fond uni (pas d'effet visible) -->
  <body style="background: white">
    <div class="glass-effect">...</div>
  </body>

  <!-- Mauvais : Animations rapides de backdrop-filter -->
  <div style="animation: blur 0.1s"></div>
</div>
```

### Conseils de performance

```scss
// ✅ Utiliser will-change pour animations smooth
.glass-effect {
  will-change: backdrop-filter;
  transition: backdrop-filter 0.3s ease;
}

// ✅ Limiter la portée du flou
.glass-effect {
  isolation: isolate; // Crée un contexte de rendu
}

// ❌ Éviter les animations fréquentes
// Animation rapide de backdrop-filter = laggy
@keyframes badBlur {
  from {
    backdrop-filter: blur(0);
  }
  to {
    backdrop-filter: blur(20px);
  }
}

// ✅ Préférer opacity pour animations
@keyframes goodFade {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
```

## 🌐 Compatibilité navigateurs

| Navigateur | Version minimale | Support               |
| ---------- | ---------------- | --------------------- |
| Chrome     | 76+              | ✅ Complet            |
| Firefox    | 103+             | ✅ Complet            |
| Safari     | 9+               | ✅ Complet (-webkit-) |
| Edge       | 79+              | ✅ Complet            |
| Opera      | 63+              | ✅ Complet            |

**Note importante** : `backdrop-filter` nécessite des navigateurs modernes. Toujours prévoir un fallback !

### Détection de support

```javascript
// Test de support
if (CSS.supports("backdrop-filter", "blur(10px)")) {
  console.log("Glassmorphism supporté!");
} else {
  console.log("Fallback nécessaire");
}
```

### Fallback robuste

```scss
.glass-effect {
  // Fallback : fond plus opaque
  background: rgba(var(--glass-bg), calc(var(--glass-opacity) + 0.2));
  border: var(--glass-border-width) solid rgba(
      var(--glass-bg),
      calc(var(--glass-border-opacity) + 0.1)
    );

  // Glass si supporté
  @supports (backdrop-filter: blur(1px)) {
    background: rgba(var(--glass-bg), var(--glass-opacity));
    backdrop-filter: blur(var(--glass-blur)) saturate(var(--glass-saturate));
    -webkit-backdrop-filter: blur(var(--glass-blur)) saturate(
        var(--glass-saturate)
      );
  }
}
```

## 🐛 Troubleshooting

### Problème : Pas d'effet visible

**Solution** : Vérifiez qu'il y a du contenu derrière

```html
<!-- ❌ Mauvais : Fond uni -->
<body style="background: white">
  <div class="glass-effect">Pas d'effet visible</div>
</body>

<!-- ✅ Bon : Fond avec image ou dégradé -->
<body style="background: linear-gradient(...)">
  <div class="glass-effect">Effet visible!</div>
</body>
```

### Problème : Performance lente

**Solution** : Réduisez l'intensité du flou

```css
/* Au lieu de */
--glass-blur: 24px; /* Très coûteux */

/* Utilisez */
--glass-blur: 10px; /* Plus performant */
```

### Problème : Bordures floues

**Solution** : Le flou affecte aussi les bordures internes

```scss
// Ajoutez une bordure externe
.glass-effect {
  outline: 1px solid rgba(255, 255, 255, 0.1);
  outline-offset: -1px;
}
```

### Problème : Effet trop subtil

**Solution** : Augmentez le contraste

```css
/* Augmentez l'opacité et la saturation */
--glass-opacity: 0.8;
--glass-saturate: 200%;

/* Ou ajoutez une ombre */
box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
```

## 📦 Classes complètes disponibles

```scss
// Classes de base
.glass-effect {
  /* Base */
}

// Couleurs
.glass-effect--light {
  /* Blanc */
}
.glass-effect--dark {
  /* Noir */
}
.glass-effect--frosted {
  /* Très transparent */
}
.glass-effect--blue {
  /* Bleu */
}
.glass-effect--purple {
  /* Violet */
}
.glass-effect--pink {
  /* Rose */
}
.glass-effect--green {
  /* Vert */
}
.glass-effect--orange {
  /* Orange */
}

// Intensité de flou
.glass-effect--blur-sm {
  --glass-blur: 4px;
}
.glass-effect--blur-md {
  --glass-blur: 10px;
}
.glass-effect--blur-lg {
  --glass-blur: 16px;
}
.glass-effect--blur-xl {
  --glass-blur: 24px;
}

// Opacité
.glass-effect--transparent {
  --glass-opacity: 0.4;
}
.glass-effect--semi {
  --glass-opacity: 0.6;
}
.glass-effect--opaque {
  --glass-opacity: 0.8;
}

// Bordures
.glass-effect--no-border {
  border: none;
}
.glass-effect--thick-border {
  /* Bordure épaisse */
}

// Effets spéciaux
.glass-effect--shine {
  /* Brillance hover */
}
.glass-effect--no-saturate {
  --glass-saturate: 100%;
}
.glass-effect--hyper-saturate {
  --glass-saturate: 200%;
}
```

## 🎓 Ressources complémentaires

- [Backdrop-filter - MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/backdrop-filter)
- [Glassmorphism - CSS Tricks](https://css-tricks.com/glassmorphism/)
- [Glassmorphism Generator](https://hype4.academy/tools/glassmorphism-generator)
- [Can I Use - backdrop-filter](https://caniuse.com/css-backdrop-filter)

## 📝 Changelog

- **v1.0** - Version initiale avec backdrop-filter
- **v1.1** - Ajout des variantes colorées
- **v1.2** - Support du fallback pour anciens navigateurs
- **v1.3** - Ajout des effets spéciaux (shine, saturate)
- **v1.4** - Optimisations performance pour mobile
- **v1.5** - Support du dark mode automatique

---

**Made with ❤️ for modern glass interfaces**
