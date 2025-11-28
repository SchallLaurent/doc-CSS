# Hover Effects Utility

> Collection d'effets hover modernes et élégants pour des interactions utilisateur fluides et engageantes

## 📋 Description

**Hover Effects** est un utilitaire CSS qui fournit une collection complète d'effets au survol (hover) pour rendre vos interfaces plus interactives et engageantes. De l'effet "lift" classique aux transformations plus créatives, cet utilitaire couvre tous les besoins d'interaction moderne avec des animations optimisées et performantes.

### ✨ Caractéristiques principales

- 🎯 **Hover Lift** : Effet d'élévation avec ombre
- 🔍 **Hover Scale** : Agrandissement au survol
- 🔄 **Hover Rotate** : Rotation subtile
- 💫 **Hover Shine** : Effet de brillance
- 🌈 **Hover Glow** : Effet lumineux
- 🎨 **Hover Tilt** : Effet 3D perspective
- ⚡ **Performances** : GPU-accelerated transforms
- 🔧 **Variables CSS** : Personnalisation complète

## 🚀 Installation

### Code SCSS

```scss
// _hover-effects.scss

// Variables globales pour effets hover
:root {
  --hover-lift-distance: -8px;
  --hover-lift-shadow: 0 12px 24px rgba(0, 0, 0, 0.15);
  --hover-scale-amount: 1.05;
  --hover-rotate-angle: 5deg;
  --hover-duration: 300ms;
  --hover-timing: ease-in-out;
}

// ============================================
// HOVER LIFT (élévation avec ombre)
// ============================================

.hover-lift {
  transition: transform var(--hover-duration, 300ms) var(
        --hover-timing,
        ease-in-out
      ), box-shadow var(--hover-duration, 300ms) var(
        --hover-timing,
        ease-in-out
      );

  &:hover {
    transform: translateY(var(--hover-lift-distance, -8px));
    box-shadow: var(--hover-lift-shadow, 0 12px 24px rgba(0, 0, 0, 0.15));
  }
}

.hover-lift-sm {
  transition: transform 300ms ease-in-out, box-shadow 300ms ease-in-out;

  &:hover {
    transform: translateY(-4px);
    box-shadow: 0 8px 16px rgba(0, 0, 0, 0.12);
  }
}

.hover-lift-lg {
  transition: transform 300ms ease-in-out, box-shadow 300ms ease-in-out;

  &:hover {
    transform: translateY(-12px);
    box-shadow: 0 16px 32px rgba(0, 0, 0, 0.2);
  }
}

// ============================================
// HOVER SCALE (agrandissement)
// ============================================

.hover-scale {
  transition: transform 300ms ease-in-out;

  &:hover {
    transform: scale(var(--hover-scale-amount, 1.05));
  }
}

.hover-scale-sm {
  transition: transform 300ms ease-in-out;

  &:hover {
    transform: scale(1.02);
  }
}

.hover-scale-lg {
  transition: transform 300ms ease-in-out;

  &:hover {
    transform: scale(1.1);
  }
}

// ============================================
// HOVER SCALE + LIFT (combiné)
// ============================================

.hover-scale-lift {
  transition: transform 300ms ease-in-out, box-shadow 300ms ease-in-out;

  &:hover {
    transform: scale(1.03) translateY(-4px);
    box-shadow: 0 12px 24px rgba(0, 0, 0, 0.15);
  }
}

// ============================================
// HOVER ROTATE (rotation)
// ============================================

.hover-rotate {
  transition: transform 300ms ease-in-out;

  &:hover {
    transform: rotate(var(--hover-rotate-angle, 5deg));
  }
}

.hover-rotate-reverse {
  transition: transform 300ms ease-in-out;

  &:hover {
    transform: rotate(-5deg);
  }
}

.hover-rotate-scale {
  transition: transform 300ms ease-in-out;

  &:hover {
    transform: rotate(5deg) scale(1.05);
  }
}

// ============================================
// HOVER TILT (perspective 3D)
// ============================================

.hover-tilt {
  transition: transform 300ms ease-in-out;
  transform-style: preserve-3d;

  &:hover {
    transform: perspective(1000px) rotateX(5deg) rotateY(5deg);
  }
}

.hover-tilt-left {
  transition: transform 300ms ease-in-out;
  transform-style: preserve-3d;

  &:hover {
    transform: perspective(1000px) rotateY(-10deg);
  }
}

.hover-tilt-right {
  transition: transform 300ms ease-in-out;
  transform-style: preserve-3d;

  &:hover {
    transform: perspective(1000px) rotateY(10deg);
  }
}

// ============================================
// HOVER SHINE (effet de brillance)
// ============================================

.hover-shine {
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
    transition: left 500ms ease-in-out;
  }

  &:hover::before {
    left: 100%;
  }
}

// ============================================
// HOVER GLOW (effet lumineux)
// ============================================

.hover-glow {
  transition: box-shadow 300ms ease-in-out, filter 300ms ease-in-out;

  &:hover {
    box-shadow: 0 0 20px currentColor, 0 0 40px currentColor;
    filter: brightness(1.1);
  }
}

.hover-glow-blue {
  transition: box-shadow 300ms ease-in-out;

  &:hover {
    box-shadow: 0 0 20px rgba(59, 130, 246, 0.6), 0 0 40px rgba(59, 130, 246, 0.4);
  }
}

.hover-glow-purple {
  transition: box-shadow 300ms ease-in-out;

  &:hover {
    box-shadow: 0 0 20px rgba(139, 92, 246, 0.6), 0 0 40px rgba(139, 92, 246, 0.4);
  }
}

.hover-glow-green {
  transition: box-shadow 300ms ease-in-out;

  &:hover {
    box-shadow: 0 0 20px rgba(34, 197, 94, 0.6), 0 0 40px rgba(34, 197, 94, 0.4);
  }
}

// ============================================
// HOVER BRIGHTNESS (luminosité)
// ============================================

.hover-brighten {
  transition: filter 300ms ease-in-out;

  &:hover {
    filter: brightness(1.15);
  }
}

.hover-darken {
  transition: filter 300ms ease-in-out;

  &:hover {
    filter: brightness(0.85);
  }
}

// ============================================
// HOVER BLUR
// ============================================

.hover-blur {
  transition: filter 300ms ease-in-out;

  &:hover {
    filter: blur(2px);
  }
}

.hover-blur-bg {
  position: relative;

  &::after {
    content: "";
    position: absolute;
    inset: 0;
    background: inherit;
    filter: blur(8px);
    opacity: 0;
    transition: opacity 300ms ease-in-out;
    z-index: -1;
  }

  &:hover::after {
    opacity: 0.5;
  }
}

// ============================================
// HOVER OPACITY
// ============================================

.hover-opacity {
  transition: opacity 300ms ease-in-out;

  &:hover {
    opacity: 0.7;
  }
}

.hover-opacity-sm {
  transition: opacity 300ms ease-in-out;

  &:hover {
    opacity: 0.85;
  }
}

.hover-opacity-full {
  opacity: 0.7;
  transition: opacity 300ms ease-in-out;

  &:hover {
    opacity: 1;
  }
}

// ============================================
// HOVER SHADOW (ombre uniquement)
// ============================================

.hover-shadow {
  transition: box-shadow 300ms ease-in-out;

  &:hover {
    box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
  }
}

.hover-shadow-lg {
  transition: box-shadow 300ms ease-in-out;

  &:hover {
    box-shadow: 0 20px 40px rgba(0, 0, 0, 0.25);
  }
}

.hover-shadow-colored {
  transition: box-shadow 300ms ease-in-out;

  &:hover {
    box-shadow: 0 10px 30px currentColor;
  }
}

// ============================================
// HOVER BORDER
// ============================================

.hover-border {
  border: 2px solid transparent;
  transition: border-color 300ms ease-in-out;

  &:hover {
    border-color: currentColor;
  }
}

.hover-border-grow {
  position: relative;

  &::after {
    content: "";
    position: absolute;
    inset: -2px;
    border: 2px solid currentColor;
    border-radius: inherit;
    opacity: 0;
    transition: opacity 300ms ease-in-out;
  }

  &:hover::after {
    opacity: 1;
  }
}

// ============================================
// HOVER UNDERLINE
// ============================================

.hover-underline {
  position: relative;

  &::after {
    content: "";
    position: absolute;
    bottom: 0;
    left: 0;
    width: 0;
    height: 2px;
    background: currentColor;
    transition: width 300ms ease-in-out;
  }

  &:hover::after {
    width: 100%;
  }
}

.hover-underline-center {
  position: relative;

  &::after {
    content: "";
    position: absolute;
    bottom: 0;
    left: 50%;
    width: 0;
    height: 2px;
    background: currentColor;
    transform: translateX(-50%);
    transition: width 300ms ease-in-out;
  }

  &:hover::after {
    width: 100%;
  }
}

// ============================================
// HOVER FLOAT (flottement)
// ============================================

.hover-float {
  animation: float 3s ease-in-out infinite;

  &:hover {
    animation-play-state: paused;
  }
}

@keyframes float {
  0%,
  100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-10px);
  }
}

// ============================================
// HOVER PULSE (pulsation)
// ============================================

.hover-pulse {
  &:hover {
    animation: pulse 1s ease-in-out infinite;
  }
}

@keyframes pulse {
  0%,
  100% {
    transform: scale(1);
  }
  50% {
    transform: scale(1.05);
  }
}

// ============================================
// HOVER SHAKE (tremblement)
// ============================================

.hover-shake {
  &:hover {
    animation: shake 500ms ease-in-out;
  }
}

@keyframes shake {
  0%,
  100% {
    transform: translateX(0);
  }
  10%,
  30%,
  50%,
  70%,
  90% {
    transform: translateX(-5px);
  }
  20%,
  40%,
  60%,
  80% {
    transform: translateX(5px);
  }
}

// ============================================
// HOVER BOUNCE
// ============================================

.hover-bounce {
  &:hover {
    animation: bounce 500ms ease-in-out;
  }
}

@keyframes bounce {
  0%,
  100% {
    transform: translateY(0);
  }
  25% {
    transform: translateY(-10px);
  }
  50% {
    transform: translateY(0);
  }
  75% {
    transform: translateY(-5px);
  }
}

// ============================================
// HOVER FLIP (retournement)
// ============================================

.hover-flip {
  transition: transform 500ms ease-in-out;
  transform-style: preserve-3d;

  &:hover {
    transform: rotateY(180deg);
  }
}

// ============================================
// HOVER SWEEP (balayage de couleur)
// ============================================

.hover-sweep {
  position: relative;
  overflow: hidden;
  z-index: 1;

  &::before {
    content: "";
    position: absolute;
    top: 0;
    left: -100%;
    width: 100%;
    height: 100%;
    background: var(--hover-sweep-color, rgba(255, 255, 255, 0.2));
    transition: left 400ms ease-in-out;
    z-index: -1;
  }

  &:hover::before {
    left: 0;
  }
}

// ============================================
// COMBINAISONS COMPLEXES
// ============================================

.hover-lift-rotate {
  transition: transform 300ms ease-in-out, box-shadow 300ms ease-in-out;

  &:hover {
    transform: translateY(-8px) rotate(3deg);
    box-shadow: 0 12px 24px rgba(0, 0, 0, 0.15);
  }
}

.hover-scale-glow {
  transition: transform 300ms ease-in-out, box-shadow 300ms ease-in-out;

  &:hover {
    transform: scale(1.05);
    box-shadow: 0 0 30px currentColor;
  }
}

.hover-lift-brighten {
  transition: transform 300ms ease-in-out, box-shadow 300ms ease-in-out,
    filter 300ms ease-in-out;

  &:hover {
    transform: translateY(-8px);
    box-shadow: 0 12px 24px rgba(0, 0, 0, 0.15);
    filter: brightness(1.1);
  }
}
```

