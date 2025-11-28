## ngOnChanges

### Définition

`ngOnChanges` est appelé **à chaque fois** qu'une ou plusieurs propriétés `@Input()` changent. Il est appelé **avant** `ngOnInit` lors de la première initialisation.

### Import et implémentation

```typescript
import { Component, OnChanges, SimpleChanges, Input } from "@angular/core";

@Component({
  selector: "app-user-card",
  template: `
    <div class="card">
      <h3>{{ user?.name }}</h3>
      <p>{{ user?.email }}</p>
    </div>
  `,
})
export class UserCardComponent implements OnChanges {
  @Input() user?: User;
  @Input() displayMode: "compact" | "full" = "compact";

  ngOnChanges(changes: SimpleChanges): void {
    console.log("Changements détectés:", changes);

    // Vérifier quel Input a changé
    if (changes["user"]) {
      console.log("User a changé");
      console.log("Ancienne valeur:", changes["user"].previousValue);
      console.log("Nouvelle valeur:", changes["user"].currentValue);
      console.log("Premier changement:", changes["user"].firstChange);
    }

    if (changes["displayMode"]) {
      console.log(
        "Mode d'affichage a changé:",
        changes["displayMode"].currentValue
      );
    }
  }
}
```

### Structure de SimpleChanges

```typescript
interface SimpleChange {
  previousValue: any; // Valeur précédente
  currentValue: any; // Valeur actuelle
  firstChange: boolean; // true si c'est le premier changement
}

interface SimpleChanges {
  [propName: string]: SimpleChange;
}
```

### Quand utiliser ngOnChanges

✅ **À utiliser pour :**

1. **Réagir aux changements d'@Input** - Effectuer une action quand un @Input change
2. **Transformation de données** - Calculer des valeurs dérivées
3. **Validation** - Valider les nouvelles valeurs
4. **Mise à jour conditionnelle** - Recharger des données si nécessaire
5. **Logging/Debug** - Tracer les changements d'inputs

### Exemples d'utilisation

#### Réagir aux changements d'Input

```typescript
@Component({
  selector: "app-product-detail",
  template: `
    <div *ngIf="product">
      <h2>{{ product.name }}</h2>
      <p>Prix: {{ product.price }}€</p>
      <div *ngIf="relatedProducts.length">
        <h3>Produits similaires</h3>
        <ul>
          <li *ngFor="let p of relatedProducts">{{ p.name }}</li>
        </ul>
      </div>
    </div>
  `,
})
export class ProductDetailComponent implements OnChanges {
  @Input() product!: Product;
  relatedProducts: Product[] = [];

  constructor(private productService: ProductService) {}

  ngOnChanges(changes: SimpleChanges): void {
    if (changes["product"] && !changes["product"].firstChange) {
      // Le produit a changé (mais pas au premier chargement)
      this.loadRelatedProducts();
    }
  }

  private loadRelatedProducts(): void {
    this.productService
      .getRelatedProducts(this.product.id)
      .subscribe((products) => {
        this.relatedProducts = products;
      });
  }
}
```

#### Transformation de données

```typescript
@Component({
  selector: "app-temperature-display",
  template: `
    <div>
      <p>Température: {{ celsius }}°C / {{ fahrenheit }}°F</p>
    </div>
  `,
})
export class TemperatureDisplayComponent implements OnChanges {
  @Input() celsius: number = 0;
  fahrenheit: number = 0;

  ngOnChanges(changes: SimpleChanges): void {
    if (changes["celsius"]) {
      // Recalculer Fahrenheit quand Celsius change
      this.fahrenheit = (this.celsius * 9) / 5 + 32;
    }
  }
}
```

#### Validation et réaction conditionnelle

```typescript
@Component({
  selector: "app-user-age-validator",
  template: `
    <div>
      <p>Âge: {{ age }}</p>
      <p *ngIf="isAdult" class="success">✓ Utilisateur majeur</p>
      <p *ngIf="!isAdult" class="warning">⚠ Utilisateur mineur</p>
    </div>
  `,
})
export class UserAgeValidatorComponent implements OnChanges {
  @Input() age: number = 0;
  isAdult: boolean = false;

  ngOnChanges(changes: SimpleChanges): void {
    if (changes["age"]) {
      const newAge = changes["age"].currentValue;

      // Validation
      if (newAge < 0 || newAge > 150) {
        console.error("Âge invalide:", newAge);
        this.age = 0;
        this.isAdult = false;
        return;
      }

      // Calcul de propriété dérivée
      this.isAdult = newAge >= 18;

      // Actions conditionnelles
      if (this.isAdult && !changes["age"].firstChange) {
        console.log("L'utilisateur vient de devenir majeur !");
      }
    }
  }
}
```

#### Comparer les changements

```typescript
@Component({
  selector: "app-settings-panel",
  template: `<div>{{ settings | json }}</div>`,
})
export class SettingsPanelComponent implements OnChanges {
  @Input() settings!: AppSettings;

  ngOnChanges(changes: SimpleChanges): void {
    if (changes["settings"]) {
      const change = changes["settings"];

      // Premier chargement
      if (change.firstChange) {
        console.log("Chargement initial des paramètres");
        this.initializeSettings();
        return;
      }

      // Changement ultérieur
      const oldSettings = change.previousValue;
      const newSettings = change.currentValue;

      // Détecter les changements spécifiques
      if (oldSettings.theme !== newSettings.theme) {
        console.log("Le thème a changé:", newSettings.theme);
        this.applyTheme(newSettings.theme);
      }

      if (oldSettings.language !== newSettings.language) {
        console.log("La langue a changé:", newSettings.language);
        this.changeLanguage(newSettings.language);
      }
    }
  }

  private initializeSettings(): void {
    console.log("Initialisation avec:", this.settings);
  }

  private applyTheme(theme: string): void {
    // Appliquer le nouveau thème
  }

  private changeLanguage(lang: string): void {
    // Changer la langue
  }
}
```

### ngOnChanges avec plusieurs Inputs

```typescript
@Component({
  selector: "app-chart",
  template: `<canvas #chart></canvas>`,
})
export class ChartComponent implements OnChanges {
  @Input() data: number[] = [];
  @Input() labels: string[] = [];
  @Input() chartType: "bar" | "line" | "pie" = "bar";
  @Input() width: number = 400;
  @Input() height: number = 300;

  private chart: any;

  ngOnChanges(changes: SimpleChanges): void {
    // Recréer le graphique si data ou labels changent
    if (changes["data"] || changes["labels"]) {
      this.updateChartData();
    }

    // Changer le type de graphique
    if (changes["chartType"] && !changes["chartType"].firstChange) {
      this.changeChartType(changes["chartType"].currentValue);
    }

    // Redimensionner le graphique
    if (changes["width"] || changes["height"]) {
      this.resizeChart();
    }
  }

  private updateChartData(): void {
    console.log("Mise à jour des données du graphique");
    // Logique de mise à jour
  }

  private changeChartType(type: string): void {
    console.log("Changement du type de graphique vers:", type);
    // Logique de changement de type
  }

  private resizeChart(): void {
    console.log(`Redimensionnement: ${this.width}x${this.height}`);
    // Logique de redimensionnement
  }
}
```
