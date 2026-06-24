# getAttribute

## getAttribute

```TypeScript
function getAttribute(portId: number): Readonly<SerialAttribute>
```

��ȡָ�����ڵ����ò�����

**起始版本：** 19

**系统能力：** SystemCapability.USB.USBManager.Serial

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| portId | number | 是 | Ŀ���豸�Ķ˿ںţ�����[getPortList](arkts-basicservices-serialmanager-getportlist-f.md#getPortList-1)��ȡ�Ĵ��ڲ���SerialPort�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Readonly&lt;SerialAttribute&gt; | ���ش��ڵ����ò����� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401) |  |
| [31400001](../../errorcode-universal.md#31400001) |  |
| [31400003](../../errorcode-universal.md#31400003) |  |
| [31400005](../../errorcode-universal.md#31400005) |  |

**示例：**

以下示例代码只是调用getAttribute接口的必要流程，需要放入具体的方法中执行。实际调用时，设备开发者需要遵循设备相关协议进行调用。

```TypeScript
import { JSON } from '@kit.ArkTS';
import { serialManager } from '@kit.BasicServicesKit';

// 获取串口列表
function getAttribute() {
  let portList: serialManager.SerialPort[] = serialManager.getPortList();
  console.info('usbSerial portList: ' + JSON.stringify(portList));
  if (!portList || portList.length === 0) {
    console.error('usbSerial portList is empty');
    return;
  }
  let portId: number = portList[0].portId;

  // 检测设备是否可被应用访问
  if (!serialManager.hasSerialRight(portId)) {
    serialManager.requestSerialRight(portId).then(result => {
      if (!result) {
        // 没有访问设备的权限且用户不授权则退出
        console.error('user is not granted the operation permission');
        return;
      } else {
        console.info('grant permission successfully');
      }
    });
  }

  // 打开设备
  try {
    serialManager.open(portId)
    console.info('open usbSerial success, portId: ' + portId);
  } catch (error) {
    console.error('open usbSerial error, ' + JSON.stringify(error));
    return;
  }

  // 获取串口配置
  try {
    let attribute: serialManager.SerialAttribute = serialManager.getAttribute(portId);
    if (attribute === undefined) {
      console.error('getAttribute usbSerial error, attribute is undefined');
    } else {
      console.info('getAttribute usbSerial success, attribute: ' + JSON.stringify(attribute));
    }
  } catch (error) {
    console.error('getAttribute usbSerial error, ' + JSON.stringify(error));
  }
}

```

