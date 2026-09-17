# queryDriverInfo（系统接口）

## 导入模块

```TypeScript
import { deviceManager } from '@kit.DriverDevelopmentKit';
```

## queryDriverInfo

```TypeScript
function queryDriverInfo(driverUid?: string): Array<Readonly<DriverInfo>>
```

查询扩展外设驱动详细信息列表。如果没有设备接入，那么将会返回一个空的列表。

**起始版本：** 12

**需要权限：** ohos.permission.ACCESS_EXTENSIONAL_DEVICE_DRIVER

**系统能力：** SystemCapability.Driver.ExternalDevice

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| driverUid | string | 否 | 驱动UID，通过[queryDeviceInfo](arkts-driverdevelopment-devicemanager-querydeviceinfo-f-sys.md)返回的设备信息获得。如果不传入驱动UID，则默认获取所有的驱动信息；如果传入了UID但不存在对应的驱动，则会返回空列表。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;Readonly&lt;[DriverInfo](arkts-driverdevelopment-devicemanager-driverinfo-i-sys.md)&gt;&gt; | 扩展外设驱动详细信息列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The permission check failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied. A non-system application cannot call a system API. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Incorrect parameter types. |
| [26300001](../errorcode-deviceManager.md#26300001-扩展外设驱动服务异常) | ExternalDeviceManager service exception. |

**示例**

```TypeScript
import { deviceManager } from '@kit.DriverDevelopmentKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // driver-12345为示例driverUid，应用开发时可通过queryDeviceInfo查询到相应设备匹配到的驱动的driverUid作为入参
  let driverInfos: Array<deviceManager.DriverInfo> = deviceManager.queryDriverInfo('driver-12345');
  for (let item of driverInfos) {
    console.info(`driver name is ${item.driverName}`);
  }
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`Failed to query driver info. Code is ${err.code}, message is ${err.message}`);
}
```
