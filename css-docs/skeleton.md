# Skeleton Loader Utility

> Placeholders animés élégants pour améliorer l'expérience de chargement et réduire la perception d'attente

## 📋 Description

**Skeleton Loader** est un utilitaire CSS qui fournit des placeholders animés (skeleton screens) pour indiquer le chargement de contenu. Ces placeholders imitent la structure du contenu à venir, offrant une expérience utilisateur fluide et moderne qui réduit la frustration liée aux temps de chargement.

### ✨ Caractéristiques principales

- 💀 **Skeleton complet** : Text, circle, rectangle, card
- 🌊 **Wave animation** : Effet de vague qui parcourt l'élément
- 💓 **Pulse animation** : Pulsation douce
- 📏 **Tailles variées** : xs, sm, md, lg, xl pour texte
- 🎨 **Thèmes** : Light et dark mode
- 🔧 **Variables CSS** : Personnalisation complète
- ⚡ **Performances** : GPU-accelerated animations
- 📱 **Responsive** : S'adapte à tous les écrans

## 🚀 Installation

### Code SCSS

```scss
// _skeleton-loader.scss

// Variables globales
:root {
  --skeleton-bg: #e5e7eb;
  --skeleton-highlight: #f3f4f6;
  --skeleton-border-radius: 0.5rem;
  --skeleton-animation-duration: 1.5s;
}

// Dark mode
@media (prefers-color-scheme: dark) {
  :root {
    --skeleton-bg: #374151;
    --skeleton-highlight: #4b5563;
  }
}

// ============================================
// BASE SKELETON
// ============================================

.skeleton {
  background: var(--skeleton-bg, #e5e7eb);
  border-radius: var(--skeleton-border-radius, 0.5rem);
  position: relative;
  overflow: hidden;

  // Empêche le contenu de s'afficher pendant le chargement
  color: transparent !important;
  pointer-events: none;
  user-select: none;

  // Cache les éléments enfants
  * {
    visibility: hidden;
  }
}

// ============================================
// ANIMATIONS
// ============================================

// Wave animation (par défaut)
.skeleton--wave {
  &::after {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: linear-gradient(
      90deg,
      transparent 0%,
      var(--skeleton-highlight, #f3f4f6) 50%,
      transparent 100%
    );
    transform: translateX(-100%);
    animation: skeleton-wave var(--skeleton-animation-duration, 1.5s) ease-in-out
      infinite;
  }
}

@keyframes skeleton-wave {
  0% {
    transform: translateX(-100%);
  }
  100% {
    transform: translateX(100%);
  }
}

// Pulse animation
.skeleton--pulse {
  animation: skeleton-pulse var(--skeleton-animation-duration, 1.5s) ease-in-out
    infinite;
}

@keyframes skeleton-pulse {
  0%,
  100% {
    opacity: 1;
  }
  50% {
    opacity: 0.5;
  }
}

// ============================================
// FORMES ET TYPES
// ============================================

// Texte (par défaut)
.skeleton-text {
  height: 1em;
  border-radius: 0.25rem;
  margin-bottom: 0.5rem;

  &:last-child {
    margin-bottom: 0;
  }
}

// Tailles de texte
.skeleton-text--xs {
  height: 0.75rem;
}

.skeleton-text--sm {
  height: 0.875rem;
}

.skeleton-text--md {
  height: 1rem;
}

.skeleton-text--lg {
  height: 1.25rem;
}

.skeleton-text--xl {
  height: 1.5rem;
}

.skeleton-text--2xl {
  height: 2rem;
}

// Texte avec largeur partielle
.skeleton-text--short {
  width: 60%;
}

.skeleton-text--medium {
  width: 80%;
}

.skeleton-text--long {
  width: 95%;
}

// ============================================
// FORMES GÉOMÉTRIQUES
// ============================================

// Circle (avatar)
.skeleton-circle {
  border-radius: 50%;
  width: var(--skeleton-size, 3rem);
  height: var(--skeleton-size, 3rem);
  flex-shrink: 0;
}

.skeleton-circle--sm {
  width: 2rem;
  height: 2rem;
}

.skeleton-circle--md {
  width: 3rem;
  height: 3rem;
}

.skeleton-circle--lg {
  width: 4rem;
  height: 4rem;
}

.skeleton-circle--xl {
  width: 6rem;
  height: 6rem;
}

// Rectangle (image placeholder)
.skeleton-rectangle {
  width: 100%;
  height: var(--skeleton-height, 12rem);
  border-radius: var(--skeleton-border-radius, 0.5rem);
}

.skeleton-rectangle--sm {
  height: 8rem;
}

.skeleton-rectangle--md {
  height: 12rem;
}

.skeleton-rectangle--lg {
  height: 16rem;
}

.skeleton-rectangle--xl {
  height: 20rem;
}

// Square
.skeleton-square {
  width: var(--skeleton-size, 8rem);
  height: var(--skeleton-size, 8rem);
  border-radius: var(--skeleton-border-radius, 0.5rem);
}

// ============================================
// COMPOSANTS PRÉFABRIQUÉS
// ============================================

// Card skeleton
.skeleton-card {
  background: white;
  border-radius: 0.75rem;
  padding: 1.5rem;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
}

// Avatar + Text (media object)
.skeleton-media {
  display: flex;
  align-items: center;
  gap: 1rem;

  .skeleton-avatar {
    flex-shrink: 0;
  }

  .skeleton-content {
    flex: 1;
    min-width: 0;
  }
}

// Article preview
.skeleton-article {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

// Profile header
.skeleton-profile {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  gap: 1rem;
}

// Comment skeleton
.skeleton-comment {
  display: flex;
  gap: 1rem;
  padding: 1rem;
  border-radius: 0.5rem;
  background: #f9fafb;
}

// ============================================
// LAYOUTS
// ============================================

// Grid de skeletons
.skeleton-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  gap: 1.5rem;
}

// Liste de skeletons
.skeleton-list {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

// ============================================
// THÈMES
// ============================================

.skeleton--light {
  --skeleton-bg: #e5e7eb;
  --skeleton-highlight: #f3f4f6;
}

.skeleton--dark {
  --skeleton-bg: #374151;
  --skeleton-highlight: #4b5563;
}

.skeleton--white {
  --skeleton-bg: #f3f4f6;
  --skeleton-highlight: #ffffff;
}

// ============================================
// UTILITAIRES
// ============================================

// Désactiver l'animation (accessibilité)
@media (prefers-reduced-motion: reduce) {
  .skeleton--wave::after {
    animation: none;
  }

  .skeleton--pulse {
    animation: none;
    opacity: 0.7;
  }
}

// Loading state utility
.is-loading {
  .skeleton {
    display: block;
  }

  .content {
    display: none;
  }
}

.is-loaded {
  .skeleton {
    display: none;
  }

  .content {
    display: block;
  }
}

// ============================================
// ASPECTS RATIO (pour images)
// ============================================

.skeleton-aspect-square {
  aspect-ratio: 1 / 1;
}

.skeleton-aspect-video {
  aspect-ratio: 16 / 9;
}

.skeleton-aspect-portrait {
  aspect-ratio: 3 / 4;
}

.skeleton-aspect-wide {
  aspect-ratio: 21 / 9;
}
```

