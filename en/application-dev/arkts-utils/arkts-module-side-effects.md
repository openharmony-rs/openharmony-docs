# Side Effects and Optimization of Module Loading
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @shilei123; @li-jiangfeng-->
<!--Designer: @shilei123-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=0677bfb1182307c7f6d27cfd4a79ebec0620eeb5 translatedAt=2026-11-04T09:06:04.650Z pushedAt=2026-11-04T09:34:09.738Z nl=1 -->

## Overview

When using [ArkTS modularization](module-principle.md), module loading and execution may cause **side effects**. A side effect refers to additional behavior or state changes beyond the exported functions or objects when a module is imported. **These behaviors may affect other parts of the program and lead to issues such as unintended top-level code execution, global state changes, prototype chain modification, and undefined imported content.**

## Scenarios and Optimization Methods for Side Effects

### Top-Level Code Execution in Modules

**Scenario of side effects**

When a module is imported, all top-level code within the module file is executed immediately, not just the exported parts. This means that even if only specific exports are needed, any code in the top-level scope will run, potentially causing side effects.

<!-- @[export_modulePartOne](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSModule/ArkModuleSideEffects/entry/src/main/ets/pages/ModulePartOne.ets) -->

``` TypeScript
// ModulePartOne.ets
console.info('Module loaded!'); // This code executes immediately upon import and may cause side effects.
export const data = 1;
```

<!-- @[import_modulePartOne](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSModule/ArkModuleSideEffects/entry/src/main/ets/pages/PageOne.ets) -->

``` TypeScript
// PageOne.ets
import { data } from './ModulePartOne'; // When imported, console.info in ModulePartOne.ets executes and produces output.
console.info('data is ', data);
```

The output is as follows:

```typescript
Module loaded!
data is  1
```

**Side effects produced**

Even though only **data** is required, **console.info("Module loaded!")** still runs, causing the unexpected output of "Module loaded!" in addition to the value of **data**.

**Optimized methods**

Optimization method 1: Remove the top-level code and export only the required content to avoid unnecessary code execution.

<!-- @[export_modulePartTwo](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSModule/ArkModuleSideEffects/entry/src/main/ets/pages/ModulePartTwo.ets) -->

``` TypeScript
// ModulePartTwo.ets
export const data = 1;
```

<!-- @[import_modulePartTwo](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSModule/ArkModuleSideEffects/entry/src/main/ets/pages/PageTwo.ets) -->

``` TypeScript
// PageTwo.ets
import { data } from './ModulePartTwo';
console.info('data is ', data);
```

The output is as follows:

```typescript
data is  1
```

Optimization method 2: Encapsulate code that may cause side effects within functions or methods, and execute the code only when needed, rather than upon module loading.

<!-- @[export_modulePartThree](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSModule/ArkModuleSideEffects/entry/src/main/ets/pages/ModulePartThree.ets) -->

``` TypeScript
// ModulePartThree.ets
export function initialize() {
  console.info('Module loaded!');
}
export const data = 1;
```

<!-- @[import_modulePartThree](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSModule/ArkModuleSideEffects/entry/src/main/ets/pages/PageThree.ets) -->

``` TypeScript
// PageThree.ets
import { data } from './ModulePartThree';
console.info('data is ', data);
```

The output is as follows:

```typescript
data is  1
```

### Modifying Global Objects

**Scenario of side effects**

The top-level code or imported modules may directly manipulate global variables, thereby changing the global state and causing side effects.

<!-- @[export_modulePartFour](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSModule/ArkModuleSideEffects/entry/src/main/ets/pages/ModulePartFour.ets) -->

``` TypeScript
// ModulePartFour.ets
export let data1 = 'data from module';
globalThis.someGlobalVar = 100; // Changes the global state.
```

<!-- @[export_sideEffectModuleFour](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSModule/ArkModuleSideEffects/entry/src/main/ets/pages/SideEffectModuleFour.ets) -->

``` TypeScript
// SideEffectModuleFour.ets
export let data2 = 'data from side effect module';
globalThis.someGlobalVar = 200; // Also changes the global state.
```

<!-- @[export_moduleUseGlobalVarFour](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSModule/ArkModuleSideEffects/entry/src/main/ets/pages/ModuleUseGlobalVarFour.ets) -->

