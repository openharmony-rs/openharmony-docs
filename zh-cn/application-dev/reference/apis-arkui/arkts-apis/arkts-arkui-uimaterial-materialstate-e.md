# MaterialState

```TypeScript
enum MaterialState
```

材质使能状态枚举，表示应用级沉浸式系统材质配置的状态。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DEFAULT

```TypeScript
DEFAULT = 0
```

默认模式。[弹出框Dialog](../../../ui/arkts-base-dialog-overview.md)、[即时反馈（Toast）](../../../ui/arkts-create-toast.md)、[AlphabetIndexer](../arkts-components/arkts-arkui-alphabetindexer-comp.md#alphabet_indexer)在组件本身未设置背景色、模糊参数和阴影参数时默认开启沉浸式系统材质；[Text](../arkts-components/arkts-arkui-text-comp.md#text)设置[copyOption](../arkts-components/arkts-arkui-text-comp-attribute.md#copyoption)后长按或双击触发的文本菜单默认开启沉浸式系统材质；其他组件由应用主动设置。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ENABLE

```TypeScript
ENABLE = 1
```

使能模式。[弹出框Dialog](../../../ui/arkts-base-dialog-overview.md)、[即时反馈（Toast）](../../../ui/arkts-create-toast.md)、[AlphabetIndexer](../arkts-components/arkts-arkui-alphabetindexer-comp.md#alphabet_indexer)、[ChipGroup](arkts-arkui-arkui-advanced-chipgroup-chipgroup-s.md)、[Chip](arkts-arkui-arkui-advanced-chip.md)、[Select](../arkts-components/arkts-arkui-select-comp.md#select)、[菜单控制](../arkts-components/arkts-arkui-common-comp.md#common)、[Toggle](../arkts-components/arkts-arkui-toggle-comp.md#toggle)、[SegmentButton](arkts-arkui-arkui-advanced-segmentbutton-segmentbutton-s.md)、[SegmentButtonV2](arkts-arkui-arkui-advanced-segmentbuttonv2.md)、[Slider](../arkts-components/arkts-arkui-slider-comp.md#slider)、[SelectionMenu](arkts-arkui-arkui-advanced-selectionmenu.md)组件默认开启沉浸式系统材质；[Text](../arkts-components/arkts-arkui-text-comp.md#text)设置[copyOption](../arkts-components/arkts-arkui-text-comp-attribute.md#copyoption)后长按或双击触发的文本菜单默认开启沉浸式系统材质。此模式下，沉浸式系统材质样式生效的优先级高于组件本身设置的背景色、模糊、阴影和边框样式。其他组件需开发者主动设置。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DISABLE

```TypeScript
DISABLE = 2
```

禁用模式。所有组件禁止开启沉浸式系统材质，即使主动为组件设置沉浸式系统材质参数也不会生效。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
