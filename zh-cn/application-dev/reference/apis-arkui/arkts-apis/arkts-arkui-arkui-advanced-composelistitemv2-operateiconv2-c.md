# OperateIconV2

列表项右侧图标元素的类型。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-export declare class OperateIconV2--><!--Device-unnamed-export declare class OperateIconV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(options?: OperateIconV2Options)
```

OperateIconV2的构造函数。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-OperateIconV2-constructor(options?: OperateIconV2Options)--><!--Device-OperateIconV2-constructor(options?: OperateIconV2Options)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [OperateIconV2Options](../../apis-na/arkts-apis/arkts-na-arkui-advanced-composelistitemv2-operateiconv2options-i.md) | 否 | 列表项右侧图标属性配置。&lt;br/&gt;默认不设置或设置为undefined时，按各属性的默认效果创建对象。 |

## accessibilityDescription

```TypeScript
@Trace
  public accessibilityDescription?: ResourceStr
```

列表项右侧图标/箭头的无障碍描述。此描述用于向用户详细解释当前组件，开发人员应为组件的这一属性提供较为详尽的文本说明，以协助用户理解即将执行的操作及其可能产生的后果。特别是当这些后果无法仅从组件的属性和无障碍文本中直接获知时。如果 组件同时具备文本属性和无障碍说明属性，当组件被选中时，系统将首先播报组件的文本属性，随后播报无障碍说明属性的内容。 默认值为"单指双击即可执行"。

**类型：** ResourceStr

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-OperateIconV2-@Trace  public accessibilityDescription?: ResourceStr--><!--Device-OperateIconV2-@Trace  public accessibilityDescription?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
@Trace
  public accessibilityLevel?: string
```

列表项右侧图标/箭头的无障碍重要性。用于控制当前项是否可被无障碍辅助服务所识别。 支持的值为: "auto":当前组件是否可被无障碍辅助服务识别由无障碍服务和ArkUI综合判断。 "yes":当前组件可被无障碍辅助服务所识别。 "no":当前组件不可被无障碍辅助服务所识别。 "no-hide-descendants":当前组件及其所有子组件不可被无障碍辅助服务所识别。 默认值:"auto"

**类型：** string

**默认值：** auto

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-OperateIconV2-@Trace  public accessibilityLevel?: string--><!--Device-OperateIconV2-@Trace  public accessibilityLevel?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityText

```TypeScript
@Trace
  public accessibilityText?: ResourceStr
```

列表项右侧图标/箭头的无障碍文本属性。当组件不包含文本属性时，屏幕朗读选中此组件时不播报，使用者无法清楚地知道当前选中了什么组件。为了解决此场景，开发人员可为不包含文字信息的组件设置无障碍文本，当屏幕朗读选中此组件时播报无障碍文本 的内容，帮助屏幕朗读的使用者清楚地知道自己选中了什么组件。 默认值:""

**类型：** ResourceStr

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-OperateIconV2-@Trace  public accessibilityText?: ResourceStr--><!--Device-OperateIconV2-@Trace  public accessibilityText?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## action

```TypeScript
@Trace
  public action?: OnActionCallback
```

列表项右侧图标/箭头点击回调。 默认不设置或设置为undefined时，点击图标/箭头不触发回调。

**类型：** [OnActionCallback](../../apis-na/arkts-apis/arkts-na-onactioncallback-t.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-OperateIconV2-@Trace  public action?: OnActionCallback--><!--Device-OperateIconV2-@Trace  public action?: OnActionCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## symbolStyle

```TypeScript
@Trace
  public symbolStyle?: SymbolGlyphModifier
```

列表项右侧Symbol图标/箭头资源，优先级大于value，同时设置时只显示Symbol图标。 默认不设置或设置为undefined时，不显示Symbol图标。

**类型：** [SymbolGlyphModifier](../arkts-components/arkts-arkui-symbolglyphmodifier-t.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-OperateIconV2-@Trace  public symbolStyle?: SymbolGlyphModifier--><!--Device-OperateIconV2-@Trace  public symbolStyle?: SymbolGlyphModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
@Trace
  public value: ResourceStr
```

列表项右侧图标/箭头资源。 同时设置symbolStyle时，只显示Symbol图标。

**类型：** ResourceStr

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-OperateIconV2-@Trace  public value: ResourceStr--><!--Device-OperateIconV2-@Trace  public value: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

