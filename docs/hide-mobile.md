# Responsive Visibility Utility

> Contrôle précis de la visibilité des éléments selon les breakpoints pour une expérience responsive optimale

## 📋 Description

**Responsive Visibility** est un utilitaire CSS qui permet de contrôler la visibilité des éléments selon les tailles d'écran (mobile, tablet, desktop). Cacher ou afficher des éléments de manière responsive est essentiel pour adapter l'interface et l'expérience utilisateur à chaque device.

### ✨ Caractéristiques principales

- 📱 **Hide Mobile** : Cacher sur mobile (< 768px)
- 💻 **Hide Desktop** : Cacher sur desktop (≥ 1024px)
- 📊 **Hide Tablet** : Cacher sur tablet (768px - 1023px)
- 👁️ **Show Only** : Afficher uniquement sur un breakpoint
- 🖨️ **Hide Print** : Cacher à l'impression
- 🔧 **Breakpoints** : Personnalisables via variables
- ♿ **Accessibilité** : Options pour screen readers
- 🎯 **Mobile-first** : Approche mobile-first par défaut

## 🚀 Installation

### Code SCSS

```scss
// _responsive-visibility.scss

// Variables de breakpoints
:root {
  --breakpoint-mobile: 768px;
  --breakpoint-tablet: 1024px;
  --breakpoint-desktop: 1280px;
}

// ============================================
// HIDE UTILITIES (cacher sur...)
// ============================================

// Cacher sur mobile (< 768px)
.hide-mobile {
  @media (max-width: 767px) {
    display: none !important;
  }
}

// Cacher sur tablet (768px - 1023px)
.hide-tablet {
  @media (min-width: 768px) and (max-width: 1023px) {
    display: none !important;
  }
}

// Cacher sur desktop (≥ 1024px)
.hide-desktop {
  @media (min-width: 1024px) {
    display: none !important;
  }
}

// Cacher sur large desktop (≥ 1280px)
.hide-desktop-lg {
  @media (min-width: 1280px) {
    display: none !important;
  }
}

// ============================================
// SHOW ONLY UTILITIES (afficher uniquement sur...)
// ============================================

// Afficher uniquement sur mobile
.show-mobile,
.mobile-only {
  @media (min-width: 768px) {
    display: none !important;
  }
}

// Afficher uniquement sur tablet
.show-tablet,
.tablet-only {
  display: none !important;

  @media (min-width: 768px) and (max-width: 1023px) {
    display: block !important;
  }
}

// Afficher uniquement sur desktop
.show-desktop,
.desktop-only {
  display: none !important;

  @media (min-width: 1024px) {
    display: block !important;
  }
}

// Afficher uniquement sur large desktop
.show-desktop-lg,
.desktop-lg-only {
  display: none !important;

  @media (min-width: 1280px) {
    display: block !important;
  }
}

// ============================================
// COMBINAISONS (cacher sur plusieurs breakpoints)
// ============================================

// Cacher sur mobile ET tablet
.hide-mobile-tablet {
  @media (max-width: 1023px) {
    display: none !important;
  }
}

// Cacher sur tablet ET desktop
.hide-tablet-desktop {
  @media (min-width: 768px) {
    display: none !important;
  }
}

// Afficher uniquement sur mobile et tablet
.show-mobile-tablet {
  @media (min-width: 1024px) {
    display: none !important;
  }
}

// ============================================
// BREAKPOINTS NUMÉRIQUES (approche utility-first)
// ============================================

// Cacher en dessous de...
.hide-below-sm {
  @media (max-width: 639px) {
    display: none !important;
  }
}

.hide-below-md {
  @media (max-width: 767px) {
    display: none !important;
  }
}

.hide-below-lg {
  @media (max-width: 1023px) {
    display: none !important;
  }
}

.hide-below-xl {
  @media (max-width: 1279px) {
    display: none !important;
  }
}

// Cacher au-dessus de...
.hide-above-sm {
  @media (min-width: 640px) {
    display: none !important;
  }
}

.hide-above-md {
  @media (min-width: 768px) {
    display: none !important;
  }
}

.hide-above-lg {
  @media (min-width: 1024px) {
    display: none !important;
  }
}

.hide-above-xl {
  @media (min-width: 1280px) {
    display: none !important;
  }
}

// ============================================
// ORIENTATION
// ============================================

// Cacher en mode portrait
.hide-portrait {
  @media (orientation: portrait) {
    display: none !important;
  }
}

// Cacher en mode paysage
.hide-landscape {
  @media (orientation: landscape) {
    display: none !important;
  }
}

// Afficher uniquement en portrait
.show-portrait {
  @media (orientation: landscape) {
    display: none !important;
  }
}

// Afficher uniquement en paysage
.show-landscape {
  @media (orientation: portrait) {
    display: none !important;
  }
}

// ============================================
// PRINT
// ============================================

// Cacher à l'impression
.hide-print {
  @media print {
    display: none !important;
  }
}

// Afficher uniquement à l'impression
.show-print {
  display: none !important;

  @media print {
    display: block !important;
  }
}

// ============================================
// ACCESSIBILITÉ (Screen Readers)
// ============================================

// Cacher visuellement mais garder pour screen readers
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
  border-width: 0;
}

// Cacher aussi pour screen readers
.hide-all {
  display: none !important;
  visibility: hidden !important;
}

// Cacher visuellement sur mobile mais garder pour SR
.sr-only-mobile {
  @media (max-width: 767px) {
    position: absolute;
    width: 1px;
    height: 1px;
    padding: 0;
    margin: -1px;
    overflow: hidden;
    clip: rect(0, 0, 0, 0);
    white-space: nowrap;
    border-width: 0;
  }
}

// ============================================
// DISPLAY TYPES (avec responsive)
// ============================================

// Flex responsive
.flex-mobile {
  @media (max-width: 767px) {
    display: flex !important;
  }
}

.flex-tablet {
  @media (min-width: 768px) and (max-width: 1023px) {
    display: flex !important;
  }
}

.flex-desktop {
  @media (min-width: 1024px) {
    display: flex !important;
  }
}

// Grid responsive
.grid-mobile {
  @media (max-width: 767px) {
    display: grid !important;
  }
}

.grid-tablet {
  @media (min-width: 768px) and (max-width: 1023px) {
    display: grid !important;
  }
}

.grid-desktop {
  @media (min-width: 1024px) {
    display: grid !important;
  }
}

// Block responsive
.block-mobile {
  @media (max-width: 767px) {
    display: block !important;
  }
}

.block-tablet {
  @media (min-width: 768px) and (max-width: 1023px) {
    display: block !important;
  }
}

.block-desktop {
  @media (min-width: 1024px) {
    display: block !important;
  }
}

// ============================================
// VISIBILITY (sans affecter le layout)
// ============================================

// Invisible mais prend de l'espace
.invisible-mobile {
  @media (max-width: 767px) {
    visibility: hidden !important;
  }
}

.invisible-tablet {
  @media (min-width: 768px) and (max-width: 1023px) {
    visibility: hidden !important;
  }
}

.invisible-desktop {
  @media (min-width: 1024px) {
    visibility: hidden !important;
  }
}

// ============================================
// OPACITY RESPONSIVE
// ============================================

.opacity-0-mobile {
  @media (max-width: 767px) {
    opacity: 0 !important;
    pointer-events: none !important;
  }
}

.opacity-0-tablet {
  @media (min-width: 768px) and (max-width: 1023px) {
    opacity: 0 !important;
    pointer-events: none !important;
  }
}

.opacity-0-desktop {
  @media (min-width: 1024px) {
    opacity: 0 !important;
    pointer-events: none !important;
  }
}
```

