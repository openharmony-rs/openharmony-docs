# openAccessory

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
import { serialManager } from '@kit.BasicServicesKit';
```

## openAccessory

```TypeScript
function openAccessory(accessory: USBAccessory): USBAccessoryHandle
```

获取配件句柄并打开配件文件描述符。之后可以通过CoreFileKit提供的read/write接口和配件进行通信。使用完后需要调用[closeAccessory](arkts-basicservices-usbmanager-closeaccessory-f.md)接 口关闭文件描述符。 需要调用[usbManager.getAccessoryList](arkts-basicservices-usbmanager-getaccessorylist-f.md)获取配件列表，得到 [USBAccessory](arkts-basicservices-usbmanager-usbaccessory-i.md)作为参数。调用前需先调用 [usbManager.requestAccessoryRight](arkts-basicservices-usbmanager-requestaccessoryright-f.md)请求访问配件权限，权限申请成功（返回true）后方可调用本接口打开配件。

**起始版本：** 23

<!--Device-usbManager-function openAccessory(accessory: USBAccessory): USBAccessoryHandle--><!--Device-usbManager-function openAccessory(accessory: USBAccessory): USBAccessoryHandle-End-->

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accessory | [USBAccessory](arkts-basicservices-usbmanager-usbaccessory-i.md) | 是 | USB配件，需要通过[getAccessoryList](arkts-basicservices-usbmanager-getaccessorylist-f.md)获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [USBAccessoryHandle](arkts-basicservices-usbmanager-usbaccessoryhandle-i.md) | USB配件句柄。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14401003](../errorcode-usb.md#14401003-不能重复打开配件) | Cannot reopen the accessory. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  <br>1. Mandatory parameters are left unspecified.  <br>2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |
| [14401002](../errorcode-usb.md#14401002-打开配件节点失败) | Failed to open the native accessory node. |
| [14401001](../errorcode-usb.md#14401001-目标usb配件未匹配) | The target USBAccessory not matched. |
| [14400001](../errorcode-usb.md#14400001-usb设备访问权限被拒绝) | Access right denied. Call requestRight to get the USBDevicePipe access right first. |
| [14400004](../errorcode-usb.md#14400004-服务异常) | Service exception. Possible causes:  <br>1. No accessory is plugged in. |

**示例**

```TypeScript
import { fileIo } from '@kit.CoreFileKit';
async function openAccessory() {
  try {
    let accList: usbManager.USBAccessory[] = usbManager.getAccessoryList();
    let flag = await usbManager.requestAccessoryRight(accList?.[0]);
    if (!flag) {
      return;
    }
    let handle = usbManager.openAccessory(accList?.[0]);
    console.info(`openAccessory success`);
    let arrayBuffer = new ArrayBuffer(4096);
    let readLength = fileIo.readSync(handle.accessoryFd, arrayBuffer, {offset: 0, length: 4096});
    console.info('readSync ret: ' + readLength.toString(10));
  } catch (error) {
    console.error(`openAccessory error ${error.code}, message is ${error.message}`);
  }
}
```

