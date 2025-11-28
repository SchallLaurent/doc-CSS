# Stack Utility

> Layouts verticaux et horizontaux avec espacements cohérents et contrôle précis de l'alignement

## 📋 Description

**Stack** est un utilitaire CSS qui permet de créer facilement des layouts en pile (vertical ou horizontal) avec des espacements cohérents entre les éléments enfants. C'est l'alternative moderne et flexible aux marges bottom traditionnelles, utilisant CSS Flexbox et Gap pour un contrôle précis.

### ✨ Caractéristiques principales

- 📚 **Stack vertical** : Empiler des éléments verticalement (défaut)
- ➡️ **Stack horizontal** : Empiler horizontalement
- 📏 **Gap variable** : 7 tailles prédéfinies (xs à 2xl)
- 🎯 **Alignement** : start, center, end, stretch
- 🔲 **Dividers** : Séparateurs entre éléments
- 📱 **Responsive** : Gaps adaptatifs par breakpoint
- 🔧 **Variables CSS** : Personnalisation complète
- ♿ **Accessibilité** : Structure sémantique

## 🚀 Installation

### Code SCSS

```scss
// _stack.scss

// Variables globales
:root {
  --stack-gap: 1rem;
  --stack-gap-xs: 0.25rem;
  --stack-gap-sm: 0.5rem;
  --stack-gap-md: 1rem;
  --stack-gap-lg: 1.5rem;
  --stack-gap-xl: 2rem;
  --stack-gap-2xl: 3rem;
}

// ============================================
// BASE STACK (vertical par défaut)
// ============================================

.stack {
  display: flex;
  flex-direction: column;
  gap: var(--stack-gap, 1rem);
}

// ============================================
// TAILLES DE GAP
// ============================================

.stack--xs {
  gap: var(--stack-gap-xs, 0.25rem);
}

.stack--sm {
  gap: var(--stack-gap-sm, 0.5rem);
}

.stack--md {
  gap: var(--stack-gap-md, 1rem);
}

.stack--lg {
  gap: var(--stack-gap-lg, 1.5rem);
}

.stack--xl {
  gap: var(--stack-gap-xl, 2rem);
}

.stack--2xl {
  gap: var(--stack-gap-2xl, 3rem);
}

// Gap personnalisé via variable
.stack--custom {
  gap: var(--gap);
}

// ============================================
// DIRECTION
// ============================================

// Horizontal stack
.stack--horizontal {
  flex-direction: row;
}

// Horizontal avec wrap
.stack--horizontal-wrap {
  flex-direction: row;
  flex-wrap: wrap;
}

// Reverse
.stack--reverse {
  flex-direction: column-reverse;
}

.stack--horizontal-reverse {
  flex-direction: row-reverse;
}

// ============================================
// ALIGNEMENT (align-items)
// ============================================

.stack--start {
  align-items: flex-start;
}

.stack--center {
  align-items: center;
}

.stack--end {
  align-items: flex-end;
}

.stack--stretch {
  align-items: stretch;
}

.stack--baseline {
  align-items: baseline;
}

// ============================================
// JUSTIFICATION (justify-content)
// ============================================

.stack--justify-start {
  justify-content: flex-start;
}

.stack--justify-center {
  justify-content: center;
}

.stack--justify-end {
  justify-content: flex-end;
}

.stack--justify-between {
  justify-content: space-between;
}

.stack--justify-around {
  justify-content: space-around;
}

.stack--justify-evenly {
  justify-content: space-evenly;
}

// ============================================
// DIVIDERS (séparateurs)
// ============================================

.stack--divider {
  > * + * {
    border-top: 1px solid var(--divider-color, #e5e7eb);
    padding-top: var(--stack-gap, 1rem);
  }
}

.stack--horizontal.stack--divider {
  > * + * {
    border-top: none;
    border-left: 1px solid var(--divider-color, #e5e7eb);
    padding-top: 0;
    padding-left: var(--stack-gap, 1rem);
  }
}

// Divider épais
.stack--divider-thick {
  > * + * {
    border-top-width: 2px;
  }
}

.stack--horizontal.stack--divider-thick {
  > * + * {
    border-left-width: 2px;
  }
}

// Divider avec couleur custom
.stack--divider-dark {
  --divider-color: #374151;
}

.stack--divider-light {
  --divider-color: #f3f4f6;
}

// ============================================
// RESPONSIVE GAPS
// ============================================

// Gap mobile
.stack--gap-mobile-xs {
  @media (max-width: 767px) {
    gap: var(--stack-gap-xs, 0.25rem);
  }
}

.stack--gap-mobile-sm {
  @media (max-width: 767px) {
    gap: var(--stack-gap-sm, 0.5rem);
  }
}

.stack--gap-mobile-md {
  @media (max-width: 767px) {
    gap: var(--stack-gap-md, 1rem);
  }
}

// Direction responsive
.stack--horizontal-desktop {
  flex-direction: column;

  @media (min-width: 1024px) {
    flex-direction: row;
  }
}

.stack--horizontal-tablet {
  flex-direction: column;

  @media (min-width: 768px) {
    flex-direction: row;
  }
}

// ============================================
// RECURSIVE STACK (espacement imbriqué)
// ============================================

.stack--recursive {
  * + * {
    margin-top: var(--stack-gap, 1rem);
  }
}

// ============================================
// STACK AVEC FULL HEIGHT
// ============================================

.stack--full-height {
  min-height: 100%;
}

.stack--stretch-children {
  > * {
    flex: 1;
  }
}

// ============================================
// COMBINAISONS COMMUNES
// ============================================

// Stack centré avec gap large
.stack--center-lg {
  align-items: center;
  gap: var(--stack-gap-lg, 1.5rem);
}

// Stack avec divider et padding
.stack--card {
  padding: 1.5rem;
  background: white;
  border-radius: 0.75rem;

  > * + * {
    border-top: 1px solid #e5e7eb;
    padding-top: var(--stack-gap, 1rem);
    margin-top: var(--stack-gap, 1rem);
  }
}

// Stack liste avec hover
.stack--list {
  > * {
    padding: 1rem;
    border-radius: 0.5rem;
    transition: background-color 200ms;
    cursor: pointer;

    &:hover {
      background-color: #f9fafb;
    }
  }
}

// ============================================
// UTILITAIRES
// ============================================

// Retirer le gap pour un enfant spécifique
.stack > .no-gap {
  margin-top: calc(-1 * var(--stack-gap, 1rem));
}

// Doubler le gap pour un enfant
.stack > .double-gap {
  margin-top: var(--stack-gap, 1rem);
}

// Élément sticky dans le stack
.stack > .sticky-top {
  position: sticky;
  top: 0;
  z-index: 10;
  background: inherit;
}
```

