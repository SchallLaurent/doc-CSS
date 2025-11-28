# Sticky Wrapper

> Utilitaire CSS pour créer des éléments sticky (collés) avec contrôle précis du positionnement

## 📝 Description

Le `sticky-wrapper` permet de créer facilement des éléments qui restent "collés" lors du scroll. Parfait pour les headers, sidebars, tableaux de bord et éléments de navigation qui doivent rester visibles.

## 🎯 Cas d'usage

- Headers et navbars qui restent en haut
- Sidebars et menus latéraux fixes
- Call-to-action flottants
- Tables avec headers fixes
- Toolbars et actions bars
- Breadcrumbs persistants

## 💾 Installation

```scss
// _sticky-wrapper.scss
.sticky-wrapper {
  --offset: 0px;
  --z-index: 100;
  --position: top; // top, bottom, left, right

  position: sticky;
  z-index: var(--z-index);

  &[data-position="top"],
  &:not([data-position]) {
    top: var(--offset);
  }

  &[data-position="bottom"] {
    bottom: var(--offset);
  }

  &[data-position="left"] {
    left: var(--offset);
  }

  &[data-position="right"] {
    right: var(--offset);
  }
}

// Modificateurs prédéfinis
.sticky-wrapper--header {
  --z-index: 1000;
  top: 0;
}

.sticky-wrapper--footer {
  --z-index: 1000;
  bottom: 0;
}

.sticky-wrapper--sidebar {
  --z-index: 100;
  top: var(--offset, 0px);
  align-self: start; // Important pour les flexbox/grid
}
```

## 🚀 Utilisation de base

### Header sticky simple

```html
<header class="sticky-wrapper sticky-wrapper--header">
  <nav>
    <a href="/">Logo</a>
    <a href="/about">À propos</a>
    <a href="/contact">Contact</a>
  </nav>
</header>
```

### Avec offset personnalisé

```html
<!-- Header décalé de 20px du haut -->
<header class="sticky-wrapper" style="--offset: 20px">
  <nav>Menu principal</nav>
</header>
```

### Sidebar sticky

```html
<div class="layout">
  <aside class="sticky-wrapper sticky-wrapper--sidebar" style="--offset: 100px">
    <nav>
      <a href="#section-1">Section 1</a>
      <a href="#section-2">Section 2</a>
      <a href="#section-3">Section 3</a>
    </nav>
  </aside>

  <main>
    <!-- Contenu principal qui scroll -->
  </main>
</div>

<style>
  .layout {
    display: grid;
    grid-template-columns: 250px 1fr;
    gap: 2rem;
  }
</style>
```

### Footer sticky

```html
<footer class="sticky-wrapper sticky-wrapper--footer">
  <p>&copy; 2025 - Tous droits réservés</p>
</footer>
```

## ⚙️ Paramètres

| Variable CSS | Type      | Défaut | Description                                     |
| ------------ | --------- | ------ | ----------------------------------------------- |
| `--offset`   | `length`  | `0px`  | Distance depuis le bord (top/bottom/left/right) |
| `--z-index`  | `integer` | `100`  | Index de superposition                          |

### Attributs data

| Attribut        | Valeurs                          | Description                  |
| --------------- | -------------------------------- | ---------------------------- |
| `data-position` | `top`, `bottom`, `left`, `right` | Position de l'élément sticky |

### Classes modificatrices

| Classe                     | Z-Index | Position        | Usage                      |
| -------------------------- | ------- | --------------- | -------------------------- |
| `.sticky-wrapper--header`  | 1000    | top: 0          | Headers principaux         |
| `.sticky-wrapper--footer`  | 1000    | bottom: 0       | Footers fixes              |
| `.sticky-wrapper--sidebar` | 100     | top avec offset | Sidebars et menus latéraux |

## 📚 Exemples avancés

### Header avec shadow au scroll

```html
<header class="sticky-wrapper sticky-header">
  <nav>Navigation</nav>
</header>

<style>
  .sticky-header {
    --offset: 0;
    --z-index: 1000;
    background: white;
    transition: box-shadow 0.3s;
  }

  /* Ajoute une ombre quand le header devient sticky */
  .sticky-header.is-stuck {
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
  }
</style>

<script>
  // Détection du sticky state
  const header = document.querySelector(".sticky-header");
  const observer = new IntersectionObserver(
    ([e]) => e.target.classList.toggle("is-stuck", e.intersectionRatio < 1),
    { threshold: [1] }
  );

  observer.observe(header);
</script>
```

### Multiple sticky headers

```html
<!-- Header principal -->
<header class="sticky-wrapper" style="--offset: 0; --z-index: 1000">
  <div class="main-nav">Logo & Navigation</div>
</header>

<!-- Sub-header qui se colle sous le header principal -->
<div class="sticky-wrapper" style="--offset: 60px; --z-index: 999">
  <div class="sub-nav">Filtres & Actions</div>
</div>

<main>
  <!-- Contenu -->
</main>
```

### Table avec header sticky

```html
<div class="table-container">
  <table>
    <thead class="sticky-wrapper" style="--offset: 0">
      <tr>
        <th>Nom</th>
        <th>Email</th>
        <th>Rôle</th>
      </tr>
    </thead>
    <tbody>
      <!-- Lignes du tableau -->
    </tbody>
  </table>
</div>

<style>
  .table-container {
    max-height: 500px;
    overflow-y: auto;
  }

  thead.sticky-wrapper {
    background: white;
  }

  thead.sticky-wrapper th {
    box-shadow: 0 2px 2px -1px rgba(0, 0, 0, 0.1);
  }
</style>
```

