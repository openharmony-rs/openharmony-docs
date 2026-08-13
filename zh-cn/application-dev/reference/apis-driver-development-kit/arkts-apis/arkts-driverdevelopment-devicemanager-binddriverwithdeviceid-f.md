# bindDriverWithDeviceId

## bindDriverWithDeviceId

```TypeScript
function bindDriverWithDeviceId(deviceId: long, onDisconnect: AsyncCallback<long>): Promise<RemoteDeviceDriver>
```

根据queryDevices()返回的设备信息绑定设备。使用Promise异步回调。 需要调用[deviceManager.queryDevices](arkts-driverdevelopment-devicemanager-querydevices-f.md#queryDevices)获取设备信息列表。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.ACCESS_DDK_DRIVERS

<!--Device-deviceManager-function bindDriverWithDeviceId(deviceId: long, onDisconnect: AsyncCallback<long>): Promise<RemoteDeviceDriver>--><!--Device-deviceManager-function bindDriverWithDeviceId(deviceId: long, onDisconnect: AsyncCallback<long>): Promise<RemoteDeviceDriver>-End-->

**系统能力：** SystemCapability.Driver.ExternalDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | long | 是 | 设备ID，通过queryDevices获得。 |
| onDisconnect | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;long&gt; | 是 | 回调函数。当绑定设备断开时，err为undefined，data为解绑的设备ID；否则为错误对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[RemoteDeviceDriver](arkts-driverdevelopment-devicemanager-remotedevicedriver-i.md)&gt; | Promise对象，返回RemoteDeviceDriver对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [26300001](../../apis-driverdevelopment-kit/errorcode-deviceManager.md#26300001-扩展外设驱动服务异常) | ExternalDeviceManager service exception. |
| [26300002](../../apis-driverdevelopment-kit/errorcode-deviceManager.md#26300002-驱动服务端不允许驱动客户端绑定) | The driver service does not allow any client to bind. |
| [201](../../errorcode-universal.md#201-权限校验失败) | The permission check failed. |

## 示例

```TypeScript
import { deviceManager } from '@kit.DriverDevelopmentKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 12345678为示例deviceId，应用开发时可通过queryDevices查询到相应设备的deviceId作为入参
  deviceManager.bindDriverWithDeviceId(12345678, (error: BusinessError, data: number) => {
    console.error(`Device is disconnected`);
  }).then((data: deviceManager.RemoteDeviceDriver) => {
    console.info(`bindDriverWithDeviceId success, Device_Id is ${data.deviceId}.
    remote is ${data.remote != null ? data.remote.getDescriptor(): "null"}`);
  }, (error: BusinessError) => {
    console.error(`bindDriverWithDeviceId async fail. Code is ${error.code}, message is ${error.message}`);
  });
} catch (error) {
  console.error(`bindDriverWithDeviceId fail. Code is ${error.code}, message is ${error.message}`);
}
```