### Import dans votre projet

```scss
// Dans styles.scss
@import "utilities/stack";
```

## 💡 Utilisation de base

### Exemple 1 : Stack vertical simple

```html
<div class="stack stack--md">
  <div class="card">Item 1</div>
  <div class="card">Item 2</div>
  <div class="card">Item 3</div>
</div>

<style>
  .card {
    padding: 1.5rem;
    background: white;
    border-radius: 0.5rem;
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
  }
</style>
```

### Exemple 2 : Stack horizontal

```html
<div class="stack stack--horizontal stack--md">
  <button class="btn">Button 1</button>
  <button class="btn">Button 2</button>
  <button class="btn">Button 3</button>
</div>

<style>
  .btn {
    padding: 0.75rem 1.5rem;
    background: #3b82f6;
    color: white;
    border: none;
    border-radius: 0.5rem;
    cursor: pointer;
  }
</style>
```

### Exemple 3 : Stack avec dividers

```html
<div class="stack stack--lg stack--divider">
  <div>Section 1</div>
  <div>Section 2</div>
  <div>Section 3</div>
</div>
```

### Exemple 4 : Stack centré

```html
<div class="stack stack--center stack--lg">
  <img
    src="avatar.jpg"
    alt="Avatar"
    style="width: 100px; height: 100px; border-radius: 50%;"
  />
  <h2>Jean Dupont</h2>
  <p>Designer & Developer</p>
  <button class="btn">Follow</button>
</div>
```

## 📊 Paramètres

| Variable          | Type   | Défaut    | Description             |
| ----------------- | ------ | --------- | ----------------------- |
| `--stack-gap`     | length | `1rem`    | Gap par défaut          |
| `--stack-gap-xs`  | length | `0.25rem` | Gap extra-small         |
| `--stack-gap-sm`  | length | `0.5rem`  | Gap small               |
| `--stack-gap-md`  | length | `1rem`    | Gap medium              |
| `--stack-gap-lg`  | length | `1.5rem`  | Gap large               |
| `--stack-gap-xl`  | length | `2rem`    | Gap extra-large         |
| `--stack-gap-2xl` | length | `3rem`    | Gap 2x extra-large      |
| `--divider-color` | color  | `#e5e7eb` | Couleur du divider      |
| `--gap`           | length | -         | Gap custom via variable |

### Modificateurs disponibles

| Catégorie         | Classes                                                             | Description        |
| ----------------- | ------------------------------------------------------------------- | ------------------ |
| **Taille**        | stack--xs, stack--sm, stack--md, stack--lg, stack--xl, stack--2xl   | Gap prédéfini      |
| **Direction**     | stack--horizontal, stack--horizontal-wrap, stack--reverse           | Direction du stack |
| **Alignement**    | stack--start, stack--center, stack--end, stack--stretch             | align-items        |
| **Justification** | stack--justify-start, stack--justify-center, stack--justify-between | justify-content    |
| **Divider**       | stack--divider, stack--divider-thick, stack--divider-dark           | Séparateurs        |
| **Responsive**    | stack--gap-mobile-md, stack--horizontal-desktop                     | Adaptatif          |

## 📚 Exemples détaillés

### Exemple 1 : Form avec stack vertical