### Sidebar avec scrollspy

```html
<div class="layout">
  <aside class="sticky-wrapper sticky-wrapper--sidebar" style="--offset: 100px">
    <nav class="toc">
      <a href="#intro" class="active">Introduction</a>
      <a href="#features">Fonctionnalités</a>
      <a href="#usage">Utilisation</a>
      <a href="#examples">Exemples</a>
    </nav>
  </aside>

  <main>
    <section id="intro">...</section>
    <section id="features">...</section>
    <section id="usage">...</section>
    <section id="examples">...</section>
  </main>
</div>

<style>
  .toc a {
    display: block;
    padding: 0.5rem;
    color: #666;
    text-decoration: none;
    border-left: 2px solid transparent;
    transition: all 0.2s;
  }

  .toc a.active {
    color: #3b82f6;
    border-left-color: #3b82f6;
    background: #eff6ff;
  }
</style>
```

### Call-to-action sticky en bas

```html
<div
  class="sticky-wrapper sticky-cta"
  data-position="bottom"
  style="--offset: 20px; --z-index: 999"
>
  <div class="cta-content">
    <p>Essayez gratuitement pendant 14 jours !</p>
    <button>Commencer maintenant</button>
  </div>
</div>

<style>
  .sticky-cta {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
    padding: 1rem;
    border-radius: 0.5rem;
    margin: 0 1rem;
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
  }

  .cta-content {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 1rem;
    max-width: 1200px;
    margin: 0 auto;
  }

  @media (max-width: 768px) {
    .cta-content {
      flex-direction: column;
      text-align: center;
    }
  }
</style>
```

### Responsive sticky

```html
<aside class="sticky-wrapper sidebar-nav">
  <nav>Menu</nav>
</aside>

<style>
  .sidebar-nav {
    --offset: 80px;
    --z-index: 100;
  }

  /* Sticky seulement sur desktop */
  @media (min-width: 1024px) {
    .sidebar-nav {
      position: sticky;
    }
  }

  /* Normal flow sur mobile/tablet */
  @media (max-width: 1023px) {
    .sidebar-nav {
      position: static;
    }
  }
</style>
```

## 🎨 Personnalisation

### Système de z-index cohérent

```scss
// _variables.scss
$z-indexes: (
  "modal": 2000,
  "overlay": 1500,
  "header": 1000,
  "dropdown": 900,
  "sticky-cta": 800,
  "sidebar": 100,
  "default": 1,
);

// Utilisation
.sticky-wrapper--header {
  --z-index: #{map-get($z-indexes, "header")};
}

.sticky-wrapper--sidebar {
  --z-index: #{map-get($z-indexes, "sidebar")};
}
```

### Animation d'entrée

```scss
.sticky-wrapper {
  --offset: 0;
  --z-index: 100;

  position: sticky;
  animation: slideDown 0.3s ease-out;
}

@keyframes slideDown {
  from {
    transform: translateY(-100%);
    opacity: 0;
  }
  to {
    transform: translateY(0);
    opacity: 1;
  }
}
```

### Backdrop blur effect

```scss
.sticky-wrapper--glass {
  --offset: 0;
  --z-index: 1000;

  background: rgba(255, 255, 255, 0.8);
  backdrop-filter: blur(10px);
  border-bottom: 1px solid rgba(0, 0, 0, 0.1);
}
```

## 🔧 Compatibilité

| Navigateur | Version minimale | Notes           |
| ---------- | ---------------- | --------------- |
| Chrome     | 56+              | Support complet |
| Firefox    | 59+              | Support complet |
| Safari     | 13+              | Support complet |
| Edge       | 79+              | Support complet |

## ⚠️ Notes importantes

- **Container parent** : Le parent doit avoir un overflow différent de `hidden` pour que sticky fonctionne
- **Hauteur parent** : Le parent doit être plus grand que l'élément sticky
- **Z-index** : Pensez à gérer les z-index pour éviter les conflits
- **Performance** : Sticky est performant mais attention avec trop d'éléments simultanés

## 🎓 Bonnes pratiques

✅ **À faire**

- Définir un offset cohérent pour plusieurs sticky headers
- Utiliser un système de z-index organisé
- Tester le comportement sur différentes tailles d'écran
- Ajouter des transitions pour améliorer l'UX
- Gérer les cas où sticky n'est pas nécessaire (mobile)

❌ **À éviter**

- Ne pas mettre position sticky sur body ou html
- Ne pas oublier le fallback pour les anciens navigateurs
- Ne pas avoir trop d'éléments sticky simultanés
- Ne pas négliger l'accessibilité (navigation au clavier)

## 💡 Astuces JavaScript

### Détecter quand un élément devient sticky

```javascript
const stickyElement = document.querySelector(".sticky-wrapper");

const observer = new IntersectionObserver(
  ([entry]) => {
    if (entry.intersectionRatio < 1) {
      stickyElement.classList.add("is-stuck");
    } else {
      stickyElement.classList.remove("is-stuck");
    }
  },
  { threshold: [1], rootMargin: "-1px 0px 0px 0px" }
);

observer.observe(stickyElement);
```

---

[← Retour à la documentation](../README.md)
