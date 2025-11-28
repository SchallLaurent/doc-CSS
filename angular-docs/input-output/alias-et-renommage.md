### Alias pour @Output

```typescript
@Component({
  selector: "app-button",
  template: ` <button (click)="handleClick()">{{ label }}</button> `,
})
export class ButtonComponent {
  @Input() label: string = "Click me";

  // Nom interne : buttonClicked
  // Nom externe : click
  @Output("click") buttonClicked = new EventEmitter<void>();

  handleClick(): void {
    this.buttonClicked.emit();
  }
}
```

**Utilisation :**

```html
<app-button (click)="onButtonClick()"></app-button>
```

### Cas d'usage des alias

```typescript
// Éviter les conflits avec les propriétés HTML natives
@Component({
  selector: "app-custom-link",
  template: `<a [href]="linkHref">{{ linkText }}</a>`,
})
export class CustomLinkComponent {
  // "href" pourrait être confondu avec l'attribut HTML
  // On utilise un alias pour clarifier
  @Input("url") linkHref: string = "";
  @Input("text") linkText: string = "Link";
}
```
