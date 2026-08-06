# hasSerialRight

## hasSerialRight

```TypeScript
function hasSerialRight(portId: int): boolean
```

检查应用程序是否具有访问串口设备的权限。应用退出后再拉起时，需要重新申请授权。

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

<!--Device-serialManager-function hasSerialRight(portId: int): boolean--><!--Device-serialManager-function hasSerialRight(portId: int): boolean-End-->

**系统能力：** SystemCapability.USB.USBManager.Serial

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| portId | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 目标设备的端口号，来自[getPortList]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_获取的串口参数SerialPort。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示已授权，false表示未授权。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) |  |
| [14400005](../../apis-basic-services-kit/errorcode-usb.md#14400005-数据库操作异常) |  |
| [31400001](../../apis-basic-services-kit/errorcode-usb.md#31400001-串口服务异常) |  |
| [31400003](../../apis-basic-services-kit/errorcode-usb.md#31400003-端口号不存在) |  |

**示例：**

以下示例代码只是调用hasSerialRight接口的必要流程，需要放入具体的方法中执行。实际调用时，设备开发者需要遵循设备相关协议进行调用。

```TypeScript
import { JSON } from '@kit.ArkTS';
import serialManager from '@ohos.usbManager.serial';

// 获取串口列表
function hasSerialRightExample() {
  let portList: serialManager.SerialPort[] = serialManager.getPortList();
  console.info('portList: ', JSON.stringify(portList));
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

