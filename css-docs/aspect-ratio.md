# Aspect Ratio Wrapper

> Utilitaire CSS pour maintenir un ratio d'aspect spécifique sur n'importe quel élément

## 📝 Description

Le `aspect-ratio` wrapper permet de contrôler facilement le ratio largeur/hauteur d'un élément. Idéal pour les images, vidéos, iframes et cards qui doivent maintenir des proportions spécifiques tout en restant responsives.

## 🎯 Cas d'usage

- Galeries d'images avec proportions cohérentes
- Lecteurs vidéo responsives (YouTube, Vimeo)
- Cards avec thumbnails uniformes
- Placeholder d'images lors du chargement
- Composants avec dimensions prévisibles

## 💾 Installation

```scss
// _aspect-ratio.scss
.aspect-ratio {
  --ratio: 16/9;
  aspect-ratio: var(--ratio);
  width: 100%;
  position: relative;
  overflow: hidden;
}

// Ratios prédéfinis
.aspect-ratio--square {
  --ratio: 1/1;
}
.aspect-ratio--video {
  --ratio: 16/9;
}
.aspect-ratio--classic {
  --ratio: 4/3;
}
.aspect-ratio--wide {
  --ratio: 21/9;
}
.aspect-ratio--portrait {
  --ratio: 3/4;
}
.aspect-ratio--golden {
  --ratio: 1.618/1;
}
```

## 🚀 Utilisation de base

### Ratio personnalisé

```html
<!-- Ratio 16:9 (vidéo) -->
<div class="aspect-ratio" style="--ratio: 16/9">
  <img src="image.jpg" alt="Image 16:9" />
</div>

<!-- Ratio 1:1 (carré) -->
<div class="aspect-ratio" style="--ratio: 1/1">
  <img src="profile.jpg" alt="Photo de profil" />
</div>

<!-- Ratio 4:3 (classique) -->
<div class="aspect-ratio" style="--ratio: 4/3">
  <iframe src="https://youtube.com/embed/..."></iframe>
</div>
```

### Classes prédéfinies

```html
<!-- Carré -->
<div class="aspect-ratio aspect-ratio--square">
  <img src="thumb.jpg" alt="Thumbnail" />
</div>

<!-- Format vidéo -->
<div class="aspect-ratio aspect-ratio--video">
  <video controls>
    <source src="video.mp4" type="video/mp4" />
  </video>
</div>

<!-- Golden ratio -->
<div class="aspect-ratio aspect-ratio--golden">
  <div class="card-content">
    <h3>Card avec ratio d'or</h3>
    <p>Contenu esthétiquement plaisant</p>
  </div>
</div>
```

## ⚙️ Paramètres

| Variable CSS | Type            | Défaut | Description                                |
| ------------ | --------------- | ------ | ------------------------------------------ |
| `--ratio`    | `number/number` | `16/9` | Ratio largeur/hauteur (ex: 16/9, 4/3, 1/1) |

### Classes modificatrices

| Classe                    | Ratio   | Usage typique                        |
| ------------------------- | ------- | ------------------------------------ |
| `.aspect-ratio--square`   | 1:1     | Photos de profil, icônes, thumbnails |
| `.aspect-ratio--video`    | 16:9    | Vidéos YouTube/Vimeo, contenu HD     |
| `.aspect-ratio--classic`  | 4:3     | Photos classiques, présentations     |
| `.aspect-ratio--wide`     | 21:9    | Bannières, headers panoramiques      |
| `.aspect-ratio--portrait` | 3:4     | Stories Instagram, mobile            |
| `.aspect-ratio--golden`   | 1.618:1 | Designs esthétiques, hero sections   |

## 📚 Exemples avancés

### Galerie d'images uniforme

```html
<div class="gallery">
  <div class="aspect-ratio aspect-ratio--square">
    <img src="photo1.jpg" alt="Photo 1" />
  </div>
  <div class="aspect-ratio aspect-ratio--square">
    <img src="photo2.jpg" alt="Photo 2" />
  </div>
  <div class="aspect-ratio aspect-ratio--square">
    <img src="photo3.jpg" alt="Photo 3" />
  </div>
</div>

<style>
  .gallery {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    gap: 1rem;
  }

  .aspect-ratio img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
</style>
```

### Embed vidéo responsive

```html
<div class="video-container">
  <div class="aspect-ratio aspect-ratio--video">
    <iframe
      src="https://www.youtube.com/embed/dQw4w9WgXcQ"
      frameborder="0"
      allowfullscreen
    >
    </iframe>
  </div>
</div>

<style>
  .aspect-ratio iframe {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
  }
</style>
```

### Cards avec ratio personnalisé

```html
<article class="card">
  <div class="aspect-ratio" style="--ratio: 3/2">
    <img src="article-cover.jpg" alt="Cover" />
  </div>
  <div class="card-body">
    <h2>Titre de l'article</h2>
    <p>Description courte...</p>
  </div>
</article>

<style>
  .card {
    border-radius: 0.5rem;
    overflow: hidden;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
  }

  .aspect-ratio img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transition: transform 0.3s;
  }

  .card:hover .aspect-ratio img {
    transform: scale(1.05);
  }
</style>
```

## 🎨 Personnalisation

### Créer vos propres ratios

```scss
// Dans votre SCSS
.aspect-ratio--instagram-post {
  --ratio: 1/1;
}
.aspect-ratio--instagram-story {
  --ratio: 9/16;
}
.aspect-ratio--twitter-card {
  --ratio: 2/1;
}
.aspect-ratio--facebook-cover {
  --ratio: 205/78;
}
.aspect-ratio--linkedin-banner {
  --ratio: 4/1;
}
```

### Combiner avec object-fit

```scss
.aspect-ratio {
  --ratio: 16/9;
  --object-fit: cover; // cover, contain, fill, none

  aspect-ratio: var(--ratio);

  img,
  video {
    width: 100%;
    height: 100%;
    object-fit: var(--object-fit);
  }
}
```

## 🔧 Compatibilité

| Navigateur | Version minimale | Notes                 |
| ---------- | ---------------- | --------------------- |
| Chrome     | 88+              | Support natif complet |
| Firefox    | 89+              | Support natif complet |
| Safari     | 15+              | Support natif complet |
| Edge       | 88+              | Support natif complet |

## ⚠️ Notes importantes

- **Performance** : L'utilisation de `aspect-ratio` évite le Cumulative Layout Shift (CLS)
- **Images** : Ajoutez toujours `width` et `height` dans le HTML pour un meilleur SEO
- **Object-fit** : Combinez avec `object-fit` pour contrôler le comportement de l'image
- **Accessibilité** : N'oubliez pas les attributs `alt` sur les images

## 🎓 Bonnes pratiques

✅ **À faire**

- Utiliser pour tous les medias (images, vidéos, iframes)
- Combiner avec lazy loading pour les performances
- Définir des ratios cohérents dans votre design system
- Ajouter des transitions pour les effets hover

❌ **À éviter**

- Ne pas utiliser de ratios trop extrêmes (1/20, 20/1)
- Ne pas oublier l'overflow hidden si besoin
- Ne pas négliger les attributs width/height dans le HTML

---

[← Retour à la documentation](../README.md)
