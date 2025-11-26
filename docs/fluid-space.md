# Fluid Spacing

> Utilitaire CSS pour créer des espacements fluides et responsives sans media queries

## 📝 Description

Le `fluid-space` permet de créer des espacements (padding/margin) qui s'adaptent automatiquement à la taille de l'écran grâce à la fonction CSS `clamp()`. Fini les media queries pour chaque breakpoint !

## 🎯 Cas d'usage

- Sections avec padding responsive
- Containers fluides
- Espacements cohérents sur tous les devices
- Layout moderne sans breakpoints multiples
- Design systems scalables

## 💾 Installation

```scss
// _fluid-spacing.scss
.fluid-space {
  --min-space: 1rem;
  --max-space: 4rem;
  --preferred-space: 5vw;

  padding: clamp(var(--min-space), var(--preferred-space), var(--max-space));
}

// Variations directionnelles
.fluid-space-x {
  --min-space: 1rem;
  --max-space: 4rem;
  --preferred-space: 5vw;

  padding-inline: clamp(
    var(--min-space),
    var(--preferred-space),
    var(--max-space)
  );
}

.fluid-space-y {
  --min-space: 1rem;
  --max-space: 4rem;
  --preferred-space: 5vw;

  padding-block: clamp(
    var(--min-space),
    var(--preferred-space),
    var(--max-space)
  );
}

// Modificateurs prédéfinis
.fluid-space--sm {
  --min-space: 0.5rem;
  --max-space: 2rem;
  --preferred-space: 3vw;
}

.fluid-space--md {
  --min-space: 1rem;
  --max-space: 4rem;
  --preferred-space: 5vw;
}

.fluid-space--lg {
  --min-space: 2rem;
  --max-space: 8rem;
  --preferred-space: 8vw;
}

.fluid-space--xl {
  --min-space: 3rem;
  --max-space: 12rem;
  --preferred-space: 10vw;
}

// Version margin
.fluid-margin {
  --min-space: 1rem;
  --max-space: 4rem;
  --preferred-space: 5vw;

  margin: clamp(var(--min-space), var(--preferred-space), var(--max-space));
}

.fluid-margin-x {
  margin-inline: clamp(
    var(--min-space),
    var(--preferred-space),
    var(--max-space)
  );
}

.fluid-margin-y {
  margin-block: clamp(
    var(--min-space),
    var(--preferred-space),
    var(--max-space)
  );
}
```

## 🚀 Utilisation de base

### Section avec padding fluide

```html
<section class="fluid-space">
  <h2>Section Title</h2>
  <p>Le padding s'adapte automatiquement à la taille de l'écran.</p>
</section>
```

### Padding horizontal seulement

```html
<div class="fluid-space-x">
  <p>Padding fluide sur les côtés uniquement</p>
</div>
```

### Avec valeurs personnalisées

```html
<section
  class="fluid-space"
  style="--min-space: 2rem; --max-space: 8rem; --preferred-space: 8vw"
>
  <h2>Section avec espacement large</h2>
</section>
```

### Classes prédéfinies

```html
<!-- Petit espacement -->
<div class="fluid-space fluid-space--sm">Espacement réduit</div>

<!-- Espacement medium (défaut) -->
<div class="fluid-space fluid-space--md">Espacement moyen</div>

<!-- Grand espacement -->
<div class="fluid-space fluid-space--lg">Grand espacement</div>

<!-- Très grand espacement -->
<div class="fluid-space fluid-space--xl">Très grand espacement</div>
```

## ⚙️ Paramètres

| Variable CSS        | Type      | Défaut | Description                        |
| ------------------- | --------- | ------ | ---------------------------------- |
| `--min-space`       | `length`  | `1rem` | Espacement minimum (petits écrans) |
| `--max-space`       | `length`  | `4rem` | Espacement maximum (grands écrans) |
| `--preferred-space` | `vw/vh/%` | `5vw`  | Valeur préférée (fluide)           |

### Classes modificatrices

| Classe             | Min    | Max   | Preferred | Usage                         |
| ------------------ | ------ | ----- | --------- | ----------------------------- |
| `.fluid-space--sm` | 0.5rem | 2rem  | 3vw       | Cards, composants compacts    |
| `.fluid-space--md` | 1rem   | 4rem  | 5vw       | Sections standards            |
| `.fluid-space--lg` | 2rem   | 8rem  | 8vw       | Hero sections, headers        |
| `.fluid-space--xl` | 3rem   | 12rem | 10vw      | Landing pages, espaces larges |

### Variations directionnelles

| Classe            | Application                 |
| ----------------- | --------------------------- |
| `.fluid-space`    | Padding sur tous les côtés  |
| `.fluid-space-x`  | Padding horizontal (inline) |
| `.fluid-space-y`  | Padding vertical (block)    |
| `.fluid-margin`   | Margin sur tous les côtés   |
| `.fluid-margin-x` | Margin horizontal           |
| `.fluid-margin-y` | Margin vertical             |

