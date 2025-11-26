# Rounded Utility

> Système de border-radius cohérent pour arrondir les coins de vos éléments avec élégance

## 📋 Description

**Rounded** est un utilitaire CSS qui fournit un système complet et cohérent pour gérer les `border-radius` (coins arrondis) de vos éléments. De légèrement arrondis à parfaitement circulaires, cet utilitaire couvre tous les cas d'usage avec des classes prédéfinies et des variables CSS personnalisables.

### ✨ Caractéristiques principales

- 📐 **Échelle cohérente** : De `none` (0) à `full` (circle)
- 🎯 **Contrôle précis** : Arrondir des coins spécifiques
- 🔧 **Variables CSS** : Personnalisation via variables
- ⚡ **Performance** : CSS natif léger
- 🎨 **Classes intuitives** : Nomenclature facile à mémoriser
- 📱 **Responsive** : Radius adaptatifs selon le viewport
- 🔄 **Combinable** : Fonctionne avec tous les éléments

## 🚀 Installation

### Code SCSS

```scss
// _rounded.scss

// Échelle de border-radius (inspirée de Tailwind)
$radius-scale: (
  "none": 0,
  "sm": 0.125rem,
  // 2px
  "default": 0.25rem,
  // 4px
  "md": 0.375rem,
  // 6px
  "lg": 0.5rem,
  // 8px
  "xl": 0.75rem,
  // 12px
  "2xl": 1rem,
  // 16px
  "3xl": 1.5rem,
  // 24px
  "full": 9999px // Circle/pill,
);

.rounded {
  // Variable par défaut
  --radius: 0.25rem; // 4px (défaut)
  --radius-tl: var(--radius); // Top-left
  --radius-tr: var(--radius); // Top-right
  --radius-br: var(--radius); // Bottom-right
  --radius-bl: var(--radius); // Bottom-left

  border-radius: var(--radius-tl) var(--radius-tr) var(--radius-br) var(
      --radius-bl
    );
}

// Variantes de taille prédéfinies (tous les coins)
.rounded-none {
  border-radius: 0;
}

.rounded-sm {
  border-radius: 0.125rem; // 2px
}

.rounded {
  border-radius: 0.25rem; // 4px (défaut)
}

.rounded-md {
  border-radius: 0.375rem; // 6px
}

.rounded-lg {
  border-radius: 0.5rem; // 8px
}

.rounded-xl {
  border-radius: 0.75rem; // 12px
}

.rounded-2xl {
  border-radius: 1rem; // 16px
}

.rounded-3xl {
  border-radius: 1.5rem; // 24px
}

.rounded-full {
  border-radius: 9999px; // Circle/pill
}

// Variantes par côté
.rounded-t-none {
  border-top-left-radius: 0;
  border-top-right-radius: 0;
}
.rounded-t-sm {
  border-top-left-radius: 0.125rem;
  border-top-right-radius: 0.125rem;
}
.rounded-t {
  border-top-left-radius: 0.25rem;
  border-top-right-radius: 0.25rem;
}
.rounded-t-md {
  border-top-left-radius: 0.375rem;
  border-top-right-radius: 0.375rem;
}
.rounded-t-lg {
  border-top-left-radius: 0.5rem;
  border-top-right-radius: 0.5rem;
}
.rounded-t-xl {
  border-top-left-radius: 0.75rem;
  border-top-right-radius: 0.75rem;
}
.rounded-t-2xl {
  border-top-left-radius: 1rem;
  border-top-right-radius: 1rem;
}
.rounded-t-3xl {
  border-top-left-radius: 1.5rem;
  border-top-right-radius: 1.5rem;
}
.rounded-t-full {
  border-top-left-radius: 9999px;
  border-top-right-radius: 9999px;
}

.rounded-r-none {
  border-top-right-radius: 0;
  border-bottom-right-radius: 0;
}
.rounded-r-sm {
  border-top-right-radius: 0.125rem;
  border-bottom-right-radius: 0.125rem;
}
.rounded-r {
  border-top-right-radius: 0.25rem;
  border-bottom-right-radius: 0.25rem;
}
.rounded-r-md {
  border-top-right-radius: 0.375rem;
  border-bottom-right-radius: 0.375rem;
}
.rounded-r-lg {
  border-top-right-radius: 0.5rem;
  border-bottom-right-radius: 0.5rem;
}
.rounded-r-xl {
  border-top-right-radius: 0.75rem;
  border-bottom-right-radius: 0.75rem;
}
.rounded-r-2xl {
  border-top-right-radius: 1rem;
  border-bottom-right-radius: 1rem;
}
.rounded-r-3xl {
  border-top-right-radius: 1.5rem;
  border-bottom-right-radius: 1.5rem;
}
.rounded-r-full {
  border-top-right-radius: 9999px;
  border-bottom-right-radius: 9999px;
}

.rounded-b-none {
  border-bottom-right-radius: 0;
  border-bottom-left-radius: 0;
}
.rounded-b-sm {
  border-bottom-right-radius: 0.125rem;
  border-bottom-left-radius: 0.125rem;
}
.rounded-b {
  border-bottom-right-radius: 0.25rem;
  border-bottom-left-radius: 0.25rem;
}
.rounded-b-md {
  border-bottom-right-radius: 0.375rem;
  border-bottom-left-radius: 0.375rem;
}
.rounded-b-lg {
  border-bottom-right-radius: 0.5rem;
  border-bottom-left-radius: 0.5rem;
}
.rounded-b-xl {
  border-bottom-right-radius: 0.75rem;
  border-bottom-left-radius: 0.75rem;
}
.rounded-b-2xl {
  border-bottom-right-radius: 1rem;
  border-bottom-left-radius: 1rem;
}
.rounded-b-3xl {
  border-bottom-right-radius: 1.5rem;
  border-bottom-left-radius: 1.5rem;
}
.rounded-b-full {
  border-bottom-right-radius: 9999px;
  border-bottom-left-radius: 9999px;
}

.rounded-l-none {
  border-top-left-radius: 0;
  border-bottom-left-radius: 0;
}
.rounded-l-sm {
  border-top-left-radius: 0.125rem;
  border-bottom-left-radius: 0.125rem;
}
.rounded-l {
  border-top-left-radius: 0.25rem;
  border-bottom-left-radius: 0.25rem;
}
.rounded-l-md {
  border-top-left-radius: 0.375rem;
  border-bottom-left-radius: 0.375rem;
}
.rounded-l-lg {
  border-top-left-radius: 0.5rem;
  border-bottom-left-radius: 0.5rem;
}
.rounded-l-xl {
  border-top-left-radius: 0.75rem;
  border-bottom-left-radius: 0.75rem;
}
.rounded-l-2xl {
  border-top-left-radius: 1rem;
  border-bottom-left-radius: 1rem;
}
.rounded-l-3xl {
  border-top-left-radius: 1.5rem;
  border-bottom-left-radius: 1.5rem;
}
.rounded-l-full {
  border-top-left-radius: 9999px;
  border-bottom-left-radius: 9999px;
}

// Variantes par coin individuel
.rounded-tl-none {
  border-top-left-radius: 0;
}
.rounded-tl-sm {
  border-top-left-radius: 0.125rem;
}
.rounded-tl {
  border-top-left-radius: 0.25rem;
}
.rounded-tl-md {
  border-top-left-radius: 0.375rem;
}
.rounded-tl-lg {
  border-top-left-radius: 0.5rem;
}
.rounded-tl-xl {
  border-top-left-radius: 0.75rem;
}
.rounded-tl-2xl {
  border-top-left-radius: 1rem;
}
.rounded-tl-3xl {
  border-top-left-radius: 1.5rem;
}
.rounded-tl-full {
  border-top-left-radius: 9999px;
}

.rounded-tr-none {
  border-top-right-radius: 0;
}
.rounded-tr-sm {
  border-top-right-radius: 0.125rem;
}
.rounded-tr {
  border-top-right-radius: 0.25rem;
}
.rounded-tr-md {
  border-top-right-radius: 0.375rem;
}
.rounded-tr-lg {
  border-top-right-radius: 0.5rem;
}
.rounded-tr-xl {
  border-top-right-radius: 0.75rem;
}
.rounded-tr-2xl {
  border-top-right-radius: 1rem;
}
.rounded-tr-3xl {
  border-top-right-radius: 1.5rem;
}
.rounded-tr-full {
  border-top-right-radius: 9999px;
}

.rounded-br-none {
  border-bottom-right-radius: 0;
}
.rounded-br-sm {
  border-bottom-right-radius: 0.125rem;
}
.rounded-br {
  border-bottom-right-radius: 0.25rem;
}
.rounded-br-md {
  border-bottom-right-radius: 0.375rem;
}
.rounded-br-lg {
  border-bottom-right-radius: 0.5rem;
}
.rounded-br-xl {
  border-bottom-right-radius: 0.75rem;
}
.rounded-br-2xl {
  border-bottom-right-radius: 1rem;
}
.rounded-br-3xl {
  border-bottom-right-radius: 1.5rem;
}
.rounded-br-full {
  border-bottom-right-radius: 9999px;
}

.rounded-bl-none {
  border-bottom-left-radius: 0;
}
.rounded-bl-sm {
  border-bottom-left-radius: 0.125rem;
}
.rounded-bl {
  border-bottom-left-radius: 0.25rem;
}
.rounded-bl-md {
  border-bottom-left-radius: 0.375rem;
}
.rounded-bl-lg {
  border-bottom-left-radius: 0.5rem;
}
.rounded-bl-xl {
  border-bottom-left-radius: 0.75rem;
}
.rounded-bl-2xl {
  border-bottom-left-radius: 1rem;
}
.rounded-bl-3xl {
  border-bottom-left-radius: 1.5rem;
}
.rounded-bl-full {
  border-bottom-left-radius: 9999px;
}

// Variantes responsive fluides
.rounded-fluid {
  border-radius: clamp(0.25rem, 2vw, 1.5rem);
}

// Variante avec transition
.rounded-transition {
  transition: border-radius 0.3s ease;
}
```

