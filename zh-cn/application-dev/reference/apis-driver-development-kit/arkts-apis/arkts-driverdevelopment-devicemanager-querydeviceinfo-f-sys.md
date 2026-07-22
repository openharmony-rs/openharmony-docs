# queryDeviceInfo（系统接口）

## 导入模块

```TypeScript
import { deviceManager } from '@kit.DriverDevelopmentKit';
```

## queryDeviceInfo

```TypeScript
function queryDeviceInfo(deviceId?: number): Array<Readonly<DeviceInfo>>
```

查询扩展外设详细信息列表。如果没有设备接入，那么将会返回一个空的列表。

**起始版本：** 12

**需要权限：** ohos.permission.ACCESS_EXTENSIONAL_DEVICE_DRIVER

<!--Device-deviceManager-function queryDeviceInfo(deviceId?: long): Array<Readonly<DeviceInfo>>--><!--Device-deviceManager-function queryDeviceInfo(deviceId?: long): Array<Readonly<DeviceInfo>>-End-->

**系统能力：** SystemCapability.Driver.ExternalDevice

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | number | 否 | 设备ID，通过[queryDevices](arkts-driverdevelopment-devicemanager-querydevices-f.md#querydevices)获得。如果不传入设备ID，则默认获取所有的设备信息；如果没有外接设备，且没有传入设备ID则会返回空数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;Readonly&lt;DeviceInfo&gt;&gt; | 扩展外设详细信息列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The permission check failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied. A non-system application cannot call a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Incorrect parameter types. |
| [26300001](../../apis-driverdevelopment-kit/errorcode-deviceManager.md#26300001-扩展外设驱动服务异常) | ExternalDeviceManager service exception. |

**示例：**

```TypeScript
import { deviceManager } from '@kit.DriverDevelopmentKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 12345678为示例deviceId，应用开发时可通过queryDevices查询到相应设备的deviceId作为入参
  let deviceInfos : Array<deviceManager.DeviceInfo> = deviceManager.queryDeviceInfo(12345678);
  for (let item of deviceInfos) {
    console.info(`Device id is ${item.deviceId}`);
  }
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`Failed to query device info. Code is ${err.code}, message is ${err.message}`);
}

```

