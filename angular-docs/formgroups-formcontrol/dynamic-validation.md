## Validation dynamique

### Ajouter/Retirer des validators

```typescript
export class DynamicValidationComponent {
  form = new FormGroup({
    accountType: new FormControl("personal"),
    companyName: new FormControl(""),
    taxId: new FormControl(""),
  });

  ngOnInit() {
    this.form.get("accountType")?.valueChanges.subscribe((type) => {
      const companyNameControl = this.form.get("companyName");
      const taxIdControl = this.form.get("taxId");

      if (type === "business") {
        // Ajouter des validators
        companyNameControl?.setValidators([Validators.required]);
        taxIdControl?.setValidators([
          Validators.required,
          Validators.pattern(/^\d{9}$/),
        ]);
      } else {
        // Retirer des validators
        companyNameControl?.clearValidators();
        taxIdControl?.clearValidators();
      }

      // IMPORTANT : mettre à jour la validation
      companyNameControl?.updateValueAndValidity();
      taxIdControl?.updateValueAndValidity();
    });
  }
}
```
