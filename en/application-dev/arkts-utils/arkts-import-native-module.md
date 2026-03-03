# Statically Loading Native Modules
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @yao_dashuai-->
<!--Designer: @yao_dashuai-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @jinqiuheng-->

In ECMAScript 6.0 (ES6) module design, the **import** syntax is used to load content exported by other files, as defined by the ECMAScript specification. To help you import content exported from native modules (.so), ArkTS has adapted and provides the following methods:

## Direct Import
Export content from the **index.d.ts** file of a native module, and then import the content to the file.

### Named Import

<!-- @[export_add](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/ArktsImportNativeModule/entry/src/main/cpp/types/libentry/Index.d.ts) -->

``` TypeScript
// index.d.ts corresponding to libentry.so
export const add: (a: number, b: number) => number;
```

<!-- @[name_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/ArktsImportNativeModule/entry/src/main/ets/pages/NameImport.ets) -->     

``` TypeScript
// NameImport.ets
import { add } from 'libentry.so'
add(2, 3);
```

### Default Import

<!-- @[export_add](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/ArktsImportNativeModule/entry/src/main/cpp/types/libentry/Index.d.ts) -->     

``` TypeScript
// index.d.ts corresponding to libentry.so
export const add: (a: number, b: number) => number;
```

<!-- @[default_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/ArktsImportNativeModule/entry/src/main/ets/pages/DefaultImport.ets) -->     

``` TypeScript
// DefaultImport.ets
import entry from 'libentry.so'
entry.add(2, 3);
```

### Namespace Import

<!-- @[export_add](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/ArktsImportNativeModule/entry/src/main/cpp/types/libentry/Index.d.ts) -->     

``` TypeScript
// index.d.ts corresponding to libentry.so
export const add: (a: number, b: number) => number;
```

<!-- @[namespace_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/ArktsImportNativeModule/entry/src/main/ets/pages/NamespaceImport.ets) -->    

``` TypeScript
// NamespaceImport.ets
import * as entry from 'libentry.so'
entry.add(2, 3);
```

## Indirect Import

### Export as Named Variables and Import

<!-- @[export_add](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/ArktsImportNativeModule/entry/src/main/cpp/types/libentry/Index.d.ts) -->     

``` TypeScript
// index.d.ts corresponding to libentry.so
export const add: (a: number, b: number) => number;
```

<!-- @[name_export](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/ArktsImportNativeModule/entry/src/main/ets/pages/NameExport.ets) -->    

``` TypeScript
// NameExport.ets
// Encapsulate the API of libentry.so and export it.
import { add } from 'libentry.so';
export { add };
```

<!-- @[nameImport_fromExport](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/ArktsImportNativeModule/entry/src/main/ets/pages/NameImportFromExport.ets) -->    

``` TypeScript
// NameImportFromExport.ets
// Import APIs from the intermediate module.
import { add } from './NameExport';
const result = add(2, 3);
```

### Export as Namespaces and Import

<!-- @[export_add](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/ArktsImportNativeModule/entry/src/main/cpp/types/libentry/Index.d.ts) -->     

``` TypeScript
// index.d.ts corresponding to libentry.so
export const add: (a: number, b: number) => number;
```

<!-- @[namespace_export](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/ArktsImportNativeModule/entry/src/main/ets/pages/NamespaceExport.ets) -->    

``` TypeScript
// NamespaceExport.ets
export * from 'libentry.so'
```

<!-- @[namespaceImport_fromExport](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/ArktsImportNativeModule/entry/src/main/ets/pages/NamespaceImportFromExport.ets) -->    

``` TypeScript
// NamespaceImportFromExport.ets
import { add } from './NamespaceExport'
add(2, 3);
```

> **NOTE**
> 
> Native modules do not support both export and import using namespaces simultaneously.

**Anti-example:**
``` TypeScript
// test1.ets
export * from 'libentry.so'
```
``` TypeScript
// test2.ets
import * as add from './test1'
// The add object cannot be obtained.
```

## Dynamic Import

### Direct Import

<!-- @[export_add](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/ArktsImportNativeModule/entry/src/main/cpp/types/libentry/Index.d.ts) -->    

``` TypeScript
// index.d.ts corresponding to libentry.so
export const add: (a: number, b: number) => number;
```

<!-- @[dynamic_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/ArktsImportNativeModule/entry/src/main/ets/pages/DynamicImport.ets) -->    

``` TypeScript
// DynamicImport.ets
import('libentry.so').then((entry:ESObject) => {
  entry.default.add(2, 3);
})
```
### Indirect Import
<!-- @[dynamic_export](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/ArktsImportNativeModule/entry/src/main/ets/pages/DynamicExport.ets) -->    

``` TypeScript
// DynamicExport.ets
import entry from 'libentry.so'
export { entry }
```

<!-- @[dynamicImport_fromExport](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/ArktsImportNativeModule/entry/src/main/ets/pages/DynamicImportFromExport.ets) -->  

``` TypeScript
// DynamicImportFromExport.ets
import('./DynamicExport').then((ns:ESObject) => {
  ns.entry.add(2, 3);
})
```

> **NOTE**
> 
> Dynamic imports do not support exporting files using namespace exports.

**Anti-example:**
``` TypeScript
// test1.ets
export * from 'libentry.so'
```
``` TypeScript
// test2.ets
import('./test1').then((ns:ESObject) => {
    // The ns object cannot be obtained.
})
```