### Import dans votre projet

```scss
// Dans styles.scss
@import "utilities/rounded";
```

## 💡 Utilisation de base

### Exemple 1 : Card arrondie simple

```html
<div
  class="card rounded-lg shadow-wrapper shadow-wrapper--md"
  style="padding: 2rem"
>
  <h3>Card arrondie</h3>
  <p>Avec rounded-lg (8px)</p>
</div>
```

### Exemple 2 : Button avec coins très arrondis

```html
<button class="btn rounded-full" style="padding: 1rem 2rem">Button Pill</button>
```

### Exemple 3 : Image avec coins arrondis

```html
<img src="image.jpg" alt="Image" class="rounded-xl" style="width: 300px" />
```

### Exemple 4 : Card avec header arrondi en haut uniquement

```html
<div class="card shadow-wrapper shadow-wrapper--md">
  <div
    class="card-header gradient-bg gradient-bg--blue rounded-t-lg"
    style="padding: 1.5rem; color: white"
  >
    <h3>Header arrondi</h3>
  </div>
  <div class="card-body" style="padding: 1.5rem">
    <p>Body avec coins carrés en haut</p>
  </div>
</div>
```

## 📊 Paramètres

| Variable      | Type   | Défaut          | Description            |
| ------------- | ------ | --------------- | ---------------------- |
| `--radius`    | length | `0.25rem`       | Border-radius uniforme |
| `--radius-tl` | length | `var(--radius)` | Coin top-left          |
| `--radius-tr` | length | `var(--radius)` | Coin top-right         |
| `--radius-br` | length | `var(--radius)` | Coin bottom-right      |
| `--radius-bl` | length | `var(--radius)` | Coin bottom-left       |