## 📚 Exemples avancés

### Hero section responsive

```html
<section class="hero fluid-space--xl">
  <h1 class="hero-title">Bienvenue</h1>
  <p class="hero-subtitle">Un espacement qui s'adapte parfaitement</p>
  <button class="cta-button">Commencer</button>
</section>

<style>
  .hero {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
    text-align: center;
    min-height: 60vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  .hero-title {
    font-size: clamp(2rem, 5vw, 4rem);
    margin-bottom: 1rem;
  }

  .hero-subtitle {
    font-size: clamp(1rem, 2vw, 1.5rem);
    margin-bottom: 2rem;
    max-width: 600px;
  }
</style>
```

### Container fluide personnalisé

```html
<div class="container-fluid">
  <h2>Container with Fluid Padding</h2>
  <p>Le padding horizontal s'adapte automatiquement.</p>
</div>

<style>
  .container-fluid {
    --min-space: 1rem;
    --max-space: 4rem;
    --preferred-space: 5vw;

    max-width: 1400px;
    margin-inline: auto;
    padding-inline: clamp(
      var(--min-space),
      var(--preferred-space),
      var(--max-space)
    );
  }
</style>
```

### Grille avec gap fluide

```html
<div class="grid-fluid">
  <div class="card">Card 1</div>
  <div class="card">Card 2</div>
  <div class="card">Card 3</div>
  <div class="card">Card 4</div>
</div>

<style>
  .grid-fluid {
    --min-gap: 1rem;
    --max-gap: 3rem;
    --preferred-gap: 4vw;

    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: clamp(var(--min-gap), var(--preferred-gap), var(--max-gap));
    padding: clamp(var(--min-gap), var(--preferred-gap), var(--max-gap));
  }
</style>
```

### Sections alternées

```html
<main>
  <section class="section section--white fluid-space-y fluid-space--lg">
    <div class="container">
      <h2>Section 1</h2>
      <p>Contenu...</p>
    </div>
  </section>

  <section class="section section--gray fluid-space-y fluid-space--lg">
    <div class="container">
      <h2>Section 2</h2>
      <p>Contenu...</p>
    </div>
  </section>

  <section class="section section--white fluid-space-y fluid-space--lg">
    <div class="container">
      <h2>Section 3</h2>
      <p>Contenu...</p>
    </div>
  </section>
</main>

<style>
  .section--white {
    background: white;
  }

  .section--gray {
    background: #f9fafb;
  }

  .container {
    max-width: 1200px;
    margin-inline: auto;
    padding-inline: clamp(1rem, 3vw, 2rem);
  }
</style>
```

### Card avec espacement fluide

```html
<article class="card">
  <img src="image.jpg" alt="Card image" />
  <div class="card-content fluid-space">
    <h3>Card Title</h3>
    <p>Description with fluid padding that adapts to screen size.</p>
    <button>Read more</button>
  </div>
</article>

<style>
  .card {
    border-radius: 0.5rem;
    overflow: hidden;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
  }

  .card img {
    width: 100%;
    height: 200px;
    object-fit: cover;
  }

  .card-content {
    --min-space: 1rem;
    --max-space: 2rem;
    --preferred-space: 3vw;
  }
</style>
```

### Combinaison avec fluid typography

```html
<article class="article">
  <h1 class="article-title">Article Title</h1>
  <p class="article-content">
    Lorem ipsum dolor sit amet, consectetur adipiscing elit...
  </p>
</article>

<style>
  .article {
    --min-space: 2rem;
    --max-space: 8rem;
    --preferred-space: 8vw;

    max-width: 800px;
    margin-inline: auto;
    padding-inline: clamp(
      var(--min-space),
      var(--preferred-space),
      var(--max-space)
    );
    padding-block: clamp(2rem, 5vw, 6rem);
  }

  .article-title {
    font-size: clamp(1.5rem, 4vw, 3rem);
    margin-bottom: clamp(1rem, 3vw, 2rem);
  }

  .article-content {
    font-size: clamp(1rem, 1.5vw, 1.125rem);
    line-height: 1.7;
  }
</style>
```

## 🎨 Personnalisation

### Design system avec échelle d'espacement

