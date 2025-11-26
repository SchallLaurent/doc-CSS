# CSS Utilities Documentation

> Documentation complète de classes CSS utilitaires réutilisables pour vos projets web

## 📋 À propos

Ce repository contient une collection de classes CSS utilitaires modernes et flexibles, conçues pour accélérer le développement front-end. Chaque utilitaire est documenté en détail avec des exemples d'utilisation, des cas d'usage et des bonnes pratiques.

## 🎯 Objectifs

- **Réutilisabilité** : Classes CSS universelles utilisables dans n'importe quel projet
- **Flexibilité** : Variables CSS personnalisables sans modification du code source
- **Performance** : Code léger et optimisé
- **Simplicité** : API intuitive et facile à mémoriser
- **Documentation** : Chaque utilitaire est accompagné d'une documentation complète

## 🚀 Installation

### Option 1 : Copier-coller
Copiez simplement le code SCSS des utilitaires dont vous avez besoin dans votre projet.

### Option 2 : Import depuis votre SCSS
```scss
// Dans votre styles.scss ou fichier principal
@import 'utilities/aspect-ratio';
@import 'utilities/fluid-space';
// etc.
```

### Option 3 : Clone du repository
```bash
git clone https://github.com/votre-username/css-utilities-doc.git
cd css-utilities-doc
```

## 📦 Utilitaires disponibles

### 🎨 Layout & Positionnement

- **[Aspect Ratio](./docs/aspect-ratio.md)** - Ratios d'images et conteneurs flexibles
- **[Sticky Wrapper](./docs/sticky-wrapper.md)** - Headers/footers collants avec offset personnalisable
- **[Center Absolute](./docs/center-absolute.md)** - Centrage absolu avec offsets
- **[Split Screen](./docs/split.md)** - Écrans divisés avec ratios personnalisables
- **[Media Object](./docs/media.md)** - Pattern média + contenu classique

### 📐 Spacing & Sizing

- **[Gap Wrapper](./docs/gap-wrapper.md)** - Espacement intelligent flex/grid
- **[Fluid Space](./docs/fluid-space.md)** - Spacing responsive sans media queries
- **[Container Fluid](./docs/container-fluid.md)** - Conteneurs avec padding intelligent

### ✍️ Typography

- **[Fluid Text](./docs/fluid-text.md)** - Typographie responsive fluide
- **[Line Clamp](./docs/line-clamp.md)** - Truncate texte multi-lignes
- **[Text Balance](./docs/text-balance.md)** - Titres équilibrés automatiquement

### 🎭 Visual Effects

- **[Shadow Wrapper](./docs/shadow-wrapper.md)** - Système d'ombres cohérent
- **[Glass Effect](./docs/glass-effect.md)** - Effet glassmorphism moderne
- **[Gradient Background](./docs/gradient-bg.md)** - Dégradés personnalisables
- **[Rounded](./docs/rounded.md)** - Système de border-radius flexible

### 🎬 Animations & Transitions

- **[Transition](./docs/transition.md)** - Transitions CSS configurables
- **[Hover Lift](./docs/hover-lift.md)** - Effets de survol élégants
- **[Skeleton](./docs/skeleton.md)** - Loading skeletons animés

### 📱 Responsive Utilities

- **[Hide Mobile](./docs/hide-mobile.md)** - Show/hide responsive
- **[Stack](./docs/stack.md)** - Layout flex responsive automatique

### 🃏 Components

- **[Card](./docs/card.md)** - Cards stylisées personnalisables
- **[Scroll Snap](./docs/scroll-snap.md)** - Scroll avec snap points
- **[Masonry](./docs/masonry.md)** - Layout en colonnes type Pinterest
- **[Grid Wrapper](./docs/grid-wrapper.md)** - Grid automatique

### 🎯 Accessibility

- **[Focus Ring](./docs/focus-ring.md)** - Focus visible accessible

## 📖 Structure du projet

```
css-utilities-doc/
├── README.md                 # Ce fichier
├── docs/                     # Documentation des utilitaires
│   ├── aspect-ratio.md
│   ├── sticky-wrapper.md
│   ├── center-absolute.md
│   ├── gap-wrapper.md
│   ├── fluid-space.md
│   ├── container-fluid.md
│   ├── fluid-text.md
│   ├── line-clamp.md
│   ├── text-balance.md
│   ├── shadow-wrapper.md
│   ├── glass-effect.md
│   ├── gradient-bg.md
│   ├── rounded.md
│   ├── transition.md
│   ├── hover-lift.md
│   ├── skeleton.md
│   ├── hide-mobile.md
│   ├── stack.md
│   ├── card.md
│   ├── media.md
│   ├── split.md
│   ├── scroll-snap.md
│   ├── masonry.md
│   └── focus-ring.md
```

