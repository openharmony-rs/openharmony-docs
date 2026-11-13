---
kits: ["ArkTS Kit"]
description: "ArkTS built-in and custom types, covering type aliases, union types, type operators, subtype relationships, type guards, and type assertions."
keywords: [ArkTS, types, built-in types, type aliases, union types, type guards, type assertions]
doctype: guide
status: active
---

# Types
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @jokerxd-liu-->
<!--Designer: @jokerxd-liu-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=8923bda514baa1452b967ea964ea779c7417bd8e translatedAt=2026-11-12T12:34:02.444Z nl=1 -->

Types constrain the possible values and operations of variables, parameters, and return values. ArkTS strengthens static checking and null safety on top of TypeScript's type system. This topic describes built-in and custom types, differences between value and reference types, type operators, subtype relationships, type guards, and type assertions.

## Built-in Types

Built-in types are predefined by the language and can be used without importing them. ArkTS provides the following built-in types:

| Type | Description |
| --- | --- |
| `number` | Numeric values, with a unified representation for integers and floating-point numbers |
| `boolean` | Logical values: `true` or `false` |
| `string` | Strings |
| `void` | No function return value |
| `null` / `undefined` | Null / undefined values |
| Literal types | Specific literal values used as types |
| `object` / `Object` | Non-primitive types / root type of all non-null types |

### number, boolean, string

`number` represents IEEE 754 double-precision floating-point numbers (64-bit), with no separate integer type. It supports decimal, hexadecimal, binary, and octal literals. `boolean` represents logical values produced by comparison and logical operations. `string` represents strings. For details, see [Strings](arkts-language-guide-strings.md).

<!-- @[builtin_primitive_types](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/TypeConversion.ets) -->

``` TypeScript
// number: unified representation for integers and floating-point numbers.
let age: number = 25;
let price: number = 9.99;
let hex: number = 0xFF; // Hexadecimal literal.

// boolean: logical values.
let enabled: boolean = true;

// string: strings.
let appName: string = 'ArkTS';
```

### void

`void` indicates that a function has no return value and is used for functions that perform operations without returning results. It differs from `undefined`: `void` describes a function's return type, while `undefined` indicates an undefined value.

<!-- @[void_type_basic](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/TypeConversion.ets) -->

``` TypeScript
function log(message: string): void {
  console.info(`${message}`);
}
```

### null and undefined

`null` represents an intentionally assigned null value, while `undefined` indicates an unassigned variable or a missing property. Distinguish these meanings explicitly. Prefer `undefined` for an absent value and use `null` only when null semantics are explicitly needed. ArkTS enables null safety by default: `null` and `undefined` cannot be assigned to non-nullable types (`let name: string = null` is a compilation error). Before accessing nullable values, use a null check, optional chaining (?.), or nullish coalescing (??). For details, see [Basics](arkts-language-guide-basics.md).

<!-- @[null_undefined_types_basic](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/TypeConversion.ets) -->

``` TypeScript
// null: explicitly indicate a null value.
let nickname: string | null = null;

// undefined: an undefined value; an optional property's implicit type is T | undefined.
interface NullableUserProfile {
  name: string;
  email?: string;
}

let nullableUser: NullableUserProfile = { name: 'Alice' };
```

### Literal Types

Literal types use values themselves as types, restricting variables to specific literal values. They are often combined with union types to constrain possible values. Constants declared with `const` are inferred as literal types; for example, `const pi = 3.14` is inferred as `3.14`.

<!-- @[literal_type_basic](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/TypeConversion.ets) -->

``` TypeScript
type TaskState = 'pending' | 'running' | 'done';

let state: TaskState = 'pending';
// state = 'finished'; // Compilation error: 'finished' is not a member of TaskState.
```

### object and Object

