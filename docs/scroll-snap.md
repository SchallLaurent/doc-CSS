# Scroll Snap Utility

> Comportements de défilement avec accrochage fluide pour créer des expériences de navigation modernes et intuitives

## 📋 Description

**Scroll Snap** est un utilitaire CSS qui permet de créer des comportements de défilement avec accrochage (snap) automatique. Parfait pour les carrousels, sliders, galleries, et pages fullscreen, il offre une expérience utilisateur fluide et native sans JavaScript.

### ✨ Caractéristiques principales

- 🎯 **Snap automatique** : Accrochage fluide lors du scroll
- ↔️ **Multi-directions** : Horizontal, vertical, both
- 🎨 **Alignements** : start, center, end
- 🔒 **Types** : mandatory, proximity
- 📱 **Touch-friendly** : Optimisé pour mobile
- ⚡ **Performant** : Natif CSS, pas de JS
- 🔧 **Variables CSS** : Personnalisation complète
- ♿ **Accessibilité** : Navigation clavier supportée

## 🚀 Installation

### Code SCSS

```scss
// _scroll-snap.scss

// Variables globales
:root {
  --scroll-padding: 0px;
  --scroll-snap-stop: normal;
}

// ============================================
// SCROLL SNAP CONTAINER
// ============================================

// Container horizontal (défaut)
.scroll-snap {
  scroll-snap-type: x mandatory;
  overflow-x: auto;
  overflow-y: hidden;
  display: flex;
  scroll-padding: var(--scroll-padding, 0);
  -webkit-overflow-scrolling: touch;
  scrollbar-width: none; // Firefox

  &::-webkit-scrollbar {
    display: none; // Chrome, Safari
  }
}

// Container vertical
.scroll-snap--vertical {
  scroll-snap-type: y mandatory;
  overflow-y: auto;
  overflow-x: hidden;
  flex-direction: column;
  height: 100vh;
}

// Container both (2D)
.scroll-snap--both {
  scroll-snap-type: both mandatory;
  overflow: auto;
}

// ============================================
// SNAP TYPE
// ============================================

// Mandatory (accrochage obligatoire)
.scroll-snap--mandatory {
  scroll-snap-type: x mandatory;
}

.scroll-snap--vertical.scroll-snap--mandatory {
  scroll-snap-type: y mandatory;
}

// Proximity (accrochage si proche)
.scroll-snap--proximity {
  scroll-snap-type: x proximity;
}

.scroll-snap--vertical.scroll-snap--proximity {
  scroll-snap-type: y proximity;
}

// ============================================
// SCROLL SNAP ITEMS
// ============================================

// Item de base
.scroll-snap__item {
  scroll-snap-align: start;
  scroll-snap-stop: var(--scroll-snap-stop, normal);
  flex-shrink: 0;
}

// ============================================
// ALIGNEMENTS
// ============================================

// Align start (début)
.scroll-snap__item--start {
  scroll-snap-align: start;
}

// Align center (centre)
.scroll-snap__item--center {
  scroll-snap-align: center;
}

// Align end (fin)
.scroll-snap__item--end {
  scroll-snap-align: end;
}

// ============================================
// SCROLL SNAP STOP
// ============================================

// Toujours s'arrêter sur cet item
.scroll-snap__item--always {
  scroll-snap-stop: always;
}

// Comportement normal
.scroll-snap__item--normal {
  scroll-snap-stop: normal;
}

// ============================================
// TAILLES D'ITEMS
// ============================================

// Pleine largeur/hauteur
.scroll-snap__item--full {
  width: 100%;
  min-width: 100%;
}

.scroll-snap--vertical .scroll-snap__item--full {
  height: 100vh;
  min-height: 100vh;
}

// Largeur personnalisée
.scroll-snap__item--80 {
  width: 80%;
  min-width: 80%;
}

.scroll-snap__item--90 {
  width: 90%;
  min-width: 90%;
}

// Width auto (basé sur le contenu)
.scroll-snap__item--auto {
  width: auto;
  min-width: auto;
}

// ============================================
// GAPS ET SPACING
// ============================================

.scroll-snap--gap-sm {
  gap: 0.5rem;
  scroll-padding: 0.5rem;
}

.scroll-snap--gap-md {
  gap: 1rem;
  scroll-padding: 1rem;
}

.scroll-snap--gap-lg {
  gap: 1.5rem;
  scroll-padding: 1.5rem;
}

.scroll-snap--gap-xl {
  gap: 2rem;
  scroll-padding: 2rem;
}

// ============================================
// PADDING CONTAINER
// ============================================

.scroll-snap--padding-sm {
  padding: 0.5rem;
  scroll-padding: 0.5rem;
}

.scroll-snap--padding-md {
  padding: 1rem;
  scroll-padding: 1rem;
}

.scroll-snap--padding-lg {
  padding: 1.5rem;
  scroll-padding: 1.5rem;
}

.scroll-snap--padding-xl {
  padding: 2rem;
  scroll-padding: 2rem;
}

// ============================================
// CAROUSEL (horizontal cards)
// ============================================

.scroll-snap--carousel {
  scroll-snap-type: x mandatory;
  display: flex;
  gap: 1rem;
  padding: 1rem;
  scroll-padding: 1rem;

  .scroll-snap__item {
    scroll-snap-align: center;
    flex: 0 0 auto;
    width: 300px;
  }
}

// Carousel responsive
.scroll-snap--carousel-responsive {
  .scroll-snap__item {
    width: 80vw;
    max-width: 400px;
  }

  @media (min-width: 768px) {
    .scroll-snap__item {
      width: 400px;
    }
  }
}

// ============================================
// FULLSCREEN SLIDER
// ============================================

.scroll-snap--fullscreen {
  height: 100vh;
  scroll-snap-type: y mandatory;
  overflow-y: auto;
  overflow-x: hidden;

  .scroll-snap__item {
    height: 100vh;
    scroll-snap-align: start;
  }
}

// ============================================
// GALLERY (grille)
// ============================================

.scroll-snap--gallery {
  scroll-snap-type: y proximity;
  overflow-y: auto;
  height: 100vh;
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 1rem;
  padding: 1rem;

  .scroll-snap__item {
    scroll-snap-align: start;
  }
}

// ============================================
// INDICATEURS
// ============================================

.scroll-snap__indicators {
  position: fixed;
  bottom: 2rem;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  gap: 0.5rem;
  z-index: 100;
}

.scroll-snap__indicator {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.5);
  border: 2px solid rgba(255, 255, 255, 0.8);
  cursor: pointer;
  transition: all 200ms;

  &.active {
    background: white;
    transform: scale(1.3);
  }

  &:hover {
    background: rgba(255, 255, 255, 0.8);
  }
}

// Indicateurs pour carousel horizontal
.scroll-snap__indicators--horizontal {
  bottom: 1rem;
  flex-direction: row;
}

// Indicateurs pour slider vertical
.scroll-snap__indicators--vertical {
  right: 2rem;
  left: auto;
  top: 50%;
  bottom: auto;
  transform: translateY(-50%);
  flex-direction: column;
}

// ============================================
// NAVIGATION BUTTONS
// ============================================

.scroll-snap__nav {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  z-index: 10;
}

.scroll-snap__nav--prev {
  left: 1rem;
}

.scroll-snap__nav--next {
  right: 1rem;
}

.scroll-snap__nav-btn {
  width: 48px;
  height: 48px;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.9);
  border: none;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.5rem;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  transition: all 200ms;

  &:hover {
    background: white;
    transform: scale(1.1);
  }

  &:active {
    transform: scale(0.95);
  }
}

// ============================================
// SMOOTH SCROLLING
// ============================================

.scroll-snap--smooth {
  scroll-behavior: smooth;
}

// ============================================
// PEEK (aperçu du contenu suivant)
// ============================================

.scroll-snap--peek {
  .scroll-snap__item {
    width: calc(100% - 4rem);
    margin-right: 2rem;
  }
}

// ============================================
// CENTERED ITEMS
// ============================================

.scroll-snap--centered {
  justify-content: center;

  &::before,
  &::after {
    content: "";
    width: 20%;
    flex-shrink: 0;
  }
}

// ============================================
// RESPONSIVE
// ============================================

// Désactiver snap sur mobile
@media (max-width: 767px) {
  .scroll-snap--no-mobile {
    scroll-snap-type: none;

    .scroll-snap__item {
      scroll-snap-align: none;
    }
  }
}

// Activer snap uniquement sur mobile
.scroll-snap--mobile-only {
  scroll-snap-type: none;

  @media (max-width: 767px) {
    scroll-snap-type: x mandatory;
  }
}

// ============================================
// UTILITAIRES
// ============================================

// Désactiver le scroll horizontal sur body
body.scroll-snap-active {
  overflow: hidden;
}

// Scroll padding pour header fixe
.scroll-snap--with-header {
  scroll-padding-top: 80px;
}

// Hide scrollbar mais garder fonctionnalité
.scroll-snap--hide-scrollbar {
  scrollbar-width: none;
  -ms-overflow-style: none;

  &::-webkit-scrollbar {
    display: none;
  }
}

// Show scrollbar
.scroll-snap--show-scrollbar {
  scrollbar-width: thin;
  scrollbar-color: rgba(0, 0, 0, 0.3) transparent;

  &::-webkit-scrollbar {
    width: 8px;
    height: 8px;
  }

  &::-webkit-scrollbar-track {
    background: transparent;
  }

  &::-webkit-scrollbar-thumb {
    background: rgba(0, 0, 0, 0.3);
    border-radius: 4px;

    &:hover {
      background: rgba(0, 0, 0, 0.5);
    }
  }
}
```

