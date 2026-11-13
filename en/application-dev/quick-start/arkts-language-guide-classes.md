---
kits: ["ArkTS Kit"]
description: "Definition and usage of ArkTS classes, covering properties, methods, constructors, access control, inheritance, abstract classes, and initialization."
keywords: [ArkTS, classes, class, decorators, constructors, access control, inheritance, abstract classes, object-oriented programming]
doctype: guide
status: active
---

# Classes
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @jokerxd-liu-->
<!--Designer: @jokerxd-liu-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=8923bda514baa1452b967ea964ea779c7417bd8e translatedAt=2026-11-12T12:34:02.295Z pushedAt=2026-10-30T06:21:33.935Z nl=1 -->

Classes are a core concept of object-oriented programming and encapsulate data and behavior. ArkTS provides full class support, including properties, methods, constructors, inheritance, access control, abstract classes, and decorators.

## Basic Concepts

A class is the basic construct of object-oriented programming. It encapsulates data (properties) and behavior (methods), and initializes instances through a constructor.

**Class Definition Syntax**

Use the `class` keyword to define a class, and declare properties, constructors, and methods within braces. Classes can be used as type annotations. Avoid defining empty classes, which have no members.

<!-- @[class_basic_definition](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Classes.ets) -->

``` TypeScript
// Basic class definition
class Person {
  public name: string;
  public age: number;
  
  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }
  
  greet(): string {
    return `Hello, I'm ${this.name}`;
  }
}

// Create an instance
let person: Person = new Person('Alice', 25);
console.info(`${person.greet()}`);

// Empty class
class EmptyClass {
}

let empty: EmptyClass = new EmptyClass();

// Class as a type
function processPerson(person: Person): void {
  console.info(`${person.name}`);
}

processPerson(person);
```

**Core Components of a Class (Properties, Methods, and Constructors)**

Properties store state, the constructor initializes properties, and methods encapsulate behavior. Together, they form the core structure of a class.

<!-- @[class_properties_methods_constructor](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Classes.ets) -->

``` TypeScript
class User {
  // Property
  public id: number;
  public name: string;
  public email: string;
  private password: string;
  
  // Constructor
  constructor(id: number, name: string, email: string) {
    this.id = id;
    this.name = name;
    this.email = email;
    this.password = '';
  }
  
  // Method
  getInfo(): string {
    return `User ${this.id}: ${this.name} (${this.email})`;
  }
  
  setPassword(password: string): void {
    this.password = password;
  }
  
  validate(): boolean {
    return this.id > 0 && this.name.length > 0;
  }
}

let user: User = new User(1, 'Alice', 'alice@example.com');
console.info(`${user.getInfo()}`);
```

**Differences Between Methods and Standalone Functions**

Methods belong to a class and can access instance state and private members through `this`. Standalone functions do not belong to a class and cannot access instance state. Methods also support access modifiers to control visibility.

<!-- @[standalone_function_vs_method](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Methods.ets) -->

``` TypeScript
// Standalone function: does not belong to a class.
function standaloneAdd(a: number, b: number): number {
  return a + b;
}

// Class method: belongs to a class and can access its internal state.
class Accumulator {
  private total: number = 0;
  
  // Method: can access private state.
  add(n: number): void {
    this.total += n;
  }
  
  getTotal(): number {
    return this.total;
  }
  
  // Advantages of methods: encapsulation and state management.
  reset(): void {
    this.total = 0;
  }
}

// Compare the differences.
console.info(`${standaloneAdd(1, 2).toString()}`);  // 3, stateless

let acc: Accumulator = new Accumulator();
acc.add(10);
acc.add(20);
console.info(`${acc.getTotal().toString()}`);  // 30, with state management

// Methods can access private data; functions cannot.
// Standalone functions cannot access acc.total (private).
```

**Reference Semantics of Classes**

Class instances are reference types. Assignment and argument passing transfer references rather than copies: modifying an object through any variable affects all references to that object.

A shallow copy copies only the object's own level: primitive-type properties are copied independently, but reference-type properties still share the same instances with the original object. A deep copy recursively copies nested reference types to make the copy fully independent. Deep copying must be implemented manually.

<!-- @[object_reference_copy](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Classes.ets) -->

``` TypeScript
class CopyPerson {
  public name: string;
  public age: number;
  
  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }
}

let person1: CopyPerson = new CopyPerson('Alice', 25);
let person2: CopyPerson = person1;  // Reference assignment, pointing to the same object.

person2.name = 'Bob';
console.info(`${person1.name}`);  // 'Bob' (person1 is also modified)

// Implement deep copying manually, for example, with a copy method in the class.
class CopyUser {
  public id: number;
  public name: string;
  
  constructor(id: number, name: string) {
    this.id = id;
    this.name = name;
  }
  
  copy(): CopyUser {
    return new CopyUser(this.id, this.name);
  }
}

let user1: CopyUser = new CopyUser(1, 'Alice');
let user2: CopyUser = user1.copy();
user2.name = 'Bob';
console.info(`${user1.name}`);  // 'Alice' (deep copy; modifying user2 does not affect user1)
console.info(`${user2.name}`);  // 'Bob'
```

**Shallow and Deep Copies**

The difference between shallow and deep copies is most apparent when properties are reference types:

<!-- @[shallow_vs_deep_copy](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Classes.ets) -->

``` TypeScript
// Differences between shallow and deep copies for reference-type properties.
class ContactInfo {
  public email: string;
  
  constructor(email: string) {
    this.email = email;
  }
}

class Employee {
  public id: number;
  public contact: ContactInfo;
  
  constructor(id: number, contact: ContactInfo) {
    this.id = id;
    this.contact = contact;
  }
  
  // Shallow copy: contact is still shared with the original object.
  shallowCopy(): Employee {
    return new Employee(this.id, this.contact);
  }
  
  // Deep copy: contact is also copied to a new instance.
  deepCopy(): Employee {
    return new Employee(this.id, new ContactInfo(this.contact.email));
  }
}

let employee1: Employee = new Employee(1, new ContactInfo('alice@example.com'));

// Shallow copy: primitive-type properties are independent; reference-type properties are shared.
let employee2: Employee = employee1.shallowCopy();
employee2.id = 100;
employee2.contact.email = 'bob@example.com';
console.info(`${employee1.id}`);              // 1 (primitive type, independent)
console.info(`${employee1.contact.email}`);   // 'bob@example.com' (reference type, shared)

// Deep copy: nested reference-type properties are also unaffected.
let employee3: Employee = new Employee(2, new ContactInfo('carol@example.com'));
let employee4: Employee = employee3.deepCopy();
employee4.contact.email = 'dave@example.com';
console.info(`${employee3.contact.email}`);   // 'carol@example.com' (reference type, independent)
```

`===` compares whether two references point to the same object, not whether their contents are equal. To compare contents, define a custom comparison method.

<!-- @[object_comparison](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Classes.ets) -->

``` TypeScript
class Point {
  public x: number;
  public y: number;
  
  constructor(x: number, y: number) {
    this.x = x;
    this.y = y;
  }
}

let p1: Point = new Point(1, 2);
let p2: Point = new Point(1, 2);
let p3: Point = p1;

// Reference comparison
console.info(`${p1 === p2}`);  // false (different objects)
console.info(`${p1 === p3}`);  // true (same reference)

// A custom method is required for content comparison.
class PointWithEquals {
  public x: number;
  public y: number;
  
  constructor(x: number, y: number) {
    this.x = x;
    this.y = y;
  }
  
  equals(other: PointWithEquals): boolean {
    return this.x === other.x && this.y === other.y;
  }
}

let pe1: PointWithEquals = new PointWithEquals(1, 2);
let pe2: PointWithEquals = new PointWithEquals(1, 2);

console.info(`${pe1 === pe2}`);      // false
console.info(`${pe1.equals(pe2)}`);  // true
```

**Type Relationships Between Classes**

In TypeScript, type compatibility between classes is based on structural typing (duck typing): classes with the same structure can substitute for each other even without an explicit inheritance relationship. **ArkTS does not support structural typing**, and assignment between classes requires an explicit inheritance or `implements` relationship.

**TypeScript Comparison**

<!-- @[ts_structural_typing](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Classes.ts) -->

``` TypeScript
// TypeScript structural typing, not supported in ArkTS
class TsRelPoint1 {
  public x: number = 0;
  public y: number = 0;
}

class TsRelPoint2 {
  public x: number = 0;
  public y: number = 0;
}

// Structurally identical, mutually assignable (not supported in ArkTS)
let tsRelP1: TsRelPoint1 = new TsRelPoint2();
let tsRelP2: TsRelPoint2 = new TsRelPoint1();
console.info(`${tsRelP1.x}`);
```

**Nested Types**

Neither TypeScript nor ArkTS supports declaring a class inside another class. To group helper types that serve only a particular outer type, declare them alongside the main class at module level and use names that indicate their relationship. If a helper class needs access to an outer class instance's data, pass a reference through its constructor.

<!-- @[nested_type_grouping](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Classes.ets) -->

``` TypeScript
class ProcessorResult {
  public success: boolean = false;
  public data: string = '';
  public error: string = '';

  isSuccess(): boolean {
    return this.success;
  }
}

class NestedDataProcessor {
  process(input: string): ProcessorResult {
    let result: ProcessorResult = new ProcessorResult();
    if (input.length > 0) {
      result.success = true;
      result.data = input.trim();
    } else {
      result.error = 'Empty input';
    }
    return result;
  }
}

let ntProcessor: NestedDataProcessor = new NestedDataProcessor();
let ntResult: ProcessorResult = ntProcessor.process('hello');
console.info(`${ntResult.isSuccess()}`); // true
```

ArkTS does not support class expressions (assigning a class to a variable). Use class declarations instead. For details, see [TypeScript to ArkTS Cookbook](typescript-to-arkts-migration-guide.md#class-literals-are-not-supported).

## Class Properties

Class properties describe object state. Declare them in the form `modifier name: Type = initialValue` and access them through `instance.propertyName`. Properties can be instance or static properties, and support computed, optional, and read-only properties and default values.

### Instance Properties

Each instance owns its instance properties independently. These properties store the object's data values, exist when the instance is created, and are accessed through `instance.propertyName`. They cannot be accessed directly through the class name.

<!-- @[property_definition_basics](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Properties.ets) -->

``` TypeScript
class Person {
  // Property definitions: store data.
  public name: string;         // Name property.
  public age: number;          // Age property.
  public email?: string;       // Optional property
  
  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }
  
  // Properties encapsulate data and provide access to it.
  getInfo(): string {
    return `${this.name}, ${this.age} years old`;
  }
}

let person: Person = new Person('Alice', 25);
console.info(`${person.name}`);  // 'Alice'
console.info(`${person.age.toString()}`);   // 25

// Properties store state.
class Counter {
  public count: number = 0;  // Store the count state.
  
  increment(): void {
    this.count++;  // Manage state through a property.
  }
  
  getCount(): number {
    return this.count;
  }
}

let counter: Counter = new Counter();
counter.increment();
console.info(`${counter.getCount().toString()}`);  // 1
```

### Static Properties

Static properties are declared with `static` and belong to the class rather than its instances. They are created when the class loads, shared by all instances, and accessed through `ClassName.propertyName` without creating an instance. Instance properties, in contrast, require a class instance and exist when it is created, so their access and lifecycle differ. Static properties suit class-level data such as global state. Their lifecycle is tied to the class, and only one copy exists regardless of the number of instances.

<!-- @[instance_vs_static_properties](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Properties.ets) -->

``` TypeScript
class Configuration {
  // Instance property: owned independently by each instance.
  public name: string;
  public value: number;
  
  // Static property: shared by all instances.
  public static version: string = '1.0.0';
  public static instanceCount: number = 0;
  
