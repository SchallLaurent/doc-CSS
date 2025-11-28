## Exemples pratiques

### Formulaire de connexion complet

```typescript
import { Component } from "@angular/core";
import { FormBuilder, FormGroup, Validators } from "@angular/forms";

@Component({
  selector: "app-login",
  template: `
    <form [formGroup]="loginForm" (ngSubmit)="onSubmit()">
      <div>
        <label>Email</label>
        <input formControlName="email" type="email" />
        <div *ngIf="email?.invalid && email?.touched" class="error">
          <span *ngIf="email?.errors?.['required']">L'email est requis</span>
          <span *ngIf="email?.errors?.['email']">Format d'email invalide</span>
        </div>
      </div>

      <div>
        <label>Mot de passe</label>
        <input formControlName="password" type="password" />
        <div *ngIf="password?.invalid && password?.touched" class="error">
          <span *ngIf="password?.errors?.['required']"
            >Le mot de passe est requis</span
          >
          <span *ngIf="password?.errors?.['minlength']">
            Minimum
            {{ password?.errors?.['minlength'].requiredLength }} caractères
          </span>
        </div>
      </div>

      <div>
        <label>
          <input formControlName="rememberMe" type="checkbox" />
          Se souvenir de moi
        </label>
      </div>

      <button type="submit" [disabled]="loginForm.invalid">Se connecter</button>
    </form>

    <pre>{{ loginForm.value | json }}</pre>
  `,
  styles: [
    `
      .error {
        color: red;
        font-size: 0.875rem;
        margin-top: 0.25rem;
      }
    `,
  ],
})
export class LoginComponent {
  loginForm: FormGroup;

  constructor(private fb: FormBuilder) {
    this.loginForm = this.fb.group({
      email: ["", [Validators.required, Validators.email]],
      password: ["", [Validators.required, Validators.minLength(8)]],
      rememberMe: [false],
    });
  }

  // Getters pour faciliter l'accès dans le template
  get email() {
    return this.loginForm.get("email");
  }

  get password() {
    return this.loginForm.get("password");
  }

  onSubmit() {
    if (this.loginForm.valid) {
      console.log("Login data:", this.loginForm.value);
      // Appeler le service d'authentification
    } else {
      this.loginForm.markAllAsTouched();
    }
  }
}
```

### Formulaire avec recherche en temps réel

```typescript
import { Component, OnInit } from "@angular/core";
import { FormControl } from "@angular/forms";
import { debounceTime, distinctUntilChanged, switchMap } from "rxjs/operators";

@Component({
  selector: "app-search",
  template: `
    <input [formControl]="searchControl" placeholder="Rechercher..." />

    <div *ngIf="loading">Chargement...</div>

    <ul>
      <li *ngFor="let result of results">{{ result }}</li>
    </ul>
  `,
})
export class SearchComponent implements OnInit {
  searchControl = new FormControl("");
  results: string[] = [];
  loading = false;

  constructor(private searchService: SearchService) {}

  ngOnInit() {
    this.searchControl.valueChanges
      .pipe(
        debounceTime(300), // Attendre 300ms après la dernière frappe
        distinctUntilChanged(), // Ignorer si la valeur n'a pas changé
        switchMap((term) => {
          this.loading = true;
          return this.searchService.search(term || "");
        })
      )
      .subscribe((results) => {
        this.results = results;
        this.loading = false;
      });
  }
}
```

### Formulaire avec tableau dynamique (FormArray)

```typescript
import { Component } from "@angular/core";
import { FormBuilder, FormGroup, FormArray, Validators } from "@angular/forms";

@Component({
  selector: "app-contact-list",
  template: `
    <form [formGroup]="contactForm">
      <div formArrayName="contacts">
        <div
          *ngFor="let contact of contacts.controls; let i = index"
          [formGroupName]="i"
        >
          <input formControlName="name" placeholder="Nom" />
          <input formControlName="phone" placeholder="Téléphone" />
          <button type="button" (click)="removeContact(i)">Supprimer</button>
        </div>
      </div>

      <button type="button" (click)="addContact()">Ajouter un contact</button>
    </form>
  `,
})
export class ContactListComponent {
  contactForm: FormGroup;

  constructor(private fb: FormBuilder) {
    this.contactForm = this.fb.group({
      contacts: this.fb.array([this.createContact()]),
    });
  }

  get contacts(): FormArray {
    return this.contactForm.get("contacts") as FormArray;
  }

  createContact(): FormGroup {
    return this.fb.group({
      name: ["", Validators.required],
      phone: ["", Validators.required],
    });
  }

  addContact() {
    this.contacts.push(this.createContact());
  }

  removeContact(index: number) {
    this.contacts.removeAt(index);
  }
}
```
