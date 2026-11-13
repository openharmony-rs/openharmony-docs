---
kits: ["ArkTS Kit"]
description: "How to define and implement ArkTS interfaces, covering interface inheritance and composition, optional members, and generic constraint interfaces."
keywords: [ArkTS, interfaces, interface, interface inheritance, optional members, generic constraints]
doctype: guide
status: active
---

# Interfaces
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @jokerxd-liu-->
<!--Designer: @jokerxd-liu-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=8923bda514baa1452b967ea964ea779c7417bd8e translatedAt=2026-11-12T12:34:02.418Z pushedAt=2026-10-30T06:21:33.935Z nl=1 -->

Interfaces are an important way to define object structures in ArkTS. An interface defines a contract consisting of properties and methods to constrain object structures, enabling code decoupling and reuse.

## Basic Concepts of Interfaces

An interface defines the structural contract of an object, specifying property names, types, and optionality without containing implementations. It is used for type constraints and code decoupling.

### Core Roles of Interfaces

Interfaces constrain object structures at compile time, decouple module dependencies through common contracts, and allow multiple classes to reuse the same type definition. They are a core mechanism for loose coupling and type safety in ArkTS. A class implements an interface with `implements` to ensure that its instances have the required members.

<!-- @[simple_interface_definition](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Interfaces.ets) -->

``` TypeScript
// Define a simple interface.
interface User {
  id: number;
  name: string;
  email: string;
}

// Use an interface to constrain an object.
let user: User = {
  id: 1,
  name: 'Alice',
  email: 'alice@example.com'
};

console.info(user.name); // 'Alice'
```

## Interface Declaration and Implementation

The `interface` keyword declares an interface structure, and a class implements the interface contract with `implements`.

### Interface Declaration Syntax

Declare an interface with the `interface` keyword, defining properties (name: type) and method signatures to describe a structural contract for objects.

<!-- @[basic_interface_declaration](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Interfaces.ets) -->

``` TypeScript
// Basic interface declaration
interface Point {
  x: number;
  y: number;
}

let point: Point = {
  x: 10,
  y: 20
};

console.info(`Point: (${point.x}, ${point.y})`);
```

### Defining Interface Members

Interface members include properties, methods, and accessors.

**Property Types**

Interface properties include required properties, optional properties (`?`), and readonly properties (`readonly`).

<!-- @[ts_interface_property_types](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Interfaces.ts) -->

``` TypeScript
interface Product {
    // Required property
  id: number;
  name: string;
  price: number;

  // Optional property (use ?)
  description?: string;
  stock?: number;

  // Readonly property (use readonly)
  readonly createdAt: Date;
}

let product: Product = {
  id: 1,
  name: 'Laptop',
  price: 999,
  createdAt: new Date()
};

// Access the optional property.
if (product.description) {
    console.info(`${product.description}`);
}

// The readonly property cannot be modified.
product.createdAt = new Date(); // Compilation error.
```

**Method declaration**

Interface methods include required and optional methods (`?`). Classes implement interface methods with `implements`.

<!-- @[interface_method_declaration](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Interfaces.ts) -->

``` TypeScript
interface Calculator {
  reset(): void;
  add(a: number, b: number): number;
  subtract(a: number, b: number): number;

  // Optional method (using ?).
  logResult?(): void;
}

class BasicCalculator implements Calculator {
  private result: number = 0;
  
  public reset(): void {
    this.result = 0;
    console.info('Calculator reset');
  }
  
  public add(a: number, b: number): number {
    this.result = a + b;
    return this.result;
  }
  
  public subtract(a: number, b: number): number {
    this.result = a - b;
    return this.result;
  }
  
  // Optional methods can be omitted. To implement one, use the following example.
  public logResult(): void {
    console.info(`Result: ${this.result}`);
  }
}

let calculator: BasicCalculator = new BasicCalculator();
let sum: number = calculator.add(10, 5);
console.info(`${sum}`); // 15
```

**Accessors (Getters/Setters)**