  constructor(name: string, value: number) {
    this.name = name;
    this.value = value;
    Configuration.instanceCount++;
  }
  
  // Access instance properties in an instance method.
  getInfo(): string {
    return `${this.name}: ${this.value}`;
  }
  
  // Access static properties in a static method.
  static getVersion(): string {
    return Configuration.version;
  }
  
  static getInstanceCount(): number {
    return Configuration.instanceCount;
  }
}

let config1: Configuration = new Configuration('A', 10);
let config2: Configuration = new Configuration('B', 20);

// Instance properties are independent.
console.info(`${config1.name}`);  // 'A'
console.info(`${config2.name}`);  // 'B'

// Static properties are shared.
console.info(`${Configuration.version}`);       // '1.0.0'
console.info(`${Configuration.instanceCount}`); // 2

// Access instance properties through this.
// Access static properties through the class name.
```

A static initialization block (`static { }`) runs once when the class loads. It can encapsulate static initialization logic that requires error handling and directly access private static fields. Alternatively, use a static method to explicitly control initialization timing.

<!-- @[static_block](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Classes.ets) -->

``` TypeScript
class TsStaticConfig {
  private static count: number = 0;

  static {
    try {
      let data: string[] = ['a', 'b', 'c'];
      TsStaticConfig.count = data.length;
    } catch (e) {
      TsStaticConfig.count = 0;
    }
  }
}
```

**Special Static Member Names**: A class is itself a function, so static member names must not conflict with the `Function` prototype. Names such as `name`, `length`, and `call` cannot be used as static property names.

**TypeScript Comparison**

<!-- @[ts_special_static_names](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Methods.ts) -->

``` TypeScript
class TsSsnConfig {
  static version: string = '1.0';

  static name: string = 'Config';  // Compilation error: conflicts with Function.name.
  static length: number = 0;       // Compilation error: conflicts with Function.length.

  static getConfigName(): string {
    return 'Config';
  }
}

console.info(`${TsSsnConfig.version}`);
console.info(`${TsSsnConfig.getConfigName()}`);
```

### Computed Properties

Computed properties are defined through `get`/`set` accessors: `get` defines a read accessor and `set` defines a write accessor. They are accessed like ordinary properties, but methods dynamically evaluate their values and can perform custom logic such as validation on reads and writes.

<!-- @[getter_setter_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Properties.ets) -->

``` TypeScript
class Circle {
  private _radius: number = 0;
  
  // Getter: obtain the computed value.
  get radius(): number {
    return this._radius;
  }
  
  // Setter: set and validate the value.
  set radius(value: number) {
    if (value >= 0) {
      this._radius = value;
    }
  }
  
  // Computed property: calculate from other properties.
  get area(): number {
    return Math.PI * this._radius * this._radius;
  }
  
  get diameter(): number {
    return this._radius * 2;
  }
  
  get circumference(): number {
    return 2 * Math.PI * this._radius;
  }
}

let circle: Circle = new Circle();

// Set through the setter.
circle.radius = 5;
console.info(`${circle.radius}`);      // 5

// Computed properties update automatically.
console.info(`${circle.area}`);        // ~78.54
console.info(`${circle.diameter}`);    // 10
console.info(`${circle.circumference}`); // ~31.42

// The setter performs validation.
circle.radius = -5;  // Invalid; the value is not set.
console.info(`${circle.radius}`);      // 5 (original value retained)
```

A computed property with a getter but no setter is read-only: it can be read but not written. Its value updates automatically when its source properties change.

<!-- @[ts_readonly_computed_properties](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Properties.ts) -->

``` TypeScript
class Rectangle {
  public width: number = 0;
  public height: number = 0;

  // Read-only computed property: getter only.
  get area(): number {
    return this.width * this.height;
  }

  get perimeter(): number {
    return 2 * (this.width + this.height);
  }

  // No setter; area cannot be set directly.
  // set area(value: number) { }  // Not provided.
}

let rect: Rectangle = new Rectangle();
rect.width = 10;
rect.height = 20;

console.info(`${rect.area}`);       // 200
console.info(`${rect.perimeter}`);  // 60

// Computed properties cannot be set.
rect.area = 100;  // Compilation error

// Change source properties to affect the computed property.
rect.width = 5;
console.info(`${rect.area}`);  // 100 (updated automatically)
```

Stored properties allocate fields to hold values. Computed properties do not allocate fields; their getters dynamically evaluate values on each access. Computed properties suit derived data, such as a full name assembled from first and last names or Fahrenheit converted from Celsius.

<!-- @[stored_vs_computed_properties](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Properties.ets) -->

``` TypeScript
class Temperature {
  // Stored property: store the value directly.
  public celsius: number = 0;
  
  // Computed property: calculate from stored properties.
  get fahrenheit(): number {
    return this.celsius * 9 / 5 + 32;
  }
  
  set fahrenheit(value: number) {
    this.celsius = (value - 32) * 5 / 9;
  }
  
  // Stored property: requires storage space.
  // Computed property: requires no storage space and is calculated dynamically.
  
  // Stored property: direct assignment.
  // Computed property: use a getter/setter.
}

let temp: Temperature = new Temperature();

// Set a stored property.
temp.celsius = 25;
console.info(`${temp.celsius}`);      // 25
console.info(`${temp.fahrenheit}`);   // 77

// Set a computed property, affecting stored properties.
temp.fahrenheit = 100;
console.info(`${temp.celsius}`);      // ~37.78
console.info(`${temp.fahrenheit}`);   // 100
```

### Optional Properties

Optional properties are marked with `?` and can remain uninitialized or be assigned later. Their values may be `undefined`. Before use, check for `undefined`, provide a default with `??`, or use optional chaining for safe access.

<!-- @[optional_properties](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Classes.ets) -->

``` TypeScript
class UserProfile {
  public name: string;
  public age?: number;          // Optional property
  public email?: string;
  public bio?: string;
  
  constructor(name: string) {
    this.name = name;
    // Optional properties do not need to be initialized.
  }
  
  setAge(age: number): void {
    this.age = age;
  }
  
  setEmail(email: string): void {
    this.email = email;
  }
  
  getAge(): number {
    return this.age ?? 0;
  }
  
  hasEmail(): boolean {
    return this.email !== undefined;
  }
}

let profile: UserProfile = new UserProfile('Alice');

// age has not been assigned; ?? provides a default value.
console.info(`${profile.getAge()}`);  // 0

profile.setAge(25);
console.info(`${profile.getAge()}`);  // 25

// Check before accessing an optional property.
if (profile.email !== undefined) {
  console.info(`${profile.email}`);
}

// Use optional chaining.
let bioLength: number | undefined = profile.bio?.length;
console.info(`${bioLength}`);  // undefined
```

### Read-Only Properties

Read-only properties are declared with `readonly` and can be assigned only at declaration or in the constructor. They cannot be modified afterward. To make a change, return a new instance instead of modifying the original.

<!-- @[ts_readonly_instance_properties](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Properties.ts) -->

``` TypeScript
class ImmutablePoint {
  // readonly read-only property
  public readonly x: number;
  public readonly y: number;

  constructor(x: number, y: number) {
    this.x = x;  // Assignable in the constructor.
    this.y = y;
  }

  // Read-only property cannot be modified.
  move(dx: number, dy: number): void {
    this.x += dx;  // Compilation error
    this.y += dy;  // Compilation error
  }

  // Return a new instance instead of modifying this one.
  translate(dx: number, dy: number): ImmutablePoint {
    return new ImmutablePoint(this.x + dx, this.y + dy);
  }
}

let point: ImmutablePoint = new ImmutablePoint(10, 20);
console.info(`${point.x}`);  // 10
console.info(`${point.y}`);  // 20

// Read-only property cannot be modified.
point.x = 15;  // Compilation error

// Return a new instance.
let newPoint: ImmutablePoint = point.translate(5, 5);
console.info(`${newPoint.x}`);  // 15
console.info(`${newPoint.y}`);  // 25

// The original instance remains unchanged.
console.info(`${point.x}`);  // 10
```

Combine `readonly` with `static` to define immutable class-level constants.

<!-- @[ts_static_readonly_constants](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Properties.ts) -->

``` TypeScript
// Combine readonly with static.
class AppConfig {
  public static readonly APP_NAME: string = 'MyApp';
  public static readonly VERSION: string = '1.0.0';
}

console.info(`${AppConfig.APP_NAME}`);   // 'MyApp'
console.info(`${AppConfig.VERSION}`);    // '1.0.0'

AppConfig.APP_NAME = 'NewApp';  // Compilation error
```

### Property Default Values

Specify property default values directly at declaration, for example, `public name: string = 'default'`. These preset values prevent `undefined` when no value is provided. There are three initialization options: assignment at declaration for fixed defaults, assignment in the constructor body for parameter-dependent or dynamically calculated values, and deferred assignment to nullable types for values determined only at runtime.

<!-- @[property_initialization_methods](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Properties.ets) -->

``` TypeScript
class User {
  // Initialize at declaration.
  public id: number = 0;
  public name: string = '';
  public active: boolean = true;
  
  // Initialize in the constructor.
  constructor(id?: number, name?: string) {
    if (id !== undefined) {
      this.id = id;
    }
    if (name !== undefined) {
      this.name = name;
    }
  }
  
  // Deferred initialization.
  public email: string | null = null;
  
  setEmail(email: string): void {
    this.email = email;  // Deferred assignment.
  }
}

let user1: User = new User();
console.info(`${user1.id}`);    // 0
console.info(`${user1.name}`);  // ''

let user2: User = new User(1, 'Alice');
console.info(`${user2.id}`);    // 1
console.info(`${user2.name}`);  // 'Alice'

// Deferred initialization.
user2.setEmail('alice@example.com');
console.info(`${user2.email}`);  // 'alice@example.com'
```

## Class Methods

Methods are functions defined in a class that describe object behavior and access instance state through `this`. They can be instance or static methods and support overloading. Parameter features such as optional, default, and rest parameters are the same as for functions. For details, see [Functions](arkts-language-guide-functions.md).

### Instance Methods

Call instance methods through a class instance (`instance.methodName()`). Within the method body, `this` refers to the current instance and can access instance properties and other instance methods.

<!-- @[instance_method_declaration](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Methods.ets) -->

``` TypeScript
class Student {
  public name: string;
  public age: number;
  
  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }
  
  // Declare an instance method.
  study(): void {
    console.info(`${this.name} is studying`);
  }
  
  // Instance method with parameters.
  studyFor(subject: string): void {
    console.info(`${this.name} is studying ${subject}`);
  }
  
  // Instance method with a return value.
  getInfo(): string {
    return `${this.name}, ${this.age} years old`;
  }
  
  // Method with default parameters.
  greet(greeting: string = 'Hello'): string {
    return `${greeting}, I'm ${this.name}`;
  }
}

let student: Student = new Student('Alice', 20);

// Call instance methods.
student.study();               // 'Alice is studying'
student.studyFor('Math');       // 'Alice is studying Math'
console.info(`${student.getInfo()}`); // 'Alice, 20 years old'
console.info(`${student.greet()}`);   // 'Hello, I'm Alice'
console.info(`${student.greet('Hi')}`); // 'Hi, I'm Alice'
```

Returning `this` from an instance method enables method chaining, commonly used in the Builder pattern.

<!-- @[instance_methods](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Classes.ets) -->

``` TypeScript
class Calculator {
  public value: number = 0;
  
  // Instance method
  add(n: number): void {
    this.value += n;
  }
  
  subtract(n: number): void {
    this.value -= n;
  }
  
  multiply(n: number): void {
    this.value *= n;
  }
  
  divide(n: number): void {
    if (n !== 0) {
      this.value /= n;
    }
  }
  
