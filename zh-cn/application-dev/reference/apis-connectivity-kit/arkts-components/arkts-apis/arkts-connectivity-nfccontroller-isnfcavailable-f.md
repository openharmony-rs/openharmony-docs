# isNfcAvailable

## 导入模块

```TypeScript
import { nfcController } from '@kit.ConnectivityKit';
```

## isNfcAvailable

```TypeScript
function isNfcAvailable(): boolean
```

查询设备是否有NFC能力。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [canIUse](../../apis-arkui/arkts-apis/arkts-arkui-global-caniuse-f.md)("SystemCapability.Communication.NFC.Core")

**系统能力：** SystemCapability.Communication.NFC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true: 设备具备NFC能力， false: 设备不具备NFC能力。 |
