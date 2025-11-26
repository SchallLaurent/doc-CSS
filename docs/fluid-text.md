# Fluid Typography

> Utilitaire CSS pour créer une typographie fluide et responsive sans media queries

## 📝 Description

Le `fluid-text` permet de créer des tailles de texte qui s'adaptent automatiquement à la taille de l'écran. Basé sur la fonction `clamp()`, il offre un contrôle précis sur les tailles minimales, maximales et préférées.

## 🎯 Cas d'usage

- Titres responsives
- Corps de texte adaptatif
- Landing pages modernes
- Design systems scalables
- Interfaces sans breakpoints multiples
- Typography harmonieuse sur tous devices

## 💾 Installation

```scss
// _fluid-typography.scss
.fluid-text {
  --min-size: 1rem;
  --max-size: 2rem;
  --preferred-size: 2vw;

  font-size: clamp(var(--min-size), var(--preferred-size), var(--max-size));
}

// Échelle typographique prédéfinie
.fluid-text--xs {
  --min-size: 0.75rem;
  --max-size: 0.875rem;
  --preferred-size: 1vw;
}

.fluid-text--sm {
  --min-size: 0.875rem;
  --max-size: 1rem;
  --preferred-size: 1.25vw;
}

.fluid-text--base {
  --min-size: 1rem;
  --max-size: 1.125rem;
  --preferred-size: 1.5vw;
}

.fluid-text--lg {
  --min-size: 1.125rem;
  --max-size: 1.5rem;
  --preferred-size: 2vw;
}

.fluid-text--xl {
  --min-size: 1.25rem;
  --max-size: 2rem;
  --preferred-size: 2.5vw;
}

.fluid-text--2xl {
  --min-size: 1.5rem;
  --max-size: 2.5rem;
  --preferred-size: 3vw;
}

.fluid-text--3xl {
  --min-size: 2rem;
  --max-size: 3.5rem;
  --preferred-size: 4vw;
}

.fluid-text--4xl {
  --min-size: 2.5rem;
  --max-size: 4.5rem;
  --preferred-size: 5vw;
}

.fluid-text--5xl {
  --min-size: 3rem;
  --max-size: 6rem;
  --preferred-size: 6vw;
}

// Headings avec fluid type
h1,
.h1 {
  font-size: clamp(2rem, 5vw, 4rem);
  line-height: 1.2;
}

h2,
.h2 {
  font-size: clamp(1.75rem, 4vw, 3rem);
  line-height: 1.3;
}

h3,
.h3 {
  font-size: clamp(1.5rem, 3vw, 2.5rem);
  line-height: 1.4;
}

h4,
.h4 {
  font-size: clamp(1.25rem, 2.5vw, 2rem);
  line-height: 1.4;
}

h5,
.h5 {
  font-size: clamp(1.125rem, 2vw, 1.5rem);
  line-height: 1.5;
}

h6,
.h6 {
  font-size: clamp(1rem, 1.5vw, 1.25rem);
  line-height: 1.5;
}
```

## 🚀 Utilisation de base

### Texte fluide simple

```html
<h1
  class="fluid-text"
  style="--min-size: 2rem; --max-size: 4rem; --preferred-size: 5vw"
>
  Titre qui s'adapte
</h1>

<p
  class="fluid-text"
  style="--min-size: 1rem; --max-size: 1.25rem; --preferred-size: 1.5vw"
>
  Paragraphe avec taille fluide
</p>
```

### Classes prédéfinies

```html
<h1 class="fluid-text fluid-text--5xl">Très grand titre</h1>
<h2 class="fluid-text fluid-text--3xl">Grand titre</h2>
<h3 class="fluid-text fluid-text--2xl">Titre moyen</h3>
<p class="fluid-text fluid-text--base">Texte de base</p>
<small class="fluid-text fluid-text--sm">Petit texte</small>
```

### Headings automatiques

```html
<!-- Les headings ont déjà une taille fluide -->
<h1>Titre principal H1</h1>
<h2>Titre H2</h2>
<h3>Titre H3</h3>
<p>Paragraphe normal</p>
```