``` TypeScript
// ModuleUseGlobalVarFour.ets
import { data1 } from './ModulePartFour'; // At this point, the global variable someGlobalVar may be expected to be 100.
export function useGlobalVar() {
  console.info('data1 is ', data1);
  console.info('globalThis.someGlobalVar is ', globalThis.someGlobalVar); // At this point, because SideEffectModuleFour is loaded in PageFour.ets, the value of someGlobalVar has already been changed to 200.
}
```

<!-- @[import_modulePartFour](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSModule/ArkModuleSideEffects/entry/src/main/ets/pages/PageFour.ets) -->

``` TypeScript
// PageFour.ets (execution entry)
import { data1 } from './ModulePartFour'; // Change the value of the global variable someGlobalVar to 100
import { data2 } from './SideEffectModuleFour'; // Change the value of the global variable someGlobalVar to 200 again
import { useGlobalVar } from './ModuleUseGlobalVarFour';

useGlobalVar();
function maybeNotCalledAtAll() {
  console.info('data1 is ', data1);
  console.info('data2 is ', data2);
}
```

The output is as follows:

```text
data1 is  data from module
globalThis.someGlobalVar is  200
```

**Side effects produced**

Modules directly change the value of the **global variable globalThis.someGlobalVar**, affecting other modules or code that depends on this variable.

**Optimized methods**

Encapsulate code that may cause side effects within functions or methods, and execute the code only when needed, rather than upon module loading.

<!-- @[export_modulePartFive](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSModule/ArkModuleSideEffects/entry/src/main/ets/pages/ModulePartFive.ets) -->

``` TypeScript
// ModulePartFive.ets
export let data1 = 'data from module';
export function changeGlobalVar() {
  globalThis.someGlobalVar = 100;
}
```

<!-- @[export_sideEffectModuleFive](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSModule/ArkModuleSideEffects/entry/src/main/ets/pages/SideEffectModuleFive.ets) -->

``` TypeScript
// SideEffectModuleFive.ets
export let data2 = 'data from side effect module';
export function changeGlobalVar() {
  globalThis.someGlobalVar = 200;
}
```

<!-- @[export_moduleUseGlobalVarFive](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSModule/ArkModuleSideEffects/entry/src/main/ets/pages/ModuleUseGlobalVarFive.ets) -->

``` TypeScript
// ModuleUseGlobalVarFive.ets
import { data1, changeGlobalVar } from './ModulePartFive';
export function useGlobalVar() {
  console.info('data1 is ', data1);
  changeGlobalVar(); // Execute the code when needed, rather than during module loading.
  console.info('globalThis.someGlobalVar is ', globalThis.someGlobalVar);
}
```

<!-- @[import_modulePartFive](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSModule/ArkModuleSideEffects/entry/src/main/ets/pages/PageFive.ets) -->

``` TypeScript
// PageFive.ets (entry point)
import { data1 } from './ModulePartFive';
import { data2 } from './SideEffectModuleFive';
import { useGlobalVar } from './ModuleUseGlobalVarFive';

useGlobalVar();
function maybeNotCalledAtAll() {
  console.info('data1 is ', data1);
  console.info('data2 is ', data2);
}
```

The output is as follows:

```text
data1 is  data from module
globalThis.someGlobalVar is  100
```

### Modifying State Variables of Application-level ArkUI Components

**Scenario of side effects**

The top-level code or imported modules may directly modify the state variables of application-level ArkUI components, thereby changing the global state and causing side effects.

<!-- @[export_modulePartSix](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSModule/ArkModuleSideEffects/entry/src/main/ets/pages/ModulePartSix.ets) -->

``` TypeScript
// ModulePartSix.ets
export let data = 'data from module';
AppStorage.setOrCreate('SomeAppStorageVar', 200); // Modify the application-global UI state.
```

<!-- @[import_modulePartSix](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSModule/ArkModuleSideEffects/entry/src/main/ets/pages/PageSix.ets) -->

``` TypeScript
// PageSix.ets
import { data } from './ModulePartSix'; // Changes SomeAppStorageVar in AppStorage to 200.

@Entry
@Component
struct Index {
  // The developer may expect this value to be 100, but because ModulePartSix is imported, the value has already been changed to 200, and the developer may not know that the value has been modified.
  @StorageLink('SomeAppStorageVar') message: number = 100;
  build() {
    Row() {
      Column() {
        Text('test' + this.message)
          .fontSize(50)
      }
      .width('100%')
    }
    .height('100%')
  }
}
function maybeNotCalledAtAll() {
  console.info('data is ', data);
}
```

The following content is displayed:

```text
test200
```

**Side effects produced**

