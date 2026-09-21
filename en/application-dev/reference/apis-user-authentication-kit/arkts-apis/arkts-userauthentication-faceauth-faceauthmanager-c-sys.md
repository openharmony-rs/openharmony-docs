# FaceAuthManager (System API)

```TypeScript
class FaceAuthManager
```

Provides APIs for facial authentication management. It provides management features during face enrollment, including setting the **SurfaceId** of the face preview page.

**Since:** 9

**System capability:** SystemCapability.UserIAM.UserAuth.FaceAuth

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { faceAuth } from '@kit.UserAuthenticationKit';
```

## constructor

```TypeScript
constructor()
```

Creates a face authentication manager object.

**Since:** 9

**System capability:** SystemCapability.UserIAM.UserAuth.FaceAuth

**System API:** This is a system API.

**Examples**

```TypeScript
import { faceAuth } from '@kit.UserAuthenticationKit';

let faceAuthManager = new faceAuth.FaceAuthManager();
```

## setSurfaceId

```TypeScript
setSurfaceId(surfaceId: string): void
```

Sets the **SurfaceId** of the face preview page during face enrollment. This API must be used together with [addCredential](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-useridentitymanager-c-sys.md#addcredential). Use the [getXComponentSurfaceId](../../apis-arkui/arkts-components/arkts-arkui-xcomponent-comp-xcomponentcontroller-c.md#getxcomponentsurfaceid) method to obtain the **SurfaceId** of the **XComponent** component to display the face preview page.

**Since:** 9

**Required permissions:** ohos.permission.MANAGE_USER_IDM

**System capability:** SystemCapability.UserIAM.UserAuth.FaceAuth

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| surfaceId | string | Yes | ID of the surface held by [XComponent](../../apis-arkui/arkts-components/arkts-arkui-xcomponent-comp.md#xcomponent). This ID is used to display the face preview page during face enrollment. <br>**Note:** A valid **surfaceId** must be obtained through the [getXComponentSurfaceId](../../apis-arkui/arkts-components/arkts-arkui-xcomponent-comp-xcomponentcontroller-c.md#getxcomponentsurfaceid) method after **XComponent** initialization. An invalid **surfaceId** may cause the preview page to fail to display or the API call to fail. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied. Called by non-system application. |
| [12700001](../errorcode-useriam.md#12700001-facial-authentication-service-unavailable) | The service is unavailable. |

**Examples**

```TypeScript
import { faceAuth } from '@kit.UserAuthenticationKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain this surfaceId through the XComponentController.getXComponentSurfaceId() method from the XComponent component. This is only an example.
let surfaceId = '123456';
let faceManager = new faceAuth.FaceAuthManager();
try {
  faceManager.setSurfaceId(surfaceId);
  console.info('set surface id successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`set surface id failed, Code is ${err?.code}, message is ${err?.message}`);
}
```
