# Line Clamp

> Utilitaire CSS pour tronquer le texte sur plusieurs lignes avec ellipsis

## 📝 Description

Le `line-clamp` permet de limiter le texte à un nombre spécifique de lignes et d'ajouter automatiquement des points de suspension (...) à la fin. Parfait pour les cards, previews et listings.

## 🎯 Cas d'usage

- Cards avec descriptions limitées
- Previews d'articles
- Listings de produits
- Résultats de recherche
- Descriptions tronquées
- Aperçus de commentaires

## 💾 Installation

```scss
// _line-clamp.scss
.line-clamp {
  --lines: 3;

  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-line-clamp: var(--lines);
  overflow: hidden;
  text-overflow: ellipsis;
}

// Modificateurs prédéfinis
.line-clamp-1 {
  --lines: 1;
}
.line-clamp-2 {
  --lines: 2;
}
.line-clamp-3 {
  --lines: 3;
}
.line-clamp-4 {
  --lines: 4;
}
.line-clamp-5 {
  --lines: 5;
}
.line-clamp-6 {
  --lines: 6;
}

// Alternative moderne (support limité)
.line-clamp-modern {
  --lines: 3;

  display: -webkit-box;
  -webkit-box-orient: vertical;
  line-clamp: var(--lines);
  -webkit-line-clamp: var(--lines);
  overflow: hidden;
}
```

## 🚀 Utilisation de base

### Clamp personnalisé

```html
<p class="line-clamp" style="--lines: 3">
  Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor
  incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis
  nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.
  Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore
  eu fugiat nulla pariatur.
</p>
```

### Classes prédéfinies

```html
<!-- Tronquer sur 1 ligne -->
<h3 class="line-clamp-1">
  Titre très long qui sera tronqué sur une seule ligne
</h3>

<!-- Tronquer sur 2 lignes -->
<p class="line-clamp-2">
  Description de produit qui sera limitée à deux lignes maximum avec des points
  de suspension à la fin si le texte est trop long.
</p>

<!-- Tronquer sur 3 lignes -->
<p class="line-clamp-3">
  Aperçu d'article avec trois lignes maximum. Le texte supplémentaire sera caché
  et remplacé par des points de suspension. Très utile pour maintenir une mise
  en page cohérente dans des grilles de cards.
</p>
```

## ⚙️ Paramètres

| Variable CSS | Type      | Défaut | Description                                  |
| ------------ | --------- | ------ | -------------------------------------------- |
| `--lines`    | `integer` | `3`    | Nombre de lignes à afficher avant truncation |

### Classes prédéfinies

| Classe          | Lignes | Usage typique              |
| --------------- | ------ | -------------------------- |
| `.line-clamp-1` | 1      | Titres, labels             |
| `.line-clamp-2` | 2      | Courtes descriptions, tags |
| `.line-clamp-3` | 3      | Descriptions de cards      |
| `.line-clamp-4` | 4      | Previews d'articles        |
| `.line-clamp-5` | 5      | Extraits longs             |
| `.line-clamp-6` | 6      | Résumés étendus            |

## 📚 Exemples avancés

### Card produit avec line-clamp

```html
<article class="product-card">
  <img src="product.jpg" alt="Product" class="product-image" />
  <div class="product-content">
    <h3 class="product-title line-clamp-2">
      Nom du produit qui peut être très long et sur plusieurs lignes
    </h3>
    <p class="product-description line-clamp-3">
      Description détaillée du produit avec toutes les caractéristiques
      importantes. Cette description sera limitée à trois lignes pour maintenir
      une présentation cohérente dans la grille de produits.
    </p>
    <div class="product-footer">
      <span class="product-price">29,99 €</span>
      <button class="btn-add">Ajouter</button>
    </div>
  </div>
</article>

<style>
  .product-card {
    border: 1px solid #e5e7eb;
    border-radius: 0.5rem;
    overflow: hidden;
    transition: transform 0.3s, box-shadow 0.3s;
  }

  .product-card:hover {
    transform: translateY(-4px);
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  }

  .product-image {
    width: 100%;
    height: 200px;
    object-fit: cover;
  }

  .product-content {
    padding: 1.5rem;
  }

  .product-title {
    font-size: 1.25rem;
    font-weight: 600;
    margin-bottom: 0.75rem;
    color: #1f2937;
  }

  .product-description {
    color: #6b7280;
    line-height: 1.6;
    margin-bottom: 1rem;
  }

  .product-footer {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .product-price {
    font-size: 1.5rem;
    font-weight: 700;
    color: #3b82f6;
  }
</style>
```

