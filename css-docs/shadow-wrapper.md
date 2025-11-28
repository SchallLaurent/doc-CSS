# Shadow Wrapper Utility

> Système d'ombres cohérent et personnalisable pour donner de la profondeur à vos interfaces

## 📋 Description

**Shadow Wrapper** est un utilitaire CSS qui fournit un système d'ombres (box-shadow) cohérent et facilement personnalisable. Il permet d'ajouter de la profondeur, de la hiérarchie et du professionnalisme à vos interfaces en quelques classes CSS. Basé sur des variables CSS, il offre un contrôle total sur la couleur, la taille et l'intensité des ombres.

### ✨ Caractéristiques principales

- 🎨 **Système d'ombres en couches** : De subtle (XS) à dramatique (XL)
- 🎯 **Personnalisation complète** : Couleur, opacité, taille via variables CSS
- 🔧 **Variables CSS** : Ajustement en temps réel sans recompilation
- ⚡ **Performance** : Box-shadow natif optimisé
- 🎭 **Ombres colorées** : Support des ombres avec teintes personnalisées
- 📱 **Responsive** : Ombres adaptables selon la taille d'écran
- 🖱️ **Effets interactifs** : Hover, focus, active states

## 🚀 Installation

### Code SCSS

```scss
// _shadow-wrapper.scss

// Échelle d'ombres prédéfinies (inspirée de Tailwind/Material Design)
$shadow-scale: (
  "none": none,
  "xs": (
    0 1px 2px 0 rgba(0, 0, 0, 0.05),
  ),
  "sm": (
    0 1px 3px 0 rgba(0, 0, 0, 0.1),
    0 1px 2px 0 rgba(0, 0, 0, 0.06),
  ),
  "md": (
    0 4px 6px -1px rgba(0, 0, 0, 0.1),
    0 2px 4px -1px rgba(0, 0, 0, 0.06),
  ),
  "lg": (
    0 10px 15px -3px rgba(0, 0, 0, 0.1),
    0 4px 6px -2px rgba(0, 0, 0, 0.05),
  ),
  "xl": (
    0 20px 25px -5px rgba(0, 0, 0, 0.1),
    0 10px 10px -5px rgba(0, 0, 0, 0.04),
  ),
  "2xl": (
    0 25px 50px -12px rgba(0, 0, 0, 0.25),
  ),
  "inner": (
    inset 0 2px 4px 0 rgba(0, 0, 0, 0.06),
  ),
);

.shadow-wrapper {
  // Variables par défaut
  --shadow-color: 0, 0, 0; // RGB de la couleur (sans alpha)
  --shadow-opacity: 0.1; // Opacité de l'ombre
  --shadow-size: md; // Taille de l'ombre

  // Application de l'ombre par défaut (medium)
  box-shadow: 0 4px 6px -1px rgba(var(--shadow-color), calc(var(
              --shadow-opacity
            ) * 1)), 0 2px 4px -1px rgba(var(--shadow-color), calc(var(
              --shadow-opacity
            ) * 0.6));

  // Transition smooth pour effets hover
  transition: box-shadow 0.3s ease;
}

// Variantes de taille prédéfinies
.shadow-wrapper--none {
  box-shadow: none;
}

.shadow-wrapper--xs {
  box-shadow: 0 1px 2px 0 rgba(var(--shadow-color), calc(var(--shadow-opacity) *
          0.5));
}

.shadow-wrapper--sm {
  box-shadow: 0 1px 3px 0 rgba(var(--shadow-color), calc(var(--shadow-opacity) *
            1)), 0 1px 2px 0 rgba(var(--shadow-color), calc(var(
              --shadow-opacity
            ) * 0.6));
}

.shadow-wrapper--md {
  // Défaut (déjà défini)
  box-shadow: 0 4px 6px -1px rgba(var(--shadow-color), calc(var(
              --shadow-opacity
            ) * 1)), 0 2px 4px -1px rgba(var(--shadow-color), calc(var(
              --shadow-opacity
            ) * 0.6));
}

.shadow-wrapper--lg {
  box-shadow: 0 10px 15px -3px rgba(var(--shadow-color), calc(var(
              --shadow-opacity
            ) * 1)), 0 4px 6px -2px rgba(var(--shadow-color), calc(var(
              --shadow-opacity
            ) * 0.5));
}

.shadow-wrapper--xl {
  box-shadow: 0 20px 25px -5px rgba(var(--shadow-color), calc(var(
              --shadow-opacity
            ) * 1)), 0 10px 10px -5px rgba(var(--shadow-color), calc(var(
              --shadow-opacity
            ) * 0.4));
}

.shadow-wrapper--2xl {
  box-shadow: 0 25px 50px -12px rgba(var(--shadow-color), calc(var(
            --shadow-opacity
          ) * 2.5));
}

// Ombre intérieure
.shadow-wrapper--inner {
  box-shadow: inset 0 2px 4px 0 rgba(var(--shadow-color), calc(var(
            --shadow-opacity
          ) * 0.6));
}

// Effets hover
.shadow-wrapper--hover-lift {
  &:hover {
    box-shadow: 0 20px 25px -5px rgba(var(--shadow-color), calc(var(
                --shadow-opacity
              ) * 1.2)), 0 10px 10px -5px rgba(var(--shadow-color), calc(var(
                --shadow-opacity
              ) * 0.5));
    transform: translateY(-2px);
  }
}

.shadow-wrapper--hover-grow {
  &:hover {
    box-shadow: 0 25px 50px -12px rgba(var(--shadow-color), calc(var(
              --shadow-opacity
            ) * 3));
    transform: scale(1.02);
  }
}

.shadow-wrapper--hover-none {
  &:hover {
    box-shadow: none;
  }
}

// Ombres colorées prédéfinies
.shadow-wrapper--blue {
  --shadow-color: 59, 130, 246; // Blue-500
}

.shadow-wrapper--purple {
  --shadow-color: 139, 92, 246; // Purple-500
}

.shadow-wrapper--pink {
  --shadow-color: 236, 72, 153; // Pink-500
}

.shadow-wrapper--green {
  --shadow-color: 34, 197, 94; // Green-500
}

.shadow-wrapper--red {
  --shadow-color: 239, 68, 68; // Red-500
}

.shadow-wrapper--orange {
  --shadow-color: 249, 115, 22; // Orange-500
}

.shadow-wrapper--yellow {
  --shadow-color: 234, 179, 8; // Yellow-500
}

// Ombres soft (opacité réduite)
.shadow-wrapper--soft {
  --shadow-opacity: 0.05;
}

// Ombres hard (opacité augmentée)
.shadow-wrapper--hard {
  --shadow-opacity: 0.2;
}

// Ombres diffuses (blur plus important)
.shadow-wrapper--diffuse {
  box-shadow: 0 10px 40px -5px rgba(var(--shadow-color), calc(var(
              --shadow-opacity
            ) * 1.5)), 0 5px 20px -5px rgba(var(--shadow-color), calc(var(
              --shadow-opacity
            ) * 0.8));
}

// Ombres nettes (sans blur)
.shadow-wrapper--sharp {
  box-shadow: 0 4px 0 0 rgba(var(--shadow-color), calc(var(--shadow-opacity) * 1));
}

// Glow effect
.shadow-wrapper--glow {
  box-shadow: 0 0 20px rgba(var(--shadow-color), calc(var(--shadow-opacity) * 2)),
    0 0 40px rgba(var(--shadow-color), calc(var(--shadow-opacity) * 1));
}

// Ombre en 3D
.shadow-wrapper--3d {
  box-shadow: 0 1px 0 rgba(var(--shadow-color), 0.1), 0 2px 0 rgba(var(--shadow-color), 0.09),
    0 3px 0 rgba(var(--shadow-color), 0.08), 0 4px 0 rgba(var(--shadow-color), 0.07),
    0 5px 0 rgba(var(--shadow-color), 0.06), 0 6px 0 rgba(var(--shadow-color), 0.05),
    0 8px 10px rgba(var(--shadow-color), 0.1);
}
```

