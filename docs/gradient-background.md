# Gradient Background Utility

> Créez des arrière-plans avec dégradés modernes et personnalisables pour des interfaces visuellement captivantes

## 📋 Description

**Gradient Background** est un utilitaire CSS qui permet de créer facilement des arrière-plans avec dégradés linéaires, radiaux ou coniques. Avec un système de variables CSS flexible, vous pouvez personnaliser les couleurs, directions, et positions pour obtenir des effets visuels impressionnants adaptés à votre design.

### ✨ Caractéristiques principales

- 🎨 **Dégradés multiples** : Linear, radial, conic
- 🎯 **Angles personnalisables** : Contrôle total de la direction
- 🔧 **Variables CSS** : Couleurs et positions ajustables
- 🌈 **Palette prédéfinie** : Dégradés populaires prêts à l'emploi
- ⚡ **Performance** : CSS natif optimisé
- 🎭 **Animations** : Dégradés animés possibles
- 📱 **Responsive** : S'adapte à tous les écrans

## 🚀 Installation

### Code SCSS

```scss
// _gradient-background.scss

// Palette de dégradés prédéfinis
$gradient-presets: (
  "sunset": (
    linear-gradient(135deg, #667eea 0%, #764ba2 100%),
  ),
  "ocean": (
    linear-gradient(135deg, #2e3192 0%, #1bffff 100%),
  ),
  "fire": (
    linear-gradient(135deg, #f093fb 0%, #f5576c 100%),
  ),
  "forest": (
    linear-gradient(135deg, #134e5e 0%, #71b280 100%),
  ),
  "candy": (
    linear-gradient(135deg, #fa709a 0%, #fee140 100%),
  ),
  "purple": (
    linear-gradient(135deg, #667eea 0%, #764ba2 100%),
  ),
  "blue": (
    linear-gradient(135deg, #3b82f6 0%, #1e40af 100%),
  ),
  "green": (
    linear-gradient(135deg, #10b981 0%, #059669 100%),
  ),
  "orange": (
    linear-gradient(135deg, #f59e0b 0%, #ea580c 100%),
  ),
  "pink": (
    linear-gradient(135deg, #ec4899 0%, #db2777 100%),
  ),
);

.gradient-bg {
  // Variables par défaut
  --gradient-color-1: #667eea; // Première couleur
  --gradient-color-2: #764ba2; // Deuxième couleur
  --gradient-color-3: null; // Troisième couleur (optionnelle)
  --gradient-angle: 135deg; // Angle du dégradé
  --gradient-type: linear; // Type (linear, radial, conic)

  // Application du dégradé linéaire par défaut
  background: linear-gradient(
    var(--gradient-angle),
    var(--gradient-color-1),
    var(--gradient-color-2)
  );

  // Assure que le dégradé couvre tout
  background-size: cover;
  background-attachment: fixed;
}

// Dégradés linéaires avec directions prédéfinies
.gradient-bg--to-right {
  --gradient-angle: 90deg;
}

.gradient-bg--to-left {
  --gradient-angle: 270deg;
}

.gradient-bg--to-bottom {
  --gradient-angle: 180deg;
}

.gradient-bg--to-top {
  --gradient-angle: 0deg;
}

.gradient-bg--diagonal {
  --gradient-angle: 135deg; // Défaut
}

.gradient-bg--diagonal-reverse {
  --gradient-angle: 45deg;
}

// Dégradé radial
.gradient-bg--radial {
  background: radial-gradient(
    circle at center,
    var(--gradient-color-1),
    var(--gradient-color-2)
  );
}

.gradient-bg--radial-top {
  background: radial-gradient(
    circle at top,
    var(--gradient-color-1),
    var(--gradient-color-2)
  );
}

.gradient-bg--radial-bottom {
  background: radial-gradient(
    circle at bottom,
    var(--gradient-color-1),
    var(--gradient-color-2)
  );
}

// Dégradé conique
.gradient-bg--conic {
  background: conic-gradient(
    from var(--gradient-angle, 0deg),
    var(--gradient-color-1),
    var(--gradient-color-2),
    var(--gradient-color-1)
  );
}

// Dégradés prédéfinis populaires
.gradient-bg--sunset {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
}

.gradient-bg--ocean {
  background: linear-gradient(135deg, #2e3192 0%, #1bffff 100%);
}

.gradient-bg--fire {
  background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
}

.gradient-bg--forest {
  background: linear-gradient(135deg, #134e5e 0%, #71b280 100%);
}

.gradient-bg--candy {
  background: linear-gradient(135deg, #fa709a 0%, #fee140 100%);
}

.gradient-bg--purple {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
}

.gradient-bg--blue {
  background: linear-gradient(135deg, #3b82f6 0%, #1e40af 100%);
}

.gradient-bg--green {
  background: linear-gradient(135deg, #10b981 0%, #059669 100%);
}

.gradient-bg--orange {
  background: linear-gradient(135deg, #f59e0b 0%, #ea580c 100%);
}

.gradient-bg--pink {
  background: linear-gradient(135deg, #ec4899 0%, #db2777 100%);
}

.gradient-bg--dark {
  background: linear-gradient(135deg, #1f2937 0%, #111827 100%);
}

.gradient-bg--light {
  background: linear-gradient(135deg, #f9fafb 0%, #e5e7eb 100%);
}

// Dégradés avec 3 couleurs
.gradient-bg--triple {
  background: linear-gradient(
    var(--gradient-angle, 135deg),
    var(--gradient-color-1),
    var(--gradient-color-2),
    var(--gradient-color-3)
  );
}

// Dégradés avec effet mesh
.gradient-bg--mesh {
  background: radial-gradient(
      at 40% 20%,
      var(--gradient-color-1) 0px,
      transparent 50%
    ), radial-gradient(at 80% 0%, var(--gradient-color-2) 0px, transparent 50%),
    radial-gradient(at 0% 50%, var(--gradient-color-1) 0px, transparent 50%),
    radial-gradient(at 80% 50%, var(--gradient-color-2) 0px, transparent 50%),
    radial-gradient(at 0% 100%, var(--gradient-color-1) 0px, transparent 50%),
    radial-gradient(at 80% 100%, var(--gradient-color-2) 0px, transparent 50%);
}

// Dégradé animé
.gradient-bg--animated {
  background: linear-gradient(
    var(--gradient-angle, 135deg),
    var(--gradient-color-1),
    var(--gradient-color-2)
  );
  background-size: 200% 200%;
  animation: gradientShift 15s ease infinite;
}

@keyframes gradientShift {
  0% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
  100% {
    background-position: 0% 50%;
  }
}

// Overlay patterns
.gradient-bg--with-pattern {
  position: relative;

  &::before {
    content: "";
    position: absolute;
    inset: 0;
    background-image: repeating-linear-gradient(
      45deg,
      transparent,
      transparent 10px,
      rgba(255, 255, 255, 0.05) 10px,
      rgba(255, 255, 255, 0.05) 20px
    );
    pointer-events: none;
  }
}

// Dégradé avec noise texture
.gradient-bg--noise {
  position: relative;

  &::after {
    content: "";
    position: absolute;
    inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 400 400' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noiseFilter'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='3' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noiseFilter)'/%3E%3C/svg%3E");
    opacity: 0.05;
    pointer-events: none;
  }
}
```

