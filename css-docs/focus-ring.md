# Focus Ring Utility

> Anneaux de focus accessibles et élégants pour une navigation au clavier optimale et une meilleure expérience utilisateur

## 📋 Description

**Focus Ring** est un utilitaire CSS qui fournit des styles de focus (outline/ring) modernes et accessibles pour tous les éléments interactifs. Essentiel pour l'accessibilité, il remplace les outlines natifs du navigateur par des anneaux personnalisés qui respectent les standards WCAG.

### ✨ Caractéristiques principales

- 🎯 **Focus visible** : Outline uniquement au clavier (pas au clic)
- 🎨 **Variantes** : Multiple couleurs et styles
- 📏 **Tailles** : sm, md, lg, xl
- 🔲 **Offset** : Contrôle de la distance
- 💫 **Animations** : Transitions fluides
- 🎭 **Focus within** : Pour containers parents
- 🔧 **Variables CSS** : Personnalisation complète
- ♿ **WCAG compliant** : Conforme aux standards d'accessibilité

## 🚀 Installation

### Code SCSS

```scss
// _focus-ring.scss

// Variables globales
:root {
  --focus-ring-color: #3b82f6;
  --focus-ring-width: 2px;
  --focus-ring-offset: 2px;
  --focus-ring-opacity: 0.5;
}

// ============================================
// BASE FOCUS RING
// ============================================

.focus-ring {
  outline: none;
  transition: box-shadow 200ms ease-in-out;

  &:focus {
    outline: none;
    box-shadow: 0 0 0 var(--focus-ring-offset, 2px) #fff, 0 0 0 calc(
          var(--focus-ring-offset, 2px) + var(--focus-ring-width, 2px)
        ) var(--focus-ring-color, #3b82f6);
  }
}

// ============================================
// FOCUS VISIBLE (uniquement clavier)
// ============================================

.focus-ring-visible {
  outline: none;
  transition: box-shadow 200ms ease-in-out;

  &:focus-visible {
    outline: none;
    box-shadow: 0 0 0 var(--focus-ring-offset, 2px) #fff, 0 0 0 calc(
          var(--focus-ring-offset, 2px) + var(--focus-ring-width, 2px)
        ) var(--focus-ring-color, #3b82f6);
  }
}

// ============================================
// TAILLES
// ============================================

// Small
.focus-ring--sm {
  --focus-ring-width: 1px;
  --focus-ring-offset: 1px;
}

// Medium (défaut)
.focus-ring--md {
  --focus-ring-width: 2px;
  --focus-ring-offset: 2px;
}

// Large
.focus-ring--lg {
  --focus-ring-width: 3px;
  --focus-ring-offset: 2px;
}

// Extra Large
.focus-ring--xl {
  --focus-ring-width: 4px;
  --focus-ring-offset: 3px;
}

// ============================================
// COULEURS
// ============================================

// Blue (défaut)
.focus-ring--blue {
  --focus-ring-color: #3b82f6;
}

// Purple
.focus-ring--purple {
  --focus-ring-color: #8b5cf6;
}

// Green
.focus-ring--green {
  --focus-ring-color: #10b981;
}

// Red
.focus-ring--red {
  --focus-ring-color: #ef4444;
}

// Orange
.focus-ring--orange {
  --focus-ring-color: #f59e0b;
}

// Pink
.focus-ring--pink {
  --focus-ring-color: #ec4899;
}

// Gray
.focus-ring--gray {
  --focus-ring-color: #6b7280;
}

// Black
.focus-ring--black {
  --focus-ring-color: #000000;
}

// White (pour fonds sombres)
.focus-ring--white {
  --focus-ring-color: #ffffff;
}

// ============================================
// OFFSET CUSTOM
// ============================================

.focus-ring--offset-0 {
  --focus-ring-offset: 0px;
}

.focus-ring--offset-1 {
  --focus-ring-offset: 1px;
}

.focus-ring--offset-2 {
  --focus-ring-offset: 2px;
}

.focus-ring--offset-4 {
  --focus-ring-offset: 4px;
}

.focus-ring--offset-8 {
  --focus-ring-offset: 8px;
}

// ============================================
// STYLES SPÉCIAUX
// ============================================

// Focus ring avec glow
.focus-ring--glow {
  &:focus,
  &:focus-visible {
    box-shadow: 0 0 0 var(--focus-ring-offset, 2px) #fff, 0 0 0 calc(
          var(--focus-ring-offset, 2px) + var(--focus-ring-width, 2px)
        ) var(--focus-ring-color, #3b82f6),
      0 0 20px var(--focus-ring-color, #3b82f6);
  }
}

// Focus ring inset
.focus-ring--inset {
  &:focus,
  &:focus-visible {
    box-shadow: inset 0 0 0 var(--focus-ring-width, 2px) var(
        --focus-ring-color,
        #3b82f6
      );
  }
}

// Focus ring avec dashed outline
.focus-ring--dashed {
  &:focus,
  &:focus-visible {
    outline: var(--focus-ring-width, 2px) dashed var(
        --focus-ring-color,
        #3b82f6
      );
    outline-offset: var(--focus-ring-offset, 2px);
    box-shadow: none;
  }
}

// Focus ring avec dotted outline
.focus-ring--dotted {
  &:focus,
  &:focus-visible {
    outline: var(--focus-ring-width, 2px) dotted var(
        --focus-ring-color,
        #3b82f6
      );
    outline-offset: var(--focus-ring-offset, 2px);
    box-shadow: none;
  }
}

// Focus ring avec double
.focus-ring--double {
  &:focus,
  &:focus-visible {
    box-shadow: 0 0 0 2px #fff, 0 0 0 4px var(--focus-ring-color, #3b82f6),
      0 0 0 6px #fff, 0 0 0 8px rgba(59, 130, 246, 0.3);
  }
}

// ============================================
// FOCUS WITHIN (pour containers)
// ============================================

.focus-within-ring {
  transition: box-shadow 200ms ease-in-out;

  &:focus-within {
    box-shadow: 0 0 0 var(--focus-ring-offset, 2px) #fff, 0 0 0 calc(
          var(--focus-ring-offset, 2px) + var(--focus-ring-width, 2px)
        ) var(--focus-ring-color, #3b82f6);
  }
}

// ============================================
// ANIMATIONS
// ============================================

// Focus ring avec scale animation
.focus-ring--scale {
  &:focus,
  &:focus-visible {
    animation: focus-ring-scale 200ms ease-out;
  }
}

@keyframes focus-ring-scale {
  0% {
    box-shadow: 0 0 0 0 #fff, 0 0 0 0 var(--focus-ring-color, #3b82f6);
  }
  100% {
    box-shadow: 0 0 0 var(--focus-ring-offset, 2px) #fff, 0 0 0 calc(
          var(--focus-ring-offset, 2px) + var(--focus-ring-width, 2px)
        ) var(--focus-ring-color, #3b82f6);
  }
}

// Focus ring avec pulse
.focus-ring--pulse {
  &:focus,
  &:focus-visible {
    animation: focus-ring-pulse 2s ease-in-out infinite;
  }
}

@keyframes focus-ring-pulse {
  0%,
  100% {
    box-shadow: 0 0 0 var(--focus-ring-offset, 2px) #fff, 0 0 0 calc(
          var(--focus-ring-offset, 2px) + var(--focus-ring-width, 2px)
        ) var(--focus-ring-color, #3b82f6);
  }
  50% {
    box-shadow: 0 0 0 var(--focus-ring-offset, 2px) #fff, 0 0 0 calc(
          var(--focus-ring-offset, 2px) + var(--focus-ring-width, 2px) + 2px
        ) var(--focus-ring-color, #3b82f6);
  }
}

// ============================================
// RESET FOCUS (pour enlever le focus)
// ============================================

.focus-ring--none {
  &:focus,
  &:focus-visible {
    outline: none;
    box-shadow: none;
  }
}

// ============================================
// PRESETS PAR TYPE D'ÉLÉMENT
// ============================================

// Input fields
.focus-ring--input {
  outline: none;
  transition: border-color 200ms, box-shadow 200ms;

  &:focus,
  &:focus-visible {
    border-color: var(--focus-ring-color, #3b82f6);
    box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.1);
  }
}

// Buttons
.focus-ring--button {
  outline: none;
  transition: box-shadow 200ms;

  &:focus-visible {
    box-shadow: 0 0 0 2px #fff, 0 0 0 4px var(--focus-ring-color, #3b82f6);
  }
}

// Cards (clickable)
.focus-ring--card {
  outline: none;
  transition: box-shadow 200ms, transform 200ms;

  &:focus-visible {
    box-shadow: 0 0 0 2px var(--focus-ring-color, #3b82f6), 0 8px 16px rgba(0, 0, 0, 0.1);
    transform: translateY(-2px);
  }
}

// Links
.focus-ring--link {
  outline: none;
  border-radius: 2px;
  transition: background-color 200ms;

  &:focus-visible {
    background-color: rgba(59, 130, 246, 0.1);
    outline: 2px solid var(--focus-ring-color, #3b82f6);
    outline-offset: 2px;
  }
}

// ============================================
// UTILITIES
// ============================================

// Désactiver focus ring sur dark mode
@media (prefers-color-scheme: dark) {
  .focus-ring--auto-dark {
    --focus-ring-color: #60a5fa;
  }
}

// Skip link (pour accessibilité)
.skip-link {
  position: absolute;
  top: -100px;
  left: 0;
  background: var(--focus-ring-color, #3b82f6);
  color: white;
  padding: 1rem 2rem;
  text-decoration: none;
  border-radius: 0 0 0.5rem 0;
  font-weight: 600;
  z-index: 9999;
  transition: top 200ms;

  &:focus {
    top: 0;
    outline: 2px solid white;
    outline-offset: -4px;
  }
}

// ============================================
// GLOBAL DEFAULTS (optionnel)
// ============================================

// Appliquer focus-visible par défaut à tous les éléments interactifs
.focus-defaults {
  button,
  a,
  input,
  textarea,
  select,
  [tabindex]:not([tabindex="-1"]) {
    outline: none;
    transition: box-shadow 200ms ease-in-out;

    &:focus-visible {
      outline: none;
      box-shadow: 0 0 0 2px #fff, 0 0 0 4px #3b82f6;
    }
  }
}

// ============================================
// REDUCED MOTION
// ============================================

@media (prefers-reduced-motion: reduce) {
  .focus-ring,
  .focus-ring-visible,
  .focus-ring--scale,
  .focus-ring--pulse {
    transition: none;
    animation: none;
  }
}
```

