## Communication entre frères

Pour la communication entre composants frères (siblings), utilisez un service partagé.

### Via un service

```typescript
// shared-data.service.ts
@Injectable({ providedIn: "root" })
export class SharedDataService {
  private messageSource = new BehaviorSubject<string>("");
  currentMessage$ = this.messageSource.asObservable();

  changeMessage(message: string): void {
    this.messageSource.next(message);
  }
}

// sibling-a.component.ts
@Component({
  selector: "app-sibling-a",
  template: `
    <input [(ngModel)]="message" />
    <button (click)="sendMessage()">Envoyer</button>
  `,
})
export class SiblingAComponent {
  message = "";

  constructor(private sharedData: SharedDataService) {}

  sendMessage(): void {
    this.sharedData.changeMessage(this.message);
  }
}

// sibling-b.component.ts
@Component({
  selector: "app-sibling-b",
  template: `<p>Message reçu : {{ receivedMessage }}</p>`,
})
export class SiblingBComponent implements OnInit {
  receivedMessage = "";

  constructor(private sharedData: SharedDataService) {}

  ngOnInit(): void {
    this.sharedData.currentMessage$.subscribe((message) => {
      this.receivedMessage = message;
    });
  }
}
```

### Via le parent

```typescript
// parent.component.ts
@Component({
  selector: "app-parent",
  template: `
    <app-sibling-a (messageToSend)="onMessageFromA($event)"></app-sibling-a>
    <app-sibling-b [messageReceived]="sharedMessage"></app-sibling-b>
  `,
})
export class ParentComponent {
  sharedMessage = "";

  onMessageFromA(message: string): void {
    this.sharedMessage = message;
  }
}

// sibling-a.component.ts
@Component({
  selector: "app-sibling-a",
  template: `
    <input [(ngModel)]="message" />
    <button (click)="send()">Envoyer</button>
  `,
})
export class SiblingAComponent {
  message = "";
  @Output() messageToSend = new EventEmitter<string>();

  send(): void {
    this.messageToSend.emit(this.message);
  }
}

// sibling-b.component.ts
@Component({
  selector: "app-sibling-b",
  template: `<p>Message : {{ messageReceived }}</p>`,
})
export class SiblingBComponent {
  @Input() messageReceived = "";
}
```