### Import dans votre projet

```scss
// Dans styles.scss
@import "utilities/gradient-background";
```

## 💡 Utilisation de base

### Exemple 1 : Dégradé simple

```html
<div class="gradient-bg" style="min-height: 300px; padding: 2rem">
  <h1 style="color: white">Dégradé par défaut</h1>
</div>
```

### Exemple 2 : Dégradé prédéfini

```html
<div
  class="gradient-bg gradient-bg--sunset"
  style="min-height: 300px; padding: 2rem"
>
  <h1 style="color: white">Sunset Gradient</h1>
</div>
```

### Exemple 3 : Dégradé personnalisé

```html
<div
  class="gradient-bg"
  style="--gradient-color-1: #ff6b6b; 
            --gradient-color-2: #4ecdc4; 
            --gradient-angle: 45deg;
            min-height: 300px; 
            padding: 2rem"
>
  <h1 style="color: white">Custom Gradient</h1>
</div>
```

### Exemple 4 : Dégradé radial

```html
<div
  class="gradient-bg gradient-bg--radial"
  style="--gradient-color-1: #667eea; 
            --gradient-color-2: #764ba2;
            min-height: 300px; 
            padding: 2rem"
>
  <h1 style="color: white">Radial Gradient</h1>
</div>
```

## 📊 Paramètres

