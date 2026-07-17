# reject

## 导入模块

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
```

## reject

```TypeScript
function reject(token: string, reason: string): void
```

在跨端应用协同过程中，在拒绝对端的连接请求后，向对端发送拒绝原因。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-abilityConnectionManager-function reject(token: string, reason: string): void--><!--Device-abilityConnectionManager-function reject(token: string, reason: string): void-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| token | string | 是 | 用于协作服务管理的令牌。 |
| reason | string | 是 | 连接被拒绝的原因。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

export default class EntryAbility extends UIAbility {
    onCollaborate(wantParam: Record<string, Object>): AbilityConstant.CollaborateResult {
      hilog.info(0x0000, 'testTag', '%{public}s', 'on collaborate');
      let collabParam = wantParam["ohos.extra.param.key.supportCollaborateIndex"] as Record<string, Object>;
      const collabToken = collabParam["ohos.dms.collabToken"] as string;
      const reason = 'test';
      hilog.info(0x0000, 'testTag', 'reject begin');
      abilityConnectionManager.reject(collabToken, reason);
      return AbilityConstant.CollaborateResult.REJECT;
    }
}


```

