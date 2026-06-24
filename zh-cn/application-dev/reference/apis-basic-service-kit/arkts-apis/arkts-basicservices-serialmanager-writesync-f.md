# writeSync

## writeSync

```TypeScript
function writeSync(portId: number, buffer: Uint8Array, timeout?: number): number
```

�򴮿��豸ͬ��д���ݣ�ÿ��д�����ݳ��Ȳ�����4KB�����ݹ���ᵼ�����ݶ�ʧ�������ݽ���ְ�д�롣

**起始版本：** 19

**系统能力：** SystemCapability.USB.USBManager.Serial

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| portId | number | 是 | Ŀ���豸�Ķ˿ںţ�����[getPortList](arkts-basicservices-serialmanager-getportlist-f.md#getPortList-1)��ȡ�Ĵ��ڲ���SerialPort�� |
| buffer | Uint8Array | 是 | д��Ŀ�껺��������󳤶�Ϊ4KB�� |
| timeout | number | 否 | ��ʱʱ�䣨��λ�����룩��ָ��ʱ���ڵȴ�API��Ŀ��˿ڵĻ������Ƿ��д������д������������������д�ȴ�����ָ��ʱ��󷵻س�ʱ��Ĭ��ֵ0��ʾ����дʱ���ȴ�ֱ�ӷ��ء� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | ����д�����ݳ��ȡ� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401) |  |
| [31400001](../../errorcode-universal.md#31400001) |  |
| [31400003](../../errorcode-universal.md#31400003) |  |
| [31400005](../../errorcode-universal.md#31400005) |  |
| [31400006](../../errorcode-universal.md#31400006) |  |
| [31400007](../../errorcode-universal.md#31400007) |  |

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
}

```

