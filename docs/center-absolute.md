# Center Absolute

> Utilitaire CSS pour centrer parfaitement les éléments avec position absolute

## 📝 Description

Le `center-absolute` permet de centrer facilement un élément en position absolute, avec possibilité d'ajouter des offsets personnalisés. Idéal pour les modals, overlays, loaders et éléments positionnés.

## 🎯 Cas d'usage

- Modals et popups centrées
- Loaders et spinners
- Overlays et tooltips
- Images en position absolute
- Badges et notifications
- Hero content centré

## 💾 Installation

```scss
// _center-absolute.scss
.center-absolute {
  --offset-x: 0;
  --offset-y: 0;

  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(
    calc(-50% + var(--offset-x)),
    calc(-50% + var(--offset-y))
  );
}

// Modificateurs
.center-absolute--fixed {
  position: fixed;
}

.center-absolute--x {
  left: 50%;
  transform: translateX(calc(-50% + var(--offset-x)));
}

.center-absolute--y {
  top: 50%;
  transform: translateY(calc(-50% + var(--offset-y)));
}
```

## 🚀 Utilisation de base

### Centrage parfait

```html
<div class="container" style="position: relative">
  <div class="center-absolute">
    <p>Je suis parfaitement centré !</p>
  </div>
</div>
```

### Avec offset

```html
<div class="container" style="position: relative">
  <!-- Décalé de 20px vers la droite et 10px vers le bas -->
  <div class="center-absolute" style="--offset-x: 20px; --offset-y: 10px">
    <p>Centré avec décalage</p>
  </div>
</div>
```

### Position fixed (modal)

```html
<div class="center-absolute center-absolute--fixed">
  <div class="modal">
    <h2>Modal Title</h2>
    <p>Modal content...</p>
  </div>
</div>
```

### Centrage horizontal seulement

```html
<div class="banner" style="position: relative">
  <img class="center-absolute--x" src="logo.svg" alt="Logo" />
</div>

<style>
  .banner {
    height: 200px;
    background: linear-gradient(135deg, #667eea, #764ba2);
  }
</style>
```

## ⚙️ Paramètres

| Variable CSS | Type     | Défaut | Description                          |
| ------------ | -------- | ------ | ------------------------------------ |
| `--offset-x` | `length` | `0`    | Décalage horizontal depuis le centre |
| `--offset-y` | `length` | `0`    | Décalage vertical depuis le centre   |

### Classes modificatrices

| Classe                    | Description                                     |
| ------------------------- | ----------------------------------------------- |
| `.center-absolute--fixed` | Utilise `position: fixed` au lieu de `absolute` |
| `.center-absolute--x`     | Centre seulement horizontalement                |
| `.center-absolute--y`     | Centre seulement verticalement                  |

## 📚 Exemples avancés

### Modal centered

```html
<div class="modal-backdrop">
  <div class="center-absolute center-absolute--fixed modal">
    <button class="modal-close">&times;</button>
    <h2>Confirmation</h2>
    <p>Êtes-vous sûr de vouloir continuer ?</p>
    <div class="modal-actions">
      <button class="btn btn-secondary">Annuler</button>
      <button class="btn btn-primary">Confirmer</button>
    </div>
  </div>
</div>

<style>
  .modal-backdrop {
    position: fixed;
    inset: 0;
    background: rgba(0, 0, 0, 0.5);
    z-index: 1000;
  }

  .modal {
    background: white;
    border-radius: 0.5rem;
    padding: 2rem;
    max-width: 500px;
    width: 90%;
    box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
    z-index: 1001;
  }

  .modal-close {
    position: absolute;
    top: 1rem;
    right: 1rem;
    background: none;
    border: none;
    font-size: 1.5rem;
    cursor: pointer;
    color: #666;
  }

  .modal-actions {
    display: flex;
    gap: 1rem;
    justify-content: flex-end;
    margin-top: 1.5rem;
  }
</style>
```

### Loading spinner

```html
<div class="loading-container" style="position: relative; min-height: 400px">
  <div class="center-absolute">
    <div class="spinner"></div>
    <p>Chargement en cours...</p>
  </div>
</div>

<style>
  .spinner {
    width: 40px;
    height: 40px;
    border: 4px solid #f3f3f3;
    border-top: 4px solid #3b82f6;
    border-radius: 50%;
    animation: spin 1s linear infinite;
    margin: 0 auto 1rem;
  }

  @keyframes spin {
    0% {
      transform: rotate(0deg);
    }
    100% {
      transform: rotate(360deg);
    }
  }
</style>
```

### Image overlay avec texte centré

```html
<div class="hero-image" style="position: relative">
  <img src="hero.jpg" alt="Hero" />
  <div class="center-absolute hero-content">
    <h1>Bienvenue</h1>
    <p>Découvrez nos services</p>
    <button class="btn">En savoir plus</button>
  </div>
</div>

<style>
  .hero-image {
    position: relative;
    width: 100%;
    height: 500px;
    overflow: hidden;
  }

  .hero-image img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    filter: brightness(0.7);
  }

  .hero-content {
    text-align: center;
    color: white;
    z-index: 2;
  }

  .hero-content h1 {
    font-size: 3rem;
    margin-bottom: 1rem;
    text-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
  }
</style>
```

### Badge positionné