### Import dans votre projet

```scss
// Dans styles.scss
@import "utilities/hover-effects";
```

## 💡 Utilisation de base

### Exemple 1 : Card avec hover-lift (le plus populaire)

```html
<div class="card hover-lift shadow-wrapper shadow-wrapper--md rounded-lg">
  <img src="image.jpg" alt="Image" />
  <h3>Card Title</h3>
  <p>Survole pour voir l'effet lift</p>
</div>

<style>
  .card {
    padding: 1.5rem;
    background: white;
    cursor: pointer;
  }

  .card img {
    width: 100%;
    border-radius: 0.5rem;
    margin-bottom: 1rem;
  }

  .card h3 {
    margin: 0 0 0.5rem 0;
  }

  .card p {
    margin: 0;
    color: #6b7280;
  }
</style>
```

### Exemple 2 : Button avec hover-scale

```html
<button class="btn hover-scale rounded-lg">Scale on Hover</button>

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

### Exemple 3 : Image avec hover-shine

```html
<div class="image-container hover-shine rounded-xl">
  <img src="photo.jpg" alt="Photo" />
</div>

<style>
  .image-container {
    width: 400px;
    cursor: pointer;
  }

  .image-container img {
    width: 100%;
    display: block;
    border-radius: inherit;
  }
