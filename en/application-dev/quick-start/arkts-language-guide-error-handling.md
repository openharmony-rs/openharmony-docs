---
kits: ["ArkTS Kit"]
description: "Explains ArkTS error handling, including try-catch-finally, throwing errors with throw, asynchronous error handling, and error recovery strategies."
keywords: ["ArkTS", "error handling", "try-catch-finally", "throw", "Error object", "asynchronous error handling", "error recovery"]
doctype: guide
status: active
---

# Error Handling
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @jokerxd-liu-->
<!--Designer: @jokerxd-liu-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=8923bda514baa1452b967ea964ea779c7417bd8e translatedAt=2026-11-12T12:34:02.353Z pushedAt=2026-10-30T06:21:33.935Z nl=1 -->

Error handling is an important part of programming. A sound error handling mechanism improves program robustness and maintainability.

## Basic Concepts of Error Handling

ArkTS uses `try-catch-finally` to catch runtime errors and `throw` to explicitly throw `Error` objects, allowing programs to handle exceptional conditions gracefully.

### Definition and Classification of Errors

An error is an abnormal situation that occurs during program execution. Errors are classified into syntax errors, runtime errors, and logic errors, each requiring a different handling approach.

<!-- @[ts_basic_error_types](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/ErrorHandling.ts) -->

``` TypeScript
// Compile-time type error: number has no toUpperCase method
let num: number = 10;
num.toUpperCase();

// Compile-time name error: the variable is not declared
console.info(`${undefinedVariable}`);

// Runtime range error: actively thrown by business validation
function readAt(values: number[], index: number): number {
  if (index < 0 || index >= values.length) {
    throw new RangeError('Array index out of range');
  }
  return values[index] ?? 0;
}

let readAtValues: number[] = [1, 2, 3];
try {
  readAt(readAtValues, 3);
} catch (error) {
  console.error(`Failed to read: ${(error as Error).message}`);
}
```

### Core Goals of Error Handling

Error handling aims to catch errors, provide recovery mechanisms, and propagate error information to ensure program robustness and availability. Follow these principles: catch only errors you can handle (do not catch all errors), log error information for tracing, provide appropriate recovery or fallback mechanisms, and do not ignore errors in `catch` blocks.

<!-- @[divide_with_error_handling](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/ErrorHandling.ets) -->

``` TypeScript
function divide(a: number, b: number): number {
  if (b === 0) {
    throw new Error('The divisor cannot be zero');
  }
  return a / b;
}

try {
  let result: number = divide(10, 0);
  console.info(`${result}`);
} catch (error) {
  console.error(`Calculation failed: ${(error as Error).message}`);
  // Provide a default value to implement fault tolerance.
  let fallbackResult: number = 0;
  console.info(`Using default value: ${fallbackResult}`);
}
```

## Creating and Using Error Objects

Create an error object using `new Error(message)`. It can carry properties such as `name`, `message`, and `stack`. In a `catch` block, use `instanceof` to distinguish error types and read details.

### Using the Native Error Class

JavaScript provides the native `Error` class as the base class of all error objects. It is the fundamental type for error handling and provides a standard error information structure.

<!-- @[error_object_properties](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/ErrorHandling.ets) -->

``` TypeScript
// Create a basic error object.
let error1: Error = new Error('This is an error');
let error2: Error = new Error(); // Optional error message.

// Properties of the Error object.
console.info(`${error1.name}`);      // 'Error'
console.info(`${error1.message}`);   // 'This is an error'
console.info(`${error1.stack ?? 'No stack information'}`);     // Error stack information.

// Throw an error.
function validateAge(age: number): void {
  if (age < 0 || age > 150) {
    throw new Error('Age must be between 0 and 150');
  }
}

try {
  validateAge(-5);
} catch (error) {
  console.error((error as Error).message);
}
```

### Native Error Types

JavaScript provides multiple native error types, each corresponding to a specific error scenario, which facilitates precise identification and handling of errors.

<!-- @[built_in_error_types](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/ErrorHandling.ets) -->

``` TypeScript
// TypeError: Type error
function typeErrorExample(): void {
  let num: number = 10;
  throw new TypeError('Expected a string, but got a number');
}

// RangeError: Range error
function rangeErrorExample(): void {
  throw new RangeError('Array index out of range');
}

// ReferenceError: reference error
function referenceErrorExample(): void {
  throw new ReferenceError('Variable is not defined');
}

// SyntaxError: syntax error
function syntaxErrorExample(): void {
  throw new SyntaxError('JSON string format is incorrect');
}

// URIError: URI error
function uriErrorExample(): void {
  throw new URIError('URI encoding error');
}
```

