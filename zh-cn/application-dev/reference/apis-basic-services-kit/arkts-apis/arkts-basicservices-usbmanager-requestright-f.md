# requestRight

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
import { serialManager } from '@kit.BasicServicesKit';
```

## requestRight

```TypeScript
function requestRight(deviceName: string): Promise<boolean>
```

请求应用访问设备的临时权限。使用Promise异步回调返回结果。系统应用默认拥有访问设备权限，无需调用此接口。

**起始版本：** 23

<!--Device-usbManager-function requestRight(deviceName: string): Promise<boolean>--><!--Device-usbManager-function requestRight(deviceName: string): Promise<boolean>-End-->

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceName | string | 是 | 设备名称，来自[getDevices](arkts-basicservices-usbmanager-getdevices-f.md)获取的设备列表USBDevice的name。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象，返回临时权限的申请结果。返回true表示临时权限申请成功；返回false则表示临时权限申请失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  <br>1.Mandatory parameters are left unspecified.  <br>2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |

**示例**

```TypeScript
function requestRight() {
  let devicesList: Array<usbManager.USBDevice> = usbManager.getDevices();
  if (!devicesList || devicesList.length == 0) {
    console.info(`device list is empty`);
    return;
  }

  let device: usbManager.USBDevice = devicesList?.[0];
  usbManager.requestRight(device.name).then(ret => {
    console.info(`requestRight = ${ret}`);
  }).catch((error) => {
    console.error(`Failed to request right. Code: ${error.code}, message: ${error.message}`);
  });
}
```

