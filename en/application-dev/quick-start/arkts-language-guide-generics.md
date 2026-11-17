---
kits: ["ArkTS Kit"]
description: "How to use ArkTS generics, covering generic functions, generic classes, generic interfaces, generic constraints (variance and subtyping), and common data structures."
keywords: [ArkTS, generics, generic functions, generic classes, generic interfaces, generic constraints, variance]
doctype: guide
status: active
---

# Generics
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @jokerxd-liu-->
<!--Designer: @jokerxd-liu-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=8923bda514baa1452b967ea964ea779c7417bd8e translatedAt=2026-11-12T12:34:02.404Z pushedAt=2026-10-30T06:21:33.935Z nl=1 -->

Generics are a powerful type system feature in ArkTS that allows type parameters in function, class, and interface definitions, enabling code reuse and type safety.

## Basic Concepts of Generics

### Definition and Core Value of Generics

Generics parameterize types so that a single piece of code works with multiple types while preserving compile-time type safety. The compiler checks the type arguments at call sites and then erases them, combining reusability, type inference, and zero runtime overhead.

<!-- @[generics_introduction](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Generics.ets) -->

``` TypeScript
// Without generics: write a function for each type.
function identityNumber(arg: number): number {
  return arg;
}

function identityString(arg: string): string {
  return arg;
}

// With generics: one function works for all types.
function identity<T>(arg: T): T {
  return arg;
}

let num: number = identity<number>(42);
let str: string = identity<string>('Hello');
let bool: boolean = identity<boolean>(true);

console.info(`${num}`);   // 42
console.info(`${str}`);   // 'Hello'
console.info(`${bool}`);  // true
```

## Generic Functions

Generic functions support multiple type parameters, enabling reusable type-safe code.

### Declaring Generic Functions

Declare a type parameter with `<T>` after the function name, and use it in the parameters and return value.

<!-- @[generic_function_declarations](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Generics.ets) -->

``` TypeScript
// Basic generic function declaration
function wrap<T>(value: T): T[] {
  return [value];
}

// Generic function in arrow function form
const wrapArrow = <T>(value: T): T[] => [value];

// Generic function using a type alias
type WrapFunction = <T>(value: T) => T[];
let wrapAlias: WrapFunction = wrap;

console.info(`${wrap<number>(42)[0]}`);           // 42
console.info(`${wrapArrow<string>('Hello')[0]}`); // 'Hello'
console.info(`${wrapAlias<boolean>(true)[0]}`);   // true
```

### Type Parameter Naming Conventions

Type parameters are typically named with uppercase letters. Common conventions include `T` (Type), `U`, `K` (Key), `V` (Value), and `E` (Element).

<!-- @[multi_type_parameter_class](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Generics.ets) -->

``` TypeScript
// K (Key) and V (Value) are commonly used for key-value pairs.
function getOrDefault<K, V>(source: Map<K, V>, key: K, fallback: V): V {
  let value: V | undefined = source.get(key);
  return value !== undefined ? value : fallback;
}

let scoreByName: Map<string, number> = new Map<string, number>();
scoreByName.set('Alice', 95);
scoreByName.set('Bob', 88);

let aliceScore: number = getOrDefault(scoreByName, 'Alice', 0);
let carolScore: number = getOrDefault(scoreByName, 'Carol', 60);

console.info(`${aliceScore}`);  // 95
console.info(`${carolScore}`);  // 60
```

### Calling Generic Functions

When calling a generic function, you can explicitly specify the type parameter, or omit it and let the compiler infer it from the arguments.

<!-- @[generic_type_inference](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Generics.ets) -->

