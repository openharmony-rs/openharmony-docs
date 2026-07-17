# usbSubmitTransfer

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## usbSubmitTransfer

```TypeScript
function usbSubmitTransfer(transfer: UsbDataTransferParams): void
```

提交异步传输请求。

> **说明：**  
>  
> 本接口为异步接口，调用后立刻返回，实际读写操作的结果以回调的方式返回。  
>  
> 在调用该接口前需要通过  
> [usbManager.claimInterface](arkts-basicservices-usbmanager-claiminterface-f.md#claiminterface-1)  
> claim通信接口。

**起始版本：** 18

<!--Device-usbManager-function usbSubmitTransfer(transfer: UsbDataTransferParams): void--><!--Device-usbManager-function usbSubmitTransfer(transfer: UsbDataTransferParams): void-End-->

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| transfer | [UsbDataTransferParams](arkts-basicservices-usbmanager-usbdatatransferparams-i.md) | 是 | 作为通用USB数据传输接口，客户端需要填充这个对象中的参数，用以发起传输请求。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14400001](../../apis-basic-services-kit/errorcode-usb.md#14400001-连接usb设备被拒绝) | Access right denied. Call requestRight to get the USBDevicePipe access right first. |
| [14400007](../../apis-basic-services-kit/errorcode-usb.md#14400007-资源繁忙) | Resource busy. Possible causes:* <br>1. The transfer has already been submitted.* <br>2. The interface is claimed by another program or driver. |
| [14400008](../../apis-basic-services-kit/errorcode-usb.md#14400008-没有设备连接已断开) | No such device (it may have been disconnected). |
| [14400009](../../apis-basic-services-kit/errorcode-usb.md#14400009-内存不足) | Insufficient memory. Possible causes:* <br>1. Memory allocation failed. |
| [14400012](../../apis-basic-services-kit/errorcode-usb.md#14400012-io错误) | Transmission I/O error. |

**示例：**

以下示例代码需要放入具体的方法中执行，只是调用usbSubmitTransfer接口的必要流程，实际调用时，设备开发者需要遵循设备相关协议进行调用，确保数据的正确传输和设备的兼容性。

```TypeScript
// usbManager.getDevices 接口返回数据集合，取其中一个设备对象，并获取权限。
// 把获取到的设备对象作为参数传入usbManager.connectDevice;当usbManager.connectDevice接口成功返回之后；
// 才可以调用第三个接口usbManager.claimInterface.当usbManager.claimInterface 调用成功以后,再调用该接口。
async function usbSubmitTransfer() {
  let devicesList: Array<usbManager.USBDevice> = usbManager.getDevices();
  if (!devicesList || devicesList.length == 0) {
    console.info(`device list is empty`);
    return;
  }
  let device: usbManager.USBDevice = devicesList?.[0];
  await usbManager.requestRight(device.name);
  if (!usbManager.hasRight(device.name)) {
    console.info(`request right fail`);
    return;
  }
  let devicepipe: usbManager.USBDevicePipe = usbManager.connectDevice(device);
  if (devicepipe == undefined) {
    console.error(`connect device failed`);
    return;
  }
  // 获取endpoint端点地址
  let endpoint = device.configs?.[0]?.interfaces?.[0]?.endpoints.find((value) => {
    return value.direction === 0 && value.type === 2
  })
  // 获取设备的第一个id。
  usbManager.claimInterface(devicepipe, device.configs?.[0]?.interfaces?.[0], true);

  let transferParams: usbManager.UsbDataTransferParams = {
    devPipe: devicepipe,
    flags: usbManager.UsbTransferFlags.USB_TRANSFER_SHORT_NOT_OK,
    endpoint: 1,
    type: usbManager.UsbEndpointTransferType.TRANSFER_TYPE_BULK,
    timeout: 2000,
    length: 10, 
    callback: () => {},
    userData: new Uint8Array(10),
    buffer: new Uint8Array(10),
    isoPacketCount: 0,
  };
  try {
    transferParams.endpoint=endpoint?.address as number;
    transferParams.callback=(err, callbackData: usbManager.SubmitTransferCallback)=>{
      if (err) {
        console.error('USB transfer failed:', err);
        return;
      }
      console.info('callbackData =' +JSON.stringify(callbackData));
    }
    usbManager.usbSubmitTransfer(transferParams); 
    console.info('USB transfer request submitted.');
  } catch (error) {
    console.error('USB transfer failed:', error);
  }
  usbManager.closePipe(devicepipe);
}

```

