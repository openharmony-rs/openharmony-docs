# getAttribute

## 导入模块

```TypeScript
import { serialManager } from '@kit.BasicServicesKit';
```

## getAttribute

```TypeScript
function getAttribute(portId: number): Readonly<SerialAttribute>
```

获取指定串口的配置参数。

**起始版本：** 19

<!--Device-serialManager-function getAttribute(portId: int): Readonly<SerialAttribute>--><!--Device-serialManager-function getAttribute(portId: int): Readonly<SerialAttribute>-End-->

**系统能力：** SystemCapability.USB.USBManager.Serial

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| portId | number | 是 | 目标设备的端口号，来自[getPortList](arkts-basicservices-serialmanager-getportlist-f.md#getportlist-1)获取的串口参数SerialPort。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Readonly<SerialAttribute> | 返回串口的配置参数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) |  |
| [31400001](../../apis-basic-services-kit/errorcode-usb.md#31400001-串口服务异常) |  |
| [31400003](../../apis-basic-services-kit/errorcode-usb.md#31400003-端口号不存在) |  |
| [31400005](../../apis-basic-services-kit/errorcode-usb.md#31400005-设备未打开) |  |

**示例：**

以下示例代码只是调用getAttribute接口的必要流程，需要放入具体的方法中执行。实际调用时，设备开发者需要遵循设备相关协议进行调用。

```TypeScript
import { JSON } from '@kit.ArkTS';
import { serialManager } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 获取串口列表
async function getAttributeExample() {
  let portList: serialManager.SerialPort[] = serialManager.getPortList();
  console.info('usbSerial portList: ' + JSON.stringify(portList));
  if (!portList || portList.length === 0) {
    console.error('usbSerial portList is empty');
    return;
  }
  let portId: number = portList[0].portId;

  // 检测设备是否可被应用访问
  if (!serialManager.hasSerialRight(portId)) {
    let result = await serialManager.requestSerialRight(portId);
    if (!result) {
      // 没有访问设备的权限且用户不授权则退出
      console.error('user is not granted the operation permission');
      return;
    } else {
      console.info('grant permission successfully');
    }
  }

  // 打开设备
  try {
    serialManager.open(portId)
    console.info('open usbSerial success, portId: ' + portId);
  } catch (error) {
    const err: BusinessError = error as BusinessError;
    console.error(`Failed to open usbSerial. Code: ${err.code}, message: ${err.message}`);
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
    const err: BusinessError = error as BusinessError;
    console.error(`Failed to get attribute. Code: ${err.code}, message: ${err.message}`);
  }

  // 关闭串口
  try {
    serialManager.close(portId);
    console.info('close usbSerial success, portId: ' + portId);
  } catch (error) {
    const err: BusinessError = error as BusinessError;
    console.error(`Failed to close usbSerial. Code: ${err.code}, message: ${err.message}`);
  }
}

```

