# @ohos.ability.particleAbility

particleAbility模块提供了操作Data和Service类型的Ability的能力，包括启动、停止指定的particleAbility，获取dataAbilityHelper，连接、断连指定的ServiceAbility等。

**起始版本：** 7

<!--Device-unnamed-declare namespace particleAbility--><!--Device-unnamed-declare namespace particleAbility-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

## 导入模块

```TypeScript
import { particleAbility } from '@kit.AbilityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [acquireDataAbilityHelper](arkts-ability-particleability-acquiredataabilityhelper-f.md#acquiredataabilityhelper-1) | 获取dataAbilityHelper对象。 |
| [cancelBackgroundRunning](arkts-ability-particleability-cancelbackgroundrunning-f.md#cancelbackgroundrunning-1) | 向系统申请取消长时任务。使用callback异步回调。 |
| [cancelBackgroundRunning](arkts-ability-particleability-cancelbackgroundrunning-f.md#cancelbackgroundrunning-2) | 向系统申请取消长时任务。使用Promise异步回调。 |
| [connectAbility](arkts-ability-particleability-connectability-f.md#connectability-1) | 将当前ability与指定的ServiceAbility进行连接。 |
| [disconnectAbility](arkts-ability-particleability-disconnectability-f.md#disconnectability-1) | 断开当前ability与指定ServiceAbility的连接。使用callback异步回调。 |
| [disconnectAbility](arkts-ability-particleability-disconnectability-f.md#disconnectability-2) | 断开当前ability与指定ServiceAbility的连接。使用Promise异步回调。 |
| [startAbility](arkts-ability-particleability-startability-f.md#startability-1) | 启动指定的particleAbility。使用callback异步回调。 |
| [startAbility](arkts-ability-particleability-startability-f.md#startability-2) | 启动指定的particleAbility。使用Promise异步回调。 |
| [startBackgroundRunning](arkts-ability-particleability-startbackgroundrunning-f.md#startbackgroundrunning-1) | 向系统申请长时任务。使用callback异步回调。 |
| [startBackgroundRunning](arkts-ability-particleability-startbackgroundrunning-f.md#startbackgroundrunning-2) | 向系统申请长时任务。使用Promise异步回调。 |
| [terminateSelf](arkts-ability-particleability-terminateself-f.md#terminateself-1) | 销毁当前particleAbility。使用callback异步回调。 |
| [terminateSelf](arkts-ability-particleability-terminateself-f.md#terminateself-2) | 销毁当前particleAbility。使用Promise异步回调。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ErrorCode](arkts-ability-particleability-errorcode-e.md) | 定义启动Ability时返回的错误码。 |

