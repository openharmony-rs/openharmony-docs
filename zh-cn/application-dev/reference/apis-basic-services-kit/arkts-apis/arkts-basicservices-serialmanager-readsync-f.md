# readSync

## 导入模块

```TypeScript
import { serialManager } from '@kit.BasicServicesKit';
```

## readSync

```TypeScript
function readSync(portId: number, buffer: Uint8Array, timeout?: number): number
```

从串口设备同步读取数据，读取的数据将存储在buffer参数中，返回实际读取的数据长度。使用前需先调用[open](arkts-basicservices-serialmanager-open-f.md)打开串口设备。适用于需要阻塞式等待数据、对读取顺序有严格要求、或实时性要求不高的简单通信场景。

**前置条件：**  
- 需要先调用[getPortList](arkts-basicservices-serialmanager-getportlist-f.md)获取端口号  
- 需要先调用[requestSerialRight](arkts-basicservices-serialmanager-requestserialright-f.md)申请访问权限  
- 需要先调用[open](arkts-basicservices-serialmanager-open-f.md)打开串口

**起始版本：** 19

**系统能力：** SystemCapability.USB.USBManager.Serial

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| portId | number | 是 | 端口号，来自[getPortList](arkts-basicservices-serialmanager-getportlist-f.md)返回的[SerialPort](arkts-basicservices-serialmanager-serialport-i.md)对象，必须使用getPortList返回的有效端口号，传入无效值时抛出错误码31400003异常。 |
| buffer | Uint8Array | 是 | 读取数据的缓冲区，用于存储从串口设备读取的二进制数据。缓冲区大小应根据预期读取的数据量确定。读取成功后，返回值表示实际读取的数据长度。 |
| timeout | number | 否 | 超时时间（单位：毫秒）。API在目标端口缓冲区无数据时，等待指定时间后返回。默认值0或不传参时，表示不等待直接返回。传入负数时抛出参数错误异常。具体值需根据设备响应速度和数据量合理设置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回实际读取到的数据长度，即成功读取的字节数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) |  |
| [31400001](../errorcode-usb.md#31400001-串口服务异常) |  |
| [31400003](../errorcode-usb.md#31400003-端口号不存在) |  |
| [31400005](../errorcode-usb.md#31400005-设备未打开) |  |
| [31400006](../errorcode-usb.md#31400006-传输超时) |  |
| [31400007](../errorcode-usb.md#31400007-io异常) |  |

**示例**

> 说明：
> 
> 以下示例代码只是调用readSync接口的必要流程，需要放入具体的方法中执行。实际调用时，设备开发者需要遵循设备相关协议进行调用。

```TypeScript
import { JSON } from '@kit.ArkTS';
import { serialManager } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 获取串口列表
async function readSyncExample() {
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

  // 同步读取
  let readSyncBuffer: Uint8Array = new Uint8Array(64);
  try {
    serialManager.readSync(portId, readSyncBuffer, 2000);
    console.info('readSync usbSerial success, readSyncBuffer: ' + readSyncBuffer.toString());
  } catch (error) {
    const err: BusinessError = error as BusinessError;
    console.error(`Failed to readSync usbSerial. Code: ${err.code}, message: ${err.message}`);
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
