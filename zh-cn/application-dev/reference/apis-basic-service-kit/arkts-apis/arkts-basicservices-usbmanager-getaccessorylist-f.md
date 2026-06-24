# getAccessoryList

## getAccessoryList

```TypeScript
function getAccessoryList(): Array<Readonly<USBAccessory>>
```

��ȡ��ǰ�ѽ���������USB����б���

**起始版本：** 14

**系统能力：** SystemCapability.USB.USBManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;Readonly&lt;USBAccessory&gt;&gt; | ֻ����USB����б�����ǰ��֧���б��а���1��USB����� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported.&lt;br&gt;**适用版本：** 18+ |
| [14400004](../../errorcode-universal.md#14400004-Service) | Service exception. Possible causes:<br/><br/>1. No accessory is plugged in. |

**示例：**

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
try {
  let accList: usbManager.USBAccessory[] = usbManager.getAccessoryList()
  hilog.info(0, 'testTag ui', `getAccessoryList success, accList: ${JSON.stringify(accList)}`)
} catch (error) {
  hilog.error(0, 'testTag ui', `getAccessoryList error ${error.code}, message is ${error.message}`)
}

```