### Import dans votre projet

```scss
// Dans styles.scss
@import "utilities/responsive-visibility";
```

## 💡 Utilisation de base

### Exemple 1 : Cacher sur mobile

```html
<!-- Navigation complète cachée sur mobile -->
<nav class="hide-mobile">
  <a href="#">Accueil</a>
  <a href="#">À propos</a>
  <a href="#">Services</a>
  <a href="#">Contact</a>
</nav>

<!-- Menu burger visible uniquement sur mobile -->
<button class="show-mobile">☰ Menu</button>
```

### Exemple 2 : Sidebar cachée sur mobile

```html
<div class="layout">
  <!-- Sidebar cachée sur mobile et tablet -->
  <aside class="sidebar hide-mobile-tablet">
    <h3>Filtres</h3>
    <!-- Filtres -->
  </aside>

  <main class="content">
    <!-- Contenu principal -->
  </main>
</div>
```

### Exemple 3 : Images différentes selon l'écran

```html
<div class="hero">
  <!-- Image mobile -->
  <img src="hero-mobile.jpg" class="show-mobile" alt="Hero Mobile" />

  <!-- Image tablet -->
  <img src="hero-tablet.jpg" class="show-tablet" alt="Hero Tablet" />

  <!-- Image desktop -->
  <img src="hero-desktop.jpg" class="show-desktop" alt="Hero Desktop" />
</div>
```

### Exemple 4 : Texte abrégé sur mobile

```html
<div class="card">
  <h3>
    <!-- Titre court sur mobile -->
    <span class="show-mobile">Titre Court</span>

    <!-- Titre complet sur desktop -->
    <span class="hide-mobile">Titre Complet et Détaillé</span>
  </h3>
</div>
```

## 📊 Paramètres

| Variable               | Type   | Défaut   | Description           |
| ---------------------- | ------ | -------- | --------------------- |
| `--breakpoint-mobile`  | length | `768px`  | Limite mobile/tablet  |
| `--breakpoint-tablet`  | length | `1024px` | Limite tablet/desktop |
| `--breakpoint-desktop` | length | `1280px` | Limite desktop/large  |

### Breakpoints par défaut

| Breakpoint | Taille         | Description   |
| ---------- | -------------- | ------------- |
| Mobile     | < 768px        | Smartphones   |
| Tablet     | 768px - 1023px | Tablettes     |
| Desktop    | ≥ 1024px       | Ordinateurs   |
| Desktop LG | ≥ 1280px       | Grands écrans |

### Classes disponibles

| Catégorie        | Classes                                | Description            |
| ---------------- | -------------------------------------- | ---------------------- |
| **Hide**         | hide-mobile, hide-tablet, hide-desktop | Cacher sur breakpoint  |
| **Show**         | show-mobile, show-tablet, show-desktop | Afficher uniquement    |
| **Alias**        | mobile-only, tablet-only, desktop-only | Alias de show-\*       |
| **Combinaisons** | hide-mobile-tablet, show-mobile-tablet | Multi-breakpoints      |
| **Numérique**    | hide-below-md, hide-above-lg           | Approche utility-first |
| **Orientation**  | hide-portrait, show-landscape          | Selon orientation      |
| **Print**        | hide-print, show-print                 | Pour impression        |

## 📚 Exemples détaillés

### Exemple 1 : Navigation responsive complète