Modules directly change the value of **SomeAppStorageVar** in AppStorage, affecting other modules or code that depends on this variable.

For more information on modifying ArkUI component state variables, see [State Management Overview](../ui/state-management/arkts-state-management-overview.md).

**Optimized methods**

Encapsulate code that may cause side effects within functions or methods, and execute the code only when needed, rather than upon module loading.

<!-- @[export_modulePartSeven](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSModule/ArkModuleSideEffects/entry/src/main/ets/pages/ModulePartSeven.ets) -->

``` TypeScript
// ModulePartSeven.ets
export let data = 'data from module';
export function initialize() {
  AppStorage.setOrCreate('SomeAppStorageVar', 200);
}
```

<!-- @[import_modulePartSeven](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSModule/ArkModuleSideEffects/entry/src/main/ets/pages/PageSeven.ets) -->

``` TypeScript
// PageSeven.ets
import { data } from './ModulePartSeven';

@Entry
@Component
struct Index {
  @StorageLink('SomeAppStorageVar') message: number = 100;
  build() {
    Row() {
      Column() {
        Text('test' + this.message)
          .fontSize(50)
      }
      .width('100%')
    }
    .height('100%')
  }
}
function maybeNotCalledAtAll() {
  console.info('data is ', data);
}
```

The following content is displayed:

```text
test100
```

### Modifying Built-in Global Variables or Prototype Chains (Modifying Object Prototypes or Built-in Methods Is Forbidden in ArkTS)

**Scenario of side effects**

To support modern JavaScript features in old browsers or runtime environments, third-party libraries or frameworks may modify built-in global objects or prototype chains. This can affect the execution of other code.

<!-- @[export_modifyPrototype](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSModule/ArkModuleSideEffects/entry/src/main/ets/pages/ModifyPrototype.ts) -->

``` TypeScript
// ModifyPrototype.ts
export let data = 'data from modifyPrototype';
Array.prototype.includes = function (value) {
  return this.indexOf(value) !== -1;
};
```

<!-- @[import_modulePartEight](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSModule/ArkModuleSideEffects/entry/src/main/ets/pages/PageEight.ets) -->

``` TypeScript
// PageEight.ets
import { data } from './ModifyPrototype'; // At this point, the prototype chain of Array is modified.
let arr = [1, 2, 3, 4];
console.info('arr.includes(1) = ' + arr.includes(1)); // At this point, the Array.prototype.includes method in ModifyPrototype.ts is called.
function maybeNotCalledAtAll() {
  console.info('data is ', data);
}
```

**Side effects produced**

Modifying built-in global objects or prototype chains may affect the execution of other code.

**Optimized methods**

When importing third-party libraries that may modify built-in global objects or prototype chains, ensure that the behavior of the third-party library is as expected.

### Circular Dependencies

**Scenario of side effects**

ArkTS modularization supports circular dependencies, where module A depends on module B, and module B depends on module A. In such cases, some imported modules may not be fully loaded, leading to abnormal behavior and unintended side effects during execution.

<!-- @[export_a](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSModule/ArkModuleSideEffects/entry/src/main/ets/pages/ExportA.ets) -->

``` TypeScript
// ExportA.ets
import { b } from './ExportB';
console.info('Module A: ', b);
export const a = 'A';
```

<!-- @[export_b](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSModule/ArkModuleSideEffects/entry/src/main/ets/pages/ExportB.ets) -->

``` TypeScript
// ExportB.ets
import { a } from './ExportA';
console.info('Module B: ', a);
export const b = 'B';
```

The output is as follows:

```text
Error message: a is not initialized
Stacktrace:
    at func_main_0 (b.ets:2:27)
```

**Side effects produced**

Due to mutual dependencies between modules, the execution order of modules may result in undefined exports, affecting the logic flow of the code. The specific error message is "Variable name is not initialized."

**Optimized methods**

Avoid circular dependencies between modules whenever possible, and ensure that the loading order of modules is clear and controllable to prevent unexpected side effects. You can use [@security/no-cycle](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide_no-cycle) when detecting circular dependencies.

### Lazy Import Changing the Module Execution Sequence and Leading to Undefined Global Variables

**Scenario of side effects**

The [Lazy Import](arkts-lazy-import.md) feature allows modules to be loaded on-demand during the application runtime, rather than during the cold start phase, thereby reducing the cold start time. However, this also changes the execution sequence of modules.

<!-- @[export_modulePartNine](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSModule/ArkModuleSideEffects/entry/src/main/ets/pages/ModulePartNine.ets) -->

