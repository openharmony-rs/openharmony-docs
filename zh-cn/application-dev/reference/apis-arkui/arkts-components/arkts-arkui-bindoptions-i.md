# BindOptions

半模态、全模态的公共配置接口。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onAppear

```TypeScript
onAppear?: () => void
```

半模态页面显示（动画结束后）回调函数。不设置时不触发回调。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDisappear

```TypeScript
onDisappear?: () => void
```

半模态页面回退（动画结束后）回调函数。不设置时不触发回调。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onWillAppear

```TypeScript
onWillAppear?: () => void
```

半模态页面显示（动画开始前）回调函数。与onAppear的时序关系：onWillAppear在显示动画开始前触发，onAppear在显示动画结束后触发，两者可同时使用。如需在动画开始前做准备工作建议使用onWillAppear，如需在动画结束后做UI更新建议使用onAppear。不设置时不触发回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onWillDisappear

```TypeScript
onWillDisappear?: () => void
```

半模态页面回退（动画开始前）回调函数。与onDisappear的时序关系：onWillDisappear在回退动画开始前触发，onDisappear在回退动画结束后触发，两者可同时使用。如需在动画开始前做状态保存建议使用onWillDisappear，如需在动画结束后做资源释放建议使用onDisappear。不设置时不触发回调。

**说明：** 

不允许在onWillDisappear函数中修改状态变量，可能会导致组件行为不稳定。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor?: ResourceColor
```

半模态页面的背板颜色。

默认值：Color.White。

**说明：** 

设置systemMaterial属性时，该属性效果可能被覆盖，不建议与systemMaterial一起使用。

**类型：** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