### Import dans votre projet

```scss
// Dans styles.scss
@import "utilities/skeleton-loader";
```

## 💡 Utilisation de base

### Exemple 1 : Texte simple avec wave

```html
<div class="skeleton skeleton--wave skeleton-text"></div>
<div class="skeleton skeleton--wave skeleton-text"></div>
<div class="skeleton skeleton--wave skeleton-text skeleton-text--short"></div>
```

### Exemple 2 : Avatar circulaire

```html
<div class="skeleton skeleton--pulse skeleton-circle skeleton-circle--lg"></div>
```

### Exemple 3 : Image placeholder

```html
<div
  class="skeleton skeleton--wave skeleton-rectangle skeleton-rectangle--md"
></div>
```

### Exemple 4 : Card complète

```html
<div class="skeleton-card">
  <!-- Image -->
  <div
    class="skeleton skeleton--wave skeleton-rectangle skeleton-rectangle--md"
  ></div>

  <!-- Title -->
  <div
    class="skeleton skeleton--wave skeleton-text skeleton-text--xl"
    style="margin-top: 1rem"
  ></div>

  <!-- Description -->
  <div class="skeleton skeleton--wave skeleton-text"></div>
  <div class="skeleton skeleton--wave skeleton-text"></div>
  <div
    class="skeleton skeleton--wave skeleton-text skeleton-text--medium"
  ></div>
</div>
```

## 📊 Paramètres

| Variable                        | Type   | Défaut    | Description               |
| ------------------------------- | ------ | --------- | ------------------------- |
| `--skeleton-bg`                 | color  | `#e5e7eb` | Couleur de fond           |
| `--skeleton-highlight`          | color  | `#f3f4f6` | Couleur du highlight      |
| `--skeleton-border-radius`      | length | `0.5rem`  | Border radius             |
| `--skeleton-animation-duration` | time   | `1.5s`    | Durée de l'animation      |
| `--skeleton-size`               | length | `3rem`    | Taille pour circle/square |
| `--skeleton-height`             | length | `12rem`   | Hauteur pour rectangle    |

### Types de skeletons

| Classe               | Usage           | Forme             |
| -------------------- | --------------- | ----------------- |
| `skeleton-text`      | Lignes de texte | Rectangle arrondi |
| `skeleton-circle`    | Avatars         | Cercle            |
| `skeleton-rectangle` | Images          | Rectangle         |
| `skeleton-square`    | Icônes/médias   | Carré             |

### Tailles disponibles

| Taille | Text     | Circle | Rectangle |
| ------ | -------- | ------ | --------- |
| `xs`   | 0.75rem  | -      | -         |
| `sm`   | 0.875rem | 2rem   | 8rem      |
| `md`   | 1rem     | 3rem   | 12rem     |
| `lg`   | 1.25rem  | 4rem   | 16rem     |
| `xl`   | 1.5rem   | 6rem   | 20rem     |
| `2xl`  | 2rem     | -      | -         |

## 📚 Exemples détaillés

### Exemple 1 : Profile card loading

```html
<div class="skeleton-card">
  <div class="skeleton-profile">
    <!-- Avatar -->
    <div
      class="skeleton skeleton--pulse skeleton-circle skeleton-circle--xl"
    ></div>

    <!-- Name -->
    <div
      class="skeleton skeleton--wave skeleton-text skeleton-text--xl"
      style="width: 200px"
    ></div>

    <!-- Bio -->
    <div style="width: 100%; max-width: 400px;">
      <div class="skeleton skeleton--wave skeleton-text"></div>
      <div class="skeleton skeleton--wave skeleton-text"></div>
      <div
        class="skeleton skeleton--wave skeleton-text skeleton-text--medium"
      ></div>
    </div>

    <!-- Stats -->
    <div style="display: flex; gap: 2rem; margin-top: 1rem;">
      <div style="text-align: center;">
        <div
          class="skeleton skeleton--pulse skeleton-text skeleton-text--xl"
          style="width: 60px; margin-bottom: 0.5rem;"
        ></div>
        <div
          class="skeleton skeleton--pulse skeleton-text skeleton-text--sm"
          style="width: 80px;"
        ></div>
      </div>
      <div style="text-align: center;">
        <div
          class="skeleton skeleton--pulse skeleton-text skeleton-text--xl"
          style="width: 60px; margin-bottom: 0.5rem;"
        ></div>
        <div
          class="skeleton skeleton--pulse skeleton-text skeleton-text--sm"
          style="width: 80px;"
        ></div>
      </div>
      <div style="text-align: center;">
        <div
          class="skeleton skeleton--pulse skeleton-text skeleton-text--xl"
          style="width: 60px; margin-bottom: 0.5rem;"
        ></div>
        <div
          class="skeleton skeleton--pulse skeleton-text skeleton-text--sm"
          style="width: 80px;"
        ></div>
      </div>
    </div>
  </div>
</div>

<style>
  .skeleton-card {
    max-width: 600px;
    margin: 2rem auto;
  }
</style>
```

