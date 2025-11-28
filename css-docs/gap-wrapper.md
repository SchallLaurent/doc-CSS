# Gap Wrapper Utility

> Gérez les espacements entre éléments avec flexibilité et cohérence via des variables CSS

## 📋 Description

**Gap Wrapper** est un utilitaire CSS qui simplifie la gestion des espacements entre éléments enfants. Fini les margins calculées manuellement ou les sélecteurs complexes - définissez simplement un gap et laissez CSS faire le reste. Parfait pour des listes, des groupes de boutons, des cartes, ou tout contenu nécessitant un espacement uniforme.

### ✨ Caractéristiques principales

- 📐 **Gap uniforme** : Espacement automatique entre tous les éléments enfants
- 🎯 **Gap directionnel** : Contrôle séparé pour horizontal (gap-x) et vertical (gap-y)
- 🔧 **Variables CSS** : Personnalisation simple sans modifier le code
- 📱 **Responsive** : Gaps adaptatifs selon la taille d'écran
- ⚡ **Performance** : Utilise les propriétés CSS natives (gap)
- 🔄 **Flexible** : Compatible avec flex et grid
- 🎨 **Échelle cohérente** : Système d'espacement prédéfini

## 🚀 Installation

### Code SCSS

```scss
// _gap-wrapper.scss

// Échelle d'espacement (Design tokens)
$spacing-scale: (
  "none": 0,
  "xs": 0.25rem,
  // 4px
  "sm": 0.5rem,
  // 8px
  "md": 1rem,
  // 16px
  "lg": 1.5rem,
  // 24px
  "xl": 2rem,
  // 32px
  "2xl": 3rem,
  // 48px
  "3xl": 4rem,
  // 64px
  "4xl": 6rem,
  // 96px
);

.gap-wrapper {
  // Variables par défaut
  --gap: 1rem; // Gap uniforme
  --gap-x: var(--gap); // Gap horizontal
  --gap-y: var(--gap); // Gap vertical
  --direction: row; // Direction du layout (row | column)
  --wrap: wrap; // Comportement wrap (wrap | nowrap)
  --align: stretch; // Alignement des items

  display: flex;
  flex-direction: var(--direction);
  flex-wrap: var(--wrap);
  gap: var(--gap-y) var(--gap-x);
  align-items: var(--align);
}

// Version Grid (pour layouts plus complexes)
.gap-wrapper--grid {
  display: grid;
  gap: var(--gap-y) var(--gap-x);
}

// Variantes de taille prédéfinies
.gap-wrapper--xs {
  --gap: 0.25rem;
}

.gap-wrapper--sm {
  --gap: 0.5rem;
}

.gap-wrapper--md {
  --gap: 1rem; // Défaut
}

.gap-wrapper--lg {
  --gap: 1.5rem;
}

.gap-wrapper--xl {
  --gap: 2rem;
}

.gap-wrapper--2xl {
  --gap: 3rem;
}

.gap-wrapper--3xl {
  --gap: 4rem;
}

// Variantes de direction
.gap-wrapper--column {
  --direction: column;
}

.gap-wrapper--row {
  --direction: row;
}

// Variantes d'alignement
.gap-wrapper--start {
  --align: flex-start;
}

.gap-wrapper--center {
  --align: center;
}

.gap-wrapper--end {
  --align: flex-end;
}

.gap-wrapper--baseline {
  --align: baseline;
}

// Désactiver le wrap
.gap-wrapper--nowrap {
  --wrap: nowrap;
}

// Gap responsive (utilise clamp)
.gap-wrapper--fluid {
  --gap: clamp(0.5rem, 2vw, 2rem);
}

// Variantes de justification
.gap-wrapper--justify-start {
  justify-content: flex-start;
}

.gap-wrapper--justify-center {
  justify-content: center;
}

.gap-wrapper--justify-end {
  justify-content: flex-end;
}

.gap-wrapper--justify-between {
  justify-content: space-between;
}

.gap-wrapper--justify-around {
  justify-content: space-around;
}

.gap-wrapper--justify-evenly {
  justify-content: space-evenly;
}
```

### Import dans votre projet

```scss
// Dans styles.scss
@import "utilities/gap-wrapper";
```

## 💡 Utilisation de base

### Exemple 1 : Gap simple (défaut)

