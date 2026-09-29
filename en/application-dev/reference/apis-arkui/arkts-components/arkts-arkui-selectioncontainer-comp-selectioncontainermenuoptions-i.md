# SelectionContainerMenuOptions

```TypeScript
export interface SelectionContainerMenuOptions
```

Provides the configuration options in the selection menu.

**Since:** 26.0.0

<!--Device-unnamed-export interface SelectionContainerMenuOptions--><!--Device-unnamed-export interface SelectionContainerMenuOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { OnMenuItemClickWithTextCallback, SelectionContainer, SelectionContainerAttribute, SelectionContainerEditMenuOptions, SelectionContainerInstance, SelectionContainerMenuOptions, SelectionContainerTextJoinStyle, SelectionContainerOptions, SelectionContainerController } from '@kit.ArkUI';
```

## onAppear

```TypeScript
onAppear?: Callback<string>
```

Triggered when the selection menu appears. The callback parameter is the selected text concatenated in the visual order of the Text components, and the concatenation method is determined by the textJoinStyle configuration. The default value is empty, and this callback is not triggered.

**Type:** Callback&lt;string&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-SelectionContainerMenuOptions-onAppear?: Callback<string>--><!--Device-SelectionContainerMenuOptions-onAppear?: Callback<string>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onDisappear

```TypeScript
onDisappear?: Callback<void>
```

Triggered when the selection menu disappears. The default value is empty, and this callback is not triggered.

**Type:** Callback&lt;void&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-SelectionContainerMenuOptions-onDisappear?: Callback<void>--><!--Device-SelectionContainerMenuOptions-onDisappear?: Callback<void>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onMenuHide

```TypeScript
onMenuHide?: Callback<string>
```

Triggered when the selection menu is hidden. The callback parameter is the selected text concatenated in the visual order of the Text components, and the concatenation method is determined by the textJoinStyle configuration. The default value is empty, and this callback is not triggered.

**Type:** Callback&lt;string&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-SelectionContainerMenuOptions-onMenuHide?: Callback<string>--><!--Device-SelectionContainerMenuOptions-onMenuHide?: Callback<string>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onMenuShow

```TypeScript
onMenuShow?: Callback<string>
```

Triggered when the selection menu is shown. The callback parameter is the selected text concatenated in the visual order of the Text components, and the concatenation method is determined by the textJoinStyle configuration. The default value is empty, and this callback is not triggered.

**Type:** Callback&lt;string&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-SelectionContainerMenuOptions-onMenuShow?: Callback<string>--><!--Device-SelectionContainerMenuOptions-onMenuShow?: Callback<string>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
