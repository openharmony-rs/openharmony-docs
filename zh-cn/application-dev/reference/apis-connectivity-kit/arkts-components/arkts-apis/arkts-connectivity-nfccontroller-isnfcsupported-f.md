# isNfcSupported

## 导入模块

```TypeScript
import { nfcController } from '@kit.ConnectivityKit';
```

## isNfcSupported

```TypeScript
function isNfcSupported(): boolean
```

查询设备是否有NFC能力。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NFC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true: 设备具备NFC能力， false: 设备不具备NFC能力。 |