| Variable             | Type    | Défaut    | Description                     |
| -------------------- | ------- | --------- | ------------------------------- |
| `--gradient-color-1` | color   | `#667eea` | Première couleur du dégradé     |
| `--gradient-color-2` | color   | `#764ba2` | Deuxième couleur du dégradé     |
| `--gradient-color-3` | color   | `null`    | Troisième couleur (optionnelle) |
| `--gradient-angle`   | angle   | `135deg`  | Angle/direction du dégradé      |
| `--gradient-type`    | keyword | `linear`  | Type de dégradé                 |

### Angles prédéfinis

| Classe               | Angle  | Direction  |
| -------------------- | ------ | ---------- |
| `--to-right`         | 90deg  | →          |
| `--to-left`          | 270deg | ←          |
| `--to-bottom`        | 180deg | ↓          |
| `--to-top`           | 0deg   | ↑          |
| `--diagonal`         | 135deg | ↘ (défaut) |
| `--diagonal-reverse` | 45deg  | ↗          |

### Dégradés prédéfinis

| Classe     | Couleurs                 | Style      |
| ---------- | ------------------------ | ---------- |
| `--sunset` | Purple → Violet          | Crépuscule |
| `--ocean`  | Navy → Cyan              | Océan      |
| `--fire`   | Pink → Red               | Feu        |
| `--forest` | Dark green → Light green | Forêt      |
| `--candy`  | Pink → Yellow            | Bonbon     |
| `--purple` | Blue-purple → Purple     | Violet     |
| `--blue`   | Blue → Dark blue         | Bleu       |
| `--green`  | Green → Dark green       | Vert       |
| `--orange` | Orange → Dark orange     | Orange     |
| `--pink`   | Pink → Dark pink         | Rose       |

## 📚 Exemples détaillés

### Exemple 1 : Hero section avec dégradé

```html
<section class="hero gradient-bg gradient-bg--sunset">
  <div class="container-fluid container-fluid--lg">
    <div class="hero-content">
      <h1 class="text-balance text-balance--center">
        Transformez votre vision en réalité
      </h1>
      <p class="lead">Plateforme complète pour créateurs modernes</p>
      <div class="hero-actions">
        <button
          class="btn glass-effect glass-effect--light shadow-wrapper shadow-wrapper--lg"
        >
          Commencer gratuitement
        </button>
        <button class="btn glass-effect glass-effect--transparent">
          En savoir plus
        </button>
      </div>
    </div>
  </div>
</section>

<style>
  .hero {
    min-height: 100vh;
    display: flex;
    align-items: center;
    color: white;
    position: relative;
    overflow: hidden;
  }

  .hero-content {
    text-align: center;
    position: relative;
    z-index: 1;
  }

  .hero h1 {
    font-size: clamp(2.5rem, 6vw, 4rem);
    margin-bottom: 1.5rem;
  }

  .lead {
    font-size: 1.25rem;
    opacity: 0.9;
    margin-bottom: 2rem;
  }

  .hero-actions {
    display: flex;
    gap: 1rem;
    justify-content: center;
    flex-wrap: wrap;
  }

  .btn {
    padding: 1rem 2rem;
    border: none;
    border-radius: 0.75rem;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.3s;
  }

  .btn:hover {
    transform: translateY(-2px);
  }
</style>
```

### Exemple 2 : Cards avec dégradés variés

```html
<div class="gradient-cards">
  <div class="card gradient-bg gradient-bg--blue">
    <div class="card-icon">🚀</div>
    <h3>Performance</h3>
    <p>Vitesse et efficacité maximales pour tous vos projets</p>
  </div>

  <div class="card gradient-bg gradient-bg--purple">
    <div class="card-icon">🎨</div>
    <h3>Design</h3>
    <p>Interface moderne et intuitive pour une expérience optimale</p>
  </div>

  <div class="card gradient-bg gradient-bg--green">
    <div class="card-icon">🔒</div>
    <h3>Sécurité</h3>
    <p>Protection des données avec chiffrement de bout en bout</p>
  </div>

  <div class="card gradient-bg gradient-bg--orange">
    <div class="card-icon">📈</div>
    <h3>Analytics</h3>
    <p>Insights détaillés en temps réel sur vos performances</p>
  </div>
</div>

<style>
  .gradient-cards {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 2rem;
    padding: 4rem 2rem;
    max-width: 1400px;
    margin: 0 auto;
  }

  .card {
    padding: 3rem 2rem;
    border-radius: 1rem;
    color: white;
    text-align: center;
    transition: transform 0.3s ease;
    box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
  }

  .card:hover {
    transform: translateY(-8px);
  }

  .card-icon {
    font-size: 4rem;
    margin-bottom: 1.5rem;
  }

  .card h3 {
    margin: 0 0 1rem 0;
    font-size: 1.75rem;
  }

  .card p {
    margin: 0;
    opacity: 0.9;
    line-height: 1.6;
  }
</style>
```

