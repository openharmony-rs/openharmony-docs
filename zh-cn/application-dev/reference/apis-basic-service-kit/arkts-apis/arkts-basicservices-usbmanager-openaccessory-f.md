# openAccessory

## openAccessory

```TypeScript
function openAccessory(accessory: USBAccessory): USBAccessoryHandle
```

��ȡ��������������ļ���������֮�����ͨ��CoreFileKit�ṩ��read/write�ӿں��������ͨ�š�
��Ҫ����[usbManager.getAccessoryList](arkts-basicservices-usbmanager-getaccessorylist-f.md#getAccessoryList-1)��ȡ����б����õ�
[USBAccessory](arkts-basicservices-usbmanager-usbaccessory-i.md#USBAccessory)��Ϊ������

**起始版本：** 14

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accessory | USBAccessory | 是 | USB�������Ҫͨ��[getAccessoryList](arkts-basicservices-usbmanager-getaccessorylist-f.md#getAccessoryList-1)��ȡ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| USBAccessoryHandle | USB�������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported.&lt;br&gt;**适用版本：** 18+ |
| [14400001](../../errorcode-universal.md#14400001-Access) | Access right denied. Call requestRight to get the USBDevicePipe access right first. |
| [14400004](../../errorcode-universal.md#14400004-Service) | Service exception. Possible causes:<br/><br/>1. No accessory is plugged in. |
| [14401001](../../errorcode-universal.md#14401001-The) | The target USBAccessory not matched. |
| [14401002](../../errorcode-universal.md#14401002-Failed) | Failed to open the native accessory node. |
| [14401003](../../errorcode-universal.md#14401003-Cannot) | Cannot reopen the accessory. |

**示例：**

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import { fileIo } from '@kit.CoreFileKit';
try {
  let accList: usbManager.USBAccessory[] = usbManager.getAccessoryList()
  let flag = usbManager.requestAccessoryRight(accList?.[0])
  let handle = usbManager.openAccessory(accList?.[0])
  hilog.info(0, 'testTag ui', `openAccessory success`)
  let arrayBuffer = new ArrayBuffer(4096);
  let readLength = fileIo.readSync(handle.accessoryFd, arrayBuffer, {offset: 0, length: 4096});
  hilog.info(0, 'testTag ui', 'readSync ret: ' + readLength.toString(10));
} catch (error) {
  hilog.error(0, 'testTag ui', `openAccessory error ${error.code}, message is ${error.message}`)
}

```