`object` represents non-primitive types, including reference types such as objects, arrays, and class instances. `Object` is the root type of all non-null types: any value other than `null` or `undefined` can be assigned to an `Object` variable. Variables of type `object` or `Object` can access only members common to all types; narrow the type or use an assertion before accessing specific members. In addition, object literals cannot directly initialize `Object` or `object` variables and must correspond to an explicitly declared class or interface. For details, see [TypeScript to ArkTS Cookbook](typescript-to-arkts-migration-guide.md#object-literal-must-correspond-to-some-explicitly-declared-class-or-interface).

<!-- @[object_object_type](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/TypeConversion.ets) -->

``` TypeScript
interface Point {
  x: number;
  y: number;
}

// object: non-primitive types.
let point: Point = { x: 1, y: 2 };
let ref: object = point;

// Object: root type of all non-null types.
let boxed: Object = 'hello';
let boxedObj: Object = point;

// Narrow an Object value before accessing specific members.
if (typeof boxed === 'string') {
  console.info(`${boxed.length}`); // 5
}
```

ArkTS also provides types such as `never` (values that never occur, such as the return type of a function that always throws), `bigint` (arbitrary-precision integers), and arrays (`T[]`). For details, see [Basics](arkts-language-guide-basics.md) and [Collection Types](arkts-language-guide-collection-types.md).

## Custom Types

Combine built-in types or declare new types to model business data. Type aliases (`type`) give any type a new name and are often used with union and function types. Classes, interfaces, and enums have dedicated topics; only simple examples are provided here.

### Type Aliases

A type alias uses `type` to give an existing type a new name without creating a new type. It commonly provides meaningful names for complex types such as union and function types, or business-specific names for primitive types.

<!-- @[type_alias_basic](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/TypeConversion.ets) -->

``` TypeScript
// Alias a primitive type to clarify its meaning.
type AccountId = number;
let accountId: AccountId = 1001;

// Alias a union of literal types to constrain possible values.
type SortOrder = 'asc' | 'desc';
let order: SortOrder = 'asc';

console.info(`${accountId}`);  // 1001
console.info(`${order}`);      // 'asc'
```

### Union Types

A union type represents a value that can be one of several types separated by a vertical bar (`|`). Only members common to all constituent types can be accessed directly. To access type-specific members, first narrow the type with a type guard (see [Type Guards](#type-guards)). Nullable types (`T | null`) and optional properties (`prop?: T`, equivalent to `T | undefined`) are common uses of union types.

<!-- @[union_type_basic](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/TypeConversion.ets) -->

``` TypeScript
type ID = string | number;

let userId: ID = 'A-001';
userId = 100; // Can also be a number.

function printId(id: ID): void {
  if (typeof id === 'string') {
    console.info(`${id.toUpperCase()}`); // string-specific member.
  } else {
    console.info(`${id.toFixed(0)}`);    // number-specific member.
  }
}
```

### Function Types

A function type describes a function signature in the form `(parameterList) => ReturnType`. Functions can be assigned to variables and passed as arguments. For details, see [Functions](arkts-language-guide-functions.md).

<!-- @[function_type_basic](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/TypeConversion.ets) -->

``` TypeScript
type Comparator = (a: number, b: number) => number;

let ascending: Comparator = (a: number, b: number): number => {
  return a - b;
};

console.info(`${ascending(3, 1)}`); // 2
```

### Enum Types

An enum type defines a set of named constant values, making fixed states easier to express meaningfully.

<!-- @[enum_type_basic](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/TypeConversion.ets) -->

``` TypeScript
enum MyColor {
  Red,
  Green,
  Blue
}

let favorite: MyColor = MyColor.Blue;
```

For details, see [Enums](arkts-language-guide-enums.md).

### Interfaces

An interface defines an object's structural contract, describing property names, types, and optionality.

<!-- @[interface_type_basic](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/TypeConversion.ets) -->

``` TypeScript
interface MyPosition {
  x: number;
  y: number;
}

let origin: MyPosition = { x: 0, y: 0 };
```

For details, see [Interfaces](arkts-language-guide-interfaces.md).

### Classes

A class defines both data structure and behavior and is the only custom type whose instances can be created with `new`.

<!-- @[class_type_basic](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/TypeConversion.ets) -->

``` TypeScript
class MyRectangle {
  public width: number;
  public height: number;

  constructor(width: number, height: number) {
    this.width = width;
    this.height = height;
  }

  public getArea(): number {
    return this.width * this.height;
  }
}

let rect: MyRectangle = new MyRectangle(3, 4);
console.info(`${rect.getArea()}`); // 12
```

For details, see [Classes](arkts-language-guide-classes.md).

## Value Types and Reference Types

ArkTS types fall into two categories by memory allocation and access. Value types (primitive types such as `number`, `boolean`, `string`, `null`, and `undefined`) store values directly, and assignment copies the values themselves. Reference types (objects, arrays, class instances, functions, and so on) store object references; assignment copies the reference, so multiple variables point to the same object.

### Differences in Assignment Behavior

After value-type assignment, the two variables are independent: modifying one does not affect the other. After reference-type assignment, they share the same object.

<!-- @[value_reference_assignment](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/TypeConversion.ets) -->

``` TypeScript
// Value type: assignment copies the value; the two variables are independent.
let countA: number = 10;
let countB: number = countA;
countB = 20;
console.info(`${countA}`); // 10 (unaffected by countB)

// Reference type: assignment copies the reference; both variables point to the same object.
interface Score {
  value: number;
}

let scoreA: Score = { value: 90 };
let scoreB: Score = scoreA;
scoreB.value = 95;
console.info(`${scoreA.value}`); // 95 (scoreA also changes)
```

### Effects of State Changes on the Original Object

Changes to object state through any reference are visible through all references to that object. The same applies to function arguments: for reference types, changes inside the function affect the original object's state; for value types, the function operates only on a copy and does not affect the external variable. To copy an object instead of sharing a reference, use a shallow or deep copy. For details, see [Classes](arkts-language-guide-classes.md#basic-concepts).

<!-- @[value_reference_mutation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/TypeConversion.ets) -->

``` TypeScript
class Task {
  public status: string = 'pending';
}

// Reference-type parameter: modify the original object's state inside the function.
function start(task: Task): void {
  task.status = 'running';
}

let myTask: Task = new Task();
start(myTask);
console.info(`${myTask.status}`); // running (original object modified)

// Value-type parameter: modify only a copy inside the function.
function double(value: number): number {
  value = value * 2; // Modify only the copy.
  return value;
}

let count: number = 10;
double(count);
console.info(`${count}`); // 10 (unchanged)
```

## Type Operators

ArkTS supports a small set of utility types for transforming existing types: `Partial<T>`, `Required<T>`, `Readonly<T>`, and `Record<K, V>`. Other TypeScript utility types, such as `Pick<T, K>` and `Omit<T, K>`, are not supported. For details, see [TypeScript to ArkTS Cookbook](typescript-to-arkts-migration-guide.md#some-utility-types-are-not-supported).

### Partial and Required

`Partial<T>` makes all properties of `T` optional and suits objects representing partial updates. `Required<T>` makes all properties of `T` required. The generic argument `T` of `Partial<T>` must be a class or interface type.

<!-- @[partial_required_types](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/TypeConversion.ets) -->

``` TypeScript
interface UserProfile {
  id: number;
  name: string;
  email: string;
}

// Partial<T>: make all properties optional.
let patch: Partial<UserProfile> = { name: 'Alice' };

interface PageQuery {
  keyword?: string;
  pageSize?: number;
}

// Required<T>: make all properties required.
let strictQuery: Required<PageQuery> = { keyword: 'arkts', pageSize: 20 };
```

### Readonly

`Readonly<T>` makes all properties of `T` read-only, preventing changes after initialization. Individual read-only class properties can also be declared with `readonly`.

<!-- @[readonly_type_operator](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/TypeConversion.ets) -->

``` TypeScript
interface AppConfig {
  appId: string;
  version: string;
}

let config: Readonly<AppConfig> = { appId: 'com.example.app', version: '1.0.0' };
// config.version = '1.0.1'; // Compilation error: the property is read-only.
```

### Record

`Record<K, V>` maps key type `K` to value type `V` and suits key-value structures. Indexed access to a `Record` object's value produces a union type that includes `undefined`. For more uses of `Record`, see [Collection Types](arkts-language-guide-collection-types.md).

<!-- @[record_type_operator](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/TypeConversion.ets) -->

``` TypeScript
interface CityInfo {
  country: string;
  population: number;
}

let cityMap: Record<string, CityInfo> = {
  'Beijing': { country: 'China', population: 21860000 }
};

let info: CityInfo | undefined = cityMap['Beijing']; // The indexed access result includes undefined.
```

TypeScript type operations such as intersection types, conditional types, mapped types, and indexed access types (`T[K]`) are not supported in ArkTS. In generic scenarios, prefer explicit interfaces, classes, or generic constraints to describe structures. For details, see [Generics](arkts-language-guide-generics.md).

## Subtyping

If any value of type `S` can be safely assigned to a variable of type `T`, `S` is a subtype of `T`. ArkTS does not support structural typing (duck typing): the compiler does not determine compatibility by comparing type structures. Subtype relationships are based on explicit inheritance and `implements` relationships. For details, see [TypeScript to ArkTS Cookbook](typescript-to-arkts-migration-guide.md#structural-typing-is-not-supported).

### Parent and Child Classes

A subclass is a subtype of its parent class. A subclass instance can be implicitly assigned to a parent-type variable (upcasting), after which only members declared in the parent are accessible. Assigning a parent-type variable to a subclass variable (downcasting) is not type-safe and requires an `as` assertion. Check the actual type with `instanceof` first.

<!-- @[subtype_class_hierarchy](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/TypeConversion.ets) -->

``` TypeScript
class Creature {
  public name: string;

  constructor(name: string) {
    this.name = name;
  }

  public speak(): void {
    console.info(`${this.name} makes a sound`);
  }
}

class Hound extends Creature {
  public breed: string;

  constructor(name: string, breed: string) {
    super(name);
    this.breed = breed;
  }

  public bark(): void {
    console.info(`${this.name} barks: Woof!`);
  }
}

// Upcasting: implicitly assign a subclass instance to a parent-type variable.
let hound: Hound = new Hound('Buddy', 'Golden Retriever');
let creature: Creature = hound;
creature.speak(); // 'Buddy makes a sound'
// creature.bark(); // Compilation error: a parent-type variable cannot access subclass-specific members.

// Downcasting: check the actual type first.
if (creature instanceof Hound) {
  let myHound: Hound = creature; // Automatically narrowed within the guarded branch.
  myHound.bark();            // 'Buddy barks: Woof!'
}
```

The same applies to implementing classes and interfaces: an instance of a class that declares `implements` can be implicitly assigned to an interface-type variable; the reverse requires an assertion.

### Subtype Relationships of Function Types

Assigning a function to a function-type variable must satisfy function subtyping rules: the source function can have fewer parameters, but not more; its parameter types can be supertypes of the target parameter types (parameter contravariance); its return type must be a subtype of the target return type (return type covariance).

<!-- @[subtype_function_type](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/TypeConversion.ets) -->

``` TypeScript
class BaseType {}
class SubType extends BaseType {}

// Target function type: (SubType) => BaseType
type Handler = (input: SubType) => BaseType;

// Supertype parameter (contravariance) and subtype return value (covariance) satisfy subtyping rules.
let handler: Handler = (input: BaseType): SubType => {
  return new SubType();
};

// A function with fewer parameters can be assigned to a function type with more parameters.
type BinaryOp = (a: number, b: number) => number;
let doubleFn: BinaryOp = (a: number): number => a * 2;
```

### Subtype Relationships of Union Types

Each constituent type of a union is a subtype of that union, so both `string` and `number` values can be assigned to a `string | number` variable. Conversely, a union is not a subtype of its constituents: a `string | number` value cannot be assigned to a `string` variable.

<!-- @[subtype_union_type](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/TypeConversion.ets) -->

``` TypeScript
type Identifier = string | number;

// Both string and number are subtypes of Identifier.
let id: Identifier = 'A-001';
id = 100;

let displayName: string = 'Alice';
id = displayName;    // OK: string is a subtype of string | number.
// displayName = id; // Compilation error: string | number is not a subtype of string.
```

## Type Guards

Type guards check a value's actual type at runtime and narrow a union to a specific type at compile time. In a branch where the guard holds, type-specific members can be accessed directly without an assertion. Unlike assertions, guards perform actual runtime checks and provide a safer way to narrow types.

### typeof Type Guard

`typeof` checks basic types and commonly narrows unions of primitive types such as `string`, `number`, and `boolean`.

<!-- @[typeof_type_guard](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/TypeConversion.ets) -->

``` TypeScript
function typeGuardProcessValue(value: string | number | boolean): void {
  if (typeof value === 'string') {
    // The compiler knows value is a string.
    console.info(`String length: ${value.length}`);
    console.info(`Uppercase: ${value.toUpperCase()}`);
  } else if (typeof value === 'number') {
    // The compiler knows value is a number.
    console.info(`Number: ${value.toFixed(2)}`);
    console.info(`Square: ${value * value}`);
  } else if (typeof value === 'boolean') {
    // The compiler knows value is a boolean.
    console.info(`Boolean: ${value ? 'True' : 'False'}`);
  }
}

typeGuardProcessValue('Hello');  // String length: 5, Uppercase: HELLO
typeGuardProcessValue(42);       // Number: 42.00, Square: 1764
typeGuardProcessValue(true);     // Boolean: True
```

### instanceof Type Guard

`instanceof` checks whether an object is an instance of a class by matching along the prototype chain. Within a guarded branch, it narrows the type to that class, allowing safe access to class-specific members. It is also commonly used to check the actual type before downcasting (see [Subtyping](#subtyping)).

<!-- @[instanceof_type_guard](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/TypeConversion.ets) -->

``` TypeScript
class TypeGuardDog {
  public name: string;

  constructor(name: string) {
    this.name = name;
  }

  public bark(): void {
    console.info(`${this.name} barks: Woof!`);
  }
}

class Cat {
  public name: string;

  constructor(name: string) {
    this.name = name;
  }

  public meow(): void {
    console.info(`${this.name} meows: Meow!`);
  }
}

function makeSound(pet: TypeGuardDog | Cat): void {
  console.info(`Pet name: ${pet.name}`);

  if (pet instanceof TypeGuardDog) {
    // The compiler knows pet is a TypeGuardDog.
    pet.bark();
  } else if (pet instanceof Cat) {
    // The compiler knows pet is a Cat.
    pet.meow();
  }
}

let myDog = new TypeGuardDog('Buddy');
let myCat = new Cat('Whiskers');

makeSound(myDog); // Pet name: Buddy, Buddy barks: Woof!
makeSound(myCat); // Pet name: Whiskers, Whiskers meows: Meow!
```

## Type Assertions

A type assertion tells the compiler to treat a value as a specified type. In ArkTS, `as` is the only assertion syntax (`value as Type`); TypeScript's angle-bracket syntax `<Type>value` is not supported. For details, see [TypeScript to ArkTS Cookbook](typescript-to-arkts-migration-guide.md#only-the-as-t-syntax-is-supported-for-type-casting).

### as Keyword Syntax

Assertions are commonly used for downcasting from a supertype to a subtype or treating a broadly typed value as a specific type.

<!-- @[as_type_assertion](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/TypeConversion.ets) -->

``` TypeScript
interface UserInfo {
  id: number;
  name: string;
}

let user: UserInfo = { id: 1, name: 'Alice' };

// Upcasting: implicit conversion from subtype to supertype.
let obj: Object = user;

// Downcasting: use an as assertion from supertype to subtype.
let restored: UserInfo = obj as UserInfo;
console.info(`${restored.name}`); // 'Alice'

// Assert a union type.
let mixed: Object = 42;
let unionValue: number | string = mixed as number | string;
```

### Type Assertions vs. Data Conversion

A type assertion does not change the value itself; it only treats it as the target type. Data conversion, such as `Number()` or `String()`, actually changes the value's type at runtime. To change a data type, use a conversion function, not an assertion.

<!-- @[assertion_vs_conversion](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/TypeConversion.ets) -->

``` TypeScript
let convValue: Object = '123';

// Type assertion: keep the value unchanged and treat it as the target type.
let text: string = convValue as string; // The runtime value is a string, so the assertion succeeds.
console.info(`${text.length}`);     // 3

// Data conversion: actually convert the data type at runtime.
let num: number = Number('123');
console.info(`${num.toFixed(2)}`); // 123.00
```

### Constraints on Type Assertions

Type assertions have two constraints: at compile time, assertions between unrelated types are prohibited; at runtime, a mismatch between the asserted and actual types throws `ClassCastException`. Prefer type guards for narrowing, since no assertion is needed within a guarded branch. If an assertion is necessary, first ensure that the actual type matches the asserted type.

<!-- @[assertion_runtime_check](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/TypeConversion.ts) -->

``` TypeScript
let checkValue: Object = 'hello';

// Throws ClassCastException at runtime: the actual string type does not match the asserted number type.
// let wrong: number = checkValue as number;

// Correct approach: check the actual type first.
if (typeof checkValue === 'string') {
  console.info(`${checkValue.length}`); // 5
}
```