### Exemple 3 : Section avec dégradé animé

```html
<section
  class="animated-section gradient-bg gradient-bg--animated"
  style="--gradient-color-1: #667eea; --gradient-color-2: #764ba2"
>
  <div class="container-fluid container-fluid--lg">
    <h2 class="section-title">Dégradé Animé</h2>
    <p class="section-description">
      Le dégradé en arrière-plan s'anime doucement
    </p>
  </div>
</section>

<style>
  .animated-section {
    padding: 6rem 2rem;
    color: white;
    text-align: center;
  }

  .section-title {
    font-size: 3rem;
    margin-bottom: 1rem;
  }

  .section-description {
    font-size: 1.25rem;
    opacity: 0.9;
    max-width: 600px;
    margin: 0 auto;
  }
</style>
```

### Exemple 4 : Pricing cards avec dégradés

```html
<section class="pricing gradient-bg gradient-bg--light">
  <div class="container-fluid container-fluid--lg">
    <h2 class="pricing-title">Tarifs Simples</h2>

    <div class="pricing-grid">
      <div class="pricing-card">
        <div class="pricing-header gradient-bg gradient-bg--blue">
          <h3>Starter</h3>
          <div class="price">
            <span class="amount">29€</span>
            <span class="period">/mois</span>
          </div>
        </div>
        <div class="pricing-body">
          <ul class="features">
            <li>✓ 5 projets</li>
            <li>✓ 10 Go stockage</li>
            <li>✓ Support email</li>
            <li>✓ Analytics de base</li>
          </ul>
          <button class="btn btn-primary">Choisir</button>
        </div>
      </div>

      <div class="pricing-card pricing-card--featured">
        <div class="badge">Populaire</div>
        <div class="pricing-header gradient-bg gradient-bg--purple">
          <h3>Pro</h3>
          <div class="price">
            <span class="amount">79€</span>
            <span class="period">/mois</span>
          </div>
        </div>
        <div class="pricing-body">
          <ul class="features">
            <li>✓ Projets illimités</li>
            <li>✓ 100 Go stockage</li>
            <li>✓ Support prioritaire</li>
            <li>✓ Analytics avancés</li>
          </ul>
          <button class="btn btn-primary">Choisir</button>
        </div>
      </div>

      <div class="pricing-card">
        <div class="pricing-header gradient-bg gradient-bg--orange">
          <h3>Enterprise</h3>
          <div class="price">
            <span class="amount">Custom</span>
          </div>
        </div>
        <div class="pricing-body">
          <ul class="features">
            <li>✓ Tout illimité</li>
            <li>✓ Storage illimité</li>
            <li>✓ Support dédié 24/7</li>
            <li>✓ SLA personnalisé</li>
          </ul>
          <button class="btn btn-primary">Contact</button>
        </div>
      </div>
    </div>
  </div>
</section>

<style>
  .pricing {
    padding: 6rem 2rem;
  }

  .pricing-title {
    text-align: center;
    font-size: 3rem;
    margin-bottom: 4rem;
  }

  .pricing-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2rem;
    max-width: 1200px;
    margin: 0 auto;
  }

  .pricing-card {
    background: white;
    border-radius: 1rem;
    overflow: hidden;
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
    transition: transform 0.3s ease;
    position: relative;
  }

  .pricing-card:hover {
    transform: translateY(-8px);
  }

  .pricing-card--featured {
    transform: scale(1.05);
  }

  .badge {
    position: absolute;
    top: 1rem;
    right: 1rem;
    background: white;
    color: #667eea;
    padding: 0.25rem 1rem;
    border-radius: 9999px;
    font-weight: 600;
    font-size: 0.875rem;
    z-index: 1;
  }

  .pricing-header {
    padding: 3rem 2rem 2rem;
    color: white;
    text-align: center;
  }

  .pricing-header h3 {
    margin: 0 0 1rem 0;
    font-size: 1.5rem;
  }

  .amount {
    font-size: 3rem;
    font-weight: 700;
  }

  .period {
    opacity: 0.8;
  }

  .pricing-body {
    padding: 2rem;
  }

  .features {
    list-style: none;
    padding: 0;
    margin: 0 0 2rem 0;
  }

  .features li {
    padding: 0.5rem 0;
  }

  .btn {
    width: 100%;
    padding: 1rem;
    border: none;
    border-radius: 0.5rem;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.3s;
  }

  .btn-primary {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
  }

  .btn:hover {
    transform: scale(1.02);
  }
</style>
```

