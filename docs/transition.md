# Transition Utility

> Système de transitions CSS cohérent pour animer les changements de propriétés avec élégance et fluidité

## 📋 Description

**Transition** est un utilitaire CSS qui fournit un système complet pour gérer les transitions (animations de changement d'état) de manière cohérente. Il offre des durées prédéfinies, des fonctions de timing (easing), et un contrôle précis sur les propriétés à animer pour créer des interfaces fluides et réactives.

### ✨ Caractéristiques principales

- ⏱️ **Durées prédéfinies** : De ultra-rapide à très lente
- 🎭 **Timing functions** : Ease, linear, spring, bounce, etc.
- 🎯 **Propriétés spécifiques** : Transition ciblée (colors, transform, opacity, etc.)
- 🔧 **Variables CSS** : Personnalisation complète
- ⚡ **Performance** : Transitions optimisées GPU
- 🎨 **Delays configurables** : Contrôle du timing
- 🔄 **Presets utiles** : Configurations courantes prêtes

## 🚀 Installation

### Code SCSS

```scss
// _transition.scss

// Échelle de durées (en millisecondes)
$duration-scale: (
  "instant": 75ms,
  "fast": 150ms,
  "normal": 300ms,
  "slow": 500ms,
  "slower": 700ms,
  "slowest": 1000ms,
);

// Timing functions
$timing-functions: (
  "linear": linear,
  "ease": ease,
  "ease-in": ease-in,
  "ease-out": ease-out,
  "ease-in-out": ease-in-out,
  "spring": cubic-bezier(0.68, -0.55, 0.265, 1.55),
  "bounce": cubic-bezier(0.68, -0.55, 0.265, 1.55),
  "smooth": cubic-bezier(0.4, 0, 0.2, 1),
);

.transition {
  // Variables par défaut
  --transition-duration: 300ms; // Durée
  --transition-timing: ease-in-out; // Fonction de timing
  --transition-property: all; // Propriété(s) à animer
  --transition-delay: 0ms; // Délai avant démarrage

  transition: var(--transition-property) var(--transition-duration) var(
      --transition-timing
    ) var(--transition-delay);
}

// Variantes de durée
.transition-instant {
  transition-duration: 75ms;
}

.transition-fast {
  transition-duration: 150ms;
}

.transition-normal {
  transition-duration: 300ms; // Défaut
}

.transition-slow {
  transition-duration: 500ms;
}

.transition-slower {
  transition-duration: 700ms;
}

.transition-slowest {
  transition-duration: 1000ms;
}

// Variantes de timing function
.transition-linear {
  transition-timing-function: linear;
}

.transition-ease {
  transition-timing-function: ease;
}

.transition-ease-in {
  transition-timing-function: ease-in;
}

.transition-ease-out {
  transition-timing-function: ease-out;
}

.transition-ease-in-out {
  transition-timing-function: ease-in-out;
}

.transition-spring {
  transition-timing-function: cubic-bezier(0.68, -0.55, 0.265, 1.55);
}

.transition-smooth {
  transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
}

// Variantes par propriété spécifique
.transition-none {
  transition: none;
}

.transition-all {
  transition-property: all;
}

.transition-colors {
  transition-property: color, background-color, border-color, fill, stroke;
}

.transition-opacity {
  transition-property: opacity;
}

.transition-shadow {
  transition-property: box-shadow;
}

.transition-transform {
  transition-property: transform;
}

// Presets courants
.transition-colors-fast {
  transition: color 150ms ease-in-out, background-color 150ms ease-in-out,
    border-color 150ms ease-in-out;
}

.transition-transform-normal {
  transition: transform 300ms ease-in-out;
}

.transition-opacity-fast {
  transition: opacity 150ms ease-in-out;
}

.transition-all-normal {
  transition: all 300ms ease-in-out;
}

// Hover effects presets
.hover-lift {
  transition: transform 300ms ease-in-out, box-shadow 300ms ease-in-out;

  &:hover {
    transform: translateY(-4px);
    box-shadow: 0 12px 24px rgba(0, 0, 0, 0.15);
  }
}

.hover-scale {
  transition: transform 300ms ease-in-out;

  &:hover {
    transform: scale(1.05);
  }
}

.hover-scale-sm {
  transition: transform 300ms ease-in-out;

  &:hover {
    transform: scale(1.02);
  }
}

.hover-rotate {
  transition: transform 300ms ease-in-out;

  &:hover {
    transform: rotate(5deg);
  }
}

.hover-brighten {
  transition: filter 300ms ease-in-out;

  &:hover {
    filter: brightness(1.1);
  }
}

.hover-blur {
  transition: filter 300ms ease-in-out;

  &:hover {
    filter: blur(2px);
  }
}

.hover-opacity {
  transition: opacity 300ms ease-in-out;

  &:hover {
    opacity: 0.7;
  }
}

// Focus effects
.focus-ring {
  transition: box-shadow 150ms ease-in-out, border-color 150ms ease-in-out;

  &:focus,
  &:focus-visible {
    outline: none;
    border-color: #3b82f6;
    box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.3);
  }
}

// Delays
.transition-delay-75 {
  transition-delay: 75ms;
}

.transition-delay-100 {
  transition-delay: 100ms;
}

.transition-delay-150 {
  transition-delay: 150ms;
}

.transition-delay-200 {
  transition-delay: 200ms;
}

.transition-delay-300 {
  transition-delay: 300ms;
}

.transition-delay-500 {
  transition-delay: 500ms;
}

.transition-delay-700 {
  transition-delay: 700ms;
}

.transition-delay-1000 {
  transition-delay: 1000ms;
}

// Désactiver les transitions (utile pour reduce-motion)
@media (prefers-reduced-motion: reduce) {
  .transition,
  .transition-instant,
  .transition-fast,
  .transition-normal,
  .transition-slow,
  .transition-slower,
  .transition-slowest {
    transition-duration: 0.01ms !important;
  }
}
```

### Import dans votre projet

```scss
// Dans styles.scss
@import "utilities/transition";
```

## 💡 Utilisation de base

### Exemple 1 : Button avec transition simple

```html
<button class="btn transition hover-lift">Hover me!</button>

<style>
  .btn {
    padding: 1rem 2rem;
    background: #3b82f6;
    color: white;
    border: none;
    border-radius: 0.5rem;
    cursor: pointer;
  }
</style>
```

### Exemple 2 : Card avec transition personnalisée

```html
<div class="card transition-slow transition-ease-in-out">
  <h3>Card Title</h3>
  <p>Hover pour voir la transition lente</p>
</div>

<style>
  .card {
    padding: 2rem;
    background: white;
    border-radius: 0.5rem;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }

  .card:hover {
    box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
    transform: scale(1.02);
  }
</style>
```

### Exemple 3 : Transition sur couleurs uniquement

```html
<button class="btn transition-colors-fast">Color transition</button>

<style>
  .btn {
    padding: 1rem 2rem;
    background: #10b981;
    color: white;
    border: none;
    border-radius: 0.5rem;
    cursor: pointer;
  }

  .btn:hover {
    background: #059669;
  }
</style>
```

### Exemple 4 : Transition avec delay

```html
<div class="element transition transition-delay-300">Transition avec delay</div>

<style>
  .element {
    padding: 2rem;
    background: #667eea;
    color: white;
    border-radius: 0.5rem;
  }

  .element:hover {
    background: #764ba2;
  }
</style>
```

## 📊 Paramètres

| Variable                | Type             | Défaut        | Description            |
| ----------------------- | ---------------- | ------------- | ---------------------- |
| `--transition-duration` | time             | `300ms`       | Durée de la transition |
| `--transition-timing`   | keyword/function | `ease-in-out` | Fonction de timing     |
| `--transition-property` | keyword          | `all`         | Propriété(s) à animer  |
| `--transition-delay`    | time             | `0ms`         | Délai avant démarrage  |

### Échelle de durées

| Classe               | Durée  | Usage                  |
| -------------------- | ------ | ---------------------- |
| `transition-instant` | 75ms   | Feedback immédiat      |
| `transition-fast`    | 150ms  | Changements rapides    |
| `transition-normal`  | 300ms  | Standard (défaut)      |
| `transition-slow`    | 500ms  | Transitions prononcées |
| `transition-slower`  | 700ms  | Effets dramatiques     |
| `transition-slowest` | 1000ms | Animations lentes      |

### Timing functions

| Classe                   | Fonction     | Comportement                |
| ------------------------ | ------------ | --------------------------- |
| `transition-linear`      | linear       | Vitesse constante           |
| `transition-ease`        | ease         | Début rapide, fin lente     |
| `transition-ease-in`     | ease-in      | Accélération                |
| `transition-ease-out`    | ease-out     | Décélération                |
| `transition-ease-in-out` | ease-in-out  | Accél. puis décél. (défaut) |
| `transition-spring`      | cubic-bezier | Effet ressort               |
| `transition-smooth`      | cubic-bezier | Extra smooth                |

### Propriétés

| Classe                 | Propriétés animées                    |
| ---------------------- | ------------------------------------- |
| `transition-all`       | Toutes                                |
| `transition-colors`    | color, background-color, border-color |
| `transition-opacity`   | opacity                               |
| `transition-shadow`    | box-shadow                            |
| `transition-transform` | transform                             |

## 📚 Exemples détaillés

### Exemple 1 : Gallery d'effets hover

```html
<div class="hover-effects-gallery">
  <div class="effect-card hover-lift">
    <div class="effect-preview"></div>
    <h4>Hover Lift</h4>
    <p>Élève au survol</p>
  </div>

  <div class="effect-card hover-scale">
    <div class="effect-preview"></div>
    <h4>Hover Scale</h4>
    <p>Agrandit au survol</p>
  </div>

  <div class="effect-card hover-scale-sm">
    <div class="effect-preview"></div>
    <h4>Hover Scale SM</h4>
    <p>Agrandit légèrement</p>
  </div>

  <div class="effect-card hover-rotate">
    <div class="effect-preview"></div>
    <h4>Hover Rotate</h4>
    <p>Rotation au survol</p>
  </div>

  <div class="effect-card hover-brighten">
    <div class="effect-preview"></div>
    <h4>Hover Brighten</h4>
    <p>Éclaircit au survol</p>
  </div>

  <div class="effect-card hover-opacity">
    <div class="effect-preview"></div>
    <h4>Hover Opacity</h4>
    <p>Transparence au survol</p>
  </div>
</div>

<style>
  .hover-effects-gallery {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 2rem;
    padding: 2rem;
  }

  .effect-card {
    background: white;
    border-radius: 0.75rem;
    padding: 1.5rem;
    text-align: center;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
    cursor: pointer;
  }

  .effect-preview {
    width: 100%;
    height: 150px;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    border-radius: 0.5rem;
    margin-bottom: 1rem;
  }

  .effect-card h4 {
    margin: 0 0 0.5rem 0;
    font-size: 1.125rem;
  }

  .effect-card p {
    margin: 0;
    color: #6b7280;
    font-size: 0.875rem;
  }
</style>
```

### Exemple 2 : Buttons avec différentes durées

```html
<div class="button-timings">
  <button class="btn transition-instant">Instant (75ms)</button>

  <button class="btn transition-fast">Fast (150ms)</button>

  <button class="btn transition-normal">Normal (300ms)</button>

  <button class="btn transition-slow">Slow (500ms)</button>

  <button class="btn transition-slower">Slower (700ms)</button>

  <button class="btn transition-slowest">Slowest (1000ms)</button>
</div>

<style>
  .button-timings {
    display: flex;
    flex-wrap: wrap;
    gap: 1rem;
    padding: 2rem;
  }

  .btn {
    padding: 0.75rem 1.5rem;
    background: #3b82f6;
    color: white;
    border: none;
    border-radius: 0.5rem;
    cursor: pointer;
    font-weight: 600;
  }

  .btn:hover {
    background: #2563eb;
    transform: translateY(-2px);
  }
</style>
```

### Exemple 3 : Modal avec transitions

```html
<div class="modal-demo">
  <button class="open-modal-btn transition-colors-fast">Ouvrir Modal</button>

  <div class="modal-overlay transition-opacity-fast" id="modalOverlay">
    <div class="modal transition-transform-normal" id="modal">
      <header class="modal-header">
        <h2>Modal Title</h2>
        <button class="close-btn transition-colors-fast" id="closeModal">
          ×
        </button>
      </header>

      <div class="modal-content">
        <p>Contenu de la modal avec transitions fluides</p>
      </div>

      <footer class="modal-footer">
        <button class="btn transition-colors-fast">Annuler</button>
        <button class="btn btn-primary transition-colors-fast">
          Confirmer
        </button>
      </footer>
    </div>
  </div>
</div>

<style>
  .modal-overlay {
    position: fixed;
    inset: 0;
    background: rgba(0, 0, 0, 0.5);
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 1000;
    opacity: 0;
    pointer-events: none;
  }

  .modal-overlay.active {
    opacity: 1;
    pointer-events: auto;
  }

  .modal {
    background: white;
    border-radius: 1rem;
    width: 90%;
    max-width: 500px;
    box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
    transform: scale(0.9);
  }

  .modal-overlay.active .modal {
    transform: scale(1);
  }

  .modal-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1.5rem;
    border-bottom: 1px solid #e5e7eb;
  }

  .modal-header h2 {
    margin: 0;
  }

  .close-btn {
    width: 32px;
    height: 32px;
    border: none;
    background: #f3f4f6;
    border-radius: 0.375rem;
    font-size: 1.5rem;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .close-btn:hover {
    background: #e5e7eb;
  }

  .modal-content {
    padding: 1.5rem;
  }

  .modal-footer {
    display: flex;
    justify-content: flex-end;
    gap: 0.75rem;
    padding: 1.5rem;
    border-top: 1px solid #e5e7eb;
  }

  .btn {
    padding: 0.75rem 1.5rem;
    border: 1px solid #e5e7eb;
    background: white;
    border-radius: 0.5rem;
    cursor: pointer;
    font-weight: 600;
  }

  .btn:hover {
    background: #f9fafb;
  }

  .btn-primary {
    background: #3b82f6;
    color: white;
    border: none;
  }

  .btn-primary:hover {
    background: #2563eb;
  }

  .open-modal-btn {
    padding: 1rem 2rem;
    background: #3b82f6;
    color: white;
    border: none;
    border-radius: 0.5rem;
    cursor: pointer;
    font-weight: 600;
  }

  .open-modal-btn:hover {
    background: #2563eb;
  }
</style>

<script>
  const openBtn = document.querySelector(".open-modal-btn");
  const closeBtn = document.getElementById("closeModal");
  const overlay = document.getElementById("modalOverlay");

  openBtn.addEventListener("click", () => {
    overlay.classList.add("active");
  });

  closeBtn.addEventListener("click", () => {
    overlay.classList.remove("active");
  });

  overlay.addEventListener("click", (e) => {
    if (e.target === overlay) {
      overlay.classList.remove("active");
    }
  });
</script>
```

### Exemple 4 : Accordion avec transitions

```html
<div class="accordion">
  <div class="accordion-item">
    <button class="accordion-header transition-colors-fast">
      <span>Section 1</span>
      <span class="accordion-icon transition-transform-normal">▼</span>
    </button>
    <div class="accordion-content">
      <p>Contenu de la section 1 avec transition de hauteur</p>
    </div>
  </div>

  <div class="accordion-item">
    <button class="accordion-header transition-colors-fast">
      <span>Section 2</span>
      <span class="accordion-icon transition-transform-normal">▼</span>
    </button>
    <div class="accordion-content">
      <p>Contenu de la section 2 avec transition fluide</p>
    </div>
  </div>

  <div class="accordion-item">
    <button class="accordion-header transition-colors-fast">
      <span>Section 3</span>
      <span class="accordion-icon transition-transform-normal">▼</span>
    </button>
    <div class="accordion-content">
      <p>Contenu de la section 3 qui s'ouvre et se ferme</p>
    </div>
  </div>
</div>

<style>
  .accordion {
    max-width: 600px;
    margin: 2rem auto;
  }

  .accordion-item {
    background: white;
    border: 1px solid #e5e7eb;
    border-radius: 0.5rem;
    margin-bottom: 0.5rem;
    overflow: hidden;
  }

  .accordion-header {
    width: 100%;
    padding: 1.25rem;
    background: white;
    border: none;
    display: flex;
    justify-content: space-between;
    align-items: center;
    cursor: pointer;
    font-weight: 600;
    font-size: 1rem;
    text-align: left;
  }

  .accordion-header:hover {
    background: #f9fafb;
  }

  .accordion-icon {
    font-size: 0.875rem;
  }

  .accordion-item.active .accordion-icon {
    transform: rotate(180deg);
  }

  .accordion-content {
    max-height: 0;
    overflow: hidden;
    transition: max-height 300ms ease-in-out, padding 300ms ease-in-out;
    padding: 0 1.25rem;
  }

  .accordion-item.active .accordion-content {
    max-height: 500px;
    padding: 1.25rem;
  }

  .accordion-content p {
    margin: 0;
  }
</style>

<script>
  document.querySelectorAll(".accordion-header").forEach((header) => {
    header.addEventListener("click", () => {
      const item = header.parentElement;
      const wasActive = item.classList.contains("active");

      // Fermer tous les items
      document.querySelectorAll(".accordion-item").forEach((i) => {
        i.classList.remove("active");
      });

      // Ouvrir l'item cliqué (si non actif)
      if (!wasActive) {
        item.classList.add("active");
      }
    });
  });
</script>
```

### Exemple 5 : Cards avec staggered transitions

```html
<div class="staggered-cards">
  <div class="card transition" style="--transition-delay: 0ms">
    <h3>Card 1</h3>
    <p>Apparaît en premier</p>
  </div>

  <div class="card transition" style="--transition-delay: 100ms">
    <h3>Card 2</h3>
    <p>Apparaît après 100ms</p>
  </div>

  <div class="card transition" style="--transition-delay: 200ms">
    <h3>Card 3</h3>
    <p>Apparaît après 200ms</p>
  </div>

  <div class="card transition" style="--transition-delay: 300ms">
    <h3>Card 4</h3>
    <p>Apparaît après 300ms</p>
  </div>
</div>

<style>
  .staggered-cards {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 2rem;
    padding: 2rem;
  }

  .card {
    padding: 2rem;
    background: white;
    border-radius: 0.75rem;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
    opacity: 0;
    transform: translateY(20px);
    transition: opacity 500ms ease-out var(--transition-delay), transform 500ms
        ease-out var(--transition-delay);
  }

  .card.visible {
    opacity: 1;
    transform: translateY(0);
  }

  .card h3 {
    margin: 0 0 0.5rem 0;
  }

  .card p {
    margin: 0;
    color: #6b7280;
  }
</style>

<script>
  // Observer pour déclencher l'animation au scroll
  const observer = new IntersectionObserver((entries) => {
    entries.forEach((entry) => {
      if (entry.isIntersecting) {
        entry.target.classList.add("visible");
      }
    });
  });

  document.querySelectorAll(".staggered-cards .card").forEach((card) => {
    observer.observe(card);
  });
</script>
```

### Exemple 6 : Menu dropdown avec transitions

```html
<div class="dropdown">
  <button class="dropdown-trigger transition-colors-fast">Menu ▼</button>

  <div class="dropdown-menu transition">
    <a href="#" class="dropdown-item transition-colors-fast">Dashboard</a>
    <a href="#" class="dropdown-item transition-colors-fast">Profile</a>
    <a href="#" class="dropdown-item transition-colors-fast">Settings</a>
    <hr />
    <a href="#" class="dropdown-item transition-colors-fast">Logout</a>
  </div>
</div>

<style>
  .dropdown {
    position: relative;
    display: inline-block;
  }

  .dropdown-trigger {
    padding: 0.75rem 1.5rem;
    background: white;
    border: 1px solid #e5e7eb;
    border-radius: 0.5rem;
    cursor: pointer;
    font-weight: 600;
  }

  .dropdown-trigger:hover {
    background: #f9fafb;
  }

  .dropdown-menu {
    position: absolute;
    top: calc(100% + 0.5rem);
    left: 0;
    min-width: 200px;
    background: white;
    border: 1px solid #e5e7eb;
    border-radius: 0.5rem;
    box-shadow: 0 10px 30px rgba(0, 0, 0, 0.15);
    overflow: hidden;
    opacity: 0;
    transform: translateY(-10px);
    pointer-events: none;
    transition: opacity 200ms ease-out, transform 200ms ease-out;
  }

  .dropdown:hover .dropdown-menu {
    opacity: 1;
    transform: translateY(0);
    pointer-events: auto;
  }

  .dropdown-item {
    display: block;
    padding: 0.75rem 1rem;
    text-decoration: none;
    color: #374151;
  }

  .dropdown-item:hover {
    background: #f3f4f6;
  }

  .dropdown-menu hr {
    margin: 0.5rem 0;
    border: none;
    border-top: 1px solid #e5e7eb;
  }
</style>
```

### Exemple 7 : Tabs avec transitions

```html
<div class="tabs-container">
  <div class="tabs">
    <button class="tab active transition-colors-fast" data-tab="tab1">
      Tab 1
    </button>
    <button class="tab transition-colors-fast" data-tab="tab2">Tab 2</button>
    <button class="tab transition-colors-fast" data-tab="tab3">Tab 3</button>
  </div>

  <div class="tab-panels">
    <div class="tab-panel active transition" id="tab1">
      <h3>Content 1</h3>
      <p>Contenu du premier tab avec transition</p>
    </div>
    <div class="tab-panel transition" id="tab2">
      <h3>Content 2</h3>
      <p>Contenu du deuxième tab</p>
    </div>
    <div class="tab-panel transition" id="tab3">
      <h3>Content 3</h3>
      <p>Contenu du troisième tab</p>
    </div>
  </div>
</div>

<style>
  .tabs-container {
    max-width: 600px;
    margin: 2rem auto;
  }

  .tabs {
    display: flex;
    gap: 0.25rem;
    border-bottom: 2px solid #e5e7eb;
  }

  .tab {
    padding: 0.75rem 1.5rem;
    background: transparent;
    border: none;
    border-bottom: 2px solid transparent;
    cursor: pointer;
    font-weight: 600;
    color: #6b7280;
    margin-bottom: -2px;
  }

  .tab:hover {
    color: #374151;
  }

  .tab.active {
    color: #3b82f6;
    border-bottom-color: #3b82f6;
  }

  .tab-panels {
    position: relative;
    min-height: 200px;
  }

  .tab-panel {
    padding: 2rem;
    opacity: 0;
    transform: translateX(-20px);
    position: absolute;
    inset: 0;
    pointer-events: none;
    transition: opacity 300ms ease-out, transform 300ms ease-out;
  }

  .tab-panel.active {
    opacity: 1;
    transform: translateX(0);
    position: relative;
    pointer-events: auto;
  }

  .tab-panel h3 {
    margin: 0 0 1rem 0;
  }

  .tab-panel p {
    margin: 0;
    color: #6b7280;
  }
</style>

<script>
  document.querySelectorAll(".tab").forEach((tab) => {
    tab.addEventListener("click", () => {
      const targetId = tab.dataset.tab;

      // Update active tab
      document
        .querySelectorAll(".tab")
        .forEach((t) => t.classList.remove("active"));
      tab.classList.add("active");

      // Update active panel
      document.querySelectorAll(".tab-panel").forEach((panel) => {
        panel.classList.remove("active");
      });
      document.getElementById(targetId).classList.add("active");
    });
  });
</script>
```

## 🎨 Personnalisation avancée

### Transition personnalisée avec variables

```html
<div
  class="transition"
  style="--transition-duration: 800ms; 
            --transition-timing: cubic-bezier(0.68, -0.55, 0.265, 1.55);
            padding: 2rem; 
            background: #3b82f6; 
            color: white"
>
  Custom transition (800ms avec spring)
</div>

<style>
  div:hover {
    background: #2563eb;
    transform: scale(1.05);
  }
</style>
```

### Multiples propriétés avec différentes durées

```html
<div class="multi-transition">Multi-property transition</div>

<style>
  .multi-transition {
    padding: 2rem;
    background: #10b981;
    color: white;
    border-radius: 0.5rem;
    transition: background-color 300ms ease-in-out, transform 150ms ease-out,
      box-shadow 300ms ease-in-out;
  }

  .multi-transition:hover {
    background: #059669;
    transform: translateY(-4px);
    box-shadow: 0 12px 24px rgba(0, 0, 0, 0.2);
  }
</style>
```

### Transition avec will-change pour performance

```html
<div class="performant-transition">Transition optimisée</div>

<style>
  .performant-transition {
    padding: 2rem;
    background: #f59e0b;
    color: white;
    border-radius: 0.5rem;
    transition: transform 300ms ease-out;
    will-change: transform;
  }

  .performant-transition:hover {
    transform: translateY(-8px) scale(1.02);
  }
</style>
```

### Transition en chaîne (sequential)

```html
<div class="sequential-container">
  <div class="seq-box" style="--delay: 0ms">1</div>
  <div class="seq-box" style="--delay: 100ms">2</div>
  <div class="seq-box" style="--delay: 200ms">3</div>
  <div class="seq-box" style="--delay: 300ms">4</div>
  <div class="seq-box" style="--delay: 400ms">5</div>
</div>

<style>
  .sequential-container {
    display: flex;
    gap: 1rem;
    padding: 2rem;
  }

  .seq-box {
    width: 60px;
    height: 60px;
    background: #667eea;
    color: white;
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: 700;
    border-radius: 0.5rem;
    transition: transform 300ms ease-out var(--delay);
  }

  .sequential-container:hover .seq-box {
    transform: translateY(-20px);
  }
</style>
```

## 🎯 Cas d'usage courants

### 1. Hover effects sur buttons

```html
<button class="transition-colors-fast">Hover effect</button>
```

### 2. Cards interactives

```html
<div class="card hover-lift">Card with lift effect</div>
```

### 3. Modals / Dialogs

```html
<div class="modal transition-opacity-fast">Modal content</div>
```

### 4. Dropdowns / Menus

```html
<div class="dropdown-menu transition">Menu items</div>
```

### 5. Accordions

```html
<div class="accordion-content transition">Expandable content</div>
```

### 6. Tabs

```html
<div class="tab-panel transition">Tab content</div>
```

### 7. Focus states

```html
<input type="text" class="focus-ring" />
```

## 🔧 Combinaison avec autres utilitaires

### Avec Shadow Wrapper

```html
<div class="shadow-wrapper shadow-wrapper--md transition hover-lift">
  Card avec ombre + lift
</div>
```

### Avec Rounded

```html
<button class="rounded-lg transition-colors-fast">
  Rounded button avec transition
</button>
```

### Avec Gradient Background

```html
<div class="gradient-bg gradient-bg--sunset transition hover-scale">
  Gradient avec scale effect
</div>
```

### Avec Glass Effect

```html
<div class="glass-effect glass-effect--light transition hover-opacity">
  Glass avec opacity transition
</div>
```

## 📱 Comportement responsive

### Respecter prefers-reduced-motion

```scss
// Déjà inclus dans le code de base
@media (prefers-reduced-motion: reduce) {
  .transition {
    transition-duration: 0.01ms !important;
  }
}
```

### Désactiver transitions sur mobile pour performance

```scss
@media (max-width: 640px) {
  .transition-expensive {
    transition: none;
  }
}
```

## ⚡ Performance & Bonnes pratiques

### ✅ À faire

```html
<!-- Bon : Animer transform et opacity (GPU-accelerated) -->
<div class="transition-transform-normal">
  <!-- Bon : Utiliser will-change pour animations complexes -->
  <div style="transition: transform 300ms; will-change: transform">
    <!-- Bon : Transitions courtes pour feedback -->
    <button class="transition-fast">
      <!-- Bon : Propriétés spécifiques -->
      <div class="transition-colors-fast"></div>
    </button>
  </div>
</div>
```

### ❌ À éviter

```html
<!-- Mauvais : Animer width/height (coûteux) -->
<div style="transition: width 300ms">
  <!-- Mauvais : Animer trop de propriétés -->
  <div style="transition: all 1s">
    <!-- Mauvais : Transitions trop lentes -->
    <button style="transition: background 2s">
      <!-- Mauvais : will-change partout -->
      <div style="will-change: transform, opacity, width, height, color"></div>
    </button>
  </div>
</div>
```

### Propriétés GPU-accelerated (rapides)

```css
/* ✅ Bon pour performance */
transform
opacity
filter

/* ❌ Éviter si possible */
width
height
margin
padding
top/left/right/bottom (sans transform)
```

### Conseils de performance

```scss
// ✅ Utiliser transform au lieu de position
// Mauvais
.element {
  transition: left 300ms;
  &:hover {
    left: 100px;
  }
}

// Bon
.element {
  transition: transform 300ms;
  &:hover {
    transform: translateX(100px);
  }
}

// ✅ Limiter will-change
.element {
  &:hover {
    will-change: transform; // Uniquement au hover
    transform: scale(1.1);
  }

  &:not(:hover) {
    will-change: auto; // Retirer après
  }
}
```

## 🌐 Compatibilité navigateurs

| Navigateur | Version minimale | Support    |
| ---------- | ---------------- | ---------- |
| Chrome     | 26+              | ✅ Complet |
| Firefox    | 16+              | ✅ Complet |
| Safari     | 9+               | ✅ Complet |
| Edge       | 12+              | ✅ Complet |
| Opera      | 12.1+            | ✅ Complet |
| IE         | 10+              | ✅ Complet |

**Note** : Les transitions CSS sont très bien supportées. Pas de préfixes nécessaires pour les navigateurs modernes.

## 🐛 Troubleshooting

### Problème : La transition ne s'applique pas

**Solution** : Vérifiez que la propriété est animable

```css
/* ❌ display n'est pas animable */
.element {
  transition: display 300ms;
}

/* ✅ Utilisez opacity à la place */
.element {
  transition: opacity 300ms;
  opacity: 0;
  pointer-events: none;
}

.element.visible {
  opacity: 1;
  pointer-events: auto;
}
```

### Problème : La transition est saccadée

**Solution** : Utilisez transform et will-change

```css
/* ❌ Mauvais */
.element {
  transition: left 300ms;
}

/* ✅ Bon */
.element {
  transition: transform 300ms;
  will-change: transform;
}
```

### Problème : Transition trop brutale

**Solution** : Ajustez la timing function

```css
/* Au lieu de linear */
transition-timing-function: linear;

/* Utilisez ease-in-out */
transition-timing-function: ease-in-out;
```

### Problème : L'élément "flashe" au chargement

**Solution** : Ajoutez une classe après le chargement

```html
<div class="element">Content</div>

<script>
  // Attendre que le DOM soit prêt
  document.addEventListener("DOMContentLoaded", () => {
    document.querySelector(".element").classList.add("transition");
  });
</script>
```

## 📦 Classes complètes disponibles

```scss
// Durées
.transition-instant {
  transition-duration: 75ms;
}
.transition-fast {
  transition-duration: 150ms;
}
.transition-normal {
  transition-duration: 300ms;
}
.transition-slow {
  transition-duration: 500ms;
}
.transition-slower {
  transition-duration: 700ms;
}
.transition-slowest {
  transition-duration: 1000ms;
}

// Timing functions
.transition-linear {
  /* linear */
}
.transition-ease {
  /* ease */
}
.transition-ease-in {
  /* ease-in */
}
.transition-ease-out {
  /* ease-out */
}
.transition-ease-in-out {
  /* ease-in-out */
}
.transition-spring {
  /* spring */
}
.transition-smooth {
  /* smooth */
}

// Propriétés
.transition-none {
  transition: none;
}
.transition-all {
  transition-property: all;
}
.transition-colors {
  /* color, bg, border */
}
.transition-opacity {
  /* opacity */
}
.transition-shadow {
  /* box-shadow */
}
.transition-transform {
  /* transform */
}

// Presets
.transition-colors-fast {
  /* 150ms colors */
}
.transition-transform-normal {
  /* 300ms transform */
}
.transition-opacity-fast {
  /* 150ms opacity */
}
.transition-all-normal {
  /* 300ms all */
}

// Hover effects
.hover-lift {
  /* Lift + shadow */
}
.hover-scale {
  /* Scale 1.05 */
}
.hover-scale-sm {
  /* Scale 1.02 */
}
.hover-rotate {
  /* Rotate 5deg */
}
.hover-brighten {
  /* Brighten */
}
.hover-blur {
  /* Blur */
}
.hover-opacity {
  /* Opacity 0.7 */
}

// Focus
.focus-ring {
  /* Focus ring */
}

// Delays
.transition-delay-75 {
  transition-delay: 75ms;
}
.transition-delay-100 {
  transition-delay: 100ms;
}
.transition-delay-150 {
  transition-delay: 150ms;
}
.transition-delay-200 {
  transition-delay: 200ms;
}
.transition-delay-300 {
  transition-delay: 300ms;
}
.transition-delay-500 {
  transition-delay: 500ms;
}
.transition-delay-700 {
  transition-delay: 700ms;
}
.transition-delay-1000 {
  transition-delay: 1000ms;
}
```

## 🎓 Ressources complémentaires

- [CSS Transitions - MDN](https://developer.mozilla.org/fr/docs/Web/CSS/CSS_Transitions)
- [Transition Property - MDN](https://developer.mozilla.org/fr/docs/Web/CSS/transition)
- [Cubic Bezier Generator](https://cubic-bezier.com/)
- [Easing Functions Cheat Sheet](https://easings.net/)

## 📝 Changelog

- **v1.0** - Version initiale avec durées et timing functions
- **v1.1** - Ajout des presets (colors, transform, opacity)
- **v1.2** - Ajout des hover effects prédéfinis
- **v1.3** - Support des delays
- **v1.4** - Support de prefers-reduced-motion
- **v1.5** - Ajout du focus-ring

---

**Made with ❤️ for smooth interactions**
