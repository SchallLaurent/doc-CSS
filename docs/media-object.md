# Media Object Utility

> Pattern classique pour aligner une image/icône avec du contenu texte de manière flexible et responsive

## 📋 Description

**Media Object** est un pattern CSS fondamental qui permet d'afficher un élément média (image, icône, avatar) aligné à côté d'un bloc de contenu texte. Ce pattern est extrêmement courant dans les interfaces modernes : commentaires, notifications, listes de produits, cartes utilisateur, etc.

### ✨ Caractéristiques principales

- 🖼️ **Alignement flexible** : Image à gauche, à droite, ou centré verticalement
- 📐 **Taille personnalisable** : Contrôle précis de la largeur de la zone média
- 📱 **Responsive natif** : Empilage automatique sur mobile
- 🔧 **Variables CSS** : Personnalisation sans modification du code
- ⚡ **Performance** : CSS Grid natif, léger et rapide
- 🎨 **Gap variable** : Espacement ajustable entre média et contenu
- 🔄 **Ordre inversable** : Média à gauche ou à droite

## 🚀 Installation

### Code SCSS

```scss
// _media-object.scss
.media {
  // Variables par défaut
  --media-width: 100px; // Largeur de la zone média
  --gap: 1rem; // Espacement entre média et contenu
  --media-align: start; // Alignement vertical (start | center | end)
  --breakpoint: 480px; // Point de rupture responsive

  display: grid;
  grid-template-columns: var(--media-width) 1fr;
  gap: var(--gap);
  align-items: var(--media-align);

  // Mode responsive : empile sur mobile
  @media (max-width: var(--breakpoint)) {
    grid-template-columns: 1fr;
    text-align: center;

    .media__image {
      margin-inline: auto;
    }
  }
}

// Structure BEM
.media__image {
  width: 100%;
  height: auto;
  object-fit: cover;

  // Pour les avatars circulaires
  &--circle {
    border-radius: 50%;
    aspect-ratio: 1;
  }

  &--rounded {
    border-radius: 0.5rem;
  }
}

.media__content {
  min-width: 0; // Évite le débordement du texte
}

// Variantes prédéfinies
.media--small {
  --media-width: 60px;
  --gap: 0.75rem;
}

.media--large {
  --media-width: 150px;
  --gap: 1.5rem;
}

.media--reverse {
  grid-template-columns: 1fr var(--media-width);

  .media__image {
    order: 2;
  }

  .media__content {
    order: 1;
  }
}

.media--center {
  --media-align: center;
}

.media--stretch {
  --media-align: stretch;
}

// Avatar spécifique
.media--avatar {
  --media-width: 48px;

  .media__image {
    border-radius: 50%;
    aspect-ratio: 1;
  }
}

// Notification style
.media--notification {
  --media-width: 40px;
  --gap: 0.875rem;
  padding: 1rem;
  background: #f8f9fa;
  border-radius: 0.5rem;
  border-left: 3px solid var(--accent-color, #3b82f6);
}
```

### Import dans votre projet

```scss
// Dans styles.scss
@import "utilities/media-object";
```

## 💡 Utilisation de base

### Exemple 1 : Media Object simple

```html
<div class="media">
  <img class="media__image" src="avatar.jpg" alt="John Doe" />
  <div class="media__content">
    <h3>John Doe</h3>
    <p>Développeur Full Stack passionné par les technologies web modernes.</p>
  </div>
</div>
```

### Exemple 2 : Commentaire avec avatar

```html
<div class="media media--avatar">
  <img class="media__image media__image--circle" src="user.jpg" alt="User" />
  <div class="media__content">
    <strong>Marie Dupont</strong>
    <p>Excellent article ! J'ai beaucoup appris sur CSS Grid.</p>
    <time>Il y a 2 heures</time>
  </div>
</div>
```

### Exemple 3 : Notification

```html
<div class="media media--notification">
  <div class="media__image">
    <svg><!-- Icône --></svg>
  </div>
  <div class="media__content">
    <strong>Nouvelle notification</strong>
    <p>Votre commande a été expédiée</p>
  </div>
</div>
```

## 📊 Paramètres

