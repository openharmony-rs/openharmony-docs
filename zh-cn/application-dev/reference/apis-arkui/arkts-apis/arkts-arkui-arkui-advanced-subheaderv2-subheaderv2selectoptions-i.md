# SubHeaderV2SelectOptions

用于构建SubHeaderV2Select对象。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

<!--Device-unnamed-export interface SubHeaderV2SelectOptions--><!--Device-unnamed-export interface SubHeaderV2SelectOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## defaultFocus

```TypeScript
defaultFocus?: boolean
```

下拉按钮是否为默认焦点。 true：下拉按钮是默认焦点。 false：下拉按钮不是默认焦点。 默认值：false

**类型：** boolean

**默认值：** false

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SubHeaderV2SelectOptions-defaultFocus?: boolean--><!--Device-SubHeaderV2SelectOptions-defaultFocus?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## id

```TypeScript
id?: string
```

下拉按钮id。需要为下拉按钮设置id的时候设置此参数，缺省时不设置此参数。 默认值：undefined，表示不设置下拉按钮id。

**类型：** string

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-SubHeaderV2SelectOptions-id?: string--><!--Device-SubHeaderV2SelectOptions-id?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onSelect

```TypeScript
onSelect?: SubHeaderV2SelectOnSelect
```

下拉菜单选中某一项的回调。 默认值：undefined

**类型：** [SubHeaderV2SelectOnSelect](arkts-arkui-subheaderv2selectonselect-t.md)

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SubHeaderV2SelectOptions-onSelect?: SubHeaderV2SelectOnSelect--><!--Device-SubHeaderV2SelectOptions-onSelect?: SubHeaderV2SelectOnSelect-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## options

```TypeScript
options: SelectOption[]
```

下拉选项内容。

**类型：** [SelectOption](../../apis-na/arkts-apis/arkts-na-select-selectoption-i.md)[]

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SubHeaderV2SelectOptions-options: SelectOption[]--><!--Device-SubHeaderV2SelectOptions-options: SelectOption[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedContent

```TypeScript
selectedContent?: ResourceStr
```

设置下拉按钮本身的文本内容。默认值：''。从API version 20开始，支持Resource类型。

**类型：** [ResourceStr](../../apis-na/arkts-apis/arkts-na-resourcestr-t.md)

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SubHeaderV2SelectOptions-selectedContent?: ResourceStr--><!--Device-SubHeaderV2SelectOptions-selectedContent?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedIndex

```TypeScript
selectedIndex?: number
```

设置下拉菜单初始选项的索引。 第一项的索引为0。 当不设置selectedIndex属性时， 默认选择值为-1，菜单项不选中。

**类型：** number

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SubHeaderV2SelectOptions-selectedIndex?: number--><!--Device-SubHeaderV2SelectOptions-selectedIndex?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

