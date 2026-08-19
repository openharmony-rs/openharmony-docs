# RatingOptions

评分组件的信息。 > **说明：** > > 为规范匿名对象的定义，API 18版本修改了此处的元素定义。其中，保留了历史匿名对象的起始版本信息，会出现外层元素@since版本号高于内层元素版本号的情况，但这不影响接口的使用。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface RatingOptions--><!--Device-unnamed-export declare interface RatingOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## indicator

```TypeScript
indicator?: boolean
```

设置评分组件作为指示器使用，值为true时，不可改变评分，值为false时，可进行评分。 默认值：false **说明：** indicator=true时，默认组件高度height=12.0vp，组件width=height * stars。 indicator=false时，默认组件高度height=28.0vp，组件width=height * stars。 **卡片能力（仅ArkTS-Dyn）：** 从API version 9开始，该接口支持在ArkTS卡片中使用。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RatingOptions-indicator?: boolean--><!--Device-RatingOptions-indicator?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## rating

```TypeScript
rating: double | undefined | Bindable<double>
```

设置并接收评分值。取值为undefined时，按默认值处理。 默认值：0 取值范围： [0, stars] 小于0取0，大于stars取最大值stars。 该参数支持[\$\$](../../../ui/state-management/arkts-two-way-sync.md)双向绑定变量。 **卡片能力（仅ArkTS-Dyn）：** 从API version 9开始，该接口支持在ArkTS卡片中使用。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**类型：** double \| undefined \| [Bindable](arkts-na-common-bindable-i.md)&lt;double&gt;

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RatingOptions-rating: double | undefined | Bindable<double>--><!--Device-RatingOptions-rating: double | undefined | Bindable<double>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

