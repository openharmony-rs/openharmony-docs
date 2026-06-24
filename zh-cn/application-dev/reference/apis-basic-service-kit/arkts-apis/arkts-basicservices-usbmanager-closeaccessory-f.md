# closeAccessory

## closeAccessory

```TypeScript
function closeAccessory(accessoryHandle: USBAccessoryHandle): void
```

�ر�����ļ���������
��Ҫ����[usbManager.openAccessory](arkts-basicservices-usbmanager-openaccessory-f.md#openAccessory-1)��ȡ����б����õ�
[USBAccessoryHandle](arkts-basicservices-usbmanager-usbaccessoryhandle-i.md#USBAccessoryHandle)��Ϊ������

**起始版本：** 14

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accessoryHandle | USBAccessoryHandle | 是 | USB����������Ҫͨ��<br/>[openAccessory](arkts-basicservices-usbmanager-openaccessory-f.md#openAccessory-1)��ȡ�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported.&lt;br&gt;**适用版本：** 18+ |
| [14400004](../../errorcode-universal.md#14400004-Service) | Service exception. Possible causes:<br/><br/>1. No accessory is plugged in. |

**示例：**

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
try {
  let accList: usbManager.USBAccessory[] = usbManager.getAccessoryList()
  let flag = usbManager.requestAccessoryRight(accList?.[0])
  let handle = usbManager.openAccessory(accList?.[0])
  usbManager.closeAccessory(handle)
  hilog.info(0, 'testTag ui', `closeAccessory success`)
} catch (error) {
  hilog.error(0, 'testTag ui', `closeAccessory error ${error.code}, message is ${error.message}`)
}

```

