# ToggleConfiguration

开发者需要自定义class实现ContentModifier接口。继承自[CommonConfiguration](arkts-arkui-common-commonconfiguration-i.md)。

**继承/实现关系：** ToggleConfiguration extends [CommonConfiguration<ToggleConfiguration>]

**起始版本：** 12

<!--Device-unnamed-declare interface ToggleConfiguration extends CommonConfiguration<ToggleConfiguration>--><!--Device-unnamed-declare interface ToggleConfiguration extends CommonConfiguration<ToggleConfiguration>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enabled

```TypeScript
enabled: boolean
```

是否可以切换状态。

true：可以切换状态；false：不可以切换状态。

默认值：true

**类型：** boolean

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ToggleConfiguration-enabled: boolean--><!--Device-ToggleConfiguration-enabled: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isOn

```TypeScript
isOn: boolean
```

开关是否打开。

true：开关打开；false：开关关闭。

默认值：false

**类型：** boolean

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ToggleConfiguration-isOn: boolean--><!--Device-ToggleConfiguration-isOn: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## triggerChange

```TypeScript
triggerChange: Callback<boolean>
```

触发switch选中状态变化。

true：状态从关切换为开；false：状态从开切换为关。

**类型：** Callback<boolean>

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ToggleConfiguration-triggerChange: Callback<boolean>--><!--Device-ToggleConfiguration-triggerChange: Callback<boolean>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

