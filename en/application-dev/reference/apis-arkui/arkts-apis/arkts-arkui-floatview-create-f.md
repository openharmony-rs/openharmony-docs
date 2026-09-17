# create

## Modules to Import

```TypeScript
import { floatView } from '@kit.ArkUI';
```

## create

```TypeScript
function create(config: FloatViewConfiguration): Promise<FloatViewController>
```

Creates a float view controller. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [FloatViewConfiguration](arkts-arkui-floatview-floatviewconfiguration-i.md) | Yes | Parameter for creating a float view controller. This parameter and the context for constructing this parameter cannot be null or undefined. Otherwise, error code 401 is thrown. Error code 1300016 is thrown for other parameter exceptions. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[FloatViewController](arkts-arkui-floatview-floatviewcontroller-i.md)&gt; | Promise used to return the created float view controller. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible cause: Call the API on unsupported device. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: 1. This window context is abnormal. 2. System error, such as a null pointer, insufficient memory or a JS engine exception. |
| [1300016](../errorcode-window.md#1300016-parameter-verification-error) | Parameter error. Possible cause: Invalid template type. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import { floatView } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  private floatViewController: floatView.FloatViewController | undefined = undefined;
  aboutToAppear(): void {
    // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
    let ctx = this.getUIContext().getHostContext() as common.UIAbilityContext;
    // Create a float view configuration object.
    let config: floatView.FloatViewConfiguration = {
      context: ctx,
      templateType: floatView.FloatViewTemplateType.ROUNDED_RECTANGLE
    };
    try {
      // Create a float view controller.
      floatView.create(config).then((data: floatView.FloatViewController) => {
        this.floatViewController = data;
        console.info(`Succeeded in creating float view controller. Data: ${data}`);
      }).catch((err: BusinessError): void => {
        console.error(`Failed to create float view controller. Cause:${err.code}, message:${err.message}`);
      });
    } catch (e) {
      console.error(`Failed to create float view controller. Cause:${e.code}, message:${e.message}`);
    }
  }
}
```