| Variable        | Type    | Défaut  | Description                                       |
| --------------- | ------- | ------- | ------------------------------------------------- |
| `--media-width` | length  | `100px` | Largeur de la zone média                          |
| `--gap`         | length  | `1rem`  | Espacement entre média et contenu                 |
| `--media-align` | keyword | `start` | Alignement vertical (start, center, end, stretch) |
| `--breakpoint`  | length  | `480px` | Point de rupture pour mode mobile                 |

### Valeurs courantes pour `--media-width`

```css
/* Tailles prédéfinies */
--media-width: 40px; /* Icône/notification */
--media-width: 48px; /* Avatar petit */
--media-width: 60px; /* Avatar moyen */
--media-width: 80px; /* Avatar large */
--media-width: 100px; /* Image standard */
--media-width: 150px; /* Image large */
--media-width: 200px; /* Feature image */

/* Tailles responsives */
--media-width: clamp(60px, 10vw, 120px);

/* Auto-sizing */
--media-width: auto; /* S'adapte au contenu */
```

### Valeurs pour `--media-align`

```css
--media-align: start; /* Aligné en haut (défaut) */
--media-align: center; /* Centré verticalement */
--media-align: end; /* Aligné en bas */
--media-align: stretch; /* Étire sur toute la hauteur */
```

## 📚 Exemples détaillés

### Exemple 1 : Commentaires avec avatars

```html
<div class="comments-list">
  <article class="media media--avatar">
    <img
      class="media__image media__image--circle"
      src="user1.jpg"
      alt="Sophie"
    />
    <div class="media__content">
      <header>
        <strong>Sophie Martin</strong>
        <time datetime="2024-01-15">15 janvier 2024</time>
      </header>
      <p>
        Super tutoriel ! Les exemples sont très clairs et bien expliqués. J'ai
        pu mettre en pratique immédiatement.
      </p>
      <footer>
        <button>👍 12</button>
        <button>Répondre</button>
      </footer>
    </div>
  </article>

  <article class="media media--avatar" style="margin-left: 2rem;">
    <img
      class="media__image media__image--circle"
      src="user2.jpg"
      alt="Thomas"
    />
    <div class="media__content">
      <header>
        <strong>Thomas Leroux</strong>
        <time datetime="2024-01-15">15 janvier 2024</time>
      </header>
      <p>Merci Sophie ! Content que ça t'ait aidé 😊</p>
      <footer>
        <button>👍 5</button>
      </footer>
    </div>
  </article>
</div>

<style>
  .comments-list .media {
    padding: 1rem;
    border-bottom: 1px solid #e5e7eb;
  }

  .media__content header {
    display: flex;
    gap: 1rem;
    align-items: center;
    margin-bottom: 0.5rem;
  }

  .media__content time {
    color: #6b7280;
    font-size: 0.875rem;
  }

  .media__content footer {
    margin-top: 0.75rem;
    display: flex;
    gap: 1rem;
  }
</style>
```

### Exemple 2 : Liste de produits

```html
<div class="product-list">
  <article class="media media--large">
    <img
      class="media__image media__image--rounded"
      src="product1.jpg"
      alt="Product"
    />
    <div class="media__content">
      <h3>MacBook Pro M3</h3>
      <p class="price">2 499,00 €</p>
      <p class="description">
        Performances exceptionnelles avec la puce M3, écran Retina 14 pouces.
      </p>
      <div class="rating">⭐⭐⭐⭐⭐ <span>(128 avis)</span></div>
      <button class="btn-primary">Ajouter au panier</button>
    </div>
  </article>
</div>

<style>
  .product-list .media {
    padding: 1.5rem;
    background: white;
    border: 1px solid #e5e7eb;
    border-radius: 0.5rem;
    margin-bottom: 1rem;
  }

  .price {
    font-size: 1.5rem;
    font-weight: bold;
    color: #059669;
    margin: 0.5rem 0;
  }

  .description {
    color: #6b7280;
    margin-bottom: 0.75rem;
  }

  .rating {
    margin-bottom: 1rem;
  }
</style>
```

### Exemple 3 : Notifications système