### Exemple 2 : Article list loading

```html
<div
  class="skeleton-list"
  style="max-width: 800px; margin: 2rem auto; padding: 1rem;"
>
  <!-- Article 1 -->
  <div class="skeleton-card">
    <div class="skeleton-media">
      <div
        class="skeleton skeleton--pulse skeleton-circle skeleton-circle--md"
      ></div>
      <div class="skeleton-content">
        <div
          class="skeleton skeleton--wave skeleton-text skeleton-text--sm"
          style="width: 150px; margin-bottom: 0.25rem;"
        ></div>
        <div
          class="skeleton skeleton--wave skeleton-text skeleton-text--xs"
          style="width: 100px;"
        ></div>
      </div>
    </div>

    <div style="margin-top: 1rem;">
      <div
        class="skeleton skeleton--wave skeleton-text skeleton-text--xl"
        style="margin-bottom: 0.75rem;"
      ></div>
      <div
        class="skeleton skeleton--wave skeleton-rectangle skeleton-rectangle--md"
      ></div>
      <div style="margin-top: 0.75rem;">
        <div class="skeleton skeleton--wave skeleton-text"></div>
        <div class="skeleton skeleton--wave skeleton-text"></div>
        <div
          class="skeleton skeleton--wave skeleton-text skeleton-text--medium"
        ></div>
      </div>
    </div>
  </div>

  <!-- Article 2 -->
  <div class="skeleton-card">
    <div class="skeleton-media">
      <div
        class="skeleton skeleton--pulse skeleton-circle skeleton-circle--md"
      ></div>
      <div class="skeleton-content">
        <div
          class="skeleton skeleton--wave skeleton-text skeleton-text--sm"
          style="width: 150px; margin-bottom: 0.25rem;"
        ></div>
        <div
          class="skeleton skeleton--wave skeleton-text skeleton-text--xs"
          style="width: 100px;"
        ></div>
      </div>
    </div>

    <div style="margin-top: 1rem;">
      <div
        class="skeleton skeleton--wave skeleton-text skeleton-text--xl"
        style="margin-bottom: 0.75rem;"
      ></div>
      <div
        class="skeleton skeleton--wave skeleton-rectangle skeleton-rectangle--md"
      ></div>
      <div style="margin-top: 0.75rem;">
        <div class="skeleton skeleton--wave skeleton-text"></div>
        <div class="skeleton skeleton--wave skeleton-text"></div>
        <div
          class="skeleton skeleton--wave skeleton-text skeleton-text--long"
        ></div>
      </div>
    </div>
  </div>

  <!-- Article 3 -->
  <div class="skeleton-card">
    <div class="skeleton-media">
      <div
        class="skeleton skeleton--pulse skeleton-circle skeleton-circle--md"
      ></div>
      <div class="skeleton-content">
        <div
          class="skeleton skeleton--wave skeleton-text skeleton-text--sm"
          style="width: 150px; margin-bottom: 0.25rem;"
        ></div>
        <div
          class="skeleton skeleton--wave skeleton-text skeleton-text--xs"
          style="width: 100px;"
        ></div>
      </div>
    </div>

    <div style="margin-top: 1rem;">
      <div
        class="skeleton skeleton--wave skeleton-text skeleton-text--xl"
        style="margin-bottom: 0.75rem;"
      ></div>
      <div
        class="skeleton skeleton--wave skeleton-rectangle skeleton-rectangle--md"
      ></div>
      <div style="margin-top: 0.75rem;">
        <div class="skeleton skeleton--wave skeleton-text"></div>
        <div class="skeleton skeleton--wave skeleton-text"></div>
        <div
          class="skeleton skeleton--wave skeleton-text skeleton-text--short"
        ></div>
      </div>
    </div>
  </div>
</div>
```

### Exemple 3 : Product grid loading

