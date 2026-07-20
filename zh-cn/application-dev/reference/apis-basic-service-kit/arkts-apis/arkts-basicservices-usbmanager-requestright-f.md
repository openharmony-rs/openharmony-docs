# requestRight

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

<a id="requestright"></a>
## requestRight

```TypeScript
function requestRight(deviceName: string): Promise<boolean>
```

请求软件包的临时权限以访问设备。使用Promise异步回调。系统应用默认拥有访问设备权限，无需调用此接口申请。

**起始版本：** 9

<!--Device-usbManager-function requestRight(deviceName: string): Promise<boolean>--><!--Device-usbManager-function requestRight(deviceName: string): Promise<boolean>-End-->

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceName | string | 是 | 设备名称，来自[usbManager.getDevices](arkts-basicservices-usbmanager-getdevices-f.md#getdevices-1)获取的设备列表USBDevice的name。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象，返回临时权限的申请结果。返回true表示临时权限申请成功；返回false则表示临时权限申请失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:* <br>1.Mandatory parameters are left unspecified.* <br>2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |

**示例：**

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
  }).catch((error: BusinessError) => {
    console.error(`Failed to request right. Code: ${error.code}, message: ${error.message}`);
  });
}

```

