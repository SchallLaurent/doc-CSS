## @Input - Données du parent vers l'enfant

Le décorateur `@Input()` permet à un composant enfant de recevoir des données depuis son parent.

### Utilisation basique

**Composant enfant :**

```typescript
import { Component, Input } from "@angular/core";

@Component({
  selector: "app-user-card",
  template: `
    <div class="card">
      <h3>{{ userName }}</h3>
      <p>Age: {{ userAge }} ans</p>
    </div>
  `,
})
export class UserCardComponent {
  @Input() userName: string = "";
  @Input() userAge: number = 0;
}
```

**Composant parent :**

```typescript
@Component({
  selector: "app-parent",
  template: `
    <app-user-card [userName]="currentUser" [userAge]="currentAge">
    </app-user-card>
  `,
})
export class ParentComponent {
  currentUser = "Laurent";
  currentAge = 30;
}
```

### @Input avec valeurs par défaut

```typescript
export class ButtonComponent {
  @Input() label: string = "Cliquez-moi";
  @Input() disabled: boolean = false;
  @Input() color: "primary" | "secondary" | "danger" = "primary";
  @Input() size: "small" | "medium" | "large" = "medium";
}
```

**Utilisation :**

```html
<!-- Avec valeurs personnalisées -->
<app-button label="Enregistrer" color="primary" size="large"> </app-button>

<!-- Avec valeurs par défaut -->
<app-button></app-button>
```

### @Input avec objets et tableaux

```typescript
// Interfaces
interface User {
  id: number;
  name: string;
  email: string;
  avatar?: string;
}

interface Product {
  id: number;
  name: string;
  price: number;
}

// Composant enfant
@Component({
  selector: "app-user-profile",
  template: `
    <div class="profile">
      <img [src]="user.avatar || 'default.png'" [alt]="user.name" />
      <h2>{{ user.name }}</h2>
      <p>{{ user.email }}</p>
    </div>
  `,
})
export class UserProfileComponent {
  @Input() user!: User; // ! = requis, doit être fourni
}

// Composant avec tableau
@Component({
  selector: "app-product-list",
  template: `
    <div class="product-list">
      <div *ngFor="let product of products" class="product-item">
        <h3>{{ product.name }}</h3>
        <p>{{ product.price }}€</p>
      </div>
    </div>
  `,
})
export class ProductListComponent {
  @Input() products: Product[] = [];
}
```

**Utilisation dans le parent :**

```typescript
@Component({
  selector: "app-parent",
  template: `
    <app-user-profile [user]="currentUser"></app-user-profile>
    <app-product-list [products]="productList"></app-product-list>
  `,
})
export class ParentComponent {
  currentUser: User = {
    id: 1,
    name: "Laurent",
    email: "laurent@example.com",
    avatar: "avatar.jpg",
  };

  productList: Product[] = [
    { id: 1, name: "Laptop", price: 999 },
    { id: 2, name: "Mouse", price: 29 },
  ];
}
```

### @Input requis (Angular 16+)

```typescript
import { Component, Input } from "@angular/core";

export class ProductComponent {
  // Obligatoire - génère une erreur si non fourni
  @Input({ required: true }) productId!: number;
  @Input({ required: true }) productName!: string;

  // Optionnel avec valeur par défaut
  @Input() quantity: number = 1;
}
```

### @Input avec transformation (Angular 16+)

```typescript
import {
  Component,
  Input,
  booleanAttribute,
  numberAttribute,
} from "@angular/core";

export class ToggleComponent {
  // Convertit automatiquement en boolean
  @Input({ transform: booleanAttribute }) disabled: boolean = false;

  // Convertit automatiquement en number
  @Input({ transform: numberAttribute }) count: number = 0;
}
```

**Utilisation :**

```html
<!-- Avant : devait écrire [disabled]="true" -->
<app-toggle disabled></app-toggle>

<!-- Les deux fonctionnent maintenant -->
<app-toggle [disabled]="true"></app-toggle>
<app-toggle disabled></app-toggle>
```

### @Input avec types complexes

```typescript
// Type union
export class AlertComponent {
  @Input() type: "success" | "warning" | "error" | "info" = "info";
}

// Type générique
export class DataTableComponent<T> {
  @Input() data: T[] = [];
  @Input() columns: TableColumn<T>[] = [];
}

// Type nullable
export class ImageComponent {
  @Input() src: string | null = null;
  @Input() fallbackSrc: string = "placeholder.png";
}
```
