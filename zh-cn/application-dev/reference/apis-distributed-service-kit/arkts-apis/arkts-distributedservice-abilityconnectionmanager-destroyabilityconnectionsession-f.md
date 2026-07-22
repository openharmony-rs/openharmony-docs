# destroyAbilityConnectionSession

## 导入模块

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
```

## destroyAbilityConnectionSession

```TypeScript
function destroyAbilityConnectionSession(sessionId: number): void
```

销毁应用间的协同会话。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-abilityConnectionManager-function destroyAbilityConnectionSession(sessionId: int): void--><!--Device-abilityConnectionManager-function destroyAbilityConnectionSession(sessionId: int): void-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sessionId | number | 是 | 待销毁的协同会话ID。<br />取值范围是大于100的整数。 |

**示例：**

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

hilog.info(0x0000, 'testTag', 'destroyAbilityConnectionSession called');
let sessionId = 100;
abilityConnectionManager.destroyAbilityConnectionSession(sessionId);

```

