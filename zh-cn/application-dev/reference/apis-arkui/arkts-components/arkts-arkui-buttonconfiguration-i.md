# ButtonConfiguration

开发者需要自定义class实现ContentModifier接口。继承自CommonConfiguration。

**继承/实现关系：** ButtonConfiguration extends CommonConfiguration<ButtonConfiguration>

**起始版本：** 12

<!--Device-unnamed-declare interface ButtonConfiguration--><!--Device-unnamed-declare interface ButtonConfiguration-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## label

```TypeScript
label: string
```

Button的文本标签，用于标识按钮的功能。 **说明：**当文本字符的长度超过按钮本身的宽度时，文本将会被截断。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ButtonConfiguration-label: string--><!--Device-ButtonConfiguration-label: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## pressed

```TypeScript
pressed: boolean
```

指示是否按下Button。 true：按下；false：未按下。 默认值：false **说明：** 此按压属性生效区域大小为原本Button组件的大小，而非build出来的新组件大小。

**类型：** boolean

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ButtonConfiguration-pressed: boolean--><!--Device-ButtonConfiguration-pressed: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## triggerClick

```TypeScript
triggerClick: ButtonTriggerClickCallback
```

点击事件回调，用于处理使用builder新构建出来组件的点击操作。

**类型：** [ButtonTriggerClickCallback](arkts-arkui-buttontriggerclickcallback-t.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ButtonConfiguration-triggerClick: ButtonTriggerClickCallback--><!--Device-ButtonConfiguration-triggerClick: ButtonTriggerClickCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

