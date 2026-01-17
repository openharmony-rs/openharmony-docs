# 静态方式加载Native模块
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @yao_dashuai-->
<!--Designer: @yao_dashuai-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @foryourself-->

在ES6(ECMAScript 6.0)模块设计中，使用import语法加载其他文件导出的内容是ECMA规范所定义的语法规则。为支持开发者使用该功能导入Native模块（so）导出的内容，ArkTS进行了相关适配，并提供了以下几种支持写法。

## 直接导入
在Native模块的index.d.ts文件中导出，并在文件内直接导入。

### 具名导入

<!-- @[export_add](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/ArktsImportNativeModule/entry/src/main/cpp/types/libentry/Index.d.ts) -->

``` TypeScript
// libentry.so对应的index.d.ts。
export const add: (a: number, b: number) => number;
```

<!-- @[name_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/ArktsImportNativeModule/entry/src/main/ets/pages/NameImport.ets) -->     

``` TypeScript
// NameImport.ets
import { add } from 'libentry.so'
add(2, 3);
```

### 默认导入

<!-- @[export_add](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/ArktsImportNativeModule/entry/src/main/cpp/types/libentry/Index.d.ts) -->     

``` TypeScript
// libentry.so对应的index.d.ts。
export const add: (a: number, b: number) => number;
```

<!-- @[default_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/ArktsImportNativeModule/entry/src/main/ets/pages/DefaultImport.ets) -->     

### 命名空间导入

<!-- @[export_add](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/ArktsImportNativeModule/entry/src/main/cpp/types/libentry/Index.d.ts) -->     

<!-- @[namespace_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/ArktsImportNativeModule/entry/src/main/ets/pages/NamespaceImport.ets) -->    

## 间接导入

### 转为具名变量导出再导入

<!-- @[export_add](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/ArktsImportNativeModule/entry/src/main/cpp/types/libentry/Index.d.ts) -->     

<!-- @[name_export](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/ArktsImportNativeModule/entry/src/main/ets/pages/NameExport.ets) -->    

<!-- @[nameImport_fromExport](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/ArktsImportNativeModule/entry/src/main/ets/pages/NameImportFromExport.ets) -->    

### 转为命名空间导出再导入

<!-- @[export_add](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/ArktsImportNativeModule/entry/src/main/cpp/types/libentry/Index.d.ts) -->     

<!-- @[namespace_export](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/ArktsImportNativeModule/entry/src/main/ets/pages/NamespaceExport.ets) -->    

<!-- @[namespaceImport_fromExport](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/ArktsImportNativeModule/entry/src/main/ets/pages/NamespaceImportFromExport.ets) -->    

> **注意：** 
> 
> 不支持Native模块导出和导入同时使用命名空间。

**反例：** 
```ts
// test1.ets
export * from 'libentry.so'
```
```ts
// test2.ets
import * as add from './test1'
// 无法获取add对象
```

## 动态导入

### 直接导入

<!-- @[export_add](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/ArktsImportNativeModule/entry/src/main/cpp/types/libentry/Index.d.ts) -->     

<!-- @[dynamic_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/ArktsImportNativeModule/entry/src/main/ets/pages/DynamicImport.ets) -->    

### 间接导入
<!-- @[export_add](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/ArktsImportNativeModule/entry/src/main/cpp/types/libentry/Index.d.ts) -->    

<!-- @[dynamic_export](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/ArktsImportNativeModule/entry/src/main/ets/pages/DynamicExport.ets) -->    

<!-- @[dynamicImport_fromExport](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/ArktsImportNativeModule/entry/src/main/ets/pages/DynamicImportFromExport.ets) -->  

> **注意：** 
> 
> 不支持动态加载时，导出文件使用命名空间。

**反例：** 
```ts
// test1.ets
export * from 'libentry.so'
```
```ts
// test2.ets
import('./test1').then((ns:ESObject) => {
    // 无法获取ns对象
})
```