An interface can declare `get`/`set` accessors, requiring the implementing class to provide getters and setters with the same names. Their usage is the same as computed properties in classes. For details, see [Computed Properties](arkts-language-guide-classes.md#computed-properties).

<!-- @[interface_accessors](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Interfaces.ets) -->

``` TypeScript
interface PersonInfo {
  get fullName(): string;
  set fullName(name: string);
}

class Person implements PersonInfo {
  private firstName: string;
  private lastName: string;

  constructor(firstName: string, lastName: string) {
    this.firstName = firstName;
    this.lastName = lastName;
  }

  get fullName(): string {
    return `${this.firstName} ${this.lastName}`;
  }

  set fullName(name: string) {
    let parts: string[] = name.split(' ');
    this.firstName = parts[0];
    this.lastName = parts[1];
  }
}

let person: PersonInfo = new Person('John', 'Smith');
console.info(`${person.fullName}`); // 'John Smith'

person.fullName = 'Bob Brown';
console.info(`${person.fullName}`); // 'Bob Brown'
```

### Implementing an Interface with a Class

A class implements an interface with the `implements` keyword and must provide concrete implementations of all required members. Different classes can implement the same interface to provide different behaviors.

<!-- @[class_implements_interface](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Interfaces.ets) -->

``` TypeScript
interface Logger {
  log(message: string): void;
  error(message: string): void;
  warn(message: string): void;
}

class ConsoleLogger implements Logger {
  public log(message: string): void {
    console.info(`[LOG] ${message}`);
  }
  
  public error(message: string): void {
    console.error(`[ERROR] ${message}`);
  }
  
  public warn(message: string): void {
    console.info(`[WARN] ${message}`);
  }
}

class FileLogger implements Logger {
  private fileName: string;
  
  constructor(fileName: string) {
    this.fileName = fileName;
  }
  
  public log(message: string): void {
    // Simulate writing to a file.
    console.info(`Writing to ${this.fileName}: [LOG] ${message}`);
  }
  
  public error(message: string): void {
    console.info(`Writing to ${this.fileName}: [ERROR] ${message}`);
  }
  
  public warn(message: string): void {
    console.info(`Writing to ${this.fileName}: [WARN] ${message}`);
  }
}

let consoleLogger = new ConsoleLogger();
let fileLogger = new FileLogger('app.log');

consoleLogger.log('Application started');
// [LOG] Application started

fileLogger.error('Connection failed');
// Writing to app.log: [ERROR] Connection failed
```

## Interface Inheritance and Composition

Interfaces use `extends` for single and multiple inheritance to reuse and compose type definitions.

### Single Inheritance of Interfaces

An interface uses `extends` to inherit a single parent interface and adds new members to those inherited from the parent. The child interface can be further inherited to form a multilevel hierarchy, with the final child containing the members of all parent interfaces.

<!-- @[interface_multi_level_inheritance](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Interfaces.ets) -->

``` TypeScript
interface Animal {
  name: string;
  age: number;
}

interface Pet extends Animal {
  owner: string;
}

interface Dog extends Pet {
  breed: string;
  bark(): void;
}

class DemoDog implements Dog {
  public name: string;
  public age: number;
  public owner: string;
  public breed: string;

  constructor(name: string, age: number, owner: string, breed: string) {
    this.name = name;
    this.age = age;
    this.owner = owner;
    this.breed = breed;
  }

  public bark(): void {
    console.info(`${this.name} barks: Woof! Woof!`);
  }
}

let myDog: Dog = new DemoDog('Buddy', 3, 'Alice', 'Golden Retriever');

myDog.bark(); // 'Buddy barks: Woof! Woof!'
```

### Multiple Interface Inheritance

Use `extends` to inherit multiple parent interfaces and combine multiple type contracts.

<!-- @[interface_multiple_inheritance](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Interfaces.ets) -->

``` TypeScript
interface MiSerializable {
  serialize(): string;
}

interface MiComparable {
  compareTo(other: Object): number;
}

interface MiEntity extends MiSerializable, MiComparable {
  id: number;
}

class MiUserEntity implements MiEntity {
  public id: number;

  constructor(id: number) {
    this.id = id;
  }

  public serialize(): string {
    return `User#${this.id}`;
  }

  public compareTo(other: Object): number {
    let otherUser: MiUserEntity = other as MiUserEntity;
    return this.id - otherUser.id;
  }
}