### Import dans votre projet

```scss
// Dans styles.scss
@import "utilities/focus-ring";
```

## 💡 Utilisation de base

### Exemple 1 : Button avec focus ring

```html
<button class="btn focus-ring-visible rounded-lg">Click me</button>

<style>
  .btn {
    padding: 1rem 2rem;
    background: #3b82f6;
    color: white;
    border: none;
    cursor: pointer;
    font-weight: 600;
  }
</style>
```

### Exemple 2 : Input avec focus ring

```html
<input
  type="text"
  class="input focus-ring--input rounded-lg"
  placeholder="Enter your name"
/>

<style>
  .input {
    width: 100%;
    padding: 0.75rem 1rem;
    border: 1px solid #e5e7eb;
    font-size: 1rem;
  }
</style>
```

### Exemple 3 : Card clickable avec focus

```html
<a href="#" class="card focus-ring--card rounded-xl">
  <h3>Card Title</h3>
  <p>Card description</p>
</a>

<style>
  .card {
    display: block;
    padding: 2rem;
    background: white;
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
    text-decoration: none;
    color: inherit;
  }
</style>
```

### Exemple 4 : Focus ring custom

```html
<button class="focus-ring-visible focus-ring--lg focus-ring--purple rounded-lg">
  Large Purple Focus
</button>
```