### Import dans votre projet

```scss
// Dans styles.scss
@import "utilities/shadow-wrapper";
```

## 💡 Utilisation de base

### Exemple 1 : Card simple avec ombre

```html
<div class="shadow-wrapper">
  <h3>Card avec ombre</h3>
  <p>Contenu de la card</p>
</div>
```

### Exemple 2 : Card avec ombre large

```html
<div class="shadow-wrapper shadow-wrapper--lg">
  <h3>Card avec ombre large</h3>
  <p>Plus de profondeur visuelle</p>
</div>
```

### Exemple 3 : Ombre personnalisée

```html
<!-- Ombre bleue avec opacité personnalisée -->
<div
  class="shadow-wrapper"
  style="--shadow-color: 59, 130, 246; --shadow-opacity: 0.3"
>
  <h3>Card avec ombre bleue</h3>
</div>
```

### Exemple 4 : Effet hover lift

```html
<div class="shadow-wrapper shadow-wrapper--hover-lift">
  <h3>Card interactive</h3>
  <p>Survole-moi !</p>
</div>
```

## 📊 Paramètres

| Variable           | Type             | Défaut    | Description                                 |
| ------------------ | ---------------- | --------- | ------------------------------------------- |
| `--shadow-color`   | RGB (sans alpha) | `0, 0, 0` | Couleur de l'ombre en RGB                   |
| `--shadow-opacity` | number           | `0.1`     | Opacité de l'ombre (0 à 1)                  |
| `--shadow-size`    | keyword          | `md`      | Taille prédéfinie (xs, sm, md, lg, xl, 2xl) |