let miUser1: MiUserEntity = new MiUserEntity(1);
let miUser2: MiUserEntity = new MiUserEntity(2);

console.info(`${miUser1.serialize()}`);        // 'User#1'
console.info(`${miUser1.compareTo(miUser2)}`); // -1
```

### Constraints on Interface Inheritance

When inheriting an interface, you can add new members or override members with the same names. An overriding method must have a signature compatible with the parent interface; its return type can differ. However, redeclaring a member with an incompatible type causes a compilation error.

<!-- @[ts_interface_inheritance_rules](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Interfaces.ts) -->

``` TypeScript
interface Base {
  method(): void;
}

interface Derived extends Base {
  // New members can be added.
  newMethod(): void;

  // Methods with the same name can be overridden with a different return type, provided the signatures are compatible.
  method(): string;
}

// An overriding property must have a type compatible with the parent interface.
interface Colorable {
  color: string;
}

interface BadColorable extends Colorable {
  // A property cannot be redeclared with an incompatible type.
  color: number; // Compilation error: type mismatch.
}
```

## Optional Members of an Interface

Optional members are marked with `?` and can be omitted in implementations.

### Optional Properties and Methods

Optional properties and methods are marked with `?` after the member name, indicating that the member may not exist. Implementing objects can provide them as needed.

<!-- @[optional_properties_methods](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Interfaces.ets) -->

``` TypeScript
interface Configuration {
  // Required property.
  apiUrl: string;

  // Optional property (using ?).
  timeout?: number;

  // Optional method.
  logError?: (error: Error) => void;
}

// Provide only required members.
let config1: Configuration = {
  apiUrl: 'EXAMPLE_API_URL'
};

// Provide optional members as needed.
let config2: Configuration = {
  apiUrl: 'EXAMPLE_API_URL',
  timeout: 5000
};

// Check whether an optional member exists before using it.
if (config2.timeout !== undefined) {
  console.info(`Timeout: ${config2.timeout}ms`);
}

if (config2.logError) {
  config2.logError(new Error('Test error'));
}
```

### Calling Notes for Optional Members

Check whether an optional member exists before calling it to avoid accessing `undefined`.

<!-- @[using_optional_members](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Interfaces.ets) -->

``` TypeScript
interface OptionalInterface {
  requiredMethod(): void;
  optionalMethod?(): void;
  requiredProperty: string;
  optionalProperty?: number;
}

function useOptionalInterface(obj: OptionalInterface): void {
  // Required members can be called directly.
  obj.requiredMethod();
  console.info(`${obj.requiredProperty}`);
  
  // Check whether the optional method exists before calling it.
  if (obj.optionalMethod) {
    obj.optionalMethod();
  }
  
  // Check whether the optional property exists before accessing it.
  if (obj.optionalProperty !== undefined) {
    console.info(`${obj.optionalProperty}`);
  }
  
  // Use the optional chaining operator (?.).
  obj.optionalMethod?.();
  console.info(`${obj.optionalProperty?.toFixed(2)}`);
  
  // Use the nullish coalescing operator (??).
  let value: number = obj.optionalProperty ?? 0;
  console.info(`${value}`);
}
```

### Alternative: Use Interface Extension to Implement Optional Members

By extending a base interface and adding optional members, implementing classes can decide whether to provide optional capabilities as needed.

<!-- @[extending_interface_with_optionals](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Interfaces.ets) -->

``` TypeScript
// Base interface (required members)
interface BaseInterface {
  requiredMethod(): void;
  requiredProperty: string;
}