## 📊 Paramètres

| Variable               | Type   | Défaut    | Description       |
| ---------------------- | ------ | --------- | ----------------- |
| `--focus-ring-color`   | color  | `#3b82f6` | Couleur du ring   |
| `--focus-ring-width`   | length | `2px`     | Épaisseur du ring |
| `--focus-ring-offset`  | length | `2px`     | Distance du ring  |
| `--focus-ring-opacity` | number | `0.5`     | Opacité           |

### Différence focus vs focus-visible

| Classe                | Déclenchement      | Usage           |
| --------------------- | ------------------ | --------------- |
| `.focus-ring`         | Clic ET clavier    | Tous les focus  |
| `.focus-ring-visible` | Clavier uniquement | Recommandé (UX) |

### Tailles disponibles

| Classe           | Width | Offset | Usage             |
| ---------------- | ----- | ------ | ----------------- |
| `focus-ring--sm` | 1px   | 1px    | Éléments compacts |
| `focus-ring--md` | 2px   | 2px    | Standard (défaut) |
| `focus-ring--lg` | 3px   | 2px    | Emphasis          |
| `focus-ring--xl` | 4px   | 3px    | Extra visibility  |

### Couleurs disponibles

| Classe               | Couleur | Hex     |
| -------------------- | ------- | ------- |
| `focus-ring--blue`   | Bleu    | #3b82f6 |
| `focus-ring--purple` | Violet  | #8b5cf6 |
| `focus-ring--green`  | Vert    | #10b981 |
| `focus-ring--red`    | Rouge   | #ef4444 |
| `focus-ring--orange` | Orange  | #f59e0b |
| `focus-ring--pink`   | Rose    | #ec4899 |
| `focus-ring--gray`   | Gris    | #6b7280 |
| `focus-ring--black`  | Noir    | #000000 |
| `focus-ring--white`  | Blanc   | #ffffff |

## 📚 Exemples détaillés

### Exemple 1 : Form complet avec focus rings

