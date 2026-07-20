# getFileDescriptor

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

<a id="getfiledescriptor"></a>
## getFileDescriptor

```TypeScript
function getFileDescriptor(pipe: USBDevicePipe): number
```

获取文件描述符。

**起始版本：** 9

<!--Device-usbManager-function getFileDescriptor(pipe: USBDevicePipe): int--><!--Device-usbManager-function getFileDescriptor(pipe: USBDevicePipe): int-End-->

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pipe | [USBDevicePipe](arkts-basicservices-usbmanager-usbdevicepipe-i.md) | 是 | 用于确定总线号和设备地址，需要调用[usbManager.connectDevice](arkts-basicservices-usbmanager-connectdevice-f.md#connectdevice-1)获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回设备对应的文件描述符，失败返回其它错误码如下：* - 88080486：服务初始化中，请稍后重试。* - 88080488：无设备访问权限，请先调用[usbManager.requestRight](arkts-basicservices-usbmanager-requestright-f.md#requestright-1)接口申请授权。* - -1：驱动异常 。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:* <br>1.Mandatory parameters are left unspecified.* <br>2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |

**示例：**

```TypeScript
async function getFileDescriptor() {
  let devicesList: Array<usbManager.USBDevice> = usbManager.getDevices();
  if (!devicesList || devicesList.length == 0) {
    console.info(`device list is empty`);
    return;
  }

  let rightResult = await usbManager.requestRight(devicesList?.[0]?.name);
  if (!rightResult) {
    console.error(`request right failed`);
    return;
  }
  let devicepipe: usbManager.USBDevicePipe = usbManager.connectDevice(devicesList?.[0]);
  if (devicepipe == undefined) {
    console.error(`connect device failed`);
    return;
  }
  let ret: number = usbManager.getFileDescriptor(devicepipe);
  console.info(`getFileDescriptor = ${ret}`);
  let closeRet: number = usbManager.closePipe(devicepipe);
  console.info(`closePipe = ${closeRet}`);
}

```

