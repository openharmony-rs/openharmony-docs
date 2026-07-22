# createDeviceManager

## 导入模块

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
```

## createDeviceManager

```TypeScript
function createDeviceManager(bundleName: string): DeviceManager
```

创建一个设备管理实例。设备管理实例是分布式设备管理方法的调用入口。用于获取可信设备和本地设备的相关信息。

**起始版本：** 10

<!--Device-distributedDeviceManager-function createDeviceManager(bundleName: string): DeviceManager--><!--Device-distributedDeviceManager-function createDeviceManager(bundleName: string): DeviceManager-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 指示应用程序的Bundle名称。长度范围1~255字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DeviceManager](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md) | 返回设备管理器对象实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter type;3. Parameter verification failed. |

**示例：**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 创建设备管理实例
  let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to create device manager. Code: ${error.code}, message: ${error.message}`);
}

```