```html
<form class="contact-form">
  <div class="stack stack--lg">
    <h2>Contact Us</h2>

    <div class="form-group stack stack--sm">
      <label for="name" class="form-label">Full Name</label>
      <input
        type="text"
        id="name"
        class="form-input focus-ring--input rounded-lg"
        placeholder="John Doe"
        required
      />
    </div>

    <div class="form-group stack stack--sm">
      <label for="email" class="form-label">Email Address</label>
      <input
        type="email"
        id="email"
        class="form-input focus-ring--input rounded-lg"
        placeholder="john@example.com"
        required
      />
    </div>

    <div class="form-group stack stack--sm">
      <label for="phone" class="form-label">Phone Number</label>
      <input
        type="tel"
        id="phone"
        class="form-input focus-ring--input rounded-lg"
        placeholder="+33 6 12 34 56 78"
      />
    </div>

    <div class="form-group stack stack--sm">
      <label for="subject" class="form-label">Subject</label>
      <select
        id="subject"
        class="form-select focus-ring--input rounded-lg"
        required
      >
        <option value="">Select a subject</option>
        <option value="general">General Inquiry</option>
        <option value="support">Technical Support</option>
        <option value="sales">Sales Question</option>
        <option value="feedback">Feedback</option>
      </select>
    </div>

    <div class="form-group stack stack--sm">
      <label for="message" class="form-label">Message</label>
      <textarea
        id="message"
        class="form-textarea focus-ring--input rounded-lg"
        rows="5"
        placeholder="Your message here..."
        required
      ></textarea>
    </div>

    <div class="form-group">
      <label class="checkbox-label focus-within-ring rounded">
        <input
          type="checkbox"
          class="form-checkbox focus-ring-visible focus-ring--sm"
          required
        />
        <span>I agree to the terms and conditions</span>
      </label>
    </div>

    <div class="stack stack--horizontal stack--sm">
      <button
        type="submit"
        class="btn-primary focus-ring-visible focus-ring--button rounded-lg"
      >
        Send Message
      </button>
      <button
        type="reset"
        class="btn-secondary focus-ring-visible focus-ring--button rounded-lg"
      >
        Reset
      </button>
    </div>
  </div>
</form>

<style>
  .contact-form {
    max-width: 600px;
    margin: 3rem auto;
    padding: 2.5rem;
    background: white;
    border-radius: 1rem;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  }

  .contact-form h2 {
    margin: 0;
    font-size: 2rem;
  }

  .form-label {
    font-weight: 600;
    color: #374151;
    display: block;
  }

  .form-input,
  .form-select,
  .form-textarea {
    width: 100%;
    padding: 0.75rem 1rem;
    border: 1px solid #e5e7eb;
    font-size: 1rem;
    font-family: inherit;
  }

  .form-textarea {
    resize: vertical;
  }

  .checkbox-label {
    display: flex;
    align-items: center;
    gap: 0.75rem;
    padding: 0.75rem;
    cursor: pointer;
  }

  .form-checkbox {
    width: 20px;
    height: 20px;
    cursor: pointer;
  }

  .btn-primary,
  .btn-secondary {
    padding: 0.875rem 2rem;
    border: none;
    cursor: pointer;
    font-weight: 600;
    font-size: 1rem;
    transition: all 200ms;
  }

  .btn-primary {
    background: #3b82f6;
    color: white;
  }

  .btn-primary:hover {
    background: #2563eb;
  }

  .btn-secondary {
    background: #f3f4f6;
    color: #374151;
  }

  .btn-secondary:hover {
    background: #e5e7eb;
  }
</style>
```

### Exemple 2 : Navigation avec focus styles

```html
<nav class="main-nav" role="navigation">
  <div class="container">
    <div class="stack stack--horizontal stack--justify-between">
      <a href="#" class="logo focus-ring-visible focus-ring--lg rounded-lg">
        <img src="logo.svg" alt="Company Logo" />
      </a>

      <ul class="nav-menu stack stack--horizontal stack--md">
        <li>
          <a href="#home" class="nav-link focus-ring-visible rounded-lg">
            Home
          </a>
        </li>
        <li>
          <a href="#about" class="nav-link focus-ring-visible rounded-lg">
            About
          </a>
        </li>
        <li>
          <a href="#services" class="nav-link focus-ring-visible rounded-lg">
            Services
          </a>
        </li>
        <li>
          <a href="#portfolio" class="nav-link focus-ring-visible rounded-lg">
            Portfolio
          </a>
        </li>
        <li>
          <a href="#contact" class="nav-link focus-ring-visible rounded-lg">
            Contact
          </a>
        </li>
      </ul>

      <div class="stack stack--horizontal stack--sm">
        <button
          class="btn-outline focus-ring-visible focus-ring--button rounded-lg"
        >
          Sign In
        </button>
        <button
          class="btn-primary focus-ring-visible focus-ring--button rounded-lg"
        >
          Sign Up
        </button>
      </div>
    </div>
  </div>
</nav>

<!-- Skip Link pour accessibilité -->
<a href="#main-content" class="skip-link"> Skip to main content </a>

<style>
  .main-nav {
    background: white;
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
    padding: 1rem 0;
    position: sticky;
    top: 0;
    z-index: 100;
  }

  .container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 2rem;
  }

  .logo {
    display: block;
    text-decoration: none;
  }

  .logo img {
    height: 40px;
  }

  .nav-menu {
    list-style: none;
    margin: 0;
    padding: 0;
  }

  .nav-link {
    text-decoration: none;
    color: #374151;
    font-weight: 500;
    padding: 0.5rem 0.75rem;
    display: block;
    transition: color 200ms;
  }

  .nav-link:hover {
    color: #3b82f6;
  }

  .btn-outline,
  .btn-primary {
    padding: 0.5rem 1.25rem;
    border: none;
    cursor: pointer;
    font-weight: 600;
    transition: all 200ms;
  }

  .btn-outline {
    background: transparent;
    border: 1px solid #e5e7eb;
    color: #374151;
  }

  .btn-outline:hover {
    border-color: #3b82f6;
    color: #3b82f6;
  }

  .btn-primary {
    background: #3b82f6;
    color: white;
  }

  .btn-primary:hover {
    background: #2563eb;
  }
</style>
```

### Exemple 3 : Cards grid avec focus effects

