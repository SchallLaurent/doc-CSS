# Card Utility

> Système de cartes flexible et moderne pour créer des conteneurs de contenu élégants et cohérents

## 📋 Description

**Card** est un utilitaire CSS qui fournit un système complet de cartes (cards) pour organiser et présenter le contenu. Les cartes sont des conteneurs visuels qui regroupent des informations connexes et offrent une hiérarchie visuelle claire.

### ✨ Caractéristiques principales

- 🎴 **Card de base** : Container avec padding et background
- 🎨 **Variantes** : Bordered, elevated, flat, outline
- 📐 **Layouts** : Vertical, horizontal, stacked
- 🧩 **Composants** : Header, body, footer, image, actions
- 🎯 **États** : Hover, active, disabled, loading
- 📏 **Tailles** : sm, md, lg, xl
- 🔧 **Variables CSS** : Personnalisation complète
- ♿ **Accessibilité** : Structure sémantique

## 🚀 Installation

### Code SCSS

```scss
// _card.scss

// Variables globales
:root {
  --card-bg: #ffffff;
  --card-padding: 1.5rem;
  --card-radius: 0.75rem;
  --card-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
  --card-border-color: #e5e7eb;
  --card-border-width: 1px;
}

// ============================================
// BASE CARD
// ============================================

.card {
  background: var(--card-bg, #ffffff);
  border-radius: var(--card-radius, 0.75rem);
  padding: var(--card-padding, 1.5rem);
  position: relative;
  overflow: hidden;
}

// ============================================
// VARIANTES
// ============================================

// Card avec ombre (défaut)
.card--elevated {
  box-shadow: var(--card-shadow, 0 1px 3px rgba(0, 0, 0, 0.1));
}

// Card avec bordure
.card--bordered {
  border: var(--card-border-width, 1px) solid var(--card-border-color, #e5e7eb);
}

// Card plate (sans ombre ni bordure)
.card--flat {
  box-shadow: none;
  border: none;
}

// Card outline uniquement
.card--outline {
  background: transparent;
  border: 2px solid var(--card-border-color, #e5e7eb);
}

// Card avec dégradé
.card--gradient {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
}

// ============================================
// TAILLES
// ============================================

.card--sm {
  padding: 1rem;
  border-radius: 0.5rem;
}

.card--md {
  padding: 1.5rem;
  border-radius: 0.75rem;
}

.card--lg {
  padding: 2rem;
  border-radius: 1rem;
}

.card--xl {
  padding: 2.5rem;
  border-radius: 1.25rem;
}

// Padding nul (pour images edge-to-edge)
.card--no-padding {
  padding: 0;
}

// ============================================
// COMPOSANTS
// ============================================

// Card Header
.card__header {
  margin: calc(-1 * var(--card-padding, 1.5rem));
  margin-bottom: var(--card-padding, 1.5rem);
  padding: var(--card-padding, 1.5rem);
  border-bottom: 1px solid var(--card-border-color, #e5e7eb);
}

// Card Body
.card__body {
  // Le contenu principal
  line-height: 1.6;
}

// Card Footer
.card__footer {
  margin: calc(-1 * var(--card-padding, 1.5rem));
  margin-top: var(--card-padding, 1.5rem);
  padding: var(--card-padding, 1.5rem);
  border-top: 1px solid var(--card-border-color, #e5e7eb);
  background: #f9fafb;
}

// Card Image
.card__image {
  margin: calc(-1 * var(--card-padding, 1.5rem));
  margin-bottom: var(--card-padding, 1.5rem);
  width: calc(100% + 2 * var(--card-padding, 1.5rem));

  img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    display: block;
  }
}

// Card Image en footer
.card__image--footer {
  margin: calc(-1 * var(--card-padding, 1.5rem));
  margin-top: var(--card-padding, 1.5rem);
  width: calc(100% + 2 * var(--card-padding, 1.5rem));
}

// Card Title
.card__title {
  margin: 0 0 0.75rem 0;
  font-size: 1.5rem;
  font-weight: 700;
  color: #111827;
  line-height: 1.3;
}

// Card Subtitle
.card__subtitle {
  margin: -0.5rem 0 1rem 0;
  font-size: 0.875rem;
  color: #6b7280;
}

// Card Description
.card__description {
  margin: 0 0 1rem 0;
  color: #374151;
  line-height: 1.6;
}

// Card Actions
.card__actions {
  display: flex;
  gap: 0.75rem;
  margin-top: 1.5rem;
}

.card__actions--centered {
  justify-content: center;
}

.card__actions--end {
  justify-content: flex-end;
}

// ============================================
// LAYOUTS
// ============================================

// Card horizontal
.card--horizontal {
  display: flex;
  flex-direction: row;
  padding: 0;

  .card__image {
    margin: 0;
    width: 40%;
    min-height: 100%;

    img {
      height: 100%;
    }
  }

  .card__content {
    flex: 1;
    padding: var(--card-padding, 1.5rem);
  }
}

// Card avec image de fond
.card--bg-image {
  background-size: cover;
  background-position: center;
  color: white;
  position: relative;

  &::before {
    content: "";
    position: absolute;
    inset: 0;
    background: linear-gradient(
      to bottom,
      rgba(0, 0, 0, 0.3),
      rgba(0, 0, 0, 0.7)
    );
    z-index: 0;
  }

  > * {
    position: relative;
    z-index: 1;
  }
}

// ============================================
// ÉTATS
// ============================================

// Card interactive (cliquable)
.card--interactive {
  cursor: pointer;
  transition: all 300ms ease-in-out;

  &:hover {
    transform: translateY(-4px);
    box-shadow: 0 12px 24px rgba(0, 0, 0, 0.15);
  }
}

// Card active
.card--active {
  border-color: #3b82f6;
  box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.1);
}

// Card disabled
.card--disabled {
  opacity: 0.6;
  pointer-events: none;
  cursor: not-allowed;
}

// Card loading
.card--loading {
  position: relative;
  pointer-events: none;

  &::after {
    content: "";
    position: absolute;
    inset: 0;
    background: rgba(255, 255, 255, 0.8);
    display: flex;
    align-items: center;
    justify-content: center;
  }
}

// ============================================
// STYLES SPÉCIAUX
// ============================================

// Feature card (pour landing pages)
.card--feature {
  text-align: center;
  padding: 2.5rem 2rem;

  .card__icon {
    font-size: 3rem;
    margin-bottom: 1.5rem;
  }

  .card__title {
    font-size: 1.5rem;
    margin-bottom: 1rem;
  }
}

// Pricing card
.card--pricing {
  text-align: center;
  padding: 2.5rem 2rem;
  position: relative;

  .card__badge {
    position: absolute;
    top: -12px;
    left: 50%;
    transform: translateX(-50%);
    padding: 0.5rem 1.5rem;
    background: #3b82f6;
    color: white;
    border-radius: 9999px;
    font-size: 0.875rem;
    font-weight: 600;
  }

  .card__price {
    display: flex;
    align-items: baseline;
    justify-content: center;
    gap: 0.5rem;
    margin: 1.5rem 0;

    .price-amount {
      font-size: 3.5rem;
      font-weight: 800;
      line-height: 1;
    }

    .price-period {
      font-size: 1.25rem;
      color: #6b7280;
    }
  }
}

// Profile card
.card--profile {
  text-align: center;

  .card__avatar {
    width: 100px;
    height: 100px;
    border-radius: 50%;
    margin: 0 auto 1.5rem;
    border: 4px solid white;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  }
}

// Testimonial card
.card--testimonial {
  position: relative;
  padding-top: 2.5rem;

  .card__quote {
    position: absolute;
    top: 1rem;
    left: 1.5rem;
    font-size: 4rem;
    color: #e5e7eb;
    line-height: 1;
  }

  .card__text {
    font-size: 1.125rem;
    font-style: italic;
    color: #374151;
    margin-bottom: 1.5rem;
    line-height: 1.7;
  }

  .card__author {
    display: flex;
    align-items: center;
    gap: 1rem;

    .author-avatar {
      width: 48px;
      height: 48px;
      border-radius: 50%;
    }

    .author-info {
      text-align: left;

      .author-name {
        font-weight: 600;
        color: #111827;
        display: block;
      }

      .author-role {
        font-size: 0.875rem;
        color: #6b7280;
      }
    }
  }
}

// Stats card
.card--stats {
  text-align: center;

  .card__stat-icon {
    font-size: 2.5rem;
    margin-bottom: 1rem;
  }

  .card__stat-value {
    font-size: 3rem;
    font-weight: 800;
    color: #111827;
    margin: 0;
    line-height: 1;
  }

  .card__stat-label {
    font-size: 0.875rem;
    color: #6b7280;
    text-transform: uppercase;
    letter-spacing: 0.05em;
    margin-top: 0.5rem;
  }

  .card__stat-change {
    font-size: 0.875rem;
    font-weight: 600;
    margin-top: 0.75rem;

    &.positive {
      color: #059669;
    }

    &.negative {
      color: #dc2626;
    }
  }
}

// ============================================
// CARD AVEC MEDIA OBJECT
// ============================================

.card--media {
  display: flex;
  gap: 1.5rem;

  .card__media-image {
    width: 120px;
    height: 120px;
    flex-shrink: 0;
    border-radius: 0.5rem;
    overflow: hidden;

    img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }
  }

  .card__media-content {
    flex: 1;
    min-width: 0;
  }
}

// ============================================
// RESPONSIVE
// ============================================

@media (max-width: 767px) {
  .card--horizontal {
    flex-direction: column;

    .card__image {
      width: 100%;
      height: 200px;
    }
  }

  .card--media {
    flex-direction: column;

    .card__media-image {
      width: 100%;
      height: 200px;
    }
  }
}

// ============================================
// GLASS CARD (glassmorphism)
// ============================================

.card--glass {
  background: rgba(255, 255, 255, 0.7);
  backdrop-filter: blur(10px) saturate(180%);
  border: 1px solid rgba(255, 255, 255, 0.18);
}

// ============================================
// GRID DE CARDS
// ============================================

.card-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 2rem;
}

.card-grid--2 {
  grid-template-columns: repeat(auto-fit, minmax(400px, 1fr));
}

.card-grid--3 {
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
}

.card-grid--4 {
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
}

@media (max-width: 767px) {
  .card-grid,
  .card-grid--2,
  .card-grid--3,
  .card-grid--4 {
    grid-template-columns: 1fr;
  }
}
```

