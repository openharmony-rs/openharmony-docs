# EditableSaveButtonV2Options

```TypeScript
export declare interface EditableSaveButtonV2Options
```

Defines the save button configuration options.

**Since:** 26.0.0

<!--Device-unnamed-export declare interface EditableSaveButtonV2Options--><!--Device-unnamed-export declare interface EditableSaveButtonV2Options-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { EditableLeftIconTypeV2, EditableTitleBarV2, EditableLeftIconV2, EditableLeftIconV2Options, EditableTitleV2, EditableTitleV2Options, EditableTitleBarItemV2, EditableTitleBarItemV2Options, EditableTitleBarMenuItemV2, EditableTitleBarMenuItemV2Options, EditableSaveButtonV2, EditableSaveButtonV2Options, EditableTitleBarStyleV2, EditableTitleBarStyleV2Options } from '@kit.ArkUI';
```

## onAction

```TypeScript
onAction?: OnActionCallback
```

Callback triggered when the save button is tapped. If not set, no response occurs when the button is tapped.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableSaveButtonV2Options-onAction?: OnActionCallback--><!--Device-EditableSaveButtonV2Options-onAction?: OnActionCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## defaultFocus

```TypeScript
defaultFocus?: boolean
```

Whether to obtain focus by default.

**true**: yes.

**false**: no.

Default value: **false**.

**Type:** boolean

**Default:** false

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableSaveButtonV2Options-defaultFocus?: boolean--><!--Device-EditableSaveButtonV2Options-defaultFocus?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isRequired

```TypeScript
isRequired?: boolean
```

Whether to display the save button.

**true**: yes.

**false**: no.

Default value: **true**.

**Type:** boolean

**Default:** true

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableSaveButtonV2Options-isRequired?: boolean--><!--Device-EditableSaveButtonV2Options-isRequired?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
