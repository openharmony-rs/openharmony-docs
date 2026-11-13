---
kits: ["ArkTS Kit"]
description: "Concepts and usage of ArkTS advanced operators, including bitwise, compound assignment, type-checking, spread, and rest operators, with an operator precedence table and ArkTS constraints."
keywords: [ArkTS, advanced operators, bitwise operators, compound assignment operators, type-checking operators, spread operator, operator precedence]
doctype: guide
status: active
---

# Advanced Operators
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @jokerxd-liu-->
<!--Designer: @jokerxd-liu-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=8923bda514baa1452b967ea964ea779c7417bd8e translatedAt=2026-11-12T12:34:02.208Z pushedAt=2026-10-30T06:21:33.935Z nl=1 -->

The [Basic Operators](arkts-language-guide-basic-operators.md) chapter introduces common operators for assignment, arithmetic, comparison, and logic. This chapter further introduces bitwise operators, compound assignment operators, type-checking operators, spread and rest operators, and the precedence and associativity of advanced operators.

## Bitwise Operators

Bitwise operators directly manipulate the binary bits of integers and are commonly used for permission flag management, data compression, encryption and decryption, and performance-sensitive mathematical computation. For example, use bitwise OR to combine permissions (`READ | WRITE`), bitwise AND to check permissions (`flags & READ`), and bitwise XOR to toggle flags (`flags ^ TOGGLE`). Bitwise operations are widely used in low-level and system programming, but are rarely used directly in everyday business logic.

### Bitwise AND (&)

The bitwise AND operator performs a logical AND operation on each bit of two integers. The result is 1 only when both corresponding bits are 1.

<!-- @[bitwise_and](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/AdvancedOperators.ets) -->

``` TypeScript
let a: number = 5;   // Binary 0101
let b: number = 3;   // Binary 0011
let bitAndResult: number = a & b;  // Binary 0001, decimal 1

// Use case: check flag bits.
const READ: number = 0b001;
const WRITE: number = 0b010;
const EXECUTE: number = 0b100;

let permission: number = 0b110;  // Writable and executable.

let canRead: boolean = (permission & READ) !== 0;
let canWrite: boolean = (permission & WRITE) !== 0;
let canExecute: boolean = (permission & EXECUTE) !== 0;

console.info(`Read: ${canRead}`);      // false
console.info(`Write: ${canWrite}`);     // true
console.info(`Execute: ${canExecute}`);   // true

// Clear the flag bit.
permission = permission & ~WRITE;  // Clear the write permission.
```

### Bitwise OR (|)

The bitwise OR operator performs a logical OR operation on each bit of two integers. If either corresponding bit is 1, the result bit is 1.

<!-- @[bitwise_or](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/AdvancedOperators.ets) -->

``` TypeScript
let bitOrA: number = 5;   // Binary: 0101
let bitOrB: number = 3;   // Binary: 0011
let bitOrResult: number = bitOrA | bitOrB;  // Binary: 0111 (decimal: 7)

// Use case: set flag bits.
const BOLD: number = 0b001;
const ITALIC: number = 0b010;
const UNDERLINE: number = 0b100;

let style: number = 0;
style = style | BOLD | ITALIC;  // Set bold and italic.

// Combine multiple flags.
let fullStyle: number = BOLD | ITALIC | UNDERLINE;  // 0b111
```

### Bitwise XOR (^)

The bitwise XOR operator performs an XOR operation on each bit of two integers. The result is 1 when the corresponding bits differ.

<!-- @[bitwise_xor](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/AdvancedOperators.ets) -->

``` TypeScript
let bitXorA: number = 5;   // Binary: 0101
let bitXorB: number = 3;   // Binary: 0011
let bitXorResult: number = bitXorA ^ bitXorB;  // Binary: 0110 (Decimal: 6)

// Use case: toggle a flag bit.
let bitXorFlags: number = 0b101;
bitXorFlags = bitXorFlags ^ 0b001;  // Toggle bit 0: 0b100.
bitXorFlags = bitXorFlags ^ 0b001;  // Toggle bit 0 again: 0b101.

// Simple encryption.
let data: number = 42;
let key: number = 123;
let encrypted: number = data ^ key;
let decrypted: number = encrypted ^ key;
console.info(`${decrypted === data}`);  // true
```

### Bitwise NOT (~)

The bitwise NOT operator inverts each bit of an integer, turning 0 into 1 and 1 into 0.

<!-- @[bitwise_not](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/AdvancedOperators.ets) -->

``` TypeScript
let bitNotA: number = 5;   // Binary: 0101
let bitNotResult: number = ~bitNotA;  // Binary: ...11111010 (decimal: -6)

// Formula: ~x = -(x + 1)
console.info(`${~5}`);   // -6
console.info(`${~(-6)}`); // 5

// Use case: clear the flag bit.
const FLAG: number = 0b010;
let bitNotValue: number = 0b111;
bitNotValue = bitNotValue & ~FLAG;  // Clear bit 1: 0b101.
```

