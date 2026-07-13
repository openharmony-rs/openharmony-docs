# writeSync

## writeSync

```TypeScript
function writeSync(portId: number, buffer: Uint8Array, timeout?: number): number
```

向串口设备同步写数据，每次写入数据长度不超过4KB，数据过大会导致数据丢失，长数据建议分包写入。

**起始版本：** 19

**系统能力：** SystemCapability.USB.USBManager.Serial

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| portId | number | 是 | 目标设备的端口号，来自[getPortList](arkts-basicservices-getportlist-f.md#getportlist-1)获取的串口参数SerialPort。 |
| buffer | Uint8Array | 是 | 写入目标缓冲区，最大长度为4KB。 |
| timeout | number | 否 | 超时时间（单位：毫秒），指定时间内等待API在目标端口的缓冲区是否可写，若可写则正常处理，若不可写等待超过指定时间后返回超时。默认值0表示不可写时不等待直接返回。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回写入数据长度。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) |  |
| [31400001](../../apis-basic-services-kit/errorcode-usb.md#31400001-串口服务异常) |  |
| [31400003](../../apis-basic-services-kit/errorcode-usb.md#31400003-端口号不存在) |  |
| [31400005](../../apis-basic-services-kit/errorcode-usb.md#31400005-设备未打开) |  |
| [31400006](../../apis-basic-services-kit/errorcode-usb.md#31400006-传输超时) |  |
| [31400007](../../apis-basic-services-kit/errorcode-usb.md#31400007-io异常) |  |

**示例：**

以下示例代码只是调用writeSync接口的必要流程，需要放入具体的方法中执行。实际调用时，设备开发者需要遵循设备相关协议进行调用。

```TypeScript
import { JSON } from '@kit.ArkTS';
import { buffer } from '@kit.ArkTS';
import { serialManager } from '@kit.BasicServicesKit';

// 获取串口列表
function writeSync() {
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
  }

  // 同步写入
  let writeSyncBuffer: Uint8Array = new Uint8Array(buffer.from('Hello World', 'utf-8').buffer)
  try {
    serialManager.writeSync(portId, writeSyncBuffer, 2000);
    console.info('writeSync usbSerial success, writeSyncBuffer: ' + writeSyncBuffer.toString());
  } catch (error) {
    console.error('writeSync usbSerial error, ' + JSON.stringify(error));
  }
  
  // 关闭串口
  try {
    serialManager.close(portId);
    console.info('close usbSerial success, portId: ' + portId);
  } catch (error) {
    console.error('close usbSerial error, ' + JSON.stringify(error));
  }
}

```