### Échelle de tailles

| Classe         | Valeur   | Pixels | Usage                   |
| -------------- | -------- | ------ | ----------------------- |
| `rounded-none` | 0        | 0px    | Coins carrés            |
| `rounded-sm`   | 0.125rem | 2px    | Très légèrement arrondi |
| `rounded`      | 0.25rem  | 4px    | Léger (défaut)          |
| `rounded-md`   | 0.375rem | 6px    | Moyen                   |
| `rounded-lg`   | 0.5rem   | 8px    | Prononcé                |
| `rounded-xl`   | 0.75rem  | 12px   | Très prononcé           |
| `rounded-2xl`  | 1rem     | 16px   | Extra arrondi           |
| `rounded-3xl`  | 1.5rem   | 24px   | Ultra arrondi           |
| `rounded-full` | 9999px   | Infini | Circle/Pill             |

### Nomenclature des côtés

| Suffixe | Signification | Coins affectés             |
| ------- | ------------- | -------------------------- |
| `-t`    | Top           | Top-left + Top-right       |
| `-r`    | Right         | Top-right + Bottom-right   |
| `-b`    | Bottom        | Bottom-right + Bottom-left |
| `-l`    | Left          | Top-left + Bottom-left     |
| `-tl`   | Top-left      | Top-left uniquement        |
| `-tr`   | Top-right     | Top-right uniquement       |
| `-br`   | Bottom-right  | Bottom-right uniquement    |
| `-bl`   | Bottom-left   | Bottom-left uniquement     |

