# disableNfc

## 导入模块

```TypeScript
import { nfcController } from '@kit.ConnectivityKit';
```

## disableNfc

```TypeScript
function disableNfc(): void
```

关闭NFC开关，该接口只能被系统应用调用。

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_SECURE_SETTINGS

**系统能力：** SystemCapability.Communication.NFC.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [3100101](../errorcode-nfc.md#3100101-开关nfc异常) | The NFC state is abnormal in the service. |
