# ButtonConfiguration

开发者需要自定义class实现ContentModifier接口。继承自CommonConfiguration。

**继承/实现关系：** ButtonConfiguration extends CommonConfiguration<ButtonConfiguration>

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface ButtonConfiguration--><!--Device-unnamed-export declare interface ButtonConfiguration-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## label

```TypeScript
label: string
```

Button的文本标签。 **说明：**当文本字符的长度超过按钮本身的宽度时，文本将会被截断。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ButtonConfiguration-label: string--><!--Device-ButtonConfiguration-label: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## pressed

```TypeScript
pressed: boolean
```

指示是否按下Button。 true：按下；false：未按下。 默认值：false **说明：** 此按压属性生效区域大小为原本Button组件的大小，而非build出来的新组件大小。若新build出来的组件超过原本组件的大小，那么超出部分按压不触发。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ButtonConfiguration-pressed: boolean--><!--Device-ButtonConfiguration-pressed: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## triggerClick

```TypeScript
triggerClick: ButtonTriggerClickCallback
```

使用builder新构建出来组件的点击事件。

**类型：** [ButtonTriggerClickCallback](arkts-na-buttontriggerclickcallback-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ButtonConfiguration-triggerClick: ButtonTriggerClickCallback--><!--Device-ButtonConfiguration-triggerClick: ButtonTriggerClickCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

