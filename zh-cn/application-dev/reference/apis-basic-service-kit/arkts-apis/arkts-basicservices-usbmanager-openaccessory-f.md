# openAccessory

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

<a id="openaccessory"></a>
## openAccessory

```TypeScript
function openAccessory(accessory: USBAccessory): USBAccessoryHandle
```

获取配件句柄并打开配件文件描述符。之后可以通过CoreFileKit提供的read/write接口和配件进行通信。需要调用[usbManager.getAccessoryList](arkts-basicservices-usbmanager-getaccessorylist-f.md#getaccessorylist-1)获取配件列表，得到[USBAccessory](arkts-basicservices-usbmanager-usbaccessory-i.md)作为参数。

**起始版本：** 14

<!--Device-usbManager-function openAccessory(accessory: USBAccessory): USBAccessoryHandle--><!--Device-usbManager-function openAccessory(accessory: USBAccessory): USBAccessoryHandle-End-->

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accessory | [USBAccessory](arkts-basicservices-usbmanager-usbaccessory-i.md) | 是 | USB配件，需要通过[getAccessoryList](arkts-basicservices-usbmanager-getaccessorylist-f.md#getaccessorylist-1)获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [USBAccessoryHandle](arkts-basicservices-usbmanager-usbaccessoryhandle-i.md) | USB配件句柄。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:* <br>1. Mandatory parameters are left unspecified.* <br>2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |
| [14400001](../../apis-basic-services-kit/errorcode-usb.md#14400001-连接usb设备被拒绝) | Access right denied. Call requestRight to get the USBDevicePipe access right first. |
| [14400004](../../apis-basic-services-kit/errorcode-usb.md#14400004-服务异常) | Service exception. Possible causes:* <br>1. No accessory is plugged in. |
| [14401001](../../apis-basic-services-kit/errorcode-usb.md#14401001-目标usb配件未匹配) | The target USBAccessory not matched. |
| [14401002](../../apis-basic-services-kit/errorcode-usb.md#14401002-打开配件节点失败) | Failed to open the native accessory node. |
| [14401003](../../apis-basic-services-kit/errorcode-usb.md#14401003-不能重复打开配件) | Cannot reopen the accessory. |

**示例：**

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import { fileIo } from '@kit.CoreFileKit';
try {
  let accList: usbManager.USBAccessory[] = usbManager.getAccessoryList()
  let flag = usbManager.requestAccessoryRight(accList?.[0])
  if (!flag) {
    return
  }
  let handle = usbManager.openAccessory(accList?.[0])
  hilog.info(0, 'testTag ui', `openAccessory success`)
  let arrayBuffer = new ArrayBuffer(4096);
  let readLength = fileIo.readSync(handle.accessoryFd, arrayBuffer, {offset: 0, length: 4096});
  hilog.info(0, 'testTag ui', 'readSync ret: ' + readLength.toString(10));
} catch (error) {
  hilog.error(0, 'testTag ui', `openAccessory error ${error.code}, message is ${error.message}`)
}

```