### Left Shift Operator (<<)

The left shift operator shifts the binary bits of an integer to the left by a specified number of positions, which is equivalent to multiplying by a power of 2.

<!-- @[left_shift](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/AdvancedOperators.ets) -->

``` TypeScript
let lshiftA: number = 5;   // Binary: 0101
let lshiftResult: number = lshiftA << 2;  // Binary: 010100 (decimal: 20)

// Shifting left by n bits is equivalent to multiplying by 2^n
console.info(`${5 << 1}`);  // 10 (5 * 2)
console.info(`${5 << 2}`);  // 20 (5 * 4)
console.info(`${5 << 3}`);  // 40 (5 * 8)

// Use case: fast multiplication.
let base: number = 10;
let doubled: number = base << 1;   // 20
let quadrupled: number = base << 2;  // 40
```

### Right Shift Operator (>>)

The right shift operator shifts the binary bits of an integer to the right by a specified number of positions, which is equivalent to dividing by a power of 2.

<!-- @[right_shift](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/AdvancedOperators.ets) -->

``` TypeScript
let rshiftA: number = 20;  // Binary 010100
let rshiftResult: number = rshiftA >> 2;  // Binary 0101, decimal 5

// Shifting right by n bits is equivalent to dividing by 2^n (rounded down).
console.info(`${20 >> 1}`);  // 10
console.info(`${20 >> 2}`);  // 5
console.info(`${20 >> 3}`);  // 2

// Right shift of a negative number.
let neg: number = -20;
console.info(`${neg >> 2}`);  // -5

// Use case: fast division.
let total: number = 100;
let half: number = total >> 1;  // 50
let quarter: number = total >> 2;  // 25
```

### Unsigned Right Shift Operator (>>>)

The unsigned right shift operator shifts the integer's binary bits to the right and pads zeros on the left. The difference from `>>` is that `>>` preserves the sign bit (padding 1s on the left for negative numbers), while `>>>` pads zeros on the left regardless of the sign. A common use is to convert a floating-point number to a 32-bit unsigned integer via `>>> 0`.

<!-- @[unsigned_right_shift](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/AdvancedOperators.ets) -->

``` TypeScript
let rshiftA2: number = 20;  // Binary: 010100
let rshiftResult2: number = rshiftA2 >>> 2;  // Binary: 0101 (decimal: 5)

// Same as >> for positive numbers.
console.info(`${20 >> 2}`);   // 5
console.info(`${20 >>> 2}`);  // 5

// Handles negative numbers differently.
let rshiftNeg: number = -20;  // Binary: ...11101100
console.info(`${rshiftNeg >> 2}`);    // -5 (sign bit preserved)
console.info(`${rshiftNeg >>> 2}`);   // 1073741819 (sign bit becomes 0)

// Use case: convert to an unsigned integer.
function toUnsigned(value: number): number {
  return value >>> 0;
}
```

## Compound Assignment Operators

Compound assignment operators combine an operation and an assignment into a single operation.

### Syntax of Compound Assignment

Compound assignment operators combine a binary operation and assignment into one step, as shorthand for `x = x op y`. Arithmetic operators include `+=`, `-=`, `*=`, `/=`, `%=`, and `**=`; bitwise operators include `&=`, `|=`, `^=`, `<<=`, `>>=`, and `>>>=`; logical operators include `??=`, `||=`, and `&&=`.

``` TypeScript
variable operator= expression
Equivalent to: variable = variable operator expression
```

<!-- @[compound_assignment_basics](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/AdvancedOperators.ets) -->

``` TypeScript
let compoundA: number = 10;
compoundA += 5;
console.info(`${compoundA}`);  // 15
compoundA -= 3;
console.info(`${compoundA}`);  // 12
compoundA *= 2;
console.info(`${compoundA}`);  // 24
compoundA /= 4;
console.info(`${compoundA}`);  // 6
```

### Bitwise Compound Assignment

Bitwise compound assignment includes `&=` (bitwise AND assignment), `|=` (bitwise OR assignment), `^=` (bitwise XOR assignment), `<<=` (left shift assignment), `>>=` (right shift assignment), and `>>>=` (unsigned right shift assignment). These operators assign the result of the bitwise operation directly to the left operand.

<!-- @[compound_assignment_bitwise](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/AdvancedOperators.ets) -->

