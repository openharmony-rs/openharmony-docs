---
kits: ["ArkTS Kit"]
description: "Explains ArkTS basic operators, including assignment, arithmetic, comparison, logical, and ternary conditional operators, and operator precedence rules."
keywords: ["ArkTS", "basic operators", "assignment operators", "arithmetic operators", "comparison operators", "logical operators", "ternary conditional operator", "operator precedence"]
doctype: guide
status: active
---

# Basic Operators
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @jokerxd-liu-->
<!--Designer: @jokerxd-liu-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=8923bda514baa1452b967ea964ea779c7417bd8e translatedAt=2026-11-12T12:34:02.246Z pushedAt=2026-10-30T06:21:33.935Z nl=1 -->

ArkTS provides a rich set of operators for data operations, logical judgment, and assignment operations.

## Assignment Operators

The assignment operator (=) assigns the value on the right to the variable on the left, and supports chained assignment and compound assignment (+=, -=, and so on).

### Simple Assignment (=)

Use `=` to assign the value on the right to the variable on the left. Assignment follows reference semantics: after assigning an object-type variable, the old and new variables point to the same object, and modifying one affects the other.

<!-- @[basic_variable_assignment](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
let value: number = 10;
let name: string = 'Alice';
let active: boolean = true;

// Reassign the value.
value = 20;
name = 'Bob';
```

### Return Value of an Assignment Expression

An assignment expression returns the assigned value. Chained assignment such as `a = b = 10` is syntactically supported, but it is **not recommended**. Assign values separately to improve readability.

<!-- @[chain_vs_separate_assignment](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
let a: number;
let b: number;

// Counterexample: chained assignment
a = b = 10;

// Recommended: assign separately
a = 10;
b = 10;
```

### Object Assignment

Assigning an object to a variable passes a reference rather than a copy—the new and old variables point to the same object, and modifying a property of one affects the other. To obtain an independent copy, you must implement a deep copy manually.

<!-- @[object_property_and_reference_assignment](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
class Point {
  public x: number = 0;
  public y: number = 0;
}

let point: Point = new Point();
point.x = 10;       // Property assignment
point.y = 20;

let another: Point = point;  // Reference assignment
another.x = 30;    // point.x also becomes 30
```

## Arithmetic Operators

Arithmetic operators include addition (+), subtraction (-), multiplication (*), division (/), remainder (%), and increment/decrement (++/--).

### Addition Operator (+)

The addition operator performs numeric addition or string concatenation and returns the sum or concatenation result.

<!-- @[addition_and_string_concatenation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
let addA: number = 10;
let addB: number = 5;

let sum: number = addA + addB;    // 15

// String concatenation
let greeting: string = 'Hello' + ' World';
let message: string = 'Count: ' + 10;
```

### Subtraction Operator (-)

The subtraction operator (`-`) calculates the difference between two numeric operands, which must be of type `number`. Unlike `+`, which supports string concatenation, `-`, `*`, `/`, `%`, and unary negation do not allow cross-type operations involving types such as `number` and `string`.

<!-- @[subtraction_and_negative_number](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
let numberA: number = 10;
let numberB: number = 5;

let diff: number = numberA - numberB;   // 5
let negative: number = -10; // Represent a negative number.
```

### Multiplication Operator (*)

The multiplication operator (`*`) computes the product of two numeric operands. The operands must be of the `number` type. ArkTS does not support string repetition (such as `'ab' * 3` in Python); use the `repeat()` method for string repetition.

<!-- @[multiplication_operator](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
let mulA: number = 10;
let mulB: number = 5;

let product: number = mulA * mulB;  // 50

// Calculate the area.
let width: number = 5;
let height: number = 10;
let area: number = width * height;  // 50
```

### Division Operator (/)

The division operator (/) calculates the quotient of two numbers, and the result is always a floating-point number.

<!-- @[division_operator](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
let divA: number = 10;
let divB: number = 4;

let quotient: number = divA / divB;  // 2.5

// Integer division.
let intDivision: number = Math.floor(10 / 4);  // 2

// Division by zero.
let zeroDiv: number = 10 / 0;   // Infinity
let negZeroDiv: number = -10 / 0;  // -Infinity
let zeroByZero: number = 0 / 0;  // NaN
```

### Remainder Operator (%)

The remainder operator returns the remainder of a division and is used for loops and periodic calculations.

<!-- @[modulo_operator](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
let modA: number = 10;
let modB: number = 3;

let remainder: number = modA % modB;  // 1

// Determine whether the number is even or odd.
let isEven: boolean = (modA % 2) === 0;
let isOdd: boolean = (modA % 2) !== 0;
```

### Unary Negation Operator (-)

The unary negation operator (-) negates a numeric value, turning a positive value into a negative one and vice versa.

<!-- @[unary_negation_operator](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
let negA: number = 5;
let negNegative: number = -negA;  // -5

let negB: number = -10;
let positive: number = -negB;  // 10
```


### Exponentiation Operator (**)

The exponentiation operator calculates a power and returns the base raised to the power of the exponent.

<!-- @[exponentiation_operator](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
let base: number = 2;
let exponent: number = 3;

let power: number = base ** exponent;  // 8 (2^3)

let square: number = 5 ** 2;   // 25
let cube: number = 3 ** 3;     // 27
```

## Compound Assignment Operators

Compound assignment operators combine an operation and an assignment to simplify code.

<!-- @[compound_assignment_operators](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
// Addition assignment
let total: number = 100;
total += 50;  // 150

// String concatenation assignment
let compoundMessage: string = 'Hello';
compoundMessage += ' World';  // 'Hello World'

// Subtraction assignment
let balance: number = 1000;
balance -= 200;  // 800

// multiplication assignment
let price: number = 10;
price *= 2;  // 20

// division assignment
let amount: number = 100;
amount /= 4;  // 25

// modulo assignment
let compoundValue: number = 17;
compoundValue %= 5;  // 2

// exponentiation assignment
let compoundBase: number = 2;
compoundBase **= 4;  // 16
```

### Logical Assignment Operators (??=, ||=, &&=)

Logical assignment operators (??=, ||=, &&=) combine logical operations with assignment. Their semantics match `??`, `||`, and `&&`, respectively, including short-circuiting: the right-hand expression is evaluated only when assignment is needed. Evaluation follows JavaScript's truthy/falsy concepts: `false`, `0`, `-0`, `NaN`, `''` (the empty string), `null`, and `undefined` are falsy in a Boolean context; all other values are truthy. The logical and nullish coalescing operators described later use the same concepts.

- `a ??= b`: assigns `b` to `a` only if `a` is `null` or `undefined`.
- `a ||= b`: assigns `b` to `a` only if `a` is falsy.
- `a &&= b`: assigns `b` to `a` only if `a` is truthy.

<!-- @[logical_assignment_operators](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
// ??= assigns only if the left-hand value is null or undefined.
let configValue: string | null = null;
configValue ??= 'default';  // "default" (the original value is null, so assignment occurs)

let timeout: number | null = 0;
timeout ??= 3000;  // 0 (0 is a valid value, so no assignment occurs)

// ||= assigns only if the left-hand value is falsy.
let label: string = '';
label ||= 'unnamed';  // "unnamed" ('' is falsy, so assignment occurs)

// &&= assigns only if the left-hand value is truthy.
let logicalCount: number = 10;
logicalCount &&= logicalCount * 2;  // 20 (10 is truthy, so assignment occurs)

// Short-circuiting: the right-hand expression is not evaluated if the left-hand condition is not met.
let cache: string | null = 'cached';
function loadFromDisk(): string {
  console.info('Reading from disk');
  return 'loaded';
}
cache ??= loadFromDisk();  // "cached" (not null, so loadFromDisk is not called)
```

## Comparison Operators

Comparison operators determine the relationship between values and return a Boolean result.

### Equality Operator (===)

Strict equality (===) returns `true` when both values and types are the same.

<!-- @[strict_equality_operator](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
// Numeric comparison
let eqA: number = 5;
let eqB: number = 5;
console.info(`${eqA === eqB}`);     // true

// Different values
let eqNum1: number = 5;
let eqNum2: number = 10;
console.info(`${eqNum1 === eqNum2}`); // false

// Compare object references
class EqPoint {
  public x: number;
  public y: number;
  constructor(x: number, y: number) {
    this.x = x;
    this.y = y;
  }
}

let p1: EqPoint = new EqPoint(1, 2);
let p2: EqPoint = new EqPoint(1, 2);
console.info(`${p1 === p2}`);  // false (different objects)

// NaN is not equal to itself.
let nan1: number = 0 / 0;  // Floating-point calculation produces NaN.
let nan2: number = 0 / 0;  // Floating-point calculation produces NaN.
console.info(`${nan1 === nan2}`);        // false
console.info(`${Number.isNaN(nan1)}`);   // true
```

`NaN` is not equal to any value, including itself. `NaN === NaN` is always `false`, so do not use `===` to check whether a floating-point calculation produces `NaN`. Use `Number.isNaN` instead.

ArkTS also supports loose equality (==). Because static type checking limits comparisons between values of different types, the main difference between `==` and `===` is how they handle `null` and `undefined`: `==` considers them equal, whereas `===` distinguishes them. Unless specifically needed, use the stricter `===`:

<!-- @[loose_equality_not_recommended](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
// == considers null and undefined equal.
let inputValue: string | null = null;
let missing: string | undefined = undefined;

console.info(`${inputValue == null}`);     // true
console.info(`${missing == null}`);        // true (undefined == null is true)
console.info(`${inputValue == missing}`);  // true

// === distinguishes null from undefined.
console.info(`${inputValue === null}`);  // true
console.info(`${missing === null}`);     // false (undefined !== null)
```

Use strict equality:

<!-- @[strict_equality_preferred](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
let eqValue: string | null = null;
let eqCount: number = 0;
// Recommended: use strict equality.
if (eqValue === null) { }
if (eqCount === 0) { }
```

### Not Equal Operator (!==)

Strict inequality (!==) returns `true` when values or types differ. Loose inequality (!=) is likewise not recommended. Use `!==` consistently.

<!-- @[strict_inequality_operator](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
let neA: number = 5;
let neB: number = 3;
console.info(`${neA !== neB}`);     // true

let neNum1: number = 5;
let neNum2: number = 10;
console.info(`${neNum1 !== neNum2}`); // true
```

### Greater Than Operator (>)

Greater than (>) returns `true` when the left-hand value is greater than the right-hand value.

<!-- @[greater_than_operator](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
let gtA: number = 10;
let gtB: number = 5;

console.info(`${gtA > gtB}`);   // true
console.info(`${gtB > gtA}`);   // false
console.info(`${gtA > gtA}`);   // false

// Compare strings by Unicode code points.
console.info(`${'gtB' > 'gtA'}`);     // true
console.info(`${'abc' > 'abb'}`); // true
```

### Less-Than Operator (<)

Less than (<) returns `true` when the left-hand value is less than the right-hand value.

<!-- @[less_than_operator](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
let ltA: number = 10;
let ltB: number = 5;

console.info(`${ltA < ltB}`);   // false
console.info(`${ltB < ltA}`);   // true
console.info(`${ltA < ltA}`);   // false
```

### Greater Than or Equal To Operator (>=)

Greater than or equal to (>=) returns `true` when the left-hand value is greater than or equal to the right-hand value.

<!-- @[greater_than_or_equal_operator](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
let gteA: number = 10;
let gteB: number = 5;
let c: number = 10;

console.info(`${gteA >= gteB}`);  // true
console.info(`${gteA >= c}`);  // true
console.info(`${gteB >= gteA}`);  // false
```

### Less Than or Equal To Operator (<=)

Less than or equal to (<=) returns `true` when the left-hand value is less than or equal to the right-hand value.

<!-- @[less_than_or_equal_operator](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
let lteA: number = 10;
let lteB: number = 5;
let lteC: number = 10;

console.info(`${lteA <= lteB}`);  // false
console.info(`${lteA <= lteC}`);  // true
console.info(`${lteB <= lteA}`);  // true
```

## Ternary Conditional Operator

The ternary conditional operator selects one of two values based on the Boolean value of a condition. It is a concise form of `if-else`, suitable for simple conditional assignments.

``` TypeScript
condition ? valueIfTrue : valueIfFalse
```

<!-- @[ternary_conditional_operator](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
let age: number = 20;
let status: string = age >= 18 ? 'adult' : 'minor';

let score: number = 85;
let result: string = score >= 60 ? 'pass' : 'fail';

// Nested ternary operator
let grade: string = 
  score >= 90 ? 'A' :
  score >= 80 ? 'B' :
  score >= 70 ? 'C' :
  score >= 60 ? 'D' : 'F';

// Function return
function getStatus(code: number): string {
  return code === 200 ? 'OK' : 'Error';
}

// Conditional assignment
let isAdmin: boolean = true;
let role: string = isAdmin ? 'admin' : 'user';
```

## Nullish Coalescing Operator

The nullish coalescing operator (??) provides a default value, returning the right-hand value only when the left-hand value is `null` or `undefined`.

`??` and logical OR `||` differ in how they handle [falsy values](#logical-assignment-operators-): `||` returns the right-hand value whenever the left-hand value is falsy, potentially replacing valid values such as `0`, `''`, and `false`. `??` returns the right-hand value only for `null` or `undefined` (a subset of falsy values), preserving other valid values.

<!-- @[nullish_coalescing_operator](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
let coalesceValue: string | null = null;
let coalesceResult: string = coalesceValue ?? 'default';
console.info(`${coalesceResult}`);  // 'default'

let value2: string = 'hello';
let result2: string = value2 ?? 'default';  // "hello"

// Difference from ||
let count: number = 0;
let text: string = '';
let flag: boolean = false;

// || replaces falsy values
let withOr1: number = count || 10;     // 10 (0 is falsy)
let withOr2: string = text || 'default'; // 'default'

// ?? replaces only null/undefined
let withNullCoalesce1: number = count ?? 10;      // 0 (0 is retained)
let withNullCoalesce2: string = text ?? 'default'; // '' (empty string is retained)

// Chained nullish coalescing
let primary: string | null = null;
let secondary: string | null = null;
let fallback: string = 'default';

let result3: string = primary ?? secondary ?? fallback;
console.info(`${result3}`);  // 'default'
```

## Logical Operators

Logical operators include NOT (!), AND (&&), and OR (||). They perform logical operations on Boolean values and support short-circuit evaluation.

### Logical NOT Operator (!)

Logical NOT (!) converts `true` to `false` and `false` to `true`.

<!-- @[logical_not_operator](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
let isA: boolean = true;
let isB: boolean = false;

console.info(`${!isA}`);  // false
console.info(`${!isB}`);  // true

// Convert double negation to a Boolean value.
let notValue: number = 5;
console.info(`${!!notValue}`);  // true (equivalent to Boolean(notValue))
```

### Logical AND Operator (&&)

Logical AND (&&) returns `true` only when both operands are `true`. If the left-hand operand is `false`, evaluation short-circuits and skips the right-hand operand.

<!-- @[logical_and_operator](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
let andA: boolean = true;
let andB: boolean = true;
let andC: boolean = false;

console.info(`${andA && andB}`);  // true
console.info(`${andA && andC}`);  // false

// Truth table
// true && true   → true
// true && false  → false
// false && true  → false
// false && false → false

// Condition check
let andAge: number = 25;
let hasLicense: boolean = true;
let hasInsurance: boolean = true;

let canDrive: boolean = andAge >= 18 && hasLicense && hasInsurance;
```

### Logical OR Operator (||)

Logical OR (||) returns `true` when either operand is `true`. If the left-hand operand is `true`, evaluation short-circuits and skips the right-hand operand.

<!-- @[logical_or_operator](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
let orA: boolean = true;
let orB: boolean = false;
let orC: boolean = false;

console.info(`${orA || orB}`);  // true
console.info(`${orB || orC}`);  // false

// Truth table
// true || true   → true
// true || false  → true
// false || true  → true
// false || false → false

// Either condition is met.
let orRole: string = 'admin';
let hasPermission: boolean = true;

let canAccess: boolean = orRole === 'admin' || hasPermission;
```

### Short-Circuit Evaluation

The logical AND (&&) and logical OR (||) operators skip the evaluation of the right-hand side when the left-hand side already determines the result.

<!-- @[short_circuit_evaluation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
// && short-circuit: the right side is not executed when the left side is false.
function expensiveCheck(): boolean {
  console.info('Performing complex check');
  return true;
}

let enabled: boolean = false;
let circuitResult: boolean = enabled && expensiveCheck();  // expensiveCheck is not executed.

// || short-circuit: if the left side is true, the right side is not evaluated.
function fallbackValue(): string {
  console.info('Use the default value.');
  return 'default';
}

let circuitPrimary: string = 'primary';
let circuitValue: string = circuitPrimary || fallbackValue();  // "primary"; fallbackValue is not called.

// ?? short-circuit: if the left side is not null/undefined, the right side is not evaluated.
function expensiveDefault(): string {
  console.info('Perform the expensive default value calculation.');
  return 'default';
}

let provided: string = 'text';
let circuitResult2: string = provided ?? expensiveDefault();  // expensiveDefault is not executed.
```

## Operator Precedence and Associativity

Operator precedence determines the evaluation order of different operators. Associativity determines the evaluation direction (left to right or right to left) for operators of the same precedence. The following table lists the operators in this chapter from highest to lowest precedence:

| Precedence | Operator | Description | Associativity |
| ------ | ------ | ---- | ------ |
| 1 | `()` | Parenthesized grouping | - |
| 2 | `?.` | Optional chaining | Left to right |
| 3 | `++`, `--` (postfix), `!` (postfix) | Postfix increment, postfix decrement, non-null assertion | - |
| 4 | `**` | Exponentiation | Right to left |
| 5 | `!`, `+`, `-` (unary), `++`, `--` (prefix) | Unary operators | Right to left |
| 6 | `*`, `/`, `%` | Multiplication, division, remainder | Left to right |
| 7 | `+`, `-` | Addition, subtraction | Left to right |
| 8 | `<`, `<=`, `>`, `>=` | Relational comparison | Left to right |
| 9 | `===`, `!==`, `==`, `!=` | Equality comparison | Left to right |
| 10 | `&&` | Logical AND | Left to right |
| 11 | `\|\|`, `??` | Logical OR, nullish coalescing | Left to right |
| 12 | `?:` | Ternary conditional | Right to left |
| 13 | `=`, `+=`, `-=`, `*=`, `/=`, `%=`, `**=`, `??=`, `\|\|=`, `&&=` | Assignment, compound assignment | Right to left |

For the precedence and associativity of advanced operators such as bitwise and shift operators, see [Advanced Operators](arkts-language-guide-advanced-operators.md#precedence-and-associativity-of-advanced-operators).

`??` cannot be mixed directly with `&&` or `||`; use parentheses to group expressions. In practice, explicitly mark precedence with parentheses to avoid ambiguity from relying on default rules:

<!-- @[parentheses_for_precedence](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
let precA: number = 5;
let precB: number = 3;
let precC: number = 10;
let precD: number = 2;
let precInput: string | null = 'hello';
// Use parentheses to clarify the precedence.
let precResult: number = (precA + precB) * (precC - precD);
let valid: boolean = (precA > precB) && (precC < precD);
let precValue: string = (precInput ?? 'default') + ' suffix';
```

## Increment and Decrement Operators

The increment (++) and decrement (--) operators add 1 to or subtract 1 from a numeric value. The prefix form changes the value before use, while the postfix form uses the value before changing it.

<!-- @[increment_decrement_operators](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
let decrCount: number = 5;

// Pre-increment: increment first, then use.
let preInc: number = ++decrCount;  // decrCount=6, preInc=6

// Post-increment: use first, then increment.
let postInc: number = decrCount++; // decrCount=7, postInc=6

// Pre-decrement
let preDec: number = --decrCount;  // decrCount=6, preDec=6

// Postfix decrement.
let postDec: number = decrCount--; // decrCount=5, postDec=6
```

## Optional Chaining Operator

The optional chaining operator (?.) safely accesses a variable or its properties that may be `null`/`undefined`, avoiding runtime errors.

<!-- @[optional_chaining_operator](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
// Access works whether the variable is an array or null.
function printScores(scores: number[] | null) {
  // Safely access a property: return undefined if scores is null.
  let scoreCount: number | undefined = scores?.length;
  console.info(`Score count: ${scoreCount}`);
  
  // Safely call a method: return undefined if scores is null.
  let hasPass: boolean | undefined = scores?.includes(60);
  console.info(`Has passing score: ${hasPass}`);
  
  // Combine with nullish coalescing to provide a default.
  let safeCount: number = scores?.length ?? 0;
  console.info(`Safe count: ${safeCount}`);
}

// Test the null case.
printScores(null);  // Output: Score count: undefined, Has passing score: undefined, Safe count: 0

// Test the array case.
printScores([80, 95]);  // Output: Score count: 2, Has passing score: false, Safe count: 2
```

## Non-Null Assertion Operator

The non-null assertion operator (!) follows a nullable value and tells the compiler that the value is neither `null` nor `undefined`, allowing direct property access or method calls. Unlike optional chaining `?.`, which safely returns `undefined` for a nullish value, `!` assumes the value is non-null and causes a runtime exception if it is actually nullish. Use it only when non-nullness is guaranteed; otherwise, prefer `?.` or `??`.

<!-- @[non_null_assertion_operator](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Operators.ets) -->

``` TypeScript
function getValue(): string | null {
  return 'Alice';
}

let nickname: string | null = getValue();
console.info(nickname!.toUpperCase());  // 'ALICE' (call directly after asserting non-nullness)
```