### Échelle des ombres

| Classe    | Usage                   | Élévation |
| --------- | ----------------------- | --------- |
| `--none`  | Pas d'ombre             | Plat      |
| `--xs`    | Ombre très subtile      | 1dp       |
| `--sm`    | Ombre légère            | 2dp       |
| `--md`    | Ombre standard (défaut) | 4dp       |
| `--lg`    | Ombre prononcée         | 8dp       |
| `--xl`    | Ombre forte             | 16dp      |
| `--2xl`   | Ombre dramatique        | 24dp      |
| `--inner` | Ombre intérieure        | Concave   |

### Valeurs courantes pour `--shadow-color` (RGB)

```css
/* Couleurs neutres */
--shadow-color: 0, 0, 0; /* Noir (défaut) */
--shadow-color: 75, 85, 99; /* Gray-600 */
--shadow-color: 17, 24, 39; /* Gray-900 */

/* Couleurs de marque */
--shadow-color: 59, 130, 246; /* Blue-500 */
--shadow-color: 139, 92, 246; /* Purple-500 */
--shadow-color: 236, 72, 153; /* Pink-500 */
--shadow-color: 34, 197, 94; /* Green-500 */
--shadow-color: 239, 68, 68; /* Red-500 */
--shadow-color: 249, 115, 22; /* Orange-500 */

/* Comment obtenir RGB d'une couleur hex */
/* #3B82F6 -> RGB(59, 130, 246) */
```

### Valeurs pour `--shadow-opacity`

```css
--shadow-opacity: 0.05; /* Très subtil */
--shadow-opacity: 0.1; /* Standard (défaut) */
--shadow-opacity: 0.15; /* Prononcé */
--shadow-opacity: 0.2; /* Fort */
--shadow-opacity: 0.3; /* Très fort */
```

## 📚 Exemples détaillés

### Exemple 1 : Cards avec différentes ombres

```html
<div class="cards-grid">
  <div class="card shadow-wrapper shadow-wrapper--xs">
    <h3>Ombre XS</h3>
    <p>Très subtile, presque invisible</p>
  </div>

  <div class="card shadow-wrapper shadow-wrapper--sm">
    <h3>Ombre SM</h3>
    <p>Légère élévation</p>
  </div>

  <div class="card shadow-wrapper shadow-wrapper--md">
    <h3>Ombre MD</h3>
    <p>Élévation standard</p>
  </div>

  <div class="card shadow-wrapper shadow-wrapper--lg">
    <h3>Ombre LG</h3>
    <p>Élévation prononcée</p>
  </div>

  <div class="card shadow-wrapper shadow-wrapper--xl">
    <h3>Ombre XL</h3>
    <p>Forte élévation</p>
  </div>

  <div class="card shadow-wrapper shadow-wrapper--2xl">
    <h3>Ombre 2XL</h3>
    <p>Élévation dramatique</p>
  </div>
</div>

<style>
  .cards-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 2rem;
    padding: 2rem;
  }

  .card {
    padding: 2rem;
    background: white;
    border-radius: 0.5rem;
  }

  .card h3 {
    margin: 0 0 0.5rem 0;
    font-size: 1.25rem;
  }

  .card p {
    margin: 0;
    color: #6b7280;
    font-size: 0.875rem;
  }
</style>
```

### Exemple 2 : Modal avec ombre forte

