# PatternLockController

PatternLock组件的控制器，用于重置组件状态和设置图案密码的正确或错误状态。

###### 导入对象

```ts
patternLockController: PatternLockController = new PatternLockController()
```

**起始版本：** 9

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor()
```

PatternLockController的构造函数。

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## reset

```TypeScript
reset()
```

重置组件状态。

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## setChallengeResult

```TypeScript
setChallengeResult(result: PatternLockChallengeResult): void
```

设置图案密码的正确或错误状态。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| result | PatternLockChallengeResult | 是 | 图案密码状态。包括正确和错误状态。 |

