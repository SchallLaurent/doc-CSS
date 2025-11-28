# Documentation : Modificateurs d'accès et méthodes statiques en POO

## Les modificateurs d'accès

Les modificateurs d'accès contrôlent la visibilité et l'accessibilité des propriétés et méthodes d'une classe. Ils sont fondamentaux pour l'encapsulation, un des piliers de la programmation orientée objet.

### Public

Les membres publics sont accessibles depuis n'importe où : à l'intérieur de la classe, dans les classes dérivées, et depuis l'extérieur de la classe.

```typescript
class Voiture {
  public marque: string;

  public constructor(marque: string) {
    this.marque = marque;
  }

  public demarrer(): void {
    console.log(`${this.marque} démarre`);
  }
}

const maVoiture = new Voiture("Peugeot");
console.log(maVoiture.marque); // Accessible ✓
maVoiture.demarrer(); // Accessible ✓
```

**Cas d'usage :** Utilisez `public` pour l'API publique de votre classe, c'est-à-dire les méthodes et propriétés que vous voulez exposer aux utilisateurs de la classe.

---

### Private

Les membres privés ne sont accessibles qu'à l'intérieur de la classe où ils sont définis. Ils ne sont pas accessibles dans les classes dérivées ni depuis l'extérieur.

```typescript
class CompteBancaire {
  private solde: number;

  constructor(soldeInitial: number) {
    this.solde = soldeInitial;
  }

  private validerMontant(montant: number): boolean {
    return montant > 0;
  }

  public deposer(montant: number): void {
    if (this.validerMontant(montant)) {
      this.solde += montant;
    }
  }

  public getSolde(): number {
    return this.solde;
  }
}

const compte = new CompteBancaire(1000);
// compte.solde // Erreur : propriété privée ✗
// compte.validerMontant(50) // Erreur : méthode privée ✗
compte.deposer(500); // Fonctionne ✓
console.log(compte.getSolde()); // 1500 ✓
```

**Cas d'usage :** Utilisez `private` pour les détails d'implémentation que vous ne voulez pas exposer, protégeant ainsi l'intégrité de vos données et gardant la flexibilité de modifier l'implémentation interne sans affecter le code externe.

---

### Protected

Les membres protégés sont accessibles à l'intérieur de la classe et dans toutes les classes qui en héritent, mais pas depuis l'extérieur.

```typescript
class Animal {
  protected nom: string;

  constructor(nom: string) {
    this.nom = nom;
  }

  protected faireBruit(): void {
    console.log("Un bruit quelconque");
  }
}

class Chien extends Animal {
  public aboyer(): void {
    // Accès au membre protected de la classe parente
    console.log(`${this.nom} aboie: Woof!`);
    this.faireBruit(); // Accessible ✓
  }
}

const monChien = new Chien("Rex");
monChien.aboyer(); // Rex aboie: Woof! ✓
// monChien.nom // Erreur : propriété protégée ✗
// monChien.faireBruit() // Erreur : méthode protégée ✗
```

**Cas d'usage :** Utilisez `protected` quand vous voulez permettre aux classes dérivées d'accéder à certains membres tout en les cachant du monde extérieur. C'est utile pour créer des classes de base extensibles.

---

## Les méthodes statiques

Les méthodes statiques appartiennent à la classe elle-même plutôt qu'aux instances de la classe. Elles sont appelées directement sur la classe et ne peuvent pas accéder aux membres d'instance (non-statiques).

```typescript
class MathUtils {
  private static PI: number = 3.14159;

  // Méthode statique
  public static calculerAireRectangle(
    longueur: number,
    largeur: number
  ): number {
    return longueur * largeur;
  }

  public static calculerAireCercle(rayon: number): number {
    // Accès à une propriété statique
    return this.PI * rayon * rayon;
  }

  // Méthode d'instance (non-statique)
  public doubler(nombre: number): number {
    return nombre * 2;
  }
}

// Appel de méthodes statiques sur la classe
console.log(MathUtils.calculerAireRectangle(5, 3)); // 15 ✓
console.log(MathUtils.calculerAireCercle(10)); // 314.159 ✓

// Pour les méthodes d'instance, il faut créer une instance
const utils = new MathUtils();
console.log(utils.doubler(5)); // 10 ✓

// Impossible d'appeler une méthode d'instance sur la classe
// MathUtils.doubler(5) // Erreur ✗
```