```html
<div class="gap-wrapper">
  <button>Button 1</button>
  <button>Button 2</button>
  <button>Button 3</button>
  <button>Button 4</button>
</div>
```

### Exemple 2 : Gap personnalisé

```html
<!-- Gap de 2rem -->
<div class="gap-wrapper" style="--gap: 2rem">
  <div class="card">Card 1</div>
  <div class="card">Card 2</div>
  <div class="card">Card 3</div>
</div>
```

### Exemple 3 : Gap différent en X et Y

```html
<!-- Gap horizontal 1rem, vertical 2rem -->
<div class="gap-wrapper" style="--gap-x: 1rem; --gap-y: 2rem">
  <div>Item 1</div>
  <div>Item 2</div>
  <div>Item 3</div>
  <div>Item 4</div>
</div>
```

### Exemple 4 : Layout vertical

```html
<div class="gap-wrapper gap-wrapper--column gap-wrapper--lg">
  <h2>Titre</h2>
  <p>Paragraphe 1</p>
  <p>Paragraphe 2</p>
  <button>Action</button>
</div>
```

## 📊 Paramètres

| Variable      | Type    | Défaut       | Description                            |
| ------------- | ------- | ------------ | -------------------------------------- |
| `--gap`       | length  | `1rem`       | Espacement uniforme entre les éléments |
| `--gap-x`     | length  | `var(--gap)` | Espacement horizontal                  |
| `--gap-y`     | length  | `var(--gap)` | Espacement vertical                    |
| `--direction` | keyword | `row`        | Direction du layout (row, column)      |
| `--wrap`      | keyword | `wrap`       | Comportement de retour à la ligne      |
| `--align`     | keyword | `stretch`    | Alignement des items                   |

### Échelle d'espacement prédéfinie

| Classe  | Valeur  | Pixels | Usage                        |
| ------- | ------- | ------ | ---------------------------- |
| `--xs`  | 0.25rem | 4px    | Espacement minimal           |
| `--sm`  | 0.5rem  | 8px    | Espacement serré             |
| `--md`  | 1rem    | 16px   | Espacement standard (défaut) |
| `--lg`  | 1.5rem  | 24px   | Espacement confortable       |
| `--xl`  | 2rem    | 32px   | Espacement large             |
| `--2xl` | 3rem    | 48px   | Espacement très large        |
| `--3xl` | 4rem    | 64px   | Espacement extra large       |

### Valeurs courantes pour `--gap`

```css
/* Tailles fixes */
--gap: 0.5rem; /* 8px */
--gap: 1rem; /* 16px */
--gap: 2rem; /* 32px */

/* Tailles responsives */
--gap: clamp(0.5rem, 2vw, 2rem); /* S'adapte à la taille d'écran */
--gap: calc(1rem + 1vw); /* Augmente avec la largeur */

/* Tailles asymétriques */
--gap-x: 1rem; /* Horizontal */
--gap-y: 2rem; /* Vertical */
```

## 📚 Exemples détaillés

### Exemple 1 : Groupe de boutons

```html
<div class="gap-wrapper gap-wrapper--sm">
  <button class="btn-primary">Enregistrer</button>
  <button class="btn-secondary">Annuler</button>
  <button class="btn-outline">Aide</button>
</div>

<style>
  button {
    padding: 0.5rem 1rem;
    border: none;
    border-radius: 0.25rem;
    cursor: pointer;
  }

  .btn-primary {
    background: #3b82f6;
    color: white;
  }

  .btn-secondary {
    background: #6b7280;
    color: white;
  }

  .btn-outline {
    background: transparent;
    border: 1px solid #d1d5db;
    color: #374151;
  }
</style>
```

### Exemple 2 : Grid de cartes

```html
<div class="gap-wrapper gap-wrapper--lg" style="--wrap: wrap">
  <div class="card">
    <img src="product1.jpg" alt="Product 1" />
    <h3>Produit 1</h3>
    <p>19,99 €</p>
    <button>Ajouter</button>
  </div>

  <div class="card">
    <img src="product2.jpg" alt="Product 2" />
    <h3>Produit 2</h3>
    <p>24,99 €</p>
    <button>Ajouter</button>
  </div>

  <div class="card">
    <img src="product3.jpg" alt="Product 3" />
    <h3>Produit 3</h3>
    <p>29,99 €</p>
    <button>Ajouter</button>
  </div>
</div>

<style>
  .card {
    flex: 0 1 300px; /* Min 300px, peut grandir */
    background: white;
    border-radius: 0.5rem;
    padding: 1.5rem;
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
  }

  .card img {
    width: 100%;
    border-radius: 0.25rem;
    margin-bottom: 1rem;
  }
</style>
```