```html
<form class="form-container">
  <div class="stack stack--lg">
    <div>
      <h2>Créer un compte</h2>
      <p class="text-muted">Remplissez les informations ci-dessous</p>
    </div>

    <div class="stack stack--sm">
      <label for="name">Nom complet</label>
      <input
        type="text"
        id="name"
        class="input rounded-lg"
        placeholder="Jean Dupont"
      />
    </div>

    <div class="stack stack--sm">
      <label for="email">Email</label>
      <input
        type="email"
        id="email"
        class="input rounded-lg"
        placeholder="jean@example.com"
      />
    </div>

    <div class="stack stack--sm">
      <label for="password">Mot de passe</label>
      <input
        type="password"
        id="password"
        class="input rounded-lg"
        placeholder="••••••••"
      />
      <small class="text-muted">Minimum 8 caractères</small>
    </div>

    <div class="stack stack--sm">
      <label for="confirm-password">Confirmer le mot de passe</label>
      <input
        type="password"
        id="confirm-password"
        class="input rounded-lg"
        placeholder="••••••••"
      />
    </div>

    <div class="stack stack--horizontal stack--sm">
      <input type="checkbox" id="terms" />
      <label for="terms">J'accepte les conditions d'utilisation</label>
    </div>

    <div class="stack stack--horizontal stack--sm">
      <button type="submit" class="btn btn-primary rounded-lg">
        Créer mon compte
      </button>
      <button type="button" class="btn btn-secondary rounded-lg">
        Annuler
      </button>
    </div>
  </div>
</form>

<style>
  .form-container {
    max-width: 500px;
    margin: 2rem auto;
    padding: 2rem;
    background: white;
    border-radius: 1rem;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  }

  label {
    font-weight: 600;
    font-size: 0.875rem;
    color: #374151;
  }

  .input {
    width: 100%;
    padding: 0.75rem 1rem;
    border: 1px solid #e5e7eb;
    font-size: 1rem;
  }

  .input:focus {
    outline: none;
    border-color: #3b82f6;
    box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.1);
  }

  .text-muted {
    color: #6b7280;
    font-size: 0.875rem;
    margin: 0;
  }

  small {
    display: block;
  }

  .btn {
    padding: 0.75rem 1.5rem;
    border: none;
    cursor: pointer;
    font-weight: 600;
    transition: all 200ms;
  }

  .btn-primary {
    background: #3b82f6;
    color: white;
  }

  .btn-primary:hover {
    background: #2563eb;
  }

  .btn-secondary {
    background: #f3f4f6;
    color: #374151;
  }

  .btn-secondary:hover {
    background: #e5e7eb;
  }
</style>
```

### Exemple 2 : Navigation avec stack horizontal

```html
<nav class="navbar">
  <div class="container">
    <div class="stack stack--horizontal stack--justify-between">
      <div class="logo">
        <img src="logo.svg" alt="Logo" style="height: 40px;" />
      </div>

      <div class="stack stack--horizontal stack--md">
        <a href="#" class="nav-link">Accueil</a>
        <a href="#" class="nav-link">À propos</a>
        <a href="#" class="nav-link">Services</a>
        <a href="#" class="nav-link">Portfolio</a>
        <a href="#" class="nav-link">Blog</a>
        <a href="#" class="nav-link">Contact</a>
      </div>

      <div class="stack stack--horizontal stack--sm">
        <button class="btn-outline rounded-lg">Connexion</button>
        <button class="btn-primary rounded-lg">S'inscrire</button>
      </div>
    </div>
  </div>
</nav>

<style>
  .navbar {
    background: white;
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
    padding: 1rem 0;
    position: sticky;
    top: 0;
    z-index: 100;
  }

  .container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 2rem;
  }

  .nav-link {
    text-decoration: none;
    color: #374151;
    font-weight: 500;
    padding: 0.5rem 0.75rem;
    border-radius: 0.5rem;
    transition: all 200ms;
  }

  .nav-link:hover {
    color: #3b82f6;
    background: #eff6ff;
  }

  .btn-outline {
    padding: 0.5rem 1.25rem;
    background: transparent;
    border: 1px solid #e5e7eb;
    color: #374151;
    cursor: pointer;
    font-weight: 500;
    transition: all 200ms;
  }

  .btn-outline:hover {
    border-color: #3b82f6;
    color: #3b82f6;
  }

  .btn-primary {
    padding: 0.5rem 1.25rem;
    background: #3b82f6;
    color: white;
    border: none;
    cursor: pointer;
    font-weight: 600;
    transition: all 200ms;
  }

  .btn-primary:hover {
    background: #2563eb;
  }
</style>
```

### Exemple 3 : Pricing cards avec stack