### Liste d'articles avec preview

```html
<div class="article-list">
  <article class="article-item">
    <img src="thumb1.jpg" alt="Article" class="article-thumb" />
    <div class="article-info">
      <h3 class="article-title line-clamp-2">
        Titre de l'article qui peut être assez long
      </h3>
      <p class="article-excerpt line-clamp-3">
        Extrait de l'article qui donne un aperçu du contenu. Ce texte sera
        limité à trois lignes pour une présentation cohérente dans la liste des
        articles.
      </p>
      <div class="article-meta">
        <span class="article-date">26 nov 2025</span>
        <span class="article-reading-time">5 min</span>
      </div>
    </div>
  </article>

  <!-- Plus d'articles... -->
</div>

<style>
  .article-item {
    display: grid;
    grid-template-columns: 200px 1fr;
    gap: 1.5rem;
    padding: 1.5rem;
    border-bottom: 1px solid #e5e7eb;
    transition: background 0.2s;
  }

  .article-item:hover {
    background: #f9fafb;
  }

  .article-thumb {
    width: 100%;
    height: 150px;
    object-fit: cover;
    border-radius: 0.5rem;
  }

  .article-title {
    font-size: 1.25rem;
    font-weight: 600;
    margin-bottom: 0.5rem;
    color: #1f2937;
  }

  .article-excerpt {
    color: #6b7280;
    line-height: 1.6;
    margin-bottom: 1rem;
  }

  .article-meta {
    display: flex;
    gap: 1rem;
    font-size: 0.875rem;
    color: #9ca3af;
  }

  @media (max-width: 768px) {
    .article-item {
      grid-template-columns: 1fr;
    }
  }
</style>
```

### Grid de cards avec expand

```html
<div class="card-grid">
  <div class="card">
    <h3 class="card-title">Card Title</h3>
    <p class="card-text line-clamp-4" data-full-text="Texte complet ici...">
      Texte de la card qui sera tronqué sur 4 lignes. Cliquez sur 'Voir plus'
      pour afficher le texte complet. Lorem ipsum dolor sit amet, consectetur
      adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore
      magna aliqua.
    </p>
    <button class="expand-btn" onclick="toggleExpand(this)">Voir plus</button>
  </div>
</div>

<style>
  .card {
    padding: 1.5rem;
    border: 1px solid #e5e7eb;
    border-radius: 0.5rem;
    background: white;
  }

  .card-title {
    margin-bottom: 1rem;
    color: #1f2937;
  }

  .card-text {
    color: #6b7280;
    line-height: 1.6;
    margin-bottom: 1rem;
    transition: all 0.3s;
  }

  .card-text.expanded {
    display: block;
    -webkit-line-clamp: unset;
  }

  .expand-btn {
    background: none;
    border: none;
    color: #3b82f6;
    font-weight: 500;
    cursor: pointer;
    padding: 0;
  }

  .expand-btn:hover {
    text-decoration: underline;
  }
</style>

<script>
  function toggleExpand(btn) {
    const text = btn.previousElementSibling;
    const isExpanded = text.classList.contains("expanded");

    if (isExpanded) {
      text.classList.remove("expanded");
      btn.textContent = "Voir plus";
    } else {
      text.classList.add("expanded");
      btn.textContent = "Voir moins";
    }
  }
</script>
```

### Commentaires avec line-clamp

