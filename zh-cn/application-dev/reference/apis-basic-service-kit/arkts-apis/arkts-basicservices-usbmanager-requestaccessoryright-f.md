# requestAccessoryRight

## requestAccessoryRight

```TypeScript
function requestAccessoryRight(accessory: USBAccessory): Promise<boolean>
```

Ϊָ��Ӧ�ó����������USB����ķ���Ȩ�ޡ�ʹ��Promise�첽�ص���
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
| Promise&lt;boolean&gt; | Promise���󣬷���Ӧ�ó���������Ȩ�޵�������������true��ʾȨ������ɹ�������false��ʾȨ������ʧ�ܡ� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported.&lt;br&gt;**适用版本：** 18+ |
| [14401001](../../errorcode-universal.md#14401001-The) | The target USBAccessory not matched. |
| [14400004](../../errorcode-universal.md#14400004-Service) | Service exception. Possible causes:<br/><br/>1. No accessory is plugged in. |
| [14400005](../../errorcode-universal.md#14400005-Database) | Database operation exception. |

**示例：**

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
try {
  let accList: usbManager.USBAccessory[] = usbManager.getAccessoryList()
  let flag = usbManager.requestAccessoryRight(accList?.[0])
  hilog.info(0, 'testTag ui', `requestAccessoryRight success, ret:${flag}`)
} catch (error) {
  hilog.error(0, 'testTag ui', `requestAccessoryRight error ${error.code}, message is ${error.message}`)
}

```