```html
<div class="pricing-section">
  <div class="container">
    <div class="stack stack--center stack--xl">
      <div class="section-header stack stack--center stack--sm">
        <h2>Choisissez votre plan</h2>
        <p class="text-muted">Des prix simples et transparents pour tous</p>
      </div>

      <div class="stack stack--horizontal stack--lg stack--horizontal-tablet">
        <!-- Plan Starter -->
        <div class="pricing-card rounded-2xl shadow-wrapper shadow-wrapper--lg">
          <div class="stack stack--lg">
            <div class="stack stack--sm">
              <h3>Starter</h3>
              <p class="text-muted">Pour les petits projets</p>
            </div>

            <div class="stack stack--xs">
              <div class="price">
                <span class="price-amount">9€</span>
                <span class="price-period">/mois</span>
              </div>
              <p class="text-muted">Facturé annuellement</p>
            </div>

            <button class="btn-outline rounded-lg">Choisir Starter</button>

            <div class="stack stack--divider stack--sm">
              <div class="feature">✓ 5 projets</div>
              <div class="feature">✓ 10 Go de stockage</div>
              <div class="feature">✓ Support email</div>
              <div class="feature">✓ Mises à jour gratuites</div>
            </div>
          </div>
        </div>

        <!-- Plan Pro (Featured) -->
        <div
          class="pricing-card pricing-card--featured rounded-2xl shadow-wrapper shadow-wrapper--xl"
        >
          <div class="badge-featured rounded-full">⭐ Populaire</div>

          <div class="stack stack--lg">
            <div class="stack stack--sm">
              <h3>Pro</h3>
              <p class="text-muted">Pour les professionnels</p>
            </div>

            <div class="stack stack--xs">
              <div class="price">
                <span class="price-amount">29€</span>
                <span class="price-period">/mois</span>
              </div>
              <p class="text-muted">Facturé annuellement</p>
            </div>

            <button class="btn-primary rounded-lg">Choisir Pro</button>

            <div class="stack stack--divider stack--sm">
              <div class="feature">✓ Projets illimités</div>
              <div class="feature">✓ 100 Go de stockage</div>
              <div class="feature">✓ Support prioritaire 24/7</div>
              <div class="feature">✓ Mises à jour gratuites</div>
              <div class="feature">✓ Fonctionnalités avancées</div>
              <div class="feature">✓ Collaboration en équipe</div>
            </div>
          </div>
        </div>

        <!-- Plan Enterprise -->
        <div class="pricing-card rounded-2xl shadow-wrapper shadow-wrapper--lg">
          <div class="stack stack--lg">
            <div class="stack stack--sm">
              <h3>Enterprise</h3>
              <p class="text-muted">Pour les grandes équipes</p>
            </div>

            <div class="stack stack--xs">
              <div class="price">
                <span class="price-amount">99€</span>
                <span class="price-period">/mois</span>
              </div>
              <p class="text-muted">Facturé annuellement</p>
            </div>

            <button class="btn-outline rounded-lg">Nous contacter</button>

            <div class="stack stack--divider stack--sm">
              <div class="feature">✓ Tout du plan Pro</div>
              <div class="feature">✓ Stockage illimité</div>
              <div class="feature">✓ Support dédié</div>
              <div class="feature">✓ SLA garanti</div>
              <div class="feature">✓ Formation personnalisée</div>
              <div class="feature">✓ Intégrations custom</div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>

<style>
  .pricing-section {
    padding: 5rem 2rem;
    background: linear-gradient(to bottom, #f9fafb, white);
  }

  .section-header {
    text-align: center;
    max-width: 600px;
  }

  .section-header h2 {
    font-size: 2.5rem;
    margin: 0;
  }

  .pricing-card {
    flex: 1;
    min-width: 300px;
    padding: 2.5rem 2rem;
    background: white;
    position: relative;
  }

  .pricing-card--featured {
    border: 2px solid #3b82f6;
    transform: scale(1.05);
  }

  .badge-featured {
    position: absolute;
    top: -12px;
    left: 50%;
    transform: translateX(-50%);
    padding: 0.5rem 1.5rem;
    background: #3b82f6;
    color: white;
    font-size: 0.875rem;
    font-weight: 600;
  }

  .pricing-card h3 {
    font-size: 1.75rem;
    margin: 0;
  }

  .price {
    display: flex;
    align-items: baseline;
    gap: 0.5rem;
  }

  .price-amount {
    font-size: 3rem;
    font-weight: 800;
    color: #111827;
  }

  .price-period {
    font-size: 1.25rem;
    color: #6b7280;
  }

  .feature {
    color: #374151;
  }

  @media (max-width: 767px) {
    .pricing-card--featured {
      transform: scale(1);
    }
  }
</style>
```

### Exemple 4 : Timeline avec stack et dividers