</style>
```

### Exemple 4 : Link avec hover-underline

```html
<a href="#" class="link hover-underline"> Hover pour souligner </a>

<style>
  .link {
    text-decoration: none;
    color: #3b82f6;
    font-weight: 600;
    display: inline-block;
  }
</style>
```

## 📊 Paramètres

| Variable                | Type     | Défaut                         | Description            |
| ----------------------- | -------- | ------------------------------ | ---------------------- |
| `--hover-lift-distance` | length   | `-8px`                         | Distance du lift       |
| `--hover-lift-shadow`   | shadow   | `0 12px 24px rgba(0,0,0,0.15)` | Ombre du lift          |
| `--hover-scale-amount`  | number   | `1.05`                         | Facteur de scale       |
| `--hover-rotate-angle`  | angle    | `5deg`                         | Angle de rotation      |
| `--hover-duration`      | time     | `300ms`                        | Durée de la transition |
| `--hover-timing`        | function | `ease-in-out`                  | Fonction de timing     |

### Catégories d'effets

| Catégorie     | Effets                         | Usage                           |
| ------------- | ------------------------------ | ------------------------------- |
| **Transform** | lift, scale, rotate, tilt      | Déplacements et transformations |
| **Visual**    | shine, glow, brighten, blur    | Effets visuels                  |
| **Opacity**   | opacity, opacity-sm            | Transparence                    |
| **Shadow**    | shadow, shadow-lg              | Ombres                          |
| **Border**    | border, border-grow, underline | Bordures et soulignement        |
| **Animation** | float, pulse, shake, bounce    | Animations en boucle            |
| **Complex**   | lift-rotate, scale-glow        | Combinaisons                    |

## 📚 Exemples détaillés

### Exemple 1 : Gallery de produits avec hover-lift

```html
<div class="products-gallery">
  <div
    class="product-card hover-lift shadow-wrapper shadow-wrapper--md rounded-xl"
  >
    <div class="product-image">
      <img src="product1.jpg" alt="Product 1" />
      <span class="product-badge">NEW</span>
    </div>
    <div class="product-info">
      <h3>Product Name</h3>
      <p class="product-description">Description courte du produit</p>
      <div class="product-footer">
        <span class="product-price">99,99 €</span>
        <button class="btn-add hover-scale-sm">Ajouter</button>
      </div>
    </div>
  </div>

  <div
    class="product-card hover-lift shadow-wrapper shadow-wrapper--md rounded-xl"
  >
    <div class="product-image">
      <img src="product2.jpg" alt="Product 2" />
      <span class="product-badge product-badge--sale">-20%</span>
    </div>
    <div class="product-info">
      <h3>Product Name</h3>
      <p class="product-description">Description courte du produit</p>
      <div class="product-footer">
        <span class="product-price">79,99 €</span>
        <button class="btn-add hover-scale-sm">Ajouter</button>
      </div>
    </div>
  </div>

  <div
    class="product-card hover-lift shadow-wrapper shadow-wrapper--md rounded-xl"
  >
    <div class="product-image">
      <img src="product3.jpg" alt="Product 3" />
    </div>
    <div class="product-info">
      <h3>Product Name</h3>
      <p class="product-description">Description courte du produit</p>
      <div class="product-footer">
        <span class="product-price">129,99 €</span>
        <button class="btn-add hover-scale-sm">Ajouter</button>
      </div>
    </div>
  </div>
