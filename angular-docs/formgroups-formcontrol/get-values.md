## Accéder aux valeurs

### Lire les valeurs

```typescript
export class FormComponent {
  form = new FormGroup({
    name: new FormControl("Laurent"),
    email: new FormControl("laurent@example.com"),
  });

  getValues() {
    // Valeur complète du formulaire
    console.log(this.form.value);
    // { name: 'Laurent', email: 'laurent@example.com' }

    // Valeur d'un contrôle spécifique
    console.log(this.form.get("name")?.value); // 'Laurent'

    // Accès direct si le FormControl est une propriété
    const nameControl = new FormControl("Laurent");
    console.log(nameControl.value); // 'Laurent'

    // getRawValue() inclut les champs désactivés
    console.log(this.form.getRawValue());
  }
}
```

### Modifier les valeurs

```typescript
export class FormComponent {
  form = new FormGroup({
    name: new FormControl(""),
    email: new FormControl(""),
  });

  setValues() {
    // setValue - doit fournir TOUTES les valeurs
    this.form.setValue({
      name: "Laurent",
      email: "laurent@example.com",
    });

    // patchValue - peut fournir seulement certaines valeurs
    this.form.patchValue({
      name: "Laurent", // email reste inchangé
    });

    // Modifier un contrôle spécifique
    this.form.get("name")?.setValue("Jean");

    // Avec options
    this.form.setValue(
      { name: "Laurent", email: "laurent@example.com" },
      { emitEvent: false } // Ne déclenche pas valueChanges
    );
  }

  resetForm() {
    // Reset à vide
    this.form.reset();

    // Reset avec valeurs spécifiques
    this.form.reset({
      name: "",
      email: "default@example.com",
    });
  }
}
```
