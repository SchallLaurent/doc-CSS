# Split Screen Utility

> Créez des layouts à deux colonnes flexibles et responsives en une ligne de CSS

## 📋 Description

**Split Screen** est un utilitaire CSS qui permet de créer facilement des mises en page à deux colonnes (50/50, 30/70, sidebar/content, etc.) avec une gestion responsive automatique. Basé sur CSS Grid et les variables CSS, il offre une flexibilité maximale sans JavaScript.

### ✨ Caractéristiques principales

- 🎯 **Ratios personnalisables** : 50/50, 30/70, 1fr 2fr, 200px auto, etc.
- 📱 **Responsive natif** : Bascule automatiquement en colonne sur mobile
- 🔧 **Variables CSS** : Personnalisation sans modifier le code source
- ⚡ **Performance** : CSS Grid natif, pas de JavaScript
- 🎨 **Gap flexible** : Espacement personnalisable entre les colonnes
- 🔄 **Ordre inversable** : Changez l'ordre des colonnes facilement

## 🚀 Installation

### Code SCSS

```scss
// _split.scss
.split {
  // Variables par défaut
  --split-ratio: 1fr 1fr; // Ratio des colonnes (50/50 par défaut)
  --gap: 2rem; // Espacement entre colonnes
  --breakpoint: 768px; // Point de rupture responsive
  --stack-order: normal; // Ordre en mode mobile (normal | reverse)

  display: grid;
  grid-template-columns: var(--split-ratio);
  gap: var(--gap);
  align-items: start; // Alignement vertical par défaut

  // Mode responsive : empile en colonne sur mobile
  @media (max-width: var(--breakpoint)) {
    grid-template-columns: 1fr;

    &[data-reverse="true"] {
      > :first-child {
        order: 2;
      }
      > :last-child {
        order: 1;
      }
    }
  }
}

// Variantes prédéfinies
.split--sidebar {
  --split-ratio: 250px 1fr;
}

.split--sidebar-right {
  --split-ratio: 1fr 250px;
}

.split--30-70 {
  --split-ratio: 30% 70%;
}

.split--70-30 {
  --split-ratio: 70% 30%;
}

.split--golden {
  --split-ratio: 38.2% 61.8%; // Ratio d'or
}

.split--center {
  align-items: center; // Centre verticalement
}

.split--stretch {
  align-items: stretch; // Étire les colonnes
}
```

### Import dans votre projet

```scss
// Dans styles.scss
@import "utilities/split";
```

## 💡 Utilisation de base

### Exemple 1 : Split 50/50 (défaut)

```html
<div class="split">
  <div>
    <h2>Colonne gauche</h2>
    <p>Contenu de la première colonne</p>
  </div>
  <div>
    <h2>Colonne droite</h2>
    <p>Contenu de la deuxième colonne</p>
  </div>
</div>
```

### Exemple 2 : Layout avec sidebar

```html
<div class="split split--sidebar">
  <aside>
    <nav>
      <a href="#">Menu 1</a>
      <a href="#">Menu 2</a>
      <a href="#">Menu 3</a>
    </nav>
  </aside>
  <main>
    <h1>Contenu principal</h1>
    <p>Lorem ipsum dolor sit amet...</p>
  </main>
</div>
```

### Exemple 3 : Ratio personnalisé

```html
<!-- Split 30/70 avec gap réduit -->
<div class="split" style="--split-ratio: 1fr 2fr; --gap: 1rem">
  <div>Petite colonne</div>
  <div>Grande colonne</div>
</div>
```

## 📊 Paramètres

| Variable        | Type                  | Défaut    | Description                                    |
| --------------- | --------------------- | --------- | ---------------------------------------------- |
| `--split-ratio` | grid-template-columns | `1fr 1fr` | Ratio des deux colonnes                        |
| `--gap`         | length                | `2rem`    | Espacement entre les colonnes                  |
| `--breakpoint`  | length                | `768px`   | Point de rupture pour le mode mobile           |
| `--stack-order` | keyword               | `normal`  | Ordre en mode empilé (non utilisé directement) |

