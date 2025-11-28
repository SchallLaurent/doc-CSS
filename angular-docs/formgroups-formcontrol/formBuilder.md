## FormBuilder

Le **FormBuilder** simplifie la création de FormGroup et FormControl.

### Import et utilisation basique

```typescript
import { Component, OnInit } from "@angular/core";
import { FormBuilder, FormGroup, Validators } from "@angular/forms";

@Component({
  selector: "app-user-form",
  templateUrl: "./user-form.component.html",
})
export class UserFormComponent implements OnInit {
  userForm!: FormGroup;

  constructor(private fb: FormBuilder) {}

  ngOnInit() {
    // Avec FormBuilder (plus concis)
    this.userForm = this.fb.group({
      name: ["", Validators.required],
      email: ["", [Validators.required, Validators.email]],
      age: [null, [Validators.min(18), Validators.max(120)]],
      address: this.fb.group({
        street: [""],
        city: ["", Validators.required],
        zipCode: [""],
      }),
    });
  }
}
```

### Comparaison sans/avec FormBuilder

```typescript
// SANS FormBuilder
userForm = new FormGroup({
  name: new FormControl("", Validators.required),
  email: new FormControl("", [Validators.required, Validators.email]),
  address: new FormGroup({
    street: new FormControl(""),
    city: new FormControl(""),
  }),
});

// AVEC FormBuilder (plus lisible)
userForm = this.fb.group({
  name: ["", Validators.required],
  email: ["", [Validators.required, Validators.email]],
  address: this.fb.group({
    street: [""],
    city: [""],
  }),
});
```

### FormBuilder avec nonNullable

```typescript
export class UserFormComponent implements OnInit {
  userForm!: FormGroup;

  constructor(private fb: FormBuilder) {}

  ngOnInit() {
    // FormBuilder avec nonNullable (Angular 14+)
    this.userForm = this.fb.nonNullable.group({
      name: ["", Validators.required],
      email: ["", [Validators.required, Validators.email]],
      age: [0, Validators.min(18)],
    });

    // Maintenant les valeurs ne peuvent pas être null
    const name: string = this.userForm.value.name; // Type: string (pas string | null)
  }
}
```