### Custom Error Classes

By inheriting from the `Error` class, you can create custom error classes that carry business information and context for fine-grained management.

<!-- @[custom_error_classes](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/ErrorHandling.ets) -->

``` TypeScript
// Custom business error class
class UserBusinessError extends Error {
  public code: number;
  public timestamp: Date;
  
  constructor(code: number, message: string) {
    super(message);
    this.name = 'BusinessError';
    this.code = code;
    this.timestamp = new Date();
  }
  
  public toString(): string {
    return `${this.name} [${this.code}]: ${this.message} at ${this.timestamp.toISOString()}`;
  }
}

// Custom validation error class
class UserValidationError extends Error {
  public field: string;
  public value: string | number | boolean;
  
  constructor(field: string, value: string | number | boolean, message: string) {
    super(message);
    this.name = 'ValidationError';
    this.field = field;
    this.value = value;
  }
}

// Use a custom error
function validateUser(username: string, age: number): void {
  if (username.length < 3) {
    throw new UserValidationError('username', username, 'Username must be at least 3 characters long');
  }
  
  if (age < 18) {
    throw new UserBusinessError(1001, 'User must be at least 18 years old');
  }
}

try {
  validateUser('ab', 16);
} catch (error) {
  if (error instanceof UserValidationError) {
    console.error(`Field validation failed: ${error.field}, value: ${error.value}, reason: ${error.message}`);
  } else if (error instanceof UserBusinessError) {
    console.error(`Business error: ${error.code}, ${error.message}`);
  }
}
```

### Concepts and Mechanisms of Error Propagation

Error propagation means that an error object, once created and thrown, travels up the call stack until caught by the nearest `try-catch`. If it remains uncaught, the program terminates.

### Encapsulating Error Information

Custom error classes extend `Error` with fields such as `code`, `details`, `context`, and `timestamp` to encapsulate error codes, context, and stack information. Methods such as `toErrorInfo` output structured error objects for unified handling and logging by higher layers.

<!-- @[detailed_error_class](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/ErrorHandling.ets) -->

``` TypeScript
interface ErrorInfo {
  code: number;           // Error code
  message: string;         // Error description
  details?: string;        // Details
  stack?: string;          // Stack information.
  timestamp: Date;         // Time when the error occurred.
  context?: Map<string, string>; // Error context.
}

class DetailedError extends Error {
  public code: number;
  public details: string;
  public context: Map<string, string>;
  public timestamp: Date;
  
  constructor(
    code: number,
    message: string,
    details: string = '',
    context: Map<string, string> = new Map<string, string>()
  ) {
    super(message);
    this.name = 'DetailedError';
    this.code = code;
    this.details = details;
    this.context = context;
    this.timestamp = new Date();
  }
  
  public toErrorInfo(): ErrorInfo {
    return {
      code: this.code,
      message: this.message,
      details: this.details,
      stack: this.stack,
      timestamp: this.timestamp,
      context: this.context
    };
  }
}

// Usage example.
function processData(data: string): void {
  if (data.length === 0) {
    let context: Map<string, string> = new Map<string, string>();
    context.set('functionName', 'processData');
    context.set('inputParam', 'data');
    throw new DetailedError(
      1002,
      'Data is empty',
      'The processData function requires non-empty input data.',
      context
    );
  }
}

try {
  processData('');
} catch (error) {
  if (error instanceof DetailedError) {
    let errorInfo: ErrorInfo = error.toErrorInfo();
    console.error(`Error code: ${errorInfo.code}`);
    console.error(`Error message: ${errorInfo.message}`);
    console.error(`Details: ${errorInfo.details ?? ''}`);
    console.error(`Context: ${errorInfo.context ? errorInfo.context.size : 0} item(s)`);
  }
}
```

## Catching Errors with try-catch-finally

The `try` block contains code that may throw errors, the `catch` block catches and handles errors, and the `finally` block runs regardless of whether an error occurs, typically to clean up resources.

### Basic Syntax Structure

