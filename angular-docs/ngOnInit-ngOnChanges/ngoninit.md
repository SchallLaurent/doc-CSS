## ngOnInit

### Définition

`ngOnInit` est appelé **une seule fois** après la première initialisation du composant, juste après le premier `ngOnChanges`.

### Import et implémentation

```typescript
import { Component, OnInit } from "@angular/core";

@Component({
  selector: "app-user-profile",
  template: `<h1>{{ userName }}</h1>`,
})
export class UserProfileComponent implements OnInit {
  userName: string = "";

  // Implémentation obligatoire de l'interface OnInit
  ngOnInit(): void {
    console.log("Le composant a été initialisé");
    this.loadUserData();
  }

  private loadUserData(): void {
    this.userName = "Laurent";
  }
}
```

### Quand utiliser ngOnInit

✅ **À utiliser pour :**

1. **Initialisation de données** - Charger des données depuis une API
2. **Configuration initiale** - Configurer des propriétés du composant
3. **Souscription aux Observables** - S'abonner à des streams de données
4. **Initialisation de FormGroup** - Créer et configurer des formulaires
5. **Logique d'initialisation complexe** - Tout ce qui dépend des @Input

```typescript
import { Component, OnInit, Input } from "@angular/core";

@Component({
  selector: "app-user-detail",
  template: `
    <div *ngIf="user">
      <h2>{{ user.name }}</h2>
      <p>{{ user.email }}</p>
    </div>
  `,
})
export class UserDetailComponent implements OnInit {
  @Input() userId!: number;
  user: User | null = null;

  constructor(private userService: UserService) {}

  ngOnInit(): void {
    // Les @Input sont disponibles ici
    console.log("User ID reçu:", this.userId);

    // Charger les données utilisateur
    this.userService.getUser(this.userId).subscribe((user) => {
      this.user = user;
    });
  }
}
```

### Pourquoi pas dans le constructor ?

```typescript
// ❌ MAUVAIS - Les @Input ne sont pas encore disponibles
constructor(private service: MyService) {
  console.log(this.userId); // undefined !
  this.loadData(); // ❌ userId n'est pas encore défini
}

// ✅ BON - Les @Input sont disponibles dans ngOnInit
ngOnInit(): void {
  console.log(this.userId); // Valeur correcte
  this.loadData(); // ✅ userId est défini
}
```

### Exemples d'utilisation courante

#### Chargement de données API

```typescript
export class ProductListComponent implements OnInit {
  products: Product[] = [];
  loading = false;

  constructor(private productService: ProductService) {}

  ngOnInit(): void {
    this.loading = true;

    this.productService.getProducts().subscribe({
      next: (products) => {
        this.products = products;
        this.loading = false;
      },
      error: (error) => {
        console.error("Erreur:", error);
        this.loading = false;
      },
    });
  }
}
```

#### Initialisation de formulaire

```typescript
export class UserFormComponent implements OnInit {
  @Input() userId?: number;
  userForm!: FormGroup;

  constructor(private fb: FormBuilder, private userService: UserService) {}

  ngOnInit(): void {
    // Créer le formulaire
    this.userForm = this.fb.group({
      name: ["", Validators.required],
      email: ["", [Validators.required, Validators.email]],
      age: [null, [Validators.min(18)]],
    });

    // Charger les données si userId existe
    if (this.userId) {
      this.loadUserData();
    }
  }

  private loadUserData(): void {
    this.userService.getUser(this.userId!).subscribe((user) => {
      this.userForm.patchValue({
        name: user.name,
        email: user.email,
        age: user.age,
      });
    });
  }
}
```

#### Souscription à un Observable

```typescript
export class NotificationComponent implements OnInit, OnDestroy {
  notifications: string[] = [];
  private destroy$ = new Subject<void>();

  constructor(private notificationService: NotificationService) {}

  ngOnInit(): void {
    this.notificationService.notifications$
      .pipe(takeUntil(this.destroy$))
      .subscribe((notification) => {
        this.notifications.push(notification);
      });
  }

  ngOnDestroy(): void {
    this.destroy$.next();
    this.destroy$.complete();
  }
}
```
