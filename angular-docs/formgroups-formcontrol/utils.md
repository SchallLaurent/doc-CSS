## Méthodes utiles

### État et validation

```typescript
export class FormComponent {
  form = new FormGroup({
    email: new FormControl("", [Validators.required, Validators.email]),
    password: new FormControl("", Validators.required),
  });

  checkFormState() {
    // Validité
    console.log(this.form.valid); // true/false
    console.log(this.form.invalid); // true/false

    // État touché (l'utilisateur a interagi)
    console.log(this.form.touched); // true/false
    console.log(this.form.untouched); // true/false

    // État modifié (la valeur a changé)
    console.log(this.form.dirty); // true/false
    console.log(this.form.pristine); // true/false

    // État en attente (async validators en cours)
    console.log(this.form.pending); // true/false

    // État désactivé
    console.log(this.form.disabled); // true/false
    console.log(this.form.enabled); // true/false

    // Erreurs
    console.log(this.form.errors); // Object ou null
    console.log(this.form.get("email")?.errors);
  }
}
```

### Marquer comme touché/modifié

```typescript
export class FormComponent {
  form = new FormGroup({
    name: new FormControl(""),
  });

  markForm() {
    // Marquer comme touché
    this.form.markAsTouched();
    this.form.get("name")?.markAsTouched();

    // Marquer tous les contrôles comme touchés (utile pour afficher toutes les erreurs)
    this.form.markAllAsTouched();

    // Marquer comme non touché
    this.form.markAsUntouched();

    // Marquer comme modifié
    this.form.markAsDirty();

    // Marquer comme non modifié
    this.form.markAsPristine();
  }

  onSubmit() {
    // Afficher toutes les erreurs avant la soumission
    if (this.form.invalid) {
      this.form.markAllAsTouched();
      return;
    }

    // Soumettre le formulaire
    console.log(this.form.value);
  }
}
```

### Activer/Désactiver des contrôles

```typescript
export class FormComponent {
  form = new FormGroup({
    agreeToTerms: new FormControl(false),
    email: new FormControl({ value: "", disabled: true }),
  });

  toggleEmailField() {
    const agreeToTerms = this.form.get("agreeToTerms")?.value;
    const emailControl = this.form.get("email");

    if (agreeToTerms) {
      emailControl?.enable();
    } else {
      emailControl?.disable();
    }
  }

  // Alternative avec valueChanges
  ngOnInit() {
    this.form.get("agreeToTerms")?.valueChanges.subscribe((agreed) => {
      if (agreed) {
        this.form.get("email")?.enable();
      } else {
        this.form.get("email")?.disable();
      }
    });
  }
}
```