``` TypeScript
function repeatItem<T>(item: T, count: number): T[] {
  let result: T[] = [];
  for (let i = 0; i < count; i++) {
    result.push(item);
  }
  return result;
}

// Explicitly specify the type parameter.
let repeatedStrings: string[] = repeatItem<string>('Hi', 3);
console.info(`${repeatedStrings.join(', ')}`); // 'Hi, Hi, Hi'

// The type parameter is inferred automatically.
let repeatedNumbers: number[] = repeatItem(7, 2);
console.info(`${repeatedNumbers.join(', ')}`); // 7, 7

// Generic function with multiple type parameters.
function createPair<T, U>(first: T, second: U): [T, U] {
  return [first, second];
}

let pair1: [string, number] = createPair<string, number>('Age', 25);
let pair2: [string, number] = createPair('Height', 180); // Automatically inferred as [string, number].

console.info(`${pair1[0]}: ${pair1[1]}`); // 'Age: 25'
console.info(`${pair2[0]}: ${pair2[1]}`); // 'Height: 180'
```

### Generic Functions with Multiple Type Parameters

A function can declare multiple type parameters (for example, `<T, U>`), each serving as an independent placeholder that supports expressing relationships between different types.

<!-- @[multi_type_parameter_function](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Generics.ets) -->

``` TypeScript
// Basic usage of multiple type parameters.
function swap<T, U>(a: T, b: U): [U, T] {
  return [b, a];
}

let swapped: [string, number] = swap(1, 'Hello');
console.info(`${swapped[0]}, ${swapped[1]}`); // 'Hello, 1'

// Complex usage of multiple type parameters: use an explicit structure to store two values of different types.
interface PairValue<T, U> {
  left: T;
  right: U;
}

function combineValues<T, U>(left: T, right: U): PairValue<T, U> {
  return {
    left: left,
    right: right
  };
}

interface Name {
  name: string;
}

interface Age {
  age: number;
}

let nameObj: Name = { name: 'Alice' };
let ageObj: Age = { age: 25 };

let combinedObj: PairValue<Name, Age> = combineValues<Name, Age>(nameObj, ageObj);
console.info(`${combinedObj.left.name}`);
console.info(`${combinedObj.right.age}`);

// Create a mapping function using type parameters.
function mapArray<T, R>(arr: T[], mapper: (item: T) => R): R[] {
  let result: R[] = [];
  for (let item of arr) {
    result.push(mapper(item));
  }
  return result;
}

let numbers: number[] = [1, 2, 3, 4, 5];
let doubled: number[] = mapArray<number, number>(numbers, (n: number): number => n * 2);
console.info(`${doubled.join(', ')}`); // 2, 4, 6, 8, 10

let strings: string[] = ['a', 'b', 'c'];
let uppercased: string[] = mapArray<string, string>(strings, (s: string): string => s.toUpperCase());
console.info(`${uppercased.join(', ')}`); // 'A, B, C'
```

## Generic Classes and Generic Interfaces
<a id="generic-classes"></a>

Generic classes create type-safe classes that support multiple data types. Generic interfaces introduce type parameters into contract definitions, allowing one interface to accommodate multiple data types. They are commonly used for abstractions such as callbacks and repositories.

### Declaring and Instantiating Generic Classes

Declare a type parameter with `<T>` after the class name and use it in class properties and methods. When instantiating the class, specify the type argument with `new ClassName<Type>(...)`. If the types are consistent, you can omit the type argument and let the compiler infer it.

<!-- @[generic_class_basic](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Generics.ets) -->

``` TypeScript
// Basic generic class declaration
class Container<T> {
  private value: T;

  constructor(initialValue: T) {
    this.value = initialValue;
  }

  public getValue(): T {
    return this.value;
  }

  public setValue(newValue: T): void {
    this.value = newValue;
  }
}

// Explicitly specify the type parameter for instantiation.
let numberContainer: Container<number> = new Container<number>(42);
console.info(`${numberContainer.getValue()}`); // 42
numberContainer.setValue(100);
console.info(`${numberContainer.getValue()}`); // 100

// Omit the type argument and let the compiler infer it from the variable type annotation and constructor argument.
let stringContainer: Container<string> = new Container('Hello');
console.info(`${stringContainer.getValue()}`); // 'Hello'
stringContainer.setValue('World');
console.info(`${stringContainer.getValue()}`); // 'World'
```