```html
<div class="cards-grid-section">
  <div class="container">
    <h2 class="section-title">Our Services</h2>

    <div class="card-grid">
      <!-- Card 1 -->
      <a href="#web-design" class="service-card focus-ring--card rounded-2xl">
        <div class="service-icon">🎨</div>
        <h3 class="service-title">Web Design</h3>
        <p class="service-description">
          Beautiful and responsive designs that engage your users
        </p>
        <span class="service-cta">Learn more →</span>
      </a>

      <!-- Card 2 -->
      <a href="#development" class="service-card focus-ring--card rounded-2xl">
        <div class="service-icon">💻</div>
        <h3 class="service-title">Development</h3>
        <p class="service-description">
          Modern web applications built with cutting-edge technology
        </p>
        <span class="service-cta">Learn more →</span>
      </a>

      <!-- Card 3 -->
      <a href="#seo" class="service-card focus-ring--card rounded-2xl">
        <div class="service-icon">📈</div>
        <h3 class="service-title">SEO</h3>
        <p class="service-description">
          Boost your online visibility and reach more customers
        </p>
        <span class="service-cta">Learn more →</span>
      </a>

      <!-- Card 4 -->
      <a href="#marketing" class="service-card focus-ring--card rounded-2xl">
        <div class="service-icon">📱</div>
        <h3 class="service-title">Digital Marketing</h3>
        <p class="service-description">
          Strategic campaigns that drive real business results
        </p>
        <span class="service-cta">Learn more →</span>
      </a>

      <!-- Card 5 -->
      <a href="#branding" class="service-card focus-ring--card rounded-2xl">
        <div class="service-icon">✨</div>
        <h3 class="service-title">Branding</h3>
        <p class="service-description">
          Create a memorable brand identity that stands out
        </p>
        <span class="service-cta">Learn more →</span>
      </a>

      <!-- Card 6 -->
      <a href="#consulting" class="service-card focus-ring--card rounded-2xl">
        <div class="service-icon">💡</div>
        <h3 class="service-title">Consulting</h3>
        <p class="service-description">
          Expert advice to help your business grow and succeed
        </p>
        <span class="service-cta">Learn more →</span>
      </a>
    </div>
  </div>
</div>

<style>
  .cards-grid-section {
    padding: 5rem 2rem;
    background: #f9fafb;
  }

  .section-title {
    font-size: 3rem;
    text-align: center;
    margin: 0 0 3rem 0;
  }

  .card-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2rem;
  }

  .service-card {
    display: block;
    padding: 2.5rem 2rem;
    background: white;
    text-decoration: none;
    color: inherit;
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
    cursor: pointer;
  }

  .service-icon {
    font-size: 3rem;
    margin-bottom: 1.5rem;
  }

  .service-title {
    margin: 0 0 1rem 0;
    font-size: 1.5rem;
  }

  .service-description {
    margin: 0 0 1.5rem 0;
    color: #6b7280;
    line-height: 1.6;
  }

  .service-cta {
    color: #3b82f6;
    font-weight: 600;
  }

  .service-card:hover .service-cta {
    text-decoration: underline;
  }
</style>
```

### Exemple 4 : Tabs avec focus management

```html
<div class="tabs-container">
  <div class="tabs-header" role="tablist">
    <button
      role="tab"
      aria-selected="true"
      aria-controls="tab-panel-1"
      class="tab-button focus-ring-visible focus-ring--blue active"
    >
      Overview
    </button>
    <button
      role="tab"
      aria-selected="false"
      aria-controls="tab-panel-2"
      class="tab-button focus-ring-visible focus-ring--blue"
    >
      Features
    </button>
    <button
      role="tab"
      aria-selected="false"
      aria-controls="tab-panel-3"
      class="tab-button focus-ring-visible focus-ring--blue"
    >
      Pricing
    </button>
    <button
      role="tab"
      aria-selected="false"
      aria-controls="tab-panel-4"
      class="tab-button focus-ring-visible focus-ring--blue"
    >
      Reviews
    </button>
  </div>

  <div class="tabs-content">
    <div id="tab-panel-1" role="tabpanel" class="tab-panel active" tabindex="0">
      <h3>Product Overview</h3>
      <p>
        Our flagship product combines cutting-edge technology with intuitive
        design to deliver an exceptional user experience.
      </p>
    </div>

    <div id="tab-panel-2" role="tabpanel" class="tab-panel" tabindex="0" hidden>
      <h3>Key Features</h3>
      <ul>
        <li>Real-time collaboration</li>
        <li>Advanced analytics</li>
        <li>Cloud sync</li>
        <li>Mobile apps</li>
      </ul>
    </div>

    <div id="tab-panel-3" role="tabpanel" class="tab-panel" tabindex="0" hidden>
      <h3>Pricing Plans</h3>
      <p>Choose the plan that fits your needs.</p>
    </div>

    <div id="tab-panel-4" role="tabpanel" class="tab-panel" tabindex="0" hidden>
      <h3>Customer Reviews</h3>
      <p>See what our customers are saying.</p>
    </div>
  </div>
</div>

<style>
  .tabs-container {
    max-width: 800px;
    margin: 3rem auto;
    background: white;
    border-radius: 1rem;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    overflow: hidden;
  }

  .tabs-header {
    display: flex;
    background: #f9fafb;
    border-bottom: 1px solid #e5e7eb;
  }

  .tab-button {
    flex: 1;
    padding: 1.25rem 1.5rem;
    background: transparent;
    border: none;
    border-bottom: 2px solid transparent;
    cursor: pointer;
    font-weight: 600;
    color: #6b7280;
    transition: all 200ms;
  }

  .tab-button:hover {
    color: #3b82f6;
    background: rgba(59, 130, 246, 0.05);
  }

  .tab-button.active {
    color: #3b82f6;
    border-bottom-color: #3b82f6;
    background: white;
  }

  .tabs-content {
    padding: 2.5rem;
  }

  .tab-panel {
    display: none;
  }

  .tab-panel.active {
    display: block;
  }

  .tab-panel h3 {
    margin: 0 0 1rem 0;
    font-size: 1.75rem;
  }

  .tab-panel p {
    margin: 0;
    color: #374151;
    line-height: 1.6;
  }

  .tab-panel ul {
    margin: 0;
    padding-left: 1.5rem;
  }

  .tab-panel li {
    margin-bottom: 0.75rem;
    color: #374151;
  }
</style>

<script>
  // Tabs keyboard navigation
  const tabs = document.querySelectorAll('[role="tab"]');
  const panels = document.querySelectorAll('[role="tabpanel"]');

  tabs.forEach((tab, index) => {
    tab.addEventListener("click", () => {
      // Désactiver tous les tabs
      tabs.forEach((t) => {
        t.setAttribute("aria-selected", "false");
        t.classList.remove("active");
      });

      // Cacher tous les panels
      panels.forEach((p) => {
        p.classList.remove("active");
        p.hidden = true;
      });

      // Activer le tab cliqué
      tab.setAttribute("aria-selected", "true");
      tab.classList.add("active");

      // Afficher le panel correspondant
      panels[index].classList.add("active");
      panels[index].hidden = false;
    });

    // Navigation au clavier
    tab.addEventListener("keydown", (e) => {
      let newIndex = index;

      if (e.key === "ArrowRight") {
        newIndex = index < tabs.length - 1 ? index + 1 : 0;
      } else if (e.key === "ArrowLeft") {
        newIndex = index > 0 ? index - 1 : tabs.length - 1;
      } else if (e.key === "Home") {
        newIndex = 0;
      } else if (e.key === "End") {
        newIndex = tabs.length - 1;
      } else {
        return;
      }

      e.preventDefault();
      tabs[newIndex].click();
      tabs[newIndex].focus();
    });
  });
</script>
```

