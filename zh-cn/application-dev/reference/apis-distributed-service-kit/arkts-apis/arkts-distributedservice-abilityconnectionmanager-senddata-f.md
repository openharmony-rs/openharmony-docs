# sendData

## sendData

```TypeScript
function sendData(sessionId: int, data: ArrayBuffer): Promise<void>
```

应用连接成功后，设备A或设备B可向对端设备发送[ArrayBuffer](../../../arkts-utils/arraybuffer-object.md)字节流。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-abilityConnectionManager-function sendData(sessionId: int, data: ArrayBuffer): Promise<void>--><!--Device-abilityConnectionManager-function sendData(sessionId: int, data: ArrayBuffer): Promise<void>-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sessionId | int | 是 | 协同会话ID。 |
| data | ArrayBuffer | 是 | 字节流信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { util } from '@kit.ArkTS';

let textEncoder = util.TextEncoder.create("utf-8");
const arrayBuffer  = textEncoder.encodeInto("data send success");

let sessionId = 100;
abilityConnectionManager.sendData(sessionId, arrayBuffer.buffer).then(() => {
  hilog.info(0x0000, 'testTag', "sendData success");
}).catch(() => {
  hilog.error(0x0000, 'testTag', "sendData failed");
})
```

ArkTS-Sta示例：

```TypeScript
import abilityConnectionManager from '@ohos.distributedsched.abilityConnectionManager';
import hilog from '@ohos.hilog';
import util from '@ohos.util';

let textEncoder = util.TextEncoder.create("utf-8");

const arrayBuffer = textEncoder.encodeInto("data send success");

let sessionId = 100;
abilityConnectionManager.sendData(sessionId, arrayBuffer.buffer).then(() => {
  hilog.info(0x0000, 'testTag', "sendData success");
}).catch(() => {
  hilog.error(0x0000, 'testTag', "sendData failed");
})
```

