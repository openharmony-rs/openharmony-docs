# releaseDeviceManager

## 导入模块

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
```

<a id="releasedevicemanager"></a>
## releaseDeviceManager

```TypeScript
function releaseDeviceManager(deviceManager: DeviceManager): void
```

设备管理实例不再使用后，通过该方法释放DeviceManager实例。

**起始版本：** 10

<!--Device-distributedDeviceManager-function releaseDeviceManager(deviceManager: DeviceManager): void--><!--Device-distributedDeviceManager-function releaseDeviceManager(deviceManager: DeviceManager): void-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceManager | [DeviceManager](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md) | 是 | 设备管理器对象实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| [11600101](../../apis-distributedservice-kit/errorcode-device-manager.md#11600101-服务调用异常) | Failed to execute the function. |

**示例：**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 创建设备管理实例
  let dmInstance = distributedDeviceManager.createDeviceManager('ohos.samples.jsHelloWorld');
  // 释放设备管理实例
  distributedDeviceManager.releaseDeviceManager(dmInstance);
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to release device manager. Code: ${error.code}, message: ${error.message}`);
}

```