### Properties and Methods in Generic Classes

The properties and methods of a generic class can use type parameters to implement type-safe containers and operations. For example, `add(item: T)` of `GenericCollection<T>` ensures that only elements of type `T` can be added, and the return value of `get(index: number): T` is automatically inferred as type `T` without type assertion.

<!-- @[generic_collection_class](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Generics.ets) -->

``` TypeScript
class GenericCollection<T> {
  // Generic property.
  private items: T[] = [];
  public count: number = 0;
  
  // Generic method.
  public add(item: T): void {
    this.items.push(item);
    this.count++;
  }
  
  public remove(item: T): boolean {
    let index = this.items.indexOf(item);
    if (index > -1) {
      this.items.splice(index, 1);
      this.count--;
      return true;
    }
    return false;
  }
  
  public get(index: number): T | undefined {
    return this.items[index];
  }
  
  public getAll(): T[] {
    return this.items;
  }
  
  // Generic method returning a generic type.
  public filter(predicate: (item: T) => boolean): GenericCollection<T> {
    let filtered = new GenericCollection<T>();
    this.items.forEach((item: T): void => {
      if (predicate(item)) {
        filtered.add(item);
      }
    });
    return filtered;
  }
}

let collection: GenericCollection<number> = new GenericCollection<number>();
collection.add(1);
collection.add(2);
collection.add(3);
collection.add(4);
collection.add(5);

console.info(`${collection.count}`); // 5
console.info(`${collection.get(0)}`); // 1

let evenNumbers: GenericCollection<number> = collection.filter((n: number): boolean => n % 2 === 0);
console.info(`${evenNumbers.getAll().join(', ')}`); // 2, 4
```

### Generic Classes with Multiple Type Parameters

A generic class can declare multiple type parameters (for example, `<K, V>`), which is commonly used in structures such as key-value pairs that require multiple types to work together.

<!-- @[multi_type_parameter_generic_class](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Generics.ets) -->

``` TypeScript
// Generic class with multiple type parameters.
class ParamPair<K, V> {
  private key: K;
  private value: V;
  
  constructor(key: K, value: V) {
    this.key = key;
    this.value = value;
  }
  
  public getKey(): K {
    return this.key;
  }
  
  public getValue(): V {
    return this.value;
  }
  
  public setKey(newKey: K): void {
    this.key = newKey;
  }
  
  public setValue(newValue: V): void {
    this.value = newValue;
  }
  
  public toString(): string {
    return `(${this.key}: ${this.value})`;
  }
}

let paramPair1: ParamPair<string, number> = new ParamPair<string, number>('Age', 25);
console.info(`${paramPair1.toString()}`); // '(Age: 25)'

let paramPair2: ParamPair<number, string> = new ParamPair<number, string>(1, 'One');
console.info(`${paramPair2.toString()}`); // '(1: One)'

// Complex generic class with multiple type parameters.
class Triple<A, B, C> {
  private first: A;
  private second: B;
  private third: C;
  
  constructor(first: A, second: B, third: C) {
    this.first = first;
    this.second = second;
    this.third = third;
  }
  
  public getFirst(): A {
    return this.first;
  }
  
  public getSecond(): B {
    return this.second;
  }
  
  public getThird(): C {
    return this.third;
  }
  
  public toArray(): [A, B, C] {
    return [this.first, this.second, this.third];
  }
}

let triple: Triple<string, number, boolean> = new Triple<string, number, boolean>('Hello', 42, true);
let tripleValues: [string, number, boolean] = triple.toArray();
console.info(`${tripleValues[0]}, ${tripleValues[1]}, ${tripleValues[2]}`); // 'Hello,42,true'
```

ArkTS supports tuple types (for example, `[A, B, C]`) as return types and variable types, with elements accessed by index (`tuple[0]`). However, it does not support tuple destructuring syntax (for example, `let [a, b, c] = tuple`); you must extract elements one by one through indexing.