</div>

<style>
  .products-gallery {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
    gap: 2rem;
    padding: 2rem;
  }

  .product-card {
    background: white;
    overflow: hidden;
    cursor: pointer;
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

  .product-badge {
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

  .product-badge--sale {
    background: #ef4444;
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
  }

  .product-footer {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .product-price {
    font-size: 1.5rem;
    font-weight: 700;
    color: #059669;
  }

  .btn-add {
    padding: 0.5rem 1rem;
    background: #3b82f6;
    color: white;
    border: none;
    border-radius: 0.5rem;
    cursor: pointer;
    font-weight: 600;
  }
</style>
```

### Exemple 2 : Social media cards avec effets variés

```html
<div class="social-cards">
  <div
    class="social-card hover-scale-lift gradient-bg gradient-bg--blue rounded-2xl"
  >
    <div class="social-icon">📘</div>
    <h3>Facebook</h3>
    <p class="followers">2.5K followers</p>
    <button class="social-btn hover-brighten rounded-lg">Suivre</button>
  </div>

  <div
    class="social-card hover-scale-lift gradient-bg gradient-bg--purple rounded-2xl"
  >
    <div class="social-icon">📷</div>
    <h3>Instagram</h3>
    <p class="followers">5.2K followers</p>
    <button class="social-btn hover-brighten rounded-lg">Suivre</button>
  </div>

  <div
    class="social-card hover-scale-lift gradient-bg gradient-bg--blue rounded-2xl"
  >
    <div class="social-icon">🐦</div>
    <h3>Twitter</h3>
    <p class="followers">1.8K followers</p>
    <button class="social-btn hover-brighten rounded-lg">Suivre</button>
  </div>

  <div
    class="social-card hover-scale-lift gradient-bg gradient-bg--pink rounded-2xl"
  >
    <div class="social-icon">🎵</div>
    <h3>TikTok</h3>
    <p class="followers">8.3K followers</p>
    <button class="social-btn hover-brighten rounded-lg">Suivre</button>
  </div>
</div>

<style>
  .social-cards {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 2rem;
    padding: 2rem;
  }

  .social-card {
    padding: 2.5rem 2rem;
    color: white;
    text-align: center;
    cursor: pointer;
  }

  .social-icon {
    font-size: 4rem;
    margin-bottom: 1rem;
  }

  .social-card h3 {
    margin: 0 0 0.5rem 0;
    font-size: 1.5rem;
  }

  .followers {
    margin: 0 0 1.5rem 0;
    opacity: 0.9;
    font-size: 0.875rem;
  }

  .social-btn {
    padding: 0.75rem 2rem;
    background: rgba(255, 255, 255, 0.2);
    backdrop-filter: blur(10px);
    color: white;
    border: 1px solid rgba(255, 255, 255, 0.3);
    cursor: pointer;
    font-weight: 600;
  }
</style>
```

### Exemple 3 : Team members avec hover-tilt

```html
<div class="team-grid">
  <div
    class="team-member hover-tilt rounded-xl shadow-wrapper shadow-wrapper--lg"
  >
    <div class="member-photo">
      <img src="member1.jpg" alt="Team Member 1" />
    </div>
    <div class="member-info">
      <h3>Jean Dupont</h3>
      <p class="member-role">CEO & Founder</p>
      <p class="member-bio">Expert en stratégie digitale</p>
      <div class="member-social">
        <a href="#" class="social-link hover-scale">💼</a>
        <a href="#" class="social-link hover-scale">🐦</a>
        <a href="#" class="social-link hover-scale">📧</a>
      </div>
    </div>
  </div>

  <div
    class="team-member hover-tilt rounded-xl shadow-wrapper shadow-wrapper--lg"
  >
    <div class="member-photo">
      <img src="member2.jpg" alt="Team Member 2" />
    </div>
    <div class="member-info">
      <h3>Marie Martin</h3>
      <p class="member-role">CTO</p>
      <p class="member-bio">Architecte logiciel passionnée</p>
      <div class="member-social">
        <a href="#" class="social-link hover-scale">💼</a>
        <a href="#" class="social-link hover-scale">🐦</a>
        <a href="#" class="social-link hover-scale">📧</a>
      </div>
    </div>
  </div>

  <div
    class="team-member hover-tilt rounded-xl shadow-wrapper shadow-wrapper--lg"
  >
    <div class="member-photo">
      <img src="member3.jpg" alt="Team Member 3" />
    </div>
    <div class="member-info">
      <h3>Thomas Leroux</h3>
      <p class="member-role">Lead Designer</p>
      <p class="member-bio">Designer UX/UI créatif</p>
      <div class="member-social">
        <a href="#" class="social-link hover-scale">💼</a>
        <a href="#" class="social-link hover-scale">🐦</a>
        <a href="#" class="social-link hover-scale">📧</a>
      </div>
    </div>
  </div>
</div>

<style>
  .team-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 3rem;
    padding: 3rem 2rem;
  }

  .team-member {
    background: white;
    overflow: hidden;
    cursor: pointer;
  }

  .member-photo {
    width: 100%;
    height: 320px;
  }

  .member-photo img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }

  .member-info {
    padding: 2rem 1.5rem;
    text-align: center;
  }

  .member-info h3 {
    margin: 0 0 0.5rem 0;
    font-size: 1.5rem;
  }

  .member-role {
    margin: 0 0 1rem 0;
    color: #3b82f6;
    font-weight: 600;
    font-size: 0.875rem;
  }

  .member-bio {
    margin: 0 0 1.5rem 0;
    color: #6b7280;
  }

  .member-social {
    display: flex;
    justify-content: center;
    gap: 1rem;
  }

  .social-link {
    width: 40px;
    height: 40px;
    display: flex;
    align-items: center;
    justify-content: center;
    background: #f3f4f6;
    border-radius: 50%;
    text-decoration: none;
    font-size: 1.25rem;
  }
</style>
```

### Exemple 4 : Buttons showcase avec tous les effets

```html
<div class="buttons-showcase">
  <div class="button-group">
    <h3>Lift Effects</h3>
    <button class="btn hover-lift-sm rounded-lg">Lift Small</button>
    <button class="btn hover-lift rounded-lg">Lift Default</button>
    <button class="btn hover-lift-lg rounded-lg">Lift Large</button>
  </div>

  <div class="button-group">
    <h3>Scale Effects</h3>
    <button class="btn hover-scale-sm rounded-lg">Scale Small</button>
    <button class="btn hover-scale rounded-lg">Scale Default</button>
    <button class="btn hover-scale-lg rounded-lg">Scale Large</button>
  </div>

  <div class="button-group">
    <h3>Rotate Effects</h3>
    <button class="btn hover-rotate rounded-lg">Rotate</button>
    <button class="btn hover-rotate-reverse rounded-lg">Rotate Reverse</button>
    <button class="btn hover-rotate-scale rounded-lg">Rotate + Scale</button>
  </div>

  <div class="button-group">
    <h3>Visual Effects</h3>
    <button class="btn hover-shine rounded-lg">Shine</button>
    <button class="btn hover-glow rounded-lg">Glow</button>
    <button class="btn hover-brighten rounded-lg">Brighten</button>
  </div>

  <div class="button-group">
    <h3>Complex Effects</h3>
    <button class="btn hover-lift-rotate rounded-lg">Lift + Rotate</button>
    <button class="btn hover-scale-lift rounded-lg">Scale + Lift</button>
    <button class="btn hover-lift-brighten rounded-lg">Lift + Brighten</button>
  </div>

  <div class="button-group">
    <h3>Animation Effects</h3>
    <button class="btn hover-pulse rounded-lg">Pulse</button>
    <button class="btn hover-shake rounded-lg">Shake</button>
    <button class="btn hover-bounce rounded-lg">Bounce</button>
  </div>
</div>

<style>
  .buttons-showcase {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 3rem;
    padding: 3rem 2rem;
  }

  .button-group {
    text-align: center;
  }

  .button-group h3 {
    margin: 0 0 1.5rem 0;
    font-size: 1.25rem;
    color: #374151;
  }

  .btn {
    display: block;
    width: 100%;
    padding: 1rem;
    margin-bottom: 0.75rem;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
    border: none;
    cursor: pointer;
    font-weight: 600;
  }
</style>
```

### Exemple 5 : Portfolio grid avec hover-shine et hover-scale

```html
<div class="portfolio-grid">
  <div
    class="portfolio-item hover-shine hover-scale-sm rounded-xl shadow-wrapper shadow-wrapper--md"
  >
    <img src="project1.jpg" alt="Project 1" />
    <div class="portfolio-overlay">
      <h3>Projet Web App</h3>
      <p>Design & Development</p>
      <button class="btn-view rounded-lg">Voir le projet</button>
    </div>
  </div>

  <div
    class="portfolio-item hover-shine hover-scale-sm rounded-xl shadow-wrapper shadow-wrapper--md"
  >
    <img src="project2.jpg" alt="Project 2" />
    <div class="portfolio-overlay">
      <h3>Mobile App</h3>
      <p>UI/UX Design</p>
      <button class="btn-view rounded-lg">Voir le projet</button>
    </div>
  </div>

  <div
    class="portfolio-item hover-shine hover-scale-sm rounded-xl shadow-wrapper shadow-wrapper--md"
  >
    <img src="project3.jpg" alt="Project 3" />
    <div class="portfolio-overlay">
      <h3>Branding</h3>
      <p>Identity Design</p>
      <button class="btn-view rounded-lg">Voir le projet</button>
    </div>
  </div>

  <div
    class="portfolio-item hover-shine hover-scale-sm rounded-xl shadow-wrapper shadow-wrapper--md"
  >
    <img src="project4.jpg" alt="Project 4" />
    <div class="portfolio-overlay">
      <h3>E-commerce</h3>
      <p>Full Stack Development</p>
      <button class="btn-view rounded-lg">Voir le projet</button>
    </div>
  </div>
</div>

<style>
  .portfolio-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(400px, 1fr));
    gap: 2rem;
    padding: 2rem;
  }

  .portfolio-item {
    position: relative;
    height: 400px;
    overflow: hidden;
    cursor: pointer;
  }

  .portfolio-item img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }

  .portfolio-overlay {
    position: absolute;
    inset: 0;
    background: linear-gradient(
      to top,
      rgba(0, 0, 0, 0.9) 0%,
      rgba(0, 0, 0, 0.4) 50%,
      transparent 100%
    );
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    padding: 2rem;
    color: white;
    opacity: 0;
    transition: opacity 300ms ease-in-out;
  }

  .portfolio-item:hover .portfolio-overlay {
    opacity: 1;
  }

  .portfolio-overlay h3 {
    margin: 0 0 0.5rem 0;
    font-size: 1.75rem;
  }

  .portfolio-overlay p {
    margin: 0 0 1.5rem 0;
    opacity: 0.9;
  }

  .btn-view {
    padding: 0.75rem 1.5rem;
    background: white;
    color: #111827;
    border: none;
    cursor: pointer;
    font-weight: 600;
    align-self: flex-start;
  }
