## Best Practices

### 1. Utiliser des interfaces pour les @Input complexes

```typescript
// ✅ BON
interface UserConfig {
  showAvatar: boolean;
  showEmail: boolean;
  theme: 'light' | 'dark';
}

@Input() config!: UserConfig;

// ❌ MAUVAIS - trop de @Input séparés
@Input() showAvatar: boolean;
@Input() showEmail: boolean;
@Input() theme: string;
```

### 2. Toujours typer les EventEmitter

```typescript
// ✅ BON
@Output() userSelected = new EventEmitter<User>();
@Output() searchPerformed = new EventEmitter<{ term: string; filters: string[] }>();

// ❌ MAUVAIS - pas de type
@Output() userSelected = new EventEmitter();
```

### 3. Utiliser des noms descriptifs

```typescript
// ✅ BON
@Output() productAddedToCart = new EventEmitter<Product>();
@Output() formSubmitted = new EventEmitter<FormData>();

// ❌ MAUVAIS - trop vague
@Output() action = new EventEmitter();
@Output() event = new EventEmitter();
```

### 4. Préférer les objets immutables

```typescript
// ✅ BON
onUpdate(): void {
  const updatedUser = { ...this.user, name: 'Nouveau nom' };
  this.userUpdate.emit(updatedUser);
}

// ❌ MAUVAIS - mutation directe
onUpdate(): void {
  this.user.name = 'Nouveau nom';
  this.userUpdate.emit(this.user);
}
```

### 5. Utiliser OnChanges pour réagir aux changements d'@Input

```typescript
// ✅ BON
export class MyComponent implements OnChanges {
  @Input() userId: number;

  ngOnChanges(changes: SimpleChanges): void {
    if (changes["userId"] && !changes["userId"].firstChange) {
      this.loadUserData();
    }
  }
}
```

### 6. Valider les @Input

```typescript
// ✅ BON
@Input()
set percentage(value: number) {
  if (value < 0 || value > 100) {
    console.warn('Percentage must be between 0 and 100');
    this._percentage = Math.max(0, Math.min(100, value));
  } else {
    this._percentage = value;
  }
}
```

### 7. Documentation avec JSDoc

```typescript
/**
 * Composant d'affichage de produit
 */
@Component({ ... })
export class ProductComponent {
  /**
   * ID du produit à afficher
   * @required
   */
  @Input({ required: true }) productId!: number;

  /**
   * Émis quand le produit est ajouté au panier
   * @event
   */
  @Output() addToCart = new EventEmitter<Product>();
}
```