```html
<div class="product-card" style="position: relative">
  <img src="product.jpg" alt="Product" />

  <!-- Badge "Nouveau" -->
  <span
    class="center-absolute badge"
    style="--offset-x: 100px; --offset-y: -80px"
  >
    Nouveau
  </span>

  <h3>Nom du produit</h3>
  <p class="price">29,99 €</p>
</div>

<style>
  .product-card {
    position: relative;
    border: 1px solid #e5e7eb;
    border-radius: 0.5rem;
    padding: 1rem;
  }

  .badge {
    background: #ef4444;
    color: white;
    padding: 0.25rem 0.75rem;
    border-radius: 9999px;
    font-size: 0.875rem;
    font-weight: 600;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }
</style>
```

### Tooltip positionné

```html
<button class="btn-with-tooltip" style="position: relative">
  Hover me
  <span class="center-absolute tooltip" style="--offset-y: -40px">
    Ceci est un tooltip
  </span>
</button>

<style>
  .tooltip {
    background: #1f2937;
    color: white;
    padding: 0.5rem 1rem;
    border-radius: 0.25rem;
    font-size: 0.875rem;
    white-space: nowrap;
    opacity: 0;
    pointer-events: none;
    transition: opacity 0.2s;
  }

  .tooltip::after {
    content: "";
    position: absolute;
    top: 100%;
    left: 50%;
    transform: translateX(-50%);
    border: 6px solid transparent;
    border-top-color: #1f2937;
  }

  .btn-with-tooltip:hover .tooltip {
    opacity: 1;
  }
</style>
```

### Carousel navigation centrée verticalement

```html
<div class="carousel" style="position: relative">
  <img src="slide1.jpg" alt="Slide 1" />

  <button
    class="center-absolute--y carousel-btn carousel-btn--prev"
    style="--offset-x: 20px"
  >
    ←
  </button>

  <button
    class="center-absolute--y carousel-btn carousel-btn--next"
    style="--offset-x: -20px"
  >
    →
  </button>
</div>

<style>
  .carousel {
    position: relative;
    max-width: 800px;
    margin: 0 auto;
  }

  .carousel-btn {
    background: rgba(255, 255, 255, 0.9);
    border: none;
    width: 50px;
    height: 50px;
    border-radius: 50%;
    font-size: 1.5rem;
    cursor: pointer;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.15);
    transition: all 0.2s;
  }

  .carousel-btn:hover {
    background: white;
    transform: scale(1.1);
  }

  .carousel-btn--prev {
    left: var(--offset-x, 20px);
  }

  .carousel-btn--next {
    right: var(--offset-x, 20px);
    left: auto;
  }
</style>
```

## 🎨 Personnalisation

### Animation d'entrée

```scss
.center-absolute {
  --offset-x: 0;
  --offset-y: 0;

  animation: fadeInCenter 0.3s ease-out;
}

@keyframes fadeInCenter {
  from {
    opacity: 0;
    transform: translate(
      calc(-50% + var(--offset-x)),
      calc(-50% + var(--offset-y) - 20px)
    );
  }
  to {
    opacity: 1;
    transform: translate(
      calc(-50% + var(--offset-x)),
      calc(-50% + var(--offset-y))
    );
  }
}
```

### Avec backdrop-filter

```scss
.center-absolute--glass {
  background: rgba(255, 255, 255, 0.8);
  backdrop-filter: blur(10px);
  padding: 2rem;
  border-radius: 1rem;
  border: 1px solid rgba(255, 255, 255, 0.3);
}
```

### Responsive offsets

```scss
.center-absolute {
  --offset-x: 0;
  --offset-y: 0;

  @media (max-width: 768px) {
    --offset-x: 0;
    --offset-y: 0;
  }
}
```

## 🔧 Compatibilité

| Navigateur | Version minimale | Notes                        |
| ---------- | ---------------- | ---------------------------- |
| Chrome     | 1+               | Support complet              |
| Firefox    | 1+               | Support complet              |
| Safari     | 1+               | Support complet              |
| Edge       | 12+              | Support complet              |
| IE         | 9+               | Support avec vendor prefixes |

## ⚠️ Notes importantes

- **Parent relatif** : Le parent doit avoir `position: relative` (ou absolute/fixed)
- **Transform conflicts** : Attention aux autres transforms qui pourraient interférer
- **Z-index** : Pensez à gérer le z-index pour les overlays
- **Accessibilité** : Les modals doivent être focusables et avoir un focus trap

## 🎓 Bonnes pratiques

✅ **À faire**

- Toujours définir position sur le parent
- Utiliser fixed pour les modals fullscreen
- Combiner avec des animations pour l'UX
- Gérer le focus pour l'accessibilité des modals
- Tester sur différentes tailles de contenu

❌ **À éviter**

- Ne pas oublier le parent positionné
- Ne pas abuser des offsets complexes
- Ne pas négliger le responsive
- Ne pas empiler trop de transforms

## 💡 Astuces JavaScript

### Ouvrir/fermer une modal

```javascript
const modal = document.querySelector(".modal");
const openBtn = document.querySelector(".open-modal");
const closeBtn = document.querySelector(".modal-close");
const backdrop = document.querySelector(".modal-backdrop");

function openModal() {
  backdrop.style.display = "block";
  document.body.style.overflow = "hidden";
  modal.focus();
}

function closeModal() {
  backdrop.style.display = "none";
  document.body.style.overflow = "";
}

openBtn.addEventListener("click", openModal);
closeBtn.addEventListener("click", closeModal);
backdrop.addEventListener("click", (e) => {
  if (e.target === backdrop) closeModal();
});

// Fermer avec Escape
document.addEventListener("keydown", (e) => {
  if (e.key === "Escape" && backdrop.style.display === "block") {
    closeModal();
  }
});
```

---

[← Retour à la documentation](../README.md)