## 📚 Exemples détaillés

### Exemple 1 : Gallery d'images avec différents radius

```html
<div class="image-gallery">
  <div class="gallery-item">
    <img src="image1.jpg" alt="Image 1" class="rounded-none" />
    <p>None (0px)</p>
  </div>

  <div class="gallery-item">
    <img src="image2.jpg" alt="Image 2" class="rounded-sm" />
    <p>Small (2px)</p>
  </div>

  <div class="gallery-item">
    <img src="image3.jpg" alt="Image 3" class="rounded" />
    <p>Default (4px)</p>
  </div>

  <div class="gallery-item">
    <img src="image4.jpg" alt="Image 4" class="rounded-md" />
    <p>Medium (6px)</p>
  </div>

  <div class="gallery-item">
    <img src="image5.jpg" alt="Image 5" class="rounded-lg" />
    <p>Large (8px)</p>
  </div>

  <div class="gallery-item">
    <img src="image6.jpg" alt="Image 6" class="rounded-xl" />
    <p>XL (12px)</p>
  </div>

  <div class="gallery-item">
    <img src="image7.jpg" alt="Image 7" class="rounded-2xl" />
    <p>2XL (16px)</p>
  </div>

  <div class="gallery-item">
    <img src="image8.jpg" alt="Image 8" class="rounded-3xl" />
    <p>3XL (24px)</p>
  </div>

  <div class="gallery-item">
    <img src="image9.jpg" alt="Image 9" class="rounded-full" />
    <p>Full (Circle)</p>
  </div>
</div>

<style>
  .image-gallery {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 2rem;
    padding: 2rem;
  }

  .gallery-item {
    text-align: center;
  }

  .gallery-item img {
    width: 100%;
    height: 200px;
    object-fit: cover;
    margin-bottom: 0.5rem;
  }

  .gallery-item p {
    font-size: 0.875rem;
    color: #6b7280;
    margin: 0;
  }
</style>
```

### Exemple 2 : Cards avec coins arrondis variés

```html
<div class="cards-showcase">
  <div class="card shadow-wrapper shadow-wrapper--md rounded-lg">
    <div class="card-image">
      <img src="card1.jpg" alt="Card 1" class="rounded-t-lg" />
    </div>
    <div class="card-content">
      <h3>Card Standard</h3>
      <p>Coins arrondis uniformes (8px)</p>
    </div>
  </div>

  <div class="card shadow-wrapper shadow-wrapper--md rounded-2xl">
    <div class="card-image">
      <img src="card2.jpg" alt="Card 2" class="rounded-t-2xl" />
    </div>
    <div class="card-content">
      <h3>Card Extra Rounded</h3>
      <p>Coins très arrondis (16px)</p>
    </div>
  </div>

  <div class="card shadow-wrapper shadow-wrapper--md rounded-3xl">
    <div class="card-image">
      <img src="card3.jpg" alt="Card 3" class="rounded-t-3xl" />
    </div>
    <div class="card-content">
      <h3>Card Ultra Rounded</h3>
      <p>Coins ultra arrondis (24px)</p>
    </div>
  </div>
</div>

<style>
  .cards-showcase {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2rem;
    padding: 2rem;
  }

  .card {
    background: white;
    overflow: hidden;
  }

  .card-image img {
    width: 100%;
    height: 200px;
    object-fit: cover;
  }

  .card-content {
    padding: 1.5rem;
  }

  .card-content h3 {
    margin: 0 0 0.5rem 0;
  }

  .card-content p {
    margin: 0;
    color: #6b7280;
  }
</style>
```

### Exemple 3 : Buttons avec différents styles

