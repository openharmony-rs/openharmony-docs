# hasRight

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
import { serialManager } from '@kit.BasicServicesKit';
```

## hasRight

```TypeScript
function hasRight(deviceName: string): boolean
```

判断是否有权访问该设备。 如果应用有权访问设备则返回true；无权访问设备则返回false。

**起始版本：** 23

<!--Device-usbManager-function hasRight(deviceName: string): boolean--><!--Device-usbManager-function hasRight(deviceName: string): boolean-End-->

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceName | string | 是 | 设备名称，来自[getDevices](arkts-basicservices-usbmanager-getdevices-f.md)获取的设备列表USBDevice的name。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示有访问设备的权限，false表示没有访问设备的权限。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  <br>1.Mandatory parameters are left unspecified.  <br>2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |

**示例**

```TypeScript
async function hasRight(): Promise<boolean> {
  let devicesList: Array<usbManager.USBDevice> = usbManager.getDevices();
  if (!devicesList || devicesList.length == 0) {
    console.info(`device list is empty`);
    return false;
  }

  let device: usbManager.USBDevice = devicesList?.[0];
  let rightResult = await usbManager.requestRight(device.name);
  if (!rightResult) {
    console.error(`request right failed`);
    return;
  }
  let right: boolean = usbManager.hasRight(device.name);
  console.info(`${right}`);
  return right;
}
```