```html
<div class="timeline-container">
  <div class="stack stack--xl stack--divider">
    <!-- Event 1 -->
    <div class="timeline-event stack stack--horizontal stack--md">
      <div class="timeline-date">
        <div class="date-badge rounded-lg">
          <span class="date-day">15</span>
          <span class="date-month">Nov</span>
        </div>
      </div>

      <div class="timeline-content stack stack--sm">
        <h3>Lancement du produit</h3>
        <p class="text-muted">
          Nous avons officiellement lancé la version 2.0 avec de nouvelles
          fonctionnalités révolutionnaires.
        </p>
        <div class="stack stack--horizontal stack--xs">
          <span class="tag rounded-full">Product</span>
          <span class="tag rounded-full">Launch</span>
        </div>
      </div>
    </div>

    <!-- Event 2 -->
    <div class="timeline-event stack stack--horizontal stack--md">
      <div class="timeline-date">
        <div class="date-badge rounded-lg">
          <span class="date-day">08</span>
          <span class="date-month">Nov</span>
        </div>
      </div>

      <div class="timeline-content stack stack--sm">
        <h3>Nouveau partenariat</h3>
        <p class="text-muted">
          Partenariat stratégique avec TechCorp pour accélérer notre expansion
          internationale.
        </p>
        <div class="stack stack--horizontal stack--xs">
          <span class="tag rounded-full">Partnership</span>
          <span class="tag rounded-full">Business</span>
        </div>
      </div>
    </div>

    <!-- Event 3 -->
    <div class="timeline-event stack stack--horizontal stack--md">
      <div class="timeline-date">
        <div class="date-badge rounded-lg">
          <span class="date-day">01</span>
          <span class="date-month">Nov</span>
        </div>
      </div>

      <div class="timeline-content stack stack--sm">
        <h3>Levée de fonds Série B</h3>
        <p class="text-muted">
          Levée de 50M€ en Série B menée par Sequoia Capital pour financer notre
          croissance.
        </p>
        <div class="stack stack--horizontal stack--xs">
          <span class="tag rounded-full">Funding</span>
          <span class="tag rounded-full">Milestone</span>
        </div>
      </div>
    </div>

    <!-- Event 4 -->
    <div class="timeline-event stack stack--horizontal stack--md">
      <div class="timeline-date">
        <div class="date-badge rounded-lg">
          <span class="date-day">25</span>
          <span class="date-month">Oct</span>
        </div>
      </div>

      <div class="timeline-content stack stack--sm">
        <h3>Nouvelle équipe</h3>
        <p class="text-muted">
          Recrutement de 20 nouveaux talents pour renforcer nos équipes
          engineering et design.
        </p>
        <div class="stack stack--horizontal stack--xs">
          <span class="tag rounded-full">Team</span>
          <span class="tag rounded-full">Growth</span>
        </div>
      </div>
    </div>
  </div>
</div>

<style>
  .timeline-container {
    max-width: 800px;
    margin: 3rem auto;
    padding: 2rem;
  }

  .timeline-event {
    align-items: flex-start;
  }

  .timeline-date {
    flex-shrink: 0;
  }

  .date-badge {
    width: 80px;
    padding: 1rem;
    background: linear-gradient(135deg, #3b82f6 0%, #2563eb 100%);
    color: white;
    text-align: center;
  }

  .date-day {
    display: block;
    font-size: 2rem;
    font-weight: 800;
    line-height: 1;
  }

  .date-month {
    display: block;
    font-size: 0.875rem;
    text-transform: uppercase;
    letter-spacing: 0.05em;
    margin-top: 0.25rem;
  }

  .timeline-content {
    flex: 1;
  }

  .timeline-content h3 {
    margin: 0;
    font-size: 1.5rem;
  }

  .timeline-content p {
    margin: 0;
    line-height: 1.6;
  }

  .tag {
    padding: 0.25rem 0.75rem;
    background: #eff6ff;
    color: #3b82f6;
    font-size: 0.75rem;
    font-weight: 600;
  }
</style>
```

### Exemple 5 : Comment section avec nested stacks