```scss
// _spacing-scale.scss
$spacing-scale: (
  "xs": (
    min: 0.25rem,
    preferred: 1vw,
    max: 0.5rem,
  ),
  "sm": (
    min: 0.5rem,
    preferred: 2vw,
    max: 1rem,
  ),
  "md": (
    min: 1rem,
    preferred: 3vw,
    max: 2rem,
  ),
  "lg": (
    min: 2rem,
    preferred: 5vw,
    max: 4rem,
  ),
  "xl": (
    min: 3rem,
    preferred: 8vw,
    max: 6rem,
  ),
  "2xl": (
    min: 4rem,
    preferred: 10vw,
    max: 8rem,
  ),
  "3xl": (
    min: 6rem,
    preferred: 12vw,
    max: 12rem,
  ),
);

@each $name, $values in $spacing-scale {
  .fluid-space--#{$name} {
    --min-space: #{map-get($values, "min")};
    --max-space: #{map-get($values, "max")};
    --preferred-space: #{map-get($values, "preferred")};
  }
}
```

### Avec breakpoints custom

```scss
.fluid-space-custom {
  --min-space: 1rem;
  --max-space: 4rem;
  --min-vw: 320px;
  --max-vw: 1200px;

  padding: clamp(
    var(--min-space),
    calc(
      var(--min-space) + (var(--max-space) - var(--min-space)) * ((
              100vw - var(--min-vw)
            ) / (var(--max-vw) - var(--min-vw)))
    ),
    var(--max-space)
  );
}
```

### Utilitaires margin fluides

```scss
.fluid-mt {
  margin-top: clamp(var(--min-space), var(--preferred-space), var(--max-space));
}
.fluid-mr {
  margin-right: clamp(
    var(--min-space),
    var(--preferred-space),
    var(--max-space)
  );
}
.fluid-mb {
  margin-bottom: clamp(
    var(--min-space),
    var(--preferred-space),
    var(--max-space)
  );
}
.fluid-ml {
  margin-left: clamp(
    var(--min-space),
    var(--preferred-space),
    var(--max-space)
  );
}

.fluid-pt {
  padding-top: clamp(
    var(--min-space),
    var(--preferred-space),
    var(--max-space)
  );
}
.fluid-pr {
  padding-right: clamp(
    var(--min-space),
    var(--preferred-space),
    var(--max-space)
  );
}
.fluid-pb {
  padding-bottom: clamp(
    var(--min-space),
    var(--preferred-space),
    var(--max-space)
  );
}
.fluid-pl {
  padding-left: clamp(
    var(--min-space),
    var(--preferred-space),
    var(--max-space)
  );
}
```

## 🔧 Compatibilité

| Navigateur | Version minimale | Notes                      |
| ---------- | ---------------- | -------------------------- |
| Chrome     | 79+              | Support complet de clamp() |
| Firefox    | 75+              | Support complet de clamp() |
| Safari     | 13.1+            | Support complet de clamp() |
| Edge       | 79+              | Support complet de clamp() |

### Fallback pour anciens navigateurs

```scss
.fluid-space {
  // Fallback pour anciens navigateurs
  padding: var(--min-space, 1rem);

  // Modern browsers avec support clamp()
  @supports (padding: clamp(1rem, 5vw, 4rem)) {
    padding: clamp(var(--min-space), var(--preferred-space), var(--max-space));
  }
}
```

## ⚠️ Notes importantes

- **Performance** : `clamp()` est très performant, pas de calcul JavaScript nécessaire
- **Valeurs** : Assurez-vous que min < preferred < max pour éviter les comportements inattendus
- **Unités** : Mélanger rem/em avec vw/vh fonctionne parfaitement
- **Accessibilité** : Respecte les préférences de taille de texte de l'utilisateur

## 🎓 Bonnes pratiques

✅ **À faire**

- Utiliser des valeurs cohérentes dans tout le design
- Tester sur différentes tailles d'écran
- Combiner avec fluid typography pour une harmonie complète
- Définir des variables CSS globales pour la consistance
- Utiliser vw pour la valeur préférée pour un scaling fluide

❌ **À éviter**

- Ne pas utiliser de valeurs trop extrêmes (min: 0.1rem, max: 20rem)
- Ne pas oublier les fallbacks pour les anciens navigateurs
- Ne pas abuser des espacements différents partout
- Ne pas négliger le test sur mobile

## 📐 Calculateur d'espacement fluide

```javascript
// Calculer les valeurs optimales
function calculateFluidSpace(minPx, maxPx, minVw = 320, maxVw = 1200) {
  const minRem = minPx / 16;
  const maxRem = maxPx / 16;
  const vwValue = ((maxPx - minPx) / (maxVw - minVw)) * 100;

  return {
    min: `${minRem}rem`,
    max: `${maxRem}rem`,
    preferred: `${vwValue.toFixed(2)}vw`,
    css: `clamp(${minRem}rem, ${vwValue.toFixed(2)}vw, ${maxRem}rem)`,
  };
}

// Exemple d'utilisation
console.log(calculateFluidSpace(16, 64));
// { min: "1rem", max: "4rem", preferred: "5.45vw", css: "clamp(1rem, 5.45vw, 4rem)" }
```

---

[← Retour à la documentation](../README.md)