```html
<header class="header">
  <div class="container">
    <div class="header-content">
      <div class="logo">
        <img src="logo.svg" alt="Logo" />
      </div>

      <!-- Navigation desktop (cachée sur mobile) -->
      <nav class="nav hide-mobile">
        <a href="#home">Accueil</a>
        <a href="#about">À propos</a>
        <a href="#services">Services</a>
        <a href="#portfolio">Portfolio</a>
        <a href="#team">Équipe</a>
        <a href="#blog">Blog</a>
        <a href="#contact">Contact</a>
      </nav>

      <!-- CTA button desktop -->
      <button class="btn-cta hide-mobile rounded-lg">
        Démarrer gratuitement
      </button>

      <!-- Menu burger mobile (visible uniquement sur mobile) -->
      <button class="menu-burger show-mobile">
        <span></span>
        <span></span>
        <span></span>
      </button>
    </div>

    <!-- Menu mobile full-screen (caché par défaut) -->
    <div class="mobile-menu show-mobile" id="mobileMenu" style="display: none;">
      <nav>
        <a href="#home">Accueil</a>
        <a href="#about">À propos</a>
        <a href="#services">Services</a>
        <a href="#portfolio">Portfolio</a>
        <a href="#team">Équipe</a>
        <a href="#blog">Blog</a>
        <a href="#contact">Contact</a>
      </nav>
      <button class="btn-cta-mobile rounded-lg">Démarrer gratuitement</button>
    </div>
  </div>
</header>

<style>
  .header {
    background: white;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    padding: 1rem 0;
  }

  .header-content {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .nav {
    display: flex;
    gap: 2rem;
  }

  .nav a {
    text-decoration: none;
    color: #374151;
    font-weight: 500;
    transition: color 300ms;
  }

  .nav a:hover {
    color: #3b82f6;
  }

  .btn-cta {
    padding: 0.75rem 1.5rem;
    background: #3b82f6;
    color: white;
    border: none;
    cursor: pointer;
    font-weight: 600;
  }

  .menu-burger {
    display: flex;
    flex-direction: column;
    gap: 4px;
    background: none;
    border: none;
    cursor: pointer;
    padding: 0.5rem;
  }

  .menu-burger span {
    width: 24px;
    height: 3px;
    background: #374151;
    border-radius: 2px;
  }

  .mobile-menu {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100vh;
    background: white;
    z-index: 1000;
    padding: 2rem;
  }

  .mobile-menu nav {
    display: flex;
    flex-direction: column;
    gap: 1.5rem;
    margin-bottom: 2rem;
  }

  .mobile-menu a {
    font-size: 1.5rem;
    color: #374151;
    text-decoration: none;
  }

  .btn-cta-mobile {
    width: 100%;
    padding: 1rem;
    background: #3b82f6;
    color: white;
    border: none;
    font-weight: 600;
    font-size: 1.125rem;
  }
</style>
```

### Exemple 2 : Dashboard avec sidebar responsive

