# GestureModifier

开发者需要自定义class实现GestureModifier接口。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## applyGesture

```TypeScript
applyGesture(event: UIGestureEvent): void
```

手势更新函数。

开发者可根据需要自定义实现该方法，对组件设置需要绑定的手势，支持使用if/else语法进行动态设置。若在当次手势操作过程中触发了组件上的手势动态切换，该切换效果在当次手势结束（所有手指抬起）后的下一次手势操作中生效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | UIGestureEvent | 是 | UIGestureEvent对象，用于设置组件需要绑定的手势。 |