### Import dans votre projet

```scss
// Dans styles.scss
@import "utilities/scroll-snap";
```

## 💡 Utilisation de base

### Exemple 1 : Carousel horizontal simple

```html
<div class="scroll-snap scroll-snap--gap-md">
  <div class="scroll-snap__item">
    <img src="image1.jpg" alt="Image 1" />
  </div>
  <div class="scroll-snap__item">
    <img src="image2.jpg" alt="Image 2" />
  </div>
  <div class="scroll-snap__item">
    <img src="image3.jpg" alt="Image 3" />
  </div>
</div>

<style>
  .scroll-snap__item img {
    width: 100%;
    height: 400px;
    object-fit: cover;
    border-radius: 1rem;
  }
</style>
```

### Exemple 2 : Slider vertical fullscreen

```html
<div class="scroll-snap scroll-snap--fullscreen">
  <section class="scroll-snap__item" style="background: #667eea;">
    <h1>Section 1</h1>
  </section>
  <section class="scroll-snap__item" style="background: #764ba2;">
    <h1>Section 2</h1>
  </section>
  <section class="scroll-snap__item" style="background: #f093fb;">
    <h1>Section 3</h1>
  </section>
</div>
```

### Exemple 3 : Cards carousel

```html
<div class="scroll-snap scroll-snap--carousel">
  <div class="scroll-snap__item card card--elevated rounded-xl">
    <h3>Card 1</h3>
    <p>Content here...</p>
  </div>
  <div class="scroll-snap__item card card--elevated rounded-xl">
    <h3>Card 2</h3>
    <p>Content here...</p>
  </div>
  <div class="scroll-snap__item card card--elevated rounded-xl">
    <h3>Card 3</h3>
    <p>Content here...</p>
  </div>
</div>
```

