# getNfcState

## 导入模块

```TypeScript
import { nfcController } from '@kit.ConnectivityKit';
```

## getNfcState

```TypeScript
function getNfcState(): NfcState
```

查询NFC状态。

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NfcState](arkts-connectivity-nfccontroller-nfcstate-e.md) | NFC状态值，详细请见[NfcState]{ |

**示例**

```TypeScript
import { nfcController } from '@kit.ConnectivityKit';

// 查询nfc状态
let nfcState: nfcController.NfcState = nfcController.getNfcState();
console.info("nfcController on callback nfcstate: " + nfcState);
```