`try-catch-finally` consists of three blocks: `try` contains code that may throw errors, `catch` catches and handles errors, and `finally` runs regardless of whether an error occurs (typically for resource cleanup). At least one of `catch` and `finally` must be present.

<!-- @[try_catch_finally_syntax](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/ErrorHandling.ets) -->

``` TypeScript
try {
  // Code that may throw errors.
} catch (error) {
  // Error handling code.
} finally {
  // Code that runs whether or not an error occurs (optional).
}
```
<!-- @[try_catch_finally_example](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/ErrorHandling.ets) -->

``` TypeScript
function divideNumbers(a: number, b: number): number {
  if (b === 0) {
    throw new Error('The divisor cannot be zero');
  }
  return a / b;
}

// Complete try-catch-finally structure.
function calculateExample(): void {
  console.info('Start calculation.');
  
  try {
    let result: number = divideNumbers(10, 0);
    console.info(`Calculation result: ${result}`);
  } catch (error) {
    console.error(`Error caught: ${(error as Error).message}`);
  } finally {
    console.info('Calculation finished (executed regardless of success or failure)');
  }
}

calculateExample();
// Output:
// Calculation started
// Error caught: divisor cannot be zero
// Calculation finished (executed regardless of success or failure)
```

### Catching Specific Error Types

Use `instanceof` in a `catch` block to determine the error type and apply handling such as retries or logging for `NetworkError`, `DatabaseError`, and other types.

<!-- @[error_type_discrimination](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/ErrorHandling.ets) -->

``` TypeScript
class NetworkError extends Error {
  constructor(message: string) {
    super(message);
    this.name = 'NetworkError';
  }
}

class DatabaseError extends Error {
  constructor(message: string) {
    super(message);
    this.name = 'DatabaseError';
  }
}

function fetchData(source: string): string {
  if (source === 'network') {
    throw new NetworkError('Network connection failed');
  } else if (source === 'database') {
    throw new DatabaseError('Database query failed');
  } else {
    throw new Error('Unknown error');
  }
}

function handleFetchData(source: string): void {
  try {
    let data = fetchData(source);
    console.info(`Data fetched successfully: ${data}`);
  } catch (error) {
    // Use instanceof to determine the error type.
    if (error instanceof NetworkError) {
      console.error(`Network error: ${error.message}`);
      // Execute the network error handling logic.
      retryNetworkRequest();
    } else if (error instanceof DatabaseError) {
      console.error(`Database error: ${error.message}`);
      // Execute database error handling logic.
      logDatabaseError(error);
    } else {
      console.error(`Unknown error: ${(error as Error).message}`);
    }
  }
}

function retryNetworkRequest(): void {
  console.info('Retrying network request...');
}

function logDatabaseError(error: DatabaseError): void {
  console.info(`Logging database error: ${error.message}`);
}

handleFetchData('network');  // Network error: network connection failed
handleFetchData('database'); // Database error: Database query failed
handleFetchData('other');    // Unknown error: Unknown error
```

### Execution Characteristics of the finally Block

The `finally` block runs whether or not `try` throws an error or `catch` catches it. It is typically used for cleanup such as releasing resources and closing connections. Even if `try` contains a `return`, `finally` runs before the function returns.

<!-- @[resource_cleanup_finally](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/ErrorHandling.ets) -->

``` TypeScript
class DemoResource {
  public name: string;
  
  constructor(name: string) {
    this.name = name;
    console.info(`${name} resource created`);
  }
  
  public use(): void {
    console.info(`${this.name} resource in use`);
    throw new Error('An error occurred while using the resource');
  }
  
  public cleanup(): void {
    console.info(`${this.name} resource cleaned up`);
  }
}

function useResource(): void {
  let resource: DemoResource | null = null;
  
  try {
    resource = new DemoResource('Database connection');
    resource.use();
  } catch (error) {
    console.error('Error caught:', (error as Error).message);
  } finally {
    // Ensure the resource is cleaned up
    if (resource) {
      resource.cleanup();
    }
  }
}

useResource();
// Output:
// Database connection resource created
// Database connection resource in use
// Error caught: an error occurred while using the resource
// Database connection resource cleaned up
```

Besides resource cleanup, the `finally` block has another noteworthy property: even when `try` uses `return`, `finally` still runs before the function returns.

<!-- @[finally_with_return](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/ErrorHandling.ets) -->