### Exemple 4 : Items centrés

```html
<div class="scroll-snap scroll-snap--gap-lg">
  <div
    class="scroll-snap__item scroll-snap__item--center scroll-snap__item--80"
  >
    <img src="image.jpg" alt="Image" />
  </div>
</div>
```

## 📊 Paramètres

| Variable             | Type    | Défaut   | Description          |
| -------------------- | ------- | -------- | -------------------- |
| `--scroll-padding`   | length  | `0px`    | Padding du scroll    |
| `--scroll-snap-stop` | keyword | `normal` | Comportement d'arrêt |

### Types de scroll-snap-type

| Type             | Description            | Usage                       |
| ---------------- | ---------------------- | --------------------------- |
| `x mandatory`    | Horizontal obligatoire | Carousel, slider horizontal |
| `y mandatory`    | Vertical obligatoire   | Pages fullscreen            |
| `both mandatory` | 2D obligatoire         | Galerie grid                |
| `x proximity`    | Horizontal si proche   | Liste scroll libre          |
| `y proximity`    | Vertical si proche     | Feed scroll libre           |

### Alignements disponibles

| Classe                      | Alignement | Description         |
| --------------------------- | ---------- | ------------------- |
| `scroll-snap__item--start`  | start      | Début du container  |
| `scroll-snap__item--center` | center     | Centre du container |
| `scroll-snap__item--end`    | end        | Fin du container    |

## 📚 Exemples détaillés

### Exemple 1 : Image gallery carousel

```html
<div class="gallery-container">
  <div
    class="scroll-snap scroll-snap--gap-lg scroll-snap--padding-lg scroll-snap--smooth"
  >
    <div class="scroll-snap__item scroll-snap__item--center">
      <div class="gallery-item rounded-2xl shadow-wrapper shadow-wrapper--lg">
        <img src="gallery1.jpg" alt="Gallery 1" />
        <div class="gallery-overlay">
          <h3>Beautiful Sunset</h3>
          <p>Maldives, 2024</p>
        </div>
      </div>
    </div>

    <div class="scroll-snap__item scroll-snap__item--center">
      <div class="gallery-item rounded-2xl shadow-wrapper shadow-wrapper--lg">
        <img src="gallery2.jpg" alt="Gallery 2" />
        <div class="gallery-overlay">
          <h3>Mountain View</h3>
          <p>Alps, 2024</p>
        </div>
      </div>
    </div>

    <div class="scroll-snap__item scroll-snap__item--center">
      <div class="gallery-item rounded-2xl shadow-wrapper shadow-wrapper--lg">
        <img src="gallery3.jpg" alt="Gallery 3" />
        <div class="gallery-overlay">
          <h3>City Lights</h3>
          <p>Tokyo, 2024</p>
        </div>
      </div>
    </div>

    <div class="scroll-snap__item scroll-snap__item--center">
      <div class="gallery-item rounded-2xl shadow-wrapper shadow-wrapper--lg">
        <img src="gallery4.jpg" alt="Gallery 4" />
        <div class="gallery-overlay">
          <h3>Ocean Waves</h3>
          <p>Hawaii, 2024</p>
        </div>
      </div>
    </div>

    <div class="scroll-snap__item scroll-snap__item--center">
      <div class="gallery-item rounded-2xl shadow-wrapper shadow-wrapper--lg">
        <img src="gallery5.jpg" alt="Gallery 5" />
        <div class="gallery-overlay">
          <h3>Desert Dunes</h3>
          <p>Sahara, 2024</p>
        </div>
      </div>
    </div>
  </div>

  <!-- Indicators -->
  <div class="scroll-snap__indicators">
    <button class="scroll-snap__indicator active"></button>
    <button class="scroll-snap__indicator"></button>
    <button class="scroll-snap__indicator"></button>
    <button class="scroll-snap__indicator"></button>
    <button class="scroll-snap__indicator"></button>
  </div>
</div>

<style>
  .gallery-container {
    position: relative;
    padding: 3rem 0;
  }

  .gallery-item {
    position: relative;
    width: 600px;
    height: 400px;
    overflow: hidden;
  }

  @media (max-width: 767px) {
    .gallery-item {
      width: 85vw;
      height: 300px;
    }
  }

  .gallery-item img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    display: block;
  }

  .gallery-overlay {
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
    padding: 2rem;
    background: linear-gradient(to top, rgba(0, 0, 0, 0.8), transparent);
    color: white;
  }

  .gallery-overlay h3 {
    margin: 0 0 0.5rem 0;
    font-size: 1.5rem;
  }

  .gallery-overlay p {
    margin: 0;
    opacity: 0.9;
  }
</style>
```

### Exemple 2 : Fullscreen vertical slider

