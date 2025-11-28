## Ordre d'exécution

### Séquence complète au chargement

```typescript
@Component({
  selector: "app-lifecycle-demo",
  template: `<p>{{ message }}</p>`,
})
export class LifecycleDemoComponent implements OnChanges, OnInit, OnDestroy {
  @Input() data: string = "";
  message: string = "";

  constructor() {
    console.log("1. Constructor");
    // this.data est undefined ici !
  }

  ngOnChanges(changes: SimpleChanges): void {
    console.log("2. ngOnChanges (avant ngOnInit)");
    console.log("   data =", this.data);
  }

  ngOnInit(): void {
    console.log("3. ngOnInit");
    console.log("   data =", this.data);
  }

  ngOnDestroy(): void {
    console.log("4. ngOnDestroy (à la destruction)");
  }
}
```

**Ordre d'exécution :**

```
1. Constructor
2. ngOnChanges (premier changement des @Input)
3. ngOnInit
4. ngOnChanges (changements ultérieurs des @Input)
...
N. ngOnDestroy
```

### Exemple avec changements multiples

```typescript
// Composant parent
@Component({
  selector: "app-parent",
  template: `
    <button (click)="updateUser()">Mettre à jour l'utilisateur</button>
    <app-child [user]="currentUser"></app-child>
  `,
})
export class ParentComponent {
  currentUser = { name: "Laurent", age: 30 };

  updateUser(): void {
    // Déclenche ngOnChanges dans le composant enfant
    this.currentUser = { name: "Jean", age: 35 };
  }
}

// Composant enfant
@Component({
  selector: "app-child",
  template: `<p>{{ user.name }} - {{ user.age }} ans</p>`,
})
export class ChildComponent implements OnChanges, OnInit {
  @Input() user!: { name: string; age: number };

  ngOnChanges(changes: SimpleChanges): void {
    console.log("ngOnChanges appelé");
    // Appelé à chaque fois que currentUser change dans le parent
  }

  ngOnInit(): void {
    console.log("ngOnInit appelé");
    // Appelé une seule fois
  }
}
```