### Declaring Generic Interfaces

Declare a type parameter with `<T>` after the interface name and use it in member signatures.

<!-- @[generic_interface_basic](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Generics.ets) -->

``` TypeScript
// Basic generic interface declaration: an interface method uses a type parameter.
interface MembershipChecker {
  contains<T>(items: T[], value: T): boolean;
}

class ArrayMembershipChecker implements MembershipChecker {
  public contains<T>(items: T[], value: T): boolean {
    return items.indexOf(value) > -1;
  }
}

// Use a generic interface as a variable type.
let membershipChecker: MembershipChecker = new ArrayMembershipChecker();

console.info(`${membershipChecker.contains<string>(['a', 'b', 'c'], 'b')}`); // true

// Use a type parameter as an interface parameter.
interface Predicate<T> {
  test(value: T): boolean;
}

class EvenNumberPredicate implements Predicate<number> {
  public test(value: number): boolean {
    return value % 2 === 0;
  }
}

let isEven: Predicate<number> = new EvenNumberPredicate();

console.info(`${isEven.test(42)}`); // true
```

### Generic Interface as a Function Type Constraint

Use a generic interface to describe a callback or function signature so that the type parameters of the callback remain consistent with the concrete implementation.

<!-- @[generic_interface_callback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Generics.ets) -->

``` TypeScript
// Define a function type with a generic interface.
interface Callback<T> {
  invoke(result: T): void;
}

interface AsyncCallback<T> {
  invoke(result: T): Promise<void>;
}

// Constrain a function type with a generic interface.
function processData<T>(data: T, callback: Callback<T>): void {
  callback.invoke(data);
}

class StringCallback implements Callback<string> {
  public invoke(result: string): void {
    console.info(`Processed: ${result}`);
  }
}

class NumberCallback implements Callback<number> {
  public invoke(result: number): void {
    console.info(`Processed: ${result}`);
  }
}

processData<string>('Hello', new StringCallback());

processData<number>(42, new NumberCallback());

// Use a generic interface in an asynchronous function.
async function processAsyncData<T>(data: T, callback: AsyncCallback<T>): Promise<void> {
  await callback.invoke(data);
}

class AsyncStringCallback implements AsyncCallback<string> {
  public async invoke(result: string): Promise<void> {
    console.info(`Async processed: ${result}`);
  }
}

processAsyncData<string>('Hello', new AsyncStringCallback());
```

### Generic Interface as a Class Implementation Constraint

When a class implements a generic interface, it must specify concrete type parameters, which uniformly constrain the method signatures and entity types exposed by the class.

<!-- @[generic_interface_repository](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Generics.ets) -->

``` TypeScript
interface Repository<T> {
  findById(id: number): T | null;
  findAll(): T[];
  save(entity: T): void;
  delete(id: number): void;
}

interface User {
  id: number;
  name: string;
  email: string;
}

class UserRepository implements Repository<User> {
  private users: User[] = [];
  
  public findById(id: number): User | null {
    return this.users.find((user: User): boolean => user.id === id) ?? null;
  }
  
  public findAll(): User[] {
    return [...this.users];
  }
  
  public save(entity: User): void {
    let existing: User | null = this.findById(entity.id);
    if (existing !== null) {
      let index = this.users.indexOf(existing);
      this.users[index] = entity;
    } else {
      this.users.push(entity);
    }
  }
  
  public delete(id: number): void {
    this.users = this.users.filter((user: User): boolean => user.id !== id);
  }
}

let userRepo = new UserRepository();

userRepo.save({ id: 1, name: 'Alice', email: 'alice@example.com' });
userRepo.save({ id: 2, name: 'Bob', email: 'bob@example.com' });

console.info(`${userRepo.findAll().length}`); // 2
console.info(`${userRepo.findById(1)?.name}`); // 'Alice'

userRepo.delete(1);
console.info(`${userRepo.findAll().length}`); // 1
```

