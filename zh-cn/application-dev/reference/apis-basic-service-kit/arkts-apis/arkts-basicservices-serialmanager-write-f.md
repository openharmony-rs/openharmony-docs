# write

## 导入模块

```TypeScript
import { serialManager } from '@kit.BasicServicesKit';
```

<a id="write"></a>
## write

```TypeScript
function write(portId: number, buffer: Uint8Array, timeout?: number): Promise<number>
```

向串口设备异步写数据，每次写入数据长度不超过4KB，数据过大会导致数据丢失，长数据建议分包写入。使用Promise异步回调。

**起始版本：** 19

<!--Device-serialManager-function write(portId: int, buffer: Uint8Array, timeout?: int): Promise<int>--><!--Device-serialManager-function write(portId: int, buffer: Uint8Array, timeout?: int): Promise<int>-End-->

**系统能力：** SystemCapability.USB.USBManager.Serial

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| portId | number | 是 | 目标设备的端口号，来自[getPortList](arkts-basicservices-serialmanager-getportlist-f.md#getportlist-1)获取的串口参数SerialPort。 |
| buffer | Uint8Array | 是 | 写入数据的缓冲区，最大长度为4KB。 |
| timeout | number | 否 | 超时时间（单位：毫秒），指定时间内等待API在目标端口的缓冲区是否可写，若可写则正常处理，若不可写等待超过指定时间后返回超时。默认值0表示不可写时不等待直接返回。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回写入数据长度。 |

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

以下示例代码只是调用write接口的必要流程，需要放入具体的方法中执行。实际调用时，设备开发者需要遵循设备相关协议进行调用。

```TypeScript
import { JSON } from '@kit.ArkTS';
import { buffer } from '@kit.ArkTS';
import { serialManager } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 获取串口列表
async function writeExample() {
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

  // 异步写入
  let writeBuffer: Uint8Array = new Uint8Array(buffer.from('Hello World', 'utf-8').buffer)
  let size: number = await serialManager.write(portId, writeBuffer, 2000);
  if (size > 0) {
    console.info('write usbSerial success, writeBuffer: ' + writeBuffer.toString());
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