``` TypeScript
// ModulePartNine.ets
export let data = 'data from module';
globalThis.someGlobalVar = 100;
```

<!-- @[import_moduleUseGlobalVarNine](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSModule/ArkModuleSideEffects/entry/src/main/ets/pages/ModuleUseGlobalVarNine.ets) -->

``` TypeScript
// ModuleUseGlobalVarNine.ets
import lazy { data } from './ModulePartNine';
console.info('globalThis.someGlobalVar', globalThis.someGlobalVar); // At this point, due to the lazy feature, the ModulePartNine module has not been executed yet, so the value of someGlobalVar is undefined
console.info('data is ', data); // Uses a variable from the ModulePartNine module, at which point the ModulePartNine module is executed and the value of someGlobalVar becomes 100
```

The output is as follows:

```text
globalThis.someGlobalVar undefined
data is  data from module
```

**Side effects produced**

Using the lazy import feature delays the execution of modules until they are needed. Modifications to global variables within these modules are also delayed, potentially leading to unexpected results.

**Optimized methods**

Encapsulate code that may cause side effects within functions or methods, and execute the code only when needed, rather than upon module loading.

<!-- @[export_modulePartTen](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSModule/ArkModuleSideEffects/entry/src/main/ets/pages/ModulePartTen.ets) -->

``` TypeScript
// ModulePartTen.ets
export let data = 'data from module';
export function initialize() {
  globalThis.someGlobalVar = 100; // Defer execution until the function is called.
}
```

<!-- @[import_moduleUseGlobalVarTen](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSModule/ArkModuleSideEffects/entry/src/main/ets/pages/ModuleUseGlobalVarTen.ets) -->

``` TypeScript
// ModuleUseGlobalVarTen.ets
import lazy { data, initialize } from './ModulePartTen';
initialize(); // Execute the initialization function to initialize someGlobalVar.
console.info('globalThis.someGlobalVar is ', globalThis.someGlobalVar); // At this point, someGlobalVar is definitely the expected value.
console.info('data is ', data);
```

The output is as follows:

```text
globalThis.someGlobalVar is  100
data is  data from module
```

## Optimizing Performance with import Path Expansion

### Working Principle

In import statements, skipping intermediate dependency paths and directly importing the module corresponding to the variable is known as import path expansion.

The following example illustrates the principle of optimizing performance with import path expansion:

