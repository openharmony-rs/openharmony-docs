# bulkTransfer

## bulkTransfer

```TypeScript
function bulkTransfer(
    pipe: USBDevicePipe,
    endpoint: USBEndpoint,
    buffer: Uint8Array,
    timeout?: number
  ): Promise<number>
```

�������䡣ʹ��Promise�첽�ص���

> **˵����**
>
> ������������Ĵ�����������������pipe��endpoint��buffer��timeout���������200KB���£�������������ᵼ�´���ʧ�ܷ���-1��
>
> �ڵ��ýӿ�ǰ��Ҫͨ��
> [usbManager.claimInterface](arkts-basicservices-usbmanager-claiminterface-f.md#claimInterface-1)
> claimͨ�Žӿڡ�

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pipe | USBDevicePipe | 是 | ����ȷ���豸����Ҫ����[usbManager.connectDevice](arkts-basicservices-usbmanager-connectdevice-f.md#connectDevice-1)��ȡ�� |
| endpoint | USBEndpoint | 是 | ����ȷ������Ķ˿ڣ���Ҫ����[usbManager.getDevices](arkts-basicservices-usbmanager-getdevices-f.md#getDevices-1)��ȡ�豸��Ϣ�б��Լ�endpoint��<br/>address����ȷ���˵��ַ��direction����ȷ���˵�ķ���interfaceId����ȷ�������ӿڣ���ǰ�������Բ��������� |
| buffer | Uint8Array | 是 | ����д����ȡ���ݵĻ������� |
| timeout | number | 否 | ��ʱʱ�䣨��λ�����룩����ѡ������ָ��ʱ���ڵȴ�����������ɣ�����ָ��ʱ���ڴ���������������أ����򷵻س�ʱ��Ĭ��Ϊ0ʱ���޵ȴ�ֱ��������ɡ��û�����ѡ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise���󣬻�ȡ�������յ������ݿ��С��ʧ�ܷ����������������£�<br/><br/>- -1�������쳣�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1.Mandatory parameters are left unspecified.<br/><br/>2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported.&lt;br&gt;**适用版本：** 18+ |

**示例：**

以下示例代码只是调用bulkTransfer接口的必要流程，实际调用时，设备开发者需要遵循设备相关协议进行调用，确保数据的正确传输和设备的兼容性。

```TypeScript
// usbManager.getDevices 接口返回数据集合，取其中一个设备对象，并获取权限。
// 把获取到的设备对象作为参数传入usbManager.connectDevice;当usbManager.connectDevice接口成功返回之后；
// 才可以调用第三个接口usbManager.claimInterface.当usbManager.claimInterface 调用成功以后,再调用该接口。
function bulkTransfer() {
  let devicesList: Array<usbManager.USBDevice> = usbManager.getDevices();
  if (!devicesList || devicesList.length == 0) {
    console.info(`device list is empty`);
    return;
  }

  let device: usbManager.USBDevice = devicesList?.[0];
  usbManager.requestRight(device.name);
  if (!usbManager.hasRight(device.name)) {
    console.error(`request right fail`);
    return;
  }
  let devicepipe: usbManager.USBDevicePipe = usbManager.connectDevice(device);
  for (let i = 0; i < device.configs?.[0]?.interfaces.length; i++) {
    if (device.configs?.[0]?.interfaces?.[i]?.endpoints?.[0]?.attributes == 2) {
      let endpoint: usbManager.USBEndpoint = device.configs?.[0]?.interfaces?.[i]?.endpoints?.[0];
      let interfaces: usbManager.USBInterface = device.configs?.[0]?.interfaces?.[i];
      let ret: number = usbManager.claimInterface(devicepipe, interfaces);
      let buffer =  new Uint8Array(128);
      usbManager.bulkTransfer(devicepipe, endpoint, buffer).then((ret: number) => {
        console.info(`bulkTransfer = ${ret}`);
      }).catch((error: BusinessError) => {
        console.error(`bulkTransfer failed : ${error}`);
      });
    }
  }
}

```