## ⚙️ Paramètres

| Variable CSS       | Type     | Défaut | Description                    |
| ------------------ | -------- | ------ | ------------------------------ |
| `--min-size`       | `length` | `1rem` | Taille minimum (petits écrans) |
| `--max-size`       | `length` | `2rem` | Taille maximum (grands écrans) |
| `--preferred-size` | `vw/%`   | `2vw`  | Taille préférée (fluide)       |

### Échelle typographique

| Classe              | Min Size | Max Size | Preferred | Usage            |
| ------------------- | -------- | -------- | --------- | ---------------- |
| `.fluid-text--xs`   | 0.75rem  | 0.875rem | 1vw       | Labels, captions |
| `.fluid-text--sm`   | 0.875rem | 1rem     | 1.25vw    | Small text       |
| `.fluid-text--base` | 1rem     | 1.125rem | 1.5vw     | Body text        |
| `.fluid-text--lg`   | 1.125rem | 1.5rem   | 2vw       | Lead paragraphs  |
| `.fluid-text--xl`   | 1.25rem  | 2rem     | 2.5vw     | Subtitles        |
| `.fluid-text--2xl`  | 1.5rem   | 2.5rem   | 3vw       | Section headers  |
| `.fluid-text--3xl`  | 2rem     | 3.5rem   | 4vw       | Page titles      |
| `.fluid-text--4xl`  | 2.5rem   | 4.5rem   | 5vw       | Hero titles      |
| `.fluid-text--5xl`  | 3rem     | 6rem     | 6vw       | Display text     |

## 📚 Exemples avancés

### Hero section avec titre fluide

```html
<section class="hero">
  <h1 class="hero-title fluid-text--5xl">Bienvenue sur notre site</h1>
  <p class="hero-subtitle fluid-text--xl">
    Une expérience utilisateur fluide et moderne
  </p>
  <button class="cta-button">Commencer</button>
</section>

<style>
  .hero {
    min-height: 80vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center;
    padding: clamp(2rem, 5vw, 4rem);
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
  }

  .hero-title {
    margin-bottom: clamp(1rem, 2vw, 2rem);
    font-weight: 800;
    line-height: 1.1;
    max-width: 20ch;
  }

  .hero-subtitle {
    margin-bottom: clamp(2rem, 4vw, 3rem);
    opacity: 0.9;
    max-width: 40ch;
  }
</style>
```

### Article avec typographie harmonieuse

```html
<article class="article">
  <header class="article-header">
    <h1 class="article-title">Titre de l'article</h1>
    <p class="article-meta fluid-text--sm">
      Publié le 26 novembre 2025 • 5 min de lecture
    </p>
  </header>

  <div class="article-content">
    <p class="lead fluid-text--lg">
      Ceci est le paragraphe d'introduction avec une taille de texte plus
      grande.
    </p>

    <p class="fluid-text--base">
      Lorem ipsum dolor sit amet, consectetur adipiscing elit. Le texte s'adapte
      automatiquement à la taille de l'écran.
    </p>

    <h2 class="fluid-text--2xl">Sous-titre</h2>
    <p class="fluid-text--base">Plus de contenu...</p>
  </div>
</article>

<style>
  .article {
    max-width: 70ch;
    margin-inline: auto;
    padding: clamp(2rem, 5vw, 4rem);
  }

  .article-title {
    font-size: clamp(2rem, 5vw, 3.5rem);
    line-height: 1.2;
    margin-bottom: 1rem;
  }

  .article-meta {
    color: #6b7280;
    margin-bottom: clamp(2rem, 4vw, 3rem);
  }

  .article-content p {
    line-height: 1.7;
    margin-bottom: 1.5em;
  }

  .article-content .lead {
    font-weight: 500;
    color: #374151;
  }
</style>
```

### Card grid avec titres fluides