### Exemple 3 : Liste verticale avec séparateurs

```html
<div class="gap-wrapper gap-wrapper--column gap-wrapper--md">
  <div class="list-item">
    <h4>Notification 1</h4>
    <p>Votre commande a été expédiée</p>
    <time>Il y a 2 heures</time>
  </div>

  <div class="list-item">
    <h4>Notification 2</h4>
    <p>Nouveau message reçu</p>
    <time>Il y a 5 heures</time>
  </div>

  <div class="list-item">
    <h4>Notification 3</h4>
    <p>Mise à jour disponible</p>
    <time>Hier</time>
  </div>
</div>

<style>
  .list-item {
    padding: 1rem;
    border-bottom: 1px solid #e5e7eb;
  }

  .list-item:last-child {
    border-bottom: none;
  }

  .list-item h4 {
    margin: 0 0 0.5rem 0;
    font-weight: 600;
  }

  .list-item p {
    margin: 0;
    color: #6b7280;
  }

  .list-item time {
    font-size: 0.875rem;
    color: #9ca3af;
  }
</style>
```

### Exemple 4 : Navigation avec espacement variable

```html
<nav class="gap-wrapper gap-wrapper--justify-between gap-wrapper--center">
  <div class="logo">
    <img src="logo.svg" alt="Logo" />
  </div>

  <div class="gap-wrapper gap-wrapper--md">
    <a href="#">Accueil</a>
    <a href="#">Produits</a>
    <a href="#">À propos</a>
    <a href="#">Contact</a>
  </div>

  <div class="gap-wrapper gap-wrapper--sm">
    <button>Connexion</button>
    <button class="btn-primary">Inscription</button>
  </div>
</nav>

<style>
  nav {
    padding: 1rem 2rem;
    background: white;
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
  }

  nav a {
    text-decoration: none;
    color: #374151;
    font-weight: 500;
  }

  nav a:hover {
    color: #3b82f6;
  }
</style>
```

### Exemple 5 : Tags/Badges

```html
<div class="gap-wrapper gap-wrapper--xs">
  <span class="tag">React</span>
  <span class="tag">TypeScript</span>
  <span class="tag">Node.js</span>
  <span class="tag">MongoDB</span>
  <span class="tag">Docker</span>
  <span class="tag">AWS</span>
</div>

<style>
  .tag {
    display: inline-block;
    padding: 0.25rem 0.75rem;
    background: #dbeafe;
    color: #1e40af;
    border-radius: 9999px;
    font-size: 0.875rem;
    font-weight: 500;
  }
</style>
```

### Exemple 6 : Form layout

```html
<form class="gap-wrapper gap-wrapper--column gap-wrapper--lg">
  <div class="form-group">
    <label for="name">Nom complet</label>
    <input type="text" id="name" placeholder="Jean Dupont" />
  </div>

  <div class="gap-wrapper">
    <div class="form-group" style="flex: 1">
      <label for="email">Email</label>
      <input type="email" id="email" placeholder="jean@example.com" />
    </div>

    <div class="form-group" style="flex: 1">
      <label for="phone">Téléphone</label>
      <input type="tel" id="phone" placeholder="+33 6 12 34 56 78" />
    </div>
  </div>

  <div class="form-group">
    <label for="message">Message</label>
    <textarea id="message" rows="4" placeholder="Votre message..."></textarea>
  </div>

  <div class="gap-wrapper gap-wrapper--sm gap-wrapper--justify-end">
    <button type="reset">Réinitialiser</button>
    <button type="submit" class="btn-primary">Envoyer</button>
  </div>
</form>

<style>
  .form-group {
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
  }

  label {
    font-weight: 500;
    color: #374151;
  }

  input,
  textarea {
    padding: 0.5rem 0.75rem;
    border: 1px solid #d1d5db;
    border-radius: 0.375rem;
    font-size: 1rem;
  }

  input:focus,
  textarea:focus {
    outline: none;
    border-color: #3b82f6;
    box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.1);
  }
</style>
```

### Exemple 7 : Dashboard stats