### Valeurs courantes pour `--split-ratio`

```css
/* Égalité */
--split-ratio: 1fr 1fr; /* 50/50 */

/* Pourcentages */
--split-ratio: 30% 70%; /* 30/70 */
--split-ratio: 25% 75%; /* 25/75 */

/* Fractions */
--split-ratio: 1fr 2fr; /* 33/66 */
--split-ratio: 2fr 3fr; /* 40/60 */

/* Sidebar fixe */
--split-ratio: 250px 1fr; /* Sidebar gauche 250px */
--split-ratio: 1fr 300px; /* Sidebar droite 300px */
--split-ratio: 200px auto; /* Sidebar avec auto */

/* Ratio d'or */
--split-ratio: 38.2% 61.8%; /* Golden ratio */

/* Colonnes min/max */
--split-ratio: minmax(200px, 1fr) 2fr; /* Min 200px, max 1fr */
```

## 📚 Exemples détaillés

### Exemple 1 : Hero section avec image

```html
<section class="split split--center" style="--gap: 3rem">
  <div class="hero-content">
    <h1>Bienvenue sur notre site</h1>
    <p>Découvrez nos services innovants</p>
    <button>En savoir plus</button>
  </div>
  <div class="hero-image">
    <img src="hero.jpg" alt="Hero" />
  </div>
</section>

<style>
  .hero-content {
    padding: 2rem;
  }

  .hero-image img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    border-radius: 0.5rem;
  }
</style>
```

### Exemple 2 : Dashboard avec sidebar

```html
<div class="split split--sidebar" style="--breakpoint: 992px">
  <aside class="sidebar">
    <div class="logo">MonApp</div>
    <nav>
      <a href="#" class="active">Dashboard</a>
      <a href="#">Analytics</a>
      <a href="#">Settings</a>
      <a href="#">Profile</a>
    </nav>
  </aside>

  <main class="dashboard-content">
    <header>
      <h1>Dashboard</h1>
      <button>New Item</button>
    </header>
    <div class="stats-grid">
      <!-- Contenu du dashboard -->
    </div>
  </main>
</div>

<style>
  .sidebar {
    background: #1a1a2e;
    color: white;
    padding: 1.5rem;
    border-radius: 0.5rem;
  }

  .dashboard-content {
    padding: 2rem;
  }
</style>
```

### Exemple 3 : Article avec table des matières

```html
<article class="split" style="--split-ratio: 250px 1fr; --gap: 3rem">
  <nav class="toc">
    <h3>Table des matières</h3>
    <ul>
      <li><a href="#intro">Introduction</a></li>
      <li><a href="#features">Fonctionnalités</a></li>
      <li><a href="#usage">Utilisation</a></li>
      <li><a href="#examples">Exemples</a></li>
    </ul>
  </nav>

  <div class="article-content">
    <h1 id="intro">Introduction</h1>
    <p>Lorem ipsum dolor sit amet...</p>

    <h2 id="features">Fonctionnalités</h2>
    <p>Consectetur adipiscing elit...</p>

    <!-- ... reste du contenu -->
  </div>
</article>

<style>
  .toc {
    position: sticky;
    top: 2rem;
    height: fit-content;
  }
</style>
```

### Exemple 4 : Formulaire avec preview

```html
<div class="split split--30-70">
  <form class="form-section">
    <h2>Créer un post</h2>
    <input type="text" placeholder="Titre" />
    <textarea placeholder="Contenu"></textarea>
    <button>Publier</button>
  </form>

  <div class="preview-section">
    <h2>Aperçu</h2>
    <div class="preview-card">
      <!-- Preview en temps réel -->
    </div>
  </div>
</div>
```

### Exemple 5 : Inversement mobile (image d'abord)

```html
<div class="split" data-reverse="true">
  <div class="text-content">
    <h2>Notre histoire</h2>
    <p>Fondée en 2020...</p>
  </div>
  <div class="image-content">
    <img src="story.jpg" alt="Notre histoire" />
  </div>
</div>

<!-- Sur mobile : l'image apparaît EN PREMIER grâce à data-reverse="true" -->
```