```html
<div class="comments-section">
  <div class="stack stack--xl">
    <h2>Commentaires (3)</h2>

    <div class="stack stack--lg stack--divider">
      <!-- Comment 1 -->
      <div class="comment">
        <div class="stack stack--md">
          <div class="stack stack--horizontal stack--sm">
            <img src="avatar1.jpg" alt="User 1" class="avatar rounded-full" />
            <div class="stack stack--xs">
              <div class="comment-author">Marie Dupont</div>
              <div class="comment-meta">Il y a 2 heures</div>
            </div>
          </div>

          <p class="comment-text">
            Super article ! Les explications sont claires et les exemples très
            concrets. Merci pour ce partage.
          </p>

          <div class="stack stack--horizontal stack--sm">
            <button class="btn-icon">👍 12</button>
            <button class="btn-icon">💬 Répondre</button>
          </div>
        </div>
      </div>

      <!-- Comment 2 avec réponse -->
      <div class="comment">
        <div class="stack stack--lg">
          <div class="stack stack--md">
            <div class="stack stack--horizontal stack--sm">
              <img src="avatar2.jpg" alt="User 2" class="avatar rounded-full" />
              <div class="stack stack--xs">
                <div class="comment-author">Jean Martin</div>
                <div class="comment-meta">Il y a 5 heures</div>
              </div>
            </div>

            <p class="comment-text">
              Excellent contenu ! J'ai une question sur la partie concernant les
              performances. Avez-vous des benchmarks ?
            </p>

            <div class="stack stack--horizontal stack--sm">
              <button class="btn-icon">👍 8</button>
              <button class="btn-icon">💬 Répondre</button>
            </div>
          </div>

          <!-- Réponse imbriquée -->
          <div class="comment-reply">
            <div class="stack stack--md">
              <div class="stack stack--horizontal stack--sm">
                <img
                  src="avatar-author.jpg"
                  alt="Author"
                  class="avatar avatar--sm rounded-full"
                />
                <div class="stack stack--xs">
                  <div class="comment-author">
                    Sophie Leroux
                    <span class="badge-author rounded-full">Auteur</span>
                  </div>
                  <div class="comment-meta">Il y a 3 heures</div>
                </div>
              </div>

              <p class="comment-text">
                Merci Jean ! Oui, j'ai fait des benchmarks que je partagerai
                dans un prochain article. En résumé, on observe une amélioration
                de 40% en moyenne.
              </p>

              <div class="stack stack--horizontal stack--sm">
                <button class="btn-icon">👍 15</button>
                <button class="btn-icon">💬 Répondre</button>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- Comment 3 -->
      <div class="comment">
        <div class="stack stack--md">
          <div class="stack stack--horizontal stack--sm">
            <img src="avatar3.jpg" alt="User 3" class="avatar rounded-full" />
            <div class="stack stack--xs">
              <div class="comment-author">Thomas Dubois</div>
              <div class="comment-meta">Il y a 1 jour</div>
            </div>
          </div>

          <p class="comment-text">
            Article très complet. J'aurais aimé voir plus d'exemples de code
            pour les cas d'usage avancés.
          </p>

          <div class="stack stack--horizontal stack--sm">
            <button class="btn-icon">👍 5</button>
            <button class="btn-icon">💬 Répondre</button>
          </div>
        </div>
      </div>
    </div>

    <!-- Add comment form -->
    <div class="comment-form rounded-xl">
      <div class="stack stack--md">
        <h3>Ajouter un commentaire</h3>
        <textarea
          class="textarea rounded-lg"
          rows="4"
          placeholder="Votre commentaire..."
        ></textarea>
        <div class="stack stack--horizontal stack--sm stack--justify-end">
          <button class="btn-secondary rounded-lg">Annuler</button>
          <button class="btn-primary rounded-lg">Publier</button>
        </div>
      </div>
    </div>
  </div>
</div>

<style>
  .comments-section {
    max-width: 800px;
    margin: 3rem auto;
    padding: 2rem;
  }

  .comments-section h2 {
    font-size: 2rem;
    margin: 0;
  }

  .comment {
    padding: 1.5rem;
    background: #f9fafb;
    border-radius: 1rem;
  }

  .avatar {
    width: 48px;
    height: 48px;
    object-fit: cover;
    flex-shrink: 0;
  }

  .avatar--sm {
    width: 40px;
    height: 40px;
  }

  .comment-author {
    font-weight: 600;
    color: #111827;
    display: flex;
    align-items: center;
    gap: 0.5rem;
  }

  .badge-author {
    padding: 0.125rem 0.5rem;
    background: #3b82f6;
    color: white;
    font-size: 0.75rem;
    font-weight: 600;
  }

  .comment-meta {
    font-size: 0.875rem;
    color: #6b7280;
  }

  .comment-text {
    margin: 0;
    color: #374151;
    line-height: 1.6;
  }

  .btn-icon {
    padding: 0.5rem 1rem;
    background: white;
    border: 1px solid #e5e7eb;
    border-radius: 0.5rem;
    cursor: pointer;
    font-size: 0.875rem;
    transition: all 200ms;
  }

  .btn-icon:hover {
    background: #f9fafb;
  }

  .comment-reply {
    margin-left: 3rem;
    padding: 1.5rem;
    background: white;
    border-radius: 1rem;
    border-left: 3px solid #3b82f6;
  }

  .comment-form {
    padding: 2rem;
    background: white;
    border: 2px solid #e5e7eb;
  }

  .comment-form h3 {
    margin: 0;
    font-size: 1.25rem;
  }

  .textarea {
    width: 100%;
    padding: 1rem;
    border: 1px solid #e5e7eb;
    font-family: inherit;
    font-size: 1rem;
    resize: vertical;
  }

  .textarea:focus {
    outline: none;
    border-color: #3b82f6;
    box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.1);
  }

  .btn-secondary {
    padding: 0.75rem 1.5rem;
    background: #f3f4f6;
    color: #374151;
    border: none;
    cursor: pointer;
    font-weight: 600;
  }

  .btn-primary {
    padding: 0.75rem 1.5rem;
    background: #3b82f6;
    color: white;
    border: none;
    cursor: pointer;
    font-weight: 600;
  }
</style>
```

### Exemple 6 : Dashboard stats avec stack

