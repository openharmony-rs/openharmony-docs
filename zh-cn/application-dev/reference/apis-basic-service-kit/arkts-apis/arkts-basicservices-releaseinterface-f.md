# releaseInterface

## releaseInterface

```TypeScript
function releaseInterface(pipe: USBDevicePipe, iface: USBInterface): number
```

释放claim过的通信接口。

> **说明：**
>
> 在调用该接口前需要通过
> [usbManager.claimInterface](arkts-basicservices-claiminterface-f.md#claiminterface-1)
> claim通信接口。

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pipe | USBDevicePipe | 是 | 用于确定总线号和设备地址，需要调用[usbManager.connectDevice](arkts-basicservices-connectdevice-f.md#connectdevice-1)获取。 |
| iface | USBInterface | 是 | 用于确定需要释放接口的索引，需要调用[usbManager.getDevices](arkts-basicservices-getdevices-f.md#getdevices-1)获取设备信息并通过id确定唯一接口。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 释放接口成功返回0；释放接口失败返回其他错误码如下：- 88080389：服务未启动，可能原因：1.无设备插入；2.服务异常退出。- 88080486：服务初始化中，请稍后重试。- 88080488：无设备访问权限，请先调用[usbManager.requestRight](arkts-basicservices-requestright-f.md#requestright-1)接口申请授权。- -1：驱动异常。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br>1.Mandatory parameters are left unspecified.<br>2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |

**示例：**

```TypeScript
function releaseInterface() {
  let devicesList: Array<usbManager.USBDevice> = usbManager.getDevices();
  if (!devicesList || devicesList.length == 0) {
    console.info(`device list is empty`);
    return;
  }

  let device: usbManager.USBDevice = devicesList?.[0];
  usbManager.requestRight(device.name);
  let devicepipe: usbManager.USBDevicePipe = usbManager.connectDevice(device);
  let interfaces: usbManager.USBInterface = device.configs?.[0]?.interfaces?.[0];
  let ret: number = usbManager.claimInterface(devicepipe, interfaces);
  ret = usbManager.releaseInterface(devicepipe, interfaces);
  console.info(`releaseInterface = ${ret}`);
  usbManager.closePipe(devicepipe);
}

```