## 🎨 Personnalisation avancée

### Différents gaps selon le viewport

```html
<div class="split responsive-gap">
  <div>Colonne 1</div>
  <div>Colonne 2</div>
</div>

<style>
  .responsive-gap {
    --gap: clamp(1rem, 3vw, 3rem);
  }
</style>
```

### Sidebar collapsible

```html
<div class="split" id="collapsible-split" style="--split-ratio: 250px 1fr">
  <aside class="sidebar">
    <button onclick="toggleSidebar()">☰</button>
    <!-- Contenu sidebar -->
  </aside>
  <main>Content</main>
</div>

<style>
  .sidebar.collapsed {
    display: none;
  }

  .sidebar.collapsed ~ main {
    grid-column: 1 / -1;
  }
</style>

<script>
  function toggleSidebar() {
    document.querySelector(".sidebar").classList.toggle("collapsed");
  }
</script>
```

### Hauteur égale avec stretch

```html
<div class="split split--stretch">
  <div class="card">
    <h3>Card courte</h3>
    <p>Peu de contenu</p>
  </div>
  <div class="card">
    <h3>Card longue</h3>
    <p>Beaucoup de contenu...</p>
    <p>Lorem ipsum dolor sit amet...</p>
    <p>Consectetur adipiscing elit...</p>
  </div>
</div>

<!-- Les deux cards auront la même hauteur grâce à split--stretch -->
```

### Breakpoint personnalisé

```html
<!-- Split qui devient vertical à 1024px au lieu de 768px -->
<div class="split" style="--breakpoint: 1024px">
  <div>Colonne 1</div>
  <div>Colonne 2</div>
</div>
```

## 🎯 Cas d'usage courants

### 1. Landing page Hero

```html
<section class="split split--center" style="--split-ratio: 45% 55%">
  <div class="hero-text">
    <h1>Transform Your Business</h1>
    <p>Solutions innovantes pour votre entreprise</p>
    <button>Démarrer</button>
  </div>
  <div class="hero-visual">
    <img src="hero.png" alt="Product" />
  </div>
</section>
```

### 2. Admin Dashboard

```html
<div class="split split--sidebar" style="--breakpoint: 992px">
  <aside>Navigation</aside>
  <main>Dashboard Content</main>
</div>
```

### 3. Blog avec sidebar

```html
<div class="split" style="--split-ratio: 1fr 300px">
  <main>Articles</main>
  <aside>Widgets, Recent Posts, Categories</aside>
</div>
```

### 4. Formulaire de paiement

```html
<div class="split split--30-70">
  <div>Résumé commande</div>
  <div>Formulaire de paiement</div>
</div>
```

### 5. Comparaison produits

```html
<div class="split">
  <div class="product-card">Produit A</div>
  <div class="product-card">Produit B</div>
</div>
```

## 🔧 Combinaison avec autres utilitaires

### Avec Grid Wrapper (nested grids)

```html
<div class="split">
  <aside>Sidebar</aside>
  <main>
    <div class="grid-wrapper" style="--cols: 3">
      <!-- Grid de 3 colonnes dans la colonne de droite -->
      <div>Item 1</div>
      <div>Item 2</div>
      <div>Item 3</div>
    </div>
  </main>
</div>
```

### Avec Card Wrapper

```html
<div class="split split--center" style="--gap: 3rem">
  <div class="card">
    <h3>Feature 1</h3>
    <p>Description</p>
  </div>
  <div class="card">
    <h3>Feature 2</h3>
    <p>Description</p>
  </div>
</div>
```

## 📱 Comportement responsive

| Viewport              | Comportement                                  |
| --------------------- | --------------------------------------------- |
| > 768px (desktop)     | Affichage en 2 colonnes selon `--split-ratio` |
| ≤ 768px (mobile)      | Empilage vertical (1 colonne)                 |
| `data-reverse="true"` | Inverse l'ordre sur mobile                    |

### Désactiver le responsive

```scss
// Si vous voulez garder le split sur mobile
.split--no-stack {
  @media (max-width: 768px) {
    grid-template-columns: var(--split-ratio) !important;

    // Attention au overflow
    overflow-x: auto;
  }
}
```