``` TypeScript
function testFinally(): string {
  try {
    console.info('try block');
    return 'return from try';
  } catch (error) {
    console.info('catch block');
    return 'return from catch';
  } finally {
    console.info('finally block');
    // Do not use return in the finally block, as it overrides the return value of try/catch.
  }
}

let result: string = testFinally();
console.info(`Return value: ${result}`);
// Output:
// try block
// finally block
// Return value: return from try
```

### When to Use Nested try-catch

Nested `try-catch` blocks place a `try-catch` inside another `try-catch` to handle errors at different layers.

<!-- @[ts_nested_try_catch](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/ErrorHandling.ts) -->

``` TypeScript
function nestedErrorHandling(): void {
  try {
    console.info(`Outer try`);

    try {
      console.info(`Inner try`);
      throw new Error('Inner error');
    } catch (innerError) {
      console.info(`Inner catch: ${(innerError as Error).message}`);
      // Decide whether to throw the error to the upper layer.
      throw innerError as Error; // Propagate the error to the outer block.
    }

    console.info(`Outer try continues`); // Not executed: rethrowing in the inner catch transfers control directly to the outer catch.
  } catch (outerError) {
    console.info(`Outer catch: ${(outerError as Error).message}`);
  }
}

nestedErrorHandling();
// Output:
// Outer try
// Inner try
// Inner catch: Inner error
// Outer catch: Inner error
```

## Throwing Errors (throw Statement)

The `throw` statement throws an `Error` object, interrupts the current function, and transfers control to the nearest `try-catch` block in the call stack.

### Throwing Native Error Instances

Use `throw` to throw an `Error` object or a subclass instance, interrupting the current function and transferring control to the nearest `catch` block in the call stack. In ArkTS, throw objects in the `Error` hierarchy rather than non-`Error` values such as strings or numbers.

<!-- @[email_validation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/ErrorHandling.ets) -->

``` TypeScript
function validateEmail(email: string): void {
  let emailRegex: RegExp = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
  
  if (!email) {
    throw new Error('Email address cannot be empty');
  }
  
  if (!emailRegex.test(email)) {
    throw new Error(`Invalid email address: ${email}`);
  }
}

try {
  validateEmail('invalid-email');
} catch (error) {
  console.error(`Validation failed: ${(error as Error).message}`);
}
```

### Throwing Custom Error Instances

Extend `Error` to create a custom error class (such as `AppError`) with business-specific fields such as `code` and `field`, so that `catch` blocks can distinguish errors by business semantics.

<!-- @[custom_error_with_code](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/ErrorHandling.ets) -->

``` TypeScript
class AppError extends Error {
  public code: number;
  
  constructor(code: number, message: string) {
    super(message);
    this.name = 'AppError';
    this.code = code;
  }
}

function withdrawMoney(balance: number, amount: number): number {
  if (amount <= 0) {
    throw new AppError(1001, 'Withdrawal amount must be greater than zero');
  }
  
  if (amount > balance) {
    throw new AppError(1002, 'Insufficient balance');
  }
  
  return balance - amount;
}

try {
  let newBalance: number = withdrawMoney(100, 200);
  console.info(`Withdrawal successful, balance: ${newBalance}`);
} catch (error) {
  if (error instanceof AppError) {
    console.error(`Error code: ${error.code}, error message: ${error.message}`);
    // Execute different logic based on the error code.
    if (error.code === 1002) {
      console.info('Suggestion: Deposit money or apply for a loan first.');
    }
  }
}
```

### Restrictions on Throwing Non-Error Values

In ArkTS, a `throw` statement can throw only objects constructed from `Error` or its subtypes. Throwing non-`Error` values such as strings or numbers prevents callers from reliably reading error information and stack traces. Always throw `Error` instances.

## Documenting Errors with @throws

Use `@throws` in comments to document potential errors from methods or functions. This informs callers but does not require them to use `try-catch`.

<!-- @[function_throws_documentation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/ErrorHandling.ets) -->

``` TypeScript
/**
 * Division operation.
 * @param a Dividend.
 * @param b Divisor.
 * @returns Quotient.
 * @throws {Error} Throws an error when the divisor is zero.
 */
function documentationDivide(a: number, b: number): number {
  if (b === 0) {
    throw new Error('The divisor cannot be zero');
  }
  return a / b;
}

/**
 * Parse a JSON string.
 * @param jsonStr JSON string.
 * @returns Parsed object.
 * @throws {SyntaxError} Throws an error when the JSON format is invalid.
 */
function documentationParseJSON(jsonStr: string): Object {
  try {
    return JSON.parse(jsonStr) as Object;
  } catch (error) {
    throw new SyntaxError('Incorrect JSON string format');
  }
}
```

