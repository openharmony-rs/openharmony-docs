# bindDevice

## bindDevice

```TypeScript
function bindDevice(deviceId: number, onDisconnect: AsyncCallback<number>,
    callback: AsyncCallback<{deviceId: number; remote: rpc.IRemoteObject;}>): void
```

根据queryDevices()返回的设备信息绑定设备。
需要调用[deviceManager.queryDevices()](arkts-driverdevelopment-devicemanager-querydevices-f.md#queryDevices-1)获取设备信息以及device。

**起始版本：** 10

**废弃版本：** 19

**替代接口：** bindDriverWithDeviceId(deviceId:

**需要权限：** ohos.permission.ACCESS_EXTENSIONAL_DEVICE_DRIVER

**系统能力：** SystemCapability.Driver.ExternalDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | number | 是 | 设备ID，通过queryDevices获得。 |
| onDisconnect | AsyncCallback&lt;number&gt; | 是 | 回调函数。当绑定设备断开时，err为undefined，data为解绑的设备ID；否则为错误对象。 |
| callback | AsyncCallback&lt;{deviceId: number; remote: rpc.IRemoteObject;}&gt; | 是 | 回调函数。当绑定设备成功时，err为undefined，<br/>data包含设备ID和绑定设备驱动通信对象；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-The) | The permission check failed. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.<br/>2.Incorrect parameter types.<br/>3.Parameter verification failed. |
| [22900001](../../errorcode-universal.md#22900001-ExternalDeviceManager) | ExternalDeviceManager service exception. |

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

根据queryDevices()返回的设备信息绑定设备。
需要调用[deviceManager.queryDevices](arkts-driverdevelopment-devicemanager-querydevices-f.md#queryDevices-1)获取设备信息以及device。

**起始版本：** 10

**废弃版本：** 19

**替代接口：** bindDriverWithDeviceId(deviceId:

**需要权限：** ohos.permission.ACCESS_EXTENSIONAL_DEVICE_DRIVER

**系统能力：** SystemCapability.Driver.ExternalDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | number | 是 | 设备ID，通过queryDevices获得。 |
| onDisconnect | AsyncCallback&lt;number&gt; | 是 | 回调函数。当绑定设备断开时，err为undefined，data为解绑的设备ID；否则为错误对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;{deviceId: number;&lt;br/&gt;    remote: rpc.IRemoteObject;}&gt; | Promise对象，返回一个包含设备ID和IRemoteObject的对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-The) | The permission check failed. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.<br/>2.Incorrect parameter types.<br/>3.Parameter verification failed. |
| [22900001](../../errorcode-universal.md#22900001-ExternalDeviceManager) | ExternalDeviceManager service exception. |

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