### Exemple 5 : Modal avec focus trap

```html
<!-- Trigger button -->
<button
  id="open-modal"
  class="btn-primary focus-ring-visible focus-ring--button rounded-lg"
>
  Open Modal
</button>

<!-- Modal -->
<div
  id="modal"
  class="modal"
  role="dialog"
  aria-modal="true"
  aria-labelledby="modal-title"
  hidden
>
  <div class="modal-overlay"></div>

  <div class="modal-content rounded-2xl">
    <div class="modal-header">
      <h2 id="modal-title">Subscribe to Newsletter</h2>
      <button
        id="close-modal"
        class="modal-close focus-ring-visible focus-ring--red rounded-full"
        aria-label="Close modal"
      >
        ✕
      </button>
    </div>

    <div class="modal-body">
      <p>Stay updated with our latest news and offers!</p>

      <form class="stack stack--md">
        <div class="stack stack--sm">
          <label for="modal-email">Email Address</label>
          <input
            type="email"
            id="modal-email"
            class="form-input focus-ring--input rounded-lg"
            placeholder="your@email.com"
            required
          />
        </div>

        <label class="checkbox-label focus-within-ring rounded">
          <input
            type="checkbox"
            class="form-checkbox focus-ring-visible focus-ring--sm"
          />
          <span>I agree to receive marketing emails</span>
        </label>
      </form>
    </div>

    <div class="modal-footer">
      <button
        class="btn-secondary focus-ring-visible focus-ring--button rounded-lg"
        id="cancel-modal"
      >
        Cancel
      </button>
      <button
        class="btn-primary focus-ring-visible focus-ring--button rounded-lg"
      >
        Subscribe
      </button>
    </div>
  </div>
</div>

<style>
  .btn-primary {
    padding: 1rem 2rem;
    background: #3b82f6;
    color: white;
    border: none;
    cursor: pointer;
    font-weight: 600;
  }

  .modal {
    position: fixed;
    inset: 0;
    z-index: 1000;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 2rem;
  }

  .modal[hidden] {
    display: none;
  }

  .modal-overlay {
    position: absolute;
    inset: 0;
    background: rgba(0, 0, 0, 0.5);
    backdrop-filter: blur(4px);
  }

  .modal-content {
    position: relative;
    z-index: 1;
    max-width: 500px;
    width: 100%;
    background: white;
    box-shadow: 0 20px 40px rgba(0, 0, 0, 0.2);
  }

  .modal-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 2rem 2rem 1rem;
    border-bottom: 1px solid #e5e7eb;
  }

  .modal-header h2 {
    margin: 0;
    font-size: 1.75rem;
  }

  .modal-close {
    width: 36px;
    height: 36px;
    display: flex;
    align-items: center;
    justify-content: center;
    background: #fef2f2;
    border: none;
    cursor: pointer;
    color: #ef4444;
    font-size: 1.25rem;
    transition: all 200ms;
  }

  .modal-close:hover {
    background: #fee2e2;
  }

  .modal-body {
    padding: 2rem;
  }

  .modal-body p {
    margin: 0 0 1.5rem 0;
    color: #6b7280;
  }

  .modal-footer {
    padding: 1rem 2rem 2rem;
    display: flex;
    justify-content: flex-end;
    gap: 1rem;
  }

  .btn-secondary {
    padding: 0.75rem 1.5rem;
    background: #f3f4f6;
    color: #374151;
    border: none;
    cursor: pointer;
    font-weight: 600;
  }

  .form-input {
    width: 100%;
    padding: 0.75rem 1rem;
    border: 1px solid #e5e7eb;
    font-size: 1rem;
  }

  .checkbox-label {
    display: flex;
    align-items: center;
    gap: 0.75rem;
    padding: 0.75rem;
    cursor: pointer;
  }

  .form-checkbox {
    width: 20px;
    height: 20px;
  }
</style>

<script>
  const modal = document.getElementById("modal");
  const openBtn = document.getElementById("open-modal");
  const closeBtn = document.getElementById("close-modal");
  const cancelBtn = document.getElementById("cancel-modal");
  const overlay = document.querySelector(".modal-overlay");

  let previousFocus;

  function openModal() {
    previousFocus = document.activeElement;
    modal.hidden = false;
    document.body.style.overflow = "hidden";

    // Focus sur le premier élément focusable
    const firstInput = modal.querySelector("input");
    firstInput.focus();
  }

  function closeModal() {
    modal.hidden = true;
    document.body.style.overflow = "";
    previousFocus?.focus();
  }

  openBtn.addEventListener("click", openModal);
  closeBtn.addEventListener("click", closeModal);
  cancelBtn.addEventListener("click", closeModal);
  overlay.addEventListener("click", closeModal);

  // Escape key pour fermer
  document.addEventListener("keydown", (e) => {
    if (e.key === "Escape" && !modal.hidden) {
      closeModal();
    }
  });

  // Focus trap
  const focusableElements =
    'button, [href], input, select, textarea, [tabindex]:not([tabindex="-1"])';

  modal.addEventListener("keydown", (e) => {
    if (e.key === "Tab") {
      const focusables = modal.querySelectorAll(focusableElements);
      const first = focusables[0];
      const last = focusables[focusables.length - 1];

      if (e.shiftKey && document.activeElement === first) {
        e.preventDefault();
        last.focus();
      } else if (!e.shiftKey && document.activeElement === last) {
        e.preventDefault();
        first.focus();
      }
    }
  });
</script>
```

