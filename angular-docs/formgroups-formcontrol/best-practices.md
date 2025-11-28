## Best Practices

### 1. Utiliser des getters pour les contrôles fréquemment accédés

```typescript
// ❌ Mauvais
<div *ngIf="loginForm.get('email')?.invalid && loginForm.get('email')?.touched">

// ✅ Bon
get email() {
  return this.loginForm.get('email');
}

<div *ngIf="email?.invalid && email?.touched">
```

### 2. Typer vos FormGroup

```typescript
// ✅ Bon - avec interface
interface LoginForm {
  email: string;
  password: string;
  rememberMe: boolean;
}

loginForm = this.fb.group<LoginForm>({
  email: ["", [Validators.required, Validators.email]],
  password: ["", Validators.required],
  rememberMe: [false],
});
```

### 3. Centraliser les messages d'erreur

```typescript
errorMessages = {
  email: {
    required: 'L\'email est requis',
    email: 'Format d\'email invalide'
  },
  password: {
    required: 'Le mot de passe est requis',
    minlength: 'Minimum 8 caractères'
  }
};

getErrorMessage(controlName: string): string {
  const control = this.loginForm.get(controlName);
  if (control?.errors) {
    const errorKey = Object.keys(control.errors)[0];
    return this.errorMessages[controlName][errorKey];
  }
  return '';
}
```

### 4. Unsubscribe des observables

```typescript
import { Component, OnDestroy } from "@angular/core";
import { Subject } from "rxjs";
import { takeUntil } from "rxjs/operators";

export class FormComponent implements OnDestroy {
  private destroy$ = new Subject<void>();

  ngOnInit() {
    this.form.valueChanges.pipe(takeUntil(this.destroy$)).subscribe((value) => {
      console.log(value);
    });
  }

  ngOnDestroy() {
    this.destroy$.next();
    this.destroy$.complete();
  }
}
```

### 5. Marquer tous les champs comme touched avant submit

```typescript
onSubmit() {
  if (this.form.invalid) {
    this.form.markAllAsTouched();  // Affiche toutes les erreurs
    return;
  }

  // Traiter le formulaire
  console.log(this.form.value);
}
```

### 6. Utiliser updateOn pour optimiser la validation

```typescript
// Valider seulement au blur (perte de focus)
form = this.fb.group(
  {
    email: ["", [Validators.required, Validators.email]],
  },
  { updateOn: "blur" }
);

// Ou par contrôle
email = new FormControl("", {
  validators: [Validators.required, Validators.email],
  updateOn: "blur",
});
```

### 7. Réinitialiser le formulaire après soumission

```typescript
onSubmit() {
  if (this.form.valid) {
    this.api.submit(this.form.value).subscribe(() => {
      this.form.reset();  // Réinitialiser
      // Ou avec valeurs par défaut
      this.form.reset({
        email: '',
        newsletter: true
      });
    });
  }
}
```
