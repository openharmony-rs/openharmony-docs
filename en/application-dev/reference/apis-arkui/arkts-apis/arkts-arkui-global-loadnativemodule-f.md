# loadNativeModule

## Modules to Import

```TypeScript
```

## loadNativeModule

```TypeScript
export declare function loadNativeModule(moduleName: string): Object
```

The **loadNativeModule** API is used to synchronously and dynamically load a native module, that is, only load the required module at a time. Using this API increases the time for loading the .so file. You need to evaluate the impact on the functionality.

> **NOTE:** 
> 
> The name of the module loaded by **loadNativeModule** is the name provided in **dependencies** in the
> **oh-package.json5** file of the dependency.
> 
> **loadNativeModule** can be used only to load native modules in the UI main thread.
> 
> Dependencies must be configured for the API call regardless of whether the parameter is a constant string or
> variable expression.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| moduleName | string | Yes | Name of the module to load. |

**Return value:**

| Type | Description |
| --- | --- |
| Object | Default export of the native module. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. |
| [10200301](../../apis-arkts/errorcode-utils.md#10200301-failed-to-load-the-native-module) | Loading native module failed. |
