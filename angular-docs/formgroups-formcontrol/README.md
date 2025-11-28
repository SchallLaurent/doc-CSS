# FormGroup et FormControl - Angular Reactive Forms

> Guide complet sur la gestion des formulaires réactifs avec FormGroup et FormControl

## 📚 Table des matières

- [FormControl](./formControl.md)
- [FormGroup](./formGroup.md)
- [Validators](./validators.md)
- [Accéder aux valeurs](./get-values.md)
- [Écouter les changements](./listen-changements.md)
- [Méthodes utiles](./utils.md)
- [Validation dynamique](./dynamic-validation.md)
- [FormBuilder](./formBuilder.md)
- [Exemples pratiques](./example.md)
- [Best Practices](./best-practices.md)

---

## Introduction

Les **Reactive Forms** dans Angular utilisent un modèle de programmation réactive pour gérer les formulaires. Contrairement aux Template-driven Forms, les Reactive Forms offrent plus de contrôle et de flexibilité.

### Import nécessaire

```typescript
import { ReactiveFormsModule } from "@angular/forms";

@NgModule({
  imports: [ReactiveFormsModule],
})
export class AppModule {}
```

Pour les composants standalone :

```typescript
import { Component } from "@angular/core";
import { ReactiveFormsModule } from "@angular/forms";

@Component({
  selector: "app-login",
  standalone: true,
  imports: [ReactiveFormsModule],
  templateUrl: "./login.component.html",
})
export class LoginComponent {}
```

_Dernière mise à jour : Novembre 2025_