### Exemple 5 : Footer avec dégradé

```html
<footer class="footer gradient-bg gradient-bg--dark">
  <div class="container-fluid container-fluid--xl">
    <div class="footer-grid">
      <div class="footer-col">
        <h4>À propos</h4>
        <ul>
          <li><a href="#">Notre histoire</a></li>
          <li><a href="#">Équipe</a></li>
          <li><a href="#">Carrières</a></li>
          <li><a href="#">Presse</a></li>
        </ul>
      </div>

      <div class="footer-col">
        <h4>Produits</h4>
        <ul>
          <li><a href="#">Fonctionnalités</a></li>
          <li><a href="#">Tarifs</a></li>
          <li><a href="#">Intégrations</a></li>
          <li><a href="#">API</a></li>
        </ul>
      </div>

      <div class="footer-col">
        <h4>Ressources</h4>
        <ul>
          <li><a href="#">Documentation</a></li>
          <li><a href="#">Guides</a></li>
          <li><a href="#">Blog</a></li>
          <li><a href="#">Support</a></li>
        </ul>
      </div>

      <div class="footer-col">
        <h4>Legal</h4>
        <ul>
          <li><a href="#">Confidentialité</a></li>
          <li><a href="#">Conditions</a></li>
          <li><a href="#">Cookies</a></li>
          <li><a href="#">Licences</a></li>
        </ul>
      </div>
    </div>

    <div class="footer-bottom">
      <p>&copy; 2024 Votre Entreprise. Tous droits réservés.</p>
      <div class="social-links">
        <a href="#">Twitter</a>
        <a href="#">LinkedIn</a>
        <a href="#">GitHub</a>
      </div>
    </div>
  </div>
</footer>

<style>
  .footer {
    padding: 4rem 2rem 2rem;
    color: white;
  }

  .footer-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 3rem;
    margin-bottom: 3rem;
  }

  .footer-col h4 {
    margin: 0 0 1rem 0;
    font-size: 1.125rem;
  }

  .footer-col ul {
    list-style: none;
    padding: 0;
    margin: 0;
  }

  .footer-col li {
    margin-bottom: 0.75rem;
  }

  .footer-col a {
    color: rgba(255, 255, 255, 0.7);
    text-decoration: none;
    transition: color 0.3s;
  }

  .footer-col a:hover {
    color: white;
  }

  .footer-bottom {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding-top: 2rem;
    border-top: 1px solid rgba(255, 255, 255, 0.1);
  }

  .footer-bottom p {
    margin: 0;
    opacity: 0.7;
  }

  .social-links {
    display: flex;
    gap: 1.5rem;
  }

  .social-links a {
    color: rgba(255, 255, 255, 0.7);
    text-decoration: none;
    transition: color 0.3s;
  }

  .social-links a:hover {
    color: white;
  }
</style>
```

### Exemple 6 : Buttons avec dégradés

```html
<div class="gradient-buttons">
  <button class="btn gradient-bg gradient-bg--blue">Blue Button</button>

  <button class="btn gradient-bg gradient-bg--purple">Purple Button</button>

  <button class="btn gradient-bg gradient-bg--pink">Pink Button</button>

  <button class="btn gradient-bg gradient-bg--green">Green Button</button>

  <button class="btn gradient-bg gradient-bg--orange">Orange Button</button>
</div>

<style>
  .gradient-buttons {
    display: flex;
    flex-wrap: wrap;
    gap: 1rem;
    padding: 2rem;
  }

  .btn {
    padding: 1rem 2rem;
    border: none;
    border-radius: 0.5rem;
    color: white;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.3s ease;
    box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
  }

  .btn:hover {
    transform: translateY(-2px);
    box-shadow: 0 6px 20px rgba(0, 0, 0, 0.3);
  }

  .btn:active {
    transform: translateY(0);
  }
</style>
```

### Exemple 7 : Banner avec dégradé mesh