### Default Type Parameters of Generic Interfaces

A generic interface uses its default type parameter when no type is specified, which simplifies the call.

<!-- @[generic_interface_default_type](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Generics.ets) -->

``` TypeScript
// Default type parameters of a generic interface
interface ApiResponse<T = string> {
  data: T;
  status: number;
  message: string;
}

// Use the default type: T is string.
let response1: ApiResponse = {
  data: 'OK',
  status: 200,
  message: 'Success'
};

// Specify a concrete type to override the default: T is number.
let response2: ApiResponse<number> = {
  data: 42,
  status: 200,
  message: 'Success'
};

console.info(`${response1.data}`);
console.info(`${response2.data}`);

// Default values for multiple type parameters.
interface DefaultPair<T = string, U = number> {
  first: T;
  second: U;
}

let defaultPair1: DefaultPair = { first: 'Hello', second: 42 };
let defaultPair2: DefaultPair<number> = { first: 100, second: 200 };
let pair3: DefaultPair<number, string> = { first: 100, second: 'Hello' };

console.info(`${defaultPair1}`);
console.info(`${defaultPair2}`);
console.info(`${pair3}`);
```

## Generic Constraints

Generic constraints address two relationships between generics and the subtype system: variance annotations declare how subtype relationships between type arguments carry over to generic types themselves, while subtype constraints use `extends` to require a type argument to be a subtype of a specified type.

### Variance Annotations

