## Différences et quand utiliser chacun

### Tableau comparatif

| Critère                | ngOnInit                                        | ngOnChanges                  |
| ---------------------- | ----------------------------------------------- | ---------------------------- |
| **Appelé quand**       | Une seule fois après la première initialisation | À chaque changement d'@Input |
| **Paramètres**         | Aucun                                           | SimpleChanges                |
| **Accès aux @Input**   | ✅ Oui                                          | ✅ Oui                       |
| **Fréquence**          | Une fois                                        | Multiple                     |
| **Premier appel**      | Après premier ngOnChanges                       | Avant ngOnInit               |
| **Use case principal** | Initialisation                                  | Réaction aux changements     |

### Flowchart de décision

```
Besoin d'accéder aux @Input ?
│
├─ Non → Utiliser le constructor
│
└─ Oui → Une seule fois ou à chaque changement ?
          │
          ├─ Une seule fois → ngOnInit
          │
          └─ À chaque changement → ngOnChanges
```

### Exemples de choix

#### Utiliser ngOnInit

```typescript
// ✅ Charger des données une seule fois
ngOnInit(): void {
  this.loadInitialData();
}

// ✅ Initialiser un formulaire
ngOnInit(): void {
  this.form = this.fb.group({...});
}

// ✅ S'abonner à un Observable
ngOnInit(): void {
  this.data$ = this.service.getData();
}
```

#### Utiliser ngOnChanges

```typescript
// ✅ Recharger des données quand l'ID change
@Input() userId: number;

ngOnChanges(changes: SimpleChanges): void {
  if (changes['userId']) {
    this.loadUserData(changes['userId'].currentValue);
  }
}

// ✅ Recalculer une valeur dérivée
@Input() price: number;
@Input() quantity: number;

ngOnChanges(changes: SimpleChanges): void {
  if (changes['price'] || changes['quantity']) {
    this.total = this.price * this.quantity;
  }
}
```

### Utiliser les deux ensemble

```typescript
@Component({
  selector: "app-data-table",
  template: `...`,
})
export class DataTableComponent implements OnInit, OnChanges {
  @Input() dataSource: any[] = [];
  @Input() pageSize: number = 10;

  currentPage: number = 1;
  displayedData: any[] = [];

  ngOnInit(): void {
    // Configuration initiale (une seule fois)
    console.log("Initialisation de la table");
    this.setupPagination();
  }

  ngOnChanges(changes: SimpleChanges): void {
    // Réagir aux changements de données
    if (changes["dataSource"]) {
      console.log("Les données ont changé");
      this.updateDisplayedData();
    }

    // Réagir aux changements de taille de page
    if (changes["pageSize"] && !changes["pageSize"].firstChange) {
      console.log("La taille de page a changé");
      this.currentPage = 1; // Reset à la page 1
      this.updateDisplayedData();
    }
  }

  private setupPagination(): void {
    // Configuration initiale
  }

  private updateDisplayedData(): void {
    const start = (this.currentPage - 1) * this.pageSize;
    const end = start + this.pageSize;
    this.displayedData = this.dataSource.slice(start, end);
  }
}
```
