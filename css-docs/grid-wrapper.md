# Grid Wrapper - Documentation

## Description

Classe CSS utilitaire pour créer des grids flexibles avec un nombre de colonnes personnalisable et des tailles de colonnes ajustables via des variables CSS.

## Installation

Ajouter le code suivant dans votre fichier SCSS global (ex: `styles.scss`) :

```scss
.grid-wrapper {
  display: grid;
  grid-template-columns: var(--grid-template, repeat(var(--cols, 2), 1fr));
  grid-auto-rows: auto;
  text-align: right;
}
```

## Utilisation

### Mode Simple - Colonnes égales

Utiliser la variable `--cols` pour définir un nombre de colonnes de taille égale.

**Syntaxe :**

```html
<div class="grid-wrapper" style="--cols: [nombre]">
  <!-- Votre contenu -->
</div>
```

**Exemples :**

```html
<!-- 2 colonnes égales (défaut) -->
<div class="grid-wrapper">
  <div>Item 1</div>
  <div>Item 2</div>
</div>

<!-- 3 colonnes égales -->
<div class="grid-wrapper" style="--cols: 3">
  <div>Item 1</div>
  <div>Item 2</div>
  <div>Item 3</div>
</div>

<!-- 4 colonnes égales -->
<div class="grid-wrapper" style="--cols: 4">
  <div>Item 1</div>
  <div>Item 2</div>
  <div>Item 3</div>
  <div>Item 4</div>
</div>
```

### Mode Avancé - Colonnes personnalisées

Utiliser la variable `--grid-template` pour définir des tailles de colonnes personnalisées.

**Syntaxe :**

```html
<div
  class="grid-wrapper"
  style="--grid-template: [valeur1] [valeur2] [valeur3]"
>
  <!-- Votre contenu -->
</div>
```

**Exemples :**

**Colonnes avec tailles fixes :**

```html
<!-- 200px fixe + 2 colonnes flexibles -->
<div class="grid-wrapper" style="--grid-template: 200px 1fr 1fr">
  <div>Sidebar fixe</div>
  <div>Contenu flexible</div>
  <div>Aside flexible</div>
</div>
```

**Colonnes avec ratios différents :**

```html
<!-- Colonne du milieu 2x plus large -->
<div class="grid-wrapper" style="--grid-template: 1fr 2fr 1fr">
  <div>Petite (1 part)</div>
  <div>Grande (2 parts)</div>
  <div>Petite (1 part)</div>
</div>

<!-- 3 colonnes avec ratios 1:3:2 -->
<div class="grid-wrapper" style="--grid-template: 1fr 3fr 2fr">
  <div>1 part</div>
  <div>3 parts</div>
  <div>2 parts</div>
</div>
```

**Mix de px, fr et auto :**

```html
<!-- Auto + Flexible + Fixe -->
<div class="grid-wrapper" style="--grid-template: auto 1fr 200px">
  <div>S'adapte au contenu</div>
  <div>Prend l'espace restant</div>
  <div>Fixe à 200px</div>
</div>
```

**Avec minmax (taille min/max) :**

```html
<!-- Minimum 200px, maximum flexible -->
<div class="grid-wrapper" style="--grid-template: minmax(200px, 1fr) 2fr">
  <div>Min 200px, max flexible</div>
  <div>2x plus large</div>
</div>

<!-- Sidebar responsive -->
<div class="grid-wrapper" style="--grid-template: minmax(250px, 300px) 1fr">
  <div>Sidebar 250-300px</div>
  <div>Contenu principal</div>
</div>
```

**Avec repeat() dans le template personnalisé :**

```html
<!-- 4 colonnes égales via template -->
<div class="grid-wrapper" style="--grid-template: repeat(4, 1fr)">
  <div>Item 1</div>
  <div>Item 2</div>
  <div>Item 3</div>
  <div>Item 4</div>
</div>

<!-- Pattern répété: fixe + flexible -->
<div class="grid-wrapper" style="--grid-template: repeat(3, 100px 1fr)">
  <!-- Crée: 100px 1fr 100px 1fr 100px 1fr -->
</div>
```

## Paramètres