```html
<div class="comments">
  <div class="comment">
    <img src="avatar1.jpg" alt="User" class="comment-avatar" />
    <div class="comment-content">
      <div class="comment-header">
        <strong class="comment-author">John Doe</strong>
        <span class="comment-date">Il y a 2h</span>
      </div>
      <p class="comment-text line-clamp-3">
        Super article ! J'ai vraiment apprécié la partie sur les CSS custom
        properties. C'est exactement ce dont j'avais besoin pour mon projet.
        Merci pour ce partage de connaissances.
      </p>
      <div class="comment-actions">
        <button class="comment-like">👍 12</button>
        <button class="comment-reply">Répondre</button>
      </div>
    </div>
  </div>

  <!-- Plus de commentaires... -->
</div>

<style>
  .comment {
    display: flex;
    gap: 1rem;
    padding: 1rem;
    border-bottom: 1px solid #e5e7eb;
  }

  .comment-avatar {
    width: 48px;
    height: 48px;
    border-radius: 50%;
    object-fit: cover;
    flex-shrink: 0;
  }

  .comment-content {
    flex: 1;
    min-width: 0;
  }

  .comment-header {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    margin-bottom: 0.5rem;
  }

  .comment-author {
    color: #1f2937;
  }

  .comment-date {
    color: #9ca3af;
    font-size: 0.875rem;
  }

  .comment-text {
    color: #4b5563;
    line-height: 1.5;
    margin-bottom: 0.75rem;
  }

  .comment-actions {
    display: flex;
    gap: 1rem;
  }

  .comment-actions button {
    background: none;
    border: none;
    color: #6b7280;
    font-size: 0.875rem;
    cursor: pointer;
    padding: 0;
  }

  .comment-actions button:hover {
    color: #3b82f6;
  }
</style>
```

### Notification list avec truncate

```html
<div class="notification-list">
  <div class="notification unread">
    <div class="notification-icon">📧</div>
    <div class="notification-content">
      <p class="notification-title line-clamp-1">
        Nouveau message de Marie Dubois
      </p>
      <p class="notification-text line-clamp-2">
        Bonjour, j'ai regardé votre proposition et je suis très intéressée.
        Pouvons-nous en discuter cette semaine ?
      </p>
      <span class="notification-time">Il y a 5 min</span>
    </div>
  </div>

  <div class="notification">
    <div class="notification-icon">🔔</div>
    <div class="notification-content">
      <p class="notification-title line-clamp-1">
        Rappel: Réunion d'équipe demain à 10h
      </p>
      <p class="notification-text line-clamp-2">
        N'oubliez pas la réunion d'équipe prévue demain matin. Préparez vos
        rapports hebdomadaires.
      </p>
      <span class="notification-time">Il y a 2h</span>
    </div>
  </div>
</div>

<style>
  .notification {
    display: flex;
    gap: 1rem;
    padding: 1rem;
    border-bottom: 1px solid #e5e7eb;
    transition: background 0.2s;
    cursor: pointer;
  }

  .notification:hover {
    background: #f9fafb;
  }

  .notification.unread {
    background: #eff6ff;
  }

  .notification.unread:hover {
    background: #dbeafe;
  }

  .notification-icon {
    font-size: 1.5rem;
    flex-shrink: 0;
  }

  .notification-content {
    flex: 1;
    min-width: 0;
  }

  .notification-title {
    font-weight: 600;
    color: #1f2937;
    margin-bottom: 0.25rem;
  }

  .notification-text {
    color: #6b7280;
    font-size: 0.875rem;
    line-height: 1.4;
    margin-bottom: 0.5rem;
  }

  .notification-time {
    color: #9ca3af;
    font-size: 0.75rem;
  }
</style>
```

### Search results avec highlight

```html
<div class="search-results">
  <div class="result-item">
    <h3 class="result-title line-clamp-1">
      <mark>CSS</mark> Utilities Documentation - Line Clamp
    </h3>
    <p class="result-url">https://example.com/docs/line-clamp</p>
    <p class="result-excerpt line-clamp-2">
      Le line-clamp permet de limiter le texte à un nombre spécifique de lignes.
      Parfait pour les cards, previews avec <mark>CSS</mark>
      moderne et listings.
    </p>
  </div>

  <!-- Plus de résultats... -->
</div>

<style>
  .result-item {
    padding: 1rem 0;
    border-bottom: 1px solid #e5e7eb;
  }

  .result-title {
    color: #1a0dab;
    font-size: 1.25rem;
    margin-bottom: 0.25rem;
    cursor: pointer;
  }

  .result-title:hover {
    text-decoration: underline;
  }

  .result-url {
    color: #006621;
    font-size: 0.875rem;
    margin-bottom: 0.5rem;
  }

  .result-excerpt {
    color: #545454;
    line-height: 1.5;
  }

  mark {
    background: #fff2cc;
    padding: 0 2px;
    font-weight: 600;
  }
</style>
```

