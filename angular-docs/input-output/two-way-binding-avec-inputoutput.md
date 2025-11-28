## Two-way binding avec @Input/@Output

Angular permet de créer un two-way binding en suivant la convention `[(property)]`.

### Convention de nommage

Pour créer un two-way binding, vous devez :

1. Créer un `@Input()` avec un nom (ex: `value`)
2. Créer un `@Output()` avec le même nom + `Change` (ex: `valueChange`)

### Exemple basique

```typescript
@Component({
  selector: "app-custom-input",
  template: `
    <input
      [value]="value"
      (input)="onInputChange($event)"
      placeholder="Entrez du texte"
    />
  `,
})
export class CustomInputComponent {
  @Input() value: string = "";
  @Output() valueChange = new EventEmitter<string>();

  onInputChange(event: Event): void {
    const newValue = (event.target as HTMLInputElement).value;
    this.value = newValue;
    this.valueChange.emit(newValue);
  }
}
```

**Utilisation avec two-way binding :**

```typescript
@Component({
  selector: "app-parent",
  template: `
    <!-- Two-way binding -->
    <app-custom-input [(value)]="userName"></app-custom-input>
    <p>Nom : {{ userName }}</p>

    <!-- Équivalent à : -->
    <app-custom-input [value]="userName" (valueChange)="userName = $event">
    </app-custom-input>
  `,
})
export class ParentComponent {
  userName = "Laurent";
}
```

### Exemple avec compteur

```typescript
@Component({
  selector: "app-stepper",
  template: `
    <div class="stepper">
      <button (click)="decrement()" [disabled]="value <= min">-</button>
      <span>{{ value }}</span>
      <button (click)="increment()" [disabled]="value >= max">+</button>
    </div>
  `,
})
export class StepperComponent {
  @Input() value: number = 0;
  @Input() min: number = 0;
  @Input() max: number = 100;
  @Input() step: number = 1;

  @Output() valueChange = new EventEmitter<number>();

  increment(): void {
    if (this.value < this.max) {
      this.value += this.step;
      this.valueChange.emit(this.value);
    }
  }

  decrement(): void {
    if (this.value > this.min) {
      this.value -= this.step;
      this.valueChange.emit(this.value);
    }
  }
}
```

**Utilisation :**

```html
<app-stepper [(value)]="quantity" [min]="1" [max]="10" [step]="1">
</app-stepper>
<p>Quantité : {{ quantity }}</p>
```

### Exemple avec sélection

```typescript
interface Option {
  id: number;
  label: string;
}

@Component({
  selector: "app-select",
  template: `
    <select (change)="onChange($event)">
      <option *ngFor="let option of options" [value]="option.id">
        {{ option.label }}
      </option>
    </select>
  `,
})
export class SelectComponent {
  @Input() options: Option[] = [];
  @Input() selectedId: number | null = null;

  @Output() selectedIdChange = new EventEmitter<number>();

  onChange(event: Event): void {
    const select = event.target as HTMLSelectElement;
    const newId = parseInt(select.value, 10);
    this.selectedId = newId;
    this.selectedIdChange.emit(newId);
  }
}
```
