## Pièges courants

### 1. Oublier que ngOnChanges est appelé avant ngOnInit

```typescript
// ❌ PROBLÈME
export class MyComponent implements OnChanges, OnInit {
  @Input() data: any;
  processedData: any;

  ngOnInit(): void {
    this.processedData = this.transformData(this.data);
  }

  ngOnChanges(): void {
    console.log(this.processedData); // undefined au premier appel !
  }
}

// ✅ SOLUTION
ngOnChanges(changes: SimpleChanges): void {
  if (changes['data'] && this.processedData) {
    // Vérifier que processedData existe
  }
}
```

### 2. Références d'objets et détection de changement

```typescript
// ❌ Angular ne détecte PAS ce changement
updateUser(): void {
  this.user.name = 'Nouveau nom'; // Même référence d'objet
}

// ✅ Créer une nouvelle référence
updateUser(): void {
  this.user = { ...this.user, name: 'Nouveau nom' };
}

// Ou
updateUser(): void {
  this.user = Object.assign({}, this.user, { name: 'Nouveau nom' });
}
```

### 3. Performance avec ngOnChanges fréquents

```typescript
// ❌ MAUVAIS - recalcul à chaque changement
@Input() items: any[] = [];

ngOnChanges(): void {
  this.expensiveCalculation(this.items); // Coûteux !
}

// ✅ MEILLEUR - avec mémoization
private lastItems: any[] = [];
private cachedResult: any;

ngOnChanges(changes: SimpleChanges): void {
  if (changes['items']) {
    const newItems = changes['items'].currentValue;

    if (!this.areArraysEqual(this.lastItems, newItems)) {
      this.cachedResult = this.expensiveCalculation(newItems);
      this.lastItems = [...newItems];
    }
  }
}
```

### 4. Accès aux ViewChild dans ngOnInit

```typescript
// ❌ MAUVAIS - ViewChild pas encore disponible
@ViewChild('myElement') myElement!: ElementRef;

ngOnInit(): void {
  console.log(this.myElement); // undefined !
}

// ✅ BON - utiliser ngAfterViewInit
ngAfterViewInit(): void {
  console.log(this.myElement); // Disponible ici
}
```

### 5. Modifications causant des erreurs de détection de changement

```typescript
// ❌ PROVOQUE ExpressionChangedAfterItHasBeenCheckedError
@Input() value: number = 0;
@Output() valueChange = new EventEmitter<number>();

ngOnChanges(changes: SimpleChanges): void {
  if (changes['value']) {
    this.valueChange.emit(this.value * 2); // ❌ Modification pendant la détection
  }
}

// ✅ SOLUTION - utiliser setTimeout ou AfterViewInit
ngOnChanges(changes: SimpleChanges): void {
  if (changes['value']) {
    setTimeout(() => {
      this.valueChange.emit(this.value * 2);
    });
  }
}
```