</style>
```

## 🎨 Personnalisation avancée

### Lift personnalisé avec variables

```html
<div
  class="hover-lift"
  style="--hover-lift-distance: -15px; 
            --hover-lift-shadow: 0 20px 40px rgba(0,0,0,0.25)"
>
  Lift personnalisé
</div>
```

### Scale avec valeur custom

```html
<div class="hover-scale" style="--hover-scale-amount: 1.15">Scale de 115%</div>
```

### Rotate avec angle personnalisé

```html
<div class="hover-rotate" style="--hover-rotate-angle: 10deg">
  Rotation de 10 degrés
</div>
```

### Combinaison personnalisée

```html
<div class="custom-hover">Effet combiné custom</div>

<style>
  .custom-hover {
    transition: transform 400ms cubic-bezier(0.68, -0.55, 0.265, 1.55), box-shadow
        400ms ease-in-out, filter 400ms ease-in-out;
  }

  .custom-hover:hover {
    transform: translateY(-12px) rotate(2deg) scale(1.03);
    box-shadow: 0 16px 32px rgba(0, 0, 0, 0.2);
    filter: brightness(1.1) saturate(1.2);
  }
</style>
```

## 🎯 Cas d'usage courants

### 1. Product cards

```html
<div class="product hover-lift shadow-wrapper shadow-wrapper--md">
  Product info
