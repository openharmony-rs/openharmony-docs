# SubHeaderV2Select

下拉选择器配置项，包含下拉选项内容、选中状态及回调事件。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

<!--Device-unnamed-export declare class SubHeaderV2Select--><!--Device-unnamed-export declare class SubHeaderV2Select-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(options: SubHeaderV2SelectOptions)
```

select内容以及事件构造函数。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SubHeaderV2Select-constructor(options: SubHeaderV2SelectOptions)--><!--Device-SubHeaderV2Select-constructor(options: SubHeaderV2SelectOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [SubHeaderV2SelectOptions](arkts-arkui-arkui-advanced-subheaderv2-subheaderv2selectoptions-i.md) | 是 | 下拉选项信息。 |

## defaultFocus

```TypeScript
@Trace
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

<!--Device-SubHeaderV2Select-@Trace  defaultFocus?: boolean--><!--Device-SubHeaderV2Select-@Trace  defaultFocus?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## id

```TypeScript
@Trace
  id?: string
```

下拉按钮id。需要为下拉按钮设置id的时候设置此参数，缺省时不设置此参数。 默认值：undefined，表示不设置下拉按钮id。

**类型：** string

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-SubHeaderV2Select-@Trace  id?: string--><!--Device-SubHeaderV2Select-@Trace  id?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onSelect

```TypeScript
@Trace
  onSelect?: SubHeaderV2SelectOnSelect
```

Sets the onSelect of the SubHeaderV2SelectOptions.

**类型：** [SubHeaderV2SelectOnSelect](arkts-arkui-subheaderv2selectonselect-t.md)

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SubHeaderV2Select-@Trace  onSelect?: SubHeaderV2SelectOnSelect--><!--Device-SubHeaderV2Select-@Trace  onSelect?: SubHeaderV2SelectOnSelect-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## options

```TypeScript
@Trace
  options: SelectOption[]
```

Sets the options of the SubHeaderV2SelectOptions.

**类型：** [SelectOption](../../apis-na/arkts-apis/arkts-na-select-selectoption-i.md)[]

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SubHeaderV2Select-@Trace  options: SelectOption[]--><!--Device-SubHeaderV2Select-@Trace  options: SelectOption[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedContent

```TypeScript
@Trace selectedContent?: ResourceStr
```

**类型：** [ResourceStr](../../apis-na/arkts-apis/arkts-na-resourcestr-t.md)

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-SubHeaderV2Select-@Trace selectedContent?: ResourceStr--><!--Device-SubHeaderV2Select-@Trace selectedContent?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedIndex

```TypeScript
@Trace
  selectedIndex?: number
```

Sets the selected index of the SubHeaderV2SelectOptions.

**类型：** number

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SubHeaderV2Select-@Trace  selectedIndex?: number--><!--Device-SubHeaderV2Select-@Trace  selectedIndex?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

