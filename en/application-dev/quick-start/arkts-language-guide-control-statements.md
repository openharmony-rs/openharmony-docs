---
kits: ["ArkTS Kit"]
description: "Syntax and usage of ArkTS branch, loop, and jump statements, including common techniques for loop control and early exits."
keywords: [ArkTS, control statements, branch statements, loop statements, switch, jump statements, early exits]
doctype: guide
status: active
---

# Control Statements
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @jokerxd-liu-->
<!--Designer: @jokerxd-liu-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=8923bda514baa1452b967ea964ea779c7417bd8e translatedAt=2026-11-12T12:34:02.325Z pushedAt=2026-10-30T06:21:33.935Z nl=1 -->

Control statements control the execution flow of a program. ArkTS provides branch statements, loop statements, and jump statements to implement complex logic control.

## Branch Statements

Branch statements select different execution paths based on conditions.

### if Statement

The `if` statement executes the corresponding code block when the condition is `true`. It can be used with `else if` and `else` to handle multi-branch scenarios. For simple scenarios where code only needs to execute when the condition is met, omit `else` if no other branches are needed:

<!-- @[simple_condition_check](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Control.ets) -->

``` TypeScript
let value: number = 10;

// Only check the condition; no else needed.
if (value > 0) {
  console.info('Positive number');
}

// Omit an empty else branch.
if (value < 0) {
  console.info('Negative number');
}

// Concise form.
if (value !== 0) {
  console.info('non-zero');
}
```

When multiple mutually exclusive conditions need to be handled, use `else if` to chain multiple judgment branches:

<!-- @[if_else_if_chain](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Control.ets) -->

``` TypeScript
let chainScore: number = 85;

if (chainScore >= 90) {
  console.info('Excellent');
} else if (chainScore >= 80) {
  console.info('Good');
} else if (chainScore >= 60) {
  console.info('Pass');
} else {
  console.info('Fail');
}

// Combine multiple conditions
let role: string = 'admin';
let hasPermission: boolean = true;

if (role === 'admin') {
  console.info('Administrator permission');
} else if (role === 'user' && hasPermission) {
  console.info('User permission');
} else {
  console.info('No permission');
}
```


### switch Statement

The `switch` statement matches `case` branches based on an expression's value and suits multi-branch selection among discrete values.

``` TypeScript
switch (expression) {
  case value1:
    // Execute the code.
    break;
  case value2:
    // Execute the code.
    break;
  default:
    // Execute the default code.
    break;
}
```

The following example shows the basic usage of `switch` through date and status matching:

<!-- @[switch_basic_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Control.ets) -->

``` TypeScript
let day: number = 3;

switch (day) {
  case 1:
    console.info('Monday');
    break;
  case 2:
    console.info('Tuesday');
    break;
  case 3:
    console.info('Wednesday');
    break;
  case 4:
    console.info('Thursday');
    break;
  case 5:
    console.info('Friday');
    break;
  case 6:
    console.info('Saturday');
    break;
  case 7:
    console.info('Sunday');
    break;
  default:
    console.info('Invalid date');
}

let status: string = 'active';

switch (status) {
  case 'active':
    console.info('Active state');
    break;
  case 'inactive':
    console.info('Inactive state');
    break;
  case 'pending':
    console.info('Pending state');
    break;
  default:
    console.info('Unknown state');
}
```

The `break` statement prevents `switch` from falling through. Omitting `break` and unintentionally executing further logic is a common programming error.

The `default` branch catches all unmatched cases and suits scenarios such as handling unknown commands.

Omitting `break` is commonly used to combine multiple `case` labels and share the same execution logic, grouping values for matching:

<!-- @[switch_case_fallthrough](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Control.ets) -->

``` TypeScript
let fallValue: number = 5;

switch (fallValue) {
  case 1:
  case 2:
  case 3:
    console.info('Small value');
    break;
  case 4:
  case 5:
  case 6:
    console.info('Medium value');
    break;
  default:
    console.info('Large value');
}
```

`switch` and `if...else if` suit different scenarios: the former handles explicit, discrete values, while the latter handles complex conditions and ranges. The following example compares the two approaches:

