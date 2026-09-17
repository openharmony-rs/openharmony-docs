# getStatusMonitor (System API)

## Modules to Import

```TypeScript
import { companionDeviceAuth } from '@kit.UserAuthenticationKit';
```

## getStatusMonitor

```TypeScript
function getStatusMonitor(localUserId: number): StatusMonitor
```

Obtains the status monitor. This API is used to obtain the status monitor object of a specified user. The object can be used to query and subscribe to the template status, continuous authentication status, and available device status of the companion device.

**Since:** 23

**Required permissions:** ohos.permission.USE_USER_IDM

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| localUserId | number | Yes | Local user ID. User ID on the primary device, which is a positive integer greater than or equal to 0. It is used to obtain the status monitor of the companion device corresponding to the user. |

**Return value:**

| Type | Description |
| --- | --- |
| [StatusMonitor](arkts-userauthentication-companiondeviceauth-statusmonitor-i-sys.md) | Status monitor object. It can be used to query the template status ([getTemplateStatus](arkts-userauthentication-companiondeviceauth-statusmonitor-i-sys.md#gettemplatestatus)), subscribe to template changes ([onTemplateChange](arkts-userauthentication-companiondeviceauth-statusmonitor-i-sys.md#ontemplatechange)), subscribe to available device status changes ([onAvailableDeviceChange](arkts-userauthentication-companiondeviceauth-statusmonitor-i-sys.md#onavailabledevicechange)), and subscribe to continuous authentication status changes ([onContinuousAuthChange](arkts-userauthentication-companiondeviceauth-statusmonitor-i-sys.md#oncontinuousauthchange)). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [32600001](../errorcode-useriam.md#32600001-system-service-not-working-properly) | The system service is not working properly. Please try again later. |
| [32600002](../errorcode-useriam.md#32600002-template-not-found) | The local user is not found. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { userAuth } from '@kit.UserAuthenticationKit';

const localUserId = 100;
try {
  const statusMonitor = companionDeviceAuth.getStatusMonitor(localUserId);
  const continuousAuthParam: companionDeviceAuth.ContinuousAuthParam = {
    templateId: new Uint8Array([])
  };
  const handler = (isAuthPassed: boolean, authTrustLevel?: userAuth.AuthTrustLevel): void => {
    console.info('continuous auth changed');
    console.info(`isAuthPassed: ${isAuthPassed}`);
    if (authTrustLevel !== undefined) {
      console.info(`authTrustLevel: ${authTrustLevel}`);
    }
  };

  statusMonitor.onContinuousAuthChange(continuousAuthParam, handler);
  statusMonitor.offContinuousAuthChange(handler);
} catch (error) {
  const message = (error as BusinessError).message;
  console.error(`error has been captured: message:${message}`);
}
```
