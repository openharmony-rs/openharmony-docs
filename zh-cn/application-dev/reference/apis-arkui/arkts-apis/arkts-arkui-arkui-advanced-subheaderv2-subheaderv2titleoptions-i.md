# SubHeaderV2TitleOptions

用于构建SubHeaderV2Title对象。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

<!--Device-unnamed-export interface SubHeaderV2TitleOptions--><!--Device-unnamed-export interface SubHeaderV2TitleOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## id

```TypeScript
id?: string
```

标题id。需要为标题设置id的时候设置此参数，缺省时不设置此参数。 默认值：undefined，表示不设置标题id。

**类型：** string

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-SubHeaderV2TitleOptions-id?: string--><!--Device-SubHeaderV2TitleOptions-id?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## primaryTitle

```TypeScript
primaryTitle?: ResourceStr
```

标题内容。 当[SubHeaderV2](arkts-arkui-arkui-advanced-subheaderv2-subheaderv2-s.md#SubHeaderV2)中同时使用primaryTitle、secondaryTitle、icon属性时，primaryTitle将不会显示。 默认值：undefined

**类型：** [ResourceStr](../../apis-na/arkts-apis/arkts-na-resourcestr-t.md)

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SubHeaderV2TitleOptions-primaryTitle?: ResourceStr--><!--Device-SubHeaderV2TitleOptions-primaryTitle?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## primaryTitleModifier

```TypeScript
primaryTitleModifier?: TextModifier
```

设置标题文本属性，如设置主标题颜色、字体大小、字重等。 默认值：undefined

**类型：** TextModifier

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SubHeaderV2TitleOptions-primaryTitleModifier?: TextModifier--><!--Device-SubHeaderV2TitleOptions-primaryTitleModifier?: TextModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## secondaryTitle

```TypeScript
secondaryTitle?: ResourceStr
```

副标题内容。 默认值：undefined

**类型：** [ResourceStr](../../apis-na/arkts-apis/arkts-na-resourcestr-t.md)

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SubHeaderV2TitleOptions-secondaryTitle?: ResourceStr--><!--Device-SubHeaderV2TitleOptions-secondaryTitle?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## secondaryTitleModifier

```TypeScript
secondaryTitleModifier?: TextModifier
```

设置副标题文本属性，如设置副标题颜色、字体大小、字重等。 默认值：undefined

**类型：** TextModifier

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SubHeaderV2TitleOptions-secondaryTitleModifier?: TextModifier--><!--Device-SubHeaderV2TitleOptions-secondaryTitleModifier?: TextModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## titleAccessibilityText

```TypeScript
titleAccessibilityText?: ResourceStr
```

设置标题自定义朗读内容。 默认值：undefined 值为undefined时，默认朗读组件显示的标题内容。

**类型：** [ResourceStr](../../apis-na/arkts-apis/arkts-na-resourcestr-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-SubHeaderV2TitleOptions-titleAccessibilityText?: ResourceStr--><!--Device-SubHeaderV2TitleOptions-titleAccessibilityText?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

