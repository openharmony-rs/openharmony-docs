# SelectionMenuOptions

```TypeScript
declare interface SelectionMenuOptions
```

Sets menu options.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onAppear

```TypeScript
onAppear?: MenuOnAppearCallback
```

Callback invoked when the custom selection menu is displayed. If custom logic needs to be executed when the menu is displayed (for example, recording user operations or dynamically adjusting menu content), this parameter can be passed; if it is not passed, no additional callback is triggered.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onMenuHide

```TypeScript
onMenuHide?: MenuCallback
```

Callback invoked when the custom selection menu is hidden. If custom logic needs to be executed when the menu is hidden, this parameter can be passed; if it is not passed, no callback is triggered.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onMenuShow

```TypeScript
onMenuShow?: MenuCallback
```

Callback invoked when the custom selection menu is shown. If custom logic needs to be executed when the menu is shown, this parameter can be passed; if it is not passed, no callback is triggered.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## menuType

```TypeScript
menuType?: MenuType
```

Type of the custom context menu on selection.

Default value: **MenuType.SELECTION_MENU**

**Type:** [MenuType](../arkts-apis/arkts-arkui-menutype-e.md)

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onDisappear

```TypeScript
onDisappear?: Callback<void>
```

Callback invoked when the custom selection menu is closed. If custom logic needs to be executed when the menu is closed (for example, restoring the UI state or clearing temporary data), this parameter can be passed; if it is not passed, no additional callback is triggered.

**Type:** Callback&lt;void&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## previewMenuOptions

```TypeScript
previewMenuOptions?: PreviewMenuOptions
```

Options of the preview menu. This parameter takes effect only in RichEditor.

Since API version 26.0.0, this parameter also takes effect in the Text component.

If this parameter is not passed, the preview menu uses the default configuration.

**Type:** [PreviewMenuOptions](arkts-arkui-richeditor-comp-previewmenuoptions-i.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