### Import dans votre projet

```scss
// Dans styles.scss
@import "utilities/card";
```

## 💡 Utilisation de base

### Exemple 1 : Card simple

```html
<div class="card card--elevated">
  <h3 class="card__title">Card Title</h3>
  <p class="card__description">
    This is a simple card with title and description.
  </p>
  <div class="card__actions">
    <button class="btn rounded-lg">Action</button>
  </div>
</div>
```

### Exemple 2 : Card avec image

```html
<div class="card card--elevated card--no-padding">
  <div class="card__image">
    <img src="image.jpg" alt="Card image" />
  </div>
  <div style="padding: 1.5rem;">
    <h3 class="card__title">Beautiful Landscape</h3>
    <p class="card__description">
      Discover the most beautiful places in the world.
    </p>
  </div>
</div>
```

### Exemple 3 : Card avec header et footer

```html
<div class="card card--bordered">
  <div class="card__header">
    <h3 class="card__title">Header Title</h3>
    <p class="card__subtitle">Subtitle here</p>
  </div>

  <div class="card__body">
    <p>Main content goes here...</p>
  </div>

  <div class="card__footer">
    <div class="card__actions card__actions--end">
      <button class="btn-secondary rounded-lg">Cancel</button>
      <button class="btn-primary rounded-lg">Submit</button>
    </div>
  </div>
</div>
```

