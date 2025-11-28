## Getters et Setters avec @Input

Les getters et setters permettent d'exécuter du code quand un @Input change.

### Setter basique

```typescript
@Component({
  selector: "app-user-avatar",
  template: ` <img [src]="imageSrc" [alt]="userName" /> `,
})
export class UserAvatarComponent {
  imageSrc: string = "default.png";

  private _userName: string = "";

  @Input()
  set userName(name: string) {
    this._userName = name;
    // Logique additionnelle lors du changement
    console.log("Nouveau nom:", name);
    this.updateAvatar(name);
  }

  get userName(): string {
    return this._userName;
  }

  private updateAvatar(name: string): void {
    // Générer une URL d'avatar basée sur le nom
    this.imageSrc = `https://ui-avatars.com/api/?name=${encodeURIComponent(
      name
    )}`;
  }
}
```

### Validation avec setter

```typescript
@Component({
  selector: "app-progress-bar",
  template: `
    <div class="progress-bar">
      <div class="progress-fill" [style.width.%]="validatedProgress"></div>
      <span>{{ validatedProgress }}%</span>
    </div>
  `,
})
export class ProgressBarComponent {
  private _progress: number = 0;
  validatedProgress: number = 0;

  @Input()
  set progress(value: number) {
    this._progress = value;
    // Valider et contraindre la valeur entre 0 et 100
    this.validatedProgress = Math.max(0, Math.min(100, value));

    if (value < 0 || value > 100) {
      console.warn(
        `Progress invalide: ${value}. Contraint à ${this.validatedProgress}`
      );
    }
  }

  get progress(): number {
    return this._progress;
  }
}
```

### Transformation de données avec setter

```typescript
@Component({
  selector: "app-temperature-display",
  template: `
    <div>
      <p>{{ celsius }}°C</p>
      <p>{{ fahrenheit }}°F</p>
      <p>{{ kelvin }}K</p>
    </div>
  `,
})
export class TemperatureDisplayComponent {
  celsius: number = 0;
  fahrenheit: number = 0;
  kelvin: number = 0;

  @Input()
  set temperature(value: number) {
    this.celsius = value;
    // Calculer automatiquement les autres unités
    this.fahrenheit = (value * 9) / 5 + 32;
    this.kelvin = value + 273.15;
  }
}
```

### Déclenchement d'actions avec setter

```typescript
interface Product {
  id: number;
  name: string;
  categoryId: number;
}

@Component({
  selector: "app-product-detail",
  template: `
    <div *ngIf="product">
      <h2>{{ product.name }}</h2>
      <div *ngIf="relatedProducts.length">
        <h3>Produits similaires</h3>
        <ul>
          <li *ngFor="let p of relatedProducts">{{ p.name }}</li>
        </ul>
      </div>
    </div>
  `,
})
export class ProductDetailComponent {
  private _product!: Product;
  relatedProducts: Product[] = [];

  @Input()
  set product(value: Product) {
    this._product = value;
    // Charger automatiquement les produits similaires
    if (value) {
      this.loadRelatedProducts(value.categoryId);
    }
  }

  get product(): Product {
    return this._product;
  }

  constructor(private productService: ProductService) {}

  private loadRelatedProducts(categoryId: number): void {
    this.productService.getByCategory(categoryId).subscribe((products) => {
      this.relatedProducts = products.filter((p) => p.id !== this.product.id);
    });
  }
}
```