<!-- @[switch_vs_if_range](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Control.ets) -->

``` TypeScript
let rangeScore: number = 85;

// Use if to implement range matching.
if (rangeScore >= 90 && rangeScore <= 100) {
  console.info('Grade A');
} else if (rangeScore >= 80 && rangeScore < 90) {
  console.info('Grade B');
} else if (rangeScore >= 70 && rangeScore < 80) {
  console.info('Grade C');
} else if (rangeScore >= 60 && rangeScore < 70) {
  console.info('Grade D');
} else {
  console.info('Grade F');
}

// Use switch mapping.
let grade: number = Math.floor(rangeScore / 10);

switch (grade) {
  case 10:
  case 9:
    console.info('Grade A');
    break;
  case 8:
    console.info('Grade B');
    break;
  case 7:
    console.info('Grade C');
    break;
  case 6:
    console.info('Grade D');
    break;
  default:
    console.info('Grade F');
}
```

## Loop Statements

A loop statement repeatedly executes a code block while its condition holds true. ArkTS provides several loop forms, including `for`, `for...of`, `while`, and `do...while`.

### for Loop (Traditional Counter-Based)

A traditional `for` loop uses a counter and consists of initialization, a condition check, and an iteration expression.

Execution proceeds as follows: run the initialization expression once, check the condition (`true` continues and `false` exits), execute the loop body, run the iteration expression, and return to the condition check.

<!-- @[traditional_for_loop](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Control.ets) -->

``` TypeScript
// Basic structure
// Initialization: let i = 0
// Condition: i < 5
// Increment: i++
for (let i = 0; i < 5; i++) {
  console.info(`${i}`);
}

// Reverse loop
for (let i = 5; i >= 0; i--) {
  console.info(`${i}`);
}

// Step of 2
for (let i = 0; i < 10; i += 2) {
  console.info(`${i}`);
}

// Iterate over array indices
let arr: number[] = [10, 20, 30, 40, 50];
for (let i = 0; i < arr.length; i++) {
  console.info(`Index ${i}: ${arr[i] ?? 0}`);
}

// Multi-variable loop
for (let i = 0, j = 10; i < j; i++, j--) {
  console.info(`i=${i}, j=${j}`);
}
```
### for...of Loop

`for...of` iterates over elements of an iterable object, providing concise syntax, versatility, and type safety.

<!-- @[for_of_iteration](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Control.ets) -->

``` TypeScript
// Iterate over the array.
let numbers: number[] = [1, 2, 3, 4, 5];
for (let num of numbers) {
  console.info(`${num}`);
}

// Iterate over the string.
let text: string = 'Hello';
for (let char of text) {
  console.info(`${char}`);
}
```

`for...of` is commonly used to traverse collection types. For more examples, see [Collection Types](./arkts-language-guide-collection-types.md).

### while Loop

A `while` loop checks its condition before executing the loop body and is controlled by that condition.

``` TypeScript
while (condition) {
  // Loop body code.
  // Note: Update the condition variable inside the loop body.
}
```

`while` is suitable for scenarios where the number of iterations cannot be determined at compile time, where iteration is based on a specific condition (such as a non-empty queue), where a condition is awaited (such as polling), or where the loop condition needs to be adjusted dynamically.

<!-- @[while_loop_basic](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Control.ets) -->

``` TypeScript
// Basic structure
let count: number = 0;
while (count < 5) {
  console.info(`${count.toString()}`);
  count++;
}

// Skip the loop body when the condition is false.
let loopValue: number = 10;
while (loopValue < 5) {
  console.info(`${loopValue.toString()}`);  // Not executed.
  loopValue++;
}

// Process data until the condition is met.
let data: string | null = 'data';
while (data !== null) {
  console.info(`${data}`);
  data = getNextData();
}

function getNextData(): string | null {
  // Return data or null.
  return null;
}

// Accumulate until the condition is met.
let sum: number = 0;
let i: number = 1;
while (sum < 100) {
  sum += i;
  i++;
}
console.info(`Accumulated to ${sum}`);
```

### do...while Loop

A `do...while` loop executes its body before checking the condition. It suits scenarios that require execution before checking, such as user input validation (ask at least once), resource acquisition (try at least once), and state checks. It executes the body, checks the condition, continues if `true`, and exits if `false`.