### Exemple 4 : Card interactive

```html
<div class="card card--elevated card--interactive">
  <h3 class="card__title">Clickable Card</h3>
  <p class="card__description">Hover to see the effect.</p>
</div>
```

## 📊 Paramètres

| Variable              | Type   | Défaut                      | Description        |
| --------------------- | ------ | --------------------------- | ------------------ |
| `--card-bg`           | color  | `#ffffff`                   | Couleur de fond    |
| `--card-padding`      | length | `1.5rem`                    | Padding interne    |
| `--card-radius`       | length | `0.75rem`                   | Border radius      |
| `--card-shadow`       | shadow | `0 1px 3px rgba(0,0,0,0.1)` | Box shadow         |
| `--card-border-color` | color  | `#e5e7eb`                   | Couleur de bordure |
| `--card-border-width` | length | `1px`                       | Épaisseur bordure  |

### Variantes disponibles

| Catégorie    | Classes                                                        | Description    |
| ------------ | -------------------------------------------------------------- | -------------- |
| **Style**    | card--elevated, card--bordered, card--flat, card--outline      | Styles visuels |
| **Taille**   | card--sm, card--md, card--lg, card--xl                         | Padding        |
| **Layout**   | card--horizontal, card--bg-image, card--media                  | Disposition    |
| **État**     | card--interactive, card--active, card--disabled                | Interactivité  |
| **Spéciaux** | card--feature, card--pricing, card--profile, card--testimonial | Préfabriqués   |

## 📚 Exemples détaillés

### Exemple 1 : Blog post cards

