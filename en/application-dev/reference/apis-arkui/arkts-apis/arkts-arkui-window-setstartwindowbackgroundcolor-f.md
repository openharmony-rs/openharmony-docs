# setStartWindowBackgroundColor

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## setStartWindowBackgroundColor

```TypeScript
function setStartWindowBackgroundColor(moduleName: string, abilityName: string, color: ColorMetrics): Promise<void>
```

Sets the background color of the splash screen of the UIAbility based on the specified module name and ability name within the same bundle name. This API uses a promise to return the result.

This API takes effect for all processes of the same bundle name, for example, in multi-instance or clone scenarios.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| moduleName | string | Yes | Module name of the UIAbility. The value is a string of 0 to 200 bytes. Only the module names within the same application can be set. The module name is specified in the **name** field of the [module.json5 file](../../../quick-start/module-configuration-file.md#tags-in-the-configuration-file). |
| abilityName | string | Yes | Name of the UIAbility. The value is a string of 0 to 200 bytes. Only the ability names within the same application can be set. The UIAbility name is specified in the **name** field under [abilities in the module.json5 file](../../../quick-start/module-configuration-file.md#abilities). |
| color | [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md) | Yes | Background color of the splash screen. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.function setStartWindowBackgroundColor can not work correctly due to limited device capabilities. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. Possible cause: Internal task error. |
| [1300016](../errorcode-window.md#1300016-parameter-verification-error) | Parameter error. Possible cause: Parameter exceeds the allowed length. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { ColorMetrics, window } from '@kit.ArkUI';

try {
  let promise = window.setStartWindowBackgroundColor("entry", "EntryAbility", ColorMetrics.numeric(0xff000000));
  promise.then(() => {
    console.info('Succeeded in setting the starting window color.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to set the starting window color. Cause code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to set the starting window color. Cause code: ${exception.code}, message: ${exception.message}`);
}
```