</div>
```

### 2. Call-to-action buttons

```html
<button class="cta hover-scale-lift">Get Started</button>
```

### 3. Portfolio items

```html
<div class="portfolio-item hover-shine hover-scale-sm">Project preview</div>
```

### 4. Social media icons

```html
<a href="#" class="social-icon hover-glow-blue hover-rotate"> Icon </a>
```

### 5. Team members

```html
<div class="team-card hover-tilt">Member info</div>
```

### 6. Navigation links

```html
<a href="#" class="nav-link hover-underline"> Link </a>
```

### 7. Feature cards

```html
<div class="feature hover-lift-rotate">Feature content</div>
```

## 🔧 Combinaison avec autres utilitaires

### Avec Shadow Wrapper

```html
<div class="card hover-lift shadow-wrapper shadow-wrapper--md rounded-xl">
  Card avec lift + ombre
</div>
```

### Avec Gradient Background

```html
<button class="btn gradient-bg gradient-bg--sunset hover-scale rounded-full">
  Gradient button avec scale
</button>
```

### Avec Glass Effect

```html
<div class="glass-effect glass-effect--light hover-lift-brighten rounded-2xl">
  Glass avec lift + brighten
</div>
```

### Avec Rounded

```html
<div class="hover-lift rounded-3xl">Coins très arrondis + lift</div>
```

## 📱 Comportement responsive

### Désactiver les effets sur mobile

```scss
@media (max-width: 768px) {
  .hover-lift,
  .hover-scale,
  .hover-rotate {
    transform: none !important;

    &:hover {
      transform: none !important;
    }
  }
}
```

### Effets réduits sur mobile

```scss
@media (max-width: 768px) {
  .hover-lift:hover {
    transform: translateY(-4px); // Au lieu de -8px
  }

  .hover-scale:hover {
    transform: scale(1.02); // Au lieu de 1.05
  }
}
```

## ⚡ Performance & Bonnes pratiques

### ✅ À faire

```html
<!-- Bon : Utiliser transform (GPU-accelerated) -->
<div class="hover-lift">
  <!-- Bon : Combiner effets compatibles -->
  <div class="hover-scale-lift">
    <!-- Bon : Utiliser will-change si animation complexe -->
    <div style="will-change: transform">
      <!-- Bon : Transitions courtes -->
      <div style="transition: transform 300ms"></div>
    </div>
  </div>