```html
<div
  class="banner gradient-bg gradient-bg--mesh"
  style="--gradient-color-1: #667eea; --gradient-color-2: #764ba2"
>
  <div class="container-fluid container-fluid--lg">
    <h2>Nouveauté : Fonctionnalité Premium</h2>
    <p>Découvrez notre dernière innovation dès maintenant</p>
    <button class="btn glass-effect glass-effect--light">
      En savoir plus →
    </button>
  </div>
</div>

<style>
  .banner {
    padding: 4rem 2rem;
    text-align: center;
    color: white;
  }

  .banner h2 {
    font-size: 2.5rem;
    margin: 0 0 1rem 0;
  }

  .banner p {
    font-size: 1.25rem;
    opacity: 0.9;
    margin: 0 0 2rem 0;
  }

  .btn {
    padding: 1rem 2rem;
    border: none;
    border-radius: 0.5rem;
    font-weight: 600;
    cursor: pointer;
  }
</style>
```

## 🎨 Personnalisation avancée

### Dégradé avec 3 couleurs

```html
<div
  class="gradient-bg gradient-bg--triple"
  style="--gradient-color-1: #ff6b6b;
            --gradient-color-2: #4ecdc4;
            --gradient-color-3: #45b7d1;
            min-height: 300px"
>
  <h2 style="color: white; padding: 2rem">Triple Gradient</h2>
</div>
```

### Dégradé avec stops personnalisés

```html
<div
  style="background: linear-gradient(135deg, 
                         #667eea 0%, 
                         #764ba2 50%, 
                         #f093fb 100%);
            min-height: 300px;
            padding: 2rem"
>
  <h2 style="color: white">Custom Stops</h2>
</div>
```

### Dégradé radial personnalisé

```html
<div
  style="background: radial-gradient(
              ellipse at top left,
              #667eea,
              #764ba2 50%,
              #f093fb
            );
            min-height: 300px;
            padding: 2rem"
>
  <h2 style="color: white">Radial Ellipse</h2>
</div>
```

### Dégradé conique (color wheel)

```html
<div
  class="gradient-bg gradient-bg--conic"
  style="--gradient-color-1: #667eea;
            --gradient-color-2: #764ba2;
            min-height: 300px;
            border-radius: 50%;
            width: 300px;
            height: 300px"
></div>
```

### Overlay de dégradé sur image

```html
<div class="image-with-gradient">
  <img src="background.jpg" alt="Background" />
  <div class="gradient-overlay"></div>
  <div class="content">
    <h2>Titre sur image</h2>
    <p>Avec overlay dégradé</p>
  </div>
</div>

<style>
  .image-with-gradient {
    position: relative;
    height: 500px;
    overflow: hidden;
  }

  .image-with-gradient img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }

  .gradient-overlay {
    position: absolute;
    inset: 0;
    background: linear-gradient(
      to top,
      rgba(0, 0, 0, 0.8) 0%,
      rgba(0, 0, 0, 0.4) 50%,
      transparent 100%
    );
  }

  .content {
    position: absolute;
    bottom: 2rem;
    left: 2rem;
    color: white;
    z-index: 1;
  }

  .content h2 {
    margin: 0 0 0.5rem 0;
    font-size: 2.5rem;
  }

  .content p {
    margin: 0;
    font-size: 1.25rem;
    opacity: 0.9;
  }
</style>
```

### Dégradé avec pattern

```html
<div
  class="gradient-bg gradient-bg--sunset gradient-bg--with-pattern"
  style="min-height: 400px; padding: 2rem"
>
  <h2 style="color: white">Gradient with Pattern</h2>
</div>
```

### Dégradé avec noise texture

```html
<div
  class="gradient-bg gradient-bg--ocean gradient-bg--noise"
  style="min-height: 400px; padding: 2rem"
>
  <h2 style="color: white">Gradient with Noise</h2>
</div>
```

## 🎯 Cas d'usage courants

### 1. Hero sections

```html
<section class="gradient-bg gradient-bg--sunset" style="min-height: 100vh">
  Hero content
</section>
```

### 2. Cards / Containers

```html
<div class="card gradient-bg gradient-bg--blue">Card content</div>
```

### 3. Buttons

```html
<button class="gradient-bg gradient-bg--purple">Click me</button>
```

### 4. Headers / Navbars

```html
<header class="gradient-bg gradient-bg--dark">Navigation</header>
```

### 5. Footers

```html
<footer class="gradient-bg gradient-bg--dark">Footer content</footer>
```

### 6. Backgrounds de section