  getValue(): number {
    return this.value;
  }
  
  reset(): void {
    this.value = 0;
  }
}

let calc: Calculator = new Calculator();
calc.add(10);
calc.multiply(2);
console.info(`${calc.getValue().toString()}`);  // 20

// Method chaining (return this)
class Builder {
  private data: string = '';
  
  add(text: string): Builder {
    this.data += text;
    return this;
  }
  
  addLine(text: string): Builder {
    this.data += text + '\n';
    return this;
  }
  
  build(): string {
    return this.data;
  }
}

let result: string = new Builder()
  .add('Hello')
  .add(' ')
  .add('World')
  .build();
console.info(`${result}`);  // 'Hello World'
```

### Static Methods

Static methods are declared with `static` and belong to the class rather than instances. Call them through the class name without instantiating the class. Static methods cannot access instance properties or instance `this`; they can access only static members.

<!-- @[ts_static_methods](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Classes.ts) -->

``` TypeScript
class MathUtils {
  // Static method
  static add(a: number, b: number): number {
    return a + b;
  }
  
  static multiply(a: number, b: number): number {
    return a * b;
  }
  
  static max(a: number, b: number): number {
    return a > b ? a : b;
  }
  
  static min(a: number, b: number): number {
    return a < b ? a : b;
  }
}

// Call a static method by the class name.
console.info(`${MathUtils.add(1, 2)}`);      // 3
console.info(`${MathUtils.multiply(3, 4)}`); // 12
console.info(`${MathUtils.max(5, 10)}`);     // 10

// Creating an instance does not affect static methods.
let utils: MathUtils = new MathUtils();
utils.add(1, 2);  // Compilation error: an instance cannot call a static method.

// A static method cannot access instance properties.
class StaticExample {
  public instanceValue: number = 10;
  public static staticValue: number = 20;
  
  static getStaticValue(): number {
    return StaticExample.staticValue;  // Can access static properties.
  }
  
  static getInstanceValue(): number {
    return this.instanceValue;  // Compilation error: cannot access instance properties.
  }
}
```

Static methods are commonly used for factory methods, the singleton pattern, and utility functions.

<!-- @[static_factory_singleton_utility](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Methods.ets) -->

``` TypeScript
// 1. Factory method.
class User {
  private id: number;
  private name: string;

  private constructor(id: number, name: string) {
    this.id = id;
    this.name = name;
  }
  
  // Static factory method.
  static create(id: number, name: string): User {
    return new User(id, name);
  }
  
  static createGuest(): User {
    return new User(0, 'Guest');
  }
  
  static createAdmin(id: number): User {
    return new User(id, 'Admin');
  }
  
  getInfo(): string {
    return `User ${this.id}: ${this.name}`;
  }
}

let admin: User = User.createAdmin(1);
let guest: User = User.createGuest();
console.info(`${admin.getInfo()}`);   // 'User 1: Admin'
console.info(`${guest.getInfo()}`);   // 'User 0: Guest'

// 2. Singleton pattern.
class Singleton {
  private static instance: Singleton | undefined = undefined;
  
  private constructor() {}
  
  static getInstance(): Singleton {
    if (Singleton.instance === undefined) {
      Singleton.instance = new Singleton();
    }
    return Singleton.instance;
  }
  
  doSomething(): void {
    console.info('Singleton working');
  }
}

let s1: Singleton = Singleton.getInstance();
let s2: Singleton = Singleton.getInstance();
console.info(`${(s1 === s2).toString()}`);  // true, the same instance

// 3. Utility methods.
class ArrayUtils {
  static isEmpty<T>(arr: T[]): boolean {
    return arr.length === 0;
  }
  
  static first<T>(arr: T[]): T | undefined {
    return arr[0];
  }
  
  static last<T>(arr: T[]): T | undefined {
    return arr[arr.length - 1];
  }
  
  static flatten<T>(arr: T[][]): T[] {
    let result: T[] = [];
    for (let sub of arr) {
      for (let item of sub) {
        result.push(item);
      }
    }
    return result;
  }
}
```

### Method Overloading

Method overloading provides multiple type signatures for the same method name and dispatches behavior based on argument types. ArkTS uses multiple overload signatures followed by one implementation signature. Overload signatures apply only at compile time for type checking. The implementation signature is not externally visible; callers can use only declared overload signatures. The implementation signature must be compatible with all overload signatures, and runtime checks such as `typeof` distinguish argument types in the function body. Declare more specific type signatures first.

<!-- @[method_overloading](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Classes.ets) -->

``` TypeScript
class DataProcessor {
  // Method overload signature
  process(data: string): string;
  process(data: number): number;
  process(data: string | number): string | number {
    if (typeof data === 'string') {
      return data.toUpperCase();
    }
    return data * 2;
  }
  
  // Multi-argument overload
  format(value: number): string;
  format(value: number, precision: number): string;
  format(value: number, precision?: number): string {
    if (precision !== undefined) {
      return value.toFixed(precision);
    }
    return value.toString();
  }
}

let processor: DataProcessor = new DataProcessor();

console.info(`${processor.process('hello')}`);  // 'HELLO'
console.info(`${processor.process(5)}`);        // 10

console.info(`${processor.format(3.14159)}`);       // '3.14159'
console.info(`${processor.format(3.14159, 2)}`);    // '3.14'
```

Avoid excessive overload signatures. Use optional parameters, union types, or different method names for different scenarios instead.

<!-- @[overload_alternatives](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Methods.ets) -->

``` TypeScript
class SafeConverter {
  // Use static methods instead of overloading for clarity.
  static toNumberFromString(value: string): number | null {
    let result: number = Number.parseInt(value, 10);
    return Number.isNaN(result) ? null : result;
  }
  
  static toNumberFromNumber(value: number): number {
    return value;
  }
  
  // Alternatively, use union types and type guards.
  convert(value: string | number): number | null {
    if (typeof value === 'string') {
      let result: number = Number.parseInt(value, 10);
      return Number.isNaN(result) ? null : result;
    }
    return value;
  }
  
  // Provide different method names for different scenarios.
  fromString(str: string): number | null {
    let result: number = Number.parseInt(str, 10);
    return Number.isNaN(result) ? null : result;
  }
  
  fromNumber(num: number): number {
    return num;
  }
}

let converter: SafeConverter = new SafeConverter();

console.info(`${SafeConverter.toNumberFromString('123')}`);  // 123
console.info(`${SafeConverter.toNumberFromNumber(456)}`);    // 456

console.info(`${converter.convert('42')}`);        // 42
console.info(`${converter.convert(100)}`);         // 100

console.info(`${converter.fromString('abc')}`);    // null
console.info(`${converter.fromNumber(200)}`);      // 200
```

### Using the this Keyword

The `this` keyword can be used only in instance (non-static) methods of a class. It refers to the object calling the instance method or the object being constructed.

Assigning a class method to a variable and then calling it loses the `this` binding. Calling it directly causes a runtime error.

**TypeScript Comparison**

<!-- @[ts_runtime_this_error](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Classes.ts) -->

``` TypeScript
// TypeScript counterpart, demonstrating the runtime error caused by losing `this`.
class TsThisExample {
  public name: string = 'MyClass';

  getName(): string {
    return this.name;
  }
}

let tsThisEx: TsThisExample = new TsThisExample();
console.info(`${tsThisEx.getName()}`);  // 'MyClass'

let tsThisG = tsThisEx.getName;
tsThisG();  // Runtime error: Cannot read property 'name' of undefined
```

An arrow function property binds `this` when it is created. Each instance has its own function copy, and base class methods defined this way cannot be called through `super`.

<!-- @[arrow_function_this](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Classes.ets) -->

``` TypeScript
class ArrowThisHandler {
  private name: string = 'handler';

  public handle = (): void => {
    console.info(`${this.name}`);
  };
}

let arrowHandler: ArrowThisHandler = new ArrowThisHandler();
let arrowH = arrowHandler.handle;
arrowH();  // handler (this is correctly bound)
```

**this Parameter**: A method can declare a `this` parameter to require the correct context type at compile time. This parameter is erased after compilation and does not affect runtime behavior. ArkTS supports `this` as an annotated parameter name, but not as a type, such as the return type `: this` or parameter type `other: this`.

<!-- @[this_parameter_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Methods.ets) -->

``` TypeScript
class TpThisCounter {
  public count: number = 0;
  increment(this: TpThisCounter): void {
    this.count++;
  }
}

let tpThisCounter: TpThisCounter = new TpThisCounter();
tpThisCounter.increment();
console.info(`${tpThisCounter.count}`); // 1
```

ArkTS imposes the following restrictions on `this`:

- The `this` type is not supported.
- Using `this` in functions or static class methods is not supported.

**TypeScript Comparison**

<!-- @[ts_this_usage_limitation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Methods.ts) -->

``` TypeScript
class TsThisLimitA {
  public n: number = 0;
  f1(arg1: this) {} // Compilation error: the this type is not supported (arkts-no-typing-with-this).
  static f2(arg1: number): void {
    this.n = arg1;  // Compilation error: this is not supported in static methods.
  }
}

function foo(arg1: number) {
  this.n = arg1;    // Compilation error: this is not supported in functions.
}
```

In TypeScript, `this` as a return type (for example, `append(text: string): this`) enables method chaining. ArkTS does not support `this` as a type annotation. Use the explicit class name as the return type to achieve the same chaining behavior.

<!-- @[string_builder_explicit_return](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Classes.ets) -->

``` TypeScript
class StringBuilder {
  public parts: string[] = [];

  append(text: string): StringBuilder {
    this.parts.push(text);
    return this;
  }

  toString(): string {
    return this.parts.join('');
  }
}

let sb: StringBuilder = new StringBuilder();
let sbResult: string = sb.append('Hello').append(', ').append('World').toString();
console.info(`${sbResult}`); // 'Hello, World'
```

> **NOTE**
>
> Using `this` as a parameter type (for example, `sameAs(other: this)`) is also not supported. Use an explicit class name as the parameter type instead.

## Access Control of Classes

Access modifiers control access to class members and protect internal data. `public`, `private`, and `protected` control visibility, while `readonly` controls writability. They can be combined independently for common encapsulation needs: for example, `public readonly` provides external read-only access and `private readonly` provides internal read-only access.

### Access Control Modifiers

`public`, `private`, and `protected` control property visibility outside a class and in subclasses: `public` allows access anywhere, `private` allows access only within the class, and `protected` allows access within the class and its subclasses.

<!-- @[ts_access_modifiers](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Classes.ts) -->

``` TypeScript
class BankAccount {
  // public: accessible from anywhere
  public accountNumber: string;
  
  // private: accessible only within the class
  private balance: number;
  
  // protected: accessible within the class and its child classes
  protected ownerName: string;
  
  constructor(accountNumber: string, ownerName: string) {
    this.accountNumber = accountNumber;
    this.ownerName = ownerName;
    this.balance = 0;
  }
  
  // Public method accesses a private property.
  deposit(amount: number): void {
    if (amount > 0) {
      this.balance += amount;
    }
  }
  
  getBalance(): number {
    return this.balance;
  }
  
  // protected method
  protected updateOwner(name: string): void {
    this.ownerName = name;
  }
}

let account: BankAccount = new BankAccount('123', 'Alice');

// public is accessible.
console.info(`${account.accountNumber}`);

// private is not accessible.
console.info(`${account.balance}`);  // Compilation error

// protected is inaccessible.
console.info(`${account.ownerName}`);  // Compilation error

// Access through a method
account.deposit(100);
console.info(`${account.getBalance()}`);  // 100
```

Methods also support access modifiers. `public` methods form the class's external interface; `private`/`protected` methods are for internal or subclass use only.

<!-- @[ts_method_access_modifiers](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Methods.ts) -->

``` TypeScript
class Service {
  // public: public method.
  public start(): void {
    console.info(`Service started`);
    this.initialize();
  }