## Including Error Information in Function Return Values

Return data and errors using an explicit result object instead of throwing errors. This provides a structured way to return error information and data.

<!-- @[result_type_pattern](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/ErrorHandling.ets) -->

``` TypeScript
interface Result<T> {
  data: T | null;
  error: Error | null;
}

// Return data and errors from a function
function parseJSONSafe(jsonStr: string): Result<Object> {
  try {
    let data: Object = JSON.parse(jsonStr) as Object;
    return {
      data: data,
      error: null
    };
  } catch (error) {
    return {
      data: null,
      error: error as Error
    };
  }
}

let parseResult: Result<Object> = parseJSONSafe('{"name": "Alice"}');

if (parseResult.error !== null) {
    console.error('Parsing failed:', parseResult.error.message);
} else {
    console.info(`Parsing succeeded: ${parseResult.data}`);
}

// Another example.
function patternDivideNumbers(a: number, b: number): Result<number> {
  if (b === 0) {
    return {
      data: null,
      error: new Error('The divisor cannot be zero.')
    };
  }
  return {
    data: a / b,
    error: null
  };
}

let divideResult: Result<number> = patternDivideNumbers(10, 2);
if (divideResult.error !== null) {
    console.error('Calculation failed:', divideResult.error.message);
} else {
    console.info(`Calculation result: ${divideResult.data}`);
}
```

## Combining Optional Chaining and Nullish Coalescing to Handle Potential Errors

Use optional chaining `?.` to safely access nested properties that may be `null` or `undefined`, avoiding runtime errors. Use nullish coalescing `??` to provide a default when the chain result is nullish. Together, they handle missing data gracefully without `try-catch`.

<!-- @[optional_chaining_nullish_coalescing](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/ErrorHandling.ets) -->

``` TypeScript
interface ErrorHandlingUserProfile {
  avatar?: string;
  bio?: string;
}

interface ErrorHandlingUser {
  id: number;
  name: string;
  email?: string;
  profile?: ErrorHandlingUserProfile;
}

function getUserEmail(user: ErrorHandlingUser | null): string {
  // Use optional chaining and nullish coalescing.
  return user?.email ?? 'No email set';
}

function getAvatar(user: ErrorHandlingUser | null): string {
  return user?.profile?.avatar ?? 'default-avatar.png';
}

// Example
let errorUser1: ErrorHandlingUser = { id: 1, name: 'Alice' };
let errorUser2: ErrorHandlingUser = { id: 2, name: 'Bob', email: 'bob@example.com' };
let errorUser3: ErrorHandlingUser = {
  id: 3,
  name: 'Charlie',
  profile: { avatar: 'charlie.png', bio: 'Developer' }
};

console.info(`${getUserEmail(errorUser1)}`); // 'No email set'
console.info(`${getUserEmail(errorUser2)}`); // 'bob@example.com'
console.info(`${getAvatar(errorUser1)}`);    // 'default-avatar.png'
console.info(`${getAvatar(errorUser3)}`);    // 'charlie.png'
```

## Error Handling in Asynchronous Code

In an `async` function, wrap `await` expressions in `try-catch` to catch `Promise` rejections.

### Catching Async Errors with async/await and try-catch

Combining `async`/`await` with `try-catch` is the standard way to handle asynchronous errors and provides a clear handling flow.

<!-- @[promise_try_catch](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/ErrorHandling.ets) -->

``` TypeScript
async function asyncOperation(): Promise<string> {
  // Simulate an asynchronous operation
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      let success = Math.random() > 0.5;
      if (success) {
        resolve('Operation succeeded');
      } else {
        reject(new Error('Operation failed'));
      }
    }, 1000);
  });
}

// Use try-catch to catch asynchronous errors.
async function handleAsyncOperation(): Promise<void> {
  try {
    let result = await asyncOperation();
    console.info(`Result: ${result}`);
    } catch (error) {
    console.error('Caught asynchronous error:', (error as Error).message);
  }
}

handleAsyncOperation();
```

### Chained Error Catching with Promise.catch()