```html
<div class="scroll-snap scroll-snap--fullscreen scroll-snap--smooth">
  <!-- Slide 1 -->
  <section
    class="scroll-snap__item hero-slide"
    style="background-image: url('hero1.jpg');"
  >
    <div class="hero-content">
      <h1 class="hero-title">Welcome to Our Platform</h1>
      <p class="hero-description">
        Discover amazing features that will transform your workflow
      </p>
      <div class="stack stack--horizontal stack--sm">
        <button class="btn-primary rounded-lg">Get Started</button>
        <button class="btn-secondary rounded-lg">Learn More</button>
      </div>
    </div>
    <div class="scroll-hint">
      <span>Scroll Down</span>
      <span class="scroll-arrow">↓</span>
    </div>
  </section>

  <!-- Slide 2 -->
  <section
    class="scroll-snap__item hero-slide"
    style="background-image: url('hero2.jpg');"
  >
    <div class="hero-content">
      <h1 class="hero-title">Powerful Features</h1>
      <p class="hero-description">
        Everything you need to succeed in one place
      </p>
      <div class="features-grid">
        <div class="feature-badge">⚡ Fast</div>
        <div class="feature-badge">🔒 Secure</div>
        <div class="feature-badge">🎨 Beautiful</div>
        <div class="feature-badge">📱 Responsive</div>
      </div>
    </div>
  </section>

  <!-- Slide 3 -->
  <section
    class="scroll-snap__item hero-slide"
    style="background-image: url('hero3.jpg');"
  >
    <div class="hero-content">
      <h1 class="hero-title">Trusted by Thousands</h1>
      <p class="hero-description">
        Join 10,000+ users who already love our platform
      </p>
      <div class="stats-grid">
        <div class="stat-item">
          <div class="stat-value">10K+</div>
          <div class="stat-label">Users</div>
        </div>
        <div class="stat-item">
          <div class="stat-value">500K+</div>
          <div class="stat-label">Projects</div>
        </div>
        <div class="stat-item">
          <div class="stat-value">4.9/5</div>
          <div class="stat-label">Rating</div>
        </div>
      </div>
    </div>
  </section>

  <!-- Slide 4 -->
  <section
    class="scroll-snap__item hero-slide"
    style="background-image: url('hero4.jpg');"
  >
    <div class="hero-content">
      <h1 class="hero-title">Ready to Start?</h1>
      <p class="hero-description">Create your free account today</p>
      <form class="signup-form">
        <input
          type="email"
          placeholder="Enter your email"
          class="input rounded-lg"
        />
        <button type="submit" class="btn-primary rounded-lg">
          Sign Up Free
        </button>
      </form>
      <p class="hero-note">No credit card required • Cancel anytime</p>
    </div>
  </section>
</div>

<!-- Vertical indicators -->
<div class="scroll-snap__indicators scroll-snap__indicators--vertical">
  <button class="scroll-snap__indicator active"></button>
  <button class="scroll-snap__indicator"></button>
  <button class="scroll-snap__indicator"></button>
  <button class="scroll-snap__indicator"></button>
</div>

<style>
  .hero-slide {
    display: flex;
    align-items: center;
    justify-content: center;
    background-size: cover;
    background-position: center;
    position: relative;
    color: white;
    text-align: center;
  }

  .hero-slide::before {
    content: "";
    position: absolute;
    inset: 0;
    background: rgba(0, 0, 0, 0.5);
  }

  .hero-content {
    position: relative;
    z-index: 1;
    max-width: 800px;
    padding: 2rem;
  }

  .hero-title {
    font-size: 4rem;
    margin: 0 0 1.5rem 0;
    font-weight: 800;
    line-height: 1.1;
  }

  @media (max-width: 767px) {
    .hero-title {
      font-size: 2.5rem;
    }
  }

  .hero-description {
    font-size: 1.5rem;
    margin: 0 0 2rem 0;
    opacity: 0.95;
  }

  .scroll-hint {
    position: absolute;
    bottom: 2rem;
    left: 50%;
    transform: translateX(-50%);
    text-align: center;
    animation: bounce 2s infinite;
  }

  .scroll-arrow {
    display: block;
    font-size: 2rem;
    margin-top: 0.5rem;
  }

  @keyframes bounce {
    0%,
    100% {
      transform: translateX(-50%) translateY(0);
    }
    50% {
      transform: translateX(-50%) translateY(-10px);
    }
  }

  .features-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
    gap: 1rem;
    max-width: 600px;
    margin: 0 auto;
  }

  .feature-badge {
    padding: 1rem;
    background: rgba(255, 255, 255, 0.2);
    backdrop-filter: blur(10px);
    border-radius: 1rem;
    border: 1px solid rgba(255, 255, 255, 0.3);
    font-weight: 600;
  }

  .stats-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 3rem;
    max-width: 600px;
    margin: 0 auto;
  }

  @media (max-width: 767px) {
    .stats-grid {
      grid-template-columns: 1fr;
      gap: 2rem;
    }
  }

  .stat-value {
    font-size: 3rem;
    font-weight: 800;
    margin-bottom: 0.5rem;
  }

  .stat-label {
    font-size: 1.125rem;
    opacity: 0.9;
  }

  .signup-form {
    display: flex;
    gap: 1rem;
    max-width: 500px;
    margin: 0 auto 1rem;
  }

  @media (max-width: 767px) {
    .signup-form {
      flex-direction: column;
    }
  }

  .signup-form .input {
    flex: 1;
    padding: 1rem 1.5rem;
    background: rgba(255, 255, 255, 0.9);
    border: none;
    font-size: 1rem;
  }

  .signup-form button {
    padding: 1rem 2rem;
    white-space: nowrap;
  }

  .hero-note {
    font-size: 0.875rem;
    opacity: 0.8;
  }

  .btn-primary {
    padding: 1rem 2rem;
    background: #3b82f6;
    color: white;
    border: none;
    cursor: pointer;
    font-weight: 600;
    font-size: 1.125rem;
  }

  .btn-secondary {
    padding: 1rem 2rem;
    background: rgba(255, 255, 255, 0.2);
    backdrop-filter: blur(10px);
    color: white;
    border: 1px solid rgba(255, 255, 255, 0.3);
    cursor: pointer;
    font-weight: 600;
    font-size: 1.125rem;
  }
</style>
```

