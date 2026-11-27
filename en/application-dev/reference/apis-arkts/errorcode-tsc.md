# TSC Error Code Introduction
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @jokerxd-liu-->
<!--Designer: @huyunhui1; @liyancheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=c8d611da517c0df9bbfb2e4952764bf8397e713e translatedAt=2026-11-16T05:14:22.539Z pushedAt=2026-11-16T06:31:14.174Z nl=1 -->

TSC (TypeScript Compiler) error codes start with `105` and are error prompts in the TSC compilation process. The error code and its corresponding error description are displayed in the editor, console, or log files.

## 10505001 TSC Native Errors

TSC Native errors: ending with `001`, these are the existing native error rules in TSC checking. In the TSC compilation process, common causes of TSC native errors include: missing keywords or symbols, multiple default exports, assignment type and receiving type mismatch, and missing interface declarations in js files. These issues are usually caused by code that does not follow the [ArkTS Language Specification](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/introduction-to-arkts). Developers can modify the code based on the error description.

### Missing Keywords or Symbols

**Error Example Scenario**

```typescript
declare type Color = 'red;
```

**Error Message**

Unterminated string literal.

**Description**

The string literal is not correctly terminated at the expected position.

**Possible Causes**

The string literal is not properly terminated at the expected position. Common causes include: a missing closing quote (single or double quote); mismatched quote types, for example starting with a single quote but ending with a double quote; and a quote character in the string that is the same as the delimiter but is not escaped.

**Solution**

To fix the unterminated string literal error, add the missing closing quote in the code block. The code after modification is as follows:

```typescript
declare type Color = 'red';
```

### Multiple Default Exports

**Error Example Scenario**

```typescript
let config = { key: 'value' };
let logger = { log: () => {} };
export default config;
export default logger;
```

**Error Message**

A module cannot have multiple default exports.

**Description**

A module cannot have multiple default exports.

**Possible Causes**

Multiple default exports are defined in the module.

**Solution**

To fix the error of multiple default exports in a module, delete the redundant default export. The code after modification is as follows:

```typescript
export default config;
```

### Type Mismatch in Assignments

**Error Example Scenario**

```typescript
let count: number = 1;
let amount: string = '2';
count = amount;
```

**Error Message**

Type 'string' is not assignable to type 'number'.

**Description**

Type 'string' cannot be assigned to type 'number'.

**Possible Causes**

Assigning a value of one type to a variable of a different type results in a type mismatch error.

**Solution**

To fix the type mismatch error, ensure that the assignment type and the receiving type are consistent. For example, change the type of the variable `amount` from `string` to `number`. The code after modification is as follows:

```typescript
let count: number = 1;
let amount: number = 2;
count = amount;
```

### Missing Interface Declaration in js Files

**Error Example Scenario**

A JS file in the har1 package defines an exportable API:
```javascript
// har1 src/main/ets/FileJs.js
export let fileJs = 1;
```
The har2 package references this API from the har1 package as follows:
```typescript
import { fileJs } from 'har1/src/main/ets/FileJs';
```

**Error Message**

Cannot find module ${moduleName} or its corresponding type declarations.

**Description**

The module or its corresponding type declaration file cannot be found, so the module cannot be imported normally.

**Possible Causes**

The [bytecode HAR](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-hvigor-build-har#section16598338112415) contains js files, and TSC does not generate the corresponding .d.ts declaration files for js files during compilation. Therefore, external modules that depend on this module cannot resolve its type declarations, which triggers an import failure.

**Solution**

If a js file in a HAR package needs to provide external export functionality, the developer must:

1. Manually write the corresponding .d.ts declaration file in the same directory as the js file, and compile and publish it together with the HAR package. Example:
    ```typescript
    // har1's src/main/ets/FileJs.d.ts
    export declare let fileJs: number;
    ```
2. Add an export statement to the Index.ets file at the top level of the har1 package. Example:
    ```typescript
    export { fileJs } from './src/main/ets/FileJs';
    ```
3. Reference this interface from the har1 package in the har2 package. Example:
    ```typescript
    import { fileJs } from 'har1/src/main/ets/FileJs';
    ```