```html
<div class="dashboard">
  <div class="container">
    <div class="stack stack--2xl">
      <!-- Header -->
      <div class="stack stack--horizontal stack--justify-between">
        <div class="stack stack--xs">
          <h1>Tableau de bord</h1>
          <p class="text-muted">Vue d'ensemble de vos statistiques</p>
        </div>

        <div class="stack stack--horizontal stack--sm">
          <button class="btn-secondary rounded-lg">📊 Exporter</button>
          <button class="btn-primary rounded-lg">➕ Nouveau projet</button>
        </div>
      </div>

      <!-- Stats cards -->
      <div class="stats-grid">
        <div class="stat-card rounded-xl">
          <div class="stack stack--sm">
            <div class="stat-icon">👥</div>
            <div class="stack stack--xs">
              <div class="stat-label">Utilisateurs</div>
              <div class="stat-value">12,345</div>
            </div>
            <div class="stat-change positive">+12% ce mois</div>
          </div>
        </div>

        <div class="stat-card rounded-xl">
          <div class="stack stack--sm">
            <div class="stat-icon">💰</div>
            <div class="stack stack--xs">
              <div class="stat-label">Revenus</div>
              <div class="stat-value">456,789 €</div>
            </div>
            <div class="stat-change positive">+23% ce mois</div>
          </div>
        </div>

        <div class="stat-card rounded-xl">
          <div class="stack stack--sm">
            <div class="stat-icon">📦</div>
            <div class="stack stack--xs">
              <div class="stat-label">Commandes</div>
              <div class="stat-value">8,901</div>
            </div>
            <div class="stat-change negative">-5% ce mois</div>
          </div>
        </div>

        <div class="stat-card rounded-xl">
          <div class="stack stack--sm">
            <div class="stat-icon">⭐</div>
            <div class="stack stack--xs">
              <div class="stat-label">Satisfaction</div>
              <div class="stat-value">4.8/5</div>
            </div>
            <div class="stat-change positive">+0.3 ce mois</div>
          </div>
        </div>
      </div>

      <!-- Charts section -->
      <div class="charts-grid">
        <div class="chart-card rounded-xl">
          <div class="stack stack--md">
            <h3>Ventes mensuelles</h3>
            <div class="chart-placeholder rounded-lg">[Chart placeholder]</div>
          </div>
        </div>

        <div class="activity-card rounded-xl">
          <div class="stack stack--md">
            <h3>Activité récente</h3>
            <div class="stack stack--sm stack--divider">
              <div class="activity-item stack stack--horizontal stack--sm">
                <div class="activity-avatar rounded-full">JD</div>
                <div class="stack stack--xs">
                  <div class="activity-text">
                    <strong>Jean Dupont</strong> a créé un projet
                  </div>
                  <div class="activity-time">Il y a 5 minutes</div>
                </div>
              </div>

              <div class="activity-item stack stack--horizontal stack--sm">
                <div class="activity-avatar rounded-full">MM</div>
                <div class="stack stack--xs">
                  <div class="activity-text">
                    <strong>Marie Martin</strong> a ajouté un commentaire
                  </div>
                  <div class="activity-time">Il y a 12 minutes</div>
                </div>
              </div>

              <div class="activity-item stack stack--horizontal stack--sm">
                <div class="activity-avatar rounded-full">TL</div>
                <div class="stack stack--xs">
                  <div class="activity-text">
                    <strong>Thomas Leroux</strong> a terminé une tâche
                  </div>
                  <div class="activity-time">Il y a 1 heure</div>
                </div>
              </div>

              <div class="activity-item stack stack--horizontal stack--sm">
                <div class="activity-avatar rounded-full">SD</div>
                <div class="stack stack--xs">
                  <div class="activity-text">
                    <strong>Sophie Dubois</strong> a invité un membre
                  </div>
                  <div class="activity-time">Il y a 2 heures</div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>

<style>
  .dashboard {
    padding: 3rem 0;
    background: #f9fafb;
    min-height: 100vh;
  }

  .dashboard h1 {
    margin: 0;
    font-size: 2.5rem;
  }

  .stats-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 1.5rem;
  }

  .stat-card {
    padding: 2rem;
    background: white;
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
  }

  .stat-icon {
    font-size: 3rem;
  }

  .stat-label {
    font-size: 0.875rem;
    color: #6b7280;
    text-transform: uppercase;
    letter-spacing: 0.05em;
  }

  .stat-value {
    font-size: 2.5rem;
    font-weight: 800;
    color: #111827;
  }

  .stat-change {
    font-size: 0.875rem;
    font-weight: 600;
  }

  .stat-change.positive {
    color: #059669;
  }

  .stat-change.negative {
    color: #dc2626;
  }

  .charts-grid {
    display: grid;
    grid-template-columns: 2fr 1fr;
    gap: 2rem;
  }

  @media (max-width: 1023px) {
    .charts-grid {
      grid-template-columns: 1fr;
    }
  }

  .chart-card,
  .activity-card {
    padding: 2rem;
    background: white;
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
  }

  .chart-card h3,
  .activity-card h3 {
    margin: 0;
    font-size: 1.25rem;
  }

  .chart-placeholder {
    height: 300px;
    background: #f3f4f6;
    display: flex;
    align-items: center;
    justify-content: center;
    color: #9ca3af;
    font-weight: 600;
  }

  .activity-item {
    align-items: flex-start;
  }

  .activity-avatar {
    width: 40px;
    height: 40px;
    background: #3b82f6;
    color: white;
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: 600;
    font-size: 0.875rem;
    flex-shrink: 0;
  }

  .activity-text {
    color: #374151;
    font-size: 0.875rem;
  }

  .activity-time {
    color: #9ca3af;
    font-size: 0.75rem;
  }
</style>
```

## 🎨 Personnalisation avancée

### Gap personnalisé

```html
<div class="stack stack--custom" style="--gap: 2.5rem">
  Custom gap de 2.5rem
</div>
```

### Divider avec couleur custom

```html
<div class="stack stack--divider" style="--divider-color: #3b82f6">
  Divider bleu
</div>
```

### Stack avec transitions

```scss
.stack--animated {
  > * {
    transition: all 300ms ease-in-out;

    &:hover {
      transform: translateX(8px);
    }
  }
}
```

## 🎯 Cas d'usage courants

### 1. Formulaires

```html
<div class="stack stack--lg">
  <input type="text" />
  <input type="email" />
  <button>Submit</button>
</div>
```

### 2. Navigation

```html
<div class="stack stack--horizontal stack--md">
  <a href="#">Link 1</a>
  <a href="#">Link 2</a>
</div>
```