### Exemple 6 : Search bar avec focus states

```html
<div class="search-container">
  <form class="search-form focus-within-ring rounded-full">
    <input
      type="search"
      class="search-input focus-ring--none"
      placeholder="Search products, articles, pages..."
      aria-label="Search"
    />
    <button
      type="submit"
      class="search-button focus-ring-visible focus-ring--white rounded-full"
      aria-label="Submit search"
    >
      🔍
    </button>
  </form>

  <!-- Search suggestions -->
  <div class="search-suggestions" hidden>
    <a href="#" class="suggestion-item focus-ring--link">
      <span class="suggestion-icon">🔍</span>
      <span>iPhone 15 Pro</span>
    </a>
    <a href="#" class="suggestion-item focus-ring--link">
      <span class="suggestion-icon">🔍</span>
      <span>Wireless headphones</span>
    </a>
    <a href="#" class="suggestion-item focus-ring--link">
      <span class="suggestion-icon">🔍</span>
      <span>Smart watch</span>
    </a>
  </div>
</div>

<style>
  .search-container {
    max-width: 600px;
    margin: 3rem auto;
    position: relative;
  }

  .search-form {
    display: flex;
    align-items: center;
    background: white;
    border: 2px solid #e5e7eb;
    padding: 0.5rem;
    transition: border-color 200ms, box-shadow 200ms;
  }

  .search-input {
    flex: 1;
    padding: 0.75rem 1.25rem;
    border: none;
    font-size: 1rem;
    background: transparent;
  }

  .search-input:focus {
    outline: none;
  }

  .search-button {
    width: 48px;
    height: 48px;
    display: flex;
    align-items: center;
    justify-content: center;
    background: #3b82f6;
    border: none;
    cursor: pointer;
    font-size: 1.25rem;
    flex-shrink: 0;
  }

  .search-suggestions {
    position: absolute;
    top: calc(100% + 0.5rem);
    left: 0;
    right: 0;
    background: white;
    border: 1px solid #e5e7eb;
    border-radius: 1rem;
    box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
    overflow: hidden;
  }

  .suggestion-item {
    display: flex;
    align-items: center;
    gap: 1rem;
    padding: 1rem 1.5rem;
    text-decoration: none;
    color: #374151;
    transition: background-color 200ms;
  }

  .suggestion-item:hover {
    background: #f9fafb;
  }

  .suggestion-icon {
    color: #9ca3af;
  }
</style>
```

## 🎨 Personnalisation avancée

### Couleur custom

```html
<button class="focus-ring-visible" style="--focus-ring-color: #ec4899">
  Custom pink focus
</button>
```

### Width et offset custom

```html
<button
  class="focus-ring-visible"
  style="--focus-ring-width: 5px; --focus-ring-offset: 5px"
>
  Extra large focus
</button>
```

### Focus ring avec gradient

```scss
.focus-ring--gradient {
  &:focus-visible {
    box-shadow: 0 0 0 2px #fff, 0 0 0 4px transparent;
    background-image: linear-gradient(white, white), linear-gradient(135deg, #667eea, #764ba2);
    background-origin: padding-box, border-box;
    background-clip: padding-box, border-box;
    border: 4px solid transparent;
  }
}
```

