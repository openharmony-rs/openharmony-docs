# BindOptions

半模态、全模态的公共配置接口。

**起始版本：** 10

<!--Device-unnamed-declare interface BindOptions--><!--Device-unnamed-declare interface BindOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor?: ResourceColor
```

半模态页面的背板颜色。

默认值：Color.White。

**类型：** ResourceColor

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-BindOptions-backgroundColor?: ResourceColor--><!--Device-BindOptions-backgroundColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onAppear

```TypeScript
onAppear?: () => void
```

半模态页面显示（动画结束后）回调函数。

**类型：** () => void

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-BindOptions-onAppear?: () => void--><!--Device-BindOptions-onAppear?: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDisappear

```TypeScript
onDisappear?: () => void
```

半模态页面回退（动画结束后）回调函数。

**类型：** () => void

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-BindOptions-onDisappear?: () => void--><!--Device-BindOptions-onDisappear?: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onWillAppear

```TypeScript
onWillAppear?: () => void
```

半模态页面显示（动画开始前）回调函数。

**类型：** () => void

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BindOptions-onWillAppear?: () => void--><!--Device-BindOptions-onWillAppear?: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onWillDisappear

```TypeScript
onWillDisappear?: () => void
```

半模态页面回退（动画开始前）回调函数。

**说明：**

不允许在onWillDisappear函数中修改状态变量，可能会导致组件行为不稳定。

**类型：** () => void

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BindOptions-onWillDisappear?: () => void--><!--Device-BindOptions-onWillDisappear?: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

