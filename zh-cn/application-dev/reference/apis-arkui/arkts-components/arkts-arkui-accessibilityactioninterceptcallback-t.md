# AccessibilityActionInterceptCallback

```TypeScript
declare type AccessibilityActionInterceptCallback = (action: AccessibilityAction) => AccessibilityActionInterceptResult
```

定义onAccessibilityActionIntercept中使用的回调类型。

@typedef { function } AccessibilityActionInterceptCallback

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本20开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| action | [AccessibilityAction](arkts-arkui-accessibilityaction-e.md) | 是 | 当前触发的无障碍控制操作类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AccessibilityActionInterceptResult](arkts-arkui-accessibilityactioninterceptresult-e.md) | 无障碍控制操作拦截结果，用于决定是否拦截当前组件的无障碍控制操作及后续处理方式。 |