### Exemple 3 : Product cards carousel avec navigation

```html
<div class="products-carousel-container">
  <h2 class="section-title">Featured Products</h2>

  <div class="carousel-wrapper">
    <!-- Navigation Previous -->
    <button class="scroll-snap__nav scroll-snap__nav--prev">
      <span class="scroll-snap__nav-btn">‹</span>
    </button>

    <!-- Carousel -->
    <div class="scroll-snap scroll-snap--carousel scroll-snap--smooth">
      <!-- Product 1 -->
      <div class="scroll-snap__item">
        <div class="product-card card card--elevated rounded-xl">
          <div class="product-image">
            <img src="product1.jpg" alt="Product 1" />
            <span class="product-badge rounded-full">NEW</span>
          </div>
          <div class="product-info">
            <h3 class="product-title">Premium Headphones</h3>
            <p class="product-description">
              Wireless noise-cancelling headphones with 30h battery
            </p>
            <div class="product-footer">
              <span class="product-price">$299</span>
              <button class="btn-add rounded-lg">Add to Cart</button>
            </div>
          </div>
        </div>
      </div>

      <!-- Product 2 -->
      <div class="scroll-snap__item">
        <div class="product-card card card--elevated rounded-xl">
          <div class="product-image">
            <img src="product2.jpg" alt="Product 2" />
            <span class="product-badge product-badge--sale rounded-full"
              >-20%</span
            >
          </div>
          <div class="product-info">
            <h3 class="product-title">Smart Watch Pro</h3>
            <p class="product-description">
              Advanced fitness tracking with heart rate monitor
            </p>
            <div class="product-footer">
              <span class="product-price">$399</span>
              <button class="btn-add rounded-lg">Add to Cart</button>
            </div>
          </div>
        </div>
      </div>

      <!-- Product 3 -->
      <div class="scroll-snap__item">
        <div class="product-card card card--elevated rounded-xl">
          <div class="product-image">
            <img src="product3.jpg" alt="Product 3" />
          </div>
          <div class="product-info">
            <h3 class="product-title">Wireless Keyboard</h3>
            <p class="product-description">
              Mechanical keyboard with RGB backlighting
            </p>
            <div class="product-footer">
              <span class="product-price">$159</span>
              <button class="btn-add rounded-lg">Add to Cart</button>
            </div>
          </div>
        </div>
      </div>

      <!-- Product 4 -->
      <div class="scroll-snap__item">
        <div class="product-card card card--elevated rounded-xl">
          <div class="product-image">
            <img src="product4.jpg" alt="Product 4" />
            <span class="product-badge rounded-full">BEST SELLER</span>
          </div>
          <div class="product-info">
            <h3 class="product-title">4K Webcam</h3>
            <p class="product-description">
              Professional streaming camera with autofocus
            </p>
            <div class="product-footer">
              <span class="product-price">$199</span>
              <button class="btn-add rounded-lg">Add to Cart</button>
            </div>
          </div>
        </div>
      </div>

      <!-- Product 5 -->
      <div class="scroll-snap__item">
        <div class="product-card card card--elevated rounded-xl">
          <div class="product-image">
            <img src="product5.jpg" alt="Product 5" />
          </div>
          <div class="product-info">
            <h3 class="product-title">USB-C Hub</h3>
            <p class="product-description">
              7-in-1 adapter with HDMI, USB 3.0, SD card
            </p>
            <div class="product-footer">
              <span class="product-price">$79</span>
              <button class="btn-add rounded-lg">Add to Cart</button>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Navigation Next -->
    <button class="scroll-snap__nav scroll-snap__nav--next">
      <span class="scroll-snap__nav-btn">›</span>
    </button>
  </div>
</div>

<style>
  .products-carousel-container {
    padding: 4rem 2rem;
    max-width: 1400px;
    margin: 0 auto;
  }

  .section-title {
    font-size: 2.5rem;
    text-align: center;
    margin: 0 0 3rem 0;
  }

  .carousel-wrapper {
    position: relative;
  }

  .product-card {
    height: 100%;
    display: flex;
    flex-direction: column;
  }

  .product-image {
    position: relative;
    width: 100%;
    height: 250px;
    overflow: hidden;
    border-radius: 0.75rem 0.75rem 0 0;
  }

  .product-image img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }

  .product-badge {
    position: absolute;
    top: 1rem;
    right: 1rem;
    padding: 0.5rem 1rem;
    background: #3b82f6;
    color: white;
    font-size: 0.75rem;
    font-weight: 600;
  }

  .product-badge--sale {
    background: #ef4444;
  }

  .product-info {
    padding: 1.5rem;
    flex: 1;
    display: flex;
    flex-direction: column;
  }

  .product-title {
    margin: 0 0 0.5rem 0;
    font-size: 1.25rem;
  }

  .product-description {
    margin: 0 0 1.5rem 0;
    color: #6b7280;
    font-size: 0.875rem;
    flex: 1;
  }

  .product-footer {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .product-price {
    font-size: 1.75rem;
    font-weight: 700;
    color: #059669;
  }

  .btn-add {
    padding: 0.75rem 1.25rem;
    background: #3b82f6;
    color: white;
    border: none;
    cursor: pointer;
    font-weight: 600;
    font-size: 0.875rem;
  }
</style>

<script>
  // Navigation buttons functionality
  const carousel = document.querySelector(".scroll-snap--carousel");
  const prevBtn = document.querySelector(".scroll-snap__nav--prev");
  const nextBtn = document.querySelector(".scroll-snap__nav--next");

  prevBtn.addEventListener("click", () => {
    carousel.scrollBy({ left: -320, behavior: "smooth" });
  });

  nextBtn.addEventListener("click", () => {
    carousel.scrollBy({ left: 320, behavior: "smooth" });
  });
</script>
```

