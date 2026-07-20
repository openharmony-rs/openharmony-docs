# hasSerialRight

## 导入模块

```TypeScript
import { serialManager } from '@kit.BasicServicesKit';
```

<a id="hasserialright"></a>
## hasSerialRight

```TypeScript
function hasSerialRight(portId: number): boolean
```

检查应用程序是否具有访问串口设备的权限。应用退出后再拉起时，需要重新申请授权。

**起始版本：** 19

<!--Device-serialManager-function hasSerialRight(portId: int): boolean--><!--Device-serialManager-function hasSerialRight(portId: int): boolean-End-->

**系统能力：** SystemCapability.USB.USBManager.Serial

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| portId | number | 是 | 目标设备的端口号，来自[getPortList](arkts-basicservices-serialmanager-getportlist-f.md#getportlist-1)获取的串口参数SerialPort。 |

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
import { serialManager } from '@kit.BasicServicesKit';

// 获取串口列表
function hasSerialRightExample() {
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

