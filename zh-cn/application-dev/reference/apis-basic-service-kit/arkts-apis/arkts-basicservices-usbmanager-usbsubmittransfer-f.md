# usbSubmitTransfer

## usbSubmitTransfer

```TypeScript
function usbSubmitTransfer(transfer: UsbDataTransferParams): void
```

�ύ�첽��������

> **˵����**
>
> ���ӿ�Ϊ�첽�ӿڣ����ú����̷��أ�ʵ�ʶ�д�����Ľ���Իص��ķ�ʽ���ء�
>
> �ڵ��øýӿ�ǰ��Ҫͨ��
> [usbManager.claimInterface](arkts-basicservices-usbmanager-claiminterface-f.md#claimInterface-1)
> claimͨ�Žӿڡ�

**起始版本：** 18

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| transfer | UsbDataTransferParams | 是 | ��Ϊͨ��USB���ݴ���ӿڣ��ͻ�����Ҫ�����������еĲ��������Է��������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. |
| [14400001](../../errorcode-universal.md#14400001-Access) | Access right denied. Call requestRight to get the USBDevicePipe access right first. |
| [14400007](../../errorcode-universal.md#14400007-Resource) | Resource busy. Possible causes:<br/><br/>1. The transfer has already been submitted.<br/><br/>2. The interface is claimed by another program or driver. |
| [14400008](../../errorcode-universal.md#14400008-No) | No such device (it may have been disconnected). |
| [14400009](../../errorcode-universal.md#14400009-Insufficient) | Insufficient memory. Possible causes:<br/><br/>1. Memory allocation failed. |
| [14400012](../../errorcode-universal.md#14400012-Transmission) | Transmission I/O error. |

**示例：**

以下示例代码需要放入具体的方法中执行，只是调用usbSubmitTransfer接口的必要流程，实际调用时，设备开发者需要遵循设备相关协议进行调用，确保数据的正确传输和设备的兼容性。

```TypeScript
// usbManager.getDevices 接口返回数据集合，取其中一个设备对象，并获取权限。
// 把获取到的设备对象作为参数传入usbManager.connectDevice;当usbManager.connectDevice接口成功返回之后；
// 才可以调用第三个接口usbManager.claimInterface.当usbManager.claimInterface 调用成功以后,再调用该接口。
function usbSubmitTransfer() {
  let devicesList: Array<usbManager.USBDevice> = usbManager.getDevices();
  if (!devicesList || devicesList.length == 0) {
    console.info(`device list is empty`);
    return;
  }
  let device: usbManager.USBDevice = devicesList?.[0];
  usbManager.requestRight(device.name);
  if (!usbManager.hasRight(device.name)) {
    console.info(`request right fail`);
    return;
  }
  let devicepipe: usbManager.USBDevicePipe = usbManager.connectDevice(device);
  // 获取endpoint端点地址。
  let endpoint = device.configs?.[0]?.interfaces?.[0]?.endpoints.find((value) => {
    return value.direction === 0 && value.type === 2
  })
  // 获取设备的第一个id。
  let ret: number = usbManager.claimInterface(devicepipe, device.configs?.[0]?.interfaces?.[0], true);

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
    transferParams.callback=(err, callBackData: usbManager.SubmitTransferCallback)=>{
      console.info('callBackData =' +JSON.stringify(callBackData));
    }
    usbManager.usbSubmitTransfer(transferParams); 
    console.info('USB transfer request submitted.');
  } catch (error) {
    console.error('USB transfer failed:', error);
  }
}

```

