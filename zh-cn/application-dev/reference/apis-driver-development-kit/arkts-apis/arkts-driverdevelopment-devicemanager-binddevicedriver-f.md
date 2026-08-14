# bindDeviceDriver

## bindDeviceDriver

```TypeScript
function bindDeviceDriver(deviceId: number, onDisconnect: AsyncCallback<number>,
    callback: AsyncCallback<RemoteDeviceDriver>): void
```

根据queryDevices()返回的设备信息绑定设备。 需要调用[deviceManager.queryDevices()](arkts-driverdevelopment-devicemanager-querydevices-f.md#queryDevices)获取设备信息以及device。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** 19

**替代接口：** [bindDriverWithDeviceId](arkts-driverdevelopment-devicemanager-binddriverwithdeviceid-f.md#bindDriverWithDeviceId)(deviceId: long, onDisconnect: AsyncCallback&lt;long&gt;)

**需要权限：** ohos.permission.ACCESS_EXTENSIONAL_DEVICE_DRIVER

<!--Device-deviceManager-function bindDeviceDriver(deviceId: number, onDisconnect: AsyncCallback<number>,    callback: AsyncCallback<RemoteDeviceDriver>): void--><!--Device-deviceManager-function bindDeviceDriver(deviceId: number, onDisconnect: AsyncCallback<number>,    callback: AsyncCallback<RemoteDeviceDriver>): void-End-->

**系统能力：** SystemCapability.Driver.ExternalDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | number | 是 | 设备ID，通过queryDevices获得。 |
| onDisconnect | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;number&gt; | 是 | 回调函数。当绑定设备断开时，err为undefined，data为解绑的设备ID；否则为错误对象。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[RemoteDeviceDriver](arkts-driverdevelopment-devicemanager-remotedevicedriver-i.md)&gt; | 是 | 回调函数。当绑定设备驱动成功时，err为undefined，data为包括设备ID和远程对象的 [RemoteDeviceDriver](arkts-driverdevelopment-devicemanager-remotedevicedriver-i.md#RemoteDeviceDriver)对象；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | The permission check failed. |
| [22900001](../../apis-driverdevelopment-kit/errorcode-deviceManager.md#22900001-扩展外设驱动服务异常或bustype参数错误) | ExternalDeviceManager service exception. |

## 示例

```TypeScript
import { deviceManager } from '@kit.DriverDevelopmentKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 12345678为示例deviceId，应用开发时可通过queryDevices查询到相应设备的deviceId作为入参
  deviceManager.bindDeviceDriver(12345678, (error: BusinessError, data: number) => {
    console.error(`Device is disconnected`);
  }, (error: BusinessError, data: deviceManager.RemoteDeviceDriver) => {
    if (error) {
      console.error(`bindDeviceDriver async fail. Code is ${error.code}, message is ${error.message}`);
      return;
    }
    console.info(`bindDeviceDriver success`);
  });
} catch (error) {
  console.error(`bindDeviceDriver fail. Code is ${error.code}, message is ${error.message}`);
}
```


## bindDeviceDriver

```TypeScript
function bindDeviceDriver(deviceId: number, onDisconnect: AsyncCallback<number>): Promise<RemoteDeviceDriver>
```

根据queryDevices()返回的设备信息绑定设备。 需要调用[deviceManager.queryDevices](arkts-driverdevelopment-devicemanager-querydevices-f.md#queryDevices)获取设备信息以及device。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** 19

**替代接口：** [bindDriverWithDeviceId](arkts-driverdevelopment-devicemanager-binddriverwithdeviceid-f.md#bindDriverWithDeviceId)(deviceId: long, onDisconnect: AsyncCallback&lt;long&gt;)

**需要权限：** ohos.permission.ACCESS_EXTENSIONAL_DEVICE_DRIVER

<!--Device-deviceManager-function bindDeviceDriver(deviceId: number, onDisconnect: AsyncCallback<number>): Promise<RemoteDeviceDriver>--><!--Device-deviceManager-function bindDeviceDriver(deviceId: number, onDisconnect: AsyncCallback<number>): Promise<RemoteDeviceDriver>-End-->

**系统能力：** SystemCapability.Driver.ExternalDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | number | 是 | 设备ID，通过queryDevices获得。 |
| onDisconnect | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;number&gt; | 是 | 回调函数。当绑定设备断开时，err为undefined，data为解绑的设备ID；否则为错误对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[RemoteDeviceDriver](arkts-driverdevelopment-devicemanager-remotedevicedriver-i.md)&gt; | Promise对象，返回RemoteDeviceDriver对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | The permission check failed. |
| [22900001](../../apis-driverdevelopment-kit/errorcode-deviceManager.md#22900001-扩展外设驱动服务异常或bustype参数错误) | ExternalDeviceManager service exception. |

## 示例

```TypeScript
import { deviceManager } from '@kit.DriverDevelopmentKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 12345678为示例deviceId，应用开发时可通过queryDevices查询到相应设备的deviceId作为入参
  deviceManager.bindDeviceDriver(12345678, (error: BusinessError, data: number) => {
    console.error(`Device is disconnected`);
  }).then((data: deviceManager.RemoteDeviceDriver) => {
    console.info(`bindDeviceDriver success, Device_Id is ${data.deviceId}.
    remote is ${data.remote != null ? data.remote.getDescriptor(): "null"}`);
  }, (error: BusinessError) => {
    console.error(`bindDeviceDriver async fail. Code is ${error.code}, message is ${error.message}`);
  });
} catch (error) {
  console.error(`bindDeviceDriver fail. Code is ${error.code}, message is ${error.message}`);
}
```

