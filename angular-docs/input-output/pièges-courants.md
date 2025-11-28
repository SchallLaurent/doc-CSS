## Pièges courants

### 1. Oublier le binding de propriété

```typescript
// ❌ MAUVAIS - passe la chaîne "userName" littérale
<app-user [name]="userName"></app-user>

// ✅ BON - passe la valeur de la variable userName
<app-user [name]="userName"></app-user>
```

### 2. Mutation d'objets @Input

```typescript
// ❌ MAUVAIS - change detection peut ne pas détecter
@Input() user: User;

updateUser(): void {
  this.user.name = 'Nouveau nom'; // Mutation !
}

// ✅ BON - créer une nouvelle référence
@Input() user: User;

updateUser(): void {
  this.user = { ...this.user, name: 'Nouveau nom' };
}
```

### 3. Ne pas unsubscribe des EventEmitter

```typescript
// ⚠️ EventEmitter nettoie automatiquement
// Pas besoin de unsubscribe pour les @Output

// ✅ Mais nécessaire pour les Observables normaux
ngOnInit(): void {
  this.subscription = this.dataService.data$.subscribe(...);
}

ngOnDestroy(): void {
  this.subscription.unsubscribe();
}
```

### 4. Confusion entre @Input et variable locale

```typescript
// ❌ MAUVAIS
@Component({
  template: `<div>{{ title }}</div>`, // Quelle title ?
})
export class MyComponent {
  @Input() title: string;
  title = "Default"; // Conflit !
}

// ✅ BON - noms différents
@Component({
  template: `<div>{{ displayTitle }}</div>`,
})
export class MyComponent {
  @Input() title: string;

  get displayTitle(): string {
    return this.title || "Default";
  }
}
```

### 5. Émettre trop d'événements

```typescript
// ❌ MAUVAIS - émet à chaque frappe
@Output() searchChange = new EventEmitter<string>();

onInput(event: Event): void {
  const value = (event.target as HTMLInputElement).value;
  this.searchChange.emit(value); // Trop d'événements !
}

// ✅ BON - debounce
searchSubject = new Subject<string>();

ngOnInit(): void {
  this.searchSubject.pipe(
    debounceTime(300),
    distinctUntilChanged()
  ).subscribe(value => {
    this.searchChange.emit(value);
  });
}

onInput(event: Event): void {
  const value = (event.target as HTMLInputElement).value;
  this.searchSubject.next(value);
}
```

### 6. Oublier le required sur les @Input critiques

```typescript
// ❌ MAUVAIS - peut crasher si userId n'est pas fourni
@Input() userId: number;

ngOnInit(): void {
  this.loadUser(this.userId); // userId peut être undefined !
}

// ✅ BON - Angular 16+
@Input({ required: true }) userId!: number;

// ✅ BON - Avant Angular 16
@Input() userId!: number;

ngOnInit(): void {
  if (!this.userId) {
    throw new Error('userId is required');
  }
  this.loadUser(this.userId);
}
```
