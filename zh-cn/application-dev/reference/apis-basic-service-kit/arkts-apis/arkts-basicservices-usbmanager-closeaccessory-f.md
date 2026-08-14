# closeAccessory

## closeAccessory

```TypeScript
function closeAccessory(accessoryHandle: USBAccessoryHandle): void
```

关闭配件文件描述符。 需要调用[usbManager.openAccessory](arkts-basicservices-usbmanager-openaccessory-f.md#openAccessory)获取配件列表，得到 [USBAccessoryHandle](arkts-basicservices-usbmanager-usbaccessoryhandle-i.md#USBAccessoryHandle)作为参数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-usbManager-function closeAccessory(accessoryHandle: USBAccessoryHandle): void--><!--Device-usbManager-function closeAccessory(accessoryHandle: USBAccessoryHandle): void-End-->

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accessoryHandle | [USBAccessoryHandle](arkts-basicservices-usbmanager-usbaccessoryhandle-i.md) | 是 | USB配件句柄。需要通过 [openAccessory](arkts-basicservices-usbmanager-openaccessory-f.md#openAccessory)获取。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  &lt;br&gt;1. Mandatory parameters are left unspecified.  &lt;br&gt;2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |
| [14400004](../../apis-basic-services-kit/errorcode-usb.md#14400004-服务异常) | Service exception. Possible causes:  &lt;br&gt;1. No accessory is plugged in. |

## 示例

```TypeScript
async function closeAccessory() {
  try {
    let accList: usbManager.USBAccessory[] = usbManager.getAccessoryList();
    let flag = await usbManager.requestAccessoryRight(accList?.[0]);
    if (!flag) {
      return;
    }
    let handle = usbManager.openAccessory(accList?.[0]);
    usbManager.closeAccessory(handle);
    console.info(`closeAccessory success`);
  } catch (error) {
    console.error(`closeAccessory error ${error.code}, message is ${error.message}`);
  }
}
```

