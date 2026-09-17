# createVirtualScreen

## Modules to Import

```TypeScript
import { display } from '@kit.ArkUI';
```

## createVirtualScreen

```TypeScript
function createVirtualScreen(config: VirtualScreenConfig): Promise<number>
```

Creates a virtual screen. This API uses a promise to return the result.

**Since:** 16

**Required permissions:** ohos.permission.ACCESS_VIRTUAL_SCREEN

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [VirtualScreenConfig](arkts-arkui-display-virtualscreenconfig-i.md) | Yes | Virtual screen parameters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the screen ID of the created virtual screen. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [1400001](../errorcode-display.md#1400001-invalid-display-or-screen) | Invalid display or screen. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let config: display.VirtualScreenConfig = {
  name: 'screen01',
  width: 1080,
  height: 2340,
  density: 2,
  surfaceId: '',
  supportsFocus: false
};

display.createVirtualScreen(config).then((screenId: number) => {
  console.info(`Succeeded in creating the virtual screen. ScreenId: ${screenId}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to create the virtual screen. Code: ${err.code}, message: ${err.message}`);
});
```