```html
<div class="modal-overlay">
  <div class="modal shadow-wrapper shadow-wrapper--2xl">
    <header class="modal-header">
      <h2>Confirmer l'action</h2>
      <button class="close-btn">×</button>
    </header>

    <div class="modal-content">
      <p>Êtes-vous sûr de vouloir continuer cette action ?</p>
    </div>

    <footer class="modal-footer">
      <button class="btn btn-secondary">Annuler</button>
      <button class="btn btn-primary">Confirmer</button>
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
    border-radius: 0.75rem;
    width: 90%;
    max-width: 500px;
  }

  .modal-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1.5rem;
    border-bottom: 1px solid #e5e7eb;
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

  .close-btn {
    font-size: 2rem;
    border: none;
    background: none;
    cursor: pointer;
    color: #6b7280;
  }
</style>
```

### Exemple 3 : Cards avec ombres colorées

```html
<div class="feature-cards">
  <div
    class="feature-card shadow-wrapper shadow-wrapper--lg shadow-wrapper--blue"
  >
    <div class="icon">🚀</div>
    <h3>Performance</h3>
    <p>Vitesse et efficacité maximales</p>
  </div>

  <div
    class="feature-card shadow-wrapper shadow-wrapper--lg shadow-wrapper--purple"
  >
    <div class="icon">🎨</div>
    <h3>Design</h3>
    <p>Interface moderne et élégante</p>
  </div>

  <div
    class="feature-card shadow-wrapper shadow-wrapper--lg shadow-wrapper--green"
  >
    <div class="icon">🔒</div>
    <h3>Sécurité</h3>
    <p>Protection des données garantie</p>
  </div>

  <div
    class="feature-card shadow-wrapper shadow-wrapper--lg shadow-wrapper--orange"
  >
    <div class="icon">📈</div>
    <h3>Analytics</h3>
    <p>Insights en temps réel</p>
  </div>
</div>

<style>
  .feature-cards {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 2rem;
    padding: 2rem;
  }

  .feature-card {
    padding: 2rem;
    background: white;
    border-radius: 0.75rem;
    text-align: center;
    transition: all 0.3s ease;
  }

  .feature-card:hover {
    transform: translateY(-4px);
  }

  .icon {
    font-size: 3rem;
    margin-bottom: 1rem;
  }

  .feature-card h3 {
    margin: 0 0 0.5rem 0;
    font-size: 1.5rem;
  }

  .feature-card p {
    margin: 0;
    color: #6b7280;
  }
</style>
```

### Exemple 4 : Buttons avec ombres interactives

```html
<div class="buttons-demo">
  <button
    class="btn shadow-wrapper shadow-wrapper--sm shadow-wrapper--hover-lift"
  >
    Hover Lift
  </button>

  <button
    class="btn shadow-wrapper shadow-wrapper--md shadow-wrapper--hover-grow"
  >
    Hover Grow
  </button>

  <button
    class="btn shadow-wrapper shadow-wrapper--lg"
    style="--shadow-color: 59, 130, 246"
  >
    Blue Shadow
  </button>

  <button
    class="btn shadow-wrapper shadow-wrapper--glow shadow-wrapper--purple"
  >
    Glow Effect
  </button>

  <button class="btn shadow-wrapper shadow-wrapper--3d">3D Effect</button>
</div>

<style>
  .buttons-demo {
    display: flex;
    flex-wrap: wrap;
    gap: 1rem;
    padding: 2rem;
  }

  .btn {
    padding: 0.75rem 1.5rem;
    background: white;
    border: 1px solid #e5e7eb;
    border-radius: 0.5rem;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.3s ease;
  }

  .btn:hover {
    background: #f9fafb;
  }
</style>
```

### Exemple 5 : Image gallery avec ombres

