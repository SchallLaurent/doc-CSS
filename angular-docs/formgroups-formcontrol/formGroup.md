## FormGroup

Un **FormGroup** regroupe plusieurs FormControl pour créer un formulaire complet.

### Création basique

```typescript
import { Component } from "@angular/core";
import { FormGroup, FormControl } from "@angular/forms";

@Component({
  selector: "app-register",
  template: `
    <form [formGroup]="registerForm" (ngSubmit)="onSubmit()">
      <input formControlName="username" placeholder="Nom d'utilisateur" />
      <input formControlName="email" type="email" placeholder="Email" />
      <input
        formControlName="password"
        type="password"
        placeholder="Mot de passe"
      />
      <button type="submit">S'inscrire</button>
    </form>
  `,
})
export class RegisterComponent {
  registerForm = new FormGroup({
    username: new FormControl(""),
    email: new FormControl(""),
    password: new FormControl(""),
  });

  onSubmit() {
    console.log(this.registerForm.value);
    // { username: '...', email: '...', password: '...' }
  }
}
```

### FormGroup avec validators

```typescript
import { Component } from "@angular/core";
import { FormGroup, FormControl, Validators } from "@angular/forms";

@Component({
  selector: "app-login",
  templateUrl: "./login.component.html",
})
export class LoginComponent {
  loginForm = new FormGroup({
    email: new FormControl("", [Validators.required, Validators.email]),
    password: new FormControl("", [
      Validators.required,
      Validators.minLength(8),
    ]),
    rememberMe: new FormControl(false),
  });

  onSubmit() {
    if (this.loginForm.valid) {
      console.log("Formulaire valide :", this.loginForm.value);
    } else {
      console.log("Formulaire invalide");
    }
  }
}
```

### FormGroup imbriqués

```typescript
export class UserProfileComponent {
  profileForm = new FormGroup({
    // Informations personnelles
    personalInfo: new FormGroup({
      firstName: new FormControl("", Validators.required),
      lastName: new FormControl("", Validators.required),
      birthDate: new FormControl(""),
    }),

    // Adresse
    address: new FormGroup({
      street: new FormControl(""),
      city: new FormControl("", Validators.required),
      zipCode: new FormControl("", [
        Validators.required,
        Validators.pattern(/^\d{5}$/),
      ]),
      country: new FormControl("France"),
    }),

    // Contact
    contact: new FormGroup({
      email: new FormControl("", [Validators.required, Validators.email]),
      phone: new FormControl(""),
    }),
  });

  onSubmit() {
    console.log(this.profileForm.value);
    /*
    {
      personalInfo: { firstName: '...', lastName: '...', birthDate: '...' },
      address: { street: '...', city: '...', zipCode: '...', country: '...' },
      contact: { email: '...', phone: '...' }
    }
    */
  }
}
```

**Template pour FormGroup imbriqués :**

```html
<form [formGroup]="profileForm" (ngSubmit)="onSubmit()">
  <div formGroupName="personalInfo">
    <input formControlName="firstName" placeholder="Prénom" />
    <input formControlName="lastName" placeholder="Nom" />
    <input formControlName="birthDate" type="date" />
  </div>

  <div formGroupName="address">
    <input formControlName="street" placeholder="Rue" />
    <input formControlName="city" placeholder="Ville" />
    <input formControlName="zipCode" placeholder="Code postal" />
    <input formControlName="country" placeholder="Pays" />
  </div>

  <div formGroupName="contact">
    <input formControlName="email" type="email" placeholder="Email" />
    <input formControlName="phone" placeholder="Téléphone" />
  </div>

  <button type="submit" [disabled]="profileForm.invalid">Enregistrer</button>
</form>
```