``` TypeScript
let compoundFlags: number = 0b1010;

// Bitwise AND assignment
compoundFlags &= 0b1100;  // compoundFlags = compoundFlags & 0b1100 = 0b1000

// Bitwise OR assignment
compoundFlags |= 0b0011;  // compoundFlags = compoundFlags | 0b0011 = 0b1011

// Bitwise XOR assignment
compoundFlags ^= 0b0001;  // compoundFlags = compoundFlags ^ 0b0001 = 0b1010

// Left shift assignment
let compoundValue: number = 5;
compoundValue <<= 2;  // compoundValue = compoundValue << 2 = 20

// Right shift assignment
compoundValue >>= 1;  // compoundValue = compoundValue >> 1 = 10

// Unsigned right shift assignment
compoundValue >>>= 1;  // compoundValue = compoundValue >>> 1 = 5
```

### Arithmetic Compound Assignment

Arithmetic compound assignment includes `+=`, `-=`, `*=`, `/=`, `%=`, and `**=`, which assign the result of an arithmetic operation directly to the left operand.

<!-- @[compound_assignment_arithmetic](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/AdvancedOperators.ets) -->

``` TypeScript
// Addition assignment
let compoundTotal: number = 100;
compoundTotal += 50;
console.info(`${compoundTotal}`);  // 150

// Subtraction assignment
let balance: number = 1000;
balance -= 200;
console.info(`${balance}`);  // 800

// Multiplication assignment
let price: number = 10;
price *= 2;
console.info(`${price}`);  // 20

// Division assignment.
let amount: number = 100;
amount /= 4;
console.info(`${amount}`);  // 25

// Modulo assignment.
let compoundValue2: number = 17;
compoundValue2 %= 5;
console.info(`${compoundValue2}`);  // 2

// Exponentiation assignment.
let compoundBase: number = 2;
compoundBase **= 4;
console.info(`${compoundBase}`);  // 16
```

### Logical Compound Assignment

Logical compound assignment includes `??=` (nullish assignment), `||=` (logical OR assignment), and `&&=` (logical AND assignment). These operators combine a logical operation and assignment while retaining the short-circuit behavior of the corresponding logical operator: the right-hand expression is evaluated only when assignment is needed.