</div>
```

### ❌ À éviter

```html
<!-- Mauvais : Trop d'effets combinés -->
<div class="hover-lift hover-scale hover-rotate hover-glow hover-brighten">
  <!-- Mauvais : Transitions trop lentes -->
  <div style="transition: transform 2s">
    <!-- Mauvais : Animer des propriétés coûteuses -->
    <div style="transition: width 300ms, height 300ms">
      <!-- Mauvais : will-change partout -->
      <div style="will-change: transform, opacity, box-shadow, filter"></div>
    </div>
  </div>
</div>
```

### Optimisations

```scss
// ✅ Grouper les transitions
.hover-lift {
  transition: transform 300ms ease-in-out, box-shadow 300ms ease-in-out;
}

// ✅ Utiliser transform au lieu de position
// Mauvais
.element:hover {
  top: -8px;
}

// Bon
.element:hover {
  transform: translateY(-8px);
}

// ✅ Précharger les images pour hover-shine
.hover-shine {
  &::before {
    content: "";
    /* Le pseudo-élément existe déjà, pas de layout shift */
  }
}
```

## 🌐 Compatibilité navigateurs

| Navigateur | Version minimale | Support    |
| ---------- | ---------------- | ---------- |
| Chrome     | 36+              | ✅ Complet |
| Firefox    | 16+              | ✅ Complet |
| Safari     | 9+               | ✅ Complet |
| Edge       | 12+              | ✅ Complet |
| Opera      | 23+              | ✅ Complet |

**Note** : Les transforms et transitions sont très bien supportés.

## 🐛 Troubleshooting

### Problème : L'effet ne se déclenche pas

**Solution** : Vérifiez que l'élément est interactif

```css
/* Ajoutez cursor: pointer */
.hover-lift {
  cursor: pointer;
}
```

### Problème : L'effet est saccadé

**Solution** : Utilisez will-change

```css
.hover-lift {
  will-change: transform;
  transition: transform 300ms ease-in-out;
}
```

### Problème : Le contenu déborde

**Solution** : Ajoutez overflow: hidden

```css
.hover-shine {
  overflow: hidden;
  position: relative;
}
```

### Problème : L'ombre est coupée

**Solution** : Ajoutez du padding au parent

```css
.container {
  padding: 1rem; /* Espace pour l'ombre */
}
```

## 📦 Classes complètes disponibles

```scss
// Lift
.hover-lift-sm {
  /* Lift 4px */
}
.hover-lift {
  /* Lift 8px */
}
.hover-lift-lg {
  /* Lift 12px */
}