```html
<div class="card-grid">
  <article class="card">
    <img src="image1.jpg" alt="Card 1" />
    <div class="card-content">
      <h3 class="card-title fluid-text--xl">Titre de la card</h3>
      <p class="card-description fluid-text--base">
        Description avec texte fluide qui s'adapte.
      </p>
      <a href="#" class="card-link fluid-text--sm">En savoir plus →</a>
    </div>
  </article>

  <!-- Plus de cards... -->
</div>

<style>
  .card-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: clamp(1rem, 3vw, 2rem);
    padding: clamp(1rem, 3vw, 2rem);
  }

  .card {
    border-radius: 0.5rem;
    overflow: hidden;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
    transition: transform 0.3s;
  }

  .card:hover {
    transform: translateY(-4px);
  }

  .card-content {
    padding: clamp(1rem, 2vw, 1.5rem);
  }

  .card-title {
    margin-bottom: 0.5rem;
    line-height: 1.3;
  }

  .card-description {
    color: #6b7280;
    line-height: 1.6;
    margin-bottom: 1rem;
  }

  .card-link {
    color: #3b82f6;
    text-decoration: none;
    font-weight: 500;
  }
</style>
```

### Pricing table responsive

```html
<div class="pricing-grid">
  <div class="pricing-card">
    <h3 class="pricing-title fluid-text--2xl">Starter</h3>
    <p class="pricing-price">
      <span class="price-amount fluid-text--4xl">$9</span>
      <span class="price-period fluid-text--sm">/mois</span>
    </p>
    <ul class="pricing-features fluid-text--base">
      <li>Feature 1</li>
      <li>Feature 2</li>
      <li>Feature 3</li>
    </ul>
    <button class="pricing-button">Choisir</button>
  </div>

  <!-- Plus de pricing cards... -->
</div>

<style>
  .pricing-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: clamp(1.5rem, 3vw, 2rem);
    padding: clamp(2rem, 5vw, 4rem);
    max-width: 1200px;
    margin: 0 auto;
  }

  .pricing-card {
    padding: clamp(1.5rem, 3vw, 2.5rem);
    border: 2px solid #e5e7eb;
    border-radius: 1rem;
    text-align: center;
  }

  .pricing-title {
    margin-bottom: 1rem;
    color: #1f2937;
  }

  .pricing-price {
    margin-bottom: 2rem;
  }

  .price-amount {
    display: block;
    font-weight: 800;
    color: #3b82f6;
  }

  .price-period {
    color: #6b7280;
  }
</style>
```

### Testimonial avec quote fluide

```html
<blockquote class="testimonial">
  <p class="testimonial-quote fluid-text--xl">
    "Cette approche de typography fluide a transformé notre design system. Plus
    besoin de gérer des dizaines de breakpoints !"
  </p>
  <footer class="testimonial-author">
    <img src="avatar.jpg" alt="John Doe" />
    <div class="author-info">
      <cite class="author-name fluid-text--base">John Doe</cite>
      <p class="author-title fluid-text--sm">CEO @ Company</p>
    </div>
  </footer>
</blockquote>

<style>
  .testimonial {
    max-width: 700px;
    margin: clamp(3rem, 6vw, 5rem) auto;
    padding: clamp(2rem, 4vw, 3rem);
    background: #f9fafb;
    border-radius: 1rem;
    border-left: 4px solid #3b82f6;
  }

  .testimonial-quote {
    font-style: italic;
    line-height: 1.6;
    margin-bottom: 2rem;
    color: #374151;
  }

  .testimonial-author {
    display: flex;
    align-items: center;
    gap: 1rem;
  }

  .testimonial-author img {
    width: 60px;
    height: 60px;
    border-radius: 50%;
  }

  .author-name {
    font-weight: 600;
    font-style: normal;
    display: block;
    margin-bottom: 0.25rem;
  }

  .author-title {
    color: #6b7280;
  }
</style>
```

## 🎨 Personnalisation

### Design system typographique complet