## 🎯 Cas d'usage courants

### 1. Forms

```html
<input class="focus-ring--input" />
```

### 2. Buttons

```html
<button class="focus-ring-visible focus-ring--button"></button>
```

### 3. Links

```html
<a href="#" class="focus-ring--link"></a>
```

### 4. Cards

```html
<div class="focus-ring--card"></div>
```

### 5. Navigation

```html
<a class="focus-ring-visible"></a>
```

## 🔧 Combinaison avec autres utilitaires

### Avec Rounded

```html
<button class="focus-ring-visible rounded-lg"></button>
```

### Avec Hover Effects

```html
<button class="focus-ring-visible hover-lift"></button>
```

### Avec Transition

```html
<button class="focus-ring-visible transition-normal"></button>
```

## 📱 Comportement responsive

Les focus rings s'adaptent automatiquement à tous les écrans.

### Ajuster sur mobile

```scss
@media (max-width: 767px) {
  .focus-ring--lg {
    --focus-ring-width: 2px;
  }
}
```

## ⚡ Performance & Bonnes pratiques

### ✅ À faire

```html
<!-- Bon : focus-visible pour UX -->
<button class="focus-ring-visible">
  <!-- Bon : Couleur contrastée -->
  <button class="focus-ring-visible focus-ring--blue">
    <!-- Bon : Skip link pour accessibilité -->
    <a href="#main" class="skip-link">
      <!-- Bon : Focus trap dans modal -->
      <!-- Voir exemple modal --></a
    >
  </button>
</button>
```

### ❌ À éviter

```html
<!-- Mauvais : Supprimer complètement focus -->
<button style="outline: none;">
  <!-- Mauvais : Couleur non contrastée -->
  <button class="focus-ring-visible" style="--focus-ring-color: #f0f0f0">
    <!-- Mauvais : Oublier focus dans modal -->
  </button>
</button>
```

## 🌐 Compatibilité navigateurs

| Navigateur | Version minimale | Support           |
| ---------- | ---------------- | ----------------- |
| Chrome     | 86+              | ✅ :focus-visible |
| Firefox    | 85+              | ✅ :focus-visible |
| Safari     | 15.4+            | ✅ :focus-visible |
| Edge       | 86+              | ✅ :focus-visible |

**Note** : :focus-visible nécessite versions récentes. Fallback sur :focus pour anciens navigateurs.

## 🐛 Troubleshooting

### Problème : Focus visible au clic

**Solution** : Utilisez focus-visible

```css
.focus-ring-visible:focus-visible {
  /* Styles uniquement clavier */
}
```

### Problème : Focus ring coupé

**Solution** : Ajoutez padding au parent

```css
.container {
  padding: 0.5rem;
}
```

### Problème : Couleur non visible

**Solution** : Vérifiez le contraste

```css
--focus-ring-color: #3b82f6; /* Bon contraste */
```

## 📦 Classes complètes disponibles

```scss
// Base
.focus-ring {
  /* Focus always */
}
.focus-ring-visible {
  /* Focus keyboard only */
}

// Tailles
.focus-ring--sm {
  /* 1px */
}
.focus-ring--md {
  /* 2px */
}
.focus-ring--lg {
  /* 3px */
}
.focus-ring--xl {
  /* 4px */
}

// Couleurs
.focus-ring--blue, .focus-ring--purple
.focus-ring--green, .focus-ring--red
.focus-ring--orange, .focus-ring--pink
.focus-ring--gray, .focus-ring--black
.focus-ring--white

// Offsets
.focus-ring--offset-0, .focus-ring--offset-1
.focus-ring--offset-2, .focus-ring--offset-4

// Styles
.focus-ring--glow {
  /* Avec glow */
}
.focus-ring--inset {
  /* Inset */
}
.focus-ring--dashed {
  /* Dashed */
}
.focus-ring--dotted {
  /* Dotted */
}
.focus-ring--double {
  /* Double ring */
}

// Animations
.focus-ring--scale {
  /* Scale animation */
}
.focus-ring--pulse {
  /* Pulse */
}

// Presets
.focus-ring--input {
  /* Pour inputs */
}
.focus-ring--button {
  /* Pour buttons */
}
.focus-ring--card {
  /* Pour cards */
}
.focus-ring--link {
  /* Pour links */
}

// Utilitaires
.focus-within-ring {
  /* Container focus */
}
.skip-link {
  /* Skip navigation */
}
.focus-ring--none {
  /* Désactiver */
}
```

## 🎓 Ressources complémentaires

- [:focus-visible - MDN](https://developer.mozilla.org/fr/docs/Web/CSS/:focus-visible)
- [WCAG Focus Visible](https://www.w3.org/WAI/WCAG21/Understanding/focus-visible.html)
- [Focus Management - A11y](https://www.a11yproject.com/posts/how-to-use-the-tabindex-attribute/)

## 📝 Changelog

- **v1.0** - Version initiale avec focus-ring de base
- **v1.1** - Ajout focus-visible (keyboard only)
- **v1.2** - Tailles et couleurs
- **v1.3** - Presets par type d'élément
- **v1.4** - Focus within et animations
- **v1.5** - Skip link et accessibilité

---

**Made with ❤️ for accessible web**