```html
<div class="gap-wrapper gap-wrapper--xl">
  <div class="stat-card">
    <div class="stat-icon">📈</div>
    <div class="stat-content">
      <h3>12,543</h3>
      <p>Total des ventes</p>
    </div>
  </div>

  <div class="stat-card">
    <div class="stat-icon">👥</div>
    <div class="stat-content">
      <h3>3,891</h3>
      <p>Utilisateurs actifs</p>
    </div>
  </div>

  <div class="stat-card">
    <div class="stat-icon">💰</div>
    <div class="stat-content">
      <h3>89,432 €</h3>
      <p>Revenus</p>
    </div>
  </div>

  <div class="stat-card">
    <div class="stat-icon">⭐</div>
    <div class="stat-content">
      <h3>4.8/5</h3>
      <p>Satisfaction</p>
    </div>
  </div>
</div>

<style>
  .stat-card {
    flex: 1 1 200px;
    display: flex;
    align-items: center;
    gap: 1rem;
    padding: 1.5rem;
    background: white;
    border-radius: 0.5rem;
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
  }

  .stat-icon {
    font-size: 2rem;
  }

  .stat-content h3 {
    margin: 0;
    font-size: 1.5rem;
    font-weight: 700;
    color: #111827;
  }

  .stat-content p {
    margin: 0.25rem 0 0 0;
    color: #6b7280;
    font-size: 0.875rem;
  }
</style>
```

## 🎨 Personnalisation avancée

### Gap responsive avec breakpoints

```html
<div class="gap-wrapper responsive-gap">
  <div>Item 1</div>
  <div>Item 2</div>
  <div>Item 3</div>
</div>

<style>
  .responsive-gap {
    --gap: 0.5rem;
  }

  @media (min-width: 640px) {
    .responsive-gap {
      --gap: 1rem;
    }
  }

  @media (min-width: 1024px) {
    .responsive-gap {
      --gap: 2rem;
    }
  }
</style>
```

### Gap fluide avec clamp

```html
<!-- Gap qui s'adapte automatiquement -->
<div class="gap-wrapper" style="--gap: clamp(0.5rem, 3vw, 3rem)">
  <div>Item 1</div>
  <div>Item 2</div>
  <div>Item 3</div>
</div>
```

### Direction responsive

```html
<div class="gap-wrapper direction-responsive">
  <div>Item 1</div>
  <div>Item 2</div>
  <div>Item 3</div>
</div>

<style>
  .direction-responsive {
    --direction: column;
  }

  @media (min-width: 768px) {
    .direction-responsive {
      --direction: row;
    }
  }
</style>
```

### Gap avec calcul dynamique

```html
<!-- Gap basé sur une échelle -->
<div class="gap-wrapper" style="--gap: calc(var(--base-spacing, 1rem) * 2)">
  <div>Item 1</div>
  <div>Item 2</div>
</div>
```

## 🎯 Cas d'usage courants

### 1. Boutons d'action

```html
<div class="gap-wrapper gap-wrapper--sm">
  <button>Action 1</button>
  <button>Action 2</button>
</div>
```

### 2. Liste de tags

```html
<div class="gap-wrapper gap-wrapper--xs">
  <span class="tag">Tag 1</span>
  <span class="tag">Tag 2</span>
  <span class="tag">Tag 3</span>
</div>
```

### 3. Cards grid

```html
<div class="gap-wrapper gap-wrapper--lg">
  <div class="card">Card 1</div>
  <div class="card">Card 2</div>
  <div class="card">Card 3</div>
</div>
```

### 4. Navigation

```html
<nav class="gap-wrapper gap-wrapper--md">
  <a href="#">Link 1</a>
  <a href="#">Link 2</a>
  <a href="#">Link 3</a>
</nav>
```

### 5. Form buttons

```html
<div class="gap-wrapper gap-wrapper--sm gap-wrapper--justify-end">
  <button type="button">Annuler</button>
  <button type="submit">Valider</button>
</div>
```

### 6. Vertical stack

```html
<div class="gap-wrapper gap-wrapper--column gap-wrapper--lg">
  <section>Section 1</section>
  <section>Section 2</section>
  <section>Section 3</section>
</div>
```

## 🔧 Combinaison avec autres utilitaires

### Avec Grid Wrapper

