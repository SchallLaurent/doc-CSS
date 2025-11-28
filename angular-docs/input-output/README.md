# @Input et @Output - Communication entre composants Angular

> Guide complet sur la communication parent-enfant avec @Input et @Output

## 📚 Table des matières

- [@Input - Données du parent vers l'enfant](./input---données-du-parent-vers-lenfant.md)
- [@Output - Événements de l'enfant vers le parent](./output---événements-de-lenfant-vers-le-parent)
- [Two-way binding avec @Input/@Output](./two-way-binding-avec-inputoutput)
- [Alias et renommage](./alias-et-renommage)
- [Getters et Setters avec @Input](./getters-et-setters-avec-input)
- [Exemples pratiques](./exemples-pratiques)
- [Communication entre frères](./communication-entre-frères)
- [Best Practices](./best-practices)
- [Pièges courants](./pièges-courants)

---

## Introduction

Dans Angular, les composants peuvent communiquer entre eux de différentes manières. Les décorateurs `@Input` et `@Output` permettent de créer une communication **parent → enfant** et **enfant → parent**.

### Pattern de communication

```
┌─────────────────────────┐
│   Composant Parent      │
│                         │
│  @Input  ──────▶        │  Données vers l'enfant
│          ◀────── @Output│  Événements vers le parent
│                         │
└─────────────────────────┘
           │
           ▼
┌─────────────────────────┐
│   Composant Enfant      │
└─────────────────────────┘
```

### Imports nécessaires

```typescript
import { Component, Input, Output, EventEmitter } from "@angular/core";
```