<!-- @[unOptIndex](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSModule/expandPath/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
// src/main/ets/pages/Index.ets
import * as har from 'expandPathHar';

console.info('har.One is ', har.One); // The One variable here is exported by expandPathHar/src/main/ets/NumberString.ets
```

<!-- @[expandPathHarIndex](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSModule/expandPath/expandPathHar/Index.ets) -->

``` TypeScript
// expandPath/expandPathHar/Index.ets
export * from './src/main/ets/OtherModule1'
export * from './src/main/ets/OtherModule2'
export * from './src/main/ets/Utils'
console.info('expandPathHar Index.ets execute.');
```

<!-- @[Utils](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSModule/expandPath/expandPathHar/src/main/ets/Utils.ets) -->

``` TypeScript
// expandPathHar/src/main/ets/Utils.ets
export * from './OtherModule3'
export * from './OtherModule4'
export * from './NumberString'
console.info('expandPathHar Utils.ets execute.');
```

<!-- @[export_numberString](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSModule/expandPath/expandPathHar/src/main/ets/NumberString.ets) -->

``` TypeScript
// expandPathHar/src/main/ets/NumberString.ets
export const One: string = '1';
console.info('expandPathHar NumberString.ets execute.');
```

1. If Index.ets only needs to depend on the NumberString module in expandPathHar, the `import xxx from "expandPathHar"` syntax will cause all modules along the entire expandPathHar chain to be parsed and executed, **increasing the time consumed by module parsing and execution**. In the example above, the expandPathHar/Index, OtherModule1, OtherModule2, Utils, OtherModule3, OtherModule4, and NumberString modules will all be parsed and executed.

2. During the module parsing phase, variable binding relationships are established through depth-first traversal. The `har.One` variable used in Index.ets is exported by expandPathHar/src/main/ets/NumberString.ets. Because the `export *` syntax is used, establishing the variable binding relationship requires recursively matching variable names, which **increases the time consumed by module parsing**.

In the example above, the `expandPathHar/Index.ets` file is searched first. This file contains multiple `export *` statements, so `OtherModule1` and `OtherModule2` are checked in turn to see whether they export the `One` variable. Next, the `Utils` module is found, which also has an `export *` statement, so `OtherModule3` and `OtherModule4` are checked further, and it is finally determined that the `One` variable is exported from the `NumberString` module.

Optimization methods: Modify the code as follows to skip intermediate dependency paths and directly import the module corresponding to the variable.

<!-- @[OptIndex](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSModule/expandPath/entry/src/main/ets/pages/index2.ets) -->

``` TypeScript
// src/main/ets/pages/index2.ets
import { One } from 'expandPathHar/src/main/ets/NumberString';

console.info('One is ', One);
```

<!-- @[export_numberString](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSModule/expandPath/expandPathHar/src/main/ets/NumberString.ets) -->

``` TypeScript
// expandPathHar/src/main/ets/NumberString.ets
export const One: string = '1';
console.info('expandPathHar NumberString.ets execute.');
```

### Side Effects

**Scenario of side effects**

Import path expansion skips the execution of intermediate modules. If the service logic depends on the order of module execution, modifications might lead to service exceptions.

<!-- @[opServiceManagerIndex](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSModule/expandPathSideEffects/entry/src/main/ets/pages/opIndex.ets) -->

``` TypeScript
// src/main/ets/pages/opIndex.ets
import { serviceManager } from 'servicemanagerhar'

serviceManager.print();
```

<!-- @[ServiceManagerIndex](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSModule/expandPathSideEffects/serviceManagerHar/Index.ets) -->

``` TypeScript
// serviceManagerHar/Index.ets
import { serviceManager } from './src/main/ets/ServiceManager';

serviceManager.init();
export { serviceManager }
```

<!-- @[ServiceManager](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSModule/expandPathSideEffects/serviceManagerHar/src/main/ets/ServiceManager.ets) -->

``` TypeScript
// serviceManagerHar/src/main/ets/ServiceManager.ets
class ServiceManager {
  public inited: boolean = false;

  public init() {
    this.inited = true;
  }
  public print() {
    if (this.inited) {
      console.info('ServiceManager is inited.');
    } else {
      console.error('ServiceManager is not inited.');
    }
  }
}
export let serviceManager: ServiceManager = new ServiceManager();
```

The output at runtime is as follows:

```text
ServiceManager is inited.
```

If import path expansion is used, the code becomes:

<!-- @[ServiceManagerIndex](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSModule/expandPathSideEffects/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
// src/main/ets/pages/Index.ets
import { serviceManager } from 'servicemanagerhar/src/main/ets/OpServiceManager'

serviceManager.print();
```

<!-- @[ServiceManager](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSModule/expandPathSideEffects/serviceManagerHar/src/main/ets/ServiceManager.ets) -->

``` TypeScript
// serviceManagerHar/src/main/ets/ServiceManager.ets
class ServiceManager {
  public inited: boolean = false;

  public init() {
    this.inited = true;
  }
  public print() {
    if (this.inited) {
      console.info('ServiceManager is inited.');
    } else {
      console.error('ServiceManager is not inited.');
    }
  }
}
export let serviceManager: ServiceManager = new ServiceManager();
```

The output at runtime is as follows:

```text
ServiceManager is not inited.
```

**Side effects produced**

Because the serviceManagerHar/Index module contains top-level code that initializes ServiceManager, if import path expansion is performed in the Index module, the serviceManagerHar/Index module will not be executed, resulting in ServiceManager not being initialized and possibly causing service exceptions.

**Optimized methods**

You need to check the impact of skipping the execution of the top-level code based on service requirements and make modifications accordingly.

For the example above, the following modifications can be made:

<!-- @[ServiceManagerIndex](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSModule/expandPathSideEffects/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
// src/main/ets/pages/Index.ets
import { serviceManager } from 'servicemanagerhar/src/main/ets/OpServiceManager'

serviceManager.print();
```

<!-- @[OpServiceManager](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSModule/expandPathSideEffects/serviceManagerHar/src/main/ets/OpServiceManager.ets) -->

``` TypeScript
// serviceManagerHar/src/main/ets/OpServiceManager.ets
class ServiceManager {
  public inited: boolean = false;

  public init() {
    this.inited = true;
  }
  public print() {
    if (this.inited) {
      console.info('ServiceManager is inited.');
    } else {
      console.error('ServiceManager is not inited.');
    }
  }
}
export let serviceManager: ServiceManager = new ServiceManager();
// Execute the corresponding logic in the exported module.
serviceManager.init();
```