  // private: private method, within the class only.
  private initialize(): void {
    console.info(`Initializing...`);
    this.loadConfig();
  }

  // protected: protected method, accessible to subclasses.
  protected loadConfig(): void {
    console.info(`Loading configuration`);
  }

  // Call a private method from a public method.
  public stop(): void {
    this.cleanup();
    console.info(`Service stopped`);
  }

  private cleanup(): void {
    console.info(`Cleaning up resources`);
  }
}

let service: Service = new Service();

// Public methods can be called.
service.start();  // Service started, Initializing..., Loading config
service.stop();   // Cleaning up..., Service stopped

// Private methods cannot be accessed.
service.initialize();  // Compilation error

// Protected methods cannot be accessed.
service.loadConfig();  // Compilation error

// Access protected methods in a subclass.
class CustomService extends Service {
  configure(): void {
    this.loadConfig();  // protected is accessible.
  }
}
```

Modifiers can be used individually or together to control visibility and writability within the class, in subclasses, and outside the class.

<!-- @[ts_access_modifiers_summary](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Classes.ts) -->

``` TypeScript
class Example {
  // public: public, accessible anywhere
  public publicProperty: string = 'public';
  
  // private: private, accessible only inside the class
  private privateProperty: string = 'private';
  
  // protected: protected, accessible in the class and its child classes
  protected protectedProperty: string = 'protected';
  
  // readonly: read-only, cannot be modified after initialization.
  readonly readonlyProperty: string = 'readonly';
  
  // Used in combination.
  private readonly privateReadonly: string = 'private readonly';
  protected readonly protectedReadonly: string = 'protected readonly';
  
  public publicMethod(): void {
    // Can access all properties.
    console.info(`${this.publicProperty}`);
    console.info(`${this.privateProperty}`);
    console.info(`${this.protectedProperty}`);
  }
  
  private privateMethod(): void {
    console.info(`Private method`);
  }
  
  protected protectedMethod(): void {
    console.info(`Protected method`);
  }
}

let example: Example = new Example();

// public is accessible.
console.info(`${example.publicProperty}`);
example.publicMethod();

// private is not accessible.
console.info(`${example.privateProperty}`);  // Compilation error.
example.privateMethod();                // Compilation error.

// protected is inaccessible.
console.info(`${example.protectedProperty}`);  // Compilation error.
example.protectedMethod();                // Compilation error.

// readonly is readable but not writable
console.info(`${example.readonlyProperty}`);
example.readonlyProperty = 'new';  // Compilation error.
```

Modifier scopes are as follows: `public` is visible within the class, in subclasses, and outside the class; `private` is visible only within the class; `protected` is visible within the class and subclasses, but not outside the class.

<!-- @[ts_access_modifiers_inheritance](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Classes.ts) -->

``` TypeScript
class Base {
  public publicValue: number = 1;
  private privateValue: number = 2;
  protected protectedValue: number = 3;
  
  testAccess(): void {
    // All members are accessible within the class.
    console.info(`${this.publicValue}`);
    console.info(`${this.privateValue}`);
    console.info(`${this.protectedValue}`);
  }
}

class Derived extends Base {
  testDerivedAccess(): void {
    // Child Classes can access public and protected members.
    console.info(`${this.publicValue}`);
    console.info(`${this.privateValue}`);  // Compilation error.
    console.info(`${this.protectedValue}`);
  }
}

// External access
let base: Base = new Base();
console.info(`${base.publicValue}`);  // 1 (public accessible)
console.info(`${base.privateValue}`);   // Compilation error
console.info(`${base.protectedValue}`); // Compilation error

let derived: Derived = new Derived();
console.info(`${derived.publicValue}`);  // 1 (public accessible)
```

**ES Private Fields (#field)**: TypeScript supports private fields prefixed with `#` that remain private at runtime. Unlike the `private` keyword, `#field` remains private after compilation. In ArkTS, use the `private` modifier instead. For details, see [TypeScript to ArkTS Cookbook](typescript-to-arkts-migration-guide.md#private-identifiers-are-not-supported).

**TypeScript Comparison**

<!-- @[ts_private_fields](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Classes.ts) -->

``` TypeScript
// TypeScript comparison; in ArkTS, use the private modifier instead.
class TsDog {
  #barkAmount: number = 0;
  public personality: string = 'happy';

  bark(): void {
    this.#barkAmount++;
  }
}
```

In ArkTS, use the `private` modifier.

<!-- @[private_field_alternative](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Classes.ets) -->

``` TypeScript
class PrivateFieldDog {
  private barkAmount: number = 0;
  public personality: string = 'happy';

  bark(): void {
    this.barkAmount++;
  }

  getBarkCount(): number {
    return this.barkAmount;
  }
}

let pfDog: PrivateFieldDog = new PrivateFieldDog();
pfDog.bark();
pfDog.bark();
console.info(`${pfDog.getBarkCount().toString()}`);  // 2
```

`private` provides compile-time checking (soft privacy), whereas `#field` remains private at runtime (hard privacy). ArkTS consistently uses the `private` modifier.

## Class Initialization

Initialization assigns valid initial property values when an object is created, ensuring that it is ready to use. ArkTS provides constructors, property defaults, and object literals for initialization, and the compiler enforces complete initialization.

### Constructors

A constructor is declared with `constructor` and called automatically when `new` creates an instance: memory is allocated, the constructor initializes properties, and an instance reference is returned. Constructors initialize all properties, validate arguments, prepare necessary resources, and set initial state.

<!-- @[constructor_responsibilities](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Initialization.ets) -->

``` TypeScript
class DatabaseConnection {
  private connection: string;
  private connected: boolean;
  private timeout: number;
  
  // Constructor responsibilities.
  constructor(connectionString: string, timeout: number = 5000) {
    // 1. Initialize properties.
    this.connection = connectionString;
    this.timeout = timeout;
    this.connected = false;
    
    // 2. Validate arguments.
    if (connectionString.length === 0) {
      throw new Error('Connection string cannot be empty');
    }
    
    // 3. Prepare resources.
    this.prepareConnection();
  }
  
  private prepareConnection(): void {
    console.info('Preparing connection resources');
  }
  
  connect(): void {
    this.connected = true;
    console.info(`Connected to ${this.connection}`);
  }
  
  disconnect(): void {
    this.connected = false;
    console.info('Disconnected');
  }
}

let db: DatabaseConnection = new DatabaseConnection('localhost:5432', 3000);
db.connect();
```

If no constructor is defined, the compiler generates a default constructor without parameters and initializes properties to their default values.

<!-- @[default_constructor](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Initialization.ets) -->

``` TypeScript
class SimpleClass {
  public value: number = 10;
  public name: string = 'default';
  
  // No constructor: the compiler generates a default constructor.
  // constructor() {}  // Generated automatically.
}

let simple: SimpleClass = new SimpleClass();
console.info(`${simple.value.toString()}`);  // 10
console.info(`${simple.name}`);   // 'default'

class DefaultConstructor {
  public x: number = 0;
  public y: number = 0;
  
  // Explicit constructor without parameters.
  constructor() {
    console.info('Default constructor called');
  }
  
  getValues(): string {
    return `${this.x}, ${this.y}`;
  }
}

let defaultObj: DefaultConstructor = new DefaultConstructor();
console.info(`${defaultObj.getValues()}`);  // '0, 0'

// Default constructor:
// No parameters.
// Automatically initialize properties to default values.
// Generated by the compiler if none is defined.
```

Constructors support overloading: declare multiple constructor signatures with different parameter lists so that objects can be initialized with different argument combinations. The compiler matches a signature based on the supplied arguments, and the implementation signature must be compatible with all overload signatures. Optional parameters and static factory methods are also commonly used to provide multiple creation options.

<!-- @[constructor_overloading](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Initialization.ets) -->

``` TypeScript
class OverloadPoint {
  public x: number;
  public y: number;
  
  // Constructor overload signatures.
  constructor();
  constructor(x: number);
  constructor(x: number, y: number);
  constructor(x?: number, y?: number) {
    this.x = x ?? 0;
    this.y = y ?? 0;
  }
}

let point1: OverloadPoint = new OverloadPoint();
let point2: OverloadPoint = new OverloadPoint(10);
let point3: OverloadPoint = new OverloadPoint(10, 20);

console.info(`${point1.x} ${point1.y}`);  // 0 0
console.info(`${point2.x} ${point2.y}`);  // 10 0
console.info(`${point3.x} ${point3.y}`);  // 10 20

class Color {
  public red: number;
  public green: number;
  public blue: number;
  
  constructor(hex: string);
  constructor(r: number, g: number, b: number);
  constructor(rOrHex: number | string, g?: number, b?: number) {
    if (typeof rOrHex === 'string') {
      // Parse from hexadecimal.
      this.red = Number.parseInt(rOrHex.substring(1, 3), 16);
      this.green = Number.parseInt(rOrHex.substring(3, 5), 16);
      this.blue = Number.parseInt(rOrHex.substring(5, 7), 16);
    } else {
      this.red = rOrHex;
      this.green = g ?? 0;
      this.blue = b ?? 0;
    }
  }
}

let color1: Color = new Color('#FF0000');
let color2: Color = new Color(255, 128, 0);
```

**Parameter Properties**: TypeScript supports access modifiers (`public`, `private`, `protected`, and `readonly`) before constructor parameters, prompting the compiler to declare and assign corresponding properties automatically. **ArkTS does not support parameter property syntax**. Declare properties explicitly and assign them in the constructor.

**TypeScript Comparison**

<!-- @[ts_parameter_properties](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Classes.ts) -->

``` TypeScript
// TypeScript syntax; ArkTS does not support constructor parameter properties
class TsPoint {
  constructor(public x: number, public y: number) {}
}

let tsPt: TsPoint = new TsPoint(3, 4);
console.info(`${tsPt.x}, ${tsPt.y}`); // 3, 4
```

ArkTS alternative: explicitly declare the property and assign it in the constructor.

<!-- @[explicit_property_declaration](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Classes.ets) -->

``` TypeScript
class ExplicitPoint {
  public x: number;
  public y: number;

  constructor(x: number, y: number) {
    this.x = x;
    this.y = y;
  }
}

let epPoint: ExplicitPoint = new ExplicitPoint(3, 4);
console.info(`${epPoint.x}, ${epPoint.y}`); // 3, 4
```

**Static factory methods** use named methods to express different construction intents. They can simplify parameters, provide defaults, and create objects for specific scenarios. ArkTS does not support `this()` calls (calling another constructor of the same class from a constructor). Use static factory methods instead.

<!-- @[static_factory_methods](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Classes.ets) -->

``` TypeScript
class ColorValue {
  public red: number;
  public green: number;
  public blue: number;

  constructor(red: number, green: number, blue: number) {
    this.red = red;
    this.green = green;
    this.blue = blue;
  }

  static fromRGB(r: number, g: number, b: number): ColorValue {
    return new ColorValue(r, g, b);
  }

  static fromHex(hex: string): ColorValue {
    let r: number = Number.parseInt(hex.substring(1, 3), 16);
    let g: number = Number.parseInt(hex.substring(3, 5), 16);
    let b: number = Number.parseInt(hex.substring(5, 7), 16);
    return new ColorValue(r, g, b);
  }

  static fromName(name: string): ColorValue {
    switch (name) {
      case 'red':
        return new ColorValue(255, 0, 0);
      case 'green':
        return new ColorValue(0, 255, 0);
      case 'blue':
        return new ColorValue(0, 0, 255);
      default:
        return new ColorValue(0, 0, 0);
    }
  }
}

let cvColor1: ColorValue = ColorValue.fromRGB(255, 128, 0);
let cvColor2: ColorValue = ColorValue.fromHex('#FF8000');
let cvColor3: ColorValue = ColorValue.fromName('red');
```