// Extended interface (with optional members)
interface ExtendedInterface extends BaseInterface {
    optionalMethod?(): void;
    optionalProperty?: number;
}

class BaseInterfaceImpl implements BaseInterface {
  public requiredProperty: string = 'Required value';

  public requiredMethod(): void {
    console.info('Required method');
  }
}

class ExtendedInterfaceImpl implements ExtendedInterface {
  public requiredProperty: string = 'Required value';
  public optionalProperty: number = 42;

  public requiredMethod(): void {
    console.info('Required method');
  }

  public optionalMethod(): void {
    console.info('Optional method');
  }
}

// Use the base interface
let baseObj: BaseInterface = new BaseInterfaceImpl();

// Use the extended interface (you can choose whether to provide the optional member).
let extendedObj: ExtendedInterface = new ExtendedInterfaceImpl();

// Make the extended interface inherit the base interface.
function processObject(obj: BaseInterface): void {
  obj.requiredMethod();
  console.info(`${obj.requiredProperty}`);
  
  // If an extended interface object is passed in, cast it to the extended interface first and then check the optional member.
  let extended: ExtendedInterface = obj as ExtendedInterface;
  if (extended.optionalMethod !== undefined) {
    extended.optionalMethod();
  }
}

processObject(baseObj);
processObject(extendedObj);
```

## Generic Interfaces

Generic interfaces introduce type parameters with `<T>`, allowing one interface to accommodate multiple data types.

<!-- @[generic_interface](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Interfaces.ets) -->

``` TypeScript
// Generic interface
interface Container<T> {
  value: T;
  getValue(): T;
  setValue(value: T): void;
}

class NumberContainer implements Container<number> {
  public value: number;
  
  constructor(initialValue: number) {
    this.value = initialValue;
  }
  
  public getValue(): number {
    return this.value;
  }
  
  public setValue(value: number): void {
    this.value = value;
  }
}

class StringContainer implements Container<string> {
  public value: string;
  
  constructor(initialValue: string) {
    this.value = initialValue;
  }
  
  public getValue(): string {
    return this.value;
  }
  
  public setValue(value: string): void {
    this.value = value;
  }
}

let numContainer = new NumberContainer(42);
let strContainer = new StringContainer('Hello');

console.info(`${numContainer.getValue().toString()}`); // 42
console.info(`${strContainer.getValue()}`); // 'Hello'
```

For details about generics (type constraints, generic classes, generic functions, and more), see [Generics](arkts-language-guide-generics.md).

## Combining Interfaces with Classes

A class implements an interface with `implements`: the interface defines the contract, and the class provides the implementation.

### Implementing a Single Interface

A class uses the `implements` keyword to implement a single interface and must provide concrete implementations of all required members.

<!-- @[single_interface_implementation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Interfaces.ets) -->

``` TypeScript
interface Drawable {
  draw(): void;
}

class Circle implements Drawable {
  private radius: number;
  
  constructor(radius: number) {
    this.radius = radius;
  }
  
  public draw(): void {
    console.info(`Drawing a circle with radius ${this.radius}`);
  }
}

let circle = new Circle(5);
circle.draw(); // Drawing a circle with radius 5
```

### Implementing Multiple Interfaces

A class can implement multiple interfaces separated by commas (for example, `implements A, B, C`) and must implement the required members of all interfaces.

<!-- @[multiple_interface_implementation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Interfaces.ets) -->

``` TypeScript
interface Printable {
  print(): void;
}

interface Saveable {
  save(): void;
}

interface Loadable {
  load(): void;
}

class Document implements Printable, Saveable, Loadable {
  private title: string;
  private content: string;
  
  constructor(title: string, content: string) {
    this.title = title;
    this.content = content;
  }
  
  public print(): void {
    console.info(`Printing: ${this.title}`);
    console.info(`${this.content}`);
  }
  
  public save(): void {
    console.info(`Saving: ${this.title}`);
  }
  