### Exemple 4 : Testimonials horizontal slider

```html
<div class="testimonials-slider">
  <h2 class="section-title">What Our Clients Say</h2>

  <div
    class="scroll-snap scroll-snap--gap-xl scroll-snap--padding-xl scroll-snap--smooth scroll-snap--centered"
  >
    <!-- Testimonial 1 -->
    <div
      class="scroll-snap__item scroll-snap__item--center scroll-snap__item--80"
    >
      <div class="testimonial-card card card--elevated rounded-2xl">
        <div class="testimonial-quote">"</div>
        <p class="testimonial-text">
          This product has completely transformed how we work. The team is more
          productive and our clients are happier than ever before. Highly
          recommended for any growing business!
        </p>
        <div class="testimonial-author">
          <img src="client1.jpg" alt="Client 1" class="author-avatar" />
          <div class="author-info">
            <div class="author-name">Sarah Johnson</div>
            <div class="author-role">CEO, TechCorp</div>
            <div class="author-rating">★★★★★</div>
          </div>
        </div>
      </div>
    </div>

    <!-- Testimonial 2 -->
    <div
      class="scroll-snap__item scroll-snap__item--center scroll-snap__item--80"
    >
      <div class="testimonial-card card card--elevated rounded-2xl">
        <div class="testimonial-quote">"</div>
        <p class="testimonial-text">
          Outstanding service and support. The implementation was smooth and the
          results exceeded our expectations. The ROI was visible within the
          first month.
        </p>
        <div class="testimonial-author">
          <img src="client2.jpg" alt="Client 2" class="author-avatar" />
          <div class="author-info">
            <div class="author-name">Michael Chen</div>
            <div class="author-role">CTO, StartupXYZ</div>
            <div class="author-rating">★★★★★</div>
          </div>
        </div>
      </div>
    </div>

    <!-- Testimonial 3 -->
    <div
      class="scroll-snap__item scroll-snap__item--center scroll-snap__item--80"
    >
      <div class="testimonial-card card card--elevated rounded-2xl">
        <div class="testimonial-quote">"</div>
        <p class="testimonial-text">
          The best investment we've made this year. Can't imagine working
          without it now. The features are exactly what we needed and the
          support team is incredibly responsive.
        </p>
        <div class="testimonial-author">
          <img src="client3.jpg" alt="Client 3" class="author-avatar" />
          <div class="author-info">
            <div class="author-name">Emma Wilson</div>
            <div class="author-role">Director, Agency Inc</div>
            <div class="author-rating">★★★★★</div>
          </div>
        </div>
      </div>
    </div>
  </div>

  <!-- Indicators -->
  <div class="scroll-snap__indicators">
    <button class="scroll-snap__indicator active"></button>
    <button class="scroll-snap__indicator"></button>
    <button class="scroll-snap__indicator"></button>
  </div>
</div>

<style>
  .testimonials-slider {
    padding: 5rem 0;
    background: linear-gradient(to bottom, #f9fafb, white);
  }

  .testimonial-card {
    padding: 3rem 2.5rem;
    min-height: 350px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
  }

  .testimonial-quote {
    font-size: 6rem;
    color: #e5e7eb;
    line-height: 1;
    margin-bottom: 1rem;
  }

  .testimonial-text {
    font-size: 1.25rem;
    line-height: 1.8;
    color: #374151;
    font-style: italic;
    margin: 0 0 2rem 0;
  }

  .testimonial-author {
    display: flex;
    gap: 1.5rem;
    align-items: center;
  }

  .author-avatar {
    width: 64px;
    height: 64px;
    border-radius: 50%;
    object-fit: cover;
  }

  .author-name {
    font-weight: 700;
    font-size: 1.125rem;
    color: #111827;
  }

  .author-role {
    color: #6b7280;
    margin-top: 0.25rem;
  }

  .author-rating {
    color: #fbbf24;
    margin-top: 0.5rem;
  }
</style>
```

### Exemple 5 : Mobile app screenshots showcase