```html
<div class="gallery">
  <div
    class="gallery-item shadow-wrapper shadow-wrapper--md shadow-wrapper--hover-lift"
  >
    <img src="image1.jpg" alt="Image 1" />
    <div class="gallery-caption">
      <h4>Image Title</h4>
      <p>Description courte</p>
    </div>
  </div>

  <div
    class="gallery-item shadow-wrapper shadow-wrapper--md shadow-wrapper--hover-lift"
  >
    <img src="image2.jpg" alt="Image 2" />
    <div class="gallery-caption">
      <h4>Image Title</h4>
      <p>Description courte</p>
    </div>
  </div>

  <div
    class="gallery-item shadow-wrapper shadow-wrapper--md shadow-wrapper--hover-lift"
  >
    <img src="image3.jpg" alt="Image 3" />
    <div class="gallery-caption">
      <h4>Image Title</h4>
      <p>Description courte</p>
    </div>
  </div>
</div>

<style>
  .gallery {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
    gap: 2rem;
    padding: 2rem;
  }

  .gallery-item {
    border-radius: 0.5rem;
    overflow: hidden;
    background: white;
    cursor: pointer;
  }

  .gallery-item img {
    width: 100%;
    height: 250px;
    object-fit: cover;
  }

  .gallery-caption {
    padding: 1rem;
  }

  .gallery-caption h4 {
    margin: 0 0 0.5rem 0;
  }

  .gallery-caption p {
    margin: 0;
    color: #6b7280;
    font-size: 0.875rem;
  }
</style>
```

### Exemple 6 : Dropdown menu

```html
<div class="dropdown">
  <button class="dropdown-trigger shadow-wrapper shadow-wrapper--sm">
    Menu ▼
  </button>

  <div class="dropdown-content shadow-wrapper shadow-wrapper--xl">
    <a href="#">Dashboard</a>
    <a href="#">Profile</a>
    <a href="#">Settings</a>
    <hr />
    <a href="#">Logout</a>
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
  }

  .dropdown-content {
    position: absolute;
    top: calc(100% + 0.5rem);
    left: 0;
    min-width: 200px;
    background: white;
    border-radius: 0.5rem;
    overflow: hidden;
    display: none;
  }

  .dropdown:hover .dropdown-content {
    display: block;
  }

  .dropdown-content a {
    display: block;
    padding: 0.75rem 1rem;
    text-decoration: none;
    color: #374151;
    transition: background 0.2s;
  }

  .dropdown-content a:hover {
    background: #f3f4f6;
  }

  .dropdown-content hr {
    margin: 0.5rem 0;
    border: none;
    border-top: 1px solid #e5e7eb;
  }
</style>
```

### Exemple 7 : Pricing cards

```html
<div class="pricing-cards">
  <div class="pricing-card shadow-wrapper shadow-wrapper--sm">
    <h3>Starter</h3>
    <div class="price">
      <span class="amount">29€</span>
      <span class="period">/mois</span>
    </div>
    <ul class="features">
      <li>✓ 5 projets</li>
      <li>✓ 10 Go stockage</li>
      <li>✓ Support email</li>
    </ul>
    <button class="btn">Choisir</button>
  </div>

  <div
    class="pricing-card pricing-card--featured shadow-wrapper shadow-wrapper--xl shadow-wrapper--blue"
  >
    <div class="badge">Populaire</div>
    <h3>Pro</h3>
    <div class="price">
      <span class="amount">79€</span>
      <span class="period">/mois</span>
    </div>
    <ul class="features">
      <li>✓ Projets illimités</li>
      <li>✓ 100 Go stockage</li>
      <li>✓ Support prioritaire</li>
    </ul>
    <button class="btn btn-primary">Choisir</button>
  </div>

  <div class="pricing-card shadow-wrapper shadow-wrapper--sm">
    <h3>Enterprise</h3>
    <div class="price">
      <span class="amount">Custom</span>
    </div>
    <ul class="features">
      <li>✓ Tout illimité</li>
      <li>✓ SLA garanti</li>
      <li>✓ Support dédié</li>
    </ul>
    <button class="btn">Nous contacter</button>
  </div>
</div>

<style>
  .pricing-cards {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 2rem;
    padding: 2rem;
    align-items: start;
  }

  .pricing-card {
    background: white;
    border-radius: 0.75rem;
    padding: 2rem;
    text-align: center;
    position: relative;
  }

  .pricing-card--featured {
    transform: scale(1.05);
    border: 2px solid #3b82f6;
  }

  .badge {
    position: absolute;
    top: -12px;
    left: 50%;
    transform: translateX(-50%);
    background: #3b82f6;
    color: white;
    padding: 0.25rem 1rem;
    border-radius: 9999px;
    font-size: 0.875rem;
    font-weight: 600;
  }

  .price {
    margin: 1.5rem 0;
  }

  .amount {
    font-size: 3rem;
    font-weight: 700;
  }

  .features {
    list-style: none;
    padding: 0;
    margin: 1.5rem 0;
  }

  .features li {
    padding: 0.5rem 0;
  }
</style>
```

