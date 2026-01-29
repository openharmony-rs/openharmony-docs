# TypeScript Compiler Error Codes
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @zju-wyx-->
<!--Designer: @xiao-peiyang; @liyancheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @foryourself-->

Error codes of TypeScript Compiler (TSC) start with '105' and serve as error indicators during the TSC compilation process. These error codes and their corresponding descriptions are shown in the editor, console, or log files.

## 10505001 TSC Native Errors

TSC native errors, ending with '001', represent existing native error rules checked by TSC. Common causes of TSC native errors during compilation include: missing keywords or symbols, type mismatches in assignments, and undefined types or variables. These issues typically arise from not adhering to [language specifications](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/introduction-to-arkts) when writing code. Developers can adjust the code based on the error descriptions.

### Missing Keywords or Symbols

**Error Example Scenario**

```typescript
declare type AAA = 'BBB;
```

**Error Message**

Unterminated string literal.

**Description**

The string literal is not correctly terminated at the expected position.

**Possible Causes**

The closing quote is missing.

**Solution**

Based on the error description, add the missing quotes to the code block. The updated code is as follows:

```typescript
declare type AAA = 'BBB';
```

### Multiple Default Exports

**Error Example Scenario**

```typescript
export default A;
export default B;
```

**Error Message**

A module cannot have multiple default exports.

**Description**

A module cannot have multiple default exports.

**Possible Causes**

Multiple default exports are defined in the module.

**Solution**

Based on the error description, delete unnecessary default exports. The updated code is as follows:

```typescript
export default A;
```

### Type Mismatch in Assignments

**Error Example Scenario**

```typescript
let a: number = 1;
let b: string = '2';
a = b;
```

**Error Message**

Type 'string' is not assignable to type 'number'.

**Description**

Type 'string' cannot be assigned to type 'number'.

**Possible Causes**

Assigning a value of one type to a variable of a different type results in a type mismatch error.

**Solution**

Based on the error description, ensure type consistency by making appropriate type assignment changes. The updated code is as follows:

```typescript
let a: number = 1;
let b: number = 2;
a = b;
```

### API Export Exception in JS Files

**Error Example Scenario**

A JS file in the har1 package defines an exportable API:
```
// har1's src/main/ets/FileJs.js
export let fileJs = 1;
```
The har2 package references this API from the har1 package as follows:
```
import { fileJs } from 'har1/src/main/ets/FileJs';
```

**Error Message**

Cannot find module XXX or its corresponding type declarations.

**Description**

When a bytecode HAR file contains a JS file, no declaration file will be generated during compilation, preventing other modules from importing it.

**Possible Causes**

When the JS file is compiled, TSC does not generate a corresponding declaration file, which blocks imports from other modules.

**Solution**

If a JS file in a HAR package needs to expose exports, follow these steps:

1. Manually create a corresponding .d.ts declaration file in the same directory as the JS file, and compile and release it alongside the HAR package. Example:
```
// har1's src/main/ets/FileJs.d.ts
export declare let fileJs: number;
```
2. Add an export statement to the **Index.ets** file at the root of the har1 package. Example:
```
export { fileJs } from './src/main/ets/FileJs';
```
3. The har2 package can then import the API from har1 as follows:
```
import { fileJs } from 'har1/src/main/ets/FileJs';
```