The `.catch()` method catches errors in a `Promise` chain, providing error handling for chained operations.

<!-- @[promise_catch_finally_chain](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/ErrorHandling.ets) -->

``` TypeScript
// Use Promise.catch() to catch errors.
function promiseErrorOperation(): Promise<string> {
  return Promise.resolve('success');
}

function promiseCatchExample(): void {
  promiseErrorOperation()
    .then((result: string): string => {
      console.info(`Success: ${result}`);
      return result.toUpperCase();
    })
    .then((upperResult: string): void => {
      console.info(`After conversion: ${upperResult}`);
    })
    .catch((error: Error): void => {
      console.error(`Caught error: ${error.message}`);
    })
    .finally((): void => {
      console.info('Operation ended');
    });
}

promiseCatchExample();
```

### Error Handling for Multiple Asynchronous Operations

If any task in `Promise.all` fails, the entire operation enters `catch`. Attach a separate `catch` to each task to handle errors independently.

<!-- @[promise_all_error_handling](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/PromiseAllErrorHandling.ets) -->

``` TypeScript
import { http } from '@kit.NetworkKit';

async function parallelErrorHandling(): Promise<void> {
  try {
    // Execute multiple asynchronous operations in parallel.
    let results = await Promise.all([
      http.createHttp().request('EXAMPLE_API_URL/users'),
      http.createHttp().request('EXAMPLE_API_URL/posts'),
      http.createHttp().request('EXAMPLE_API_URL/comments')
    ]);
    
    let usersRes = results[0];
    let postsRes = results[1];
    let commentsRes = results[2];
    console.info(`All requests succeeded: ${usersRes.responseCode}, ${postsRes.responseCode}, ${commentsRes.responseCode}`);
  } catch (error) {
    console.error(`At least one request failed: ${(error as Error).message}`);
  }
}

// Use Promise.allSettled to obtain all results (whether successful or failed).
async function allSettledExample(): Promise<void> {
  let results = await Promise.allSettled([
    Promise.resolve('Success 1'),
    Promise.reject(new Error('Failure 1')),
    Promise.resolve('Success 2')
  ]);
  
  results.forEach((result, index) => {
    if (result.status === 'fulfilled') {
      console.info(`The ${index + 1}th success: ${result.value}`);
    } else {
      console.error(`The ${index + 1}th failed:`, result.reason);
    }
  });
}

allSettledExample();
// Output:
// The 1st succeeded: Success 1
// The 2nd failed: Failure 1
// The 3rd succeeded: Success 2
```

Unlike parallel execution, in serial asynchronous operations each step depends on the result of the previous step, so error handling needs to record the completed steps for troubleshooting and recovery.

<!-- @[serial_async_error_handling](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/ErrorHandling.ets) -->

``` TypeScript
function serialAsyncOperation(stepName: string): Promise<string> {
  return Promise.resolve(`${stepName} completed`);
}

async function serialErrorHandling(): Promise<void> {
  let stepResults: string[] = [];
  
  try {
    // First step
    let step1: string = await serialAsyncOperation('First step');
    stepResults.push(step1);
    
    // Second step (depends on the first step)
    let step2: string = await serialAsyncOperation('Step 2');
    stepResults.push(step2);
    
    // Step 3 (depends on Step 2)
    let step3: string = await serialAsyncOperation('Step 3');
    stepResults.push(step3);
    
    console.info(`All steps succeeded: ${stepResults.join(', ')}`);
  } catch (error) {
    console.error(`Step execution failed: ${(error as Error).message}`);
    console.info(`Completed steps: ${stepResults.join(', ')}`);
  }
}

serialErrorHandling();
```

### Listening for Unhandled Promise Rejections in the Current Thread

Use the `unhandledRejection` event of [errorManager](../reference/apis-ability-kit/js-apis-app-ability-errorManager.md) to listen for unhandled `Promise` rejections in the current thread (supported since API version 12). This listener applies only to the current thread and cannot catch errors in other runtime instances such as `Worker` or `TaskPool`. Save the callback in an `observer` variable and call `off` to unregister it when no longer needed (for example, when the page is destroyed), avoiding duplicate registration or difficulty removing the exact listener.

<!-- @[unhandled_rejection_handler](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/UnhandledRejectionHandler.ts) -->