```html
<div class="dashboard-layout">
  <!-- Sidebar (cachée sur mobile, visible sur desktop) -->
  <aside class="sidebar hide-mobile shadow-wrapper shadow-wrapper--md">
    <div class="sidebar-header">
      <h2>Dashboard</h2>
    </div>

    <nav class="sidebar-nav">
      <a href="#" class="nav-item active">
        <span class="icon">📊</span>
        <span>Vue d'ensemble</span>
      </a>
      <a href="#" class="nav-item">
        <span class="icon">📈</span>
        <span>Statistiques</span>
      </a>
      <a href="#" class="nav-item">
        <span class="icon">👥</span>
        <span>Utilisateurs</span>
      </a>
      <a href="#" class="nav-item">
        <span class="icon">⚙️</span>
        <span>Paramètres</span>
      </a>
      <a href="#" class="nav-item">
        <span class="icon">💬</span>
        <span>Messages</span>
      </a>
      <a href="#" class="nav-item">
        <span class="icon">🔔</span>
        <span>Notifications</span>
      </a>
    </nav>

    <div class="sidebar-footer">
      <div class="user-profile">
        <img src="avatar.jpg" alt="User" class="avatar" />
        <div class="user-info">
          <span class="user-name">Jean Dupont</span>
          <span class="user-role">Admin</span>
        </div>
      </div>
    </div>
  </aside>

  <!-- Main content -->
  <main class="dashboard-main">
    <!-- Header mobile avec menu toggle -->
    <header class="mobile-header show-mobile">
      <button class="menu-toggle">☰</button>
      <h1>Dashboard</h1>
      <button class="notifications">🔔</button>
    </header>

    <!-- Content -->
    <div class="dashboard-content">
      <h1 class="hide-mobile">Vue d'ensemble</h1>

      <!-- Stats grid -->
      <div class="stats-grid">
        <div class="stat-card rounded-xl shadow-wrapper shadow-wrapper--sm">
          <div class="stat-icon">👥</div>
          <div class="stat-info">
            <h3>Utilisateurs</h3>
            <p class="stat-value">1,234</p>
            <p class="stat-change positive hide-mobile">+12% ce mois</p>
          </div>
        </div>

        <div class="stat-card rounded-xl shadow-wrapper shadow-wrapper--sm">
          <div class="stat-icon">💰</div>
          <div class="stat-info">
            <h3>Revenus</h3>
            <p class="stat-value">45,678 €</p>
            <p class="stat-change positive hide-mobile">+23% ce mois</p>
          </div>
        </div>

        <div class="stat-card rounded-xl shadow-wrapper shadow-wrapper--sm">
          <div class="stat-icon">📦</div>
          <div class="stat-info">
            <h3>Commandes</h3>
            <p class="stat-value">567</p>
            <p class="stat-change negative hide-mobile">-5% ce mois</p>
          </div>
        </div>

        <div class="stat-card rounded-xl shadow-wrapper shadow-wrapper--sm">
          <div class="stat-icon">⭐</div>
          <div class="stat-info">
            <h3>Satisfaction</h3>
            <p class="stat-value">4.8/5</p>
            <p class="stat-change positive hide-mobile">+0.3 ce mois</p>
          </div>
        </div>
      </div>

      <!-- Charts section -->
      <div class="charts-section">
        <div class="chart-card rounded-xl shadow-wrapper shadow-wrapper--md">
          <div class="chart-header">
            <h2>Ventes mensuelles</h2>
            <!-- Détails cachés sur mobile -->
            <div class="chart-actions hide-mobile">
              <button class="btn-secondary">Cette semaine</button>
              <button class="btn-secondary">Ce mois</button>
              <button class="btn-primary">Cette année</button>
            </div>
          </div>
          <div
            class="chart-placeholder skeleton skeleton--wave skeleton-rectangle"
            style="height: 300px;"
          ></div>
        </div>
      </div>
    </div>
  </main>
</div>

<style>
  .dashboard-layout {
    display: flex;
    min-height: 100vh;
  }

  .sidebar {
    width: 280px;
    background: white;
    display: flex;
    flex-direction: column;
    position: sticky;
    top: 0;
    height: 100vh;
  }

  .sidebar-header {
    padding: 2rem;
    border-bottom: 1px solid #e5e7eb;
  }

  .sidebar-nav {
    flex: 1;
    padding: 1rem;
    overflow-y: auto;
  }

  .nav-item {
    display: flex;
    align-items: center;
    gap: 1rem;
    padding: 0.75rem 1rem;
    color: #6b7280;
    text-decoration: none;
    border-radius: 0.5rem;
    margin-bottom: 0.5rem;
    transition: all 300ms;
  }

  .nav-item:hover,
  .nav-item.active {
    background: #eff6ff;
    color: #3b82f6;
  }

  .sidebar-footer {
    padding: 1rem;
    border-top: 1px solid #e5e7eb;
  }

  .user-profile {
    display: flex;
    align-items: center;
    gap: 1rem;
  }

  .avatar {
    width: 40px;
    height: 40px;
    border-radius: 50%;
  }

  .user-info {
    display: flex;
    flex-direction: column;
  }

  .user-name {
    font-weight: 600;
    font-size: 0.875rem;
  }

  .user-role {
    font-size: 0.75rem;
    color: #6b7280;
  }

  .dashboard-main {
    flex: 1;
    background: #f9fafb;
  }

  .mobile-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1rem;
    background: white;
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
  }

  .menu-toggle,
  .notifications {
    background: none;
    border: none;
    font-size: 1.5rem;
    cursor: pointer;
  }

  .dashboard-content {
    padding: 2rem;
  }

  @media (max-width: 767px) {
    .dashboard-content {
      padding: 1rem;
    }
  }

  .stats-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 1.5rem;
    margin-bottom: 2rem;
  }

  .stat-card {
    background: white;
    padding: 1.5rem;
    display: flex;
    gap: 1rem;
  }

  .stat-icon {
    font-size: 2.5rem;
  }

  .stat-info h3 {
    margin: 0 0 0.5rem 0;
    font-size: 0.875rem;
    color: #6b7280;
  }

  .stat-value {
    margin: 0 0 0.25rem 0;
    font-size: 1.75rem;
    font-weight: 700;
  }

  .stat-change {
    margin: 0;
    font-size: 0.75rem;
  }

  .stat-change.positive {
    color: #059669;
  }

  .stat-change.negative {
    color: #dc2626;
  }

  .chart-card {
    background: white;
    padding: 2rem;
  }

  .chart-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 1.5rem;
  }

  .chart-actions {
    display: flex;
    gap: 0.5rem;
  }

  .btn-secondary,
  .btn-primary {
    padding: 0.5rem 1rem;
    border: 1px solid #e5e7eb;
    background: white;
    border-radius: 0.5rem;
    cursor: pointer;
    font-size: 0.875rem;
  }

  .btn-primary {
    background: #3b82f6;
    color: white;
    border-color: #3b82f6;
  }
</style>
```

### Exemple 3 : Product cards avec informations adaptatives

```html
<div class="products-grid">
  <div class="product-card rounded-xl shadow-wrapper shadow-wrapper--md">
    <div class="product-image">
      <img src="product.jpg" alt="Product" />
      <span class="badge hide-mobile">Nouveau</span>
    </div>

    <div class="product-info">
      <!-- Titre court sur mobile, complet sur desktop -->
      <h3>
        <span class="show-mobile">iPhone 15 Pro</span>
        <span class="hide-mobile">iPhone 15 Pro - 256GB Titane</span>
      </h3>

      <!-- Description cachée sur mobile -->
      <p class="product-description hide-mobile">
        Le smartphone le plus puissant avec puce A17 Pro, caméra professionnelle
        et design en titane.
      </p>

      <!-- Prix et CTA -->
      <div class="product-footer">
        <div class="price-section">
          <span class="price">1 299 €</span>
          <!-- Prix barré caché sur mobile -->
          <span class="old-price hide-mobile">1 499 €</span>
        </div>

        <!-- Bouton texte complet sur desktop, icône sur mobile -->
        <button class="btn-add rounded-lg">
          <span class="show-mobile">🛒</span>
          <span class="hide-mobile">Ajouter au panier</span>
        </button>
      </div>

      <!-- Features list cachée sur mobile -->
      <ul class="features-list hide-mobile">
        <li>✓ Livraison gratuite</li>
        <li>✓ Garantie 2 ans</li>
        <li>✓ Retour sous 30 jours</li>
      </ul>

      <!-- Rating visible partout -->
      <div class="rating">
        <span class="stars">★★★★★</span>
        <span class="rating-count">(248 avis)</span>
      </div>
    </div>
  </div>

  <!-- Plus de products... -->
</div>

<style>
  .products-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
    gap: 2rem;
    padding: 2rem;
  }

  .product-card {
    background: white;
    overflow: hidden;
  }

  .product-image {
    position: relative;
    width: 100%;
    height: 300px;
  }

  .product-image img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }

  .badge {
    position: absolute;
    top: 1rem;
    right: 1rem;
    padding: 0.5rem 1rem;
    background: #3b82f6;
    color: white;
    border-radius: 9999px;
    font-size: 0.875rem;
    font-weight: 600;
  }

  .product-info {
    padding: 1.5rem;
  }

  .product-info h3 {
    margin: 0 0 0.5rem 0;
    font-size: 1.25rem;
  }

  .product-description {
    margin: 0 0 1rem 0;
    color: #6b7280;
    font-size: 0.875rem;
    line-height: 1.6;
  }

  .product-footer {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 1rem;
  }

  .price {
    font-size: 1.75rem;
    font-weight: 700;
    color: #059669;
  }

  .old-price {
    font-size: 1rem;
    color: #9ca3af;
    text-decoration: line-through;
    margin-left: 0.5rem;
  }

  .btn-add {
    padding: 0.75rem 1.5rem;
    background: #3b82f6;
    color: white;
    border: none;
    cursor: pointer;
    font-weight: 600;
  }

  @media (max-width: 767px) {
    .btn-add {
      padding: 0.75rem;
      font-size: 1.25rem;
    }
  }

  .features-list {
    list-style: none;
    padding: 0;
    margin: 0 0 1rem 0;
    font-size: 0.875rem;
    color: #6b7280;
  }

  .features-list li {
    margin-bottom: 0.25rem;
  }

  .rating {
    display: flex;
    align-items: center;
    gap: 0.5rem;
  }

  .stars {
    color: #fbbf24;
  }

  .rating-count {
    color: #6b7280;
    font-size: 0.875rem;
  }
</style>
```