```html
<div class="card-grid">
  <!-- Card 1 -->
  <div
    class="card card--elevated card--no-padding card--interactive rounded-xl"
  >
    <div class="card__image">
      <img src="blog1.jpg" alt="Blog post 1" />
    </div>
    <div style="padding: 1.5rem;">
      <div class="stack stack--xs">
        <div class="stack stack--horizontal stack--xs">
          <span class="badge rounded-full">Design</span>
          <span class="text-muted">• 5 min read</span>
        </div>

        <h3 class="card__title">The Future of Web Design</h3>

        <p class="card__description">
          Exploring the latest trends in web design and how they shape the user
          experience of tomorrow.
        </p>

        <div class="card__author stack stack--horizontal stack--sm">
          <img src="author1.jpg" alt="Author" class="avatar-sm rounded-full" />
          <div class="stack stack--xs">
            <span class="author-name">Marie Dupont</span>
            <span class="author-date">15 Nov 2024</span>
          </div>
        </div>
      </div>
    </div>
  </div>

  <!-- Card 2 -->
  <div
    class="card card--elevated card--no-padding card--interactive rounded-xl"
  >
    <div class="card__image">
      <img src="blog2.jpg" alt="Blog post 2" />
    </div>
    <div style="padding: 1.5rem;">
      <div class="stack stack--xs">
        <div class="stack stack--horizontal stack--xs">
          <span class="badge rounded-full">Development</span>
          <span class="text-muted">• 8 min read</span>
        </div>

        <h3 class="card__title">Building Modern APIs</h3>

        <p class="card__description">
          A comprehensive guide to creating scalable and secure RESTful APIs for
          modern applications.
        </p>

        <div class="card__author stack stack--horizontal stack--sm">
          <img src="author2.jpg" alt="Author" class="avatar-sm rounded-full" />
          <div class="stack stack--xs">
            <span class="author-name">Jean Martin</span>
            <span class="author-date">12 Nov 2024</span>
          </div>
        </div>
      </div>
    </div>
  </div>

  <!-- Card 3 -->
  <div
    class="card card--elevated card--no-padding card--interactive rounded-xl"
  >
    <div class="card__image">
      <img src="blog3.jpg" alt="Blog post 3" />
    </div>
    <div style="padding: 1.5rem;">
      <div class="stack stack--xs">
        <div class="stack stack--horizontal stack--xs">
          <span class="badge rounded-full">Business</span>
          <span class="text-muted">• 6 min read</span>
        </div>

        <h3 class="card__title">Startup Success Stories</h3>

        <p class="card__description">
          Learn from successful entrepreneurs who built billion-dollar companies
          from scratch.
        </p>

        <div class="card__author stack stack--horizontal stack--sm">
          <img src="author3.jpg" alt="Author" class="avatar-sm rounded-full" />
          <div class="stack stack--xs">
            <span class="author-name">Sophie Leroux</span>
            <span class="author-date">10 Nov 2024</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>

<style>
  .badge {
    padding: 0.25rem 0.75rem;
    background: #eff6ff;
    color: #3b82f6;
    font-size: 0.75rem;
    font-weight: 600;
  }

  .text-muted {
    color: #9ca3af;
    font-size: 0.875rem;
  }

  .avatar-sm {
    width: 40px;
    height: 40px;
    object-fit: cover;
  }

  .author-name {
    font-weight: 600;
    font-size: 0.875rem;
    color: #111827;
  }

  .author-date {
    font-size: 0.75rem;
    color: #6b7280;
  }
</style>
```

### Exemple 2 : Pricing cards

