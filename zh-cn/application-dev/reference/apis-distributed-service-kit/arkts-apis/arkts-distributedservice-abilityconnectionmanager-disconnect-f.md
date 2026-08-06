# disconnect

## disconnect

```TypeScript
function disconnect(sessionId: int): void
```

当协同业务执行完毕后，协同双端的任意一台设备，应断开UIAbility的连接，结束协同状态。

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-abilityConnectionManager-function disconnect(sessionId: int): void--><!--Device-abilityConnectionManager-function disconnect(sessionId: int): void-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sessionId | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 协同会话ID |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

hilog.info(0x0000, 'testTag', 'disconnectRemoteAbility begin');
let sessionId = 100;
abilityConnectionManager.disconnect(sessionId);
```

ArkTS-Sta示例：

```TypeScript
import abilityConnectionManager from '@ohos.distributedsched.abilityConnectionManager';
import hilog from '@ohos.hilog';

hilog.info(0x0000, 'testTag', 'disconnectRemoteAbility begin');
let sessionId = 100;
abilityConnectionManager.disconnect(sessionId);
```