### Exemple 4 : Hero section avec images responsive

```html
<section class="hero">
  <!-- Background différent par device -->
  <div class="hero-background">
    <!-- Image mobile (portrait) -->
    <img src="hero-mobile.jpg" class="show-mobile" alt="Hero Mobile" />

    <!-- Image tablet (paysage) -->
    <img src="hero-tablet.jpg" class="show-tablet" alt="Hero Tablet" />

    <!-- Image desktop (wide) -->
    <img src="hero-desktop.jpg" class="hide-mobile-tablet" alt="Hero Desktop" />
  </div>

  <div class="hero-content">
    <div class="container">
      <!-- Titre adaptatif -->
      <h1>
        <!-- Version mobile concise -->
        <span class="show-mobile"> Créez votre site web </span>

        <!-- Version desktop complète -->
        <span class="hide-mobile">
          Créez votre site web professionnel en quelques minutes
        </span>
      </h1>

      <!-- Description cachée sur mobile -->
      <p class="hero-description hide-mobile">
        Avec notre éditeur drag & drop, créez un site web magnifique sans aucune
        connaissance en code. Plus de 500 templates disponibles.
      </p>

      <!-- CTA buttons -->
      <div class="hero-cta">
        <!-- Bouton principal -->
        <button class="btn-primary rounded-lg">
          <span class="hide-mobile">Commencer gratuitement</span>
          <span class="show-mobile">Démarrer</span>
        </button>

        <!-- Bouton secondaire caché sur mobile -->
        <button class="btn-secondary rounded-lg hide-mobile">
          Voir la démo
        </button>
      </div>

      <!-- Features badges cachés sur mobile -->
      <div class="hero-features hide-mobile">
        <span class="feature-badge">✓ Sans carte bancaire</span>
        <span class="feature-badge">✓ Annulation à tout moment</span>
        <span class="feature-badge">✓ Support 24/7</span>
      </div>

      <!-- Social proof visible partout -->
      <div class="social-proof">
        <div class="avatars-group">
          <img src="avatar1.jpg" alt="User 1" class="avatar" />
          <img src="avatar2.jpg" alt="User 2" class="avatar" />
          <img src="avatar3.jpg" alt="User 3" class="avatar" />
          <span class="avatars-more">+1000</span>
        </div>
        <p>
          <!-- Texte court sur mobile -->
          <span class="show-mobile"> <strong>1,234</strong> utilisateurs </span>
          <!-- Texte complet sur desktop -->
          <span class="hide-mobile">
            Rejoignez <strong>1,234</strong> créateurs qui ont déjà lancé leur
            site
          </span>
        </p>
      </div>
    </div>
  </div>
</section>

<style>
  .hero {
    position: relative;
    min-height: 600px;
    display: flex;
    align-items: center;
    overflow: hidden;
  }

  .hero-background {
    position: absolute;
    inset: 0;
    z-index: -1;
  }

  .hero-background img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }

  .hero-content {
    position: relative;
    z-index: 1;
    width: 100%;
    padding: 4rem 2rem;
  }

  .hero-content::before {
    content: "";
    position: absolute;
    inset: 0;
    background: linear-gradient(
      to bottom,
      rgba(0, 0, 0, 0.5),
      rgba(0, 0, 0, 0.7)
    );
    z-index: -1;
  }

  .container {
    max-width: 1200px;
    margin: 0 auto;
  }

  h1 {
    font-size: 3rem;
    font-weight: 800;
    color: white;
    margin: 0 0 1.5rem 0;
    line-height: 1.2;
  }

  @media (max-width: 767px) {
    h1 {
      font-size: 2rem;
    }
  }

  .hero-description {
    font-size: 1.25rem;
    color: rgba(255, 255, 255, 0.9);
    margin: 0 0 2rem 0;
    max-width: 600px;
    line-height: 1.6;
  }

  .hero-cta {
    display: flex;
    gap: 1rem;
    margin-bottom: 2rem;
  }

  @media (max-width: 767px) {
    .hero-cta {
      flex-direction: column;
    }
  }

  .btn-primary,
  .btn-secondary {
    padding: 1rem 2.5rem;
    font-size: 1.125rem;
    font-weight: 600;
    border: none;
    cursor: pointer;
    transition: all 300ms;
  }

  .btn-primary {
    background: #3b82f6;
    color: white;
  }

  .btn-secondary {
    background: rgba(255, 255, 255, 0.2);
    color: white;
    backdrop-filter: blur(10px);
    border: 1px solid rgba(255, 255, 255, 0.3);
  }

  .hero-features {
    display: flex;
    gap: 1.5rem;
    margin-bottom: 2rem;
  }

  .feature-badge {
    padding: 0.5rem 1rem;
    background: rgba(255, 255, 255, 0.2);
    backdrop-filter: blur(10px);
    color: white;
    border-radius: 9999px;
    font-size: 0.875rem;
    border: 1px solid rgba(255, 255, 255, 0.3);
  }

  .social-proof {
    display: flex;
    align-items: center;
    gap: 1rem;
    color: white;
  }

  .avatars-group {
    display: flex;
    align-items: center;
  }

  .avatar {
    width: 40px;
    height: 40px;
    border-radius: 50%;
    border: 2px solid white;
    margin-left: -12px;
  }

  .avatar:first-child {
    margin-left: 0;
  }

  .avatars-more {
    margin-left: -12px;
    width: 40px;
    height: 40px;
    border-radius: 50%;
    background: #3b82f6;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 0.75rem;
    font-weight: 600;
  }

  .social-proof p {
    margin: 0;
    font-size: 0.875rem;
  }
</style>
```

