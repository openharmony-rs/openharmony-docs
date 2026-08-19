# hasSerialRight

## 导入模块

```TypeScript
import { serialManager } from '@kit.BasicServicesKit';
```

## hasSerialRight

```TypeScript
function hasSerialRight(portId: int): boolean
```

检查应用是否具有访问串口设备的权限。应用退出后再拉起时，需要重新申请授权。通常在打开串口设备、执行串口操作前调用此接口检查权限状态。 **前置条件：** - 需要先调用[getPortList](arkts-basicservices-serialmanager-getportlist-f.md)获取端口号

**起始版本：** 23

<!--Device-serialManager-function hasSerialRight(portId: int): boolean--><!--Device-serialManager-function hasSerialRight(portId: int): boolean-End-->

**系统能力：** SystemCapability.USB.USBManager.Serial

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| portId | int | 是 | 端口号，来自[getPortList](arkts-basicservices-serialmanager-getportlist-f.md)返回的 [SerialPort](arkts-basicservices-serialmanager-serialport-i.md)对象，必须使用getPortList返回的有效端口号，传入无效值时抛出错误码31400003异常。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示已授权，false表示未授权。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) |  |
| [31400003](../errorcode-usb.md#31400003-端口号不存在) |  |
| [14400005](../errorcode-usb.md#14400005-数据库操作异常) |  |
| [31400001](../errorcode-usb.md#31400001-串口服务异常) |  |

**示例**

以下示例代码只是调用hasSerialRight接口的必要流程，需要放入具体的方法中执行。实际调用时，设备开发者需要遵循设备相关协议进行调用。

```TypeScript
import { JSON } from '@kit.ArkTS';
import serialManager from '@ohos.usbManager.serial';

// 获取串口列表
function hasSerialRightExample() {
  let portList: serialManager.SerialPort[] = serialManager.getPortList();
  console.info('portList: '+ JSON.stringify(portList));
  if (portList === undefined || portList.length === 0) {
    console.error('portList is empty');
    return;
  }
  let portId: int = portList[0].portId;

  // 检测设备是否可被应用访问
  if (serialManager.hasSerialRight(portId)) {
    console.info('The serial port is accessible');
  } else {
    console.error('No permission to access the serial port');
  }
}
```

