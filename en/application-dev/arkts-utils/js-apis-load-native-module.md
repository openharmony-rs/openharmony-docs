# Dynamically Loading Native Modules in Synchronous Mode
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @shilei123-->
<!--Designer: @yao_dashuai-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @foryourself-->

The **loadNativeModule** API is used to dynamically load native modules in synchronous mode. Using this API increases the time for loading the .so file. You need to evaluate the impact on the functionality.

## API Description

```js
loadNativeModule(moduleName: string): Object;
```

| Parameter           | Description         |
| :------------- | :----------------------------- |
| moduleName            | Name of the module to load.      |

> **NOTE**
> The name of the module loaded by **loadNativeModule** is the name provided in **dependencies** in the **oh-package.json5** file of the dependency.
>
> **loadNativeModule** must be called in the UI main thread.
>
> Dependencies must be configured for the API call regardless of whether the parameter is a constant string or variable expression.

## Supported Scenarios

| Scenario           | Example          | 
| :------------- | :----------------------------- | 
| System library module       | Load **@ohos.** or **@system.**.       | 
| Native module in an application| Load **libNativeLibrary.so**.|

## Usage Example

- **Loading a system library module to a HAP**

```js
let hilog: ESObject = loadNativeModule("@ohos.hilog");
hilog.info(0, "testTag", "loadNativeModule ohos.hilog success");
```

- **Loading a native library to a HAP**

The **index.d.ts** file of **libentry.so** is as follows:

```javascript
//index.d.ts
export const add: (a: number, b: number) => number;
```

1. When loading a local .so library, configure dependencies in the **oh-package.json5** file.

```json
{
  "dependencies": {
    "libentry.so": "file:./src/main/cpp/types/libentry"
  }
}
```

2. Configure the **build-profile.json5** file.

```json
{
  "buildOption": {
    "arkOptions": {
      "runtimeOnly": {
        "packages": [
          "libentry.so"
        ]
      }
    }
  }
}
```

3. Use **loadNativeModule** to load **libentry.so** and call the **add** function.

```js
let module: ESObject = loadNativeModule("libentry.so");
let sum: number = module.add(1, 2);
```