### Exemple 5 : Article avec sidebar responsive

```html
<article class="article-layout">
  <div class="container">
    <div class="article-grid">
      <!-- Main content -->
      <div class="article-main">
        <!-- Meta info adaptative -->
        <div class="article-meta">
          <div class="author">
            <img src="author.jpg" alt="Author" class="author-avatar" />
            <div class="author-info">
              <span class="author-name">Marie Dupont</span>
              <!-- Rôle caché sur mobile -->
              <span class="author-role hide-mobile">Rédactrice en chef</span>
            </div>
          </div>

          <div class="article-stats hide-mobile">
            <span>📅 5 nov. 2024</span>
            <span>⏱️ 8 min de lecture</span>
            <span>👁️ 1,234 vues</span>
          </div>

          <!-- Stats simplifiées sur mobile -->
          <div class="article-stats-simple show-mobile">
            <span>5 nov. 2024</span>
            <span>8 min</span>
          </div>
        </div>

        <h1>Le guide complet du design moderne</h1>

        <!-- Featured image -->
        <img
          src="article-featured.jpg"
          alt="Featured"
          class="featured-image rounded-xl"
        />

        <!-- Article content -->
        <div class="article-content">
          <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit...</p>

          <!-- Table of contents cachée sur mobile -->
          <div class="toc hide-mobile rounded-lg">
            <h3>Table des matières</h3>
            <ol>
              <li><a href="#section1">Introduction au design</a></li>
              <li><a href="#section2">Principes fondamentaux</a></li>
              <li><a href="#section3">Outils recommandés</a></li>
              <li><a href="#section4">Conclusion</a></li>
            </ol>
          </div>

          <!-- Plus de contenu... -->
        </div>

        <!-- Share buttons -->
        <div class="share-buttons">
          <!-- Labels cachés sur mobile -->
          <button class="share-btn rounded-lg">
            <span>📘</span>
            <span class="hide-mobile">Partager sur Facebook</span>
          </button>
          <button class="share-btn rounded-lg">
            <span>🐦</span>
            <span class="hide-mobile">Partager sur Twitter</span>
          </button>
          <button class="share-btn rounded-lg">
            <span>💼</span>
            <span class="hide-mobile">Partager sur LinkedIn</span>
          </button>
        </div>
      </div>

      <!-- Sidebar (cachée sur mobile) -->
      <aside class="article-sidebar hide-mobile">
        <!-- Author card -->
        <div class="author-card rounded-xl shadow-wrapper shadow-wrapper--md">
          <img src="author-large.jpg" alt="Author" class="author-card-avatar" />
          <h3>Marie Dupont</h3>
          <p class="author-card-role">Rédactrice en chef</p>
          <p class="author-card-bio">
            Passionnée de design avec 10 ans d'expérience dans le domaine du web
            et du branding.
          </p>
          <button class="btn-follow rounded-lg">Suivre</button>
        </div>

        <!-- Related articles -->
        <div class="related-articles">
          <h3>Articles similaires</h3>
          <a href="#" class="related-article rounded-lg">
            <img src="related1.jpg" alt="Related 1" />
            <h4>Les tendances design 2024</h4>
          </a>
          <a href="#" class="related-article rounded-lg">
            <img src="related2.jpg" alt="Related 2" />
            <h4>Maîtriser la typographie</h4>
          </a>
          <a href="#" class="related-article rounded-lg">
            <img src="related3.jpg" alt="Related 3" />
            <h4>Couleurs et psychologie</h4>
          </a>
        </div>
      </aside>
    </div>
  </div>
</article>

<style>
  .article-layout {
    padding: 3rem 0;
  }

  @media (max-width: 767px) {
    .article-layout {
      padding: 1rem 0;
    }
  }

  .article-grid {
    display: grid;
    grid-template-columns: 1fr 350px;
    gap: 3rem;
  }

  @media (max-width: 767px) {
    .article-grid {
      grid-template-columns: 1fr;
    }
  }

  .article-meta {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 2rem;
    padding-bottom: 1rem;
    border-bottom: 1px solid #e5e7eb;
  }

  .author {
    display: flex;
    align-items: center;
    gap: 1rem;
  }

  .author-avatar {
    width: 48px;
    height: 48px;
    border-radius: 50%;
  }

  .author-info {
    display: flex;
    flex-direction: column;
  }

  .author-name {
    font-weight: 600;
  }

  .author-role {
    font-size: 0.875rem;
    color: #6b7280;
  }

  .article-stats,
  .article-stats-simple {
    display: flex;
    gap: 1.5rem;
    font-size: 0.875rem;
    color: #6b7280;
  }

  @media (max-width: 767px) {
    .article-stats-simple {
      gap: 0.75rem;
      font-size: 0.75rem;
    }
  }

  .article-main h1 {
    font-size: 2.5rem;
    margin: 0 0 2rem 0;
    line-height: 1.2;
  }

  @media (max-width: 767px) {
    .article-main h1 {
      font-size: 1.75rem;
    }
  }

  .featured-image {
    width: 100%;
    height: 400px;
    object-fit: cover;
    margin-bottom: 2rem;
  }

  @media (max-width: 767px) {
    .featured-image {
      height: 250px;
    }
  }

  .article-content {
    font-size: 1.125rem;
    line-height: 1.8;
    color: #374151;
  }

  .toc {
    background: #f9fafb;
    padding: 1.5rem;
    margin: 2rem 0;
  }

  .toc h3 {
    margin: 0 0 1rem 0;
  }

  .toc ol {
    margin: 0;
    padding-left: 1.5rem;
  }

  .toc li {
    margin-bottom: 0.5rem;
  }

  .toc a {
    color: #3b82f6;
    text-decoration: none;
  }

  .share-buttons {
    display: flex;
    gap: 1rem;
    margin-top: 3rem;
    padding-top: 2rem;
    border-top: 1px solid #e5e7eb;
  }

  @media (max-width: 767px) {
    .share-buttons {
      flex-wrap: wrap;
    }
  }

  .share-btn {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    padding: 0.75rem 1.5rem;
    background: white;
    border: 1px solid #e5e7eb;
    cursor: pointer;
    transition: all 300ms;
  }

  @media (max-width: 767px) {
    .share-btn {
      padding: 0.75rem;
      font-size: 1.25rem;
    }
  }

  .share-btn:hover {
    background: #f9fafb;
  }

  .article-sidebar {
    display: flex;
    flex-direction: column;
    gap: 2rem;
  }

  .author-card {
    background: white;
    padding: 2rem;
    text-align: center;
  }

  .author-card-avatar {
    width: 100px;
    height: 100px;
    border-radius: 50%;
    margin-bottom: 1rem;
  }

  .author-card h3 {
    margin: 0 0 0.5rem 0;
  }

  .author-card-role {
    color: #3b82f6;
    font-size: 0.875rem;
    margin: 0 0 1rem 0;
  }

  .author-card-bio {
    color: #6b7280;
    font-size: 0.875rem;
    line-height: 1.6;
    margin: 0 0 1.5rem 0;
  }

  .btn-follow {
    width: 100%;
    padding: 0.75rem;
    background: #3b82f6;
    color: white;
    border: none;
    cursor: pointer;
    font-weight: 600;
  }

  .related-articles h3 {
    margin: 0 0 1rem 0;
  }

  .related-article {
    display: flex;
    gap: 1rem;
    padding: 1rem;
    background: white;
    border: 1px solid #e5e7eb;
    text-decoration: none;
    color: inherit;
    margin-bottom: 1rem;
    transition: all 300ms;
  }

  .related-article:hover {
    background: #f9fafb;
  }

  .related-article img {
    width: 80px;
    height: 80px;
    object-fit: cover;
    border-radius: 0.5rem;
  }

  .related-article h4 {
    margin: 0;
    font-size: 0.875rem;
    line-height: 1.4;
  }
</style>
```

