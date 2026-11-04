# Statically Loading Native Modules
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @yao_dashuai-->
<!--Designer: @yao_dashuai-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=6bbb64fd5d8fdd5780a6d9ccd6e77aab73121f9f translatedAt=2026-11-04T09:03:45.811Z pushedAt=2026-11-04T09:27:29.916Z nl=1 -->

In the ES6 (ECMAScript 6.0) module design, using the import syntax to load content exported by other files is a syntax rule defined by the ECMA specification. To support developers in using this feature to import content exported by Native modules (so), ArkTS has made relevant adaptations and provides the following three supported writing styles: direct import, indirect import, and dynamic import.

## Direct Import
Export it in the Index.d.ts file of the Native module and import it directly within the file.

### Named Import

<!-- @[export_add](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/ArktsImportNativeModule/entry/src/main/cpp/types/libentry/Index.d.ts) -->  

``` TypeScript
// Index.d.ts corresponding to libentry.so
export const add: (a: number, b: number) => number;
```


<!-- @[name_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/ArktsImportNativeModule/entry/src/main/ets/pages/NameImport.ets) -->     

``` TypeScript
// NameImport.ets
import { add } from 'libentry.so';
add(2, 3);
```

### Default Import

<!-- @[export_add](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/ArktsImportNativeModule/entry/src/main/cpp/types/libentry/Index.d.ts) -->   

``` TypeScript
// Index.d.ts corresponding to libentry.so
export const add: (a: number, b: number) => number;
```


<!-- @[default_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/ArktsImportNativeModule/entry/src/main/ets/pages/DefaultImport.ets) -->     

``` TypeScript
// DefaultImport.ets
import entry from 'libentry.so';
entry.add(2, 3);
```

### Namespace Import

<!-- @[export_add](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/ArktsImportNativeModule/entry/src/main/cpp/types/libentry/Index.d.ts) -->   

``` TypeScript
// Index.d.ts corresponding to libentry.so
export const add: (a: number, b: number) => number;
```


<!-- @[namespace_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/ArktsImportNativeModule/entry/src/main/ets/pages/NamespaceImport.ets) -->    

``` TypeScript
// NamespaceImport.ets
import * as entry from 'libentry.so';
entry.add(2, 3);
```

## Indirect Import

### Export as Named Variables and Import

<!-- @[export_add](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/ArktsImportNativeModule/entry/src/main/cpp/types/libentry/Index.d.ts) -->   

``` TypeScript
// Index.d.ts corresponding to libentry.so
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
// Index.d.ts corresponding to libentry.so
export const add: (a: number, b: number) => number;
```


<!-- @[namespace_export](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/ArktsImportNativeModule/entry/src/main/ets/pages/NamespaceExport.ets) -->    

``` TypeScript
// NamespaceExport.ets
export * from 'libentry.so';
```

<!-- @[namespaceImport_fromExport](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/ArktsImportNativeModule/entry/src/main/ets/pages/NamespaceImportFromExport.ets) -->    

``` TypeScript
// NamespaceImportFromExport.ets
import { add } from './NamespaceExport';
add(2, 3);
```

> **Note:** 
> 
> Using namespace export (export *) on the export side together with namespace import (import * as) on the import side is not supported.

**Anti-example:** 
``` TypeScript
// test1.ets
export * from 'libentry.so';
```
``` TypeScript
// test2.ets
import * as lib from './test1'
// Unable to obtain the lib object.
```

## Dynamic Import

### Direct Import

<!-- @[export_add](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/ArktsImportNativeModule/entry/src/main/cpp/types/libentry/Index.d.ts) -->  

``` TypeScript
// Index.d.ts corresponding to libentry.so
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
import entry from 'libentry.so';
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
export * from 'libentry.so';
```
``` TypeScript
// test2.ets
import('./test1').then((ns:ESObject) => {
    // The ns object cannot be obtained.
})
```