// Scale
.hover-scale-sm {
  /* Scale 1.02 */
}
.hover-scale {
  /* Scale 1.05 */
}
.hover-scale-lg {
  /* Scale 1.1 */
}

// Rotate
.hover-rotate {
  /* Rotate 5deg */
}
.hover-rotate-reverse {
  /* Rotate -5deg */
}
.hover-rotate-scale {
  /* Rotate + Scale */
}

// Tilt (3D)
.hover-tilt {
  /* 3D tilt */
}
.hover-tilt-left {
  /* Tilt left */
}
.hover-tilt-right {
  /* Tilt right */
}

// Visual
.hover-shine {
  /* Brillance */
}
.hover-glow {
  /* Glow effet */
}
.hover-brighten {
  /* Luminosité */
}
.hover-darken {
  /* Assombrir */
}
.hover-blur {
  /* Flou */
}

// Opacity
.hover-opacity {
  /* Opacity 0.7 */
}
.hover-opacity-sm {
  /* Opacity 0.85 */
}
.hover-opacity-full {
  /* Opacity 1 */
}

// Shadow
.hover-shadow {
  /* Ombre */
}
.hover-shadow-lg {
  /* Grande ombre */
}

// Border & Underline
.hover-border {
  /* Bordure */
}
.hover-underline {
  /* Soulignement */
}
.hover-underline-center {
  /* Soulignement centré */
}

// Animations
.hover-float {
  /* Flottement */
}
.hover-pulse {
  /* Pulsation */
}
.hover-shake {
  /* Tremblement */
}
.hover-bounce {
  /* Rebond */
}
.hover-flip {
  /* Retournement */
}

// Complex
.hover-lift-rotate {
  /* Lift + Rotate */
}
.hover-scale-lift {
  /* Scale + Lift */
}
.hover-scale-glow {
  /* Scale + Glow */
}
.hover-lift-brighten {
  /* Lift + Brighten */
}
```

## 🎓 Ressources complémentaires

- [CSS Transform - MDN](https://developer.mozilla.org/fr/docs/Web/CSS/transform)
- [CSS Transition - MDN](https://developer.mozilla.org/fr/docs/Web/CSS/transition)
- [Hover.css](https://ianlunn.github.io/Hover/)
- [Animista](https://animista.net/)

## 📝 Changelog

- **v1.0** - Version initiale avec hover-lift et hover-scale
- **v1.1** - Ajout des effets rotate, tilt, shine
- **v1.2** - Ajout des effets glow, brighten, blur
- **v1.3** - Ajout des animations (pulse, shake, bounce)
- **v1.4** - Ajout des combinaisons complexes
- **v1.5** - Optimisations performance

---

**Made with ❤️ for delightful interactions**