```html
<div class="pricing-container">
  <div class="stack stack--horizontal stack--lg stack--horizontal-tablet">
    <!-- Starter Plan -->
    <div
      class="card card--pricing card--elevated rounded-2xl shadow-wrapper shadow-wrapper--lg"
    >
      <div class="stack stack--lg">
        <div class="stack stack--sm">
          <h3 class="card__title">Starter</h3>
          <p class="text-muted">Perfect for small projects</p>
        </div>

        <div class="card__price">
          <span class="price-amount">$9</span>
          <span class="price-period">/month</span>
        </div>

        <button class="btn-outline rounded-lg">Choose Starter</button>

        <div class="stack stack--divider stack--sm">
          <div class="feature">✓ 5 projects</div>
          <div class="feature">✓ 10 GB storage</div>
          <div class="feature">✓ Email support</div>
          <div class="feature">✓ Basic analytics</div>
        </div>
      </div>
    </div>

    <!-- Pro Plan (Featured) -->
    <div
      class="card card--pricing card--elevated rounded-2xl shadow-wrapper shadow-wrapper--xl"
      style="border: 2px solid #3b82f6; transform: scale(1.05);"
    >
      <div class="card__badge">⭐ Most Popular</div>

      <div class="stack stack--lg">
        <div class="stack stack--sm">
          <h3 class="card__title">Pro</h3>
          <p class="text-muted">For growing businesses</p>
        </div>

        <div class="card__price">
          <span class="price-amount">$29</span>
          <span class="price-period">/month</span>
        </div>

        <button class="btn-primary rounded-lg">Choose Pro</button>

        <div class="stack stack--divider stack--sm">
          <div class="feature">✓ Unlimited projects</div>
          <div class="feature">✓ 100 GB storage</div>
          <div class="feature">✓ Priority support 24/7</div>
          <div class="feature">✓ Advanced analytics</div>
          <div class="feature">✓ Team collaboration</div>
          <div class="feature">✓ Custom integrations</div>
        </div>
      </div>
    </div>

    <!-- Enterprise Plan -->
    <div
      class="card card--pricing card--elevated rounded-2xl shadow-wrapper shadow-wrapper--lg"
    >
      <div class="stack stack--lg">
        <div class="stack stack--sm">
          <h3 class="card__title">Enterprise</h3>
          <p class="text-muted">For large organizations</p>
        </div>

        <div class="card__price">
          <span class="price-amount">$99</span>
          <span class="price-period">/month</span>
        </div>

        <button class="btn-outline rounded-lg">Contact Sales</button>

        <div class="stack stack--divider stack--sm">
          <div class="feature">✓ Everything in Pro</div>
          <div class="feature">✓ Unlimited storage</div>
          <div class="feature">✓ Dedicated support</div>
          <div class="feature">✓ SLA guarantee</div>
          <div class="feature">✓ Custom training</div>
          <div class="feature">✓ API access</div>
        </div>
      </div>
    </div>
  </div>
</div>

<style>
  .pricing-container {
    padding: 5rem 2rem;
    max-width: 1200px;
    margin: 0 auto;
  }

  .feature {
    color: #374151;
    font-size: 0.875rem;
  }

  .btn-outline,
  .btn-primary {
    width: 100%;
    padding: 1rem;
    border: none;
    cursor: pointer;
    font-weight: 600;
    transition: all 200ms;
  }

  .btn-outline {
    background: transparent;
    border: 2px solid #e5e7eb;
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

### Exemple 3 : Profile cards

```html
<div class="card-grid card-grid--3">
  <!-- Profile 1 -->
  <div class="card card--profile card--elevated rounded-2xl">
    <div class="stack stack--center stack--lg">
      <img src="profile1.jpg" alt="Profile 1" class="card__avatar" />

      <div class="stack stack--center stack--xs">
        <h3 class="card__title">Marie Dupont</h3>
        <p class="card__subtitle">CEO & Founder</p>
      </div>

      <p class="card__description" style="text-align: center;">
        Digital strategy expert with 15 years of experience in building
        successful startups.
      </p>

      <div class="stack stack--horizontal stack--sm">
        <a href="#" class="social-icon rounded-full">💼</a>
        <a href="#" class="social-icon rounded-full">🐦</a>
        <a href="#" class="social-icon rounded-full">📧</a>
      </div>

      <button class="btn-primary rounded-lg" style="width: 100%;">
        Follow
      </button>
    </div>
  </div>

  <!-- Profile 2 -->
  <div class="card card--profile card--elevated rounded-2xl">
    <div class="stack stack--center stack--lg">
      <img src="profile2.jpg" alt="Profile 2" class="card__avatar" />

      <div class="stack stack--center stack--xs">
        <h3 class="card__title">Jean Martin</h3>
        <p class="card__subtitle">CTO</p>
      </div>

      <p class="card__description" style="text-align: center;">
        Software architect passionate about building scalable and secure
        distributed systems.
      </p>

      <div class="stack stack--horizontal stack--sm">
        <a href="#" class="social-icon rounded-full">💼</a>
        <a href="#" class="social-icon rounded-full">🐦</a>
        <a href="#" class="social-icon rounded-full">📧</a>
      </div>

      <button class="btn-primary rounded-lg" style="width: 100%;">
        Follow
      </button>
    </div>
  </div>

  <!-- Profile 3 -->
  <div class="card card--profile card--elevated rounded-2xl">
    <div class="stack stack--center stack--lg">
      <img src="profile3.jpg" alt="Profile 3" class="card__avatar" />

      <div class="stack stack--center stack--xs">
        <h3 class="card__title">Sophie Leroux</h3>
        <p class="card__subtitle">Lead Designer</p>
      </div>

      <p class="card__description" style="text-align: center;">
        Creative UI/UX designer crafting beautiful and intuitive digital
        experiences.
      </p>

      <div class="stack stack--horizontal stack--sm">
        <a href="#" class="social-icon rounded-full">💼</a>
        <a href="#" class="social-icon rounded-full">🐦</a>
        <a href="#" class="social-icon rounded-full">📧</a>
      </div>

      <button class="btn-primary rounded-lg" style="width: 100%;">
        Follow
      </button>
    </div>
  </div>