```html
<div class="button-styles">
  <button class="btn rounded-none shadow-wrapper shadow-wrapper--sm">
    Square
  </button>

  <button class="btn rounded shadow-wrapper shadow-wrapper--sm">Default</button>

  <button class="btn rounded-md shadow-wrapper shadow-wrapper--sm">
    Medium
  </button>

  <button class="btn rounded-lg shadow-wrapper shadow-wrapper--sm">
    Large
  </button>

  <button class="btn rounded-xl shadow-wrapper shadow-wrapper--sm">XL</button>

  <button class="btn rounded-2xl shadow-wrapper shadow-wrapper--sm">2XL</button>

  <button class="btn rounded-full shadow-wrapper shadow-wrapper--sm">
    Pill Button
  </button>
</div>

<style>
  .button-styles {
    display: flex;
    flex-wrap: wrap;
    gap: 1rem;
    padding: 2rem;
  }

  .btn {
    padding: 0.75rem 1.5rem;
    background: white;
    border: 1px solid #e5e7eb;
    cursor: pointer;
    font-weight: 600;
    transition: all 0.3s;
  }

  .btn:hover {
    background: #f9fafb;
    transform: translateY(-2px);
  }
</style>
```

### Exemple 4 : Avatars circulaires

```html
<div class="avatar-sizes">
  <img src="avatar1.jpg" alt="Avatar" class="avatar avatar-sm rounded-full" />
  <img src="avatar2.jpg" alt="Avatar" class="avatar avatar-md rounded-full" />
  <img src="avatar3.jpg" alt="Avatar" class="avatar avatar-lg rounded-full" />
  <img src="avatar4.jpg" alt="Avatar" class="avatar avatar-xl rounded-full" />
</div>

<style>
  .avatar-sizes {
    display: flex;
    align-items: center;
    gap: 1.5rem;
    padding: 2rem;
  }

  .avatar {
    object-fit: cover;
  }

  .avatar-sm {
    width: 32px;
    height: 32px;
  }

  .avatar-md {
    width: 48px;
    height: 48px;
  }

  .avatar-lg {
    width: 64px;
    height: 64px;
  }

  .avatar-xl {
    width: 96px;
    height: 96px;
  }
</style>
```

### Exemple 5 : Modal avec coins spécifiques arrondis

```html
<div class="modal-overlay">
  <div class="modal shadow-wrapper shadow-wrapper--2xl rounded-2xl">
    <header class="modal-header gradient-bg gradient-bg--purple rounded-t-2xl">
      <h2>Modal Title</h2>
      <button class="close-btn rounded-full">×</button>
    </header>

    <div class="modal-content">
      <p>Modal avec header arrondi en haut et coins généraux arrondis</p>
    </div>

    <footer class="modal-footer rounded-b-2xl">
      <button class="btn rounded-lg">Cancel</button>
      <button class="btn btn-primary rounded-lg">Confirm</button>
    </footer>
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
  }

  .modal {
    background: white;
    width: 90%;
    max-width: 500px;
    overflow: hidden;
  }

  .modal-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1.5rem;
    color: white;
  }

  .modal-header h2 {
    margin: 0;
  }

  .close-btn {
    width: 32px;
    height: 32px;
    border: none;
    background: rgba(255, 255, 255, 0.2);
    color: white;
    font-size: 1.5rem;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .modal-content {
    padding: 2rem;
  }

  .modal-footer {
    display: flex;
    justify-content: flex-end;
    gap: 0.75rem;
    padding: 1.5rem;
    background: #f9fafb;
  }

  .btn {
    padding: 0.75rem 1.5rem;
    border: 1px solid #e5e7eb;
    background: white;
    cursor: pointer;
    font-weight: 600;
  }

  .btn-primary {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
    border: none;
  }
</style>
```

### Exemple 6 : Tabs avec coins arrondis

```html
<div class="tabs-container">
  <div class="tabs">
    <button class="tab active rounded-t-lg">Dashboard</button>
    <button class="tab rounded-t-lg">Analytics</button>
    <button class="tab rounded-t-lg">Settings</button>
    <button class="tab rounded-t-lg">Profile</button>
  </div>

  <div class="tab-content rounded-lg rounded-tl-none">
    <h3>Dashboard Content</h3>
    <p>Contenu du tab actif avec coins arrondis sauf en haut à gauche</p>
  </div>
</div>

<style>
  .tabs-container {
    padding: 2rem;
  }

  .tabs {
    display: flex;
    gap: 0.25rem;
    margin-bottom: -1px;
  }

  .tab {
    padding: 0.75rem 1.5rem;
    background: #f3f4f6;
    border: 1px solid #e5e7eb;
    border-bottom: none;
    cursor: pointer;
    font-weight: 600;
    color: #6b7280;
    transition: all 0.3s;
  }

  .tab:hover {
    background: #e5e7eb;
  }

  .tab.active {
    background: white;
    color: #111827;
    position: relative;
    z-index: 1;
  }

  .tab-content {
    background: white;
    border: 1px solid #e5e7eb;
    padding: 2rem;
  }

  .tab-content h3 {
    margin: 0 0 1rem 0;
  }

  .tab-content p {
    margin: 0;
    color: #6b7280;
  }
</style>
```

