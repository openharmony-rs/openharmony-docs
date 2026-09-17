# loadNativeModule (Synchronously and Dynamically Loading a System Library)

<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @yao_dashuai-->
<!--Designer: @yao_dashuai-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=c7b0ff87b548f85547c88080131a6da45e73ec82 translatedAt=2026-08-27T03:50:27.217Z pushedAt=2026-08-27T07:02:18.984Z -->

This module provides the capability of synchronously and dynamically loading a system library.

> **NOTE**
>
> The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.


## loadNativeModule

loadNativeModule(moduleName: string): Object

The **loadNativeModule** API is used to synchronously and dynamically load a native module, so as to load the required module on demand.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name   | Type    | Mandatory     | Description |
| ----- | -------- | ----  | ---------------- |
| moduleName | string | Yes    | Name of the module to load.|

**Return value**

| Type| Description|
| -------- | -------- |
| Object | Default export of the native module, which must be received using the ESObject type of ArkTS. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Utils Error Codes](../apis-arkts/errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 401 | The parameter check failed.|
| 10200301 | Loading native module failed.|

**Scenarios supported by loadNativeModule**

| Scenario           | Example          | 
| :------------- | :----------------------------- | 
| System library module       | Load **@ohos.** or **@system.**.       | 
| Native module in an application | Load **libNativeLibrary.so**.|

### Usage Notes

- **loadNativeModule** supports loading a native module only in the UI main thread of the Stage model.

- Using this API increases the loading time of the .so file. Evaluate its impact on app performance and functionality before use.

- Regardless of whether the **moduleName** parameter uses a constant string or a variable expression, the dependency must be configured in the **dependencies** field of the module-level **oh-package.json5** file of the dependent party. The value of **moduleName** is the dependency name declared in the **dependencies** field.

- When loading a native module in an app, you also need to configure the module name in the **buildOption.arkOptions.runtimeOnly.packages** field of the module-level **build-profile.json5** file of the dependent party. This name must be consistent with the dependency name in the **oh-package.json5** file and the input parameter of **loadNativeModule**.

- The return value type declared by the API is **Object**. When calling the API, use a variable of the **ESObject** type to receive the return value so that you can call the methods exported by the native module. If you use a variable of the **Object** type to receive the return value, calling the methods may cause a compilation error.

Take loading **libentry.so** as an example. The following configurations are required.

1. Configure the **dependencies** field in the module-level **oh-package.json5** file. For details, see [Module-level oh-package.json5](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-oh-package-json5#en-us_topic_0000001792256137_oh-packagejson5-%E5%AD%97%E6%AE%B5%E8%AF%B4%E6%98%8E).

    ```json
    {
      "dependencies": {
        "libentry.so": "file:./src/main/cpp/types/libentry"
      }
    }
    ```

2. Configure the **runtimeOnly.packages** field in the module-level **build-profile.json5** file. For details, see [Module-level build-profile.json5 File](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-hvigor-build-profile).

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

**Example 1**: Loading a System Library Module to a HAP

```js
let hilog: ESObject = loadNativeModule("@ohos.hilog");
hilog.info(0, "testTag", "loadNativeModule ohos.hilog success");
```

**Example 2**: Loading a Native Library to a HAP

The **index.d.ts** file of **libentry.so** is as follows:

```javascript
//index.d.ts
export const add: (a: number, b: number) => number;
```

After completing the dependency configuration in [Usage Notes](#usage-notes), use **loadNativeModule** to load **libentry.so** and call the **add** function.

```js
let module: ESObject = loadNativeModule("libentry.so");
let sum: number = module.add(1, 2);
```