  public load(): void {
    console.info(`Loading: ${this.title}`);
  }
}

let document = new Document('My Document', 'This is the content.');
document.print();
document.save();
document.load();
```

### Inheriting a Class and Implementing Interfaces

A class can use `extends` to inherit a parent class and `implements` to implement interfaces, reusing parent class code while satisfying interface contracts.

<!-- @[class_inheritance_with_interface](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Interfaces.ets) -->

``` TypeScript
class BaseEntity {
  public id: number;
  public createdAt: Date;
  
  constructor(id: number) {
    this.id = id;
    this.createdAt = new Date();
  }
  
  public getInfo(): string {
    return `ID: ${this.id}, Created: ${this.createdAt}`;
  }
}

interface Named {
  name: string;
  getName(): string;
}

interface Active {
  active: boolean;
  activate(): void;
  deactivate(): void;
}

class InterfaceUser extends BaseEntity implements Named, Active {
  public name: string;
  public active: boolean;
  
  constructor(id: number, name: string) {
    super(id);
    this.name = name;
    this.active = false;
  }
  
  public getName(): string {
    return this.name;
  }
  
  public activate(): void {
    this.active = true;
    console.info(`${this.name} activated`);
  }
  
  public deactivate(): void {
    this.active = false;
    console.info(`${this.name} deactivated`);
  }
}

let interfaceUser = new InterfaceUser(1, 'Alice');
console.info(`${interfaceUser.getInfo()}`);  // 'ID: 1, Created: ...'
console.info(`${interfaceUser.getName()}`);  // 'Alice'
interfaceUser.activate();
interfaceUser.deactivate();
```

### Interfaces as Type Constraints for Classes

An interface can be used as a constraint on a generic parameter (for example, `<T extends Comparable<T>>`), restricting the type parameter to types that implement the specified interface, so that interface members can be safely called in generic code.

<!-- @[comparable_equatable_interface](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Interfaces.ets) -->

``` TypeScript
interface EquatableComparable<T> {
  compareTo(other: T): number;
}

interface Equatable<T> {
  equals(other: T): boolean;
}

class NumericValue implements EquatableComparable<NumericValue>, Equatable<NumericValue> {
  public value: number;
  
  constructor(value: number) {
    this.value = value;
  }
  
  public compareTo(other: NumericValue): number {
    return this.value - other.value;
  }
  
  public equals(other: NumericValue): boolean {
    return this.value === other.value;
  }
}

let num1 = new NumericValue(10);
let num2 = new NumericValue(20);
let num3 = new NumericValue(10);

console.info(`${num1.compareTo(num2)}`); // -10
console.info(`${num1.equals(num2)}`);    // false
console.info(`${num1.equals(num3)}`);    // true

// Use an interface type as a constraint.
function findMax<T extends EquatableComparable<T>>(items: T[]): T | null {
  if (items.length === 0) {
    return null;
  }
  
  let max: T = items[0] as T;
  for (let i = 1; i < items.length; i++) {
    let current: T = items[i] as T;
    if (current.compareTo(max) > 0) {
      max = current;
    }
  }
  return max;
}

let values: NumericValue[] = [new NumericValue(5), new NumericValue(15), new NumericValue(10)];
let maxValue = findMax(values);
console.info(`${maxValue ? maxValue.value : 0}`); // 15
```

## Using Interfaces as Types

An interface can be used as a type annotation for a variable to constrain the structure of an object.

### Interface as a Variable Type

An interface name can be used directly as a type annotation for a variable. During assignment, the object literal must contain all required members with matching types, and excess properties are rejected by the compiler.

<!-- @[interface_object_literal_type](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Interfaces.ets) -->

``` TypeScript
interface LiteralPoint {
  x: number;
  y: number;
}

let literalPoint: LiteralPoint = { x: 10, y: 20 };

interface Color {
  red: number;
  green: number;
  blue: number;
}

let color: Color = { red: 255, green: 128, blue: 0 };

