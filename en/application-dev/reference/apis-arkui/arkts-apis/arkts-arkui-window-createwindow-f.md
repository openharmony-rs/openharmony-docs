# createWindow

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## createWindow

```TypeScript
function createWindow(config: Configuration, callback: AsyncCallback<Window>): void
```

Creates a child window or system window. This API uses an asynchronous callback to return the result.

In non-[freeform window](../../../windowmanager/window-terminology.md#freeform-window) mode, the child window created uses an [immersive layout](../../../windowmanager/window-terminology.md#immersive-layout) by default.

In freeform window mode, the child window created uses an immersive layout when [decorEnabled](arkts-arkui-window-configuration-i.md) is set to **false**, and it uses a non-immersive layout when this parameter is set to **true**.

**Since:** 9

**Required permissions:** 
- API version 12 and later: ohos.permission.SYSTEM_FLOAT_WINDOW
- API versions 9 to 11: N/A

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [Configuration](arkts-arkui-window-configuration-i.md) | Yes | Parameters for window creation. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Window](arkts-arkui-window-window-i.md)&gt; | Yes | Callback used to return the window created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.createWindow cannot work correctly due to limited device capabilities.<br>**Applicable version:** 12 and later |
| [1300001](../errorcode-window.md#1300001-repeated-operation) | Repeated operation. Possible cause: The window has been created and cannot be created again. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: Invalid parent window type, parent window cannot be a subWindow.<br>**Applicable version:** 12 and later |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: The window type in the configuration is invalid.<br>**Applicable version:** 12 and later |
| [1300006](../errorcode-window.md#1300006-abnormal-window-context) | This window context is abnormal. |
| [1300008](../errorcode-window.md#1300008-display-device-exception) | The display device is abnormal.<br>**Applicable version:** 9 - 16 |
| [1300009](../errorcode-window.md#1300009-invalid-parent-window) | The parent window is invalid. |

**Examples**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage): void {
    let windowClass: window.Window | undefined = undefined;
    let config: window.Configuration = {
      name: "test",
      windowType: window.WindowType.TYPE_DIALOG,
      ctx: this.context
    };
    try {
      window.createWindow(config, (err: BusinessError, data) => {
        const errCode: number = err.code;
        if (errCode) {
          console.error(`Failed to create the window. Cause code: ${err.code}, message: ${err.message}`);
          return;
        }
        windowClass = data;
        console.info('Succeeded in creating the window. Data: ' + JSON.stringify(data));
        windowClass.resize(500, 1000);
      });
    } catch (exception) {
      console.error(`Failed to create the window. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
}
```

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage): void {
    let windowClass: window.Window | undefined = undefined;
    let config: window.Configuration = {
      name: "test",
      windowType: window.WindowType.TYPE_DIALOG,
      ctx: this.context
    };
    try {
      window.createWindow(config).then((value:window.Window) => {
        console.info('Succeeded in creating the window. Data: ' + JSON.stringify(value));
        windowClass = value;
        windowClass.resize(500, 1000);
      }).catch((err:BusinessError)=> {
        console.error(`Failed to create the window. Cause code: ${err.code}, message: ${err.message}`);
      });
    } catch (exception) {
      console.error(`Failed to create the window. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
}
```


## createWindow

```TypeScript
function createWindow(config: Configuration): Promise<Window>
```

Creates a child window or system window. This API uses a promise to return the result.

In non-[freeform window](../../../windowmanager/window-terminology.md#freeform-window) mode, the child window created uses an [immersive layout](../../../windowmanager/window-terminology.md#immersive-layout) by default.

In freeform window mode, the child window created uses an immersive layout when [decorEnabled](arkts-arkui-window-configuration-i.md) is set to **false**, and it uses a non-immersive layout when this parameter is set to **true**.

**Since:** 9

**Required permissions:** 
- API version 12 and later: ohos.permission.SYSTEM_FLOAT_WINDOW
- API versions 9 to 11: N/A

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [Configuration](arkts-arkui-window-configuration-i.md) | Yes | Parameters for window creation. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Window](arkts-arkui-window-window-i.md)&gt; | Promise used to return the window created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.createWindow cannot work correctly due to limited device capabilities.<br>**Applicable version:** 12 and later |
| [1300001](../errorcode-window.md#1300001-repeated-operation) | Repeated operation. Possible cause: The window has been created and cannot be created again. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. Possible cause: Invalid parent window type, parent window cannot be a subWindow.<br>**Applicable version:** 12 and later |
| [1300004](../errorcode-window.md#1300004-unauthorized-operation) | Unauthorized operation. Possible cause: The window type in the configuration is invalid.<br>**Applicable version:** 12 and later |
| [1300006](../errorcode-window.md#1300006-abnormal-window-context) | This window context is abnormal. |
| [1300008](../errorcode-window.md#1300008-display-device-exception) | The display device is abnormal.<br>**Applicable version:** 9 - 16 |
| [1300009](../errorcode-window.md#1300009-invalid-parent-window) | The parent window is invalid. |

**Examples**

See [createWindow](#createwindow)