```html
<div class="screenshots-showcase">
  <div class="container">
    <div class="stack stack--center stack--xl">
      <div class="section-header stack stack--center stack--sm">
        <h2>Beautiful on Every Device</h2>
        <p class="text-muted">Experience the app in action</p>
      </div>

      <div
        class="scroll-snap scroll-snap--gap-lg scroll-snap--smooth scroll-snap--peek"
      >
        <!-- Screenshot 1 -->
        <div class="scroll-snap__item scroll-snap__item--center">
          <div class="screenshot-frame">
            <div class="phone-mockup">
              <div class="phone-notch"></div>
              <img src="screenshot1.jpg" alt="Screenshot 1" />
            </div>
            <div class="screenshot-caption">
              <h4>Dashboard</h4>
              <p>Track your progress at a glance</p>
            </div>
          </div>
        </div>

        <!-- Screenshot 2 -->
        <div class="scroll-snap__item scroll-snap__item--center">
          <div class="screenshot-frame">
            <div class="phone-mockup">
              <div class="phone-notch"></div>
              <img src="screenshot2.jpg" alt="Screenshot 2" />
            </div>
            <div class="screenshot-caption">
              <h4>Analytics</h4>
              <p>Detailed insights and reports</p>
            </div>
          </div>
        </div>

        <!-- Screenshot 3 -->
        <div class="scroll-snap__item scroll-snap__item--center">
          <div class="screenshot-frame">
            <div class="phone-mockup">
              <div class="phone-notch"></div>
              <img src="screenshot3.jpg" alt="Screenshot 3" />
            </div>
            <div class="screenshot-caption">
              <h4>Notifications</h4>
              <p>Stay updated in real-time</p>
            </div>
          </div>
        </div>

        <!-- Screenshot 4 -->
        <div class="scroll-snap__item scroll-snap__item--center">
          <div class="screenshot-frame">
            <div class="phone-mockup">
              <div class="phone-notch"></div>
              <img src="screenshot4.jpg" alt="Screenshot 4" />
            </div>
            <div class="screenshot-caption">
              <h4>Settings</h4>
              <p>Customize your experience</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>

<style>
  .screenshots-showcase {
    padding: 5rem 2rem;
    overflow: hidden;
  }

  .section-header {
    text-align: center;
    margin-bottom: 3rem;
  }

  .section-header h2 {
    font-size: 3rem;
    margin: 0;
  }

  .screenshot-frame {
    text-align: center;
  }

  .phone-mockup {
    width: 300px;
    height: 600px;
    background: #1f2937;
    border-radius: 3rem;
    padding: 1rem;
    box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
    position: relative;
    margin: 0 auto 2rem;
  }

  .phone-notch {
    position: absolute;
    top: 0;
    left: 50%;
    transform: translateX(-50%);
    width: 120px;
    height: 30px;
    background: #1f2937;
    border-radius: 0 0 1rem 1rem;
    z-index: 10;
  }

  .phone-mockup img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    border-radius: 2rem;
  }

  .screenshot-caption h4 {
    margin: 0 0 0.5rem 0;
    font-size: 1.25rem;
  }

  .screenshot-caption p {
    margin: 0;
    color: #6b7280;
  }
</style>
```

## 🎨 Personnalisation avancée

### Scroll padding personnalisé

```html
<div class="scroll-snap" style="--scroll-padding: 2rem">Padding de 2rem</div>
```

### Désactiver snap sur certains items

```html
<div class="scroll-snap__item" style="scroll-snap-align: none">
  Pas de snap sur cet item
</div>
```

### Forcer arrêt sur item

```html
<div class="scroll-snap__item scroll-snap__item--always">
  Toujours s'arrêter ici
</div>
```

## 🎯 Cas d'usage courants

### 1. Image carousel

```html
<div class="scroll-snap scroll-snap--gap-md">
  <div class="scroll-snap__item">...</div>
</div>
```

### 2. Fullscreen slides

```html
<div class="scroll-snap scroll-snap--fullscreen">
  <section class="scroll-snap__item">...</section>
</div>
```

### 3. Product showcase

```html
<div class="scroll-snap scroll-snap--carousel">
  <div class="scroll-snap__item">...</div>
</div>
```

### 4. Testimonials

```html
<div class="scroll-snap scroll-snap--centered">
  <div class="scroll-snap__item scroll-snap__item--center">...</div>
</div>
```

### 5. Mobile screenshots

```html
<div class="scroll-snap scroll-snap--peek">
  <div class="scroll-snap__item">...</div>
</div>
```

## 🔧 Combinaison avec autres utilitaires

### Avec Card

```html
<div class="scroll-snap scroll-snap--carousel">
  <div class="scroll-snap__item">
    <div class="card card--elevated rounded-xl">...</div>
  </div>
</div>
```

### Avec Shadow Wrapper

```html
<div class="scroll-snap__item">
  <div class="shadow-wrapper shadow-wrapper--xl">...</div>
</div>
```

### Avec Rounded

```html
<div class="scroll-snap__item rounded-2xl">Content</div>
```

## 📱 Comportement responsive

### Désactiver sur mobile

```html
<div class="scroll-snap scroll-snap--no-mobile">
  <!-- Pas de snap sur mobile -->
</div>
```

### Activer uniquement sur mobile

```html
<div class="scroll-snap scroll-snap--mobile-only">
  <!-- Snap uniquement sur mobile -->
</div>
```

## ⚡ Performance & Bonnes pratiques

### ✅ À faire