```html
<div class="skeleton-grid" style="padding: 2rem;">
  <!-- Product 1 -->
  <div class="skeleton-card">
    <div
      class="skeleton skeleton--wave skeleton-rectangle skeleton-rectangle--lg"
    ></div>
    <div style="margin-top: 1rem;">
      <div
        class="skeleton skeleton--wave skeleton-text skeleton-text--lg"
      ></div>
      <div
        class="skeleton skeleton--wave skeleton-text skeleton-text--sm"
        style="margin-top: 0.5rem; width: 60%;"
      ></div>
      <div
        style="display: flex; justify-content: space-between; align-items: center; margin-top: 1rem;"
      >
        <div
          class="skeleton skeleton--pulse skeleton-text skeleton-text--xl"
          style="width: 80px;"
        ></div>
        <div
          class="skeleton skeleton--pulse skeleton-square"
          style="--skeleton-size: 40px;"
        ></div>
      </div>
    </div>
  </div>

  <!-- Product 2 -->
  <div class="skeleton-card">
    <div
      class="skeleton skeleton--wave skeleton-rectangle skeleton-rectangle--lg"
    ></div>
    <div style="margin-top: 1rem;">
      <div
        class="skeleton skeleton--wave skeleton-text skeleton-text--lg"
      ></div>
      <div
        class="skeleton skeleton--wave skeleton-text skeleton-text--sm"
        style="margin-top: 0.5rem; width: 60%;"
      ></div>
      <div
        style="display: flex; justify-content: space-between; align-items: center; margin-top: 1rem;"
      >
        <div
          class="skeleton skeleton--pulse skeleton-text skeleton-text--xl"
          style="width: 80px;"
        ></div>
        <div
          class="skeleton skeleton--pulse skeleton-square"
          style="--skeleton-size: 40px;"
        ></div>
      </div>
    </div>
  </div>

  <!-- Product 3 -->
  <div class="skeleton-card">
    <div
      class="skeleton skeleton--wave skeleton-rectangle skeleton-rectangle--lg"
    ></div>
    <div style="margin-top: 1rem;">
      <div
        class="skeleton skeleton--wave skeleton-text skeleton-text--lg"
      ></div>
      <div
        class="skeleton skeleton--wave skeleton-text skeleton-text--sm"
        style="margin-top: 0.5rem; width: 60%;"
      ></div>
      <div
        style="display: flex; justify-content: space-between; align-items: center; margin-top: 1rem;"
      >
        <div
          class="skeleton skeleton--pulse skeleton-text skeleton-text--xl"
          style="width: 80px;"
        ></div>
        <div
          class="skeleton skeleton--pulse skeleton-square"
          style="--skeleton-size: 40px;"
        ></div>
      </div>
    </div>
  </div>

  <!-- Product 4 -->
  <div class="skeleton-card">
    <div
      class="skeleton skeleton--wave skeleton-rectangle skeleton-rectangle--lg"
    ></div>
    <div style="margin-top: 1rem;">
      <div
        class="skeleton skeleton--wave skeleton-text skeleton-text--lg"
      ></div>
      <div
        class="skeleton skeleton--wave skeleton-text skeleton-text--sm"
        style="margin-top: 0.5rem; width: 60%;"
      ></div>
      <div
        style="display: flex; justify-content: space-between; align-items: center; margin-top: 1rem;"
      >
        <div
          class="skeleton skeleton--pulse skeleton-text skeleton-text--xl"
          style="width: 80px;"
        ></div>
        <div
          class="skeleton skeleton--pulse skeleton-square"
          style="--skeleton-size: 40px;"
        ></div>
      </div>
    </div>
  </div>
</div>
```

### Exemple 4 : Comments loading

```html
<div
  class="skeleton-list"
  style="max-width: 700px; margin: 2rem auto; padding: 1rem;"
>
  <!-- Comment 1 -->
  <div class="skeleton-comment">
    <div
      class="skeleton skeleton--pulse skeleton-circle skeleton-circle--md"
    ></div>
    <div style="flex: 1;">
      <div
        class="skeleton skeleton--wave skeleton-text skeleton-text--sm"
        style="width: 120px; margin-bottom: 0.5rem;"
      ></div>
      <div class="skeleton skeleton--wave skeleton-text"></div>
      <div class="skeleton skeleton--wave skeleton-text"></div>
      <div
        class="skeleton skeleton--wave skeleton-text skeleton-text--medium"
      ></div>
      <div style="display: flex; gap: 1rem; margin-top: 0.75rem;">
        <div
          class="skeleton skeleton--pulse skeleton-text skeleton-text--xs"
          style="width: 60px;"
        ></div>
        <div
          class="skeleton skeleton--pulse skeleton-text skeleton-text--xs"
          style="width: 60px;"
        ></div>
      </div>
    </div>
  </div>

  <!-- Comment 2 (avec réponse indentée) -->
  <div>
    <div class="skeleton-comment">
      <div
        class="skeleton skeleton--pulse skeleton-circle skeleton-circle--md"
      ></div>
      <div style="flex: 1;">
        <div
          class="skeleton skeleton--wave skeleton-text skeleton-text--sm"
          style="width: 120px; margin-bottom: 0.5rem;"
        ></div>
        <div class="skeleton skeleton--wave skeleton-text"></div>
        <div
          class="skeleton skeleton--wave skeleton-text skeleton-text--long"
        ></div>
        <div style="display: flex; gap: 1rem; margin-top: 0.75rem;">
          <div
            class="skeleton skeleton--pulse skeleton-text skeleton-text--xs"
            style="width: 60px;"
          ></div>
          <div
            class="skeleton skeleton--pulse skeleton-text skeleton-text--xs"
            style="width: 60px;"
          ></div>
        </div>
      </div>
    </div>

    <!-- Réponse -->
    <div
      class="skeleton-comment"
      style="margin-left: 4rem; margin-top: 0.5rem;"
    >
      <div
        class="skeleton skeleton--pulse skeleton-circle skeleton-circle--sm"
      ></div>
      <div style="flex: 1;">
        <div
          class="skeleton skeleton--wave skeleton-text skeleton-text--xs"
          style="width: 100px; margin-bottom: 0.5rem;"
        ></div>
        <div
          class="skeleton skeleton--wave skeleton-text skeleton-text--sm"
        ></div>
        <div
          class="skeleton skeleton--wave skeleton-text skeleton-text--sm skeleton-text--short"
        ></div>
      </div>
    </div>
  </div>

  <!-- Comment 3 -->
  <div class="skeleton-comment">
    <div
      class="skeleton skeleton--pulse skeleton-circle skeleton-circle--md"
    ></div>
    <div style="flex: 1;">
      <div
        class="skeleton skeleton--wave skeleton-text skeleton-text--sm"
        style="width: 120px; margin-bottom: 0.5rem;"
      ></div>
      <div class="skeleton skeleton--wave skeleton-text"></div>
      <div class="skeleton skeleton--wave skeleton-text"></div>
      <div
        class="skeleton skeleton--wave skeleton-text skeleton-text--short"
      ></div>
      <div style="display: flex; gap: 1rem; margin-top: 0.75rem;">
        <div
          class="skeleton skeleton--pulse skeleton-text skeleton-text--xs"
          style="width: 60px;"
        ></div>
        <div
          class="skeleton skeleton--pulse skeleton-text skeleton-text--xs"
          style="width: 60px;"
        ></div>
      </div>
    </div>
  </div>
</div>
```

