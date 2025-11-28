## Exemples pratiques complets

### Exemple 1 : Composant de pagination

```typescript
@Component({
  selector: "app-paginator",
  template: `
    <div class="paginator">
      <button (click)="previousPage()" [disabled]="currentPage === 1">
        Précédent
      </button>
      <span>Page {{ currentPage }} / {{ totalPages }}</span>
      <button (click)="nextPage()" [disabled]="currentPage === totalPages">
        Suivant
      </button>
    </div>
  `,
})
export class PaginatorComponent implements OnChanges {
  @Input() totalItems: number = 0;
  @Input() itemsPerPage: number = 10;
  @Input() currentPage: number = 1;
  @Output() pageChange = new EventEmitter<number>();

  totalPages: number = 0;

  ngOnChanges(changes: SimpleChanges): void {
    // Recalculer le nombre de pages si totalItems ou itemsPerPage change
    if (changes["totalItems"] || changes["itemsPerPage"]) {
      this.totalPages = Math.ceil(this.totalItems / this.itemsPerPage);

      // Valider currentPage
      if (this.currentPage > this.totalPages) {
        this.currentPage = this.totalPages || 1;
        this.pageChange.emit(this.currentPage);
      }
    }

    // Valider currentPage si elle change directement
    if (changes["currentPage"]) {
      const newPage = changes["currentPage"].currentValue;
      if (newPage < 1 || newPage > this.totalPages) {
        console.warn("Page invalide:", newPage);
        this.currentPage = 1;
      }
    }
  }

  previousPage(): void {
    if (this.currentPage > 1) {
      this.currentPage--;
      this.pageChange.emit(this.currentPage);
    }
  }

  nextPage(): void {
    if (this.currentPage < this.totalPages) {
      this.currentPage++;
      this.pageChange.emit(this.currentPage);
    }
  }
}
```

### Exemple 2 : Composant de filtre avec recherche

```typescript
@Component({
  selector: "app-search-filter",
  template: `
    <input [(ngModel)]="searchTerm" placeholder="Rechercher..." />
    <div>{{ filteredItems.length }} résultats</div>
  `,
})
export class SearchFilterComponent implements OnInit, OnChanges, OnDestroy {
  @Input() items: any[] = [];
  @Input() searchFields: string[] = ["name"];
  @Output() filteredItemsChange = new EventEmitter<any[]>();

  searchTerm: string = "";
  filteredItems: any[] = [];
  private destroy$ = new Subject<void>();
  private searchSubject = new Subject<string>();

  ngOnInit(): void {
    // Debounce de la recherche
    this.searchSubject
      .pipe(debounceTime(300), distinctUntilChanged(), takeUntil(this.destroy$))
      .subscribe((term) => {
        this.performFilter(term);
      });
  }

  ngOnChanges(changes: SimpleChanges): void {
    // Re-filtrer si les items ou searchFields changent
    if (changes["items"] || changes["searchFields"]) {
      this.performFilter(this.searchTerm);
    }
  }

  ngOnDestroy(): void {
    this.destroy$.next();
    this.destroy$.complete();
  }

  private performFilter(term: string): void {
    if (!term) {
      this.filteredItems = [...this.items];
    } else {
      this.filteredItems = this.items.filter((item) =>
        this.searchFields.some((field) =>
          item[field]?.toLowerCase().includes(term.toLowerCase())
        )
      );
    }
    this.filteredItemsChange.emit(this.filteredItems);
  }
}
```