### Exemple pratique : Factory Pattern

```typescript
class User {
  constructor(public id: number, public nom: string, public email: string) {}

  // Méthode statique pour créer un utilisateur depuis JSON
  public static fromJSON(json: string): User {
    const data = JSON.parse(json);
    return new User(data.id, data.nom, data.email);
  }

  // Méthode statique pour créer un utilisateur par défaut
  public static creerParDefaut(): User {
    return new User(0, "Anonyme", "anonyme@example.com");
  }
}

const user1 = User.fromJSON(
  '{"id": 1, "nom": "Laurent", "email": "laurent@example.com"}'
);
const user2 = User.creerParDefaut();
```

---

## Tableau récapitulatif

| Modificateur  | Classe elle-même | Classes dérivées | Extérieur |
| ------------- | ---------------- | ---------------- | --------- |
| **public**    | ✓                | ✓                | ✓         |
| **protected** | ✓                | ✓                | ✗         |
| **private**   | ✓                | ✗                | ✗         |

---

## Bonnes pratiques

### 1. Principe du moindre privilège

Commencez toujours par `private`, puis passez à `protected` ou `public` uniquement si nécessaire.

### 2. Encapsulation

Utilisez des getters/setters plutôt que d'exposer directement les propriétés publiques, cela vous permet de contrôler l'accès et la validation.

```typescript
class Utilisateur {
  private _age: number;

  public get age(): number {
    return this._age;
  }

  public set age(value: number) {
    if (value < 0 || value > 150) {
      throw new Error("Âge invalide");
    }
    this._age = value;
  }
}
```

### 3. Méthodes statiques

Utilisez-les pour les fonctions utilitaires, les factory methods, ou quand la logique ne dépend pas de l'état d'une instance.

### 4. Évitez l'abus de statique

Trop de méthodes statiques peuvent rendre le code difficile à tester et à maintenir.

### 5. Protected avec parcimonie

N'exposez en `protected` que ce qui est vraiment nécessaire pour l'extension de la classe.

---

## Exemples dans différents langages

### Java

```java
public class Exemple {
    public int publicVar;
    protected int protectedVar;
    private int privateVar;

    public static void methodeStatique() {
        System.out.println("Méthode statique");
    }
}
```

### C#

```csharp
public class Exemple {
    public int PublicVar;
    protected int ProtectedVar;
    private int PrivateVar;

    public static void MethodeStatique() {
        Console.WriteLine("Méthode statique");
    }
}
```

### PHP

```php
class Exemple {
    public $publicVar;
    protected $protectedVar;
    private $privateVar;

    public static function methodeStatique() {
        echo "Méthode statique";
    }
}
```

---

## Cas d'usage avancés

### Singleton Pattern avec private constructor

```typescript
class Configuration {
  private static instance: Configuration;
  private config: Map<string, any>;

  // Constructeur privé pour empêcher l'instanciation directe
  private constructor() {
    this.config = new Map();
  }

  public static getInstance(): Configuration {
    if (!Configuration.instance) {
      Configuration.instance = new Configuration();
    }
    return Configuration.instance;
  }

  public set(key: string, value: any): void {
    this.config.set(key, value);
  }

  public get(key: string): any {
    return this.config.get(key);
  }
}

// Utilisation
const config1 = Configuration.getInstance();
const config2 = Configuration.getInstance();
console.log(config1 === config2); // true - même instance
```

### Template Method Pattern avec protected

```typescript
abstract class DataProcessor {
  // Méthode template publique
  public process(): void {
    this.loadData();
    this.validateData();
    this.transformData();
    this.saveData();
  }

  // Méthodes protected que les sous-classes peuvent surcharger
  protected abstract loadData(): void;
  protected abstract transformData(): void;

  protected validateData(): void {
    console.log("Validation des données par défaut");
  }

  protected saveData(): void {
    console.log("Sauvegarde des données par défaut");
  }
}

class CSVProcessor extends DataProcessor {
  protected loadData(): void {
    console.log("Chargement depuis CSV");
  }

  protected transformData(): void {
    console.log("Transformation spécifique CSV");
  }
}
```

---

## Conclusion

Les modificateurs d'accès et les méthodes statiques sont des outils essentiels pour créer du code orienté objet robuste, maintenable et sécurisé. En comprenant et en appliquant correctement ces concepts, vous pourrez mieux structurer vos classes et contrôler l'accès à leurs membres.