### Exemple 5 : Dashboard loading

```html
<div style="padding: 2rem; max-width: 1200px; margin: 0 auto;">
  <!-- Header -->
  <div
    style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 2rem;"
  >
    <div>
      <div
        class="skeleton skeleton--wave skeleton-text skeleton-text--2xl"
        style="width: 250px; margin-bottom: 0.5rem;"
      ></div>
      <div
        class="skeleton skeleton--wave skeleton-text"
        style="width: 180px;"
      ></div>
    </div>
    <div
      class="skeleton skeleton--pulse skeleton-square"
      style="--skeleton-size: 48px; border-radius: 0.5rem;"
    ></div>
  </div>

  <!-- Stats cards -->
  <div
    style="display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 1.5rem; margin-bottom: 2rem;"
  >
    <div class="skeleton-card">
      <div
        class="skeleton skeleton--wave skeleton-text skeleton-text--sm"
        style="width: 100px; margin-bottom: 0.75rem;"
      ></div>
      <div
        class="skeleton skeleton--pulse skeleton-text skeleton-text--2xl"
        style="width: 120px; margin-bottom: 0.5rem;"
      ></div>
      <div
        class="skeleton skeleton--wave skeleton-text skeleton-text--xs"
        style="width: 80px;"
      ></div>
    </div>

    <div class="skeleton-card">
      <div
        class="skeleton skeleton--wave skeleton-text skeleton-text--sm"
        style="width: 100px; margin-bottom: 0.75rem;"
      ></div>
      <div
        class="skeleton skeleton--pulse skeleton-text skeleton-text--2xl"
        style="width: 120px; margin-bottom: 0.5rem;"
      ></div>
      <div
        class="skeleton skeleton--wave skeleton-text skeleton-text--xs"
        style="width: 80px;"
      ></div>
    </div>

    <div class="skeleton-card">
      <div
        class="skeleton skeleton--wave skeleton-text skeleton-text--sm"
        style="width: 100px; margin-bottom: 0.75rem;"
      ></div>
      <div
        class="skeleton skeleton--pulse skeleton-text skeleton-text--2xl"
        style="width: 120px; margin-bottom: 0.5rem;"
      ></div>
      <div
        class="skeleton skeleton--wave skeleton-text skeleton-text--xs"
        style="width: 80px;"
      ></div>
    </div>

    <div class="skeleton-card">
      <div
        class="skeleton skeleton--wave skeleton-text skeleton-text--sm"
        style="width: 100px; margin-bottom: 0.75rem;"
      ></div>
      <div
        class="skeleton skeleton--pulse skeleton-text skeleton-text--2xl"
        style="width: 120px; margin-bottom: 0.5rem;"
      ></div>
      <div
        class="skeleton skeleton--wave skeleton-text skeleton-text--xs"
        style="width: 80px;"
      ></div>
    </div>
  </div>

  <!-- Chart placeholder -->
  <div class="skeleton-card">
    <div
      class="skeleton skeleton--wave skeleton-text skeleton-text--lg"
      style="width: 200px; margin-bottom: 1rem;"
    ></div>
    <div
      class="skeleton skeleton--wave skeleton-rectangle"
      style="height: 300px;"
    ></div>
  </div>

  <!-- Recent activity -->
  <div class="skeleton-card" style="margin-top: 2rem;">
    <div
      class="skeleton skeleton--wave skeleton-text skeleton-text--lg"
      style="width: 180px; margin-bottom: 1.5rem;"
    ></div>

    <div class="skeleton-list">
      <div class="skeleton-media">
        <div
          class="skeleton skeleton--pulse skeleton-circle skeleton-circle--sm"
        ></div>
        <div class="skeleton-content">
          <div class="skeleton skeleton--wave skeleton-text"></div>
          <div
            class="skeleton skeleton--wave skeleton-text skeleton-text--xs"
            style="width: 100px; margin-top: 0.25rem;"
          ></div>
        </div>
      </div>

      <div class="skeleton-media">
        <div
          class="skeleton skeleton--pulse skeleton-circle skeleton-circle--sm"
        ></div>
        <div class="skeleton-content">
          <div class="skeleton skeleton--wave skeleton-text"></div>
          <div
            class="skeleton skeleton--wave skeleton-text skeleton-text--xs"
            style="width: 100px; margin-top: 0.25rem;"
          ></div>
        </div>
      </div>

      <div class="skeleton-media">
        <div
          class="skeleton skeleton--pulse skeleton-circle skeleton-circle--sm"
        ></div>
        <div class="skeleton-content">
          <div class="skeleton skeleton--wave skeleton-text"></div>
          <div
            class="skeleton skeleton--wave skeleton-text skeleton-text--xs"
            style="width: 100px; margin-top: 0.25rem;"
          ></div>
        </div>
      </div>
    </div>
  </div>
</div>
```

### Exemple 6 : Table loading

