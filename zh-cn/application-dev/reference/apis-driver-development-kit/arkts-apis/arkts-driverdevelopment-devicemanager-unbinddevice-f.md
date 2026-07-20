# unbindDevice

## 导入模块

```TypeScript
import { deviceManager } from '@kit.DriverDevelopmentKit';
```

<a id="unbinddevice"></a>
## unbindDevice

```TypeScript
function unbindDevice(deviceId: number, callback: AsyncCallback<number>): void
```

解除设备绑定。

**起始版本：** 10

**废弃版本：** 19

**替代接口：** [unbindDriverWithDeviceId(deviceId:](arkts-driverdevelopment-devicemanager-unbinddriverwithdeviceid-f.md#unbinddriverwithdeviceid-1)

**需要权限：** ohos.permission.ACCESS_EXTENSIONAL_DEVICE_DRIVER

<!--Device-deviceManager-function unbindDevice(deviceId: number, callback: AsyncCallback<number>): void--><!--Device-deviceManager-function unbindDevice(deviceId: number, callback: AsyncCallback<number>): void-End-->

**系统能力：** SystemCapability.Driver.ExternalDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | number | 是 | 设备ID，通过queryDevices获得。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。当解绑设备成功时，err为undefined，data为设备ID；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The permission check failed. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [22900001](../../apis-driverdevelopment-kit/errorcode-deviceManager.md#22900001-扩展外设驱动服务异常或bustype参数错误) | ExternalDeviceManager service exception. |

**示例：**

```TypeScript
import { deviceManager } from '@kit.DriverDevelopmentKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 12345678为示例deviceId，应用开发时可通过queryDevices查询到相应设备的deviceId作为入参
  deviceManager.unbindDevice(12345678, (error : BusinessError, data : number) => {
    if (error) {
      console.error(`unbindDevice async fail. Code is ${error.code}, message is ${error.message}`);
      return;
    }
    console.info(`unbindDevice success`);
  });
} catch (error) {
  console.error(`unbindDevice fail. Code is ${error.code}, message is ${error.message}`);
}

```


<a id="unbinddevice-1"></a>
## unbindDevice

```TypeScript
function unbindDevice(deviceId: number): Promise<number>
```

解除设备绑定。

**起始版本：** 10

**废弃版本：** 19

**替代接口：** [unbindDriverWithDeviceId(deviceId:](arkts-driverdevelopment-devicemanager-unbinddriverwithdeviceid-f.md#unbinddriverwithdeviceid-1)

**需要权限：** ohos.permission.ACCESS_EXTENSIONAL_DEVICE_DRIVER

<!--Device-deviceManager-function unbindDevice(deviceId: number): Promise<number>--><!--Device-deviceManager-function unbindDevice(deviceId: number): Promise<number>-End-->

**系统能力：** SystemCapability.Driver.ExternalDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | number | 是 | 设备ID，通过queryDevices获得。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回解除绑定的设备ID。 |

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
  deviceManager.unbindDevice(12345678).then((data : number) => {
    console.info(`unbindDevice success, Device_Id is ${data}.`);
  }, (error : BusinessError) => {
    console.error(`unbindDevice async fail. Code is ${error.code}, message is ${error.message}`);
  });
} catch (error) {
  console.error(`unbindDevice fail. Code is ${error.code}, message is ${error.message}`);
}

```