console.info(`LiteralPoint: (${literalPoint.x}, ${literalPoint.y})`);
console.info(`Color: RGB(${color.red}, ${color.green}, ${color.blue})`);
```

### Interface as Function Parameter/Return Value Type

An interface used as a function parameter and return value type constrains the structure of the input and output.

<!-- @[interface_function_types](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Interfaces.ets) -->

``` TypeScript
interface UserRequest {
  name: string;
  email: string;
}

interface ApiResponse<T> {
  success: boolean;
  data?: T;
  error?: string;
}

// Use the interface as a parameter type.
function validateRequest(request: UserRequest): boolean {
  return request.name.length > 0 && request.email.includes('@');
}

// Use the interface as a return value type.
function getUserName(id: number): ApiResponse<string> {
  if (id > 0) {
    return { success: true, data: 'Alice' };
  }
  return { success: false, error: 'Invalid user ID' };
}

console.info(`${validateRequest({ name: 'Alice', email: 'alice@example.com' })}`); // true

let response: ApiResponse<string> = getUserName(1);
if (response.success && response.data !== undefined) {
  console.info(`${response.data}`); // 'Alice'
}
```

### Polymorphism of Interface Types

A variable of an interface type can point to an instance of any class that implements the interface. When a method with the same name is called, the respective implementation is executed, achieving runtime polymorphism.

<!-- @[interface_polymorphism](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Interfaces.ets) -->

``` TypeScript
interface PolyAnimal {
  name: string;
  speak(): void;
}

class PolyDog implements PolyAnimal {
  public name: string;
  
  constructor(name: string) {
    this.name = name;
  }
  
  public speak(): void {
    console.info(`${this.name} barks: Woof! Woof!`);
  }
}

class Cat implements PolyAnimal {
  public name: string;
  
  constructor(name: string) {
    this.name = name;
  }
  
  public speak(): void {
    console.info(`${this.name} meows: Meow!`);
  }
}

class Cow implements PolyAnimal {
  public name: string;
  
  constructor(name: string) {
    this.name = name;
  }
  
  public speak(): void {
    console.info(`${this.name} moos: Moo!`);
  }
}

// Use an interface type to implement polymorphism.
function makeAnimalSpeak(animal: PolyAnimal): void {
  animal.speak();
}

let dog = new PolyDog('Buddy');
let cat = new Cat('Whiskers');
let cow = new Cow('Daisy');

makeAnimalSpeak(dog); // 'Buddy barks: Woof! Woof!'
makeAnimalSpeak(cat); // 'Whiskers meows: Meow!'
makeAnimalSpeak(cow); // 'Daisy moos: Moo!'

// Use an array of interface types.
let animals: PolyAnimal[] = [dog, cat, cow];

animals.forEach(animal => {
    animal.speak();
});
```

### Converting an Interface Type to a Concrete Type

For a variable of an interface type, use `instanceof` to determine its concrete type, then use an `as` assertion to convert it back to a subtype and access members specific to the implementing class.

<!-- @[interface_type_casting](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Interfaces.ets) -->

``` TypeScript
interface CastingVehicle {
  brand: string;
  model: string;
}

class CastingCar implements CastingVehicle {
  public brand: string;
  public model: string;
  public doors: number;

  constructor(brand: string, model: string, doors: number) {
    this.brand = brand;
    this.model = model;
    this.doors = doors;
  }

  public drive(): void {
    console.info(`Driving ${this.brand} ${this.model}`);
  }
}

// Convert an interface type to a concrete type (type check required).
function processVehicle(vehicle: CastingVehicle): void {
  if (vehicle instanceof CastingCar) {
    let car: CastingCar = vehicle as CastingCar;
    console.info(`Doors: ${car.doors}`);
    car.drive();
  }
}

let car: CastingVehicle = new CastingCar('Toyota', 'Camry', 4);