</div>

<style>
  .social-icon {
    width: 40px;
    height: 40px;
    display: flex;
    align-items: center;
    justify-content: center;
    background: #f3f4f6;
    text-decoration: none;
    font-size: 1.25rem;
    transition: all 200ms;
  }

  .social-icon:hover {
    background: #e5e7eb;
    transform: translateY(-2px);
  }
</style>
```

### Exemple 4 : Feature cards

```html
<div class="features-section">
  <div class="container">
    <div class="stack stack--center stack--2xl">
      <div class="section-header stack stack--center stack--sm">
        <h2>Why Choose Us</h2>
        <p class="text-muted">Everything you need to succeed</p>
      </div>

      <div class="card-grid card-grid--3">
        <!-- Feature 1 -->
        <div class="card card--feature card--elevated rounded-xl hover-lift">
          <div class="stack stack--lg">
            <div class="card__icon">⚡</div>
            <h3 class="card__title">Lightning Fast</h3>
            <p class="card__description">
              Optimized performance with blazing fast load times and smooth
              interactions.
            </p>
          </div>
        </div>

        <!-- Feature 2 -->
        <div class="card card--feature card--elevated rounded-xl hover-lift">
          <div class="stack stack--lg">
            <div class="card__icon">🔒</div>
            <h3 class="card__title">Secure by Default</h3>
            <p class="card__description">
              Enterprise-grade security with encryption, compliance, and data
              protection.
            </p>
          </div>
        </div>

        <!-- Feature 3 -->
        <div class="card card--feature card--elevated rounded-xl hover-lift">
          <div class="stack stack--lg">
            <div class="card__icon">🎨</div>
            <h3 class="card__title">Beautiful Design</h3>
            <p class="card__description">
              Stunning interfaces crafted with attention to detail and user
              experience.
            </p>
          </div>
        </div>

        <!-- Feature 4 -->
        <div class="card card--feature card--elevated rounded-xl hover-lift">
          <div class="stack stack--lg">
            <div class="card__icon">📱</div>
            <h3 class="card__title">Mobile Responsive</h3>
            <p class="card__description">
              Perfect experience across all devices, from mobile to desktop.
            </p>
          </div>
        </div>

        <!-- Feature 5 -->
        <div class="card card--feature card--elevated rounded-xl hover-lift">
          <div class="stack stack--lg">
            <div class="card__icon">🚀</div>
            <h3 class="card__title">Easy to Deploy</h3>
            <p class="card__description">
              One-click deployment with automated CI/CD pipelines and rollbacks.
            </p>
          </div>
        </div>

        <!-- Feature 6 -->
        <div class="card card--feature card--elevated rounded-xl hover-lift">
          <div class="stack stack--lg">
            <div class="card__icon">💬</div>
            <h3 class="card__title">24/7 Support</h3>
            <p class="card__description">
              Round-the-clock support from our dedicated team of experts.
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>