### Exemple 7 : Badges et tags

```html
<div class="badges-demo">
  <span class="badge rounded-full">Full Rounded</span>
  <span class="badge rounded-2xl">2XL Rounded</span>
  <span class="badge rounded-lg">LG Rounded</span>
  <span class="badge rounded-md">MD Rounded</span>
  <span class="badge rounded">Default</span>
  <span class="badge rounded-none">Square</span>
</div>

<style>
  .badges-demo {
    display: flex;
    flex-wrap: wrap;
    gap: 1rem;
    padding: 2rem;
  }

  .badge {
    display: inline-block;
    padding: 0.5rem 1rem;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
    font-size: 0.875rem;
    font-weight: 600;
  }
</style>
```

### Exemple 8 : Input group avec radius asymétriques

```html
<div class="input-groups">
  <div class="input-group">
    <input type="text" class="input rounded-l-lg" placeholder="Search..." />
    <button class="btn-search rounded-r-lg">🔍</button>
  </div>

  <div class="input-group">
    <span class="addon rounded-l-lg">@</span>
    <input type="text" class="input rounded-r-lg" placeholder="username" />
  </div>

  <div class="input-group">
    <input type="text" class="input rounded-l-lg" placeholder="Amount" />
    <span class="addon rounded-r-lg">€</span>
  </div>
</div>

<style>
  .input-groups {
    display: flex;
    flex-direction: column;
    gap: 1.5rem;
    padding: 2rem;
    max-width: 400px;
  }

  .input-group {
    display: flex;
  }

  .input {
    flex: 1;
    padding: 0.75rem 1rem;
    border: 1px solid #d1d5db;
    font-size: 1rem;
  }

  .btn-search,
  .addon {
    padding: 0.75rem 1rem;
    border: 1px solid #d1d5db;
    background: #f9fafb;
    font-weight: 600;
  }

  .btn-search {
    cursor: pointer;
    transition: background 0.3s;
  }

  .btn-search:hover {
    background: #e5e7eb;
  }

  .input-group .input {
    border-left: none;
    border-right: none;
  }

  .input-group .input:first-child {
    border-left: 1px solid #d1d5db;
  }

  .input-group .input:last-child {
    border-right: 1px solid #d1d5db;
  }
</style>
```

## 🎨 Personnalisation avancée

### Radius personnalisé avec variables

```html
<div class="rounded" style="--radius: 2rem; padding: 2rem; background: #f3f4f6">
  Custom radius de 2rem (32px)
</div>
```

### Radius différent par coin

```html
<div
  class="rounded"
  style="--radius-tl: 0; 
            --radius-tr: 1rem; 
            --radius-br: 2rem; 
            --radius-bl: 0.5rem;
            padding: 2rem; 
            background: #667eea; 
            color: white"
>
  Chaque coin avec un radius différent
</div>
```

### Radius responsive

```html
<div
  class="responsive-radius"
  style="padding: 2rem; background: #764ba2; color: white"
>
  Radius qui s'adapte à la taille d'écran
</div>

<style>
  .responsive-radius {
    border-radius: 0.25rem;
  }

  @media (min-width: 640px) {
    .responsive-radius {
      border-radius: 0.5rem;
    }
  }

  @media (min-width: 1024px) {
    .responsive-radius {
      border-radius: 1rem;
    }
  }
</style>
```

### Radius fluide avec clamp

```html
<div
  class="rounded-fluid"
  style="padding: 2rem; background: #10b981; color: white"
>
  Radius fluide qui s'adapte automatiquement
</div>
```

### Animation de radius au hover

```html
<div
  class="animate-radius rounded-lg"
  style="padding: 2rem; background: #3b82f6; color: white"
>
  Hover pour animer le radius
</div>

<style>
  .animate-radius {
    transition: border-radius 0.3s ease;
  }

  .animate-radius:hover {
    border-radius: 2rem;
  }
</style>
```

