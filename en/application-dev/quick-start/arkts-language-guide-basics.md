---
kits: ["ArkTS Kit"]
description: "ArkTS basics, including constants and variables, comments, semicolons, type declarations and annotations, type inference, nullable types, non-null assertions, and type safety."
keywords: ["ArkTS", "basics", "const", "let", "type annotations", "type inference", "nullable types", "non-null assertions", "type safety"]
doctype: guide
status: active
---

# Basics
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @jokerxd-liu-->
<!--Designer: @jokerxd-liu-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=8923bda514baa1452b967ea964ea779c7417bd8e translatedAt=2026-11-12T12:34:02.263Z pushedAt=2026-10-30T06:21:33.935Z nl=1 -->

ArkTS is an extension of TypeScript designed for OpenHarmony application development. This chapter introduces ArkTS fundamentals, including constants and variables, the type system, comments, semicolons, and other core concepts.

## Constants and Variables

ArkTS uses `const` to declare constants that cannot be reassigned and `let` to declare variables that can be reassigned. Use `const` by default and switch to `let` only when reassignment is needed. This follows the principle of least privilege: data that is not intended to change should not be accidentally overwritten. `const` keeps the variable binding unchanged, but for objects it only locks the reference; properties inside the object can still be modified (for example, `const arr = []; arr.push(1)` is valid).

### Declaration

ArkTS uses `let` and `const` to declare variables and constants.

<!-- @[variable_declaration](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Basics.ets) -->

``` TypeScript
let count: number = 10;
let name: string = 'ArkTS';
let isActive: boolean = true;

// Reassignable
let message: string = 'Hello';
message = 'Hello, ArkTS';
```

Unlike `let`, a binding declared with `const` cannot be reassigned. However, for reference types, the internal properties of the object can still be modified.

<!-- @[ts_const_reassignment](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Basics.ts) -->

``` TypeScript
const MAX_SIZE: number = 100;
const APP_NAME: string = 'MyApp';

// Constants must be initialized.
const value: number = 10;  // Correct.

// Reference type: the reference remains unchanged, but the content can be modified.
const numbers: number[] = [1, 2, 3];
numbers.push(4);           // Valid.
numbers = [5, 6];          // Compilation error.
```

### Naming

