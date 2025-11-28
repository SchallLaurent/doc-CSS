## Best Practices

### 1. Toujours vérifier firstChange dans ngOnChanges

```typescript
// ✅ BON
ngOnChanges(changes: SimpleChanges): void {
  if (changes['userId'] && !changes['userId'].firstChange) {
    this.loadUserData();
  }
}

// ❌ MAUVAIS - charge les données deux fois
ngOnChanges(changes: SimpleChanges): void {
  if (changes['userId']) {
    this.loadUserData(); // Appelé par ngOnChanges ET ngOnInit
  }
}

ngOnInit(): void {
  this.loadUserData(); // Doublon !
}
```

### 2. Gérer le cas où l'Input est undefined

```typescript
// ✅ BON
ngOnChanges(changes: SimpleChanges): void {
  if (changes['data'] && changes['data'].currentValue) {
    this.processData(changes['data'].currentValue);
  }
}

// ❌ MAUVAIS - peut crasher si data est null/undefined
ngOnChanges(changes: SimpleChanges): void {
  if (changes['data']) {
    this.processData(changes['data'].currentValue); // Peut être undefined !
  }
}
```

### 3. Ne pas muter les @Input directement

```typescript
// ❌ MAUVAIS
@Input() items: string[] = [];

ngOnChanges(): void {
  this.items.push('new item'); // Mutation directe !
}

// ✅ BON
@Input() items: string[] = [];
processedItems: string[] = [];

ngOnChanges(): void {
  this.processedItems = [...this.items, 'new item']; // Copie
}
```

### 4. Unsubscribe dans ngOnDestroy

```typescript
// ✅ BON
export class MyComponent implements OnInit, OnDestroy {
  private destroy$ = new Subject<void>();

  ngOnInit(): void {
    this.dataService
      .getData()
      .pipe(takeUntil(this.destroy$))
      .subscribe((data) => {
        // Traiter les données
      });
  }

  ngOnDestroy(): void {
    this.destroy$.next();
    this.destroy$.complete();
  }
}
```

### 5. Éviter la logique lourde dans ngOnChanges

```typescript
// ❌ MAUVAIS - calculs lourds à chaque changement
ngOnChanges(changes: SimpleChanges): void {
  if (changes['data']) {
    this.heavyComputation(); // Exécuté à chaque changement !
  }
}

// ✅ BON - debounce ou check si vraiment nécessaire
ngOnChanges(changes: SimpleChanges): void {
  if (changes['data']) {
    const oldValue = changes['data'].previousValue;
    const newValue = changes['data'].currentValue;

    // Vérifier si le recalcul est nécessaire
    if (this.hasSignificantChange(oldValue, newValue)) {
      this.heavyComputation();
    }
  }
}
```

### 6. Typer correctement SimpleChanges

```typescript
// ✅ BON - Type-safe
interface MyInputs {
  userId: number;
  userName: string;
}

ngOnChanges(changes: SimpleChanges): void {
  if (changes['userId']) {
    const userId = changes['userId'].currentValue as number;
    this.loadUser(userId);
  }
}

// Ou avec un helper type-safe
private hasChanged<K extends keyof MyInputs>(
  changes: SimpleChanges,
  key: K
): boolean {
  return changes[key] && !changes[key].firstChange;
}

ngOnChanges(changes: SimpleChanges): void {
  if (this.hasChanged(changes, 'userId')) {
    this.loadUser(this.userId);
  }
}
```