## 🎨 Personnalisation avancée

### Ombres avec dégradé de couleur

```html
<div
  class="card-gradient shadow-wrapper"
  style="--shadow-color: 59, 130, 246; --shadow-opacity: 0.5"
>
  <h3>Card avec ombre dégradée</h3>
</div>

<style>
  .card-gradient {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
    padding: 2rem;
    border-radius: 0.75rem;
  }
</style>
```

### Ombre responsive

```html
<div class="card-responsive shadow-wrapper">
  <h3>Ombre adaptative</h3>
</div>

<style>
  .card-responsive {
    /* Mobile : ombre légère */
    --shadow-opacity: 0.05;
  }

  @media (min-width: 768px) {
    .card-responsive {
      /* Tablet : ombre normale */
      --shadow-opacity: 0.1;
    }
  }

  @media (min-width: 1024px) {
    .card-responsive {
      /* Desktop : ombre prononcée */
      --shadow-opacity: 0.15;
    }
  }
</style>
```

### Animation d'ombre au scroll

```html
<div class="card-scroll shadow-wrapper shadow-wrapper--sm" id="scrollCard">
  <h3>Scroll pour voir l'effet</h3>
</div>

<script>
  const card = document.getElementById("scrollCard");

  window.addEventListener("scroll", () => {
    const scrolled = window.scrollY;
    const opacity = Math.min(0.3, scrolled / 1000);
    card.style.setProperty("--shadow-opacity", opacity);
  });
</script>
```

### Dark mode avec ombres adaptées

```scss
.shadow-wrapper {
  --shadow-color: 0, 0, 0;
  --shadow-opacity: 0.1;

  @media (prefers-color-scheme: dark) {
    --shadow-color: 255, 255, 255; // Ombre blanche en dark mode
    --shadow-opacity: 0.05; // Plus subtile
  }
}
```

### Ombre avec bordure subtile

```html
<div class="card-bordered shadow-wrapper shadow-wrapper--md">
  <h3>Card avec bordure + ombre</h3>
</div>

<style>
  .card-bordered {
    border: 1px solid rgba(0, 0, 0, 0.05);
    background: white;
    padding: 2rem;
    border-radius: 0.5rem;
  }
</style>
```

## 🎯 Cas d'usage courants

### 1. Cards de contenu

```html
<div class="card shadow-wrapper shadow-wrapper--md">
  <h3>Titre</h3>
  <p>Contenu</p>
</div>
```

### 2. Modals / Dialogs

```html
<div class="modal shadow-wrapper shadow-wrapper--2xl">
  <h2>Modal</h2>
</div>
```

### 3. Tooltips

```html
<div class="tooltip shadow-wrapper shadow-wrapper--lg">Info bulle</div>
```

### 4. Dropdowns / Menus

```html
<div class="dropdown shadow-wrapper shadow-wrapper--xl">
  <a href="#">Item 1</a>
</div>
```

### 5. Images / Gallery

```html
<img class="shadow-wrapper shadow-wrapper--md" src="image.jpg" />
```

### 6. Buttons (effet hover)

```html
<button class="shadow-wrapper shadow-wrapper--sm shadow-wrapper--hover-lift">
  Click me
</button>
```

### 7. Pricing cards (featured)

```html
<div class="pricing shadow-wrapper shadow-wrapper--xl shadow-wrapper--blue">
  Premium
</div>
```

## 🔧 Combinaison avec autres utilitaires

### Avec Container Fluid

```html
<div class="container-fluid container-fluid--lg">
  <div class="shadow-wrapper shadow-wrapper--lg">
    <h2>Card dans un container</h2>
  </div>
</div>
```

### Avec Grid Wrapper

```html
<div class="grid-wrapper" style="--cols: 3; --gap: 2rem">
  <div class="shadow-wrapper shadow-wrapper--md shadow-wrapper--hover-lift">
    Card 1
  </div>
  <div class="shadow-wrapper shadow-wrapper--md shadow-wrapper--hover-lift">
    Card 2
  </div>
  <div class="shadow-wrapper shadow-wrapper--md shadow-wrapper--hover-lift">
    Card 3
  </div>
</div>
```

### Avec Text Balance

```html
<div class="shadow-wrapper shadow-wrapper--lg">
  <h2 class="text-balance text-balance--center">
    Titre équilibré dans une card avec ombre
  </h2>
</div>
```

