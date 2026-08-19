# getPeerInfoById

## 导入模块

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
```

## getPeerInfoById

```TypeScript
function getPeerInfoById(sessionId: int): PeerInfo | undefined
```

获取指定会话中对端应用信息。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-abilityConnectionManager-function getPeerInfoById(sessionId: int): PeerInfo | undefined--><!--Device-abilityConnectionManager-function getPeerInfoById(sessionId: int): PeerInfo | undefined-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sessionId | int | 是 | 协同会话ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PeerInfo](arkts-distributedservice-abilityconnectionmanager-peerinfo-i.md) | 若存在对应PeerInfo，则返回接收端的协作应用信息。若sessionId未找到，则查询失败，返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

hilog.info(0x0000, 'testTag', 'getPeerInfoById called');
// sessionId需通过createAbilityConnectionSession接口创建并获取，此处仅为示例
let sessionId = 100;
// 获取指定会话中对端应用信息
const peerInfo = abilityConnectionManager.getPeerInfoById(sessionId);
```

ArkTS-Sta示例：

```TypeScript
import abilityConnectionManager from '@ohos.distributedsched.abilityConnectionManager';
import hilog from '@ohos.hilog';

hilog.info(0x0000, 'testTag', 'getPeerInfoById called');
// sessionId需通过createAbilityConnectionSession接口创建并获取，此处仅为示例
let sessionId = 100;
// 获取指定会话中对端应用信息
const peerInfo = abilityConnectionManager.getPeerInfoById(sessionId);
```

