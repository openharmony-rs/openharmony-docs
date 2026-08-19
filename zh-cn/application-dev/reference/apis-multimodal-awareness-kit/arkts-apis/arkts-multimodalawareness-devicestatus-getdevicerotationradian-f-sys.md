# getDeviceRotationRadian（系统接口）

## 导入模块

```TypeScript
import { deviceStatus } from '@kit.MultimodalAwarenessKit';
```

## getDeviceRotationRadian

```TypeScript
function getDeviceRotationRadian(): Promise<DeviceRotationRadian>
```

获取设备的姿态数据。 姿态数据包含x、y、z三轴的姿态旋转角，即三轴的欧拉角，三轴定义与设备sensor定义相同，为右手系。姿态旋转角在ZXY旋转顺序、内旋下计算， <br>通过传感器融合获取的四元数计算得到结果。

**起始版本：** 23

<!--Device-deviceStatus-function getDeviceRotationRadian(): Promise<DeviceRotationRadian>--><!--Device-deviceStatus-function getDeviceRotationRadian(): Promise<DeviceRotationRadian>-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[DeviceRotationRadian](arkts-multimodalawareness-devicestatus-devicerotationradian-i-sys.md)&gt; | 设备旋转弧度结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Function can not work correctly due to limited <br> device capabilities. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission check failed. A non-system application uses the system API. |
| [32500001](../../apis-multimodalawareness-kit/errorcode-deviceStatus.md#32500001-服务异常) | Service exception. |

**示例**

ArkTS-Dyn示例：

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

ArkTS-Sta示例：

```TypeScript
import { deviceStatus } from '@kit.MultimodalAwarenessKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
   deviceStatus.getDeviceRotationRadian().then((radian: deviceStatus.DeviceRotationRadian) => {
      console.info('x:' + radian.x + ' y:' + radian.y + ' z:' + radian.z);
   }).catch((err: BusinessError): void => {
      console.error('get device rotation radian failed, errmsg:' + err);
   })
} catch (err) {
   console.error('invoke failed, errmsg:' + err)
}
```