```html
<div class="grid-wrapper" style="--cols: 3">
  <!-- Chaque grid item a du gap interne -->
  <div class="gap-wrapper gap-wrapper--column gap-wrapper--sm">
    <h3>Titre</h3>
    <p>Contenu</p>
    <button>Action</button>
  </div>

  <div class="gap-wrapper gap-wrapper--column gap-wrapper--sm">
    <h3>Titre</h3>
    <p>Contenu</p>
    <button>Action</button>
  </div>

  <div class="gap-wrapper gap-wrapper--column gap-wrapper--sm">
    <h3>Titre</h3>
    <p>Contenu</p>
    <button>Action</button>
  </div>
</div>
```

### Avec Media Object

```html
<div class="media">
  <img class="media__image" src="avatar.jpg" alt="Avatar" />
  <div class="media__content">
    <h3>Nom</h3>
    <!-- Gap pour les boutons d'action -->
    <div class="gap-wrapper gap-wrapper--xs">
      <button>Suivre</button>
      <button>Message</button>
    </div>
  </div>
</div>
```

### Avec Split Screen

```html
<div class="split">
  <aside>
    <!-- Gap pour la navigation -->
    <nav class="gap-wrapper gap-wrapper--column gap-wrapper--sm">
      <a href="#">Nav 1</a>
      <a href="#">Nav 2</a>
      <a href="#">Nav 3</a>
    </nav>
  </aside>
  <main>
    <!-- Gap pour le contenu -->
    <div class="gap-wrapper gap-wrapper--column gap-wrapper--xl">
      <section>Section 1</section>
      <section>Section 2</section>
    </div>
  </main>
</div>
```

## 📱 Comportement responsive

### Stratégies responsive

```scss
// Option 1 : Media queries classiques
.gap-wrapper {
  --gap: 0.5rem;

  @media (min-width: 640px) {
    --gap: 1rem;
  }

  @media (min-width: 1024px) {
    --gap: 2rem;
  }
}

// Option 2 : Clamp (fluide)
.gap-wrapper--fluid {
  --gap: clamp(0.5rem, 2vw, 2rem);
}

// Option 3 : Container queries (moderne)
@container (min-width: 500px) {
  .gap-wrapper {
    --gap: 2rem;
  }
}
```

### Changer la direction sur mobile

```html
<div class="gap-wrapper stack-mobile">
  <div>Item 1</div>
  <div>Item 2</div>
  <div>Item 3</div>
</div>

<style>
  .stack-mobile {
    --direction: column;
  }

  @media (min-width: 768px) {
    .stack-mobile {
      --direction: row;
    }
  }
</style>
```

## ⚡ Performance & Bonnes pratiques

### ✅ À faire

```html
<!-- Bon : Gap cohérent avec l'échelle de design -->
<div class="gap-wrapper gap-wrapper--md">
  <!-- Bon : Gap responsive -->
  <div class="gap-wrapper" style="--gap: clamp(0.5rem, 2vw, 2rem)">
    <!-- Bon : Utiliser les classes prédéfinies -->
    <div class="gap-wrapper gap-wrapper--lg gap-wrapper--column">
      <!-- Bon : Direction adaptative -->
      <div class="gap-wrapper" style="--direction: column">
        @media (min-width: 768px) { --direction: row; }
      </div>
    </div>
  </div>
</div>
```

### ❌ À éviter

```html
<!-- Mauvais : Gap trop petit (illisible) -->
<div class="gap-wrapper" style="--gap: 0.1rem">
  <!-- Mauvais : Gap incohérent -->
  <div class="gap-wrapper" style="--gap: 0.73rem">
    <!-- Mauvais : Trop de variations de gap -->
    <div style="--gap: 0.5rem"></div>
    <div style="--gap: 0.7rem"></div>
    <div style="--gap: 0.9rem"></div>

    <!-- Mauvais : Gap trop grand pour mobile -->
    <div class="gap-wrapper" style="--gap: 5rem"></div>
  </div>
</div>
```

### Conseils de performance

```scss
// Utiliser des valeurs en rem pour la cohérence
--gap: 1rem; // ✅ Bon

// Éviter les calculs complexes
--gap: calc(1rem + 2vw + 0.5vh); // ❌ Trop complexe

// Préférer clamp pour le responsive
--gap: clamp(0.5rem, 2vw, 2rem); // ✅ Élégant
```

## 🌐 Compatibilité navigateurs

