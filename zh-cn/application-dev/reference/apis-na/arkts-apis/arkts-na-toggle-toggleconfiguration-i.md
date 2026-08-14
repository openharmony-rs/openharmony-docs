# ToggleConfiguration

开发者需要自定义class实现ContentModifier接口。继承自CommonConfiguration。

**继承/实现关系：** ToggleConfiguration extends CommonConfiguration<ToggleConfiguration>

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface ToggleConfiguration--><!--Device-unnamed-export declare interface ToggleConfiguration-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isOn

```TypeScript
isOn: boolean
```

开关是否打开。 true：开关打开；false：开关关闭。 默认值：false **ArkTS-Sta起始版本：** 23

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ToggleConfiguration-isOn: boolean--><!--Device-ToggleConfiguration-isOn: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## triggerChange

```TypeScript
triggerChange: Callback<boolean>
```

触发switch选中状态变化。 true：状态从关切换为开；false：状态从开切换为关。 **ArkTS-Sta起始版本：** 23

**类型：** [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;boolean&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ToggleConfiguration-triggerChange: Callback<boolean>--><!--Device-ToggleConfiguration-triggerChange: Callback<boolean>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

