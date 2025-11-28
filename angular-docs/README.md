# 🅰️ Angular Docs

Documentation complète sur Angular pour le développement d'applications web modernes.

## 📖 Contenu

Ce dossier contient des guides détaillés sur Angular, organisés par thématiques pour faciliter l'apprentissage et servir de référence rapide lors du développement.

### 📚 Documents disponibles

#### Formulaires (Forms)

- [FormGroups & FormControl](./formgroups-formcontrol/)
  - Gestion des formulaires réactifs
  - FormControl - Contrôles individuels
  - FormGroup - Groupement de contrôles
  - Validators - Validation prédéfinie et personnalisée
  - FormBuilder - Simplification de la création
  - Exemples pratiques et best practices

#### Lifecycle Hooks

- **[ngOnInit & ngOnChanges](./ngOnInit-ngOnChanges/)** - Hooks de cycle de vie des composants
  - ngOnInit - Initialisation du composant
  - ngOnChanges - Réaction aux changements d'@Input
  - SimpleChanges - Structure et utilisation
  - Ordre d'exécution des hooks
  - Différences et cas d'usage
  - Best practices et pièges à éviter

#### Communication entre composants

- **[@Input & @Output](./input-output/)** - Communication parent-enfant
  - @Input - Passage de données du parent vers l'enfant
  - @Output - Émission d'événements de l'enfant vers le parent
  - EventEmitter - Gestion des événements
  - Two-way binding - Convention [(property)]
  - Alias et renommage de propriétés
  - Getters/Setters avec @Input
  - Communication entre frères (siblings)
  - Best practices et pièges à éviter

## 🎯 Objectifs

- 📖 Fournir des explications claires des concepts Angular
- 💻 Proposer des exemples de code prêts à l'emploi
- 🔍 Servir de référence rapide pendant le développement
- 🎓 Accompagner la montée en compétences sur Angular
- ⚡ Partager les bonnes pratiques et patterns Angular

### Pour une recherche rapide

Utilisez la table des matières pour naviguer directement vers le sujet qui vous intéresse.

## 💡 Cas d'usage fréquents

### Je veux...

**...créer un formulaire avec validation**
→ Voir [formgroups-formcontrol](./formgroups-formcontrol/) - FormGroup avec validators

## 🛠️ Setup et configuration

### Prérequis

```bash
# Installer Node.js (version 18+ recommandée)
node --version

# Installer Angular CLI
npm install -g @angular/cli

# Vérifier l'installation
ng version
```

### Créer un nouveau projet

```bash
# Créer un projet avec routing et CSS
ng new mon-projet

# Créer un projet avec options spécifiques
ng new mon-projet --routing --style=scss --standalone

# Lancer le serveur de développement
cd mon-projet
ng serve

# Ouvrir http://localhost:4200
```

### Commandes essentielles

```bash
# Générer un composant
ng generate component mon-composant
ng g c mon-composant

# Générer un service
ng generate service mon-service
ng g s mon-service

# Générer un module
ng generate module mon-module
ng g m mon-module

# Générer une directive
ng g directive ma-directive

# Générer un pipe
ng g pipe mon-pipe

# Build de production
ng build --configuration production

# Lancer les tests
ng test

# Lancer les tests E2E
ng e2e
```

### Best Practices d'organisation

1. **Un composant = un dossier** contenant .ts, .html, .scss, .spec.ts
2. **Services dans core/** pour les singletons
3. **Composants réutilisables dans shared/**
4. **Features séparés** avec lazy loading
5. **Models/interfaces** dans des fichiers dédiés

## 🔧 Outils et extensions recommandés

### VSCode Extensions

- **Angular Language Service** - IntelliSense pour Angular
- **Angular Snippets** - Snippets de code
- **ESLint** - Linting TypeScript/Angular
- **Prettier** - Formatage de code
- **Auto Rename Tag** - Renommer les tags HTML
- **Path Intellisense** - Autocomplétion des chemins

### Outils de développement

- **Angular DevTools** - Extension Chrome/Firefox pour debug
- **Augury** - Inspecteur de composants (legacy)
- **Redux DevTools** - Pour NgRx

### Librairies utiles

- **@angular/material** - Composants Material Design
- **@ngrx/store** - State management
- **ngx-translate** - Internationalisation (i18n)
- **@angular/pwa** - Progressive Web App
- **tailwindcss** - Framework CSS utility-first
- **ng-zorro-antd** - Composants UI Ant Design
- **primeng** - Suite de composants UI

## 🚦 Convention de nommage

### Fichiers

```
feature-name.component.ts       # Composant
feature-name.component.html     # Template
feature-name.component.scss     # Styles
feature-name.component.spec.ts  # Tests
feature-name.service.ts         # Service
feature-name.module.ts          # Module
feature-name.routes.ts          # Routes
```

### Classes

```typescript
// Composants
export class UserProfileComponent {}

// Services
export class AuthService {}

// Directives
export class HighlightDirective {}

// Pipes
export class FormatDatePipe {}

// Guards
export class AuthGuard {}
```

### Sélecteurs

```typescript
// Préfixe app- pour éviter les conflits
@Component({
  selector: 'app-user-profile',  // Convention kebab-case
})
```

## 📚 Ressources complémentaires

### Documentation officielle

- [Angular.io](https://angular.io/) - Documentation officielle
- [Angular Blog](https://blog.angular.io/) - Actualités et annonces
- [Angular Update Guide](https://update.angular.io/) - Guide de migration

### Communauté

- [Angular GitHub](https://github.com/angular/angular)
- [r/Angular](https://www.reddit.com/r/Angular2/)
- [Stack Overflow - Angular](https://stackoverflow.com/questions/tagged/angular)
- [Angular Discord](https://discord.gg/angular)

### Performance

```typescript
// Utiliser OnPush change detection
@Component({
  changeDetection: ChangeDetectionStrategy.OnPush
})

// TrackBy pour ngFor
<div *ngFor="let item of items; trackBy: trackById">

trackById(index: number, item: any): number {
  return item.id;
}
```

### Debugging

```typescript
// Inspecter dans le template
{{ variable | json }}

// Logger les changes
ngOnChanges(changes: SimpleChanges) {
  console.log('Changes:', changes);
}
```

### Productivité

```bash
# Snippets pour générer rapidement
ng g c components/header --skip-tests
ng g s services/auth --skip-tests

# Dry run avant de générer
ng g c mon-component --dry-run
```

---

**Note :** Angular évolue rapidement. Cette documentation est maintenue à jour avec les dernières versions et best practices.