- `x ??= y`: assigns `y` to `x` only when `x` is `null` or `undefined`.
- `x ||= y`: assigns `y` to `x` only when `x` is a [falsy value](arkts-language-guide-basic-operators.md#logical-assignment-operators---).
- `x &&= y`: assigns `y` to `x` only when `x` is truthy.

<!-- @[logical_operation_compound_assignment](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/AdvancedOperators.ets) -->

``` TypeScript
// ??= assigns only when the left operand is null or undefined.
let logicAssignConfig: string | null = null;
logicAssignConfig ??= 'default';  // "default"

// ||= assigns only when the left operand is falsy.
let logicAssignLabel: string = '';
logicAssignLabel ||= 'unnamed';  // "unnamed"

// &&= assigns only when the left operand is truthy.
let logicAssignCount: number = 10;
logicAssignCount &&= logicAssignCount * 2;  // 20
```

## Type-Checking Operators

The type-checking operators `typeof` and `instanceof` check the actual type of a value at runtime. They are commonly used in type guards to narrow a union type to a concrete type in conditional branches:

- `typeof value === 'string'`: checks whether `value` is of type `string` (similarly for primitive types such as `number` and `boolean`).
- `pet instanceof Dog`: checks whether `pet` is an instance of the `Dog` class.

For details about type checking and type guards, see [Types](arkts-language-guide-types.md#type-guards).

## Spread and Rest Operators

The spread operator (...) expands array elements into individual elements for merging, copying, and argument passing. The rest operator (...) collects multiple arguments into an array.

### Array Spread Operator

The spread operator (...) expands array elements into individual elements for copying, merging, and passing arguments.

<!-- @[spread_operator_array](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/AdvancedOperators.ets) -->

``` TypeScript
// Spread array elements.
let spreadArr1: number[] = [1, 2, 3];
let spreadArr2: number[] = [4, 5, 6];

// Merge arrays.
let merged: number[] = [...spreadArr1, ...spreadArr2];
console.info(`${merged.join(', ')}`);  // 1, 2, 3, 4, 5, 6

// Insert at any position.
let inserted: number[] = [0, ...spreadArr1, 4];
console.info(`${inserted.join(', ')}`);  // 0, 1, 2, 3, 4

// Copy the array.
let spreadCopied: number[] = [...spreadArr1];
console.info(`${spreadCopied.join(', ')}`);  // 1, 2, 3

// As function arguments: the spread array should be passed to the rest parameter.
function spreadSum(...values: number[]): number {
  let spreadTotal: number = 0;
  for (let value of values) {
    spreadTotal += value;
  }
  return spreadTotal;
}

let numbers: number[] = [1, 2, 3];
let spreadTotal: number = spreadSum(...numbers);  // 6

// Combine spread with array methods.
let spreadMax: number = Math.max(...spreadArr1);  // 3
let min: number = Math.min(...spreadArr2);  // 4
```

### Rest Parameter Operator

The rest parameter operator (...) collects multiple parameters into an array and is used to handle a variable number of parameters.

<!-- @[rest_parameters](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/AdvancedOperators.ets) -->

``` TypeScript
// Rest parameter in function parameters
function sumAll(...numbers: number[]): number {
  let total: number = 0;
  for (const num of numbers) {
    total += num;
  }
  return total;
}

console.info(`${sumAll(1, 2, 3, 4, 5)}`);  // 15

// Combined with fixed parameters
function greet(greeting: string, ...names: string[]): string {
  return `${greeting}, ${names.join(', ')}!`;
}

console.info(`${greet('Hello', 'Alice', 'Bob', 'Charlie')}`);  // 'Hello, Alice, Bob, Charlie!'

// Rest element in array destructuring
let arr: number[] = [1, 2, 3, 4, 5];
// ArkTS does not support destructuring assignment. Extract it manually.
let first: number = arr[0] ?? 0;
let rest: number[] = arr.slice(1);
console.info(`${first}`);  // 1
console.info(`${rest.join(', ')}`);   // 2, 3, 4, 5

// Collect function parameters.
function restProcess(first: string, second: string, ...remaining: string[]): void {
  console.info(`First: ${first}`);
  console.info(`Second: ${second}`);
  console.info(`Remaining: ${remaining.join(', ')}`);
}

restProcess('a', 'b', 'c', 'd', 'e');
// First: a
// Second: b
// Remaining: c, d, e
```

## Precedence and Associativity of Advanced Operators

Operator precedence determines the evaluation order of different operators, while associativity determines the evaluation direction of operators at the same precedence level (left to right or right to left). The following table summarizes the precedence and associativity of common ArkTS operators, from highest to lowest precedence. It covers the bitwise, type-checking, and compound assignment operators introduced in this chapter, as well as common operators introduced in [Basic Operators](arkts-language-guide-basic-operators.md):

| Precedence | Operator | Description | Associativity |
| ------ | ------ | ---- | ------ |
| 1 | `()` | Parenthesized grouping | - |
| 2 | `.`, `[]`, `?.` | Member access, optional chaining | Left to right |
| 3 | `++`, `--` (postfix), `!` (postfix) | Postfix increment, postfix decrement, non-null assertion | - |
| 4 | `!`, `~`, `typeof`, `+`, `-` (unary), `++`, `--` (prefix) | Unary operators | Right to left |
| 5 | `**` | Exponentiation | Right to left |
| 6 | `*`, `/`, `%` | Multiplication, division, remainder | Left to right |
| 7 | `+`, `-` | Addition, subtraction | Left to right |
| 8 | `<<`, `>>`, `>>>` | Bitwise shifts | Left to right |
| 9 | `<`, `<=`, `>`, `>=`, `instanceof` | Relational comparison, `instanceof` type checking | Left to right |
| 10 | `===`, `!==`, `==`, `!=` | Equality comparison | Left to right |
| 11 | `&` | Bitwise AND | Left to right |
| 12 | `^` | Bitwise XOR | Left to right |
| 13 | `\|` | Bitwise OR | Left to right |
| 14 | `&&` | Logical AND | Left to right |
| 15 | `\|\|`, `??` | Logical OR, nullish coalescing | Left to right |
| 16 | `?:` | Ternary conditional | Right to left |
| 17 | `=`, `+=`, `-=`, `*=`, `/=`, `%=`, `**=`, `&=`, `\|=`, `^=`, `<<=`, `>>=`, `>>>=`, `??=`, `\|\|=`, `&&=` | Assignment, compound assignment | Right to left |

Operators at the same precedence level are evaluated according to their associativity. For example, `10 - 5 - 2` is evaluated from left to right, equivalent to `(10 - 5) - 2`. The bitwise operators `&`, `^`, and `|` introduced in this chapter have precedence between equality comparison and logical operators, in decreasing order. For example, `flags & MASK !== 0` is parsed as `flags & (MASK !== 0)`, so write `(flags & MASK) !== 0` when checking flags. `??` cannot be mixed directly with `&&` or `||`; parentheses are required for grouping. For complex expressions, use parentheses to make precedence explicit and avoid ambiguity from relying on default rules:

<!-- @[parentheses_for_precedence](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/AdvancedOperators.ets) -->

``` TypeScript
let precA: number = 5;
let precB: number = 3;
let precC: number = 10;
let precD: number = 2;
let precInput: string | null = 'hello';
// Use parentheses to clarify precedence.
let precResult: number = (precA + precB) * (precC - precD);
let valid: boolean = (precA > precB) && (precC < precD);
let precValue: string = (precInput ?? 'default') + ' suffix';
```