## 💡 Exemples rapides

### Aspect Ratio pour images
```html
<div class="aspect-ratio" style="--ratio: 16/9">
  <img src="image.jpg" alt="Image 16:9">
</div>
```

### Texte fluide responsive
```html
<h1 class="fluid-text" style="--min-size: 1.5rem; --max-size: 3rem">
  Titre responsive
</h1>
```

### Card avec effet glassmorphism
```html
<div class="card glass-effect" style="--blur: 15px; --opacity: 0.9">
  <h2>Contenu</h2>
</div>
```

### Grid masonry
```html
<div class="masonry" style="--cols: 3; --gap: 1rem">
  <div>Item 1</div>
  <div>Item 2</div>
  <div>Item 3</div>
</div>
```

## 🛠️ Technologies

- **SCSS** - Préprocesseur CSS
- **CSS Custom Properties** - Variables CSS natives
- **CSS Grid** - Layout moderne
- **Flexbox** - Layout flexible
- **Modern CSS** - clamp(), min(), max(), aspect-ratio

## 🎨 Principes de design

Ces utilitaires suivent les principes suivants :
- **Utility-first** : Classes réutilisables et composables
- **CSS Variables** : Personnalisation sans recompilation
- **Mobile-first** : Responsive par défaut
- **Performance** : Code minimal et optimisé
- **Accessibilité** : Conformité aux standards WCAG
- **Modern CSS** : Utilisation des dernières spécifications CSS

## 🌐 Compatibilité

| Navigateur | Version minimale |
|-----------|------------------|
| Chrome    | 88+             |
| Firefox   | 89+             |
| Safari    | 14+             |
| Edge      | 88+             |

*Note : Certains utilitaires nécessitent des fonctionnalités CSS récentes*

## 🤝 Contribuer

Les contributions sont les bienvenues ! Voici comment contribuer :

1. **Fork** le projet
2. **Créez** votre branche (`git checkout -b feature/nouvelle-utility`)
3. **Committez** vos changements (`git commit -m 'Add: nouvelle utility pour X'`)
4. **Pushez** vers la branche (`git push origin feature/nouvelle-utility`)
5. **Ouvrez** une Pull Request

### Guidelines de contribution

- Suivez la structure de documentation existante
- Incluez des exemples d'utilisation
- Testez la compatibilité sur les navigateurs modernes
- Documentez tous les paramètres et variables
- Ajoutez des cas d'usage pratiques

## 🔧 Utilisation dans différents frameworks

### Angular
```scss
// styles.scss
@import 'utilities/aspect-ratio';
@import 'utilities/fluid-text';
```
```html
<!-- component.html -->
<div class="aspect-ratio" [style.--ratio]="'16/9'">
  <img [src]="imageUrl" alt="Image">
</div>
```

### React
```jsx
// App.jsx
import './utilities.scss';

function App() {
  return (
    <div className="aspect-ratio" style={{'--ratio': '16/9'}}>
      <img src={imageUrl} alt="Image" />
    </div>
  );
}
```

### Vue
```vue
<!-- Component.vue -->
<template>
  <div class="aspect-ratio" :style="{ '--ratio': '16/9' }">
    <img :src="imageUrl" alt="Image">
  </div>
</template>

<style lang="scss">
@import '@/utilities/aspect-ratio';
</style>
```

## 🏆 Top 5 des utilitaires les plus utilisés

1. **Aspect Ratio** - Pour toutes vos images et vidéos
2. **Fluid Space** - Spacing responsive moderne
3. **Line Clamp** - Besoin très fréquent
4. **Card** - Component de base
5. **Stack** - Layout responsive facile

## 📊 Roadmap

- [x] Layout & Positionnement (5 utilitaires)
- [x] Spacing & Sizing (3 utilitaires)
- [x] Typography (3 utilitaires)
- [x] Visual Effects (4 utilitaires)
- [x] Animations & Transitions (3 utilitaires)
- [x] Responsive Utilities (2 utilitaires)
- [x] Components (5 utilitaires)
- [x] Accessibility (1 utilitaire)
- [ ] Form utilities
- [ ] Color system
- [ ] Advanced animations

## 📄 Licence

MIT License - Libre d'utilisation dans vos projets personnels et commerciaux.

## 👤 Auteur

**Votre Nom**
- GitHub: [@votre-username](https://github.com/votre-username)
- LinkedIn: [Votre Profil](https://linkedin.com/in/votre-profil)

## ⭐ Support

Si ce projet vous aide, n'hésitez pas à lui donner une ⭐ !

## 📞 Contact

Des questions ? Des suggestions ? Ouvrez une [issue](https://github.com/votre-username/css-utilities-doc/issues) !

---

**Made with ❤️ for the web development community**
