# destroyAbilityConnectionSession

## destroyAbilityConnectionSession

```TypeScript
function destroyAbilityConnectionSession(sessionId: int): void
```

销毁应用间的协同会话。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-abilityConnectionManager-function destroyAbilityConnectionSession(sessionId: int): void--><!--Device-abilityConnectionManager-function destroyAbilityConnectionSession(sessionId: int): void-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sessionId | int | 是 | 待销毁的协同会话ID。&lt;br /&gt;取值范围是大于100的整数。 |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

hilog.info(0x0000, 'testTag', 'destroyAbilityConnectionSession called');
let sessionId = 100;
abilityConnectionManager.destroyAbilityConnectionSession(sessionId);
```

ArkTS-Sta示例：

```TypeScript
import abilityConnectionManager from '@ohos.distributedsched.abilityConnectionManager';
import hilog from '@ohos.hilog';

hilog.info(0x0000, 'testTag', 'destroyAbilityConnectionSession called');
let sessionId = 100;
abilityConnectionManager.destroyAbilityConnectionSession(sessionId);
```

