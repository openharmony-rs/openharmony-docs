# cancelSerialRight

## 导入模块

```TypeScript
import { serialManager } from '@kit.BasicServicesKit';
```

## cancelSerialRight

```TypeScript
function cancelSerialRight(portId: number): void
```

移除应用程序运行时访问串口设备的权限。此接口会调用close关闭已打开的串口。

**起始版本：** 19

<!--Device-serialManager-function cancelSerialRight(portId: int): void--><!--Device-serialManager-function cancelSerialRight(portId: int): void-End-->

**系统能力：** SystemCapability.USB.USBManager.Serial

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| portId | number | 是 | 目标设备的端口号，来自[getPortList](arkts-basicservices-serialmanager-getportlist-f.md#getportlist-1)获取的串口参数SerialPort。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) |  |
| [14400005](../../apis-basic-services-kit/errorcode-usb.md#14400005-数据库操作异常) |  |
| [31400001](../../apis-basic-services-kit/errorcode-usb.md#31400001-串口服务异常) |  |
| [31400002](../../apis-basic-services-kit/errorcode-usb.md#31400002-没有串口设备访问权限) |  |
| [31400003](../../apis-basic-services-kit/errorcode-usb.md#31400003-端口号不存在) |  |

**示例：**

以下示例代码只是调用cancelSerialRight接口的必要流程，需要放入具体的方法中执行。实际调用时，设备开发者需要遵循设备相关协议进行调用。

```TypeScript
import { JSON } from '@kit.ArkTS';
import { serialManager } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 获取串口列表
async function cancelSerialRightExample() {
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

  // 取消已经授予的权限
  try {
    serialManager.cancelSerialRight(portId);
    console.info('cancelSerialRight success, portId: ', portId);
  } catch (error) {
    const err: BusinessError = error as BusinessError;
    console.error(`Failed to cancel serial right. Code: ${err.code}, message: ${err.message}`);
  }
}

```