## 🎨 Personnalisation avancée

### Breakpoints personnalisés

```scss
// Redéfinir les breakpoints
:root {
  --breakpoint-mobile: 640px; // Au lieu de 768px
  --breakpoint-tablet: 1024px;
  --breakpoint-desktop: 1440px; // Au lieu de 1280px
}

// Créer des classes custom
.hide-mobile-custom {
  @media (max-width: 639px) {
    display: none !important;
  }
}
```

### Créer vos propres utilitaires

```scss
// Cacher uniquement sur tablette horizontale
.hide-tablet-landscape {
  @media (min-width: 768px) and (max-width: 1023px) and (orientation: landscape) {
    display: none !important;
  }
}

// Afficher uniquement sur petit mobile
.show-mobile-sm {
  @media (min-width: 480px) {
    display: none !important;
  }
}
```

## 🎯 Cas d'usage courants

### 1. Navigation responsive

```html
<nav>
  <div class="hide-mobile">Desktop Menu</div>
  <button class="show-mobile">☰ Mobile Menu</button>
</nav>
```

### 2. Sidebar conditionnelle

```html
<aside class="hide-mobile-tablet">Sidebar</aside>
```

### 3. Images responsive

```html
<img src="desktop.jpg" class="hide-mobile" />
<img src="mobile.jpg" class="show-mobile" />
```

### 4. Texte adaptatif

```html
<span class="show-mobile">Court</span>
<span class="hide-mobile">Titre complet et détaillé</span>
```

### 5. Boutons avec labels

```html
<button>
  <span>🛒</span>
  <span class="hide-mobile">Ajouter au panier</span>
</button>
```

## 🔧 Combinaison avec autres utilitaires

### Avec Flex Wrapper

```html
<div class="flex-wrapper hide-mobile">Desktop flex layout</div>
```

### Avec Grid Wrapper

```html
<div class="grid-wrapper hide-mobile" style="--cols: 4">
  Desktop 4 columns grid
</div>
```

### Avec Hover Effects

```html
<div class="hover-lift hide-mobile">Desktop interactive card</div>
```

## 📱 Comportement responsive

### Stratégie mobile-first

```scss
// ✅ Bon : Commencer mobile, améliorer sur desktop
.element {
  font-size: 1rem;

  @media (min-width: 768px) {
    font-size: 1.25rem;
  }
}

// ❌ Éviter : Desktop-first
.element {
  font-size: 1.25rem;

  @media (max-width: 767px) {
    font-size: 1rem;
  }
}
```

