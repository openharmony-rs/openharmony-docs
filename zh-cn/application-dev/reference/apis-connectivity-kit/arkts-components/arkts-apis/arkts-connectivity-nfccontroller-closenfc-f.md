# closeNfc

## 导入模块

```TypeScript
import { nfcController } from '@kit.ConnectivityKit';
```

## closeNfc

```TypeScript
function closeNfc(): boolean
```

关闭NFC开关。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [disableNfc](arkts-connectivity-nfccontroller-disablenfc-f.md)

**需要权限：** ohos.permission.MANAGE_SECURE_SETTINGS

**系统能力：** SystemCapability.Communication.NFC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true: 关闭NFC成功， false: 关闭NFC失败。 |
