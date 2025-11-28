## Écouter les changements

### valueChanges

```typescript
export class FormComponent implements OnInit {
  form = new FormGroup({
    search: new FormControl(""),
    category: new FormControl("all"),
  });

  ngOnInit() {
    // Écouter tous les changements du formulaire
    this.form.valueChanges.subscribe((values) => {
      console.log("Formulaire modifié :", values);
    });

    // Écouter un contrôle spécifique
    this.form.get("search")?.valueChanges.subscribe((searchTerm) => {
      console.log("Recherche :", searchTerm);
      // Faire une recherche, filtrer, etc.
    });

    // Avec debounce pour optimiser
    this.form
      .get("search")
      ?.valueChanges.pipe(debounceTime(300), distinctUntilChanged())
      .subscribe((searchTerm) => {
        console.log("Recherche avec debounce :", searchTerm);
      });
  }
}
```

### statusChanges

```typescript
export class FormComponent implements OnInit {
  form = new FormGroup({
    email: new FormControl("", [Validators.required, Validators.email]),
  });

  ngOnInit() {
    // Écouter les changements de statut
    this.form.statusChanges.subscribe((status) => {
      console.log("Statut du formulaire :", status);
      // Status peut être : 'VALID', 'INVALID', 'PENDING', 'DISABLED'
    });

    this.form.get("email")?.statusChanges.subscribe((status) => {
      console.log("Statut du champ email :", status);
    });
  }
}
```