```html
<div class="notifications">
  <!-- Success -->
  <div class="media media--notification" style="--accent-color: #10b981">
    <div class="media__image">
      <svg class="icon-success" width="24" height="24" fill="#10b981">
        <path d="M9 16.17L4.83 12l-1.42 1.41L9 19 21 7l-1.41-1.41z" />
      </svg>
    </div>
    <div class="media__content">
      <strong>Succès</strong>
      <p>Votre profil a été mis à jour avec succès</p>
    </div>
  </div>

  <!-- Warning -->
  <div class="media media--notification" style="--accent-color: #f59e0b">
    <div class="media__image">
      <svg class="icon-warning" width="24" height="24" fill="#f59e0b">
        <path d="M1 21h22L12 2 1 21zm12-3h-2v-2h2v2zm0-4h-2v-4h2v4z" />
      </svg>
    </div>
    <div class="media__content">
      <strong>Attention</strong>
      <p>Votre session expire dans 5 minutes</p>
    </div>
  </div>

  <!-- Error -->
  <div class="media media--notification" style="--accent-color: #ef4444">
    <div class="media__image">
      <svg class="icon-error" width="24" height="24" fill="#ef4444">
        <path
          d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm1 15h-2v-2h2v2zm0-4h-2V7h2v6z"
        />
      </svg>
    </div>
    <div class="media__content">
      <strong>Erreur</strong>
      <p>Impossible de se connecter au serveur</p>
    </div>
  </div>
</div>

<style>
  .notifications .media {
    margin-bottom: 1rem;
  }

  .media__content strong {
    display: block;
    margin-bottom: 0.25rem;
  }

  .media__content p {
    margin: 0;
    color: #6b7280;
    font-size: 0.875rem;
  }
</style>
```

### Exemple 4 : Team members

```html
<div class="team-grid">
  <div class="media media--center" style="--gap: 1.5rem">
    <img class="media__image media__image--circle" src="ceo.jpg" alt="CEO" />
    <div class="media__content">
      <h3>Jean Dupont</h3>
      <p class="role">CEO & Fondateur</p>
      <p class="bio">
        20 ans d'expérience dans le développement web et la gestion d'équipes
        techniques.
      </p>
      <div class="social-links">
        <a href="#">LinkedIn</a>
        <a href="#">Twitter</a>
      </div>
    </div>
  </div>

  <div class="media media--center" style="--gap: 1.5rem">
    <img class="media__image media__image--circle" src="cto.jpg" alt="CTO" />
    <div class="media__content">
      <h3>Marie Martin</h3>
      <p class="role">CTO</p>
      <p class="bio">
        Experte en architecture logicielle et innovation technologique.
      </p>
      <div class="social-links">
        <a href="#">LinkedIn</a>
        <a href="#">GitHub</a>
      </div>
    </div>
  </div>
</div>

<style>
  .team-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2rem;
  }

  .role {
    color: #6b7280;
    font-weight: 600;
    margin: 0.25rem 0;
  }

  .bio {
    margin: 0.75rem 0;
    line-height: 1.6;
  }

  .social-links {
    display: flex;
    gap: 0.5rem;
  }
</style>
```

### Exemple 5 : Message list (reverse)

```html
<div class="messages">
  <!-- Message reçu -->
  <div class="media media--avatar">
    <img
      class="media__image media__image--circle"
      src="sender.jpg"
      alt="Sender"
    />
    <div class="media__content">
      <div class="message-bubble message-bubble--received">
        <p>Salut ! Tu as vu le nouveau design ?</p>
        <time>10:32</time>
      </div>
    </div>
  </div>

  <!-- Message envoyé -->
  <div class="media media--avatar media--reverse">
    <img class="media__image media__image--circle" src="me.jpg" alt="Me" />
    <div class="media__content">
      <div class="message-bubble message-bubble--sent">
        <p>Oui, c'est super ! J'adore les nouvelles couleurs 🎨</p>
        <time>10:35</time>
      </div>
    </div>
  </div>
</div>

<style>
  .messages {
    max-width: 600px;
    margin: 0 auto;
  }

  .messages .media {
    margin-bottom: 1rem;
  }

  .message-bubble {
    padding: 0.75rem 1rem;
    border-radius: 1rem;
    max-width: 70%;
  }

  .message-bubble--received {
    background: #f3f4f6;
    border-bottom-left-radius: 0.25rem;
  }

  .message-bubble--sent {
    background: #3b82f6;
    color: white;
    margin-left: auto;
    border-bottom-right-radius: 0.25rem;
  }

  .message-bubble time {
    font-size: 0.75rem;
    opacity: 0.7;
    display: block;
    margin-top: 0.25rem;
  }
</style>
```

## 🎨 Personnalisation avancée

### Media avec taille responsive