The basic concept of subtyping (S is a subtype of T if any value of type S can be safely assigned to a variable of type T) is described in [Subtyping](arkts-language-guide-types.md#subtyping). Variance describes how this relationship carries over from type arguments to generic types: covariance (`out`) preserves the direction, so `Producer<Cat>` is a subtype of `Producer<Animal>`; contravariance (`in`) reverses the direction, so `Consumer<Animal>` is a subtype of `Consumer<Cat>`; invariance (`in out`) means that there is no subtype relationship between the generic types.

ArkTS supports the `in`/`out`/`in out` syntax for variance annotations.

<!-- @[variance_annotations](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Generics.ets) -->

``` TypeScript
interface VaConsumer<in T> {
  consume(arg: T): void;
}

interface VaProducer<out T> {
  make(): T;
}

interface VaProducerConsumer<in out T> {
  consume(arg: T): void;
  make(): T;
}

class VaAnimal {
  public name: string;

  constructor(name: string) {
    this.name = name;
  }
}

class VaDog extends VaAnimal {
  public breed: string;

  constructor(name: string, breed: string) {
    super(name);
    this.breed = breed;
  }
}

// Covariance (out): VaProducer<VaDog> is a subtype of VaProducer<VaAnimal>.
class VaDogFactory implements VaProducer<VaDog> {
  public make(): VaDog {
    return new VaDog('Buddy', 'Golden Retriever');
  }
}

let vaAnimalFactory: VaProducer<VaAnimal> = new VaDogFactory();
console.info(`${vaAnimalFactory.make().name}`); // 'Buddy'

// Contravariance (in): VaConsumer<VaAnimal> is a subtype of VaConsumer<VaDog>.
class VaAnimalFeeder implements VaConsumer<VaAnimal> {
  public consume(arg: VaAnimal): void {
    console.info(`Feeding: ${arg.name}`);
  }
}

let vaDogFeeder: VaConsumer<VaDog> = new VaAnimalFeeder();
vaDogFeeder.consume(new VaDog('Max', 'Beagle')); // Feeding: Max

// Invariance (in out): neither VaProducerConsumer<VaAnimal> nor VaProducerConsumer<VaDog> is a subtype of the other. Assigning one to the other causes a compilation error.
```

ArkTS generics are invariant by default. Variance must be explicitly annotated with `in`/`out`/`in out`, and the compiler checks whether the annotations are valid.

### Subtype Constraints

Constraints are imposed on type parameters via `extends`, restricting them to interfaces or structures they must satisfy, thereby striking a balance between flexibility and type safety in generics.

Use `<T extends SomeInterface>` to constrain a type parameter to a specific structure (such as the `length` property). A compilation error is reported if the constraint is not satisfied.

<!-- @[ts_generic_constraint_length](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Generics.ts) -->

``` TypeScript
// Constrain the generic parameter to have the length property.
interface Lengthwise {
  length: number;
}

function getLength<T extends Lengthwise>(arg: T): number {
  return arg.length;
}

class LengthSample implements Lengthwise {
  public length: number;

  constructor(length: number) {
    this.length = length;
  }
}

console.info(`${getLength('Hello')}`);        // 5
console.info(`${getLength([1, 2, 3])}`);      // 3
console.info(`${getLength(new LengthSample(10))}`); // 10

// Compilation error: the number type has no length property.
console.info(`${getLength(42)}`);
```

Constrain a type parameter to an interface or class to ensure that the methods defined by that interface can be called within the generic function.

<!-- @[ts_generic_constraint_serializable](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Generics.ts) -->

``` TypeScript
interface Serializable {
  serialize(): string;
}

class User implements Serializable {
  public name: string;
  public age: number;

  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }

  public serialize(): string {
    return JSON.stringify({ name: this.name, age: this.age });
  }
}

class Product implements Serializable {
  public id: number;
  public title: string;

  constructor(id: number, title: string) {
    this.id = id;
    this.title = title;
  }

  public serialize(): string {
    return JSON.stringify({ id: this.id, title: this.title });
  }
}

// Constrain the generic parameter to implement the Serializable interface.
function saveToStorage<T extends Serializable>(entity: T): void {
  let serialized = entity.serialize();
  console.info(`Saving: ${serialized}`);
}

let user = new User('Alice', 25);
let product = new Product(1, 'Laptop');

saveToStorage(user);    // Saving: {"name":"Alice","age":25}
saveToStorage(product); // Saving: {"id":1,"title":"Laptop"}

// Compilation error: the number type has no serialize method.
saveToStorage(42);
```

Define the required set of properties through an interface to require a type argument to have all of these properties.

<!-- @[generic_constraint_property](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Generics.ets) -->

``` TypeScript
interface HasId {
  id: number;
}

interface HasName {
  name: string;
}

// Constrain the generic parameter to include the id property.
function findById<T extends HasId>(items: T[], id: number): T | null {
  for (let item of items) {
    if (item.id === id) {
      return item;
    }
  }
  return null;
}

// Constrain the generic parameter to include the name property.
function findByName<T extends HasName>(items: T[], name: string): T | null {
  for (let item of items) {
    if (item.name === name) {
      return item;
    }
  }
  return null;
}

interface ConstraintUser extends HasId, HasName {
  email: string;
}

let users: ConstraintUser[] = [
  { id: 1, name: 'Alice', email: 'alice@example.com' },
  { id: 2, name: 'Bob', email: 'bob@example.com' },
  { id: 3, name: 'Charlie', email: 'charlie@example.com' }
];

let userById: ConstraintUser | null = findById<ConstraintUser>(users, 1);
let userByName: ConstraintUser | null = findByName<ConstraintUser>(users, 'Bob');
console.info(`${userById ? userById.name : ''}`);    // 'Alice'
console.info(`${userByName ? userByName.id : 0}`); // 2
```

## When to Use

Generics are commonly used for general-purpose data structures, utility functions, and network request wrappers.

### Generic Data Structures

Generic data structures (queues, stacks, linked lists, and more) work with any element type.

<!-- @[generic_data_structures](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Generics.ets) -->

``` TypeScript
// Generic queue data structure.
class Queue<T> {
  private items: T[] = [];
  
  enqueue(item: T): void {
    this.items.push(item);
  }
  
  dequeue(): T | undefined {
    return this.items.shift();
  }
  
  front(): T | undefined {
    return this.items[0];
  }
  
  isEmpty(): boolean {
    return this.items.length === 0;
  }
  
  size(): number {
    return this.items.length;
  }
}

let stringQueue = new Queue<string>();
stringQueue.enqueue('First');
stringQueue.enqueue('Second');
stringQueue.enqueue('Third');

console.info(`${stringQueue.dequeue()}`); // 'First'
console.info(`${stringQueue.front()}`);   // 'Second'
console.info(`${stringQueue.size()}`);    // 2
```

### Generic Utility Functions

Generic utility functions such as `map` and `filter` work with collections of any type.

<!-- @[generic_array_utilities](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Generics.ets) -->

``` TypeScript
// Generic array utility function
function utilitiesFirst<T>(arr: T[]): T | undefined {
  return arr[0];
}

function last<T>(arr: T[]): T | undefined {
  return arr[arr.length - 1];
}

function shuffle<T>(arr: T[]): T[] {
  let result = [...arr];
  for (let i = result.length - 1; i > 0; i--) {
    let j = Math.floor(Math.random() * (i + 1));
    let temp: T = result[i];
    result[i] = result[j];
    result[j] = temp;
  }
  return result;
}

function unique<T>(arr: T[]): T[] {
  return Array.from(new Set(arr));
}

let utilitiesNumbers: number[] = [1, 2, 3, 4, 5, 3, 2];
let utilitiesStrings: string[] = ['a', 'b', 'c', 'b', 'a'];

let firstResult: number | undefined = utilitiesFirst(utilitiesNumbers);
console.info(`${firstResult}`);  // 1

let lastResult: string | undefined = last(utilitiesStrings);
console.info(`${lastResult}`);  // 'a'

let shuffled: number[] = shuffle(utilitiesNumbers);
console.info(`${shuffled.join(', ')}`);  // Randomly shuffle

let uniqueNumbers: number[] = unique(utilitiesNumbers);
console.info(`${uniqueNumbers.join(', ')}`);  // 1, 2, 3, 4, 5

let uniqueStrings: string[] = unique(utilitiesStrings);
console.info(`${uniqueStrings.join(', ')}`);  // 'a, b, c'

interface UtilitiesUser {
  id: number;
  name: string;
  email: string;
}

let utilitiesUser: UtilitiesUser = {
  id: 1,
  name: 'Alice',
  email: 'alice@example.com'
};

// In ArkTS, prefer explicit property access and avoid relying on keyof and indexed access types
function renameUser(target: UtilitiesUser, newName: string): void {
  target.name = newName;
}

console.info(`${utilitiesUser.name}`);  // 'Alice'
renameUser(utilitiesUser, 'Bob');
console.info(`${utilitiesUser.name}`);  // 'Bob'
```

### Component Encapsulation

Generic components use type parameters to describe structures such as `props` and `render`, allowing the same component to accommodate multiple data types without losing type safety.

<!-- @[generic_ui_components](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Generics.ets) -->

``` TypeScript
// Generic list component.
interface ListComponentProps<T> {
  items: T[];
  renderItem: (item: T, index: number) => string;
  onItemClick?: (item: T, index: number) => void;
}

class ListComponent<T> {
  private props: ListComponentProps<T>;
  
  constructor(props: ListComponentProps<T>) {
    this.props = props;
  }
  
  render(): string {
    let itemsHtml = this.props.items.map((item, index) =>
      this.props.renderItem(item, index)
    ).join('');
    
    return `<ul>${itemsHtml}</ul>`;
  }
  
  handleClick(index: number): void {
    if (this.props.onItemClick) {
      this.props.onItemClick(this.props.items[index], index);
    }
  }
}

interface ComponentsUser {
  id: number;
  name: string;
  email: string;
}

let componentsUsers: ComponentsUser[] = [
  { id: 1, name: 'Alice', email: 'alice@example.com' },
  { id: 2, name: 'Bob', email: 'bob@example.com' },
  { id: 3, name: 'Charlie', email: 'charlie@example.com' }
];

let userList = new ListComponent<ComponentsUser>({
  items: componentsUsers,
  renderItem: (user) => `<li>${user.name} (${user.email})</li>`,
  onItemClick: (user) => console.info(`Clicked: ${user.name}`)
});

console.info(`${userList.render()}`);

// Generic table component.
interface TableColumn<T> {
  header: string;
  getValue: (row: T) => string;
}

interface TableComponentProps<T> {
  columns: TableColumn<T>[];
  data: T[];
}

class TableComponent<T> {
  private props: TableComponentProps<T>;
  
  constructor(props: TableComponentProps<T>) {
    this.props = props;
  }
  
  render(): string {
    let headerHtml = this.props.columns.map(col =>
      `<th>${col.header}</th>`
    ).join('');
    
    let bodyHtml = this.props.data.map(row => {
      let cells = this.props.columns.map(col => {
        return `<td>${col.getValue(row)}</td>`;
      }).join('');
      return `<tr>${cells}</tr>`;
    }).join('');
    
    return `<table><thead><tr>${headerHtml}</tr></thead><tbody>${bodyHtml}</tbody></table>`;
  }
}

let userTable = new TableComponent<ComponentsUser>({
  columns: [
    { header: 'ID', getValue: (row: ComponentsUser): string => row.id.toString() },
    { header: 'Name', getValue: (row: ComponentsUser): string => row.name },
    { header: 'Email', getValue: (row: ComponentsUser): string => row.email }
  ],
  data: componentsUsers
});

console.info(`${userTable.render()}`);
```

### Encapsulating API Requests

Use generics to encapsulate network requests and uniformly handle the request and response types of different APIs.

<!-- @[generic_api_client](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Generics.ets) -->

``` TypeScript
interface ClientApiResponse<T> {
  data: T;
  status: number;
  message: string;
}

class ApiClient {
  private baseUrl: string;

  constructor(baseUrl: string) {
    this.baseUrl = baseUrl;
  }

  async get<T>(endpoint: string): Promise<ClientApiResponse<T>> {
    let url: string = `${this.baseUrl}${endpoint}`;
    let result: string = await this.mockRequest(url);
    let data: T = JSON.parse(result) as T;
    return { data: data, status: 200, message: 'Success' };
  }

  async post<T, U>(endpoint: string, body: T): Promise<ClientApiResponse<U>> {
    let url: string = `${this.baseUrl}${endpoint}`;
    let result: string = await this.mockRequest(url);
    let data: U = JSON.parse(result) as U;
    return { data: data, status: 200, message: 'Success' };
  }

  private mockRequest(url: string): Promise<string> {
    return new Promise<string>((resolve: (value: string) => void): void => {
      setTimeout(() => {
        resolve(JSON.stringify({ id: 1, name: 'Alice', email: 'alice@example.com' }));
      }, 100);
    });
  }
}

interface ClientUser {
  id: number;
  name: string;
  email: string;
}

interface CreateUserRequest {
  name: string;
  email: string;
}

let gacClient: ApiClient = new ApiClient('EXAMPLE_API_URL');

async function gacFetchUser(id: number): Promise<void> {
  try {
    let response: ClientApiResponse<ClientUser> = await gacClient.get<ClientUser>(`/users/${id}`);
    console.info(`${response.data.name}`); // 'Alice'
  } catch (error) {
    console.error(`Error: ${(error as Error).message}`);
  }
}

async function gacCreateUser(name: string, email: string): Promise<void> {
  try {
    let request: CreateUserRequest = { name: name, email: email };
    let response: ClientApiResponse<ClientUser> = await gacClient.post<CreateUserRequest, ClientUser>('/users', request);
    console.info(`${response.data.id}`); // 1
  } catch (error) {
    console.error(`Error: ${(error as Error).message}`);
  }
}

gacFetchUser(1);
gacCreateUser('Alice', 'alice@example.com');
```