Constructors also support access modifiers. A `private` constructor prevents direct external instantiation and is often combined with static factory methods for patterns such as singletons. A `protected` constructor allows instantiation only within the class and subclasses (through `super()` in subclass constructors), and is commonly used for base classes intended to be used through subclasses.

<!-- @[private_constructor_with_factory](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Initialization.ets) -->

``` TypeScript
class FactoryConfiguration {
  public apiUrl: string;
  public timeout: number;
  public debug: boolean;
  
  private constructor(apiUrl: string, timeout: number, debug: boolean) {
    this.apiUrl = apiUrl;
    this.timeout = timeout;
    this.debug = debug;
  }
  
  // Use static factory methods instead of constructor overloading.
  static createDefault(): FactoryConfiguration {
    return new FactoryConfiguration('EXAMPLE_API_URL', 5000, false);
  }
  
  static createWithUrl(apiUrl: string): FactoryConfiguration {
    // Use the default configuration and modify some parameters.
    let factoryDefaultConfig: FactoryConfiguration = FactoryConfiguration.createDefault();
    return new FactoryConfiguration(apiUrl, factoryDefaultConfig.timeout, factoryDefaultConfig.debug);
  }
  
  static createDebug(): FactoryConfiguration {
    return new FactoryConfiguration('EXAMPLE_API_URL', 5000, true);
  }
  
  static copy(config: FactoryConfiguration): FactoryConfiguration {
    return new FactoryConfiguration(config.apiUrl, config.timeout, config.debug);
  }
}

let factoryDefaultConfig: FactoryConfiguration = FactoryConfiguration.createDefault();
let factoryUrlConfig: FactoryConfiguration = FactoryConfiguration.createWithUrl('EXAMPLE_API_URL');
let debugConfig: FactoryConfiguration = FactoryConfiguration.createDebug();
let copiedConfig: FactoryConfiguration = FactoryConfiguration.copy(factoryDefaultConfig);
```

**Initialization order**: When both a base class and a derived class initialize fields, the order is: base class fields, base class constructor, derived class fields, then derived class constructor. The base class constructor still sees its own field values because derived fields are initialized afterward. A static initialization block (`static { }`) runs when the class first loads, before any instance field initialization or constructor calls. Static fields are initialized in declaration order, with static initialization blocks executed in sequence among them.

<!-- @[init_order](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Initialization.ets) -->

``` TypeScript
class IoBase {
  public static baseStatic: number = 10;
  public name: string = 'base';

  static {
    console.info('Base static block');
  }

  constructor() {
    console.info(`Base constructor: name = ${this.name}`);
  }
}

class IoDerived extends IoBase {
  public static derivedStatic: number = 20;
  public name: string = 'derived';

  static {
    console.info('Derived static block');
  }

  constructor() {
    super();
    console.info(`Derived constructor: name = ${this.name}`);
  }
}

let ioD: IoDerived = new IoDerived();
// Output:
// Base static block (runs when the class loads, before instance creation)
// Derived static block
// Base constructor: name = base (derived fields are not yet initialized)
// Derived constructor: name = derived
```