## ⚡ Performance & Bonnes pratiques

### ✅ À faire

```html
<!-- Bon : Cacher élément non-critique -->
<div class="sidebar hide-mobile">...</div>

<!-- Bon : Alternative mobile -->
<button class="show-mobile">Menu</button>

<!-- Bon : Images adaptatives -->
<picture>
  <source media="(min-width: 768px)" srcset="desktop.jpg" />
  <img src="mobile.jpg" alt="Image" />
</picture>
```

### ❌ À éviter

```html
<!-- Mauvais : Cacher du contenu important -->
<div class="hide-mobile">
  <p>Information critique pour l'utilisateur</p>
</div>

<!-- Mauvais : Dupliquer beaucoup de contenu -->
<div class="show-mobile">Long texte...</div>
<div class="hide-mobile">Long texte...</div>

<!-- Mauvais : Cacher pour l'accessibilité -->
<button class="hide-mobile" aria-label="Important">
  <!-- Utilisez sr-only à la place -->
</button>
```

### Accessibilité

```html
<!-- ✅ Bon : Garder accessible aux screen readers -->
<span class="sr-only">Description pour lecteurs d'écran</span>

<!-- ✅ Bon : Alternative visible -->
<nav aria-label="Main navigation" class="hide-mobile">...</nav>
<button aria-label="Open menu" class="show-mobile">☰</button>

<!-- ❌ Éviter : Cacher sans alternative -->
<div class="hide-mobile">Unique moyen de navigation</div>
```

## 🌐 Compatibilité navigateurs

| Navigateur | Version minimale | Support    |
| ---------- | ---------------- | ---------- |
| Chrome     | 26+              | ✅ Complet |
| Firefox    | 16+              | ✅ Complet |
| Safari     | 9+               | ✅ Complet |
| Edge       | 12+              | ✅ Complet |
| Opera      | 12.1+            | ✅ Complet |

**Note** : Les media queries sont universellement supportées.

## 🐛 Troubleshooting

### Problème : L'élément ne se cache pas

**Solution** : Vérifiez la spécificité CSS

```css
/* Si ça ne marche pas... */
.element.hide-mobile {
}

/* Ajoutez !important */
.hide-mobile {
  display: none !important;
}
```

### Problème : Contenu qui flash au chargement

**Solution** : Chargez le CSS en priorité

```html
<head>
  <link rel="stylesheet" href="responsive-visibility.css" />
  <!-- Avant les autres CSS -->
</head>
```

### Problème : Breakpoint ne correspond pas

**Solution** : Vérifiez le viewport

```html
<meta name="viewport" content="width=device-width, initial-scale=1" />
```

## 📦 Classes complètes disponibles

```scss
// Hide utilities
.hide-mobile          { /* < 768px */ }
.hide-tablet          { /* 768-1023px */ }
.hide-desktop         { /* ≥ 1024px */ }
.hide-desktop-lg      { /* ≥ 1280px */ }
.hide-mobile-tablet   { /* < 1024px */ }
.hide-tablet-desktop  { /* ≥ 768px */ }

// Show utilities
.show-mobile / .mobile-only         { /* < 768px */ }
.show-tablet / .tablet-only         { /* 768-1023px */ }
.show-desktop / .desktop-only       { /* ≥ 1024px */ }
.show-desktop-lg / .desktop-lg-only { /* ≥ 1280px */ }
.show-mobile-tablet                 { /* < 1024px */ }

// Numeric breakpoints
.hide-below-sm   { /* < 640px */ }
.hide-below-md   { /* < 768px */ }
.hide-below-lg   { /* < 1024px */ }
.hide-below-xl   { /* < 1280px */ }
.hide-above-sm   { /* ≥ 640px */ }
.hide-above-md   { /* ≥ 768px */ }
.hide-above-lg   { /* ≥ 1024px */ }
.hide-above-xl   { /* ≥ 1280px */ }

// Orientation
.hide-portrait    { /* Portrait */ }
.hide-landscape   { /* Landscape */ }
.show-portrait    { /* Portrait only */ }
.show-landscape   { /* Landscape only */ }

// Print
.hide-print       { /* Hidden in print */ }
.show-print       { /* Visible only in print */ }

// Accessibility
.sr-only          { /* Screen reader only */ }
.sr-only-mobile   { /* SR only on mobile */ }
.hide-all         { /* Hidden for everyone */ }

// Display types
.flex-mobile, .flex-tablet, .flex-desktop
.grid-mobile, .grid-tablet, .grid-desktop
.block-mobile, .block-tablet, .block-desktop

// Visibility
.invisible-mobile, .invisible-tablet, .invisible-desktop

// Opacity
.opacity-0-mobile, .opacity-0-tablet, .opacity-0-desktop
```

## 🎓 Ressources complémentaires

- [Responsive Design - MDN](https://developer.mozilla.org/fr/docs/Learn/CSS/CSS_layout/Responsive_Design)
- [Media Queries - CSS Tricks](https://css-tricks.com/a-complete-guide-to-css-media-queries/)
- [Mobile First Design](https://www.uxpin.com/studio/blog/a-hands-on-guide-to-mobile-first-design/)

## 📝 Changelog

- **v1.0** - Version initiale avec hide/show mobile/desktop
- **v1.1** - Ajout des classes tablet
- **v1.2** - Ajout des breakpoints numériques
- **v1.3** - Support orientation (portrait/landscape)
- **v1.4** - Ajout des utilitaires print
- **v1.5** - Utilitaires d'accessibilité (sr-only)
- **v1.6** - Display types responsive (flex, grid, block)

---

**Made with ❤️ for responsive perfection**
