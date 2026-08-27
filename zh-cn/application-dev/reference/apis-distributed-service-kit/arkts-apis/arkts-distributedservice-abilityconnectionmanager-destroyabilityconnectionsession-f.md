# destroyAbilityConnectionSession

## 导入模块

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
```

## destroyAbilityConnectionSession

```TypeScript
function destroyAbilityConnectionSession(sessionId: number): void
```

销毁应用间的协同会话，与createAbilityConnectionSession配对使用用于释放会话资源。 此接口需在成功创建协同会话后调用。销毁会话会释放相关资源，建议先调用disconnect断开连接后再销毁会话。 不调用此方法会导致资源泄漏。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sessionId | number | 是 | 待销毁的协同会话ID。取值范围是不小于100的整数。 传入小于100的值或不存在的协同会话ID时返回错误码401。 |

**示例**

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

hilog.info(0x0000, 'testTag', 'destroyAbilityConnectionSession called');
let sessionId = 100;
abilityConnectionManager.destroyAbilityConnectionSession(sessionId);
```