| Variable          | Type   | Défaut                        | Description                                     |
| ----------------- | ------ | ----------------------------- | ----------------------------------------------- |
| `--cols`          | number | 2                             | Nombre de colonnes égales (mode simple)         |
| `--grid-template` | string | `repeat(var(--cols, 2), 1fr)` | Template de colonnes personnalisé (mode avancé) |

## Unités disponibles

| Unité              | Description                     | Exemple              |
| ------------------ | ------------------------------- | -------------------- |
| `fr`               | Fraction de l'espace disponible | `1fr 2fr`            |
| `px`               | Pixels fixes                    | `200px`              |
| `%`                | Pourcentage du conteneur        | `50%`                |
| `auto`             | S'adapte au contenu             | `auto`               |
| `minmax(min, max)` | Taille entre min et max         | `minmax(200px, 1fr)` |
| `min-content`      | Taille minimale du contenu      | `min-content`        |
| `max-content`      | Taille maximale du contenu      | `max-content`        |

## Propriétés CSS appliquées

- `display: grid` - Active le mode grid
- `grid-template-columns` - Définit la structure des colonnes
- `grid-auto-rows: auto` - Les lignes s'adaptent au contenu
- `text-align: right` - Aligne le texte à droite

## Cas d'usage courants

### Layout 2 colonnes : Sidebar + Contenu

```html
<div class="grid-wrapper" style="--grid-template: 250px 1fr">
  <aside>Navigation</aside>
  <main>Contenu principal</main>
</div>
```

### Layout 3 colonnes : Sidebar + Contenu + Aside

```html
<div class="grid-wrapper" style="--grid-template: 200px 1fr 300px">
  <aside>Menu</aside>
  <main>Contenu</main>
  <aside>Publicités</aside>
</div>
```

### Layout responsive avec minmax

```html
<div
  class="grid-wrapper"
  style="--grid-template: repeat(auto-fit, minmax(250px, 1fr))"
>
  <!-- Les colonnes s'adaptent automatiquement à l'écran -->
  <div>Card 1</div>
  <div>Card 2</div>
  <div>Card 3</div>
</div>
```

### Dashboard avec ratios

```html
<div class="grid-wrapper" style="--grid-template: 2fr 1fr">
  <div>Graphique principal (2/3)</div>
  <div>Stats secondaires (1/3)</div>
</div>
```

## Personnalisation

### Ajouter un espacement (gap)

```scss
.grid-wrapper {
  display: grid;
  grid-template-columns: var(--grid-template, repeat(var(--cols, 2), 1fr));
  grid-auto-rows: auto;
  text-align: right;
  gap: 16px; // Espacement entre les items
}
```

### Avec gap variable

```scss
.grid-wrapper {
  display: grid;
  grid-template-columns: var(--grid-template, repeat(var(--cols, 2), 1fr));
  grid-auto-rows: auto;
  text-align: right;
  gap: var(--gap, 16px); // Gap personnalisable
}
```

```html
<div class="grid-wrapper" style="--cols: 3; --gap: 24px">
  <!-- Grid 3 colonnes avec gap de 24px -->
</div>
```

### Modifier l'alignement du texte

```html
<div class="grid-wrapper" style="--cols: 3; text-align: left">
  <!-- Texte aligné à gauche -->
</div>
```

## Compatibilité

- ✅ Chrome/Edge 57+
- ✅ Firefox 52+
- ✅ Safari 10.1+
- ✅ Angular, React, Vue, HTML/CSS pur

## Notes

- La variable `--grid-template` a la priorité sur `--cols`
- Si aucune variable n'est définie, le grid aura 2 colonnes égales par défaut
- Aucun JavaScript requis
- Compatible avec les media queries CSS

## Exemples avancés

### Combinaison avec media queries

```scss
.grid-wrapper {
  display: grid;
  grid-template-columns: var(--grid-template, repeat(var(--cols, 2), 1fr));
  grid-auto-rows: auto;
  text-align: right;
  gap: 16px;

  @media (max-width: 768px) {
    grid-template-columns: 1fr; // Force 1 colonne sur mobile
  }
}
```

### Grids imbriqués

```html
<div class="grid-wrapper" style="--cols: 2">
  <div class="grid-wrapper" style="--cols: 2">
    <!-- Grid 2x2 imbriqué -->
    <div>A</div>
    <div>B</div>
  </div>
  <div>Item 2</div>
</div>
```

[← Retour à la documentation](../README.md)
