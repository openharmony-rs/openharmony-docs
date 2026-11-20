---
kits: ["ArkTS Kit"]
description: "How to declare and use ArkTS enum types, covering numeric and string enums, enums with associated values, const enum, and mappings between associated values and enum members."
keywords: [ArkTS, enums, enum, numeric enums, string enums, const enum]
doctype: guide
status: active
---

# Enums
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @jokerxd-liu-->
<!--Designer: @jokerxd-liu-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=8923bda514baa1452b967ea964ea779c7417bd8e translatedAt=2026-11-12T12:34:02.336Z pushedAt=2026-10-30T06:21:33.935Z nl=1 -->

An enum is a user-defined type containing a finite set of named constant values. Its main purpose is to replace magic numbers or strings with meaningful names, making code clearer, more readable, and easier to maintain.

## Defining and Using Enums

ArkTS supports two forms of enums: numeric enums and string enums.

### Defining Simple Enums

Define an enum with the `enum` keyword, for example:

<!-- @[basic_enum_declaration](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Enums.ets) -->

``` TypeScript
// Enum definition.
enum Direction {
  Up,
  Down,
  Left,
  Right
}
let direction: Direction = Direction.Up;
```

This defines the enum type `Direction`, which contains four members: `Up`, `Down`, `Left`, and `Right`.

Access these enum members using qualified names, such as `Direction.Up`.

Use the enum as follows:

<!-- @[enum_as_function_parameter](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Enums.ets) -->

``` TypeScript
// Enum as a function parameter
function declarationMove(direction: Direction): void {
  switch (direction) {
    case Direction.Up:
      console.info('Up');
      break;
    case Direction.Down:
      console.info('Down');
      break;
    case Direction.Left:
      console.info('Left');
      break;
    case Direction.Right:
      console.info('Right');
      break;
  }
}

declarationMove(Direction.Up);  // Up
```

## Enums with Associated Values

Enum members can be explicitly assigned numeric or string associated values for serialization, persistence, or interaction with external APIs.

### Numeric Enums

Members without explicit values automatically receive incrementing numeric values, starting from 0 or continuing from the previous explicit value.

<!-- @[auto_increment_numeric_enum](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Enums.ets) -->

``` TypeScript
// Numeric enum auto-increment.
enum AutoNumberEnum {
  First,    // 0 (automatic)
  Second,   // 1 (automatic)
  Third,    // 2 (automatic)
  Custom = 10,
  Fourth,   // 11 (continues from Custom)
  Fifth     // 12
}
```

### String Enums

Every member of a string enum must have an explicitly specified associated value.

<!-- @[enum_auto_increment_rules](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Enums.ets) -->

``` TypeScript
enum AutoStringEnum {
  A = 'A',
  B = 'B',
  C = 'C'
}
```

### Associated Value Type Constraints

Within an enum, the associated values of all members must have the same type. Mixing strings and numbers causes a compilation error.

<!-- @[enum_mixed_type_error](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Enums.ts) -->

``` TypeScript
enum Mixed {
  No = 0,
  Yes = 'YES'  // Compilation error: inconsistent associated value types.
}
```

### Mapping Between Associated Values and Enum Members

Numeric enums support obtaining enum member names from associated values, but string enums do not.

<!-- @[enum_bidirectional_mapping](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Enums.ets) -->

``` TypeScript
enum BiUserRole {
  Admin = 100,
  Moderator = 200,
  User = 300
}

let biRole: BiUserRole = BiUserRole.Admin;     // 100
let biRoleName: string = BiUserRole[100];      // 'Admin'

function getBiRoleName(roleId: number): string | undefined {
  return BiUserRole[roleId];
}

console.info(`${getBiRoleName(100)}`);  // 'Admin'
console.info(`${getBiRoleName(200)}`);  // 'Moderator'
```

### Using Enum Members as Literal Types

<!-- @[ts_enum_member_types](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Enums.ts) -->

``` TypeScript
// Enum members are unique types.
let up: Direction.Up = Direction.Up;  // Type Direction.Up
let down: Direction.Down = Direction.Down;

// Members of different types are not interchangeable.
up = down;  // Compilation error: type mismatch.

// Use enumerated values as a union type.
type HorizontalDirection = Direction.Left | Direction.Right;
type VerticalDirection = Direction.Up | Direction.Down;

function moveHorizontal(dir: HorizontalDirection): void {
  console.info(`Horizontal movement: ${dir}`);
}

moveHorizontal(Direction.Left);
moveHorizontal(Direction.Up);  // Compilation error: type mismatch.
```

### Using Enums Instead of Magic Strings

Use enums instead of magic strings/numbers to improve code readability and maintainability.

<!-- @[replace_magic_strings_numbers](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Enums.ets) -->

``` TypeScript
// Counterexample: using magic strings
function getStatusLabel(status: string): string {
  if (status === 'pending') {
    return 'Pending';
  } else if (status === 'active') {
    return 'Active';
  } else if (status === 'completed') {
    return 'Completed';
  }
  return 'Unknown';
}

// Recommended: use an enum
enum OrderStatus {
  Pending = 'pending',
  Active = 'active',
  Completed = 'completed'
}

function getStatusLabelEnum(status: OrderStatus): string {
  switch (status) {
    case OrderStatus.Pending:
      return 'Pending';
    case OrderStatus.Active:
      return 'Active';
    case OrderStatus.Completed:
      return 'Completed';
    default:
      return 'Unknown';
  }
}

// Counterexample: Use a magic number.
function getErrorCode(code: number): string {
  if (code === 404) {
    return 'Not Found';
  } else if (code === 401) {
    return 'Unauthorized';
  }
  return 'Unknown';
}

// Recommended: Use an enum.
enum HttpErrorCode {
  NotFound = 404,
  Unauthorized = 401
}

function getErrorCodeEnum(code: HttpErrorCode): string {
  switch (code) {
    case HttpErrorCode.NotFound:
      return 'Not Found';
    case HttpErrorCode.Unauthorized:
      return 'Unauthorized';
    default:
      return 'Unknown';
  }
}
```

## const enum

A `const enum` inlines its member values at compile time and does not generate a runtime enum object. ArkTS supports `const enum`. However, note that there is a version dependency risk when sharing it across projects (through `.d.ts` files): the member values of a `const enum` are inlined into the consumer's code at compile time. If the source definition of the `const enum` changes, the consumer must recompile to obtain the new values. It is recommended to use `const enum` within a project and use a regular enum when sharing across projects.

<!-- @[const_enum_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Enums.ets) -->

``` TypeScript
const enum CeConstDirection {
  Up,
  Down
}

let cedDir: CeConstDirection = CeConstDirection.Up;
console.info(`${cedDir}`); // 0
```

Using a regular enum instead of a `const enum` avoids the cross-project pitfalls:

<!-- @[const_enum_alternative](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Enums.ets) -->

``` TypeScript
enum CeDirection {
  Up = 0,
  Down = 1
}

let ceD: CeDirection = CeDirection.Up;
console.info(`${ceD}`);  // 0
```
