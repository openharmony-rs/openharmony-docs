# EditableLeftIconV2Options

```TypeScript
export declare interface EditableLeftIconV2Options
```

Defines the left icon configuration options.

**Since:** 26.0.0

<!--Device-unnamed-export declare interface EditableLeftIconV2Options--><!--Device-unnamed-export declare interface EditableLeftIconV2Options-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { EditableLeftIconTypeV2, EditableTitleBarV2, EditableLeftIconV2, EditableLeftIconV2Options, EditableTitleV2, EditableTitleV2Options, EditableTitleBarItemV2, EditableTitleBarItemV2Options, EditableTitleBarMenuItemV2, EditableTitleBarMenuItemV2Options, EditableSaveButtonV2, EditableSaveButtonV2Options, EditableTitleBarStyleV2, EditableTitleBarStyleV2Options } from '@kit.ArkUI';
```

## onAction

```TypeScript
onAction?: OnActionCallback
```

Callback triggered when the left icon is tapped. If not set, the Back type performs route return by default, and the Cancel type has no operation.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableLeftIconV2Options-onAction?: OnActionCallback--><!--Device-EditableLeftIconV2Options-onAction?: OnActionCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## defaultFocus

```TypeScript
defaultFocus?: boolean
```

Whether to obtain focus by default.

**true**: Obtains focus.

**false**: Does not obtain focus.

Default value: **false**.

If multiple operable areas of the title bar are set as the default focus, the first operable area in display order among those set as the default focus is the default focus.

**Type:** boolean

**Default:** false

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableLeftIconV2Options-defaultFocus?: boolean--><!--Device-EditableLeftIconV2Options-defaultFocus?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## iconType

```TypeScript
iconType?: EditableLeftIconTypeV2
```

Type of the left icon, which determines the style and default click behavior of the left icon. For the Back type, the route back operation is performed by default when clicked. For the Cancel type, no default operation is performed when clicked, and a custom callback is required.

Default value: **EditableLeftIconTypeV2.Back**.

**Type:** [EditableLeftIconTypeV2](arkts-arkui-arkui-advanced-editabletitlebarv2-editablelefticontypev2-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableLeftIconV2Options-iconType?: EditableLeftIconTypeV2--><!--Device-EditableLeftIconV2Options-iconType?: EditableLeftIconTypeV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