```html
<section class="gradient-bg gradient-bg--light">Section content</section>
```

### 7. Overlays

```html
<div
  class="gradient-overlay"
  style="background: linear-gradient(to bottom, transparent, rgba(0,0,0,0.8))"
></div>
```

## 🔧 Combinaison avec autres utilitaires

### Avec Glass Effect

```html
<div
  class="gradient-bg gradient-bg--sunset"
  style="min-height: 100vh; padding: 4rem"
>
  <div
    class="glass-effect glass-effect--light"
    style="padding: 3rem; border-radius: 1rem"
  >
    <h2>Glass sur Gradient</h2>
    <p>Effet combiné élégant</p>
  </div>
</div>
```

### Avec Shadow Wrapper

```html
<div
  class="card gradient-bg gradient-bg--purple shadow-wrapper shadow-wrapper--xl"
>
  <h3 style="color: white">Card avec gradient + ombre</h3>
</div>
```

### Avec Text Balance

```html
<section class="gradient-bg gradient-bg--ocean" style="padding: 6rem 2rem">
  <h1 class="text-balance text-balance--center" style="color: white">
    Titre équilibré sur dégradé
  </h1>
</section>
```

## 📱 Comportement responsive

### Dégradé adaptatif

```scss
.gradient-bg {
  // Mobile : dégradé simple
  background: linear-gradient(180deg, #667eea 0%, #764ba2 100%);

  @media (min-width: 768px) {
    // Tablet : diagonal
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  }

  @media (min-width: 1024px) {
    // Desktop : avec animation
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    background-size: 200% 200%;
  }
}
```

### Désactiver animation sur mobile

```scss
.gradient-bg--animated {
  @media (max-width: 640px) {
    animation: none; // Performance
  }
}
```

## ⚡ Performance & Bonnes pratiques

### ✅ À faire

```html
<!-- Bon : Dégradé simple (2 couleurs) -->
<div class="gradient-bg gradient-bg--sunset">
  <!-- Bon : Utiliser des dégradés prédéfinis -->
  <div class="gradient-bg gradient-bg--ocean">
    <!-- Bon : Limiter les animations -->
    <div class="gradient-bg gradient-bg--animated">
      <!-- Bon : Fixed attachment pour parallax léger -->
      <div class="gradient-bg" style="background-attachment: fixed"></div>
    </div>
  </div>
</div>
```

### ❌ À éviter

```html
<!-- Mauvais : Trop de couleurs (complexe) -->
<div
  style="background: linear-gradient(135deg, #f00, #0f0, #00f, #ff0, #f0f, #0ff)"
>
  <!-- Mauvais : Animation trop rapide -->
  <div style="animation: gradient 1s ease infinite">
    <!-- Mauvais : Dégradés multiples imbriqués -->
    <div class="gradient-bg">
      <div class="gradient-bg">
        <div class="gradient-bg">...</div>
      </div>
    </div>

    <!-- Mauvais : Background-size trop grand -->
    <div style="background-size: 400% 400%"></div>
  </div>
</div>
```

### Conseils de performance

```scss
// ✅ Utiliser will-change pour animations
.gradient-bg--animated {
  will-change: background-position;
}

// ✅ Préférer transform pour mouvement
// Au lieu d'animer background-position
@keyframes betterAnimation {
  from {
    transform: translateX(0);
  }
  to {
    transform: translateX(-50%);
  }
}

// ❌ Éviter trop de stops
// Mauvais
background: linear-gradient(
  0deg,
  #f00 0%,
  #0f0 10%,
  #00f 20%,
  #ff0 30%,
  #f0f 40%,
  #0ff 50%,
  #f00 60%,
  #0f0 70%
);

// ✅ Bon
background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
```

## 🌐 Compatibilité navigateurs

| Navigateur | Version minimale | Support               |
| ---------- | ---------------- | --------------------- |
| Chrome     | 26+              | ✅ Complet            |
| Firefox    | 16+              | ✅ Complet            |
| Safari     | 6.1+             | ✅ Complet            |
| Edge       | 12+              | ✅ Complet            |
| Opera      | 12.1+            | ✅ Complet            |
| IE         | 10+              | ✅ Partiel (préfixes) |

**Note** : Les dégradés sont très bien supportés. Les anciens navigateurs peuvent nécessiter des préfixes.

### Préfixes pour IE

```scss
.gradient-bg {
  // Fallback couleur unie
  background: #667eea;

  // Dégradé moderne
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);

  // Pour IE10/11
  background: -ms-linear-gradient(135deg, #667eea 0%, #764ba2 100%);
}
```

