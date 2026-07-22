# unbindDriverWithDeviceId

## 导入模块

```TypeScript
import { deviceManager } from '@kit.DriverDevelopmentKit';
```

## unbindDriverWithDeviceId

```TypeScript
function unbindDriverWithDeviceId(deviceId: number): Promise<number>
```

解除设备绑定。使用Promise异步回调。

**起始版本：** 19

**需要权限：** ohos.permission.ACCESS_DDK_DRIVERS

<!--Device-deviceManager-function unbindDriverWithDeviceId(deviceId: long): Promise<int>--><!--Device-deviceManager-function unbindDriverWithDeviceId(deviceId: long): Promise<int>-End-->

**系统能力：** SystemCapability.Driver.ExternalDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | number | 是 | 设备ID，通过[queryDevices](arkts-driverdevelopment-devicemanager-querydevices-f.md#querydevices)获得。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回解除绑定的设备ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The permission check failed. |
| [26300001](../../apis-driverdevelopment-kit/errorcode-deviceManager.md#26300001-扩展外设驱动服务异常) | ExternalDeviceManager service exception. |
| [26300003](../../apis-driverdevelopment-kit/errorcode-deviceManager.md#26300003-驱动客户端未绑定任何驱动服务端) | There is no binding relationship. |

**示例：**

```TypeScript
import { deviceManager } from '@kit.DriverDevelopmentKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 12345678为示例deviceId，应用开发时可通过queryDevices查询到相应设备的deviceId作为入参
  deviceManager.unbindDriverWithDeviceId(12345678).then((data : number) => {
    console.info(`unbindDriverWithDeviceId success, Device_Id is ${data}.`);
  }, (error : BusinessError) => {
    console.error(`unbindDriverWithDeviceId async fail. Code is ${error.code}, message is ${error.message}`);
  });
} catch (error) {
  console.error(`unbindDriverWithDeviceId fail. Code is ${error.code}, message is ${error.message}`);
}

```

