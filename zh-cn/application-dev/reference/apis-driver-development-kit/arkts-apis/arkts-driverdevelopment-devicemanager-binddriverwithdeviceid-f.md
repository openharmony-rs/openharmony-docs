# bindDriverWithDeviceId

## bindDriverWithDeviceId

```TypeScript
function bindDriverWithDeviceId(deviceId: long, onDisconnect: AsyncCallback<long>): Promise<RemoteDeviceDriver>
```

根据queryDevices()返回的设备信息绑定设备。使用Promise异步回调。 需要调用[deviceManager.queryDevices]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_获取设备信息列表。

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.ACCESS_DDK_DRIVERS

<!--Device-deviceManager-function bindDriverWithDeviceId(deviceId: long, onDisconnect: AsyncCallback<long>): Promise<RemoteDeviceDriver>--><!--Device-deviceManager-function bindDriverWithDeviceId(deviceId: long, onDisconnect: AsyncCallback<long>): Promise<RemoteDeviceDriver>-End-->

**系统能力：** SystemCapability.Driver.ExternalDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：long | 是 | 设备ID，通过queryDevices获得。 |
| onDisconnect | ArkTS-Dyn: \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;number&gt;  \_\_\_HTML\_TAG\_USD\_2\_\_\_ArkTS-Sta：\_\_\_MD\_LINK\_USD\_1\_\_\_&lt;long&gt; | 是 | 回调函数。当绑定设备断开时，err为undefined，data为解绑的设备ID；否则为错误对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;RemoteDeviceDriver&gt; | Promise对象，返回RemoteDeviceDriver对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The permission check failed. |
| [26300001](../../apis-driverdevelopment-kit/errorcode-deviceManager.md#26300001-扩展外设驱动服务异常) | ExternalDeviceManager service exception. |
| [26300002](../../apis-driverdevelopment-kit/errorcode-deviceManager.md#26300002-驱动服务端不允许驱动客户端绑定) | The driver service does not allow any client to bind. |

**示例：**

```TypeScript
import { deviceManager } from '@kit.DriverDevelopmentKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 12345678为示例deviceId，应用开发时可通过queryDevices查询到相应设备的deviceId作为入参
  deviceManager.bindDriverWithDeviceId(12345678, (error : BusinessError, data : number) => {
    console.error(`Device is disconnected`);
  }).then((data: deviceManager.RemoteDeviceDriver) => {
    console.info(`bindDriverWithDeviceId success, Device_Id is ${data.deviceId}.
    remote is ${data.remote != null ? data.remote.getDescriptor() : "null"}`);
  }, (error: BusinessError) => {
    console.error(`bindDriverWithDeviceId async fail. Code is ${error.code}, message is ${error.message}`);
  });
} catch (error) {
  console.error(`bindDriverWithDeviceId fail. Code is ${error.code}, message is ${error.message}`);
}
```