## 🎯 Cas d'usage courants

### 1. Cards standards

```html
<div class="card rounded-lg shadow-wrapper shadow-wrapper--md">
  Card content
</div>
```

### 2. Buttons

```html
<button class="btn rounded-md">Default Button</button>
<button class="btn rounded-full">Pill Button</button>
```

### 3. Images

```html
<img src="image.jpg" alt="Image" class="rounded-xl" />
```

### 4. Avatars

```html
<img src="avatar.jpg" alt="Avatar" class="rounded-full" />
```

### 5. Inputs

```html
<input type="text" class="rounded-lg" placeholder="Text input" />
```

### 6. Badges/Tags

```html
<span class="badge rounded-full">Badge</span>
```

### 7. Modals

```html
<div class="modal rounded-2xl">Modal content</div>
```

## 🔧 Combinaison avec autres utilitaires

### Avec Shadow Wrapper

```html
<div
  class="rounded-xl shadow-wrapper shadow-wrapper--lg"
  style="padding: 2rem; background: white"
>
  Card avec radius + ombre
</div>
```

### Avec Gradient Background

```html
<div
  class="rounded-2xl gradient-bg gradient-bg--sunset"
  style="padding: 3rem; color: white"
>
  <h2>Gradient avec coins arrondis</h2>
</div>
```

### Avec Glass Effect

```html
<div
  class="rounded-xl glass-effect glass-effect--light shadow-wrapper shadow-wrapper--xl"
  style="padding: 2rem"
>
  Glass effect avec coins arrondis
</div>
```

### Avec Container Fluid

```html
<section class="container-fluid container-fluid--lg">
  <div
    class="rounded-2xl shadow-wrapper shadow-wrapper--md"
    style="padding: 3rem; background: white"
  >
    Container avec card arrondie
  </div>
</section>
```

## 📱 Comportement responsive

### Radius adaptatif par breakpoint

```scss
.card {
  border-radius: 0.25rem; // Mobile : petit

  @media (min-width: 640px) {
    border-radius: 0.5rem; // Tablet : moyen
  }

  @media (min-width: 1024px) {
    border-radius: 1rem; // Desktop : large
  }
}
```

### Radius fluide automatique

```scss
.rounded-fluid {
  border-radius: clamp(0.25rem, 2vw, 1.5rem);
  // Min: 4px, Max: 24px, fluide entre les deux
}
```

## ⚡ Performance & Bonnes pratiques

### ✅ À faire

```html
<!-- Bon : Utiliser l'échelle prédéfinie -->
<div class="rounded-lg">
  <!-- Bon : Radius cohérent dans le design -->
  <button class="rounded-md">Button 1</button>
  <button class="rounded-md">Button 2</button>

  <!-- Bon : Combiner avec overflow hidden -->
  <div class="rounded-xl" style="overflow: hidden">
    <img src="image.jpg" alt="Image" />
  </div>

  <!-- Bon : Radius proportionnel à la taille -->
  <div class="avatar-sm rounded-full"><!-- Petit élément, circle OK --></div>
</div>
```

### ❌ À éviter

```html
<!-- Mauvais : Radius trop grand pour élément petit -->
<button class="rounded-3xl" style="padding: 0.25rem 0.5rem">Tiny</button>

<!-- Mauvais : Radius incohérent -->
<div class="rounded-sm">Item 1</div>
<div class="rounded-2xl">Item 2</div>
<div class="rounded-md">Item 3</div>

<!-- Mauvais : Valeurs arbitraires -->
<div style="border-radius: 7.3px">
  <!-- Mauvais : Trop de variations de radius -->
  .element1 { border-radius: 4px; } .element2 { border-radius: 6px; } .element3
  { border-radius: 9px; } .element4 { border-radius: 11px; }
</div>
```

### Conseils de performance

```scss
// ✅ Border-radius est très performant
.rounded-lg {
  border-radius: 0.5rem;
  // Pas d'impact performance significatif
}

// ✅ Utiliser overflow: hidden si nécessaire
.card {
  border-radius: 1rem;
  overflow: hidden; // Cache le débordement des enfants
}

// ⚠️ Attention avec border-radius + backdrop-filter
.glass-card {
  border-radius: 1rem;
  backdrop-filter: blur(10px); // Peut être coûteux
}
```

## 🌐 Compatibilité navigateurs