```html
<div
  class="skeleton-card"
  style="max-width: 1000px; margin: 2rem auto; padding: 0; overflow: hidden;"
>
  <!-- Table header -->
  <div
    style="display: grid; grid-template-columns: 3fr 2fr 1fr 1fr; gap: 1rem; padding: 1rem; background: #f9fafb; border-bottom: 1px solid #e5e7eb;"
  >
    <div
      class="skeleton skeleton--pulse skeleton-text skeleton-text--sm"
      style="width: 100px;"
    ></div>
    <div
      class="skeleton skeleton--pulse skeleton-text skeleton-text--sm"
      style="width: 80px;"
    ></div>
    <div
      class="skeleton skeleton--pulse skeleton-text skeleton-text--sm"
      style="width: 60px;"
    ></div>
    <div
      class="skeleton skeleton--pulse skeleton-text skeleton-text--sm"
      style="width: 70px;"
    ></div>
  </div>

  <!-- Table rows -->
  <div style="padding: 1rem;">
    <!-- Row 1 -->
    <div
      style="display: grid; grid-template-columns: 3fr 2fr 1fr 1fr; gap: 1rem; align-items: center; padding: 1rem 0; border-bottom: 1px solid #f3f4f6;"
    >
      <div class="skeleton-media" style="gap: 0.75rem;">
        <div
          class="skeleton skeleton--pulse skeleton-circle skeleton-circle--sm"
        ></div>
        <div class="skeleton skeleton--wave skeleton-text"></div>
      </div>
      <div class="skeleton skeleton--wave skeleton-text"></div>
      <div
        class="skeleton skeleton--pulse skeleton-square"
        style="--skeleton-size: 60px; border-radius: 9999px;"
      ></div>
      <div
        class="skeleton skeleton--pulse skeleton-square"
        style="--skeleton-size: 32px;"
      ></div>
    </div>

    <!-- Row 2 -->
    <div
      style="display: grid; grid-template-columns: 3fr 2fr 1fr 1fr; gap: 1rem; align-items: center; padding: 1rem 0; border-bottom: 1px solid #f3f4f6;"
    >
      <div class="skeleton-media" style="gap: 0.75rem;">
        <div
          class="skeleton skeleton--pulse skeleton-circle skeleton-circle--sm"
        ></div>
        <div class="skeleton skeleton--wave skeleton-text"></div>
      </div>
      <div class="skeleton skeleton--wave skeleton-text"></div>
      <div
        class="skeleton skeleton--pulse skeleton-square"
        style="--skeleton-size: 60px; border-radius: 9999px;"
      ></div>
      <div
        class="skeleton skeleton--pulse skeleton-square"
        style="--skeleton-size: 32px;"
      ></div>
    </div>

    <!-- Row 3 -->
    <div
      style="display: grid; grid-template-columns: 3fr 2fr 1fr 1fr; gap: 1rem; align-items: center; padding: 1rem 0; border-bottom: 1px solid #f3f4f6;"
    >
      <div class="skeleton-media" style="gap: 0.75rem;">
        <div
          class="skeleton skeleton--pulse skeleton-circle skeleton-circle--sm"
        ></div>
        <div class="skeleton skeleton--wave skeleton-text"></div>
      </div>
      <div class="skeleton skeleton--wave skeleton-text"></div>
      <div
        class="skeleton skeleton--pulse skeleton-square"
        style="--skeleton-size: 60px; border-radius: 9999px;"
      ></div>
      <div
        class="skeleton skeleton--pulse skeleton-square"
        style="--skeleton-size: 32px;"
      ></div>
    </div>

    <!-- Row 4 -->
    <div
      style="display: grid; grid-template-columns: 3fr 2fr 1fr 1fr; gap: 1rem; align-items: center; padding: 1rem 0; border-bottom: 1px solid #f3f4f6;"
    >
      <div class="skeleton-media" style="gap: 0.75rem;">
        <div
          class="skeleton skeleton--pulse skeleton-circle skeleton-circle--sm"
        ></div>
        <div class="skeleton skeleton--wave skeleton-text"></div>
      </div>
      <div class="skeleton skeleton--wave skeleton-text"></div>
      <div
        class="skeleton skeleton--pulse skeleton-square"
        style="--skeleton-size: 60px; border-radius: 9999px;"
      ></div>
      <div
        class="skeleton skeleton--pulse skeleton-square"
        style="--skeleton-size: 32px;"
      ></div>
    </div>

    <!-- Row 5 -->
    <div
      style="display: grid; grid-template-columns: 3fr 2fr 1fr 1fr; gap: 1rem; align-items: center; padding: 1rem 0;"
    >
      <div class="skeleton-media" style="gap: 0.75rem;">
        <div
          class="skeleton skeleton--pulse skeleton-circle skeleton-circle--sm"
        ></div>
        <div class="skeleton skeleton--wave skeleton-text"></div>
      </div>
      <div class="skeleton skeleton--wave skeleton-text"></div>
      <div
        class="skeleton skeleton--pulse skeleton-square"
        style="--skeleton-size: 60px; border-radius: 9999px;"
      ></div>
      <div
        class="skeleton skeleton--pulse skeleton-square"
        style="--skeleton-size: 32px;"
      ></div>
    </div>
  </div>
</div>
```

## 🎨 Personnalisation avancée

### Couleurs personnalisées

```html
<div
  class="skeleton skeleton--wave skeleton-text"
  style="--skeleton-bg: #dbeafe; --skeleton-highlight: #eff6ff"
>
  Skeleton bleu
</div>
```

### Animation plus rapide

```html
<div
  class="skeleton skeleton--wave skeleton-rectangle"
  style="--skeleton-animation-duration: 1s"
>
  Animation rapide (1s)
</div>
```

### Combiner pulse et wave