``` TypeScript
import { errorManager } from '@kit.AbilityKit';

// Save the callback as observer so it can be unregistered precisely later.
let observer: errorManager.UnhandledRejectionObserver = (reason: Error, promise: Promise<void>) => {
  console.error(`Unhandled promise rejection: ${reason.message}`);
};

// Register the listener (registration is supported only in the main thread).
errorManager.on('unhandledRejection', observer);

// Example: trigger an unhandled Promise rejection.
async function triggerUnhandledRejection(): Promise<void> {
  // This error is not handled by try-catch or .catch().
  await Promise.reject(new Error('Uncaught Promise error'));
}

triggerUnhandledRejection(); // This unhandled rejection triggers the listener registered above.

// Unregister the listener at an appropriate time (for example, when the page is destroyed):
errorManager.off('unhandledRejection', observer);
```

To listen for unhandled `Promise` rejections throughout the process (including instances such as `Worker` and `TaskPool`), use the `globalUnhandledRejectionDetected` event of `errorManager` (supported since API version 18). This event can be registered in any thread in the process to catch unhandled `Promise` rejections in the current process.

## Error Recovery and Fallback Strategies

After catching an error, return a default value or execute fallback logic to ensure that the caller obtains a valid result.

### Returning Default Values After Catching Errors

Return a default value in the `catch` block to ensure that the function always returns a valid value.

<!-- @[fallback_default_values](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/ErrorHandling.ets) -->

``` TypeScript
interface FallbackData {
  name: string;
}

function safeParseJSON(jsonStr: string, defaultValue: FallbackData | null = null): FallbackData | null {
  try {
    let parsed: Object = JSON.parse(jsonStr);
    return parsed as FallbackData;
  } catch (error) {
    console.info(`JSON parsing failed, using default value: ${(error as Error).message}`);
    return defaultValue;
  }
}

let fbData1: FallbackData | null = safeParseJSON('{"name": "Alice"}', { name: 'Unknown' });
console.info(`${JSON.stringify(fbData1)}`);  // '{"name":"Alice"}'

let fbData2: FallbackData | null = safeParseJSON('invalid json', { name: 'Unknown' });
console.info(`${JSON.stringify(fbData2)}`);  // '{"name":"Unknown"}'

function safeArrayAccess<T>(arr: T[], index: number, defaultValue: T): T {
  try {
    if (index >= 0 && index < arr.length) {
      return arr[index];
    }
    throw new Error('Index out of range');
  } catch (error) {
    console.info(`Array access failed, using default value: ${(error as Error).message}`);
    return defaultValue;
  }
}

let fbNumbers: number[] = [1, 2, 3];
console.info(`${safeArrayAccess(fbNumbers, 5, 0)}`); // 0 (index out of range)
```

### Implementing the Error Retry Mechanism

Encapsulate retry logic for asynchronous operations that may fail intermittently: execute the operation in a loop, and on failure wait for a fixed interval or use exponential backoff before retrying. If the maximum number of attempts is reached and the operation still fails, throw the accumulated error to improve the robustness of the call.

<!-- @[retry_with_backoff](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/ErrorHandling.ets) -->

``` TypeScript
interface RetryExampleOptions {
  maxRetries: number;      // Maximum number of retries.
  delay: number;           // Retry interval (in milliseconds).
  backoff?: boolean;       // Whether to use exponential backoff.
}

async function retryExampleAsyncOperation<T>(
  operation: () => Promise<T>,
  options: RetryExampleOptions
): Promise<T> {
  let lastError: Error | null = null;
  
  for (let attempt = 0; attempt <= options.maxRetries; attempt++) {
    try {
      let result = await operation();
      console.info(`Operation succeeded (attempt ${attempt + 1})`);
      return result;
    } catch (error) {
      lastError = error as Error;
      console.info(`Attempt ${attempt + 1} failed: ${lastError.message}`);
      
      if (attempt < options.maxRetries) {
        // Calculate the wait time.
        let waitTime = options.delay;
        if (options.backoff) {
          waitTime = options.delay * Math.pow(2, attempt);
        }
        
        console.info(`Waiting ${waitTime}ms before retrying...`);
        await new Promise<void>((resolve: () => void) => setTimeout(resolve, waitTime));
      }
    }
  }
  
  throw new Error(`Retry failed after ${options.maxRetries} attempts: ${lastError ? lastError.message : 'unknown error'}`);
}

// Usage example.
let retryAttemptCount: number = 0;

async function retryExampleUnstableOperation(): Promise<string> {
  retryAttemptCount++;
  if (retryAttemptCount < 2) {
    throw new Error('Operation failed');
  }
  return 'Operation succeeded';
}

async function testRetry(): Promise<void> {
  try {
    let result: string = await retryExampleAsyncOperation<string>(
      retryExampleUnstableOperation,
      { maxRetries: 3, delay: 10, backoff: true }
    );
    console.info(`Final result: ${result}`);
  } catch (error) {
    console.error(`All retries failed: ${(error as Error).message}`);
  }
}

testRetry();
```

