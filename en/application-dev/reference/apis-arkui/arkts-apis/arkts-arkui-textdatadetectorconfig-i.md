# TextDataDetectorConfig

```TypeScript
declare interface TextDataDetectorConfig
```

This configuration is only available for the [Text](../arkts-components/arkts-arkui-text-comp.md) and [RichEditor](../arkts-components/arkts-arkui-richeditor-comp.md) components.

**Since:** 11

<!--Device-unnamed-declare interface TextDataDetectorConfig--><!--Device-unnamed-declare interface TextDataDetectorConfig-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color?: ResourceColor
```

Sets the entity color after text recognition succeeds.

Default value: **'#ff0a59f7'**, which indicates blue (with 100% opacity).

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextDataDetectorConfig-color?: ResourceColor--><!--Device-TextDataDetectorConfig-color?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## decoration

```TypeScript
decoration?: DecorationStyleInterface
```

Sets the decoration line style of the entity after text recognition succeeds.

Default value:

{

 type: TextDecorationType.Underline,

 color: the same as the entity color,

 style: TextDecorationStyle.SOLID

}

**Type:** [DecorationStyleInterface](arkts-arkui-decorationstyleinterface-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextDataDetectorConfig-decoration?: DecorationStyleInterface--><!--Device-TextDataDetectorConfig-decoration?: DecorationStyleInterface-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enablePreviewMenu

```TypeScript
enablePreviewMenu?: boolean
```

Sets whether to enable the preview menu displayed on long press after text recognition. The value **true** indicates enabled, and **false** indicates disabled.

Default value: **false**

When [copyOptions](../arkts-components/arkts-arkui-richeditor-comp-attribute.md#copyoptions) is set to **None**, the preview menu is not displayed on long press of an AI entity even if **enablePreviewMenu** is set to **true**.

The actual device types supported by this API (phones and tablets) are fewer than those supported by its system capability (phones, 2-in-1 devices, tablets, TVs, cars, and wearables). Due to hardware form limitations, this API does not respond on 2-in-1 devices, TVs, cars, and wearables.

**Type:** boolean

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextDataDetectorConfig-enablePreviewMenu?: boolean--><!--Device-TextDataDetectorConfig-enablePreviewMenu?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onDetectResultUpdate

```TypeScript
onDetectResultUpdate?: Callback<string>
```

Callback invoked when text recognition succeeds.

Default value: **undefined**, which means the callback is not triggered.

**Type:** Callback&lt;string&gt;

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextDataDetectorConfig-onDetectResultUpdate?: Callback<string>--><!--Device-TextDataDetectorConfig-onDetectResultUpdate?: Callback<string>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## types

```TypeScript
types: TextDataDetectorType[]
```

Sets the entity types for text recognition. When **types** is set to **null** or **[]**, all types of entities are recognized; otherwise, only the specified types of entities are recognized.

**Type:** [TextDataDetectorType](arkts-arkui-textdatadetectortype-e.md)[]

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextDataDetectorConfig-types: TextDataDetectorType[]--><!--Device-TextDataDetectorConfig-types: TextDataDetectorType[]-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
