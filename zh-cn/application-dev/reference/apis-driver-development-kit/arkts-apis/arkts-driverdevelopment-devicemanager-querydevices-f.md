# queryDevices

## 导入模块

```TypeScript
import { deviceManager } from '@kit.DriverDevelopmentKit';
```

## queryDevices

```TypeScript
function queryDevices(busType?: number): Array<Readonly<Device>>
```

获取接入主设备的外部设备列表。如果没有设备接入，那么将会返回一个空的列表。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_EXTENSIONAL_DEVICE_DRIVER

<!--Device-deviceManager-function queryDevices(busType?: int): Array<Readonly<Device>>--><!--Device-deviceManager-function queryDevices(busType?: int): Array<Readonly<Device>>-End-->

**系统能力：** SystemCapability.Driver.ExternalDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| busType | number | 否 | 由[BusType](arkts-driverdevelopment-devicemanager-bustype-e.md)约定的设备总线类型，不填则查找所有类型设备。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;Readonly&lt;Device&gt;&gt; | 设备信息列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The permission check failed. |
| [22900001](../../apis-driverdevelopment-kit/errorcode-deviceManager.md#22900001-扩展外设驱动服务异常或bustype参数错误) | ExternalDeviceManager service exception or busType parameter error. |

**示例：**

```TypeScript
import { deviceManager } from '@kit.DriverDevelopmentKit';

try {
  let devices : Array<deviceManager.Device> = deviceManager.queryDevices(deviceManager.BusType.USB);
  for (let item of devices) {
    let device : deviceManager.USBDevice = item as deviceManager.USBDevice;
    console.info(`Device id is ${device.deviceId}`);
  }
} catch (error) {
  console.error(`Failed to query device. Code is ${error.code}, message is ${error.message}`);
}

```