## 🐛 Troubleshooting

### Problème : Le dégradé ne s'affiche pas

**Solution** : Vérifiez la syntaxe et les couleurs

```css
/* ❌ Mauvais */
background: gradient(#667eea, #764ba2);

/* ✅ Bon */
background: linear-gradient(135deg, #667eea, #764ba2);
```

### Problème : Le dégradé semble pixelisé

**Solution** : Utilisez plus de stops ou blur

```css
/* Dégradé plus smooth */
background: linear-gradient(
  135deg,
  #667eea 0%,
  #6e7ceb 25%,
  #7179ec 50%,
  #7476a6 75%,
  #764ba2 100%
);
```

### Problème : Animation saccadée

**Solution** : Utilisez will-change et réduisez complexity

```scss
.gradient-bg--animated {
  will-change: background-position;
  animation-timing-function: ease-in-out;
}
```

### Problème : Texte illisible sur dégradé

**Solution** : Ajoutez un overlay ou text-shadow

```scss
.gradient-bg {
  position: relative;

  &::before {
    content: "";
    position: absolute;
    inset: 0;
    background: rgba(0, 0, 0, 0.3); // Overlay sombre
  }

  > * {
    position: relative;
    z-index: 1;
  }
}

// Ou text-shadow
h1 {
  text-shadow: 0 2px 10px rgba(0, 0, 0, 0.5);
}
```

## 📦 Classes complètes disponibles

```scss
// Classes de base
.gradient-bg {
  /* Base avec dégradé */
}

// Directions
.gradient-bg--to-right {
  --gradient-angle: 90deg;
}
.gradient-bg--to-left {
  --gradient-angle: 270deg;
}
.gradient-bg--to-bottom {
  --gradient-angle: 180deg;
}
.gradient-bg--to-top {
  --gradient-angle: 0deg;
}
.gradient-bg--diagonal {
  --gradient-angle: 135deg;
}
.gradient-bg--diagonal-reverse {
  --gradient-angle: 45deg;
}

// Types
.gradient-bg--radial {
  /* Radial gradient */
}
.gradient-bg--conic {
  /* Conic gradient */
}
.gradient-bg--triple {
  /* 3 couleurs */
}
.gradient-bg--mesh {
  /* Mesh effect */
}

// Presets
.gradient-bg--sunset {
  /* Purple → Violet */
}
.gradient-bg--ocean {
  /* Navy → Cyan */
}
.gradient-bg--fire {
  /* Pink → Red */
}
.gradient-bg--forest {
  /* Dark green → Light green */
}
.gradient-bg--candy {
  /* Pink → Yellow */
}
.gradient-bg--purple {
  /* Blue-purple → Purple */
}
.gradient-bg--blue {
  /* Blue → Dark blue */
}
.gradient-bg--green {
  /* Green → Dark green */
}
.gradient-bg--orange {
  /* Orange → Dark orange */
}
.gradient-bg--pink {
  /* Pink → Dark pink */
}
.gradient-bg--dark {
  /* Dark gray → Black */
}
.gradient-bg--light {
  /* Light gray → White */
}

// Effets
.gradient-bg--animated {
  /* Animation */
}
.gradient-bg--with-pattern {
  /* Pattern overlay */
}
.gradient-bg--noise {
  /* Noise texture */
}
```

## 🎓 Ressources complémentaires

- [CSS Gradients - MDN](https://developer.mozilla.org/fr/docs/Web/CSS/CSS_Images/Using_CSS_gradients)
- [Linear Gradient - MDN](https://developer.mozilla.org/fr/docs/Web/CSS/gradient/linear-gradient)
- [Radial Gradient - MDN](https://developer.mozilla.org/fr/docs/Web/CSS/gradient/radial-gradient)
- [CSS Gradient Generator](https://cssgradient.io/)
- [UI Gradients](https://uigradients.com/)
- [WebGradients](https://webgradients.com/)

## 📝 Changelog

- **v1.0** - Version initiale avec dégradés linéaires
- **v1.1** - Ajout des dégradés radiaux et coniques
- **v1.2** - Ajout de 10+ presets populaires
- **v1.3** - Support des dégradés animés
- **v1.4** - Ajout des effets mesh et noise
- **v1.5** - Optimisations performance et responsive

---

**Made with ❤️ for beautiful gradients**