```html
<!-- Bon : Images optimisées -->
<img src="image-optimized.jpg" loading="lazy" />

<!-- Bon : Smooth scrolling -->
<div class="scroll-snap scroll-snap--smooth">
  <!-- Bon : Hide scrollbar -->
  <div class="scroll-snap scroll-snap--hide-scrollbar">
    <!-- Bon : Nombre raisonnable d'items -->
    <div class="scroll-snap">
      <!-- 5-20 items max -->
    </div>
  </div>
</div>
```

### ❌ À éviter

```html
<!-- Mauvais : Trop d'items -->
<div class="scroll-snap">
  <!-- 100+ items (utiliser pagination) -->
</div>

<!-- Mauvais : Images non optimisées -->
<img src="huge-image.jpg" />

<!-- Mauvais : Contenu trop lourd -->
<div class="scroll-snap__item">
  <!-- Trop de contenu complexe -->
</div>
```

### JavaScript pour indicateurs

```javascript
const container = document.querySelector(".scroll-snap");
const indicators = document.querySelectorAll(".scroll-snap__indicator");

container.addEventListener("scroll", () => {
  const scrollLeft = container.scrollLeft;
  const itemWidth = container.querySelector(".scroll-snap__item").offsetWidth;
  const currentIndex = Math.round(scrollLeft / itemWidth);

  indicators.forEach((indicator, index) => {
    indicator.classList.toggle("active", index === currentIndex);
  });
});

// Click sur indicateur
indicators.forEach((indicator, index) => {
  indicator.addEventListener("click", () => {
    const itemWidth = container.querySelector(".scroll-snap__item").offsetWidth;
    container.scrollTo({
      left: itemWidth * index,
      behavior: "smooth",
    });
  });
});
```

## 🌐 Compatibilité navigateurs

| Navigateur | Version minimale | Support    |
| ---------- | ---------------- | ---------- |
| Chrome     | 69+              | ✅ Complet |
| Firefox    | 68+              | ✅ Complet |
| Safari     | 11+              | ✅ Complet |
| Edge       | 79+              | ✅ Complet |

**Note** : Scroll Snap est bien supporté sur les navigateurs modernes.

## 🐛 Troubleshooting

### Problème : Le snap ne fonctionne pas

**Solution** : Vérifiez overflow et display

```css
.scroll-snap {
  overflow-x: auto; /* Nécessaire */
  display: flex; /* Nécessaire */
}
```

### Problème : Items trop petits

**Solution** : Définissez width/min-width

```css
.scroll-snap__item {
  min-width: 300px;
  flex-shrink: 0;
}
```

### Problème : Snap trop agressif

**Solution** : Utilisez proximity

```css
.scroll-snap {
  scroll-snap-type: x proximity;
}
```

### Problème : Scrollbar visible

**Solution** : Cachez la scrollbar

```css
.scroll-snap {
  scrollbar-width: none;
  &::-webkit-scrollbar {
    display: none;
  }
}
```

## 📦 Classes complètes disponibles

```scss
// Container
.scroll-snap {
  /* Horizontal mandatory */
}
.scroll-snap--vertical {
  /* Vertical mandatory */
}
.scroll-snap--both {
  /* 2D mandatory */
}

// Type
.scroll-snap--mandatory {
  /* Obligatoire */
}
.scroll-snap--proximity {
  /* Si proche */
}

// Items
.scroll-snap__item {
  /* Item de base */
}
.scroll-snap__item--start {
  /* Align start */
}
.scroll-snap__item--center {
  /* Align center */
}
.scroll-snap__item--end {
  /* Align end */
}

// Tailles
.scroll-snap__item--full {
  /* 100% */
}
.scroll-snap__item--80 {
  /* 80% */
}
.scroll-snap__item--90 {
  /* 90% */
}

// Gap
.scroll-snap--gap-sm {
  /* 0.5rem */
}
.scroll-snap--gap-md {
  /* 1rem */
}
.scroll-snap--gap-lg {
  /* 1.5rem */
}

// Presets
.scroll-snap--carousel {
  /* Cards carousel */
}
.scroll-snap--fullscreen {
  /* Fullscreen slides */
}
.scroll-snap--gallery {
  /* Grid gallery */
}

// Utilitaires
.scroll-snap--smooth {
  /* Smooth scroll */
}
.scroll-snap--peek {
  /* Aperçu suivant */
}
.scroll-snap--centered {
  /* Items centrés */
}
.scroll-snap--hide-scrollbar {
  /* Cache scrollbar */
}

// Responsive
.scroll-snap--no-mobile {
  /* Pas de snap mobile */
}
.scroll-snap--mobile-only {
  /* Snap mobile uniquement */
}
```

## 🎓 Ressources complémentaires

- [CSS Scroll Snap - MDN](https://developer.mozilla.org/fr/docs/Web/CSS/CSS_Scroll_Snap)
- [Scroll Snap Guide - CSS Tricks](https://css-tricks.com/practical-css-scroll-snapping/)
- [Scroll Snap Examples](https://codepen.io/collection/KpMqQo)

## 📝 Changelog

- **v1.0** - Version initiale avec scroll snap horizontal
- **v1.1** - Ajout du scroll snap vertical
- **v1.2** - Presets (carousel, fullscreen, gallery)
- **v1.3** - Indicateurs et navigation
- **v1.4** - Support responsive
- **v1.5** - Optimisations performance

---

**Made with ❤️ for smooth scrolling experiences**
