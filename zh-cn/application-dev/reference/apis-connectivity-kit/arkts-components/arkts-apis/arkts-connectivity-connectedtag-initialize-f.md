# initialize

## 导入模块

```TypeScript
import { connectedTag } from '@kit.ConnectivityKit';
```

## initialize

```TypeScript
function initialize(): void
```

初始化有源标签芯片。对有源标签进行读写操作前需调用本接口初始化一次，若想再次初始化需先调用[uninitialize](arkts-connectivity-connectedtag-uninitialize-f.md)。

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
    console.info("connectedTag initialize");
    connectedTag.initialize();
} catch (error) {
    console.error("initialize error:" + error);
}
```
