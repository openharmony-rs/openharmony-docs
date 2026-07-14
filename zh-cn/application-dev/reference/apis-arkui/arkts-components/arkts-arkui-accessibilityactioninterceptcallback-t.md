# AccessibilityActionInterceptCallback

```TypeScript
declare type AccessibilityActionInterceptCallback = (action: AccessibilityAction) => AccessibilityActionInterceptResult
```

定义在可访问性操作拦截中使用的回调类型。
action的值表示可访问性动作类型。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本20开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| action | AccessibilityAction | 是 | 可访问性操作类型的枚举。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| AccessibilityActionInterceptResult | 继续执行操作、中断操作或事件冒泡的结果 |

