# getAccessoryList

## getAccessoryList

```TypeScript
function getAccessoryList(): Array<Readonly<USBAccessory>>
```

获取当前已接入主机的USB配件列表。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-usbManager-function getAccessoryList(): Array<Readonly<USBAccessory>>--><!--Device-usbManager-function getAccessoryList(): Array<Readonly<USBAccessory>>-End-->

**系统能力：** SystemCapability.USB.USBManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;Readonly&lt;[USBAccessory](arkts-basicservices-usbmanager-usbaccessory-i.md)&gt;&gt; | 只读的USB配件列表。当前仅支持列表中包含1个USB配件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |
| [14400004](../../apis-basic-services-kit/errorcode-usb.md#14400004-服务异常) | Service exception. Possible causes:  &lt;br&gt;1. No accessory is plugged in. |

## 示例

```TypeScript
try {
  let accList: usbManager.USBAccessory[] = usbManager.getAccessoryList();
  console.info(`getAccessoryList success, accList: ${JSON.stringify(accList)}`);
} catch (error) {
  console.error(`getAccessoryList error ${error.code}, message is ${error.message}`);
}
```