### 3. Cards

```html
<div class="stack stack--md">
  <h3>Title</h3>
  <p>Content</p>
  <button>CTA</button>
</div>
```

### 4. Lists

```html
<div class="stack stack--sm stack--divider">
  <div>Item 1</div>
  <div>Item 2</div>
</div>
```

### 5. Profiles

```html
<div class="stack stack--center stack--lg">
  <img src="avatar.jpg" class="rounded-full" />
  <h2>Name</h2>
  <p>Bio</p>
</div>
```

## 🔧 Combinaison avec autres utilitaires

### Avec Rounded

```html
<div class="stack stack--md rounded-xl">Stack avec coins arrondis</div>
```

### Avec Shadow Wrapper

```html
<div class="stack stack--lg shadow-wrapper shadow-wrapper--md">
  Stack avec ombre
</div>
```

### Avec Hover Effects

```html
<div class="stack stack--sm hover-lift">Stack interactif</div>
```

## 📱 Comportement responsive

### Gap adaptatif

```html
<div class="stack stack--lg stack--gap-mobile-sm">
  Gap large sur desktop, small sur mobile
</div>
```

### Direction responsive

```html
<div class="stack stack--horizontal-tablet">
  Vertical sur mobile, horizontal sur tablet+
</div>
```

## ⚡ Performance & Bonnes pratiques

### ✅ À faire

```html
<!-- Bon : Utiliser gap (propre et moderne) -->
<div class="stack stack--md">
  <!-- Bon : Structurer logiquement -->
  <div class="stack">
    <header>...</header>
    <main>...</main>
    <footer>...</footer>
  </div>

  <!-- Bon : Combiner avec sémantique HTML -->
  <nav class="stack stack--horizontal"></nav>
</div>
```

### ❌ À éviter

```html
<!-- Mauvais : Trop de nesting -->
<div class="stack">
  <div class="stack">
    <div class="stack">
      <!-- Trop profond -->
    </div>
  </div>
</div>

<!-- Mauvais : Gap trop grand -->
<div class="stack" style="--gap: 10rem">
  <!-- Mauvais : Mixer stack avec margins manuelles -->
  <div class="stack">
    <div style="margin-bottom: 2rem"></div>
  </div>
</div>
```

## 🌐 Compatibilité navigateurs

| Navigateur | Version minimale | Support                     |
| ---------- | ---------------- | --------------------------- |
| Chrome     | 84+              | ✅ Complet (gap in flexbox) |
| Firefox    | 63+              | ✅ Complet                  |
| Safari     | 14.1+            | ✅ Complet                  |
| Edge       | 84+              | ✅ Complet                  |

**Note** : La propriété `gap` en Flexbox nécessite des versions récentes. Pour les anciens navigateurs, utilisez les marges.

## 🐛 Troubleshooting

### Problème : Gap ne fonctionne pas

**Solution** : Vérifiez la compatibilité navigateur

```scss
// Fallback pour anciens navigateurs
.stack {
  display: flex;
  flex-direction: column;
  gap: 1rem;

  // Fallback
  > * + * {
    margin-top: 1rem;
  }
}
```

### Problème : Divider mal aligné

**Solution** : Ajustez le padding-top

```scss
.stack--divider > * + * {
  padding-top: var(--stack-gap, 1rem);
}
```

### Problème : Alignement horizontal

**Solution** : Utilisez align-items

```html
<div class="stack stack--horizontal stack--center">Centré verticalement</div>
```

## 📦 Classes complètes disponibles

```scss
// Base
.stack {
  /* Vertical stack */
}

// Tailles
.stack--xs, .stack--sm, .stack--md
.stack--lg, .stack--xl, .stack--2xl

// Direction
.stack--horizontal {
  /* Horizontal */
}
.stack--horizontal-wrap {
  /* Wrap */
}
.stack--reverse {
  /* Reverse */
}

// Alignement
.stack--start, .stack--center, .stack--end
.stack--stretch, .stack--baseline

// Justification
.stack--justify-start, .stack--justify-center
.stack--justify-end, .stack--justify-between

// Divider
.stack--divider {
  /* Avec séparateur */
}
.stack--divider-thick {
  /* Séparateur épais */
}
.stack--divider-dark {
  /* Couleur foncée */
}

// Responsive
.stack--gap-mobile-sm {
  /* Gap mobile */
}
.stack--horizontal-tablet {
  /* Direction responsive */
}

// Utilitaires
.stack--full-height {
  /* 100% height */
}
.stack--stretch-children {
  /* Enfants flex: 1 */
}
```

## 🎓 Ressources complémentaires

- [CSS Gap - MDN](https://developer.mozilla.org/fr/docs/Web/CSS/gap)
- [Flexbox Guide - CSS Tricks](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
- [Every Layout - Stack](https://every-layout.dev/layouts/stack/)

## 📝 Changelog

- **v1.0** - Version initiale avec stack vertical
- **v1.1** - Ajout du stack horizontal
- **v1.2** - Système de dividers
- **v1.3** - Options d'alignement
- **v1.4** - Gaps responsive
- **v1.5** - Utilitaires avancés

---

**Made with ❤️ for better layouts**
