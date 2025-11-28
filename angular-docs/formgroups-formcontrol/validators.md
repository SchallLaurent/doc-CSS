## Validators

Angular fournit des validators prédéfinis et permet de créer des validators personnalisés.

### Validators prédéfinis

```typescript
import { Validators } from "@angular/forms";

export class FormComponent {
  form = new FormGroup({
    // Champ requis
    name: new FormControl("", Validators.required),

    // Email valide
    email: new FormControl("", [Validators.required, Validators.email]),

    // Longueur minimale
    password: new FormControl("", [
      Validators.required,
      Validators.minLength(8),
    ]),

    // Longueur maximale
    bio: new FormControl("", Validators.maxLength(500)),

    // Pattern (regex)
    phone: new FormControl("", Validators.pattern(/^0[1-9]\d{8}$/)),

    // Valeur minimale (pour nombres)
    age: new FormControl("", [
      Validators.required,
      Validators.min(18),
      Validators.max(120),
    ]),

    // Multiple validators
    username: new FormControl("", [
      Validators.required,
      Validators.minLength(3),
      Validators.maxLength(20),
      Validators.pattern(/^[a-zA-Z0-9_]+$/),
    ]),
  });
}
```

### Validator personnalisé

```typescript
import { AbstractControl, ValidationErrors, ValidatorFn } from "@angular/forms";

// Validator de confirmation de mot de passe
export function passwordMatchValidator(): ValidatorFn {
  return (control: AbstractControl): ValidationErrors | null => {
    const password = control.get("password");
    const confirmPassword = control.get("confirmPassword");

    if (!password || !confirmPassword) {
      return null;
    }

    return password.value === confirmPassword.value
      ? null
      : { passwordMismatch: true };
  };
}

// Utilisation
export class RegisterComponent {
  registerForm = new FormGroup(
    {
      password: new FormControl("", [
        Validators.required,
        Validators.minLength(8),
      ]),
      confirmPassword: new FormControl("", Validators.required),
    },
    { validators: passwordMatchValidator() }
  );
}
```

**Autre exemple - Validator de domaine email :**

```typescript
export function emailDomainValidator(domain: string): ValidatorFn {
  return (control: AbstractControl): ValidationErrors | null => {
    const email = control.value;

    if (!email) {
      return null;
    }

    const emailDomain = email.substring(email.lastIndexOf("@") + 1);

    return emailDomain.toLowerCase() === domain.toLowerCase()
      ? null
      : { invalidDomain: { expected: domain, actual: emailDomain } };
  };
}

// Utilisation
email = new FormControl("", [
  Validators.required,
  Validators.email,
  emailDomainValidator("company.com"),
]);
```

### Validator asynchrone

Utile pour vérifier la disponibilité d'un username via API.

```typescript
import { AsyncValidatorFn } from "@angular/forms";
import { Observable, of } from "rxjs";
import { map, delay } from "rxjs/operators";

export class RegisterComponent {
  constructor(private userService: UserService) {}

  usernameValidator(): AsyncValidatorFn {
    return (control: AbstractControl): Observable<ValidationErrors | null> => {
      if (!control.value) {
        return of(null);
      }

      return this.userService
        .checkUsername(control.value)
        .pipe(
          map((isAvailable) => (isAvailable ? null : { usernameTaken: true }))
        );
    };
  }

  registerForm = new FormGroup({
    username: new FormControl(
      "",
      [Validators.required],
      [this.usernameValidator()] // Async validator en 3ème paramètre
    ),
  });
}
```
