# TextMenuItem

```TypeScript
declare interface TextMenuItem
```

TextMenuItem

**Since:** 12

<!--Device-unnamed-declare interface TextMenuItem--><!--Device-unnamed-declare interface TextMenuItem-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## content

```TypeScript
content: ResourceStr
```

Menu name.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextMenuItem-content: ResourceStr--><!--Device-TextMenuItem-content: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: ResourceStr
```

Menu icon.

Network images are not supported.

Default value: undefined, which means no menu icon is displayed.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextMenuItem-icon?: ResourceStr--><!--Device-TextMenuItem-icon?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## id

```TypeScript
id: TextMenuItemId
```

Menu ID.

**Type:** [TextMenuItemId](arkts-arkui-textmenuitemid-c.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextMenuItem-id: TextMenuItemId--><!--Device-TextMenuItem-id: TextMenuItemId-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## labelInfo

```TypeScript
labelInfo?: ResourceStr
```

Shortcut key hint.

This field is supported only on 2-in-1 devices.

Default value: undefined, which means no shortcut key hint is displayed.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-TextMenuItem-labelInfo?: ResourceStr--><!--Device-TextMenuItem-labelInfo?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
