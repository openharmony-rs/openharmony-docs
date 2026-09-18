# usbCancelTransfer

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## usbCancelTransfer

```TypeScript
function usbCancelTransfer(transfer: UsbDataTransferParams): void
```

取消异步传输请求。适用于需要主动终止未完成USB数据传输的场景，如用户手动取消长时间数据传输、传输超时后的错误恢复、应用切换时中止当前传输等。

> **说明：** 
> 
> 主动取消尚未完成的USB数据传输请求（如usbSubmitTransfer提交的传输）。

> 在调用该接口前需要通过[usbManager.claimInterface](arkts-basicservices-usbmanager-claiminterface-f.md) claim通信接口。

**起始版本：** 18

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| transfer | [UsbDataTransferParams](arkts-basicservices-usbmanager-usbdatatransferparams-i.md) | 是 | 被取消传输的参数，该参数与[usbManager.usbSubmitTransfer](arkts-basicservices-usbmanager-usbsubmittransfer-f.md)接口的transfer参数相同。在调用该接口前需要通过[usbManager.claimInterface](arkts-basicservices-usbmanager-claiminterface-f.md) claim通信接口。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14400001](../errorcode-usb.md#14400001-usb设备访问权限被拒绝) | Access right denied. Call requestRight to get the USBDevicePipe access right first. |
| [14400008](../errorcode-usb.md#14400008-没有设备连接已断开) | No such device (it may have been disconnected). |
| [14400010](../errorcode-usb.md#14400010-无法识别的错误) | Other USB error. Possible causes:<br>1.Unrecognized discard error code. |
| [14400011](../errorcode-usb.md#14400011-未找到正在进行的传输) | The transfer is not in progress, or is already complete or cancelled. |

**示例**

```TypeScript
> 说明：
> 
> 以下示例代码需要放入具体的方法中执行，只是调用usbCancelTransfer接口的必要流程，实际调用时，设备开发者需要遵循目标USB设备的协议规范进行调用，具体协议要求请参考设备的技术文档，确保数据的正确传输和设备的兼容性。
```