```html
<div class="media" style="--media-width: clamp(60px, 10vw, 120px)">
  <img class="media__image" src="image.jpg" alt="Image" />
  <div class="media__content">
    <h3>Titre responsive</h3>
    <p>L'image s'adapte à la taille de l'écran</p>
  </div>
</div>
```

### Gap variable selon le breakpoint

```scss
.media {
  --gap: clamp(0.75rem, 2vw, 1.5rem);
}
```

### Media avec actions

```html
<div class="media media--avatar">
  <img class="media__image media__image--circle" src="user.jpg" alt="User" />
  <div class="media__content">
    <div class="media-header">
      <div>
        <strong>Jean Martin</strong>
        <p>Développeur Frontend</p>
      </div>
      <div class="media-actions">
        <button>✉️</button>
        <button>📞</button>
        <button>⋯</button>
      </div>
    </div>
  </div>
</div>

<style>
  .media-header {
    display: flex;
    justify-content: space-between;
    align-items: start;
  }

  .media-actions {
    display: flex;
    gap: 0.5rem;
  }
</style>
```

### Media avec badge

```html
<div class="media media--avatar">
  <div class="media__image-wrapper">
    <img class="media__image media__image--circle" src="user.jpg" alt="User" />
    <span class="status-badge status-badge--online"></span>
  </div>
  <div class="media__content">
    <strong>Marie Dubois</strong>
    <p>En ligne</p>
  </div>
</div>

<style>
  .media__image-wrapper {
    position: relative;
  }

  .status-badge {
    position: absolute;
    bottom: 0;
    right: 0;
    width: 12px;
    height: 12px;
    border-radius: 50%;
    border: 2px solid white;
  }

  .status-badge--online {
    background: #10b981;
  }
</style>
```

## 🎯 Cas d'usage courants

### 1. Commentaires de blog

```html
<div class="media media--avatar">
  <img class="media__image media__image--circle" src="avatar.jpg" alt="User" />
  <div class="media__content">
    <strong>Username</strong> • <time>Il y a 2h</time>
    <p>Commentaire...</p>
  </div>
</div>
```

### 2. Cartes de profil

```html
<div class="media media--center" style="--media-width: 80px">
  <img
    class="media__image media__image--circle"
    src="profile.jpg"
    alt="Profile"
  />
  <div class="media__content">
    <h3>Nom Prénom</h3>
    <p>Titre professionnel</p>
  </div>
</div>
```

### 3. Notifications

```html
<div class="media media--notification">
  <div class="media__image">🔔</div>
  <div class="media__content">
    <strong>Notification</strong>
    <p>Message de notification</p>
  </div>
</div>
```

### 4. Liste de contacts

```html
<div class="media media--small">
  <img
    class="media__image media__image--circle"
    src="contact.jpg"
    alt="Contact"
  />
  <div class="media__content">
    <strong>Nom du contact</strong>
    <p>En ligne</p>
  </div>
</div>
```

### 5. Features list

```html
<div class="media" style="--media-width: 64px">
  <div class="media__image">
    <svg><!-- Icône --></svg>
  </div>
  <div class="media__content">
    <h4>Titre de la fonctionnalité</h4>
    <p>Description détaillée...</p>
  </div>
</div>
```

## 🔧 Combinaison avec autres utilitaires

### Media Object dans une Grid

```html
<div class="grid-wrapper" style="--cols: 2">
  <div class="media media--avatar">
    <img
      class="media__image media__image--circle"
      src="user1.jpg"
      alt="User 1"
    />
    <div class="media__content">
      <h3>User 1</h3>
      <p>Description</p>
    </div>
  </div>

  <div class="media media--avatar">
    <img
      class="media__image media__image--circle"
      src="user2.jpg"
      alt="User 2"
    />
    <div class="media__content">
      <h3>User 2</h3>
      <p>Description</p>
    </div>
  </div>
</div>
```

### Media Object avec Card

```html
<div class="card">
  <div class="media media--avatar">
    <img
      class="media__image media__image--circle"
      src="author.jpg"
      alt="Author"
    />
    <div class="media__content">
      <strong>Auteur</strong>
      <p>Article publié le 15 janvier 2024</p>
    </div>
  </div>
  <hr />
  <p>Contenu de l'article...</p>
</div>
```

## 📱 Comportement responsive