## ⚡ Performance & Bonnes pratiques

### ✅ À faire

```html
<!-- Bon : Ratios clairs et simples -->
<div class="split" style="--split-ratio: 1fr 2fr">
  <!-- Bon : Classes prédéfinies -->
  <div class="split split--sidebar">
    <!-- Bon : Gap responsive -->
    <div class="split" style="--gap: clamp(1rem, 3vw, 3rem)"></div>
  </div>
</div>
```

### ❌ À éviter

```html
<!-- Mauvais : Ratios trop complexes -->
<div
  class="split"
  style="--split-ratio: minmax(200px, 1fr) minmax(300px, 2fr) calc(100% - 500px)"
>
  <!-- Mauvais : Trop de contenu sur mobile -->
  <div class="split" style="--breakpoint: 320px">
    <!-- Trop étroit sur mobile -->
  </div>

  <!-- Mauvais : Gap trop grand -->
  <div class="split" style="--gap: 10rem">
    <!-- Perte d'espace -->
  </div>
</div>
```

## 🌐 Compatibilité navigateurs

| Navigateur | Version minimale | Support    |
| ---------- | ---------------- | ---------- |
| Chrome     | 57+              | ✅ Complet |
| Firefox    | 52+              | ✅ Complet |
| Safari     | 10.1+            | ✅ Complet |
| Edge       | 16+              | ✅ Complet |
| Opera      | 44+              | ✅ Complet |

### Fallback pour anciens navigateurs

```scss
.split {
  // Fallback Flexbox
  display: flex;
  flex-wrap: wrap;
  gap: var(--gap, 2rem);

  > * {
    flex: 1;
    min-width: 300px; // Empêche les colonnes trop étroites
  }

  // Grid prend le relais si supporté
  @supports (display: grid) {
    display: grid;
    grid-template-columns: var(--split-ratio);

    > * {
      min-width: unset;
    }
  }
}
```

## 🐛 Troubleshooting

### Problème : Les colonnes ne s'empilent pas sur mobile

**Solution** : Vérifiez que vous n'avez pas de `min-width` qui empêche l'empilement

```css
/* Mauvais */
.split > * {
  min-width: 400px; /* Trop large pour mobile */
}

/* Bon */
.split > * {
  min-width: 0; /* Permet la flexibilité */
}
```

### Problème : Débordement horizontal sur mobile

**Solution** : Ajoutez un overflow

```scss
.split {
  @media (max-width: 768px) {
    overflow-x: hidden;
  }
}
```

### Problème : Gap trop grand sur mobile

**Solution** : Utilisez un gap responsive

```html
<div class="split" style="--gap: clamp(1rem, 2vw, 2rem)"></div>
```

## 📦 Variantes complètes

```scss
// Toutes les variantes disponibles
.split {
  /* Base */
}
.split--sidebar {
  --split-ratio: 250px 1fr;
}
.split--sidebar-right {
  --split-ratio: 1fr 250px;
}
.split--30-70 {
  --split-ratio: 30% 70%;
}
.split--70-30 {
  --split-ratio: 70% 30%;
}
.split--golden {
  --split-ratio: 38.2% 61.8%;
}
.split--center {
  align-items: center;
}
.split--stretch {
  align-items: stretch;
}
.split--end {
  align-items: end;
}
```

## 🎓 Ressources complémentaires

- [CSS Grid Layout - MDN](https://developer.mozilla.org/fr/docs/Web/CSS/CSS_Grid_Layout)
- [CSS Custom Properties - MDN](https://developer.mozilla.org/fr/docs/Web/CSS/--*)
- [A Complete Guide to Grid - CSS-Tricks](https://css-tricks.com/snippets/css/complete-guide-grid/)

## 📝 Changelog

- **v1.0** - Version initiale avec ratios de base
- **v1.1** - Ajout des variantes prédéfinies
- **v1.2** - Support de l'inversion mobile avec `data-reverse`
- **v1.3** - Amélioration du responsive avec `clamp()`

---

**Made with ❤️ for flexible layouts**