| Navigateur | Version minimale | Support    |
| ---------- | ---------------- | ---------- |
| Chrome     | 4+               | ✅ Complet |
| Firefox    | 4+               | ✅ Complet |
| Safari     | 5+               | ✅ Complet |
| Edge       | 12+              | ✅ Complet |
| Opera      | 10.5+            | ✅ Complet |
| IE         | 9+               | ✅ Complet |

**Note** : `border-radius` est une des propriétés CSS les mieux supportées. Aucun préfixe nécessaire pour les navigateurs modernes.

## 🐛 Troubleshooting

### Problème : Les coins ne s'arrondissent pas

**Solution** : Vérifiez overflow

```css
/* Si l'élément parent a overflow visible */
.parent {
  overflow: hidden; /* Nécessaire pour que les enfants respectent le radius */
}

.child {
  border-radius: 1rem;
}
```

### Problème : Image dépasse des coins arrondis

**Solution** : Ajoutez overflow: hidden

```html
<div class="card rounded-lg" style="overflow: hidden">
  <img src="image.jpg" alt="Image" />
</div>
```

### Problème : Radius trop prononcé sur petit élément

**Solution** : Utilisez un radius proportionnel

```html
<!-- ❌ Trop grand -->
<button class="rounded-3xl" style="padding: 0.5rem">Small</button>

<!-- ✅ Proportionnel -->
<button class="rounded-md" style="padding: 0.5rem">Small</button>
```

### Problème : Coins arrondis + bordure bizarre

**Solution** : Assurez-vous que border et radius sont cohérents

```css
.element {
  border: 2px solid #000;
  border-radius: 0.5rem;
  /* Les coins de la bordure suivent automatiquement le radius */
}
```

## 📦 Classes complètes disponibles

```scss
// Tous les coins (uniforme)
.rounded-none     { border-radius: 0; }
.rounded-sm       { border-radius: 0.125rem; }
.rounded          { border-radius: 0.25rem; }
.rounded-md       { border-radius: 0.375rem; }
.rounded-lg       { border-radius: 0.5rem; }
.rounded-xl       { border-radius: 0.75rem; }
.rounded-2xl      { border-radius: 1rem; }
.rounded-3xl      { border-radius: 1.5rem; }
.rounded-full     { border-radius: 9999px; }

// Par côté (t=top, r=right, b=bottom, l=left)
.rounded-t-{size}   { /* Top corners */ }
.rounded-r-{size}   { /* Right corners */ }
.rounded-b-{size}   { /* Bottom corners */ }
.rounded-l-{size}   { /* Left corners */ }

// Par coin individuel (tl, tr, br, bl)
.rounded-tl-{size}  { /* Top-left */ }
.rounded-tr-{size}  { /* Top-right */ }
.rounded-br-{size}  { /* Bottom-right */ }
.rounded-bl-{size}  { /* Bottom-left */ }

// Utilitaires
.rounded-fluid      { /* Fluide avec clamp */ }
.rounded-transition { /* Avec transition */ }
```

## 📐 Guide de sélection de radius

| Type d'élément  | Radius recommandé    | Raison                     |
| --------------- | -------------------- | -------------------------- |
| Cards standards | `rounded-lg` (8px)   | Moderne sans être excessif |
| Buttons         | `rounded-md` (6px)   | Équilibré                  |
| Pill buttons    | `rounded-full`       | Style moderne              |
| Images          | `rounded-xl` (12px)  | Doux et élégant            |
| Avatars         | `rounded-full`       | Standard                   |
| Inputs          | `rounded-md` (6px)   | Cohérent avec buttons      |
| Badges/Tags     | `rounded-full`       | Pill shape                 |
| Modals          | `rounded-2xl` (16px) | Premium look               |
| Containers      | `rounded-xl` (12px)  | Espace important           |

## 🎓 Ressources complémentaires

- [Border Radius - MDN](https://developer.mozilla.org/fr/docs/Web/CSS/border-radius)
- [Border Radius Generator](https://border-radius.com/)
- [Smooth Corners](https://larsenwork.com/easing-gradients/)

## 📝 Changelog

- **v1.0** - Version initiale avec échelle complète
- **v1.1** - Ajout des variantes par côté
- **v1.2** - Ajout des variantes par coin individuel
- **v1.3** - Support des radius fluides avec clamp
- **v1.4** - Ajout de la classe transition

---

**Made with ❤️ for smooth corners**
