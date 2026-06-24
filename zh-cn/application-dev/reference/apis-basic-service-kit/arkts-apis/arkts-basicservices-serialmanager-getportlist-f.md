# getPortList

## getPortList

```TypeScript
function getPortList(): Readonly<SerialPort>[]
```

��ѯ�����豸�嵥�������豸���ƺͶ�Ӧ�Ķ˿ںš�

**起始版本：** 19

**系统能力：** SystemCapability.USB.USBManager.Serial

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Readonly&lt;SerialPort&gt;[] | Serial port information list. |

**示例：**

以下示例代码只是调用getPortList接口的必要流程，需要放入具体的方法中执行。实际调用时，设备开发者需要遵循设备相关协议进行调用。

```TypeScript
import { JSON } from '@kit.ArkTS';
import { serialManager } from '@kit.BasicServicesKit';

// 获取串口设备清单 
function getPortList() {
  let portList: serialManager.SerialPort[] = serialManager.getPortList();
  console.info('usbSerial portList: ' + JSON.stringify(portList));
  if (!portList || portList.length === 0) {
    console.error('usbSerial portList is empty');
    return;
  }
  let portId: number = portList[0].portId;
}

```

