# getDeviceRotationRadian (System API)

## Modules to Import

```TypeScript
import { deviceStatus } from '@kit.MultimodalAwarenessKit';
```

## getDeviceRotationRadian

```TypeScript
function getDeviceRotationRadian(): Promise<DeviceRotationRadian>
```

Obtains the device posture data.

The posture data contains the rotation angles of the x, y, and z axes, that is, the Euler angles of the three axes. The definitions of the three axes are the same as those of the device sensor, and the right-handed coordinate system is used. Posture rotation angles are calculated under the z-x-y intrinsic rotation order, and derived by converting quaternions obtained via sensor fusion.

**Since:** 20

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[DeviceRotationRadian](arkts-multimodalawareness-devicestatus-devicerotationradian-i-sys.md)&gt; | The result of device rotation radian. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission check failed. A non-system application uses the system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Function can not work correctly due to limited<br> device capabilities. |
| [32500001](../errorcode-deviceStatus.md#32500001-abnormal-service) | Service exception. |

**Examples**

```TypeScript
import { deviceStatus } from '@kit.MultimodalAwarenessKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
   deviceStatus.getDeviceRotationRadian().then((radian: deviceStatus.DeviceRotationRadian) => {
      console.info('x:' + radian.x + ' y:' + radian.y + ' z:' + radian.z);
   }).catch((err: BusinessError) => {
      console.error('get device rotation radian failed, errmsg:' + err);
   })
} catch (err) {
   console.error('invoke failed, errmsg:' + err)
}
```
