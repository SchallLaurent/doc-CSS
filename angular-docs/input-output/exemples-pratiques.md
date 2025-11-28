## Exemples pratiques

### Exemple 1 : Composant de carte réutilisable

```typescript
// card.component.ts
@Component({
  selector: "app-card",
  template: `
    <div class="card" [class.card-clickable]="clickable">
      <div class="card-header" *ngIf="title">
        <h3>{{ title }}</h3>
        <button *ngIf="closable" (click)="onClose()" class="close-btn">
          ×
        </button>
      </div>
      <div class="card-body">
        <ng-content></ng-content>
      </div>
      <div class="card-footer" *ngIf="footer">
        <ng-content select="[footer]"></ng-content>
      </div>
    </div>
  `,
  styles: [
    `
      .card {
        border: 1px solid #ddd;
        border-radius: 8px;
        padding: 16px;
      }
      .card-clickable {
        cursor: pointer;
      }
      .card-header {
        display: flex;
        justify-content: space-between;
      }
      .close-btn {
        border: none;
        background: none;
        cursor: pointer;
      }
    `,
  ],
})
export class CardComponent {
  @Input() title: string = "";
  @Input() closable: boolean = false;
  @Input() clickable: boolean = false;
  @Input() footer: boolean = false;

  @Output() cardClose = new EventEmitter<void>();
  @Output() cardClick = new EventEmitter<void>();

  onClose(): void {
    this.cardClose.emit();
  }

  @HostListener("click")
  onClick(): void {
    if (this.clickable) {
      this.cardClick.emit();
    }
  }
}
```

**Utilisation :**

```html
<app-card
  title="Mon titre"
  [closable]="true"
  [clickable]="true"
  [footer]="true"
  (cardClose)="onCardClose()"
  (cardClick)="onCardClick()"
>
  <p>Contenu de la carte</p>

  <div footer>
    <button>Action</button>
  </div>
</app-card>
```

### Exemple 2 : Composant de table de données

```typescript
interface Column<T> {
  key: keyof T;
  label: string;
  sortable?: boolean;
}

interface SortEvent<T> {
  column: keyof T;
  direction: "asc" | "desc";
}

@Component({
  selector: "app-data-table",
  template: `
    <table>
      <thead>
        <tr>
          <th
            *ngFor="let column of columns"
            [class.sortable]="column.sortable"
            (click)="column.sortable && onSort(column.key)"
          >
            {{ column.label }}
            <span *ngIf="column.sortable && sortColumn === column.key">
              {{ sortDirection === "asc" ? "▲" : "▼" }}
            </span>
          </th>
          <th *ngIf="actions">Actions</th>
        </tr>
      </thead>
      <tbody>
        <tr
          *ngFor="let row of data; let i = index"
          (click)="onRowClick(row, i)"
        >
          <td *ngFor="let column of columns">
            {{ row[column.key] }}
          </td>
          <td *ngIf="actions">
            <button (click)="onEdit(row); $event.stopPropagation()">✏️</button>
            <button (click)="onDelete(row); $event.stopPropagation()">
              🗑️
            </button>
          </td>
        </tr>
      </tbody>
    </table>
  `,
})
export class DataTableComponent<T> {
  @Input() data: T[] = [];
  @Input() columns: Column<T>[] = [];
  @Input() actions: boolean = false;

  @Output() rowClick = new EventEmitter<{ row: T; index: number }>();
  @Output() sort = new EventEmitter<SortEvent<T>>();
  @Output() edit = new EventEmitter<T>();
  @Output() delete = new EventEmitter<T>();

  sortColumn: keyof T | null = null;
  sortDirection: "asc" | "desc" = "asc";

  onRowClick(row: T, index: number): void {
    this.rowClick.emit({ row, index });
  }

  onSort(column: keyof T): void {
    if (this.sortColumn === column) {
      this.sortDirection = this.sortDirection === "asc" ? "desc" : "asc";
    } else {
      this.sortColumn = column;
      this.sortDirection = "asc";
    }

    this.sort.emit({ column, direction: this.sortDirection });
  }

  onEdit(row: T): void {
    this.edit.emit(row);
  }

  onDelete(row: T): void {
    this.delete.emit(row);
  }
}
```

**Utilisation :**

```typescript
interface User {
  id: number;
  name: string;
  email: string;
  age: number;
}

@Component({
  template: `
    <app-data-table
      [data]="users"
      [columns]="columns"
      [actions]="true"
      (rowClick)="onRowClick($event)"
      (sort)="onSort($event)"
      (edit)="onEdit($event)"
      (delete)="onDelete($event)"
    >
    </app-data-table>
  `,
})
export class UserListComponent {
  users: User[] = [
    { id: 1, name: "Laurent", email: "laurent@example.com", age: 30 },
    { id: 2, name: "Marie", email: "marie@example.com", age: 25 },
  ];

  columns: Column<User>[] = [
    { key: "id", label: "ID", sortable: true },
    { key: "name", label: "Nom", sortable: true },
    { key: "email", label: "Email", sortable: false },
    { key: "age", label: "Âge", sortable: true },
  ];

  onRowClick(event: { row: User; index: number }): void {
    console.log("Row clicked:", event.row);
  }

  onSort(event: SortEvent<User>): void {
    console.log("Sort by:", event.column, event.direction);
    // Trier les données
  }

  onEdit(user: User): void {
    console.log("Edit:", user);
  }

  onDelete(user: User): void {
    console.log("Delete:", user);
  }
}
```

### Exemple 3 : Pagination réutilisable

```typescript
@Component({
  selector: "app-pagination",
  template: `
    <div class="pagination">
      <button (click)="goToPage(1)" [disabled]="currentPage === 1">
        ⏮️ Premier
      </button>

      <button
        (click)="goToPage(currentPage - 1)"
        [disabled]="currentPage === 1"
      >
        ◀️ Précédent
      </button>

      <span class="page-info"> Page {{ currentPage }} / {{ totalPages }} </span>

      <button
        (click)="goToPage(currentPage + 1)"
        [disabled]="currentPage === totalPages"
      >
        Suivant ▶️
      </button>

      <button
        (click)="goToPage(totalPages)"
        [disabled]="currentPage === totalPages"
      >
        Dernier ⏭️
      </button>
    </div>
  `,
})
export class PaginationComponent {
  @Input() totalItems: number = 0;
  @Input() currentPage: number = 1;
  @Input() itemsPerPage: number = 10;

  @Output() pageChange = new EventEmitter<number>();

  get totalPages(): number {
    return Math.ceil(this.totalItems / this.itemsPerPage);
  }

  goToPage(page: number): void {
    if (page >= 1 && page <= this.totalPages && page !== this.currentPage) {
      this.pageChange.emit(page);
    }
  }
}
```