## 📱 Comportement responsive

### Stratégie d'ombres responsive

```scss
// Ombres plus légères sur mobile (performance)
.shadow-wrapper {
  @media (max-width: 640px) {
    --shadow-opacity: 0.05;
  }

  @media (min-width: 641px) and (max-width: 1024px) {
    --shadow-opacity: 0.1;
  }

  @media (min-width: 1025px) {
    --shadow-opacity: 0.15;
  }
}
```

### Désactiver les ombres sur mobile

```scss
.shadow-wrapper--no-mobile {
  @media (max-width: 640px) {
    box-shadow: none;
    border: 1px solid #e5e7eb; // Bordure à la place
  }
}
```

## ⚡ Performance & Bonnes pratiques

### ✅ À faire

```html
<!-- Bon : Utiliser l'échelle prédéfinie -->
<div class="shadow-wrapper shadow-wrapper--md">
  <!-- Bon : Ombres subtiles par défaut -->
  <div class="shadow-wrapper" style="--shadow-opacity: 0.1">
    <!-- Bon : Transition smooth pour hover -->
    <div class="shadow-wrapper shadow-wrapper--hover-lift">
      <!-- Bon : RGB pour la couleur (permet alpha channel) -->
      <div class="shadow-wrapper" style="--shadow-color: 59, 130, 246"></div>
    </div>
  </div>
</div>
```

### ❌ À éviter

```html
<!-- Mauvais : Trop d'ombres empilées -->
<div style="box-shadow: 0 1px 3px, 0 2px 6px, 0 3px 9px, 0 4px 12px">
  <!-- Mauvais : Ombre trop forte partout -->
  <div class="shadow-wrapper" style="--shadow-opacity: 0.8">
    <!-- Mauvais : Ombre sans transition -->
    <div class="shadow-wrapper" style="transition: none">
      <!-- Mauvais : Utiliser directement box-shadow au lieu des variables -->
      <div style="box-shadow: 0 4px 6px rgba(0,0,0,0.1)"></div>
    </div>
  </div>
</div>
```

### Conseils de performance

```scss
// ✅ Limiter le nombre d'ombres par élément
.shadow-wrapper--md {
  // 2 ombres max (une principale + une d'accentuation)
  box-shadow: 0 4px 6px -1px rgba(var(--shadow-color), var(--shadow-opacity)), 0
      2px 4px -1px rgba(var(--shadow-color), calc(var(--shadow-opacity) * 0.6));
}

// ❌ Éviter trop d'ombres (impact performance)
.bad-shadow {
  box-shadow: 0 1px 1px rgba(0, 0, 0, 0.1), 0 2px 2px rgba(0, 0, 0, 0.1),
    0 3px 3px rgba(0, 0, 0, 0.1), 0 4px 4px rgba(0, 0, 0, 0.1),
    0 5px 5px rgba(0, 0, 0, 0.1); // Trop !
}

// ✅ Utiliser will-change pour animations
.shadow-wrapper--hover-lift {
  will-change: box-shadow, transform;

  &:hover {
    // Animation smooth
  }
}
```

### Optimisation pour mobile

```scss
// Réduire la complexité sur mobile
@media (max-width: 640px) {
  .shadow-wrapper {
    // Ombre simple (1 couche au lieu de 2)
    box-shadow: 0 2px 4px rgba(var(--shadow-color), var(--shadow-opacity));
  }
}
```

## 🌐 Compatibilité navigateurs

| Navigateur | Version minimale | Support    |
| ---------- | ---------------- | ---------- |
| Chrome     | 10+              | ✅ Complet |
| Firefox    | 4+               | ✅ Complet |
| Safari     | 5.1+             | ✅ Complet |
| Edge       | 12+              | ✅ Complet |
| Opera      | 10.5+            | ✅ Complet |
| IE         | 9+               | ✅ Complet |

**Note** : `box-shadow` est une propriété très bien supportée depuis longtemps. Les variables CSS nécessitent des navigateurs modernes (2016+).

### Fallback pour anciens navigateurs

```scss
.shadow-wrapper {
  // Fallback statique pour IE/anciens navigateurs
  box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);

  // Variables CSS (override si supporté)
  @supports (--css: variables) {
    box-shadow: 0 4px 6px -1px rgba(var(--shadow-color), var(--shadow-opacity)),
      0 2px 4px -1px rgba(var(--shadow-color), calc(var(--shadow-opacity) * 0.6));
  }
}
```