<!-- @[do_while_loop](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Control.ets) -->

``` TypeScript
// Basic structure: execute at least once.
let loopCount: number = 0;
do {
  console.info(`${loopCount.toString()}`);
  loopCount++;
} while (loopCount < 5);

// Execute once even if the condition is initially false.
let loopValue2: number = 10;
do {
  console.info(`${loopValue2.toString()}`);  // Execute once and output 10.
  loopValue2++;
} while (loopValue2 < 5);

// Validate user input.
let input: string = '';
do {
  input = getInput();
} while (input.length === 0);

function getInput(): string {
  return 'valid input';
}

// Retry logic.
let success: boolean = false;
let attempts: number = 0;
do {
  success = tryConnect();
  attempts++;
} while (!success && attempts < 3);

function tryConnect(): boolean {
  return true;
}
```

## Jump Statements

Jump statements change loop execution flow.

### break Statement

`break` exits a loop or `switch`, immediately terminating the current loop or branch.

`break` is commonly used to stop after finding an element, exit when a condition is met, break out on errors, or improve performance by ending unnecessary iterations early.

<!-- @[break_statement](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Control.ets) -->

``` TypeScript
// Exit the for loop.
for (let i = 0; i < 10; i++) {
  if (i === 5) {
    break;  // Exit the loop.
  }
  console.info(`${i.toString()}`);
}
// Output: 0, 1, 2, 3, 4

// Exit the while loop.
let breakCount: number = 0;
while (breakCount < 10) {
  if (breakCount === 5) {
    break;
  }
  console.info(`${breakCount.toString()}`);
  breakCount++;
}

// Exit after finding the element.
let breakNumbers: number[] = [1, 2, 3, 4, 5];
for (let num of breakNumbers) {
  if (num === 3) {
    console.info('Found 3');
    break;
  }
}
```

In nested loops, a labeled `break` can directly exit the outer loop:

<!-- @[nested_loop_break](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Control.ets) -->

``` TypeScript
// Labeled break: exit the outer loop.
outerLoop: for (let i = 0; i < 10; i++) {
  for (let j = 0; j < 10; j++) {
    if (i + j === 15) {
      console.info(`Found: i=${i}, j=${j}`);
      break outerLoop;
    }
  }
}
```

### continue Statement

`continue` skips the current iteration and proceeds to the next one. It is commonly used to filter invalid data, skip when a condition is met, improve performance by avoiding unnecessary code, and simplify logic by replacing complex `if-else` nesting.

<!-- @[continue_statement](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Control.ets) -->

``` TypeScript
// Skip even numbers.
for (let i = 0; i < 10; i++) {
  if (i % 2 === 0) {
    continue;  // Skip even numbers.
  }
  console.info(`${i.toString()}`);
}
// Output: 1, 3, 5, 7, 9

// Skip specific values.
let continueNumbers: number[] = [1, 2, 3, 4, 5];
for (let num of continueNumbers) {
  if (num === 3) {
    continue;  // Skip 3.
  }
  console.info(`${num.toString()}`);
}
// Output: 1, 2, 4, 5

// Filter invalid data.
let continueData: (string | null)[] = ['valid', '', 'valid', null, 'valid'];
for (let item of continueData) {
  if (item === '' || item === null) {
    continue;  // Skip null values.
  }
  processItem(item);
}

function processItem(item: string): void {
  console.info(`Processing: ${item}`);
}
```

Similarly, `continue` also supports the label syntax, which is used to skip the current iteration of the outer loop:

<!-- @[nested_loop_continue](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Control.ets) -->

``` TypeScript
// Labeled continue: skip the current iteration of the outer loop.
outerLoop: for (let i = 0; i < 5; i++) {
  for (let j = 0; j < 5; j++) {
    if (j === 2) {
      continue outerLoop;
    }
    console.info(`i=${i}, j=${j}`);
  }
}
```

### Other Control Statements (return and throw)

ArkTS also supports other control statements, such as [return](./arkts-language-guide-functions.md) and [throw](./arkts-language-guide-error-handling.md). For details, see the linked topics.