```scss
.skeleton--combo {
  animation: skeleton-pulse 1.5s ease-in-out infinite;

  &::after {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: linear-gradient(
      90deg,
      transparent 0%,
      rgba(255, 255, 255, 0.3) 50%,
      transparent 100%
    );
    transform: translateX(-100%);
    animation: skeleton-wave 1.5s ease-in-out infinite;
  }
}
```

### Skeleton avec gradient

```scss
.skeleton--gradient {
  background: linear-gradient(
    135deg,
    var(--skeleton-bg) 0%,
    var(--skeleton-highlight) 50%,
    var(--skeleton-bg) 100%
  );
  background-size: 200% 200%;
  animation: skeleton-gradient 2s ease-in-out infinite;
}

@keyframes skeleton-gradient {
  0%,
  100% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
}
```

## 🎯 Cas d'usage courants

### 1. Chargement initial de page

```html
<div class="is-loading">
  <div class="skeleton skeleton--wave skeleton-rectangle"></div>
  <div class="content">
    <img src="image.jpg" alt="Image réelle" />
  </div>
</div>
```

### 2. Infinite scroll (chargement progressif)

```html
<div id="posts-container">
  <!-- Posts existants -->
</div>

<!-- Skeletons pour le loading -->
<div id="loading-skeletons" class="skeleton-list" style="display: none;">
  <div class="skeleton-card">...</div>
  <div class="skeleton-card">...</div>
</div>
```

### 3. Lazy loading d'images

```html
<div class="skeleton skeleton--wave skeleton-rectangle skeleton-aspect-video">
  <img data-src="image.jpg" class="lazy-image" />
</div>
```

### 4. Formulaire en cours de soumission

```html
<form class="is-submitting">
  <div class="skeleton skeleton--pulse skeleton-text"></div>
  <div class="skeleton skeleton--pulse skeleton-text"></div>
  <div
    class="skeleton skeleton--pulse skeleton-square"
    style="--skeleton-size: 100px; margin-top: 1rem;"
  ></div>
</form>
```

### 5. Chat messages loading

```html
<div class="skeleton-comment">
  <div
    class="skeleton skeleton--pulse skeleton-circle skeleton-circle--sm"
  ></div>
  <div style="flex: 1;">
    <div class="skeleton skeleton--wave skeleton-text"></div>
    <div
      class="skeleton skeleton--wave skeleton-text skeleton-text--short"
    ></div>
  </div>
</div>
```

## 🔧 Combinaison avec autres utilitaires

### Avec Rounded

```html
<div class="skeleton skeleton--wave skeleton-rectangle rounded-2xl">
  Rectangle très arrondi
</div>
```

### Avec Shadow Wrapper

```html
<div class="skeleton-card shadow-wrapper shadow-wrapper--lg">
  Card skeleton avec ombre
</div>
```

### Avec Glass Effect (pour overlay)

```html
<div class="glass-effect glass-effect--light">
  <div class="skeleton skeleton--pulse skeleton-text"></div>
  <div class="skeleton skeleton--pulse skeleton-text"></div>
</div>
```

### Avec Grid Wrapper

```html
<div class="grid-wrapper" style="--cols: 3; gap: 1.5rem;">
  <div class="skeleton skeleton--wave skeleton-square"></div>
  <div class="skeleton skeleton--wave skeleton-square"></div>
  <div class="skeleton skeleton--wave skeleton-square"></div>
</div>
```

## 📱 Comportement responsive

### Adapter la taille sur mobile

```scss
@media (max-width: 768px) {
  .skeleton-circle--lg {
    width: 3rem;
    height: 3rem;
  }

  .skeleton-rectangle--lg {
    height: 10rem;
  }

  .skeleton-grid {
    grid-template-columns: 1fr;
  }
}
```

### Réduire le nombre de skeletons sur mobile

```html
<div class="skeleton-list">
  <div class="skeleton-card">Item 1</div>
  <div class="skeleton-card">Item 2</div>
  <div class="skeleton-card hide-mobile">Item 3</div>
  <div class="skeleton-card hide-mobile">Item 4</div>
</div>

<style>
  @media (max-width: 768px) {
    .hide-mobile {
      display: none;
    }
  }
</style>
```

## ⚡ Performance & Bonnes pratiques

### ✅ À faire

```html
<!-- Bon : Utiliser wave (GPU-accelerated) -->
<div class="skeleton skeleton--wave">
  <!-- Bon : Nombre limité de skeletons -->
  <div class="skeleton-list">
    <!-- 5-10 items maximum -->
  </div>

  <!-- Bon : Structure simple -->
  <div class="skeleton-card">
    <div class="skeleton skeleton--wave skeleton-rectangle"></div>
    <div class="skeleton skeleton--wave skeleton-text"></div>
  </div>

  <!-- Bon : Désactiver pour prefers-reduced-motion -->
  @media (prefers-reduced-motion: reduce) { }
</div>
```

### ❌ À éviter

```html
<!-- Mauvais : Trop de skeletons imbriqués -->
<div class="skeleton">
  <div class="skeleton">
    <div class="skeleton">
      <div class="skeleton"></div>
    </div>
  </div>
</div>

<!-- Mauvais : Animation trop rapide -->
<div style="--skeleton-animation-duration: 0.3s">
  <!-- Mauvais : Trop de détails dans le skeleton -->
  <!-- Le skeleton doit être une approximation simple -->

  <!-- Mauvais : Oublier le loading state -->
  <div>
    <img src="image.jpg" />
    <!-- Pas de fallback skeleton -->
  </div>
</div>
```

### Optimisations

```scss
// ✅ Utiliser transform au lieu de left/right
@keyframes skeleton-wave {
  0% {
    transform: translateX(-100%);
  }
  100% {
    transform: translateX(100%);
  }
}

// ✅ Réduire la complexité des gradients
.skeleton--wave::after {
  background: linear-gradient(
    90deg,
    transparent,
    var(--skeleton-highlight),
    transparent
  );
  // Simple = plus performant
}

// ✅ Utiliser will-change pour animation complexe
.skeleton--wave::after {
  will-change: transform;
}
```

