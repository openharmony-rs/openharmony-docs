# openNfc

## 导入模块

```TypeScript
import { nfcController } from '@kit.ConnectivityKit';
```

## openNfc

```TypeScript
function openNfc(): boolean
```

打开NFC开关。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [enableNfc](arkts-connectivity-nfccontroller-enablenfc-f.md)

**需要权限：** ohos.permission.MANAGE_SECURE_SETTINGS

**系统能力：** SystemCapability.Communication.NFC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true: 打开NFC成功， false: 打开NFC失败。 |