## 🎨 Personnalisation

### Avec animation au hover

```scss
.line-clamp-expandable {
  --lines: 3;

  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-line-clamp: var(--lines);
  overflow: hidden;
  transition: all 0.3s;
  cursor: pointer;

  &:hover {
    -webkit-line-clamp: unset;
    max-height: 500px;
  }
}
```

### Avec gradient fade

```scss
.line-clamp-fade {
  --lines: 3;

  position: relative;
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-line-clamp: var(--lines);
  overflow: hidden;

  &::after {
    content: "";
    position: absolute;
    bottom: 0;
    right: 0;
    width: 100%;
    height: 1.5em;
    background: linear-gradient(to bottom, transparent, white);
    pointer-events: none;
  }
}
```

### Responsive line-clamp

```scss
.line-clamp-responsive {
  --lines-mobile: 2;
  --lines-tablet: 3;
  --lines-desktop: 4;

  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-line-clamp: var(--lines-mobile);
  overflow: hidden;

  @media (min-width: 768px) {
    -webkit-line-clamp: var(--lines-tablet);
  }

  @media (min-width: 1024px) {
    -webkit-line-clamp: var(--lines-desktop);
  }
}
```

## 🔧 Compatibilité

| Navigateur | Version minimale | Notes                         |
| ---------- | ---------------- | ----------------------------- |
| Chrome     | 6+               | Support complet avec -webkit- |
| Firefox    | 68+              | Support complet               |
| Safari     | 5+               | Support complet avec -webkit- |
| Edge       | 17+              | Support complet               |

## ⚠️ Notes importantes

- **Direction du texte** : Fonctionne avec ltr et rtl
- **Box-orient** : Le préfixe -webkit- est nécessaire même en 2025
- **Display** : Doit être utilisé avec display: -webkit-box
- **Line-height** : Influence le nombre de lignes réelles affichées
- **Overflow** : Doit être hidden pour fonctionner

## 🎓 Bonnes pratiques

✅ **À faire**

- Toujours tester avec du contenu réel de longueurs variées
- Utiliser un line-height cohérent (1.5-1.7)
- Prévoir une option "Lire plus" si besoin
- Tester l'accessibilité avec les lecteurs d'écran
- Utiliser des couleurs de texte avec bon contraste

❌ **À éviter**

- Ne pas oublier le préfixe -webkit-
- Ne pas utiliser sur des éléments inline
- Ne pas mettre de padding excessif qui affecte le calcul
- Ne pas oublier overflow: hidden
- Ne pas négliger les cas où le texte est court

## 💡 Astuces JavaScript

### Toggle expand/collapse

```javascript
function setupLineClampToggle() {
  const clampedElements = document.querySelectorAll(".line-clamp-toggle");

  clampedElements.forEach((element) => {
    // Vérifier si le texte est tronqué
    const isOverflowing = element.scrollHeight > element.clientHeight;

    if (isOverflowing) {
      // Créer le bouton "Voir plus"
      const button = document.createElement("button");
      button.textContent = "Voir plus";
      button.className = "expand-button";
      element.parentNode.appendChild(button);

      button.addEventListener("click", () => {
        const isExpanded = element.classList.contains("expanded");

        if (isExpanded) {
          element.classList.remove("expanded");
          button.textContent = "Voir plus";
        } else {
          element.classList.add("expanded");
          button.textContent = "Voir moins";
        }
      });
    }
  });
}

// Initialiser au chargement
document.addEventListener("DOMContentLoaded", setupLineClampToggle);
```

---

[← Retour à la documentation](../README.md)