<style>
  .features-section {
    padding: 5rem 2rem;
    background: linear-gradient(to bottom, #f9fafb, white);
  }

  .section-header {
    text-align: center;
  }

  .section-header h2 {
    font-size: 3rem;
    margin: 0;
  }
</style>
```

### Exemple 5 : Testimonial cards

```html
<div class="testimonials-section">
  <div class="container">
    <div class="stack stack--center stack--2xl">
      <h2>What Our Clients Say</h2>

      <div class="card-grid card-grid--2">
        <!-- Testimonial 1 -->
        <div class="card card--testimonial card--elevated rounded-xl">
          <div class="card__quote">"</div>

          <p class="card__text">
            This product has completely transformed how we work. The team is
            more productive and our clients are happier than ever before.
          </p>

          <div class="card__author">
            <img src="client1.jpg" alt="Client 1" class="author-avatar" />
            <div class="author-info">
              <span class="author-name">Sarah Johnson</span>
              <span class="author-role">CEO, TechCorp</span>
            </div>
          </div>
        </div>

        <!-- Testimonial 2 -->
        <div class="card card--testimonial card--elevated rounded-xl">
          <div class="card__quote">"</div>

          <p class="card__text">
            Outstanding service and support. The implementation was smooth and
            the results exceeded our expectations. Highly recommended!
          </p>

          <div class="card__author">
            <img src="client2.jpg" alt="Client 2" class="author-avatar" />
            <div class="author-info">
              <span class="author-name">Michael Chen</span>
              <span class="author-role">CTO, StartupXYZ</span>
            </div>
          </div>
        </div>

        <!-- Testimonial 3 -->
        <div class="card card--testimonial card--elevated rounded-xl">
          <div class="card__quote">"</div>

          <p class="card__text">
            The best investment we've made this year. ROI was visible within the
            first month. Can't imagine working without it now.
          </p>

          <div class="card__author">
            <img src="client3.jpg" alt="Client 3" class="author-avatar" />
            <div class="author-info">
              <span class="author-name">Emma Wilson</span>
              <span class="author-role">Director, Agency Inc</span>
            </div>
          </div>
        </div>

        <!-- Testimonial 4 -->
        <div class="card card--testimonial card--elevated rounded-xl">
          <div class="card__quote">"</div>

          <p class="card__text">
            Incredible attention to detail and customer service. They really
            care about their customers' success and it shows in every
            interaction.
          </p>

          <div class="card__author">
            <img src="client4.jpg" alt="Client 4" class="author-avatar" />
            <div class="author-info">
              <span class="author-name">David Brown</span>
              <span class="author-role">Founder, Digital Co</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>

<style>
  .testimonials-section {
    padding: 5rem 2rem;
  }

  .testimonials-section h2 {
    font-size: 2.5rem;
    text-align: center;
  }
</style>
```

### Exemple 6 : Dashboard stats cards

```html
<div class="stats-dashboard">
  <div class="card-grid card-grid--4">
    <!-- Stat 1 -->
    <div class="card card--stats card--elevated rounded-xl hover-lift">
      <div class="card__stat-icon">👥</div>
      <p class="card__stat-value">12,345</p>
      <p class="card__stat-label">Total Users</p>
      <p class="card__stat-change positive">+12% this month</p>
    </div>

    <!-- Stat 2 -->
    <div class="card card--stats card--elevated rounded-xl hover-lift">
      <div class="card__stat-icon">💰</div>
      <p class="card__stat-value">$456K</p>
      <p class="card__stat-label">Revenue</p>
      <p class="card__stat-change positive">+23% this month</p>
    </div>

    <!-- Stat 3 -->
    <div class="card card--stats card--elevated rounded-xl hover-lift">
      <div class="card__stat-icon">📦</div>
      <p class="card__stat-value">8,901</p>
      <p class="card__stat-label">Orders</p>
      <p class="card__stat-change negative">-5% this month</p>
    </div>

    <!-- Stat 4 -->
    <div class="card card--stats card--elevated rounded-xl hover-lift">
      <div class="card__stat-icon">⭐</div>
      <p class="card__stat-value">4.8/5</p>
      <p class="card__stat-label">Satisfaction</p>
      <p class="card__stat-change positive">+0.3 this month</p>
    </div>
  </div>
</div>

<style>
  .stats-dashboard {
    padding: 2rem;
  }
</style>
```

## 🎨 Personnalisation avancée

### Card avec couleurs custom

```html
<div
  class="card card--elevated"
  style="--card-bg: #eff6ff; 
            --card-border-color: #3b82f6"
>
  Card avec fond bleu clair
</div>
```

### Card avec padding custom

```html
<div class="card" style="--card-padding: 3rem">
  Card avec padding extra-large
</div>
```

### Card avec ombre custom

```html
<div
  class="card card--elevated"
  style="--card-shadow: 0 20px 40px rgba(0,0,0,0.2)"
>
  Card avec grande ombre
</div>
```

## 🎯 Cas d'usage courants

### 1. Blog posts

```html
<div class="card card--elevated card--no-padding">
  <div class="card__image">...</div>
  <div style="padding: 1.5rem;">...</div>
</div>
```

### 2. Pricing plans

```html
<div class="card card--pricing card--elevated">
  <div class="card__badge">Popular</div>
  ...
</div>
```

### 3. Team members

```html
<div class="card card--profile card--elevated">
  <img class="card__avatar" src="..." />
  ...
</div>
```

### 4. Features

```html
<div class="card card--feature card--elevated">
  <div class="card__icon">⚡</div>
  ...
</div>
```

### 5. Testimonials

```html
<div class="card card--testimonial card--elevated">
  <div class="card__quote">"</div>
  ...
</div>
```

## 🔧 Combinaison avec autres utilitaires

### Avec Rounded

```html
<div class="card card--elevated rounded-2xl">Card très arrondie</div>
```

### Avec Shadow Wrapper

```html
<div class="card shadow-wrapper shadow-wrapper--xl">Card avec grande ombre</div>
```

### Avec Hover Effects

```html
<div class="card card--elevated hover-lift">Card avec effet hover</div>
```

### Avec Stack

```html
<div class="card card--elevated">
  <div class="stack stack--lg">
    <h3>Title</h3>
    <p>Content</p>
    <button>CTA</button>
  </div>
</div>
```

## 📱 Comportement responsive

### Card horizontal → vertical sur mobile

```html
<div class="card card--horizontal card--elevated">
  <!-- Devient vertical automatiquement sur mobile -->
</div>
```

### Grid adaptatif

```html
<div class="card-grid card-grid--3">
  <!-- 3 colonnes desktop, 1 colonne mobile -->
</div>
```

## ⚡ Performance & Bonnes pratiques

### ✅ À faire

```html
<!-- Bon : Structure sémantique -->
<article class="card card--elevated">
  <!-- Bon : Images optimisées -->
  <div class="card__image">
    <img src="image-optimized.jpg" loading="lazy" />
  </div>

  <!-- Bon : Contenu accessible -->
  <div class="card" role="article" aria-label="Blog post"></div>
</article>
```

### ❌ À éviter

```html
<!-- Mauvais : Trop de nesting -->
<div class="card">
  <div class="card">
    <div class="card">
      <!-- Mauvais : Images non optimisées -->
      <img src="huge-image-10mb.jpg" />

      <!-- Mauvais : Contenu trop long -->
      <div class="card">
        <p>Very very very long text...</p>
      </div>
    </div>
  </div>
</div>
```

### Optimisations

```scss
// ✅ Utiliser will-change pour animations
.card--interactive {
  will-change: transform, box-shadow;
}

// ✅ Lazy loading pour images
<img loading="lazy" src="...">

// ✅ Aspect ratio pour éviter layout shift
.card__image {
  aspect-ratio: 16 / 9;
}
```

## 🌐 Compatibilité navigateurs

| Navigateur | Version minimale | Support    |
| ---------- | ---------------- | ---------- |
| Chrome     | 88+              | ✅ Complet |
| Firefox    | 87+              | ✅ Complet |
| Safari     | 14+              | ✅ Complet |
| Edge       | 88+              | ✅ Complet |

**Note** : Aspect-ratio nécessite des versions récentes.

## 🐛 Troubleshooting

### Problème : Image déborde

**Solution** : Utilisez card--no-padding

```html
<div class="card card--no-padding">
  <div class="card__image">
    <img src="..." />
  </div>
</div>
```

### Problème : Header/Footer mal alignés

**Solution** : Utilisez les marges négatives

```scss
.card__header {
  margin: calc(-1 * var(--card-padding));
  margin-bottom: var(--card-padding);
}
```

### Problème : Card trop étroite

**Solution** : Définissez min-width

```css
.card {
  min-width: 300px;
}
```

## 📦 Classes complètes disponibles

```scss
// Base
.card                     { /* Card de base */ }

// Variantes
.card--elevated           { /* Avec ombre */ }
.card--bordered           { /* Avec bordure */ }
.card--flat               { /* Sans ombre */ }
.card--outline            { /* Outline */ }
.card--gradient           { /* Dégradé */ }
.card--glass              { /* Glassmorphism */ }

// Tailles
.card--sm, .card--md, .card--lg, .card--xl

// Layouts
.card--horizontal         { /* Layout horizontal */ }
.card--bg-image           { /* Image de fond */ }
.card--media              { /* Media object */ }

// États
.card--interactive        { /* Hover lift */ }
.card--active             { /* État actif */ }
.card--disabled           { /* Désactivée */ }
.card--loading            { /* En chargement */ }

// Spéciaux
.card--feature            { /* Feature card */ }
.card--pricing            { /* Pricing card */ }
.card--profile            { /* Profile card */ }
.card--testimonial        { /* Testimonial */ }
.card--stats              { /* Stats card */ }

// Composants
.card__header, .card__body, .card__footer
.card__image, .card__title, .card__subtitle
.card__description, .card__actions

// Grid
.card-grid                { /* Grid auto */ }
.card-grid--2, .card-grid--3, .card-grid--4
```

## 🎓 Ressources complémentaires

- [Cards - Material Design](https://material.io/components/cards)
- [Card Component - Bootstrap](https://getbootstrap.com/docs/5.0/components/card/)
- [Every Layout - Card](https://every-layout.dev/)

## 📝 Changelog

- **v1.0** - Version initiale avec card de base
- **v1.1** - Ajout des variantes (elevated, bordered)
- **v1.2** - Composants (header, body, footer)
- **v1.3** - Layouts (horizontal, media)
- **v1.4** - Cards spéciaux (pricing, profile, testimonial)
- **v1.5** - États interactifs et grid

---

**Made with ❤️ for beautiful interfaces**