## 🐛 Troubleshooting

### Problème : L'ombre ne s'affiche pas

**Solution** : Vérifiez le z-index et le background

```css
/* L'élément doit avoir un background */
.shadow-wrapper {
  background: white; /* Important ! */
  box-shadow: ...;
}

/* Vérifiez le z-index si masqué par autre élément */
.shadow-wrapper {
  position: relative;
  z-index: 1;
}
```

### Problème : L'ombre est trop sombre/claire

**Solution** : Ajustez l'opacité

```css
/* Trop sombre */
--shadow-opacity: 0.3; /* Réduire à 0.1 ou 0.15 */

/* Trop claire */
--shadow-opacity: 0.05; /* Augmenter à 0.1 ou 0.15 */
```

### Problème : La couleur personnalisée ne fonctionne pas

**Solution** : Utilisez le format RGB (sans "rgb()")

```css
/* ❌ Mauvais */
--shadow-color: rgb(59, 130, 246);

/* ✅ Bon */
--shadow-color: 59, 130, 246;
```

### Problème : Performance médiocre sur mobile

**Solution** : Simplifiez les ombres sur mobile

```scss
@media (max-width: 640px) {
  .shadow-wrapper {
    // Ombre plus simple
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }

  // Désactiver les animations coûteuses
  .shadow-wrapper--hover-lift {
    transform: none !important;
  }
}
```

## 📦 Classes complètes disponibles

```scss
// Tailles
.shadow-wrapper--none {
  box-shadow: none;
}
.shadow-wrapper--xs {
  /* 1dp */
}
.shadow-wrapper--sm {
  /* 2dp */
}
.shadow-wrapper--md {
  /* 4dp - défaut */
}
.shadow-wrapper--lg {
  /* 8dp */
}
.shadow-wrapper--xl {
  /* 16dp */
}
.shadow-wrapper--2xl {
  /* 24dp */
}
.shadow-wrapper--inner {
  /* Inset */
}

// Effets hover
.shadow-wrapper--hover-lift {
  /* Lift + augmente ombre */
}
.shadow-wrapper--hover-grow {
  /* Scale + augmente ombre */
}
.shadow-wrapper--hover-none {
  /* Supprime ombre */
}

// Couleurs prédéfinies
.shadow-wrapper--blue {
  --shadow-color: 59, 130, 246;
}
.shadow-wrapper--purple {
  --shadow-color: 139, 92, 246;
}
.shadow-wrapper--pink {
  --shadow-color: 236, 72, 153;
}
.shadow-wrapper--green {
  --shadow-color: 34, 197, 94;
}
.shadow-wrapper--red {
  --shadow-color: 239, 68, 68;
}
.shadow-wrapper--orange {
  --shadow-color: 249, 115, 22;
}
.shadow-wrapper--yellow {
  --shadow-color: 234, 179, 8;
}

// Intensité
.shadow-wrapper--soft {
  --shadow-opacity: 0.05;
}
.shadow-wrapper--hard {
  --shadow-opacity: 0.2;
}

// Styles spéciaux
.shadow-wrapper--diffuse {
  /* Blur étendu */
}
.shadow-wrapper--sharp {
  /* Sans blur */
}
.shadow-wrapper--glow {
  /* Effet lumineux */
}
.shadow-wrapper--3d {
  /* Effet 3D */
}
```

## 🎓 Ressources complémentaires

- [Box Shadow - MDN](https://developer.mozilla.org/fr/docs/Web/CSS/box-shadow)
- [CSS Box Shadow Generator](https://cssgenerator.org/box-shadow-css-generator.html)
- [Material Design Elevation](https://material.io/design/environment/elevation.html)
- [Smooth Shadow Tool](https://shadows.brumm.af/)

## 📝 Changelog

- **v1.0** - Version initiale avec échelle d'ombres de base
- **v1.1** - Ajout des ombres colorées (blue, purple, green, etc.)
- **v1.2** - Support des effets hover (lift, grow)
- **v1.3** - Ajout des styles spéciaux (glow, 3d, diffuse, sharp)
- **v1.4** - Amélioration des performances avec will-change
- **v1.5** - Support des ombres responsive

---

**Made with ❤️ for depth and dimension**
