# open

## 导入模块

```TypeScript
import { serialManager } from '@kit.BasicServicesKit';
```

## open

```TypeScript
function open(portId: number): void
```

打开串口设备。使用前需先通过[requestSerialRight](arkts-basicservices-serialmanager-requestserialright-f.md)申请权限，使用完毕后需调用[close](arkts-basicservices-serialmanager-close-f.md)关闭串口。调用成功后，可对该串口进行读写、配置参数等操作。

**前置条件：**  
- 需要先调用[getPortList](arkts-basicservices-serialmanager-getportlist-f.md)获取端口号  
- 需要先调用[requestSerialRight](arkts-basicservices-serialmanager-requestserialright-f.md)申请访问权限

**配对调用：**  
- 必须与[close](arkts-basicservices-serialmanager-close-f.md)方法配对使用  
- 打开串口后，使用完毕必须调用close()释放资源

**起始版本：** 19

**系统能力：** SystemCapability.USB.USBManager.Serial

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| portId | number | 是 | 端口号，来自[getPortList](arkts-basicservices-serialmanager-getportlist-f.md)返回的[SerialPort](arkts-basicservices-serialmanager-serialport-i.md)对象，必须使用getPortList返回的有效端口号，传入无效值时抛出错误码31400003异常。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) |  |
| [31400001](../errorcode-usb.md#31400001-串口服务异常) |  |
| [31400002](../errorcode-usb.md#31400002-没有串口设备访问权限) |  |
| [31400003](../errorcode-usb.md#31400003-端口号不存在) |  |
| [31400004](../errorcode-usb.md#31400004-串口设备被占用) |  |

**示例**

> 说明：
> 
> 以下示例代码只是调用open接口的必要流程，需要放入具体的方法中执行。实际调用时，设备开发者需要遵循设备相关协议进行调用。

```TypeScript
import { JSON } from '@kit.ArkTS';
import { serialManager } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 获取串口列表
async function openExample() {
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
    serialManager.open(portId);
    console.info('open usbSerial success, portId: ' + portId);
  } catch (error) {
    const err: BusinessError = error as BusinessError;
    console.error(`Failed to open usbSerial. Code: ${err.code}, message: ${err.message}`);
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