An identifier consists of letters, digits, underscores, and `$`. It cannot start with a digit and cannot use [reserved keywords](#reserved-keywords). It is recommended to use lowerCamelCase for variables and functions, UpperCamelCase for classes and interfaces, and UPPER_SNAKE_CASE for constants.

<!-- @[ts_illegal_naming](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Basics.ts) -->

``` TypeScript
// Valid naming
let validName: number = 1;
let _private: number = 2;
let $special: number = 3;
let camelCase: number = 4;

// Invalid naming
let 123start: number = 1;    // Starts with a digit
let my-var: number = 2;      // Contains a hyphen
let class: number = 3;       // reserved keyword
```

Building on valid naming, following consistent naming conventions can significantly improve code readability. The following examples show the recommended naming styles for various scenarios.

<!-- @[naming_conventions](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Basics.ets) -->

``` TypeScript
let userName: string = 'Alice';
let itemCount: number = 10;

const MAX_RETRY_COUNT: number = 3;
const API_BASE_URL: string = 'EXAMPLE_API_URL';

class UserProfile { }
interface IRepository { }
```

### Reserved Keywords

The following keywords have special semantics in ArkTS and cannot be used as identifier names.

| Category | Keywords |
| --- | --- |
| Control flow | `break` `case` `catch` `continue` `default` `do` `else` `finally` `for` `if` `of` `return` `switch` `throw` `try` `while` |
| Declarations | `class` `const` `declare` `enum` `export` `extends` `function` `import` `interface` `let` `type` `var` |
| Modifiers and accessors | `abstract` `get` `private` `protected` `public` `readonly` `set` `static` |
| Operators and operations | `delete` `in` `instanceof` `new` `super` `this` `typeof` `void` |
| Values | `false` `null` `true` |
| Others | `as` `async` `await` `debugger` `implements` `package` `with` `yield` |

### Printing

`console` provides multiple output methods: `console.info` for general information, `console.warn` for warnings, `console.error` for errors, and `console.log` for logs. Use `console.info` instead of `console.log`, which is not recommended. During development and debugging, you can use template literals to include variable values or `JSON.stringify` to output objects.

<!-- @[variable_output](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Basics.ets) -->

``` TypeScript
let outputName: string = 'ArkTS';
const version: number = 1.0;

console.info(`${outputName}`);              // 'ArkTS'
console.info(`${version}`);      // 1
console.info(`Name: ${outputName}`);   // 'Name: ArkTS'
console.info(`Version: ${version}, Name: ${outputName}`);  // 'Version: 1, Name: ArkTS'
console.warn(`Version: ${version}, Name: ${outputName}`);  // 'Version: 1, Name: ArkTS'
console.error('Invalid input');        // 'Invalid input'
```

During debugging, select the corresponding method based on the information level, and use template strings or `JSON.stringify` to format complex object output.

## Comments

ArkTS supports single-line comments (//) and multi-line comments (/* */) to explain the intent of the code.

### Single-Line Comments

A single-line comment starts with `//` and is used for brief explanations or temporarily disabling code.

<!-- @[single_line_comment](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Basics.ets) -->

``` TypeScript
let commentCount: number = 10;  // Single-line comment
```

### Multi-line Comments

Multi-line comments are enclosed in `/* */` and are used for detailed explanations or commenting out large blocks of code.

<!-- @[multi_line_comment](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Basics.ets) -->

``` TypeScript
/*
 * Multi-line comment
 * Can span multiple lines
 */
function calculate(): number {
  return 100;
}
```

### Documentation Comments

Documentation comments are enclosed in `/** */` and are used to generate API documentation and type hints.

<!-- @[documentation_comment](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Basics.ets) -->

``` TypeScript
/**
 * Calculate the sum of two numbers.
 * @param a The first number.
 * @param b The second number.
 * @returns The sum of the two numbers.
 */
function add(a: number, b: number): number {
  return a + b;
}
```

## Semicolons

It is recommended to end each statement with a semicolon to improve code consistency and readability. When multiple statements are written on the same line, semicolons are required.

<!-- @[semicolon_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Basics.ets) -->

``` TypeScript
let x: number = 10;
let y: number = 20;

// Semicolons are required for multiple statements on the same line.
let a: number = 1; let b: number = 2;

// The semicolon at the end of a statement block is optional.
function greet(): void {
  console.info('Hello');
}
```

## Type Declaration

Type declarations constrain the types of variables, parameters, and return values at compile time through type annotations, allowing the compiler to detect type mismatches (such as assigning a `string` to a `number` variable) before execution rather than at runtime. ArkTS provides three forms of type declarations: [type annotations](#type-annotation) (`: type`), [type aliases](#type-alias) (`type Name = ...`), and [interface declarations](arkts-language-guide-interfaces.md) (`interface`), each suited to different scenarios.

### Basic Type Declaration

Use [type annotations](#type-annotation) (`: type`) to annotate types for variables, parameters, and return values.

<!-- @[type_annotation_examples](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Basics.ets) -->

``` TypeScript
// Variable type
let annotExAge: number = 0;

// Function parameter and return value types
function annotExGreet(name: string): string {
  return `Hello, ${name}`;
}

// Class property type
class User {
  public id: number = 0;
  public name: string = '';
}
```

### Type Alias

A type alias gives a new name to an existing type, simplifying the writing of complex types. An alias is fully equivalent to the original type — using the alias is the same as using the original type, and no new type is created. It is commonly used to simplify union types (for example, `type ID = number | string`) and complex generics (for example, `type Mapper<T, R> = (input: T) => R`).

<!-- @[type_alias](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Basics.ets) -->

``` TypeScript
type ID = number | string;
type Age = number;

let userId: ID = 123;
userId = 'ABC';
```

### API Declaration

`interface` defines a structural contract for objects, describing property names, types, and optionality. For details, see [Interfaces](arkts-language-guide-interfaces.md).

<!-- @[interface_definition](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Basics.ets) -->

``` TypeScript
interface IfaceDefUser {
  id: number;
  name: string;
  email?: string;
}

let user: IfaceDefUser = { id: 1, name: 'Alice' };
```

## Type

ArkTS provides types such as `number`, `boolean`, `string`, arrays, and enums to constrain value ranges and operations.

### number Type

The `number` type represents IEEE 754 double-precision floating-point numbers (64-bit), with no separate integer type. It supports decimal, hexadecimal, binary, and octal literals.

<!-- @[number_literals](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Basics.ets) -->

``` TypeScript
let decimal: number = 42;      // Decimal
let hex: number = 0xFF;        // Hexadecimal (255)
let binary: number = 0b1010;   // Binary (10)
let octal: number = 0o755;     // octal (493)
```

### boolean Type

The `boolean` type represents the logical values `true` and `false`, produced by direct assignment, comparison operators (`===`, `!==`, `>`, `<`), and logical operators (`&&`, `||`, `!`). Boolean values cannot be implicitly converted to or from other types, avoiding JavaScript type confusion.

<!-- @[boolean_type](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Basics.ets) -->

``` TypeScript
let boolTypeIsActive: boolean = true;
let isComplete: boolean = false;

// Comparison produces a boolean value.
let boolTypeX: number = 10;
let boolTypeY: number = 5;
let greater: boolean = boolTypeX > boolTypeY;  // true
```

Note that when performing conditional checks, do not mix boolean values with other types. ArkTS rejects implicit conversions at compile time.

### array Type

The `array` type represents an ordered collection of elements, where all elements are of the same type and can be accessed by index. The `number[]` syntax is recommended, but the `Array<number>` generic syntax can also be used. For details, see [Collection Types](arkts-language-guide-collection-types.md).

<!-- @[array_type](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Basics.ets) -->

``` TypeScript
// Declare an array.
let arrTypeNumbers: number[] = [1, 2, 3];
let arrTypeNames: string[] = ['A', 'B', 'C'];

// Operate on the array.
arrTypeNumbers.push(4);
arrTypeNumbers.pop();
let first: number = arrTypeNumbers[0];
```

The two syntaxes are equivalent. It is recommended that a team consistently use `number[]` to keep the style uniform.

### enum Type

The `enum` type defines an enumeration of named constant values, providing meaningful names for fixed states. For details, see [Enums](arkts-language-guide-enums.md).

<!-- @[enum_type](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Basics.ets) -->

``` TypeScript
enum Direction {
  Up,
  Down,
  Left,
  Right
}

let dir: Direction = Direction.Up;

// Enum with values
enum Status {
  Pending = 'pending',
  Active = 'active',
  Completed = 'completed'
}

let status: Status = Status.Active;
```
Enum values increment from 0 by default. You can also explicitly specify string or numeric values to improve readability and stability.

### union Type

A union type represents a value that can be one of several types, separated by a vertical bar (`|`). Union types are suitable for: function parameters that accept multiple types (for example, `id: number | string`), variables that hold values of different types in different branches, and extended sets of enumerated values. When using a value of a union type, you can only access properties common to all members; to access properties of a specific type, you must narrow the type using `typeof`, `instanceof`, or a discriminant field.

<!-- @[union_type](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Basics.ets) -->

``` TypeScript
let unionTypeId: number | string = 123;
unionTypeId = 'ABC-123';

let result: number | null = null;
result = 100;

// Union of multiple types
let data: number | string | boolean = 1;
data = 'text';
data = true;
```

### Literal Type

A literal type uses a value itself as the type, restricting a variable to only specific literal values.

<!-- @[literal_union_type](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Basics.ets) -->

``` TypeScript
type TaskState = 'pending' | 'running' | 'done';

let state: TaskState = 'pending';
state = 'running';
```
For a stable set of states, prefer `enum` to avoid scattering a large number of string literals throughout business code.

### void Type

The `void` type indicates that a function has no return value. It is commonly used for functions that perform operations without returning results. Note that `void` differs from `undefined`, which represents an undefined value.

<!-- @[void_type](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Basics.ets) -->

``` TypeScript
function logMessage(message: string): void {
  console.info(`${message}`);
}

function doNothing(): void {
  // No return value.
}
```

### never Type

The `never` type represents functions that never return, either because they throw an exception or loop indefinitely.

<!-- @[never_type](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Basics.ets) -->

``` TypeScript
function fail(message: string): never {
  throw new Error(message);
}

function assertNever(value: never): never {
  throw new Error(`Unexpected value: ${value}`);
}
```

The `never` type is commonly used in two scenarios: exception functions that always throw and never return, and exhaustiveness checks, where making the `default` branch return `never` ensures that a `switch` covers all enum values.

### bigint Type

The `bigint` type represents arbitrary-precision integers. Its literals use an n suffix, making it suitable for very large integer calculations.

<!-- @[bigint_type](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Basics.ets) -->

``` TypeScript
let bigValue: bigint = 999999999999999999999999999999999999n;
console.info(`${bigValue.toString()}`);

let nextValue: bigint = bigValue + 1n;
console.info(`${nextValue.toString()}`);
```

Adding `n` after a numeric literal indicates the `bigint` type. `bigValue` represents a very large integer without precision loss, and `nextValue` performs addition with an exact result. `bigint` and `number` cannot be used together directly in arithmetic; explicit conversion is required.

<!-- @[bigint_conversion](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Basics.ets) -->

``` TypeScript
let bigintCount: number = 10;
let preciseCount: bigint = BigInt(bigintCount);
let total: bigint = preciseCount + 20n;
```

Some APIs (such as `Date`-related methods) or annotation fields may not support `bigint`. Check the type constraints in the corresponding API documentation before use. Prefer `bigint` for large integers to avoid `number` precision loss, and use explicit conversion for mixed arithmetic. `bigint` supports only integer arithmetic, not fractions, and some older API versions may not support it.

## Type Annotation

Type annotation specifies types for variables, parameters, and return values, allowing the compiler to check type correctness at compile time.

<!-- @[type_annotation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Basics.ets) -->

``` TypeScript
// Basic type annotation
let age: number = 25;
let annotName: string = 'Alice';
let isValid: boolean = true;

// Reference type annotation
let annotNumbers: number[] = [1, 2, 3];
let names: string[] = ['A', 'B', 'C'];

// Union type
let id: number | string = 123;
id = 'ABC-123';
```

Public APIs and complex types (unions, generics) should be explicitly annotated, while simple local variables can rely on type inference.

## Type Inference

Type inference is the process by which the compiler automatically derives the type of a variable or expression from the context, without requiring you to explicitly annotate it. ArkTS supports type inference in most scenarios, and using it appropriately can reduce redundant annotations.

### Variable Type Inference

When a variable is assigned a value, the compiler infers the type of the variable from the value on the right side.

<!-- @[type_inference_variables](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Basics.ets) -->

``` TypeScript
let tiCount = 10;        // Inferred as number
let tiMessage = 'hello'; // Inferred as string
let tiItems = [1, 2, 3]; // Inferred as number[]
```

Variables declared with `const` are inferred as literal types, while variables declared with `let` are inferred as widened types.

<!-- @[type_inference_const_let](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Basics.ets) -->

``` TypeScript
const tiPi = 3.14;   // Inferred as 3.14 (literal type).
let tiRatio = 3.14;  // Inferred as number (widened type).
```

When multiple candidate types exist, the compiler selects the most general type. If an array contains elements of multiple types (such as numbers and `null`), explicitly annotate it as an array of the union of the element types.

<!-- @[type_inference_best_common](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Basics.ets) -->

``` TypeScript
let tiMixed: (number | null)[] = [0, 1, null]; // Must be explicitly annotated as a union type array.
let tiNames: string[] = ['Alice', 'Bob'];      // Inferred as string[].
```

If no unified common type can be found, you must annotate the type explicitly.

### Control Flow Inference

The compiler tracks type changes along control flow branches such as `if`/`else`, `switch`, and loops, narrowing a variable to a more specific type within different branches and taking the union type after the branches merge.

<!-- @[type_inference_control_flow](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Basics.ets) -->

``` TypeScript
let tiValue: string | number = 'hello';
if (typeof tiValue === 'string') {
  console.info(tiValue.toUpperCase()); // tiValue is narrowed to string here.
} else {
  console.info(`${tiValue}`);          // tiValue is narrowed to number here.
}
```

## Optional/Nullable Types

Optional types allow `null` or `undefined` to represent values that may be absent.

### null/undefined

`null` represents an intentionally assigned empty value, while `undefined` indicates that a variable has not been assigned or a property does not exist. They have different semantics and must be explicitly distinguished in ArkTS.

<!-- @[null_undefined_types](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Basics.ets) -->

``` TypeScript
// null: an intentional empty value
let empty: null = null;
let nullUndefData: string | null = null;

// undefined: an undefined value
let missing: undefined = undefined;
let optional: string | undefined = undefined;

// Difference between null and undefined
let nickname: string | null = null;     // Explicitly indicates that there is no nickname.
let title: string | undefined;          // May not be provided.
```

### Optional Value Binding

An optional property (?) indicates that the property may not exist. Before accessing it, handle it through an explicit check (`if (value !== undefined)`), a type guard (`if (value !== null)`), or optional chaining (`value?.property`).

<!-- @[optional_property](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Basics.ets) -->

``` TypeScript
interface OptPropUser {
  id: number;
  name: string;
  email?: string;  // Optional property
}

let optPropUser: OptPropUser = { id: 1, name: 'Alice' };

// Check whether the optional value exists
if (optPropUser.email !== undefined) {
  console.info(`${optPropUser.email}`);
}
```

When accessing optional properties nested at multiple levels, optional chaining avoids null checks at each level, making the code more concise.

### Providing Default Values

Use the nullish coalescing operator (??) or default function parameters to provide fallback values for `null`/`undefined`. Note that `??` applies only to `null`/`undefined`, while `||` applies to all falsy values (`0`, `false`, and `''`). Choose according to the scenario.

<!-- @[null_handling](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Basics.ets) -->

``` TypeScript
// Nullish coalescing operator
let nullHandleValue: string | null = null;
let display: string = nullHandleValue ?? 'default';

// Function default parameters
function nullHandleGreet(name: string, title: string = 'User'): string {
  return `Hello, ${title} ${name}`;
}

nullHandleGreet('Alice');           // 'Hello, User Alice'
nullHandleGreet('Alice', 'Dr.');    // 'Hello, Dr. Alice'
```

When the default value needs to preserve legitimate values such as `0`, `false`, and `''`, you must use `??` instead of `||`.

## Non-null Assertion

The non-null assertion uses the `!` operator to tell the compiler "treat this as non-null here." The non-null assertion bypasses the compiler's null check but does not generate any verification code at runtime. Prefer type guards, optional chaining, or nullish coalescing, and use the non-null assertion only when you are certain that the value is non-null.

<!-- @[non_null_assertion](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Basics.ets) -->

``` TypeScript
let nonNullValue: string | null = 'text';

// Non-null assertion (confirm the value is not null).
let length: number = nonNullValue!.length;

// Type guard check.
if (nonNullValue !== null) {
  let len: number = nonNullValue.length;  // Safe access.
}
```

The non-null assertion is a shortcut for "the developer's promise that the value is non-null". If the promise fails, the program crashes directly at runtime. Therefore, use it only when you are certain that the value is non-null and the condition cannot be expressed with a type guard.

### Implicit Resolution of Nullable Types

A nullable type (`T | null`/`T | undefined`) indicates that a value may not exist. The difference from an optional property `?` is that `?` is a modifier used at property declaration (`name?: string`), whereas a nullable type is an explicit union type annotation (`name: string | null`). Before accessing a value of a nullable type, you must handle the possible null value through an `if` check, optional chaining `?.`, or nullish coalescing `??`.

<!-- @[null_safety](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Basics.ets) -->

``` TypeScript
interface NullableSub {
  sub?: string;
}

interface NullableObj {
  prop?: NullableSub;
}

let optionalValue: string | null = 'hello';

// Explicitly handle null values.
if (optionalValue !== null) {
  console.info(`${optionalValue.length}`);
}

// Use optional chaining.
let obj: NullableObj = {};
let sub: string | undefined = obj?.prop?.sub;
```

## Type Safety

Type safety catches type errors at compile time, reducing runtime issues that are difficult to diagnose.

The compiler rejects type-mismatched assignments, such as assigning a `string` to a `number` variable.

<!-- @[ts_type_mismatch](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Basics.ts) -->

``` TypeScript
let typeCheckAge: number = 25;
typeCheckAge = 'text';  // Compilation error: type mismatch

function typeCheckAdd(a: number, b: number): number {
  return a + b;
}

typeCheckAdd(1, 2);      // Correct
typeCheckAdd(1, '2');    // Compilation error
```

Type safety detects errors at compile time to avoid runtime crashes, improves code readability and refactoring safety, and supports intelligent hints in DevEco Studio.

## Error Handling

Use `try-catch` to catch runtime exceptions and prevent unexpected program termination.

### try-catch Exception Handling

The `try` block contains code that may throw an exception, and the `catch` block catches and handles the exception to prevent unexpected program termination.

<!-- @[try_catch_basic](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Basics.ets) -->

``` TypeScript
function riskyOperation(): number {
  throw new Error('operation failed');
}

function parseJSON(data: string): Object {
  return JSON.parse(data);
}

let tcData: string = '{"name": "Alice"}';

try {
  let result: number = riskyOperation();
} catch (error) {
  console.info(`Error: ${error}`);
}

// Catch a specific error.
try {
  parseJSON(tcData);
} catch (error) {
  if (error instanceof SyntaxError) {
    console.info(`JSON parsing error`);
  }
}
```

### Throwing Errors with throw

The `throw` statement throws an `Error` object, interrupts the current function, and propagates the exception outward.

<!-- @[throwing_exceptions](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Basics.ets) -->

``` TypeScript
function validateAge(age: number): void {
  if (age < 0) {
    throw new Error('Age cannot be negative');
  }
  if (age > 150) {
    throw new Error('Age is out of a reasonable range');
  }
}
```

Always throw an `Error` object with a clear error message, and throw only for genuinely exceptional conditions. Avoid using exceptions to control normal program flow.

### Error Handling Conventions

Return a tuple `[result, Error | null]` so that the caller obtains both the result and the error information.

<!-- @[error_tuple_return](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Basics.ets) -->

``` TypeScript
// Return the error information tuple.
function divide(a: number, b: number): [number, Error | null] {
  if (b === 0) {
    return [0, new Error('The divisor cannot be zero.')];
  }
  return [a / b, null];
}

let divideResult: [number, Error | null] = divide(10, 0);
let errTupleResult: number = divideResult[0];
let error: Error | null = divideResult[1];

if (error !== null) {
  console.info(`${error.message}`);
}
```

## Scope Rules

Scope determines the visibility and lifecycle of variables. ArkTS supports block scope and function scope.

### let/const Declarations (Block Scope)

Variables declared with `let` and `const` have block scope, cannot be accessed before their declaration, and cannot be redeclared in the same scope.

<!-- @[let_const_block_scope](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Basics.ets) -->

``` TypeScript
function blockScope(): void {
  let bsA: number = 10;
  const bsB: number = 20;
  if (true) {
    let bsA: number = 30; // An independent variable in the inner scope that does not affect the outer scope.
    console.info(`${bsA}`); // 30
    console.info(`${bsB}`); // 20, accessible from the outer scope.
  }
  console.info(`${bsA}`); // 10
}
```

### Nested Scope

An inner scope can access outer variables, but not vice versa. `let`/`const` declarations in nested blocks can shadow outer variables with the same names.

<!-- @[nested_scope](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Basics.ets) -->

``` TypeScript
let nsOuter: string = 'outer';

function nestedScope(): void {
  let nsInner: number = 100;
  console.info(`${nsOuter}`); // Accessible from the outer scope

  if (true) {
    let nsInner: number = 200; // Shadows the outer nsInner
    console.info(`${nsInner}`); // 200
  }
  console.info(`${nsInner}`); // 100
}
```

## Spread Syntax (spread)

The spread syntax `...` expands an array into individual elements. ArkTS supports spreading arrays in array literals and passing spread arrays to function rest parameters.

<!-- @[spread_syntax_alternative](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Basics.ets) -->

``` TypeScript
// Copy an array into an array literal.
let spreadArr1: number[] = [1, 2, 3];
let spreadArr2: number[] = [...spreadArr1, 4, 5];

// Spread an array into a rest parameter.
function spreadTotal(...values: number[]): number {
  let total: number = 0;
  for (const value of values) {
    total += value;
  }
  return total;
}

let spreadNums: number[] = [1, 2, 3];
console.info(`${spreadTotal(...spreadNums)}`);  // 6
```
