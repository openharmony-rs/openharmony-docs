# bindDevice

## 导入模块

```TypeScript
import { deviceManager } from '@kit.DriverDevelopmentKit';
```

## bindDevice

```TypeScript
function bindDevice(deviceId: number, onDisconnect: AsyncCallback<number>,
    callback: AsyncCallback<{deviceId: number; remote: rpc.IRemoteObject;}>): void
```

根据queryDevices()返回的设备信息绑定设备。需要调用[deviceManager.queryDevices()](arkts-driverdevelopment-devicemanager-querydevices-f.md#querydevices-1)获取设备信息以及device。

**起始版本：** 10

**废弃版本：** 19

**替代接口：** bindDriverWithDeviceId(deviceId:

**需要权限：** ohos.permission.ACCESS_EXTENSIONAL_DEVICE_DRIVER

<!--Device-deviceManager-function bindDevice(deviceId: number, onDisconnect: AsyncCallback<number>,
    callback: AsyncCallback<{deviceId: number; remote: rpc.IRemoteObject;}>): void--><!--Device-deviceManager-function bindDevice(deviceId: number, onDisconnect: AsyncCallback<number>,
    callback: AsyncCallback<{deviceId: number; remote: rpc.IRemoteObject;}>): void-End-->

**系统能力：** SystemCapability.Driver.ExternalDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | number | 是 | 设备ID，通过queryDevices获得。 |
| onDisconnect | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<number> | 是 | 回调函数。当绑定设备断开时，err为undefined，data为解绑的设备ID；否则为错误对象。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<{deviceId: number; remote: rpc.IRemoteObject;}> | 是 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The permission check failed. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types.3.Parameter verification failed. |
| [22900001](../../apis-driverdevelopment-kit/errorcode-deviceManager.md#22900001-扩展外设驱动服务异常或bustype参数错误) | ExternalDeviceManager service exception. |

**示例：**

```TypeScript
import { deviceManager } from '@kit.DriverDevelopmentKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { rpc } from '@kit.IPCKit';

interface DataType {
  deviceId : number;
  remote : rpc.IRemoteObject;
}

try {
  // 12345678为示例deviceId，应用开发时可通过queryDevices查询到相应设备的deviceId作为入参
  deviceManager.bindDevice(12345678, (error : BusinessError, data : number) => {
    console.error(`Device is disconnected`);
  }, (error : BusinessError, data : DataType) => {
    if (error) {
      console.error(`bindDevice async fail. Code is ${error.code}, message is ${error.message}`);
      return;
    }
    console.info(`bindDevice success`);
  });
} catch (error) {
  console.error(`bindDevice fail. Code is ${error.code}, message is ${error.message}`);
}

```


## bindDevice

```TypeScript
function bindDevice(deviceId: number, onDisconnect: AsyncCallback<number>): Promise<{deviceId: number;
    remote: rpc.IRemoteObject;}>
```

根据queryDevices()返回的设备信息绑定设备。需要调用[deviceManager.queryDevices](arkts-driverdevelopment-devicemanager-querydevices-f.md#querydevices-1)获取设备信息以及device。

**起始版本：** 10

**废弃版本：** 19

**替代接口：** bindDriverWithDeviceId(deviceId:

**需要权限：** ohos.permission.ACCESS_EXTENSIONAL_DEVICE_DRIVER

<!--Device-deviceManager-function bindDevice(deviceId: number, onDisconnect: AsyncCallback<number>): Promise<{deviceId: number;
    remote: rpc.IRemoteObject;}>--><!--Device-deviceManager-function bindDevice(deviceId: number, onDisconnect: AsyncCallback<number>): Promise<{deviceId: number;
    remote: rpc.IRemoteObject;}>-End-->

**系统能力：** SystemCapability.Driver.ExternalDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | number | 是 | 设备ID，通过queryDevices获得。 |
| onDisconnect | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<number> | 是 | 回调函数。当绑定设备断开时，err为undefined，data为解绑的设备ID；否则为错误对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<{deviceId: number;     remote: rpc.IRemoteObject;}> |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The permission check failed. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types.3.Parameter verification failed. |
| [22900001](../../apis-driverdevelopment-kit/errorcode-deviceManager.md#22900001-扩展外设驱动服务异常或bustype参数错误) | ExternalDeviceManager service exception. |

**示例：**

```TypeScript
import { deviceManager } from '@kit.DriverDevelopmentKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 12345678为示例deviceId，应用开发时可通过queryDevices查询到相应设备的deviceId作为入参
  deviceManager.bindDevice(12345678, (error : BusinessError, data : number) => {
    console.error(`Device is disconnected`);
  }).then(data => {
    console.info(`bindDevice success, Device_Id is ${data.deviceId}.
    remote is ${data.remote != null ? data.remote.getDescriptor() : "null"}`);
  }, (error: BusinessError) => {
    console.error(`bindDevice async fail. Code is ${error.code}, message is ${error.message}`);
  });
} catch (error) {
  console.error(`bindDevice fail. Code is ${error.code}, message is ${error.message}`);
}

```

