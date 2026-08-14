# ToggleOptions

Toggle的信息。 > **说明：** > > 为规范匿名对象的定义，API 18版本修改了此处的元素定义。其中，保留了历史匿名对象的起始版本信息，会出现外层元素@since版本号高于内层元素版本号的情况，但这不影响接口的使用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface ToggleOptions--><!--Device-unnamed-export declare interface ToggleOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isOn

```TypeScript
isOn?: boolean | undefined | Bindable<boolean>
```

开关是否打开。 true：打开；false：关闭。 默认值：false 该属性支持[\$\$](../../../ui/state-management/arkts-two-way-sync.md)双向绑定变量。 该属性支持[!!](../../../ui/state-management/arkts-new-binding.md#系统组件参数双向绑定)双向绑定变量。 **卡片能力（仅ArkTS-Dyn）：** 从API version 9开始，该接口支持在ArkTS卡片中使用。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。 **ArkTS-Dyn起始版本：** 8 **ArkTS-Sta起始版本：** 23

**类型：** boolean \| undefined \| [Bindable](arkts-na-common-bindable-i.md)&lt;boolean&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ToggleOptions-isOn?: boolean | undefined | Bindable<boolean>--><!--Device-ToggleOptions-isOn?: boolean | undefined | Bindable<boolean>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: ToggleType
```

开关的样式。 默认值：ToggleType.Switch **卡片能力（仅ArkTS-Dyn）：** 从API version 9开始，该接口支持在ArkTS卡片中使用。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。 **ArkTS-Dyn起始版本：** 8 **ArkTS-Sta起始版本：** 23

**类型：** [ToggleType](arkts-na-toggle-toggletype-e.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ToggleOptions-type: ToggleType--><!--Device-ToggleOptions-type: ToggleType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