### Degradation Handling

When an error occurs, execute fallback logic to keep the system's basic functions running.

<!-- @[service_fallback_pattern](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/ErrorHandling.ets) -->

``` TypeScript
interface FallbackDataService {
  getData(): Promise<string>;
}

class PrimaryDataService implements FallbackDataService {
  async getData(): Promise<string> {
        // Simulate a possible failure of the primary service.
    throw new Error('Primary service unavailable');
  }
}

class SecondaryDataService implements FallbackDataService {
  async getData(): Promise<string> {
    return 'Backup service data';
  }
}

class ResilientDataFetcher {
  private primaryService: FallbackDataService;
  private fallbackService: FallbackDataService;
  
  constructor() {
    this.primaryService = new PrimaryDataService();
    this.fallbackService = new SecondaryDataService();
  }
  
  async fetchData(): Promise<string> {
    try {
      // Try to use the primary service.
      return await this.primaryService.getData();
    } catch (error) {
      console.info(`Primary service failed, switching to fallback service: ${(error as Error).message}`);
      
      try {
        // Use the fallback service.
        return await this.fallbackService.getData();
      } catch (fallbackError) {
        console.error(`Fallback service also failed: ${(fallbackError as Error).message}`);
        // Return the default data.
        return 'Default data';
      }
    }
  }
}

// Usage example.
async function runDataFetcherExample(): Promise<void> {
  let fetcher: ResilientDataFetcher = new ResilientDataFetcher();
  let data = await fetcher.fetchData();
  console.info(`Data obtained: ${data}`);
}

runDataFetcherExample();
```

### Comprehensive Example: Complete Error Handling Flow

Combine retry, timeout, fallback, and logging to build a complete error handling flow for API calls.

<!-- @[api_client_with_retry](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/ErrorHandling.ets) -->

``` TypeScript
interface RetryConfig {
  maxRetries: number;
  timeout: number;
}

class ApiClient {
  private baseUrl: string;
  private maxRetries: number;
  private timeout: number;

  constructor(baseUrl: string, config?: RetryConfig) {
    this.baseUrl = baseUrl;
    this.maxRetries = config?.maxRetries ?? 3;
    this.timeout = config?.timeout ?? 5000;
  }

  async get(endpoint: string): Promise<string> {
    let url: string = `${this.baseUrl}${endpoint}`;
    let lastError: Error | null = null;

    for (let attempt = 0; attempt <= this.maxRetries; attempt++) {
      try {
        let result: string = await this.mockRequest(url);
        return result;
      } catch (error) {
        lastError = error as Error;

        if (attempt < this.maxRetries) {
          console.info(`Request failed, retry ${attempt + 1}...`);
          await this.delay(1000 * (attempt + 1));
        }
      }
    }

    throw new Error(`Request failed: ${lastError?.message}`);
  }

  private delay(ms: number): Promise<void> {
    return new Promise<void>((resolve: () => void): void => {
      setTimeout(() => resolve(), ms);
    });
  }

  private mockRequest(url: string): Promise<string> {
    return new Promise<string>((resolve: (value: string) => void, reject: (reason: Error) => void): void => {
      setTimeout(() => {
        if (url.includes('error')) {
          reject(new Error('Network error'));
        } else {
          resolve(`Data from ${url}`);
        }
      }, 100);
    });
  }
}

async function retryFetchUserInfo(): Promise<void> {
  let client: ApiClient = new ApiClient('EXAMPLE_API_URL', { maxRetries: 2, timeout: 3000 });

  try {
    let user: string = await client.get('/users/1');
    console.info(`User information: ${user}`);
  } catch (error) {
    console.error(`Failed to obtain user information: ${(error as Error).message}`);
    console.info('Using default user information');
  }
}

retryFetchUserInfo();
```