### JavaScript pour toggle loading state

```javascript
// Bon pattern pour gérer le loading
function showSkeleton(container) {
  container.classList.add("is-loading");
  container.classList.remove("is-loaded");
}

function hideSkeleton(container) {
  container.classList.remove("is-loading");
  container.classList.add("is-loaded");
}

// Usage
const container = document.querySelector("#content");

// Commencer le chargement
showSkeleton(container);

// Fetch data
fetch("/api/data")
  .then((response) => response.json())
  .then((data) => {
    // Remplir le contenu
    renderContent(data);
    // Cacher le skeleton
    hideSkeleton(container);
  });
```

## 🌐 Compatibilité navigateurs

| Navigateur | Version minimale | Support    |
| ---------- | ---------------- | ---------- |
| Chrome     | 43+              | ✅ Complet |
| Firefox    | 16+              | ✅ Complet |
| Safari     | 9+               | ✅ Complet |
| Edge       | 12+              | ✅ Complet |
| Opera      | 30+              | ✅ Complet |

**Note** : Les animations CSS sont très bien supportées. Pour IE11, les skeletons fonctionnent mais sans animation.

## 🐛 Troubleshooting

### Problème : L'animation ne s'affiche pas

**Solution** : Vérifiez que `overflow: hidden` est présent

```css
.skeleton--wave {
  overflow: hidden; /* Nécessaire pour l'animation */
  position: relative;
}
```

### Problème : Le contenu est visible à travers le skeleton

**Solution** : Forcez la visibilité des enfants

```css
.skeleton * {
  visibility: hidden !important;
}
```

### Problème : Le skeleton ne remplit pas l'espace

**Solution** : Donnez des dimensions explicites

```css
.skeleton-rectangle {
  width: 100%;
  height: 200px; /* Hauteur explicite */
}
```

### Problème : Animation saccadée

**Solution** : Utilisez will-change

```css
.skeleton--wave::after {
  will-change: transform;
}
```

### Problème : Le skeleton clignote au chargement

**Solution** : Préchargez l'état de loading

```html
<div class="is-loading">
  <!-- Skeleton visible immédiatement -->
  <div class="skeleton skeleton--wave skeleton-rectangle"></div>
</div>
```

## 📦 Classes complètes disponibles

```scss
// Base
.skeleton {
  /* Base skeleton */
}

// Animations
.skeleton--wave {
  /* Wave animation */
}
.skeleton--pulse {
  /* Pulse animation */
}

// Types
.skeleton-text {
  /* Ligne de texte */
}
.skeleton-circle {
  /* Avatar circulaire */
}
.skeleton-rectangle {
  /* Image placeholder */
}
.skeleton-square {
  /* Carré */
}

// Tailles text
.skeleton-text--xs {
  /* 0.75rem */
}
.skeleton-text--sm {
  /* 0.875rem */
}
.skeleton-text--md {
  /* 1rem */
}
.skeleton-text--lg {
  /* 1.25rem */
}
.skeleton-text--xl {
  /* 1.5rem */
}
.skeleton-text--2xl {
  /* 2rem */
}

// Largeurs text
.skeleton-text--short {
  /* 60% */
}
.skeleton-text--medium {
  /* 80% */
}
.skeleton-text--long {
  /* 95% */
}

// Tailles circle
.skeleton-circle--sm {
  /* 2rem */
}
.skeleton-circle--md {
  /* 3rem */
}
.skeleton-circle--lg {
  /* 4rem */
}
.skeleton-circle--xl {
  /* 6rem */
}

// Tailles rectangle
.skeleton-rectangle--sm {
  /* 8rem */
}
.skeleton-rectangle--md {
  /* 12rem */
}
.skeleton-rectangle--lg {
  /* 16rem */
}
.skeleton-rectangle--xl {
  /* 20rem */
}

// Aspects ratio
.skeleton-aspect-square {
  /* 1:1 */
}
.skeleton-aspect-video {
  /* 16:9 */
}
.skeleton-aspect-portrait {
  /* 3:4 */
}
.skeleton-aspect-wide {
  /* 21:9 */
}

// Composants
.skeleton-card {
  /* Card container */
}
.skeleton-media {
  /* Avatar + text */
}
.skeleton-profile {
  /* Profile layout */
}
.skeleton-comment {
  /* Comment layout */
}

// Layouts
.skeleton-grid {
  /* Grid layout */
}
.skeleton-list {
  /* List layout */
}

// Thèmes
.skeleton--light {
  /* Light mode */
}
.skeleton--dark {
  /* Dark mode */
}
.skeleton--white {
  /* White theme */
}

// States
.is-loading {
  /* Show skeleton */
}
.is-loaded {
  /* Show content */
}
```

## 🎓 Ressources complémentaires

- [Skeleton Screens - UX Best Practices](https://www.nngroup.com/articles/skeleton-screens/)
- [CSS Animation - MDN](https://developer.mozilla.org/fr/docs/Web/CSS/animation)
- [React Content Loader](https://skeletonreact.com/)
- [Loading.io](https://loading.io/)

## 📝 Changelog

- **v1.0** - Version initiale avec wave et pulse animations
- **v1.1** - Ajout des composants préfabriqués (card, media, profile)
- **v1.2** - Ajout des aspects ratio et thèmes
- **v1.3** - Support du dark mode
- **v1.4** - Optimisations performance
- **v1.5** - Ajout des layouts (grid, list)

---

**Made with ❤️ for better loading experiences**
