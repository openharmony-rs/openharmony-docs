# Lazy Import
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @shilei123-->
<!--Designer: @shilei123-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=a3a2ca5bc4d88586dfb836a22fbed6fefbb6524f translatedAt=2026-11-04T09:05:05.976Z pushedAt=2026-11-04T09:32:25.735Z nl=1 -->

As applications evolve with more features, the time required for cold start increases significantly. The main reason is that numerous modules that are not actually executed are loaded during the initial startup. This not only prolongs application initialization but also leads to invalid resource utilization. To address this, it is crucial to streamline the loading process by eliminating non-essential file executions to optimize cold start performance and ensure a smooth user experience.

> **NOTE**
>
> - The lazy import feature is supported from API version 12.
>
> - To use the lazy import syntax on API 12, developers must configure `"compatibleSdkVersionStage": "beta3"` in the project; otherwise, compilation will fail. For details, see the DevEco Studio [build-profile.json5](https://developer.huawei.com/consumer/en/doc/harmonyos-guides-V5/ide-hvigor-build-profile-V5#section511142752919) configuration.
> - For projects with an API version later than 12, developers can directly use the lazy import syntax without any additional configuration.

## Features

The lazy import feature prevents files from being loaded during the cold start phase. Instead, they are loaded on demand as the program runs, which helps to reduce cold start time.

## Usage

Developers can refer to [Basic Operations of the Launch Template](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-insight-session-launch), [Detecting Files Eligible for Lazy Import](#detecting-files-eligible-for-lazy-import), <!--Del-->[<!--DelEnd-->Common Trace Usage Guide<!--Del-->](../performance/common-trace-using-instructions.md)<!--DelEnd-->, and use tools or logging to identify files that are not actually called during cold start<!--RP1-->. For the analysis method, see [Detecting Files Eligible for Lazy Import](#detecting-files-eligible-for-lazy-import)<!--RP1End-->. By analyzing this data, developers can accurately identify the list of files that do not need to be preloaded during the startup phase, and add the lazy flag at the call sites of these files. However, note that the subsequent loading is synchronous loading, which may block task execution (for example, if a click task triggers lazy loading, the runtime will execute the files that were not loaded during cold start, increasing time consumption). Therefore, developers need to evaluate whether to use lazy loading on their own.

> **NOTE**
>
> You are not advised to blindly add **lazy** flags, as this can also increase the overhead of identification during compilation and runtime.

## Scenario Behavior Analysis

- Use lazy-import for deferred loading.

```typescript
// main.ets
import lazy { a } from "./mod1";    // "mod1" is not executed.
import { c } from "./mod2";         // "mod2" is executed.

// ...

console.info("main executed");
function useModules(): void{
    let xx = a;
    let yy = c;
}
```

```typescript
// mod1.ets
export let a = "mod1 executed"
console.info(a);
```

```typescript
// mod2.ets
export let c = "mod2 executed"
console.info(c);

```

The execution result is as follows:

```typescript
mod2 executed
main executed
```

- Use both lazy-import and import for the same module.

<!-- @[import_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/LazyImport/entry/src/main/ets/pages/main.ets) -->

``` TypeScript
import lazy { a } from './mod1'; // 'mod1' is not executed
import { c } from './mod2'; // 'mod2' is executed
import { b } from './mod1'; // 'mod1' is executed
```

<!-- @[main_running_info](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/LazyImport/entry/src/main/ets/pages/main.ets) -->

``` TypeScript
console.info('main executed');
function useModules(): void{
  let xx = a;
  let yy = c;
  let zz = b;
}
```
<!-- @[export_module_variable_01](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/LazyImport/entry/src/main/ets/pages/mod1.ets) -->

``` TypeScript
export let a = 'mod1 a executed';
console.info(a);
export let b = 'mod1 b executed';
console.info(b);
```

<!-- @[export_module_variable_02](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/LazyImport/entry/src/main/ets/pages/mod2.ets) -->

``` TypeScript
export let c = 'mod2 c executed';
console.info(c);
```

The execution result is as follows:

```typescript
mod2 c executed
mod1 a executed
mod1 b executed
main executed
```

If the keyword **lazy** is deleted from the **main.ets** file, the execution sequence is as follows:

```typescript
mod1 a executed
mod1 b executed
mod2 c executed
main executed
```

## Differences Between Lazy Import And Dynamic Loading

Both lazy import and [dynamic loading](./arkts-dynamic-import.md) can delay the execution of specific files to balance performance consumption and relieve performance pressure in specific periods.

| Difference      | Dynamic Loading                                        | Lazy Import                                                |
|-----------|----------------------------------------------|-------------------------------------------------------------|
| Syntax example     | let A = await import("./A");                 | import lazy { A } from "./A";                               |
| Performance overhead     | 1. Creates asynchronous task overhead.<br>2. Triggers the module parsing and source code execution of the dependent module when dynamic import is executed.| 1. Module parsing of lazy import still triggers traversal during cold start.<br>2. Executes the source code of the module when the imported variable A is used.|
| Usage position     | Used within code blocks/runtime logic                                 | Written at the beginning of the source code.                                                   |
| Runtime concatenation| Supported                                           | Not supported                                                          |
| Loading sequence     | Asynchronous                                          | Synchronous                                                         |

Advantages of lazy import over dynamic loading:

1. When using dynamic imports, you need to rewrite the static loading code (synchronous import) into the dynamic import syntax (asynchronous import), which may require extensive code modifications.
2. When aiming to optimize cold startup through dynamic loading, you need to explicitly ensure that dynamically loaded files will not execute during cold startup. Otherwise, it will increase cold startup overhead (such as being added to asynchronous queues).
3. Compared with dynamic import, lazy import can be implemented only by adding **lazy** keywords to the import syntax.

## Syntax Specifications and Supported Versions

- The lazy import feature supports the following syntax:

| Syntax                                           | ModuleRequest  | ImportName | LocalName   | Supported API Version|
|:----------------------------------------------|:---------------|:-----------|:------------|:-----------|
| import lazy { x } from "mod";                 | "mod"          | "x"        | "x"         | API 12      |
| import lazy { x as v } from "mod";            | "mod"          | "x"        | "v"         | API 12      |
| import lazy x from "mod";                     | "mod"          | "default"  | "x"         | API 12      |
| import lazy { KitClass } from "@kit.SomeKit"; | "@kit.SomeKit" | "KitClass" | "KitClass"  | API 12      |

- Lazy importing of shared modules or modules within a dependency path that includes shared modules

    Lazy loading still takes effect for shared modules. For usage restrictions, see the [Shared Module](../arkts-utils/arkts-sendable-module.md) development guide.

### Incorrect Example

The following syntax will cause compilation errors:

```typescript
export lazy var v;                    // The compiler reports an application compilation error.
export lazy default function f(){};   // The compiler reports an application compilation error.
export lazy default function(){};     // The compiler reports an application compilation error.
export lazy default 42;               // The compiler reports an application compilation error.
export lazy { x };                    // The compiler reports an application compilation error.
export lazy { x as v };               // The compiler reports an application compilation error.
export lazy { x } from "mod";         // The compiler reports an application compilation error.
export lazy { x as v } from "mod";    // The compiler reports an application compilation error.
export lazy * from "mod";             // The compiler reports an application compilation error.

import lazy * as ns from "mod";            // The compiler reports an application compilation error.
import lazy KitClass from "@kit.SomeKit"   // The compiler reports an application compilation error.
import lazy * as MyKit from "@kit.SomeKit" // The compiler reports an application compilation error.
```

If the **type** keyword is added to the syntax, a compilation error is reported.

```typescript
import lazy type { obj } from "./mod";    // Not supported. The compiler reports an application compilation error.
import type lazy { obj } from "./mod";    // Not supported. The compiler reports an application compilation error.
```

### Syntax Not Recommended

- In the same .ets file, the expected lazy-imported dependency modules are not fully marked.

Incomplete marking will cause lazy import to fail and increase the overhead of identifying lazy-imported modules.

```typescript
// mod1.ets
export let a = "Variable A from mod1";
export let b = "Variable B from mod1";
console.info("mod1 executed");
```

```typescript
// mod2.ets
export let c = "Variable C from mod2";
console.info("mod2 executed");
```

```typescript
// main.ets
import lazy { a } from "./mod1";    // Obtain the object a from "mod1" and add the lazy flag.
import { c } from "./mod2";
import { b } from "./mod1";         // Obtain the attributes in "mod1". This syntax is not added with the lazy flag, so "mod1" is executed by default.

// ...
```

- In the same .ets file, re-exporting unused lazy-imported variables is not supported. To identify and resolve such issues, you can enable the **reExportCheckMode** switch in the project-level **build-profile.json5** file to perform a scan and check.

<!-- @[lazy_import_build](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/LazyImport/build-profile.json5) -->

``` JSON5
"buildOption": {
  "arkOptions": {
    "reExportCheckMode": "compatible"
  },
  // ...
}
```
> **NOTE**
>
> - For the following scenario, whether to intercept and report errors during compilation: Variables imported using lazy import are re-exported within the same file.
> - **noCheck** (default value): No check is performed, and no error is reported.
> - **compatible**: A warning is reported.
> - **strict**: An error is reported.
> - This field is supported since DevEco Studio 5.0.13.200.

The variable **c** is not used in **B.ets**, so **C.ets** does not trigger execution. When **c** is used in **A.ets**, it is not initialized, resulting in a JavaScript exception.

<!-- @[import_variable_c](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/LazyImport/entry/src/main/ets/pages/A.ets) -->

``` TypeScript
// A.ets
import { c } from './B';
console.info(c);
```

<!-- @[import_export_variable_c](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/LazyImport/entry/src/main/ets/pages/B.ets) -->

``` TypeScript
// B.ets
import lazy { c } from './C'; // Obtain the c object from 'C' and mark it as lazy loading
export { c };
```

<!-- @[export_variable_c](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/LazyImport/entry/src/main/ets/pages/C.ets) -->

``` TypeScript
// C.ets
let c = 'c';
export { c };
```

Result:

```typescript
ReferenceError: c is not initialized
    at func_main_0 (A.ets:2:13)
```

<!-- @[a_ns](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/LazyImport/entry/src/main/ets/pages/A_ns.ets) -->

``` TypeScript
// A_ns.ets
import * as ns from './B';
console.info(ns.c);
```

<!-- @[import_export_variable_c](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/LazyImport/entry/src/main/ets/pages/B.ets) -->

``` TypeScript
// B.ets
import lazy { c } from './C'; // Obtain the c object from 'C' and mark it as lazy loading
export { c };
```

<!-- @[export_variable_c](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/LazyImport/entry/src/main/ets/pages/C.ets) -->

``` TypeScript
// C.ets
let c = 'c';
export { c };
```

Result:

```typescript
ReferenceError: module environment is undefined
    at func_main_0 (A_ns.js:2:13)
```

### Precautions

- Side effects that are independent of the module's execution (such as initializing global variables and mounting **globalThis**). For details, see [Side Effects and Optimization of Module Loading](./arkts-module-side-effects.md).
- When using an exported object, the time consumption of triggering lazy loading may degrade the corresponding feature. Since the subsequent loading of lazy import is synchronous loading, it may block task execution in certain scenarios (for example, if lazy loading is triggered when a service is clicked, the runtime will execute the files that were not loaded during cold start, increasing execution time consumption and posing a risk of frame drops). Whether to use lazy loading still needs to be evaluated by developers.
- Using the lazy import feature may cause the module not to be executed, thereby triggering bugs.
- When lazy import is used for files that have been dynamically loaded, the lazy flag is executed for these files and the files are synchronously loaded in the **then** logic of dynamic import.

## Detecting Files Eligible for Lazy Import

This tool is used for local detection of file loading during application cold start. It can print the names of files that are used and unused within a fixed time period after the application starts, helping you identify files eligible for lazy import.

> **NOTE**
>
> This feature is supported starting from API version 20.

### Detection Procedure

1. Open the tool: Obtain the [hdc](../dfx/hdc.md) tool, connect the device, and directly enter the following command in the terminal to execute it.

    ```shell
    hdc shell param set persist.ark.properties 0x200105c
    ```

2. (Optional) Set the time for capturing the application startup phase, in milliseconds. The value ranges from 100 to 30000. The default value is 2s. Timing accuracy cannot be ensured for values outside this range.

    ```shell
    hdc shell param set persist.ark.importDuration 1000
    ```

3. After clearing the application background process, restart the application process and wait for the capture time to end. The files corresponding to the main thread and sub-thread will be generated in the application sandbox (data/app/el2/100/base/${bundleName}/files/).

    > **NOTE**
    >
    > 1. This tool supports only applications installed locally.
    > 2. File generation requires the current process to remain active.
    > 3. No files will be generated if the process exits during capture.

4. Close the tool.

   Keeping this tool enabled for a long time degrades performance. Close it promptly after use.

    ```shell
    hdc shell param set persist.ark.properties 0x000105c
    ```

### Generated Files

Based on the configured capture time, the tool records the file loading status of the main thread and sub-thread within that time period. Each thread is timed independently.

For example, if the time is set to 1 second, the tool records the file execution status of the main thread and sub-thread within 1 second after each thread starts.

Generated file path: `data/app/el2/100/base/${bundleName}/files`

Main thread file name: `${bundleName}_redundant_file.txt`

Child thread file name: `${bundleName}_${tId}_redundant_file.txt`

> **NOTE**
>
> 1. The main thread file name does not contain the thread ID. Therefore, file overwriting may occur.
>
> 2. The child thread file name contains the thread ID (**tId**), and each **tId** is unique. Ensure that each child thread corresponds to an independent file. To find the corresponding thread file, you can match the thread ID in the log or use the trace tool to view the thread ID.

**Example**

The bundleName of the current test application is com.example.myapplication. A sub-thread is created in the application, and the thread ID is 18089 (random).

File generation path: data/app/el2/100/base/com.example.myapplication/files

Main thread file name: data/app/el2/100/base/com.example.myapplication/files/com.example.myapplication_redundant_file.txt

Sub-thread file name: data/app/el2/100/base/com.example.myapplication/files/com.example.myapplication_18089_redundant_file.txt

![deferrable-tool-file](figures/deferrable-tool-file.png)

### Detection Principles

As shown in the following example, if both file A and file B are dependencies of the **Index** file, they will be loaded and executed directly when the **Index** file is loaded.

During execution, file A completes variable definition, assignment, and export. This accounts for the time it takes to process file A. File B defines and exports a function, which corresponds to its processing time.

When the **Index** file runs, the exported function **func** from file B executes at the top level. As a result, file B's exports cannot be optimized and will be marked as **used** in the tool. However, the exported variable **a** from file A is only used when the **myFunc** function in the **Index** file is called. If no other files call **myFunc** during cold start, file A will be marked as **unused** in the tool, meaning it is eligible for lazy import.

<!-- @[testing_principle01](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/LazyImport/entry/src/main/ets/pages/index.ets) -->

``` TypeScript
import { a } from './A';
import { func } from './B';
func(); // Use the variable in file B.
export function myFunc() {
  return a; // The variable a is not used.
}
```

<!-- @[export_variable_a](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/LazyImport/entry/src/main/ets/pages/A.ets) -->

``` TypeScript
// A.ets
export let a = 10;
```

<!-- @[export_func](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/LazyImport/entry/src/main/ets/pages/B.ets) -->

``` TypeScript
// B.ets
export function func() {
  return 20;
}
```

### Loading Summary

The following summarizes all files loaded and their loading durations, including both used and unused files and their respective durations.

Example:

```text
<----Summary----> Total file number: 13, total time: 2ms, including used file:12, cost time: 1ms, and unused file: 1, cost time: 1ms
```

The above information indicates that the current thread of the application loaded 13 files during the cold start capture period, with a total time consumption of 2ms. Among them, the exported content of 12 files was loaded and used by other files, and executing these 12 files took 1ms in total; 1 file finished execution, but its exported content was not used by other files during the cold start phase, taking 1ms.

### Used Files

During the cold start phase, a file whose exported content is used by other files is called a used file.

- Scenario 1: For files loaded via static import, the parent file (**parentModule**) represents the importer of the file.

    ```text
    used file 1: &entry/src/main/ets/pages/1&, cost time: 0.248ms
        parentModule 1: &entry/src/main/ets/pages/outer1& a
    ```

    Example:

    <!-- @[scenario_1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/LazyImport/entry/src/main/ets/pages/outer1.ets) -->
    
    ``` TypeScript
    // entry/src/main/ets/pages/outer1.ets
    import { a } from './1' // outer1 file loads variable a from file 1
    console.info('example ', a); // variable a is used when the outer1 file is executed
    ```

    ```ts
    // entry/src/main/ets/pages/1.ets
    export let a = "a";
    ```

- Scenario 2: For files loaded through static loading, there are multiple parent files.

    ```text
    // Note: The display sequence does not indicate the loading sequence of the parent file.
    used file 1: &entry/src/main/ets/pages/1&, cost time: 0.248ms
       parentModule 1: &entry/src/main/ets/pages/outer1& a
       parentModule 2: &entry/src/main/ets/pages/innerinner& a
    ```

    Example:

    <!-- @[scenario_1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/LazyImport/entry/src/main/ets/pages/outer1.ets) -->
    
    ``` TypeScript
    // entry/src/main/ets/pages/outer1.ets
    import { a } from './1' // outer1 file loads variable a from file 1
    console.info('example ', a); // variable a is used when the outer1 file is executed
    ```

    <!-- @[scenario_2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/LazyImport/entry/src/main/ets/pages/innerinner.ets) -->
    
    ``` TypeScript
    import { a } from './1' // innerinner file loads variable a from file 1
    console.info('example ', a); // variable a is used when the innerinner file is executed
    ```

    ```ts
    // entry/src/main/ets/pages/1.ets
    export let a = "a";
    ```

- Scenario 3: Files loaded via static import have multiple exports, but only some of them are displayed.

    ```text
    used file 1: &entry/src/main/ets/pages/1&, cost time: 0.248ms
       parentModule 1: &entry/src/main/ets/pages/outer2& a
    ```

    Example:

    <!-- @[scenario_3](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/LazyImport/entry/src/main/ets/pages/outer2.ets) -->
    
    ``` TypeScript
    import { a , b } from './1' // Load multiple variables from file 1.
    console.info('example', a); // a is used
    export function myFunc() {
      return b; // b is not used
    }
    ```

    <!-- @[export_variable_001](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/LazyImport/entry/src/main/ets/pages/1.ets) -->
    
    ``` TypeScript
    export let a = 10;
    export let b = 100;
    ```

- Scenario 4: For files loaded via dynamic imports or NAPIs, parent file printing is not currently supported, so no parent modules will be displayed.

    ```text
    unused file 1: &entry/src/main/ets/pages/1&, cost time: 0.07ms
    ```

    Example:

    <!-- @[scenario_4](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/LazyImport/entry/src/main/ets/pages/outer3.ets) -->
    
    ``` TypeScript
    import('./1').then((ns:ESObject) => {
      console.info('import file 1 success');
    }).catch((e: Error) => {
      console.error('import file 1 failed: ' + e.message);
    });
    ```

    ```ts
    // entry/src/main/ets/pages/1.ets
    export let a = "a";
    ```

- Scenario 5: For files loaded via APIs such as **loadContent** and **pushUrl**, the parent file (**parentModule**) is displayed as **EntryPoint**.

    ```text
    used file 1: &entry/src/main/ets/pages/Index&, cost time: 0.545ms
    parentModule 1: EntryPoint
    ```

### Unused Files

During cold start, files whose exports are not used by other files are considered unused files and are eligible for lazy import.

The scenario is the same as that of used files, but unused files contain no information about variable usage.

- Scenario: When a file is referenced by parent files but its variables remain unused, you can load the unused file using lazy import in the parent file.

    ```text
    unused file 1: &entry/src/main/ets/pages/under1&, cost time: 0.001ms
        parentModule 1: &entry/src/main/ets/pages/1&
    ```

    Example:

    <!-- @[unused_file_no_lazy](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/LazyImport/entry/src/main/ets/pages/2.ets) -->
    
    ``` TypeScript
    import { a } from './under1' // Load the variable from the under1 file
    export function myFunc() {
      return a; // a is not used
    }
    ```

    ```ts
    // entry/src/main/ets/pages/under1.ets
    export let a = "a";
    ```

    Use lazy import:

    <!-- @[unused_file_with_lazy](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/LazyImport/entry/src/main/ets/pages/3.ets) -->
    
    ``` TypeScript
    import lazy { a } from './under1' // The under1 file is not loaded here.
    export function myFunc() {
      return a; // Trigger the loading of the under1 file at this point.
    }
    ```

### Usage Examples

**Scenario**

In the following example, file A is referenced but is not actually executed from application launch until the button is clicked. Loading file A during cold start is therefore unnecessary.

```javascript
// A.ets
export let A = "A";
```

```javascript
// Index.ets
import { A } from "./A";

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Button('Click to execute file A')
        .onClick(() => {
          // Trigger the execution of file A after clicking
          console.info("Execute file A", A);
        })
    }
    // ...
  }
}
```

![img](./figures/Lazy-Import-Instructions-1.png)

By capturing the trace and viewing the call stack, you can find that the application loads file A during cold start.

**Analysis**

1. Connect to the device and run the following command:

    ```shell
    hdc shell param set persist.ark.properties 0x200105c
    ```

2. Start the application and close it after the startup is complete.
3. Download the file to the local host. `${bundleName}` indicates the application name.

    ```shell
    hdc file recv data/app/el2/100/base/${bundleName}/files/${bundleName}_redundant_file.txt D:\
    ```

4. Analyze the file obtained.

   ![img](./figures/Lazy-Import-Instructions-2.png)

**Modification**

After redundant files are filtered out, you can add the `lazy` keyword to mark the files for lazy import.

```javascript
// A.ets
export let A = "A";
```

```javascript
// Index.ets
import lazy { A } from "./A"; // Add the lazy keyword here to mark this file as lazily loadable

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Button('Click to execute file A')
        .onClick(() => {
          // Click to execute file A.
          console.info("Execute file A", A);
        })
    }
    // ...
  }
}
```

![img](./figures/Lazy-Import-Instructions-3.png)

By capturing the trace and viewing the call stack, you can find that the application does not load file A during cold start.

**Optimization Effect**

| Phase| File Loading Duration (μs)|
|---------| --------------------- |
| Before optimization | 412μs              |
| After optimization | 350μs              |

From the comparison, with lazy import in place, file A no longer loads during the application's cold start. This reduces the time spent loading redundant files in the resource loading phase by around 15%, boosting cold start performance. (This example is purely for demonstration, and the optimization data should be treated as reference only. In real-world scenarios, as referenced files increase in both complexity and number, the optimization effect will improve accordingly.)