| Navigateur | Version minimale | Support                  |
| ---------- | ---------------- | ------------------------ |
| Chrome     | 84+              | ✅ Complet (Flexbox gap) |
| Firefox    | 63+              | ✅ Complet (Flexbox gap) |
| Safari     | 14.1+            | ✅ Complet (Flexbox gap) |
| Edge       | 84+              | ✅ Complet (Flexbox gap) |
| Opera      | 70+              | ✅ Complet (Flexbox gap) |

### Fallback pour anciens navigateurs

```scss
.gap-wrapper {
  // Fallback avec margin
  > * + * {
    margin-left: var(--gap, 1rem);
  }

  // Gap natif si supporté
  @supports (gap: 1rem) {
    gap: var(--gap-y) var(--gap-x);

    > * + * {
      margin-left: 0;
    }
  }
}
```

## 🐛 Troubleshooting

### Problème : Le gap ne s'applique pas

**Solution** : Vérifiez le support du navigateur ou utilisez le fallback

```scss
// Ajoutez cette règle de fallback
.gap-wrapper > * + * {
  margin-left: var(--gap, 1rem);
}
```

### Problème : Gap différent que prévu

**Solution** : Vérifiez les variables CSS héritées

```css
/* Réinitialisez explicitement */
.gap-wrapper {
  --gap: 1rem;
  --gap-x: var(--gap);
  --gap-y: var(--gap);
}
```

### Problème : Gap trop grand sur mobile

**Solution** : Utilisez un gap responsive

```html
<div class="gap-wrapper" style="--gap: clamp(0.5rem, 2vw, 2rem)"></div>
```

### Problème : Les éléments ne wrappent pas

**Solution** : Vérifiez la propriété flex-wrap

```html
<div class="gap-wrapper" style="--wrap: wrap"></div>
```

## 📦 Échelle complète

```scss
// Toutes les classes de taille disponibles
.gap-wrapper--xs {
  --gap: 0.25rem;
} // 4px
.gap-wrapper--sm {
  --gap: 0.5rem;
} // 8px
.gap-wrapper--md {
  --gap: 1rem;
} // 16px (défaut)
.gap-wrapper--lg {
  --gap: 1.5rem;
} // 24px
.gap-wrapper--xl {
  --gap: 2rem;
} // 32px
.gap-wrapper--2xl {
  --gap: 3rem;
} // 48px
.gap-wrapper--3xl {
  --gap: 4rem;
} // 64px
.gap-wrapper--4xl {
  --gap: 6rem;
} // 96px

// Classes de direction
.gap-wrapper--row {
  --direction: row;
}
.gap-wrapper--column {
  --direction: column;
}

// Classes d'alignement
.gap-wrapper--start {
  --align: flex-start;
}
.gap-wrapper--center {
  --align: center;
}
.gap-wrapper--end {
  --align: flex-end;
}
.gap-wrapper--stretch {
  --align: stretch;
}
.gap-wrapper--baseline {
  --align: baseline;
}

// Classes de justification
.gap-wrapper--justify-start {
  justify-content: flex-start;
}
.gap-wrapper--justify-center {
  justify-content: center;
}
.gap-wrapper--justify-end {
  justify-content: flex-end;
}
.gap-wrapper--justify-between {
  justify-content: space-between;
}
.gap-wrapper--justify-around {
  justify-content: space-around;
}
.gap-wrapper--justify-evenly {
  justify-content: space-evenly;
}

// Classes utilitaires
.gap-wrapper--nowrap {
  --wrap: nowrap;
}
.gap-wrapper--fluid {
  --gap: clamp(0.5rem, 2vw, 2rem);
}
```

## 🎓 Ressources complémentaires

- [CSS Gap Property - MDN](https://developer.mozilla.org/fr/docs/Web/CSS/gap)
- [Flexbox Gap - Can I Use](https://caniuse.com/flexbox-gap)
- [CSS Custom Properties - MDN](https://developer.mozilla.org/fr/docs/Web/CSS/--*)
- [Spacing Design Tokens](https://www.designtokens.org/)

## 📝 Changelog

- **v1.0** - Version initiale avec gap de base
- **v1.1** - Ajout de l'échelle d'espacement complète
- **v1.2** - Support gap-x et gap-y séparés
- **v1.3** - Ajout des variantes de direction et alignement
- **v1.4** - Gap fluide avec clamp()
- **v1.5** - Amélioration du fallback pour anciens navigateurs

---

**Made with ❤️ for consistent spacing**
