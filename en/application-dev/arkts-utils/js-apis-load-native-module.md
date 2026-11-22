---
kits: ["ArkTS / Ark Programming Language"]
description: "Describes how to use the loadNativeModule API to synchronously and dynamically load Native modules. It supports loading system libraries and in-app Native modules, and is applicable to scenarios where .so libraries are loaded on demand."
keywords: [ArkTS, loadNativeModule, dynamic loading, Native module, synchronous loading, .so library, system library, on-demand loading]
doctype: guide
status: active
---

# Dynamically Loading Native Modules in Synchronous Mode
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @shilei123-->
<!--Designer: @yao_dashuai-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=da641289f51d20c4f9fd6f0614d722cdc941f200 translatedAt=2026-11-06T10:36:04.563Z pushedAt=2026-11-12T06:48:42.289Z nl=1 -->

[loadNativeModule (synchronous dynamic loading system library API)](../reference/common/js-apis-common-load-native-module.md) is used to synchronously dynamically load Native modules, with the purpose of loading the required modules on demand.

## API Description

```js
loadNativeModule(moduleName: string): Object;
```

| Parameter           | Description         |
| :------------- | :----------------------------- |
| moduleName            | Name of the module to load.      |

## Supported Scenarios

| Scenario           | Example          | 
| :------------- | :----------------------------- | 
| System library module       | Load **@ohos.** or **@system.**.       | 
| Native module in an application | Load **libNativeLibrary.so**.|

## Usage Notes

- `loadNativeModule` supports loading native modules only in the UI main thread of the Stage model.
- Using this API increases the loading time of the .so file. Evaluate its impact on application performance and functionality before use.
- Regardless of whether the `moduleName` parameter uses a constant string or a variable expression, the dependency must be configured in the `dependencies` field of the dependent module's `oh-package.json5` file. The value of `moduleName` is the dependency name declared in the `dependencies` field.
- When loading an in-app native module, you must also configure the module name in the `buildOption.arkOptions.runtimeOnly.packages` field of the dependent module's `build-profile.json5` file. This name must be consistent with the dependency name in the `oh-package.json5` file and the input parameter of `loadNativeModule`.
- The return value type declared by the API is `Object`. When calling the API, use a variable of the `ESObject` type to receive the return value so that you can call the methods exported by the native module. If you use the `Object` type to receive the return value, calling the methods in it may cause compilation errors.

Take loading `libentry.so` as an example. The following configurations are required.

1. Configure the `dependencies` field in the module-level `oh-package.json5` file.

    <!-- @[hap_load_native_dependence](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/JsApisLoadNativeModule/entry/oh-package.json5) -->
    
    ``` JSON5
    "dependencies": {
      "libentry.so": "file:./src/main/cpp/types/libentry"
    },
    ```

2. Configure the `runtimeOnly.packages` field in the module-level `build-profile.json5` file.

    <!-- @[hap_load_native_dependence_01](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/JsApisLoadNativeModule/entry/build-profile.json5) -->
    
    ``` JSON5
    "buildOption": {
      "arkOptions": {
        "runtimeOnly": {
          "packages": [
            "libentry.so"
          ]
        }
      },
      // ...
    },
    ```

## Usage Example

**Example 1**: HAP loads a system library module

<!-- @[hap_load_system_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/JsApisLoadNativeModule/entry/src/main/ets/pages/Index.ets) --> 

``` TypeScript
// HAP loads the system library module.
let hilog: ESObject = loadNativeModule('@ohos.hilog');
hilog.info(0, 'testTag', 'loadNativeModule ohos.hilog success');
```

**Example 2**: HAP loads a Native library

The **index.d.ts** file of **libentry.so** is as follows:

<!-- @[hap_load_native](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/JsApisLoadNativeModule/entry/src/main/cpp/types/libentry/index.d.ts) -->

``` TypeScript
export const add: (a: number, b: number) => number;
```

After completing the dependency configuration in [Usage Notes](#usage-notes), use `loadNativeModule` to load `libentry.so` and call the `add` function.

<!-- @[load_native_module_libentry](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArkTSModule/JsApisLoadNativeModule/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
// HAP loads the Native library.
let module: ESObject = loadNativeModule('libentry.so');
let sum: number = module.add(1, 2);
```
