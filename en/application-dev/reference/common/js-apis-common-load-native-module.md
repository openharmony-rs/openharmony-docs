# loadNativeModule (Synchronously and Dynamically Loading a System Library)

This module provides the capability of synchronously and dynamically loading a system library.

> **NOTE**
>
> The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module can be used only in the stage model.

## loadNativeModule

loadNativeModule(moduleName: string): Object

The `loadNativeModule` API is used to synchronously dynamically load a native module, that is, load the required module on demand. Using this API increases the time for loading the .so file. You need to evaluate the impact on the functionality.

> **NOTE**
>
> The module name loaded by loadNativeModule refers to the name in the `dependencies` field of the `oh-package.json5` file of the dependency party.
>
> The loadNativeModule API can load native modules only in the UI main thread.
>
> Dependencies must be configured when constant strings or variable expressions are used as parameters of this API.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name   | Type    | Mandatory     | Description |
| ----- | -------- | ----  | ---------------- |
| moduleName | string | Yes    | Name of the module to load.|

**Return value**

| Type| Description|
| -------- | -------- |
| Object | Default export of the native module.|

**Error codes**

For details about the error codes, see Common Error Codes and Language Foundation Library Error Codes.

| ID| Error Message|
| -------- | -------- |
| 401 | The parameter check failed.|
| 10200301 | Loading native module failed.|

**Scenarios supported by loadNativeModule**

| Scenario           | Example          | 
| :------------- | :----------------------------- | 
| System library module       | Load **@ohos.** or **@system.**.       | 
| Native module in an application| Load **libNativeLibrary.so**.|

**Example 1**: Load a system library module using a HAP.

```js
let hilog: ESObject = loadNativeModule("@ohos.hilog");
hilog.info(0, "testTag", "loadNativeModule ohos.hilog success");
```

**Example 2**: Loading a Native Library to a HAP

The content of the index.d.ts file of libentry.so is as follows:

```javascript
//index.d.ts
export const add: (a: number, b: number) => number;
```

1. Configure the dependencies item in the module-level `oh-package.json5` file when loading the local .so library. For details, see https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-oh-package-json5#zh-cn_topic_0000001792256137_oh-packagejson5-%E5%AD%97%E6%AE%B5%E8%AF%B4%E6%98%8E.

```json
{
  "dependencies": {
    "libentry.so": "file:./src/main/cpp/types/libentry"
  }
}
```

2. Configure the module-level `build-profile.json5` file. For details, see https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-hvigor-build-profile.

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

3. Use `loadNativeModule` to load `libentry.so` and call the `add` function.

```js
let module: ESObject = loadNativeModule("libentry.so");
let sum: number = module.add(1, 2);
```