A subclass constructor must call the parent constructor through `super()` to initialize parent properties first. For details, see [Using the super Keyword](#using-the-super-keyword).

### Object Literals

Object literals suit simple, one-off data organization. ArkTS requires an explicit type annotation (class or interface) for an object literal. The compiler checks properties against that type: all required members must be present with matching types, and extra properties are rejected. A class with `private` properties cannot be initialized with an object literal; use a constructor instead.

Choose a class to encapsulate data and its operations when reuse and inheritance are needed, an interface to describe only a data structure's shape, and an object literal for simple, one-off data organization.

<!-- @[class_vs_interface](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Classes.ets) -->

``` TypeScript
// Use a class: for scenarios that require encapsulating data and behavior.
class Order {
  public id: number;
  public items: string[];
  public total: number;
  
  constructor(id: number) {
    this.id = id;
    this.items = [];
    this.total = 0;
  }
  
  addItem(item: string, price: number): void {
    this.items.push(item);
    this.total += price;
  }
  
  removeItem(item: string, price: number): void {
    let index: number = this.items.indexOf(item);
    if (index >= 0) {
      this.items.splice(index, 1);
      this.total -= price;
    }
  }
  
  getTotal(): number {
    return this.total;
  }
}

// Use an interface: for scenarios that only require a data structure.
interface Product {
  id: number;
  name: string;
  price: number;
}

let product: Product = { id: 1, name: 'Item', price: 100 };

// Class vs. object literal
// Class: reusable, with methods, and inheritable.
// Object literal: simple data for one-time use.
```

For details about object literals, see [Interfaces](arkts-language-guide-interfaces.md) and [Object Literal Must Correspond to Some Explicitly Declared Class or Interface](typescript-to-arkts-migration-guide.md#object-literal-must-correspond-to-some-explicitly-declared-class-or-interface).

### Uninitialized Property Checks

The ArkTS compiler enforces property initialization checks, equivalent to TypeScript's `strictPropertyInitialization` option but not disableable in ArkTS. All non-optional properties must be assigned at declaration or in the constructor; otherwise, compilation fails. Optional properties (`?`) do not require initialization.

**TypeScript Comparison**

<!-- @[ts_required_properties_initialization](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Initialization.ts) -->

``` TypeScript
class StrictInitialization {
  // Required properties: must be initialized.
  public name: string;  // Compilation error: not initialized.
  public age: number;   // Compilation error: not initialized.
  
  constructor() {
    // name and age are not initialized.
    // TypeScript reports a compilation error (TS2564).
  }
  
  // Correct approach: initialize all properties.
  correctConstructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }
}

class ProperInitialization {
  // Initialize at declaration.
  public name: string = '';
  public age: number = 0;
  
  constructor() {
    // Properties are initialized.
  }
}

class OptionalInitialization {
  // Optional properties: initialization is optional.
  public name?: string;
  public age?: number;
  
  constructor() {
    // Optional properties may remain uninitialized.
  }
  
  initialize(name: string, age: number): void {
    this.name = name;
    this.age = age;
  }
}
```

Avoid `undefined` exceptions by ensuring properties have values and using safe access techniques such as nullish coalescing (`??`) and optional chaining (`?.`).

<!-- @[safe_initialization_techniques](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Initialization.ets) -->

``` TypeScript
class SafeInitialization {
  public name: string;
  public age: number;
  public email?: string;
  
  constructor(name: string, age: number) {
    // Ensure required properties are initialized.
    this.name = name ?? 'default';
    this.age = age ?? 0;
    
    // Handle optional properties carefully.
    if (this.email === undefined) {
      console.info('Email not initialized');
    }
  }
  
  // Safe access techniques.
  getEmail(): string {
    return this.email ?? '';
  }
  
  hasEmail(): boolean {
    return this.email !== undefined && this.email.length > 0;
  }
  
  safeProcess(): void {
    // Check before accessing.
    if (this.name !== undefined) {
      console.info(`${this.name}`);
    }
    
    // Use nullish coalescing.
    let safeAge: number = this.age ?? 0;
    
    // Use optional chaining for object properties.
    let emailLength: number | undefined = this.email?.length;
  }
}
```

## Class Inheritance

With `extends`, a subclass inherits its parent's properties and methods, calls `super()` in its constructor to reuse parent initialization, and can override or add methods to extend behavior. The base (parent) class provides common members for reuse, while the derived (child) class specializes and extends them. ArkTS supports only single inheritance: a subclass can `extends` only one parent class.

Inheritance reduces duplicate code through member reuse, improves maintainability by propagating parent changes, enables polymorphism through method overriding, and establishes a clear type hierarchy.

<!-- @[basic_inheritance_example](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Inheritance.ets) -->

``` TypeScript
// Parent (base) class.
class Animal {
  public name: string;
  
  constructor(name: string) {
    this.name = name;
  }
  
  speak(): void {
    console.info(`${this.name} makes a sound`);
  }
  
  move(): void {
    console.info(`${this.name} moves`);
  }
}

// Child (derived) class inherits the parent class.
class Dog extends Animal {
  public breed: string;
  
  constructor(name: string, breed: string) {
    super(name);  // Call the parent constructor.
    this.breed = breed;
  }
  
  // Inherit a parent method, which can be overridden.
  speak(): void {
    console.info(`${this.name} barks`);
  }
  
  // Add a method.
  fetch(): void {
    console.info(`${this.name} fetches the ball`);
  }
}

let dog: Dog = new Dog('Max', 'Labrador');
dog.speak();   // 'Max barks' (overridden method)
dog.move();    // 'Max moves' (inherited method)
dog.fetch();   // 'Max fetches the ball' (new method)
```

Reusing parent properties and methods through inheritance avoids duplicating the same logic across subclasses.

<!-- @[inheritance_code_reuse](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Inheritance.ets) -->

``` TypeScript
// Without inheritance: duplicate code.
class DogWithoutInheritance {
  public name: string;
  public age: number;
  
  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }
  
  eat(): void {
    console.info(`${this.name} is eating`);
  }
  
  sleep(): void {
    console.info(`${this.name} is sleeping`);
  }
  
  bark(): void {
    console.info(`${this.name} is barking`);
  }
}

class CatWithoutInheritance {
  public name: string;
  public age: number;
  
  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }
  
  eat(): void {
    console.info(`${this.name} is eating`);  // Duplicate code.
  }
  
  sleep(): void {
    console.info(`${this.name} is sleeping`);  // Duplicate code.
  }
  
  meow(): void {
    console.info(`${this.name} is meowing`);
  }
}

// With inheritance: code reuse.
class ReuseAnimal {
  public name: string;
  public age: number;
  
  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }
  
  // Common methods: reused by subclasses.
  eat(): void {
    console.info(`${this.name} is eating`);
  }
  
  sleep(): void {
    console.info(`${this.name} is sleeping`);
  }
}

class ReuseDog extends ReuseAnimal {
  constructor(name: string, age: number) {
    super(name, age);
  }
  
  // Subclass-specific method.
  bark(): void {
    console.info(`${this.name} is barking`);
  }
}

class Cat extends ReuseAnimal {
  constructor(name: string, age: number) {
    super(name, age);
  }
  
  // Subclass-specific method.
  meow(): void {
    console.info(`${this.name} is meowing`);
  }
}

let reuseDog: ReuseDog = new ReuseDog('Max', 3);
let cat: Cat = new Cat('Whiskers', 2);

reuseDog.eat();    // Reuse a parent method.
reuseDog.sleep();  // Reuse a parent method.
reuseDog.bark();   // Subclass-specific method.

cat.eat();    // Reuse a parent method.
cat.sleep();  // Reuse a parent method.
cat.meow();   // Subclass-specific method.
```

An empty subclass adds no new members. It is commonly used for type tagging (runtime distinction through `instanceof`) and reserving an inheritance point for future extensions. It does not need an explicit constructor: creating an instance implicitly calls the parent constructor.

<!-- @[empty_child_class](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Inheritance.ets) -->

``` TypeScript
class Base {
  public value: number = 10;
  
  getValue(): number {
    return this.value;
  }
  
  increment(): void {
    this.value++;
  }
}

// Empty subclass: no new properties or methods.
class EmptyChild extends Base {
  // An empty subclass inherits all parent functionality.
}

let empty: EmptyChild = new EmptyChild();

// An empty subclass fully inherits its parent.
console.info(`${empty.getValue()}`);  // 10
empty.increment();
console.info(`${empty.getValue()}`);  // 11

// Uses of empty subclasses:
// 1. Type tagging: distinguish categories.
class User {
  public name: string;
  constructor(name: string) {
    this.name = name;
  }
}

class RegularUser extends User {}
class PremiumUser extends User {}

let regular: RegularUser = new RegularUser('Bob');
let premium: PremiumUser = new PremiumUser('Alice');

// Distinguish user categories by type.
function getServiceLevel(user: User): string {
  if (user instanceof PremiumUser) {
    return 'Premium service';
  }
  return 'Regular service';
}

console.info(`${getServiceLevel(regular)}`);   // 'Regular service'
console.info(`${getServiceLevel(premium)}`);   // 'Premium service'

// 2. Reserve for future extensions.
class FutureFeature extends Base {
  // Reserved subclass; functionality can be added later.
}
```

**Member inheritance rules**: A subclass automatically inherits its parent's `public` and `protected` members. It cannot inherit or directly access `private` members, but can use them indirectly through `public` methods provided by the parent.

<!-- @[ts_access_modifier_inheritance](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Inheritance.ts) -->

``` TypeScript
class Parent {
  // Instance property.
  public publicValue: string = 'public';
  protected protectedValue: string = 'protected';

  // Instance method
  public publicMethod(): void {
    console.info(`Public method`);
  }

  protected protectedMethod(): void {
    console.info(`Protected method`);
  }

  private privateMethod(): void {
    console.info(`Private method`);
  }

  // Public method that accesses a private method.
  callPrivate(): void {
    this.privateMethod();
  }
}

class AccessChildTest extends Parent {
  // Inherit public properties and methods.
  testPublic(): void {
    console.info(`${this.publicValue}`);    // Accessible.
    this.publicMethod();               // Accessible.
  }

  // Inherit protected properties and methods.
  testProtected(): void {
    console.info(`${this.protectedValue}`); // Accessible.
    this.protectedMethod();            // Accessible.
  }

  // Cannot inherit private properties and methods.
  testPrivate(): void {
    // this.privateMethod();  // Compilation error.
    this.callPrivate();       // Access through a public method.
  }
}

let accessChild: AccessChildTest = new AccessChildTest();

accessChild.testPublic();     // 'public', 'Public method'
accessChild.testProtected();  // 'protected', 'Protected method'
accessChild.testPrivate();    // 'Private method'
```

Static properties and methods are also inherited by subclasses and can be accessed through the subclass name.

<!-- @[static_member_inheritance](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Inheritance.ets) -->

``` TypeScript
class MemberBase {
  // Static property.
  public static staticValue: number = 100;
  
  // Static method
  public static staticMethod(): void {
    console.info('Static method');
  }
  
  public static getStaticValue(): number {
    return MemberBase.staticValue;
  }
}

class Derived extends MemberBase {
  // Inherit a static method.
  callStaticMethod(): void {
    MemberBase.staticMethod();    // Call through the parent class name.
    Derived.staticMethod(); // Call through the subclass name (inherited).
  }
  
  // Inherit a static property.
  getInheritedStaticValue(): number {
    return Derived.getStaticValue();  // Inherited static method.
  }
  
  // Subclass static method.
  static childStaticMethod(): void {
    console.info('Child static method');
    Derived.staticMethod();  // Call an inherited static method.
  }
}

// Call a static method by the class name.
MemberBase.staticMethod();           // 'Static method'
Derived.staticMethod();        // 'Static method' (inherited)
Derived.childStaticMethod();   // 'Child static method', 'Static method'

console.info(`${MemberBase.staticValue}`);       // 100
console.info(`${Derived.staticValue}`);    // 100 (inherited)

let derived: Derived = new Derived();
derived.callStaticMethod();           // 'Static method', 'Static method'
console.info(`${derived.getInheritedStaticValue()}`);  // 100

// Static member inheritance rules:
// Access static properties and methods through the class name.
// Subclasses inherit their parent's static members.
// Subclasses can add their own static members.
```

The same applies to properties: a subclass inherits its parent's `public` and `protected` properties and can declare same-name properties to override (hide) them, but cannot change parent members' access levels.

<!-- @[ts_property_inheritance](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Properties.ts) -->

``` TypeScript
class Parent {
  public publicProp: string = 'public';
  protected protectedProp: string = 'protected';
  private privateProp: string = 'private';

  getPrivateProp(): string {
    return this.privateProp;
  }
}

class Child extends Parent {
  // Add a property.
  public childProp: string = 'child';

  // Inherit a public property.
  getPublicFromParent(): string {
    return this.publicProp;  // Accessible.
  }

  // Inherit a protected property.
  getProtectedFromParent(): string {
    return this.protectedProp;  // Accessible.
  }

  // Cannot inherit a private property.
  getPrivateFromParent(): string {
    return this.privateProp;  // Compilation error
  }

  // Access a private property through the parent's public method.
  getParentPrivate(): string {
    return this.getPrivateProp();  // Accessible.
  }

  // Override (hide) a parent property.
  public publicProp: string = 'child override';

  testOverride(): void {
    console.info(`${this.publicProp}`);  // 'child override'
  }
}

let child: Child = new Child();

console.info(`${child.publicProp}`);           // 'child override'
console.info(`${child.getProtectedFromParent()}`); // 'protected' (inherited)
console.info(`${child.childProp}`);            // 'child'
console.info(`${child.getParentPrivate()}`);   // 'private'

// Property inheritance summary:
// public: fully inherited and overridable.
// protected: inherited and accessible to subclasses.
// private: not inherited or directly accessible to subclasses.
```

**Type-only field declarations with declare**: When redeclaring an inherited field with a more precise type in a subclass, use `declare` to avoid overwriting the parent value at runtime. Without `declare`, the subclass field initializer runs during construction and overwrites the value set by the parent constructor, potentially causing data loss or type inconsistency. A `declare` field generates no runtime code and only ensures type correctness.

<!-- @[declare_field](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Properties.ets) -->

``` TypeScript
interface DclAnimal {
  dateOfBirth: Date;
}

interface DclDog extends DclAnimal {
  breed: string;
}

class DclAnimalHouse {
  public resident: DclAnimal;

  constructor(animal: DclAnimal) {
    this.resident = animal;
  }
}

class DclDogHouse extends DclAnimalHouse {
  // declare: generate no runtime code; refine the type only.
  public declare resident: DclDog;

  constructor(dog: DclDog) {
    super(dog);
  }
}

let dclDog: DclDog = { dateOfBirth: new Date(), breed: 'Labrador' };
let dclHouse: DclDogHouse = new DclDogHouse(dclDog);
console.info(`${dclHouse.resident.breed}`);  // 'Labrador'
```

**Inheritance chains and multilevel inheritance**: Inheritance can form multiple levels, such as `GrandParent -> Parent -> Child`, with subclasses inheriting members along the ancestor chain. This propagates code reuse across levels, but excessive depth makes code harder to understand and increases member lookup costs. Keep hierarchies to no more than three levels; consider composition instead of deep inheritance for complex scenarios.

<!-- @[multi_level_inheritance](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Inheritance.ets) -->

``` TypeScript
// Inheritance hierarchy: multiple levels.
class GrandParent {
  methodGrandParent(): void {
    console.info('GrandParent method');
  }
}

class MultiLevelParent extends GrandParent {
  methodParent(): void {
    console.info('MultiLevelParent method');
  }
  
  methodGrandParent(): void {
    console.info('MultiLevelParent overrides GrandParent');
    super.methodGrandParent();  // Call the parent class method.
  }
}

class MultiLevelChild extends MultiLevelParent {
  methodChild(): void {
    console.info('MultiLevelChild method');
  }
  
  methodParent(): void {
    console.info('MultiLevelChild overrides MultiLevelParent');
    super.methodParent();  // Call the parent class method.
  }
}

let multiLevelChild: MultiLevelChild = new MultiLevelChild();

multiLevelChild.methodChild();           // 'MultiLevelChild method'
multiLevelChild.methodParent();          // 'MultiLevelChild overrides MultiLevelParent', 'MultiLevelParent method'
multiLevelChild.methodGrandParent();     // 'MultiLevelParent overrides GrandParent', 'GrandParent method'

// Inheritance chain lookup: from child to parent.
// MultiLevelChild.methodChild() -> MultiLevelChild itself
// MultiLevelChild.methodParent() -> MultiLevelChild override -> MultiLevelParent method
// MultiLevelChild.methodGrandParent() -> MultiLevelParent override -> GrandParent method

// Limit inheritance depth.
// Recommended: no more than three inheritance levels.
// Counterexample: excessive inheritance depth increases complexity.
```

**Prototype chain**: The prototype chain underlies class inheritance. The `prototype` object stores methods shared by all instances. When accessing an instance member, the engine searches upward from the instance itself, then the parent and grandparent classes until a match is found. Same-name subclass members override parent members. ArkTS automatically maintains the prototype chain through `class extends` and does not support direct manipulation of `prototype`. For details, see [TypeScript to ArkTS Cookbook](typescript-to-arkts-migration-guide.md#prototype-assignment-is-not-supported).

<!-- @[prototype_chain](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Classes.ets) -->

``` TypeScript
class PcGrandParent {
  methodA(): void {
    console.info('GrandParent A');
  }
}

class PcParent extends PcGrandParent {
  methodB(): void {
    console.info('Parent B');
  }
}

class PcChild extends PcParent {
  methodC(): void {
    console.info('Child C');
  }
}

let pcChild: PcChild = new PcChild();

// Prototype chain lookup
pcChild.methodA();  // GrandParent (inherited)
pcChild.methodB();  // Parent (inherited)
pcChild.methodC();  // Child (itself)

// Method overriding
class PcParent2 {
  method(): void {
    console.info('Parent method');
  }
}

class PcChild2 extends PcParent2 {
  method(): void {
    console.info('Child method');
    super.method();
  }
}

let pcChild2: PcChild2 = new PcChild2();
pcChild2.method();
```

### Using the super Keyword

A subclass constructor must call the parent constructor through `super()` to initialize the parent part before initializing its own properties. Call `super()` in the constructor body before any access to `this`; statements that do not use `this` may precede it. Arguments must match the parent constructor signature. If no subclass constructor is defined, the compiler generates code to call the parent constructor.

**TypeScript Comparison**

<!-- @[ts_super_call_rules](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Initialization.ts) -->

``` TypeScript
class Vehicle {
  public brand: string;

  constructor(brand: string) {
    this.brand = brand;
    console.info(`Vehicle constructor`);
  }
}

class Car extends Vehicle {
  public model: string;

  constructor(brand: string, model: string) {
    super(brand);  // Call super() first.
    this.model = model;
    console.info(`Car constructor`);
  }

  getInfo(): string {
    return `${this.brand} ${this.model}`;
  }
}

let car: Car = new Car('Toyota', 'Camry');
// Output: 'Vehicle constructor', 'Car constructor'

// super() rules:
// 1. A subclass constructor must call super().
// 2. super() must be on the first line.
// 3. super() arguments must match the parent constructor.

class InvalidChild extends Vehicle {
  public model: string;

  constructor(brand: string, model: string) {
    this.model = model;  // Compilation error: super() has not been called.

    super(brand);  // Must precede access to this.

    this.model = model;  // Correct.
  }
}
```

A subclass constructor forwards arguments to its parent constructor through `super(...)`. It can also apply defaults or convert types before passing the arguments.

<!-- @[passing_parameters_to_super](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Initialization.ets) -->

``` TypeScript
class MultiParamParent {
  public name: string;
  public age: number;
  public email: string;
  
  constructor(name: string, age: number, email: string) {
    this.name = name;
    this.age = age;
    this.email = email;
  }
}

class MultiParamChild extends MultiParamParent {
  public phone: string;
  
  constructor(name: string, age: number, email: string, phone: string) {
    super(name, age, email);  // Pass all parent arguments.
    this.phone = phone;
  }
  
  getInfo(): string {
    return `${this.name}, ${this.age}, ${this.email}, ${this.phone}`;
  }
}

let superChild: MultiParamChild = new MultiParamChild('Alice', 25, 'alice@example.com', '123-456');

// Argument handling:
class FlexibleParent {
  public value: number;
  
  constructor(value: number = 10) {
    this.value = value;
  }
}

class FlexibleChild extends FlexibleParent {
  public extra: number;
  
  constructor(value?: number, extra?: number) {
    super(value ?? 10);  // Pass the processed argument.
    this.extra = extra ?? 0;
  }
}

// Convert an argument before passing it.
class TransformedParent {
  public id: number;
  
  constructor(id: number) {
    this.id = id;
  }
}

class TransformedChild extends TransformedParent {
  public name: string;
  
  constructor(idString: string, name: string) {
    let id: number = Number.parseInt(idString, 10);
    super(id);  // Pass the converted argument.
    this.name = name;
  }
}
```

In an instance method, call a parent instance method through `super.methodName()`. This commonly reuses parent logic in an overridden method before adding subclass-specific behavior.

<!-- @[super_keyword](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Classes.ets) -->

``` TypeScript
class Parent {
  greet(): string {
    return 'Hello from Parent';
  }
  
  process(): void {
    console.info('Parent processing');
  }
}

class Child extends Parent {
  greet(): string {
    return 'Hello from Child';
  }
  
  greetWithParent(): string {
    return `${super.greet()} and ${this.greet()}`;
  }
  
  process(): void {
    super.process();  // Call the parent class method.
    console.info('Child processing');
  }
}

let child: Child = new Child();
console.info(`${child.greetWithParent()}`);  
// 'Hello from Parent and Hello from Child'

child.process();
// Output: Parent processing, Child processing

// super in the constructor
class KwBase {
  protected value: number;
  
  constructor(value: number) {
    this.value = value;
  }
}

class Extended extends KwBase {
  public multiplier: number;
  
  constructor(value: number, multiplier: number) {
    super(value);  // Call super first.
    this.multiplier = multiplier;
  }
  
  getCalculated(): number {
    return this.value * this.multiplier;
  }
}
```

In subclass static methods, access parent static members through `super.staticMethodName()` or the parent class name.

<!-- @[static_method_call](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Inheritance.ets) -->

``` TypeScript
class StaticBase {
  public static baseValue: number = 10;

  static baseMethod(): void {
    console.info(`Base static method`);
  }

  static getValue(): number {
    return StaticBase.baseValue;
  }
}

class StaticChild extends StaticBase {
  public static childValue: number = 20;

  // Call a parent static method from a subclass static method.
  static combinedMethod(): void {
    StaticBase.baseMethod();   // Call through the parent class name.
    StaticChild.baseMethod();  // Call through the subclass name (inherited).
  }

  // Access a parent static property from a subclass static method.
  static getTotalValue(): number {
    return StaticBase.baseValue + StaticChild.childValue;
  }

  // Call an inherited static method.
  static getInheritedValue(): number {
    return StaticChild.getValue();  // Inherited static method.
  }

  // Call a parent static method through super in a static method.
  static callViaSuper(): void {
    super.baseMethod();  // Call a parent static method through super.
  }
}

StaticChild.combinedMethod();       // 'Base static method', 'Base static method'
console.info(`${StaticChild.getTotalValue()}`);       // 30
console.info(`${StaticChild.getInheritedValue()}`);   // 10
StaticChild.callViaSuper();         // 'Base static method'

// Static method call rules:
// Call static members through the class name.
// Call inherited static members through the subclass name.
// Call parent static methods through super.
```

Restrictions on `super`: call `super()` before any access to `this`; do not access parent instance properties directly through `super` (use `this` instead); use `super` only for the calls described above.

**TypeScript Comparison**

<!-- @[ts_super_usage_limitation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Inheritance.ts) -->

``` TypeScript
class SuperBase {
  public value: number = 10;

  method(): void {
    console.info(`Base method`);
  }

  static staticMethod(): void {
    console.info(`Base static method`);
  }
}

class SuperChild extends SuperBase {
  public value: number = 20;

  method(): void {
    // Call a parent method through super.
    super.method();  // Correct.

    // super cannot directly access parent instance properties.
    console.info(`${super.value}`);  // Compilation error: use this, not super, to access parent instance properties.

    // Use this or the class name to access properties.
    console.info(`${this.value}`);          // 20 (subclass property)
    console.info(`${SuperChild.prototype.value}`); // Counterexample: parent property.
  }

  anotherMethod(): void {
    // super can only call methods.
    super.method();

    // It cannot be used in other scenarios.
    let base: SuperBase = super;  // Compilation error
    return super;  // Compilation error
  }

  static childStaticMethod(): void {
    // Use super in a static method to call a parent static method.
    super.staticMethod();

    // The class name can also be used.
    SuperBase.staticMethod();
  }

  constructor() {
    super();  // Use super() in the constructor to call the parent constructor.
  }
}
```

### override Keyword and Method Overriding

Method overriding redefines a parent's same-name method in a subclass to implement polymorphism. Signatures must match: the method name, parameter types, and parameter count must be the same, and return types must be identical or compatible. Access must not be more restrictive: an overridden `public` method must remain `public`; an overridden `protected` method may remain `protected` or become `public`; `private` methods cannot be overridden.

The `override` keyword marks an overriding method so that the compiler reports an error if the parent method is renamed or removed, preventing accidental disconnection. In ArkTS, `override` is optional, but explicit annotation is recommended so that the compiler checks for a same-name parent method.

<!-- @[method_override](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Classes.ets) -->

``` TypeScript
class Base {
  method(): void {
    console.info('Base method');
  }
}

class Derived extends Base {
  // TypeScript uses override to mark the method (optional)
  method(): void {
    console.info('Derived method');
  }
}

let derived: Derived = new Derived();
derived.method();  // 'Derived method'

// Override a method with a return value.
class OverrideCalculator {
  calculate(a: number, b: number): number {
    return a + b;
  }
}

class AdvancedCalculator extends OverrideCalculator {
  calculate(a: number, b: number): number {
    return a * b;  // Change the calculation logic
  }
}

let overrideCalc: OverrideCalculator = new AdvancedCalculator();
console.info(`${overrideCalc.calculate(3, 4)}`);  // 12

// Keep signatures consistent when overriding.
class Logger {
  log(message: string): void {
    console.info(`${message}`);
  }
}

class FileLogger extends Logger {
  log(message: string): void {  // The parameter and return types must remain consistent.
    // Write to a file.
    console.info(`[File] ${message}`);
  }
}
```

Overridden method parameters and return values must match the parent method to ensure type safety.

**TypeScript Comparison**

<!-- @[ts_method_signature_match](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Inheritance.ts) -->

``` TypeScript
class NumberProcessor {
  process(value: number): number {
    return value * 2;
  }

  convert(input: string): number {
    return Number.parseInt(input, 10);
  }
}

class AdvancedProcessor extends NumberProcessor {
  // Parameters and return values must match exactly.
  process(value: number): number {
    return value * 3;  // Same return type.
  }

  // Compatible return value: the subclass return type can be a subtype of the parent's return type.
  convert(input: string): number {
    let result: number = super.convert(input);
    return result * 10;
  }

  // Parameter types cannot be changed.
  process(value: string): number {}  // Compilation error

  // The parameter count cannot be changed.
  process(value: number, extra: number): number {}  // Compilation error

  // The return type cannot be changed to an incompatible type.
  process(value: number): string {}  // Compilation error
}

let processor: AdvancedProcessor = new AdvancedProcessor();

console.info(`${processor.process(5).toString()}`);      // 15
console.info(`${processor.convert('10').toString()}`);   // 100

// A parent reference points to a subclass instance.
let baseProcessor: NumberProcessor = new AdvancedProcessor();
console.info(`${baseProcessor.process(5).toString()}`);  // 15 (calls the subclass override)
```

Overridden methods can retain or increase access, but cannot reduce it.

**TypeScript Comparison**

<!-- @[ts_override_access_modifiers](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Methods.ts) -->

``` TypeScript
class Base {
  // Public method.
  public publicMethod(): void {
    console.info(`Base public`);
  }

  // protected method
  protected protectedMethod(): void {
    console.info(`Base protected`);
  }

  // Private method (cannot be overridden).
  private privateMethod(): void {
    console.info(`Base private`);
  }

  protected loweredPublicMethod(): void {}
}

class Derived extends Base {
  // Override a public method: retain public access.
  public publicMethod(): void {
    console.info(`Derived public`);
  }

  // Override a protected method: retain protected access or make it public.
  public protectedMethod(): void {
    console.info(`Derived public (was protected)`);
  }

  // Private methods cannot be overridden.
  // private privateMethod(): void {}  // Compilation error.

  // Access cannot be reduced.
  // private loweredPublicMethod(): void {}  // Compilation error: cannot change protected to private.

  callProtected(): void {
    this.protectedMethod();  // Can access the parent's protected member.
  }
}

let derived: Derived = new Derived();
derived.publicMethod();        // 'Derived public'
derived.protectedMethod();     // 'Derived public (was protected)'
derived.callProtected();       // 'Derived public (was protected)'
```

When overriding a parent method, completely replace its behavior or call the parent implementation through `super.methodName()` and add new logic.

<!-- @[override_and_extend](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Methods.ets) -->

``` TypeScript
class ExtendLogger {
  log(message: string): void {
    console.info(`[LOG] ${message}`);
  }
}

class DetailedLogger extends ExtendLogger {
  // Override the method to change behavior.
  log(message: string): void {
    console.info(`[DETAIL] ${message}`);
    console.info(`Timestamp: ${new Date().toISOString()}`);
  }
  
  // Retain parent behavior and add new behavior.
  logWithParent(message: string): void {
    super.log(message);  // Parent method.
    console.info(`Additional info for ${message}`);
  }
  
  // New method; no conflict.
  logError(error: string): void {
    this.log(`ERROR: ${error}`);
  }
}

let detailed: DetailedLogger = new DetailedLogger();

detailed.log('test');           // [DETAIL] test, Timestamp: ...
detailed.logWithParent('test'); // [LOG] test, Additional info...
detailed.logError('failed');    // '[DETAIL] ERROR: failed'

// Parent reference.
let logger: ExtendLogger = new DetailedLogger();
logger.log('test');  // [DETAIL] test (calls the subclass override)
```

Polymorphism is the core benefit of overriding: subclasses provide different implementations of the same method, producing different behavior when called through parent references. Adding subclass types does not affect existing code, and a unified interface can handle all subclasses.

<!-- @[polymorphism_concept](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Inheritance.ets) -->

``` TypeScript
// Polymorphism: subclasses implement the same method differently.
class ConceptShape {
  // Parent method.
  draw(): void {
    console.info('Drawing shape');
  }

  getArea(): number {
    return 0;
  }
}

class ConceptCircle extends ConceptShape {
  public radius: number;

  constructor(radius: number) {
    super();
    this.radius = radius;
  }

  // Override a method to implement polymorphism.
  draw(): void {
    console.info(`Drawing circle with radius ${this.radius}`);
  }

  getArea(): number {
    return Math.PI * this.radius * this.radius;
  }
}

class ConceptRectangle extends ConceptShape {
  public width: number;
  public height: number;

  constructor(width: number, height: number) {
    super();
    this.width = width;
    this.height = height;
  }

  // Override a method to implement polymorphism.
  draw(): void {
    console.info(`Drawing rectangle ${this.width}x${this.height}`);
  }

  getArea(): number {
    return this.width * this.height;
  }
}

// Polymorphism: a parent reference points to a subclass instance.
let shapes: ConceptShape[] = [
  new ConceptCircle(5),
  new ConceptRectangle(10, 20),
  new ConceptCircle(3)
];

// Unified interface calls produce different behavior.
for (let shape of shapes) {
  shape.draw();
  console.info(`Area: ${shape.getArea()}`);
}
```

### Abstract Classes and Interfaces

Abstract classes are declared with `abstract` and cannot be instantiated. They define common templates and contracts for subclasses. Abstract methods (marked with `abstract`) require subclass implementations, while concrete methods provide defaults that subclasses can inherit or override.

**TypeScript Comparison**

<!-- @[ts_abstract_class_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Inheritance.ts) -->

``` TypeScript
// Abstract class: can only be inherited, not instantiated.
abstract class Animal {
  public name: string;

  constructor(name: string) {
    this.name = name;
  }

  // Abstract method: subclasses must implement it.
  abstract speak(): void;

  // Concrete method: subclasses can inherit it.
  move(): void {
    console.info(`${this.name} is moving`);
  }

  // Concrete method: provide a default implementation.
  sleep(): void {
    console.info(`${this.name} is sleeping`);
  }
}

// Implement the abstract class in a subclass.
class Dog extends Animal {
  public breed: string;

  constructor(name: string, breed: string) {
    super(name);
    this.breed = breed;
  }

  // Implement an abstract method.
  speak(): void {
    console.info(`${this.name} barks`);
  }

  // Override a concrete method.
  move(): void {
    console.info(`${this.name} runs`);
  }
}

class Cat extends Animal {
  public color: string;

  constructor(name: string, color: string) {
    super(name);
    this.color = color;
  }

  // Implement an abstract method.
  speak(): void {
    console.info(`${this.name} meows`);
  }
}

// Abstract classes cannot be instantiated.
let animal: Animal = new Animal('Test');  // Compilation error

// Use through subclasses.
let dog: Dog = new Dog('Max', 'Labrador');
let cat: Cat = new Cat('Whiskers', 'Orange');

dog.speak();  // Max barks (implemented method)
dog.move();   // Max runs (overridden method)
dog.sleep();  // Max is sleeping (inherited method)

cat.speak();  // Whiskers meows (implemented method)
cat.move();   // Whiskers is moving (inherited method)
cat.sleep();  // Whiskers is sleeping (inherited method)
```

The `implements` clause checks whether a class meets an interface contract. Unlike `extends`, it performs only type checking and does not inherit implementations. A class can use both `extends` and `implements` and can implement multiple interfaces.

<!-- @[implements_clause](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Inheritance.ets) -->

``` TypeScript
interface InhComparable {
  compareTo(other: Object): number;
}

class InhProduct implements InhComparable {
  public price: number;

  constructor(price: number) {
    this.price = price;
  }

  compareTo(other: Object): number {
    if (other instanceof InhProduct) {
      return this.price - other.price;
    }
    return 0;
  }
}

class InhDiscountedProduct extends InhProduct implements InhComparable {
  public discount: number;

  constructor(price: number, discount: number) {
    super(price);
    this.discount = discount;
  }

  getFinalPrice(): number {
    return this.price * (1 - this.discount);
  }
}
```

ArkTS supports only single inheritance, not multiple inheritance: for example, `class C extends A, B` causes a compilation error. Multiple inheritance introduces the diamond problem: if two parents define a same-name method, the subclass cannot determine which to inherit, causing ambiguity. To combine behaviors from multiple types, use `implements` with multiple interfaces instead. Interfaces define contracts without implementations, avoiding conflicts.

**TypeScript Comparison**

<!-- @[ts_single_inheritance_limitation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Inheritance.ts) -->

``` TypeScript
// ArkTS supports only single inheritance: a subclass can have only one parent.
class ParentA {
  methodA(): void {
    console.info(`Method A`);
  }
}

class ParentB {
  methodB(): void {
    console.info(`Method B`);
  }
}

// Cannot also inherit ParentB.
class ErrorChild extends ParentA, ParentB {}  // Compilation error

// Single inheritance: only one parent class.
class Child extends ParentA {
  // Can inherit ParentA.
  methodA(): void {
    super.methodA();
    console.info(`Child overrides Method A`);
  }
}

let child: Child = new Child();
child.methodA();  // 'Method A', 'Child overrides Method A'
```

Implement multiple interfaces to combine multiple behavior contracts.

<!-- @[interface_multi_implementation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Inheritance.ets) -->

``` TypeScript
// Alternative to multiple inheritance: interface implementation.
interface IFeatureA {
  methodA(): void;
}

interface IFeatureB {
  methodB(): void;
}

class MultiFeature implements IFeatureA, IFeatureB {
  methodA(): void {
    console.info(`Feature A`);
  }

  methodB(): void {
    console.info(`Feature B`);
  }
}

let multi: MultiFeature = new MultiFeature();
multi.methodA();
multi.methodB();
```

TypeScript can mix multiple behaviors into a class at runtime using the Mixin pattern. **ArkTS does not support the Mixin pattern**. To reuse implementations from multiple classes, use composition (hold instances of other classes and delegate calls) or interface implementation instead.

**TypeScript Comparison**

<!-- @[ts_mixins](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Classes.ts) -->

``` TypeScript
// TypeScript syntax; ArkTS does not support the Mixin pattern.
class TsBaseWidget {
  public id: number = 0;
}

function Scoped(Base: typeof TsBaseWidget) {
  return class extends Base {
    public scope: string = 'local';
  };
}

let ScopedWidget = Scoped(TsBaseWidget);
let tsWidget = new ScopedWidget();
console.info(`${tsWidget.scope}`); // 'local'
```

ArkTS alternative: composition pattern.

<!-- @[mixin_composition_alternative](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Classes.ets) -->

``` TypeScript
interface MixinLoggable {
  log(message: string): void;
}

class MixinConsoleLogger implements MixinLoggable {
  log(message: string): void {
    console.info(`[LOG] ${message}`);
  }
}

class MixinService {
  public logger: MixinLoggable;

  constructor(logger: MixinLoggable) {
    this.logger = logger;
  }

  processData(data: string): void {
    this.logger.log(`Processing: ${data}`);
  }
}

let mixinService: MixinService = new MixinService(new MixinConsoleLogger());
mixinService.processData('test'); // '[LOG] Processing: test'
```

**Inheriting built-in types**: Inheriting built-in types such as `Error` and `Array` may encounter prototype chain issues with an ES5 target, requiring manual fixes. ArkTS does not support `Object.setPrototypeOf` or `prototype` manipulation. Prefer composition when working with built-in types.

**TypeScript Comparison**

<!-- @[ts_inherit_builtin_error](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Inheritance.ts) -->

``` TypeScript
// TypeScript comparison: repair the prototype chain when inheriting Error.
class InhAppError extends Error {
  public code: number;

  constructor(message: string, code: number) {
    super(message);
    this.code = code;

    // Repair the prototype chain (required for an ES5 target).
    Object.setPrototypeOf(this, InhAppError.prototype);
  }

  getInfo(): string {
    return `[${this.code}] ${this.message}`;
  }
}

let inhError: InhAppError = new InhAppError('Not found', 404);
console.info(`${inhError.getInfo()}`);  // '[404] Not found'
console.info(`${(inhError instanceof InhAppError).toString()}`);  // true
console.info(`${(inhError instanceof Error).toString()}`);  // true
```

## Decorators

ArkTS supports class decorators, method decorators, accessor decorators, property decorators, and parameter decorators. Decorator implementations must follow the ArkTS syntax rules: use arrow functions instead of function expressions, explicitly annotate types, and avoid a standalone `this`. The `@Component`, `@Entry`, and state decorators in ArkUI, as well as `@Sendable` and `@Concurrent` in concurrency scenarios, are dedicated decorators defined by the framework or the concurrency model.

### Class Decorator

A class decorator modifies a class declaration through a function and executes the decoration logic when the class is created.

<!-- @[class_decorator_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Classes.ets) -->

``` TypeScript
function logged(constructor: Function): void {
  console.info(`Class ${constructor.name} created`);
}

@logged
class DecoService {
  public name: string = 'default';
}

let decoService: DecoService = new DecoService();
// Console output: Class DecoService created
```

### Decorator Factory

A decorator factory returns a decorator function and can accept parameters for configuration.

<!-- @[decorator_factory_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Classes.ets) -->

``` TypeScript
function format(prefix: string): (constructor: Function) => void {
  return (constructor: Function): void => {
    console.info(`${prefix} ${constructor.name}`);
  };
}

@format('Created')
class DecoFactoryService {
  public id: number = 0;
}

let decoFactoryService: DecoFactoryService = new DecoFactoryService();
// Console output: Created DecoFactoryService
```

### Method Decorator

A method decorator receives three parameters: `target`, `propertyKey`, and `descriptor`. It can read or modify the method descriptor.

<!-- @[method_decorator_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Classes.ets) -->

``` TypeScript
function logMethod(target: Object, propertyKey: string, descriptor: PropertyDescriptor): void {
  console.info(`Method ${propertyKey} decorated`);
}

class DecoCalculator {
  @logMethod
  add(a: number, b: number): number {
    return a + b;
  }
}

let decoCalc: DecoCalculator = new DecoCalculator();
console.info(`${decoCalc.add(1, 2)}`); // 3
```

### Accessor Decorator

An accessor decorator is used to decorate `get`/`set` accessors. Its parameters are the same as those of a method decorator.

<!-- @[accessor_decorator_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Classes.ets) -->

``` TypeScript
function logAccessor(target: Object, propertyKey: string, descriptor: PropertyDescriptor): void {
  console.info(`Accessor ${propertyKey} decorated`);
}

class DecoCounter {
  private _count: number = 0;

  @logAccessor
  get count(): number {
    return this._count;
  }

  set count(value: number) {
    this._count = value;
  }
}

let decoCounter: DecoCounter = new DecoCounter();
decoCounter.count = 5;
console.info(`${decoCounter.count}`); // 5
```

### Property Decorator

A property decorator receives two parameters, `target` and `propertyKey`, and is commonly used for marking or injection.

<!-- @[property_decorator_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Classes.ets) -->

``` TypeScript
function logProperty(target: Object, propertyKey: string): void {
  console.info(`Property ${propertyKey} decorated`);
}

class DecoConfig {
  @logProperty
  public name: string = 'default';
}

let decoConfig: DecoConfig = new DecoConfig();
console.info(`${decoConfig.name}`); // 'default'
```

### Parameter Decorator

A parameter decorator receives three parameters: `target`, `propertyKey`, and `parameterIndex`. It is commonly used for parameter validation marking.

<!-- @[parameter_decorator_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Classes.ets) -->

``` TypeScript
function logParam(target: Object, propertyKey: string, parameterIndex: number): void {
  console.info(`Param ${parameterIndex} of ${propertyKey} decorated`);
}

class DecoProcessor {
  process(@logParam input: string): string {
    return input.toUpperCase();
  }
}

let decoProc: DecoProcessor = new DecoProcessor();
console.info(`${decoProc.process('hello')}`); // 'HELLO'
```

### Implementing Cross-Cutting Logic Through Inheritance or Composition

An alternative to decorators is to implement cross-cutting logic through base class inheritance (injecting logic such as logging into the parent class constructor or methods) or composition (holding a functional object and delegating calls to it).

<!-- @[base_class_pattern](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Classes.ets) -->

``` TypeScript
class LoggedBase {
  private className: string;

  constructor(className: string) {
    this.className = className;
    console.info(`Creating ${className}`);
  }

  protected log(methodName: string): void {
    console.info(`Calling ${this.className}.${methodName}`);
  }
}

class UserService extends LoggedBase {
  constructor() {
    super('UserService');
  }

  getData(): string {
    this.log('getData');
    return 'data';
  }
}

let service: UserService = new UserService();
console.info(`${service.getData()}`);
```
