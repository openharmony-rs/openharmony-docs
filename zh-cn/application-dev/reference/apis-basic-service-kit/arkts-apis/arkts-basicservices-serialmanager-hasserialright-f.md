# hasSerialRight

## hasSerialRight

```TypeScript
function hasSerialRight(portId: number): boolean
```

���Ӧ�ó����Ƿ���з��ʴ����豸��Ȩ�ޡ�Ӧ���˳���������ʱ����Ҫ����������Ȩ��

**起始版本：** 19

**系统能力：** SystemCapability.USB.USBManager.Serial

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| portId | number | 是 | Ŀ���豸�Ķ˿ںţ�����[getPortList](arkts-basicservices-serialmanager-getportlist-f.md#getPortList-1)��ȡ�Ĵ��ڲ���SerialPort�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true��ʾ����Ȩ��false��ʾδ��Ȩ�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401) |  |
| [14400005](../../errorcode-universal.md#14400005) |  |
| [31400001](../../errorcode-universal.md#31400001) |  |
| [31400003](../../errorcode-universal.md#31400003) |  |

**示例：**

以下示例代码只是调用hasSerialRight接口的必要流程，需要放入具体的方法中执行。实际调用时，设备开发者需要遵循设备相关协议进行调用。

```TypeScript
import { JSON } from '@kit.ArkTS';
import { serialManager } from '@kit.BasicServicesKit';

// 获取串口列表
function hasSerialRight() {
  let portList: serialManager.SerialPort[] = serialManager.getPortList();
  console.info('portList: ', JSON.stringify(portList));
  if (!portList || portList.length === 0) {
    console.error('portList is empty');
    return;
  }
  let portId: number = portList[0].portId;

  // 检测设备是否可被应用访问
  if (serialManager.hasSerialRight(portId)) {
    console.info('The serial port is accessible');
  } else {
    console.error('No permission to access the serial port');
  }
}

```