```scss
// _typography-system.scss

// Échelle modulaire (ratio 1.25)
$type-scale: (
  "xs": (
    min: 0.64rem,
    max: 0.8rem,
  ),
  "sm": (
    min: 0.8rem,
    max: 1rem,
  ),
  "base": (
    min: 1rem,
    max: 1.25rem,
  ),
  "lg": (
    min: 1.25rem,
    max: 1.563rem,
  ),
  "xl": (
    min: 1.563rem,
    max: 1.953rem,
  ),
  "2xl": (
    min: 1.953rem,
    max: 2.441rem,
  ),
  "3xl": (
    min: 2.441rem,
    max: 3.052rem,
  ),
  "4xl": (
    min: 3.052rem,
    max: 3.815rem,
  ),
  "5xl": (
    min: 3.815rem,
    max: 4.768rem,
  ),
);

@each $name, $sizes in $type-scale {
  .fluid-text--#{$name} {
    $min: map-get($sizes, "min");
    $max: map-get($sizes, "max");
    $preferred: calc((#{$max} - #{$min}) * 2 + #{$min});

    font-size: clamp(#{$min}, #{$preferred}, #{$max});
  }
}
```

### Avec line-height fluide

```scss
.fluid-text-full {
  --min-size: 1rem;
  --max-size: 2rem;
  --min-line-height: 1.5;
  --max-line-height: 1.7;

  font-size: clamp(var(--min-size), 2vw, var(--max-size));
  line-height: clamp(var(--min-line-height), 1.6, var(--max-line-height));
}
```

### Typography avec container queries

```scss
.card {
  container-type: inline-size;

  h3 {
    font-size: clamp(1rem, 5cqi, 2rem); // 5% of container width
  }
}
```

## 🔧 Compatibilité

| Navigateur | Version minimale | Notes                   |
| ---------- | ---------------- | ----------------------- |
| Chrome     | 79+              | Support complet clamp() |
| Firefox    | 75+              | Support complet clamp() |
| Safari     | 13.1+            | Support complet clamp() |
| Edge       | 79+              | Support complet clamp() |

### Fallback pour anciens navigateurs

```scss
.fluid-text {
  // Fallback
  font-size: var(--min-size, 1rem);

  // Modern browsers
  @supports (font-size: clamp(1rem, 2vw, 2rem)) {
    font-size: clamp(var(--min-size), var(--preferred-size), var(--max-size));
  }
}
```

## ⚠️ Notes importantes

- **Accessibilité** : Toujours respecter les préférences utilisateur pour la taille de texte
- **Lisibilité** : Ne pas descendre en dessous de 16px pour le body text
- **Line-height** : Ajuster le line-height en fonction de la taille du texte
- **Contraste** : Maintenir un contraste suffisant sur tous les devices

## 🎓 Bonnes pratiques

✅ **À faire**

- Définir une échelle typographique cohérente
- Tester sur différentes tailles d'écran
- Limiter le nombre de tailles différentes
- Utiliser des unités rem pour l'accessibilité
- Combiner avec fluid spacing pour l'harmonie

❌ **À éviter**

- Texte trop petit sur mobile (< 14px)
- Texte trop grand sur desktop (> 24px pour body)
- Trop de variation dans les tailles
- Ignorer le line-height
- Oublier les tests d'accessibilité

## 📐 Calculateur de fluid typography

```javascript
function calculateFluidType(minPx, maxPx, minVw = 320, maxVw = 1200) {
  const minRem = minPx / 16;
  const maxRem = maxPx / 16;

  // Calcul du slope
  const slope = (maxPx - minPx) / (maxVw - minVw);
  const yAxisIntersection = -minVw * slope + minPx;

  const preferredValue = `${(yAxisIntersection / 16).toFixed(4)}rem + ${(
    slope * 100
  ).toFixed(4)}vw`;

  return {
    min: `${minRem}rem`,
    max: `${maxRem}rem`,
    preferred: preferredValue,
    css: `clamp(${minRem}rem, ${preferredValue}, ${maxRem}rem)`,
  };
}

// Exemple
console.log(calculateFluidType(16, 32));
```

---

[← Retour à la documentation](../README.md)
