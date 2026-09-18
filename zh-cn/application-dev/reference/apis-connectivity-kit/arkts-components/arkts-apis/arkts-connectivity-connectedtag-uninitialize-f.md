# uninitialize

## 导入模块

```TypeScript
import { connectedTag } from '@kit.ConnectivityKit';
```

## uninitialize

```TypeScript
function uninitialize(): void
```

卸载有源标签芯片资源。

**起始版本：** 9

**需要权限：** ohos.permission.NFC_TAG

**系统能力：** SystemCapability.Communication.ConnectedTag

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [3200101](../errorcode-nfc.md#3200101-有源nfc标签状态异常) | Connected NFC tag running state is abnormal in service. |

**示例**

```TypeScript
import { connectedTag } from '@kit.ConnectivityKit';

try {
    console.info("connectedTag uninitialize");
    connectedTag.uninitialize();
} catch (error) {
    console.error("connectedTag error: " + error);
}
```