processVehicle(car);
// Doors: 4
// Driving Toyota Camry
```

## Notes on implements

The `implements` clause checks whether a class satisfies an interface, but it has several important limitations.

**`implements` does not change the class type.** It only performs checks and does not pass interface type information into the class body. Member types in the class are not automatically inferred from the interface and must be explicitly annotated.

**`implements` does not create optional properties.** Optional interface properties can be omitted. If the implementing class does not declare a property, it does not exist on instances, and accessing it through an instance causes a compilation error. If the property is needed, declare it explicitly in the class.

**`implements` checks only the instance side.** It only checks whether instance members satisfy the interface. Static members (`static`) are not checked, and interfaces cannot declare static members.

<!-- @[implements_cautions](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Interfaces.ets) -->

``` TypeScript
interface ImplCheckable {
  check(name: string): boolean;
}

class ImplNameChecker implements ImplCheckable {
  // implements does not pass interface type information into the class body.
  // Explicitly annotate parameter types rather than relying on inference from the interface.
  check(s: string): boolean {
    return s.toLowerCase() === 'ok';
  }
}

interface ImplConfigA {
  x: number;
  y?: number;
}

class ImplC implements ImplConfigA {
  public x: number = 0;
  // y is optional and can be omitted. If omitted, instances do not have a y property.
}

let implC: ImplC = new ImplC();
console.info(`${implC.x.toString()}`); // 0

// console.info(`${implC.y}`); // Compilation error: property y does not exist on ImplC.
```

<!-- @[implements_static_members](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Interfaces.ets) -->

``` TypeScript
interface ImplLoggable {
  log(message: string): void;
}

class ImplStaticCounter implements ImplLoggable {
  // Static members are not checked by implements.
  private static count: number = 0;

  log(message: string): void {
    ImplStaticCounter.count++;
    console.info(`[${ImplStaticCounter.count}] ${message}`);
  }
}

let staticCounter = new ImplStaticCounter();
staticCounter.log('hello'); // '[1] hello'
```

## Comparison Between Abstract Classes and Interfaces

Neither abstract classes nor interfaces can be instantiated. An abstract class is an abstraction of a class, used to capture the common characteristics of child classes; an interface is an abstraction of behavior. In ArkTS syntax, the differences between abstract classes and interfaces are as follows:

- A class can inherit from only one abstract class, whereas a class can implement one or more interfaces.

<!-- @[bird_multiple_interface](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Interfaces.ets) -->

``` TypeScript
abstract class AcAnimal {
  public name: string;

  constructor(name: string) {
    this.name = name;
  }

  abstract makeSound(): void;
}

interface AcCanFly {
  fly(): void;
}

interface AcCanSwim {
  swim(): void;
}

class AcBird extends AcAnimal implements AcCanFly, AcCanSwim {
  constructor(name: string) {
    super(name);
  }

  makeSound(): void {
    console.info(`${this.name} chirps`);
  }

  fly(): void {
    console.info(`${this.name} flies`);
  }

  swim(): void {
    console.info(`${this.name} swims`);
  }
}

let acBird: AcBird = new AcBird('Sparrow');
acBird.makeSound(); // 'Sparrow chirps'
acBird.fly();       // 'Sparrow flies'
acBird.swim();      // 'Sparrow swims'
```

- An interface cannot contain static blocks or static methods, whereas an abstract class can contain at most one static block and can contain static methods.

<!-- @[abstract_vs_interface_static](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Interfaces.ets) -->

``` TypeScript
abstract class AviAbstractClass {
  static staticMethod(): void { console.info('static'); }
  static { console.info('static initialization block'); }
}
```

- An abstract class can have method implementations, but an interface has no method implementations and is completely abstract.

<!-- @[abstract_vs_interface_method](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Interfaces.ets) -->

``` TypeScript
abstract class AimAbstractClass {
  func(): void { console.info('func'); }
}
```

- An abstract class can have a constructor, while an interface cannot.

<!-- @[abstract_vs_interface_constructor](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Interfaces.ets) -->

``` TypeScript
abstract class AvicAbstractClass {
  constructor() {}
}
```
