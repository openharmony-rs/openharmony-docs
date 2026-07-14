# BaseGestureHandlingProposal

智慧手势处理基类。当通过[registerMonitor](arkts-arkui-smartgesturecontroller-c.md#registermonitor-1)接口动态自定义智慧手势行为时，其回调参数类型为具体的子类类型实例。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## action

```TypeScript
action: SmartGestureAction
```

智慧手势最终执行动作。

**类型：** SmartGestureAction

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## operateIntention

```TypeScript
operateIntention: OperateIntention
```

智慧手势底层操作意图。

**类型：** OperateIntention

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

