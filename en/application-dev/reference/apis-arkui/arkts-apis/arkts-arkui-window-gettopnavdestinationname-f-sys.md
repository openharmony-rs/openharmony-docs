# getTopNavDestinationName (System API)

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## getTopNavDestinationName

```TypeScript
function getTopNavDestinationName(windowId: number): Promise<string>
```

Obtains the name of [NavDestination](../arkts-components/arkts-arkui-navdestination-comp.md#navdestination) in the current top-level [Navigation](../arkts-components/arkts-arkui-navigation-comp.md#navigation) component of the specified foreground window. This API uses a promise to return the result.

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| windowId | number | Yes | ID of the window to query. This parameter must be an integer greater than 0. If it is less than or equal to 0, error code 1300016 is returned. If the specified window does not exist or is not in the foreground, error code 1300002 is returned. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the [NavDestination](../arkts-components/arkts-arkui-navdestination-comp.md#navdestination) name obtained. <br>If there are nested [Navigation](../arkts-components/arkts-arkui-navigation-comp.md#navigation) components or multiple [Navigation](../arkts-components/arkts-arkui-navigation-comp.md#navigation) components on the current page, the information of the most recently created [Navigation](../arkts-components/arkts-arkui-navigation-comp.md#navigation) component is queried. <br>If the page does not have the [Navigation](../arkts-components/arkts-arkui-navigation-comp.md#navigation) component or the [Navigation](../arkts-components/arkts-arkui-navigation-comp.md#navigation) component does not have [NavDestination](../arkts-components/arkts-arkui-navdestination-comp.md#navdestination), an empty string is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed, non-system application uses system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |
| [1300016](../errorcode-window.md#1300016-parameter-verification-error) | Parameter error. Possible cause: 1. Invalid parameter range. |

**Examples**

```TypeScript
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let windowId = 10;
  let promise = window.getTopNavDestinationName(windowId);
  promise.then((data) => {
    console.info(`Succeeded, data: ${data}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed, cause code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed, exception code: ${exception.code}, message: ${exception.message}`);
}
```
