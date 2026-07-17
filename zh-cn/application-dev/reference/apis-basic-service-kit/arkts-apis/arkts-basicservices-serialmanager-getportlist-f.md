# getPortList

## 导入模块

```TypeScript
import { serialManager } from '@kit.BasicServicesKit';
```

## getPortList

```TypeScript
function getPortList(): Readonly<SerialPort>[]
```

查询串口设备清单，包括设备名称和对应的端口号。

**起始版本：** 19

<!--Device-serialManager-function getPortList(): Readonly<SerialPort>[]--><!--Device-serialManager-function getPortList(): Readonly<SerialPort>[]-End-->

**系统能力：** SystemCapability.USB.USBManager.Serial

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Readonly<SerialPort>[] | Serial port information list. |

**示例：**

以下示例代码只是调用getPortList接口的必要流程，需要放入具体的方法中执行。实际调用时，设备开发者需要遵循设备相关协议进行调用。

```TypeScript
import { JSON } from '@kit.ArkTS';
import { serialManager } from '@kit.BasicServicesKit';

// 获取串口设备清单 
function getPortListExample() {
  let portList: serialManager.SerialPort[] = serialManager.getPortList();
  console.info('usbSerial portList: ' + JSON.stringify(portList));
  if (!portList || portList.length === 0) {
    console.error('usbSerial portList is empty');
    return;
  }
}

```

