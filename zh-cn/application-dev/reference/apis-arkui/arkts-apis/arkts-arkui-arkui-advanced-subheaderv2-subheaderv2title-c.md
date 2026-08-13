# SubHeaderV2Title

标题设置项。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

<!--Device-unnamed-export declare class SubHeaderV2Title--><!--Device-unnamed-export declare class SubHeaderV2Title-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(options: SubHeaderV2TitleOptions)
```

标题内容信息SubHeaderV2Title构造函数。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SubHeaderV2Title-constructor(options: SubHeaderV2TitleOptions)--><!--Device-SubHeaderV2Title-constructor(options: SubHeaderV2TitleOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [SubHeaderV2TitleOptions](arkts-arkui-arkui-advanced-subheaderv2-subheaderv2titleoptions-i.md) | 是 | 标题内容信息。 |

## id

```TypeScript
@Trace
  id?: string
```

标题id。需要为标题设置id的时候设置此参数，缺省时不设置此参数。 默认值：undefined，表示不设置标题id。

**类型：** string

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-SubHeaderV2Title-@Trace  id?: string--><!--Device-SubHeaderV2Title-@Trace  id?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## primaryTitle

```TypeScript
@Trace
  primaryTitle?: ResourceStr
```

The first line text of content area.

**类型：** [ResourceStr](../../apis-na/arkts-apis/arkts-na-resourcestr-t.md)

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SubHeaderV2Title-@Trace  primaryTitle?: ResourceStr--><!--Device-SubHeaderV2Title-@Trace  primaryTitle?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## primaryTitleModifier

```TypeScript
@Trace
  primaryTitleModifier?: TextModifier
```

Text modifier for primary title.

**类型：** TextModifier

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SubHeaderV2Title-@Trace  primaryTitleModifier?: TextModifier--><!--Device-SubHeaderV2Title-@Trace  primaryTitleModifier?: TextModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## secondaryTitle

```TypeScript
@Trace
  secondaryTitle?: ResourceStr
```

The secondary line text of content area.

**类型：** [ResourceStr](../../apis-na/arkts-apis/arkts-na-resourcestr-t.md)

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SubHeaderV2Title-@Trace  secondaryTitle?: ResourceStr--><!--Device-SubHeaderV2Title-@Trace  secondaryTitle?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## secondaryTitleModifier

```TypeScript
@Trace
  secondaryTitleModifier?: TextModifier
```

Text modifier for secondary title.

**类型：** TextModifier

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SubHeaderV2Title-@Trace  secondaryTitleModifier?: TextModifier--><!--Device-SubHeaderV2Title-@Trace  secondaryTitleModifier?: TextModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## titleAccessibilityText

```TypeScript
@Trace
  titleAccessibilityText?: ResourceStr
```

设置标题自定义朗读内容。 默认值：undefined 值为undefined时，默认朗读组件显示的标题内容。

**类型：** [ResourceStr](../../apis-na/arkts-apis/arkts-na-resourcestr-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-SubHeaderV2Title-@Trace  titleAccessibilityText?: ResourceStr--><!--Device-SubHeaderV2Title-@Trace  titleAccessibilityText?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