| Viewport    | Comportement                                     |
| ----------- | ------------------------------------------------ |
| > 480px     | Affichage en ligne (média + contenu côte à côte) |
| ≤ 480px     | Empilage vertical (média au-dessus du contenu)   |
| Mode mobile | Centrage automatique du média                    |

### Désactiver le responsive

```scss
.media--no-stack {
  @media (max-width: 480px) {
    grid-template-columns: var(--media-width) 1fr !important;
  }
}
```

### Breakpoint personnalisé

```html
<!-- Empile à 640px au lieu de 480px -->
<div class="media" style="--breakpoint: 640px">
  <img class="media__image" src="image.jpg" alt="Image" />
  <div class="media__content">Content</div>
</div>
```

## ⚡ Performance & Bonnes pratiques

### ✅ À faire

```html
<!-- Bon : Images optimisées -->
<img class="media__image" src="avatar-thumb.jpg" alt="User" loading="lazy" />

<!-- Bon : Taille appropriée -->
<div class="media" style="--media-width: 48px">
  <!-- Bon : min-width: 0 pour éviter overflow -->
  <div class="media__content" style="min-width: 0">
    <p>Texte très long qui pourrait déborder...</p>
  </div>
</div>
```

### ❌ À éviter

```html
<!-- Mauvais : Image trop large non optimisée -->
<img class="media__image" src="full-size-4k.jpg" alt="Image" />

<!-- Mauvais : Taille média trop grande -->
<div class="media" style="--media-width: 400px">
  <!-- Mauvais : Pas de alt sur les images -->
  <img class="media__image" src="avatar.jpg" />
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
.media {
  // Fallback Flexbox
  display: flex;
  gap: var(--gap, 1rem);

  .media__image {
    width: var(--media-width, 100px);
    flex-shrink: 0;
  }

  .media__content {
    flex: 1;
    min-width: 0;
  }

  // Grid prend le relais si supporté
  @supports (display: grid) {
    display: grid;
    grid-template-columns: var(--media-width) 1fr;
  }
}
```

## 🐛 Troubleshooting

### Problème : Le texte déborde

**Solution** : Ajoutez `min-width: 0` sur `.media__content`

```scss
.media__content {
  min-width: 0; // Permet au contenu de se réduire
  overflow-wrap: break-word; // Coupe les mots longs
}
```

### Problème : L'image ne garde pas son ratio

**Solution** : Utilisez `aspect-ratio` ou `object-fit`

```scss
.media__image {
  aspect-ratio: 1; // Force un carré
  object-fit: cover; // Recadre l'image
}
```

### Problème : Gap ne fonctionne pas

**Solution** : Vérifiez le support ou utilisez margin

```scss
.media {
  gap: var(--gap);

  // Fallback
  @supports not (gap: 1rem) {
    .media__content {
      margin-left: var(--gap);
    }
  }
}
```

## 📦 Variantes complètes

```scss
// Classes disponibles
.media {
  /* Base */
}
.media--small {
  --media-width: 60px;
  --gap: 0.75rem;
}
.media--large {
  --media-width: 150px;
  --gap: 1.5rem;
}
.media--reverse {
  /* Média à droite */
}
.media--center {
  --media-align: center;
}
.media--stretch {
  --media-align: stretch;
}
.media--avatar {
  --media-width: 48px;
}
.media--notification {
  /* Style notification */
}

// Modificateurs d'image
.media__image--circle {
  border-radius: 50%;
  aspect-ratio: 1;
}
.media__image--rounded {
  border-radius: 0.5rem;
}
```

## 🎓 Ressources complémentaires

- [Media Object - Every Layout](https://every-layout.dev/layouts/sidebar/)
- [CSS Grid Layout - MDN](https://developer.mozilla.org/fr/docs/Web/CSS/CSS_Grid_Layout)
- [The Media Object - Nicole Sullivan](http://www.stubbornella.org/content/2010/06/25/the-media-object-saves-hundreds-of-lines-of-code/)

## 📝 Changelog

- **v1.0** - Version initiale du Media Object
- **v1.1** - Ajout des variantes prédéfinies (small, large, avatar)
- **v1.2** - Support du mode reverse (média à droite)
- **v1.3** - Amélioration du responsive avec breakpoint personnalisable
- **v1.4** - Ajout du style notification

---

**Made with ❤️ for clean layouts**
