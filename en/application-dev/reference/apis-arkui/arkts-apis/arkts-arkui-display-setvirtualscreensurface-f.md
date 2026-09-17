# setVirtualScreenSurface

## Modules to Import

```TypeScript
import { display } from '@kit.ArkUI';
```

## setVirtualScreenSurface

```TypeScript
function setVirtualScreenSurface(screenId: number, surfaceId: string): Promise<void>
```

Sets a surface for a virtual screen. This API uses a promise to return the result.

**Since:** 16

**Required permissions:** ohos.permission.ACCESS_VIRTUAL_SCREEN

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| screenId | number | Yes | Screen ID, which must match the ID of the virtual screen created by calling the [createVirtualScreen()](arkts-arkui-display-createvirtualscreen-f.md) API. This parameter only accepts integer values. |
| surfaceId | string | Yes | ID of the surface bound to the virtual screen. You can specify the ID of an existing surface. The maximum length for this parameter is 4096 bytes. If it goes beyond that, only the first 4096 bytes are used. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [1400001](../errorcode-display.md#1400001-invalid-display-or-screen) | Invalid display or screen. |
| [1400003](../errorcode-display.md#1400003-abnormal-display-manager-service) | This display manager service works abnormally. |

**Examples**

```TypeScript
// Index.ets
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  xComponentController: XComponentController = new XComponentController();

  setVirtualScreenSurface = () => {
    let screenId: number = 1;
    let surfaceId = this.xComponentController.getXComponentSurfaceId();
    display.setVirtualScreenSurface(screenId, surfaceId).then(() => {
      console.info('Succeeded in setting the surface for the virtual screen.');
    }).catch((err: BusinessError) => {
      console.error(`Failed to set the surface for the virtual screen. Code: ${err.code}, message: ${err.message}`);
    });
  }
  build() {
    RelativeContainer() {
      XComponent({
        type: XComponentType.SURFACE,
        controller: this.xComponentController
      })
      Button('setSurface')
        .onClick(() => {
          this.setVirtualScreenSurface();
      }).width('100%')
      .height(20)
    }
    .width('100%')
    .height('100%')
  }
}
```
