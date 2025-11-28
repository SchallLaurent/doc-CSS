## @Output - Événements de l'enfant vers le parent

Le décorateur `@Output()` permet à un composant enfant d'émettre des événements vers son parent en utilisant `EventEmitter`.

### Utilisation basique

**Composant enfant :**

```typescript
import { Component, Output, EventEmitter } from "@angular/core";

@Component({
  selector: "app-counter",
  template: `
    <div>
      <button (click)="decrement()">-</button>
      <span>{{ count }}</span>
      <button (click)="increment()">+</button>
    </div>
  `,
})
export class CounterComponent {
  count = 0;

  @Output() countChange = new EventEmitter<number>();

  increment(): void {
    this.count++;
    this.countChange.emit(this.count);
  }

  decrement(): void {
    this.count--;
    this.countChange.emit(this.count);
  }
}
```

**Composant parent :**

```typescript
@Component({
  selector: "app-parent",
  template: `
    <app-counter (countChange)="onCountChange($event)"></app-counter>
    <p>Valeur dans le parent : {{ parentCount }}</p>
  `,
})
export class ParentComponent {
  parentCount = 0;

  onCountChange(newCount: number): void {
    this.parentCount = newCount;
    console.log("Nouveau compte:", newCount);
  }
}
```

### @Output avec objets

```typescript
interface SearchEvent {
  term: string;
  filters: string[];
  timestamp: Date;
}

@Component({
  selector: "app-search-bar",
  template: `
    <input [(ngModel)]="searchTerm" (keyup.enter)="search()" />
    <button (click)="search()">Rechercher</button>
  `,
})
export class SearchBarComponent {
  searchTerm = "";

  @Output() searchPerformed = new EventEmitter<SearchEvent>();

  search(): void {
    this.searchPerformed.emit({
      term: this.searchTerm,
      filters: ["active", "recent"],
      timestamp: new Date(),
    });
  }
}
```

**Utilisation :**

```typescript
@Component({
  selector: "app-parent",
  template: `
    <app-search-bar (searchPerformed)="handleSearch($event)"></app-search-bar>
  `,
})
export class ParentComponent {
  handleSearch(event: SearchEvent): void {
    console.log("Recherche:", event.term);
    console.log("Filtres:", event.filters);
    console.log("Date:", event.timestamp);
  }
}
```

### Événements multiples

```typescript
@Component({
  selector: "app-modal",
  template: `
    <div class="modal" *ngIf="isOpen">
      <div class="modal-header">
        <h2>{{ title }}</h2>
        <button (click)="close()">×</button>
      </div>
      <div class="modal-body">
        <ng-content></ng-content>
      </div>
      <div class="modal-footer">
        <button (click)="cancel()">Annuler</button>
        <button (click)="confirm()">Confirmer</button>
      </div>
    </div>
  `,
})
export class ModalComponent {
  @Input() title: string = "Modal";
  @Input() isOpen: boolean = false;

  @Output() modalClose = new EventEmitter<void>();
  @Output() modalConfirm = new EventEmitter<void>();
  @Output() modalCancel = new EventEmitter<void>();

  close(): void {
    this.modalClose.emit();
  }

  confirm(): void {
    this.modalConfirm.emit();
  }

  cancel(): void {
    this.modalCancel.emit();
  }
}
```

**Utilisation :**

```html
<app-modal
  [title]="'Confirmation'"
  [isOpen]="showModal"
  (modalClose)="onModalClose()"
  (modalConfirm)="onModalConfirm()"
  (modalCancel)="onModalCancel()"
>
  <p>Êtes-vous sûr de vouloir continuer ?</p>
</app-modal>
```

### @Output avec données de formulaire

```typescript
interface LoginData {
  email: string;
  password: string;
  rememberMe: boolean;
}

@Component({
  selector: "app-login-form",
  template: `
    <form [formGroup]="loginForm" (ngSubmit)="submit()">
      <input formControlName="email" type="email" placeholder="Email" />
      <input
        formControlName="password"
        type="password"
        placeholder="Mot de passe"
      />
      <label>
        <input formControlName="rememberMe" type="checkbox" />
        Se souvenir de moi
      </label>
      <button type="submit" [disabled]="loginForm.invalid">Se connecter</button>
    </form>
  `,
})
export class LoginFormComponent {
  @Output() loginSubmit = new EventEmitter<LoginData>();
  @Output() loginError = new EventEmitter<string>();

  loginForm = this.fb.group({
    email: ["", [Validators.required, Validators.email]],
    password: ["", [Validators.required, Validators.minLength(8)]],
    rememberMe: [false],
  });

  constructor(private fb: FormBuilder) {}

  submit(): void {
    if (this.loginForm.valid) {
      this.loginSubmit.emit(this.loginForm.value as LoginData);
    } else {
      this.loginError.emit("Formulaire invalide");
    }
  }
}
```
