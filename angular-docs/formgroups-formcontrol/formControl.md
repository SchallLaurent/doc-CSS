## FormControl

Un **FormControl** représente un seul champ de formulaire. Il track la valeur et l'état de validation du champ.

### Création basique

```typescript
import { Component } from "@angular/core";
import { FormControl } from "@angular/forms";

@Component({
  selector: "app-user",
  template: `
    <input [formControl]="name" placeholder="Nom" />
    <p>Valeur : {{ name.value }}</p>
  `,
})
export class UserComponent {
  // FormControl simple
  name = new FormControl("");

  // Avec valeur initiale
  email = new FormControl("laurent@example.com");

  // Avec valeur initiale typée
  age = new FormControl<number>(25);
}
```

### FormControl avec options

```typescript
import { FormControl, Validators } from "@angular/forms";

export class UserComponent {
  // Avec validators
  email = new FormControl("", [Validators.required, Validators.email]);

  // Avec valeur initiale et validators
  password = new FormControl("", [
    Validators.required,
    Validators.minLength(8),
  ]);

  // Désactivé par défaut
  username = new FormControl({ value: "", disabled: true });

  // Configuration complète
  phone = new FormControl("", {
    validators: [Validators.required],
    updateOn: "blur", // ou 'change' (défaut) ou 'submit'
  });
}
```

### Nouvelle syntaxe avec nonNullable (Angular 14+)

```typescript
// Ancienne syntaxe
name = new FormControl(""); // Type: FormControl<string | null>

// Nouvelle syntaxe - empêche null
name = new FormControl("", { nonNullable: true }); // Type: FormControl<string>

// Avec validators
email = new FormControl("", {
  validators: [Validators.required, Validators.email],
  nonNullable: true,
});
```
