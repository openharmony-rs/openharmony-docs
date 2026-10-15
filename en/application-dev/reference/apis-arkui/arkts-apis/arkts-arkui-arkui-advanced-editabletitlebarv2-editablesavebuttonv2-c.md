# EditableSaveButtonV2

```TypeScript
export declare class EditableSaveButtonV2
```

Defines the save button configuration class, which is decorated by **@ObservedV2** and supports state observation.

**Since:** 26.0.0

**Decorator:** @ObservedV2

<!--Device-unnamed-export declare class EditableSaveButtonV2--><!--Device-unnamed-export declare class EditableSaveButtonV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { EditableLeftIconTypeV2, EditableTitleBarV2, EditableLeftIconV2, EditableLeftIconV2Options, EditableTitleV2, EditableTitleV2Options, EditableTitleBarItemV2, EditableTitleBarItemV2Options, EditableTitleBarMenuItemV2, EditableTitleBarMenuItemV2Options, EditableSaveButtonV2, EditableSaveButtonV2Options, EditableTitleBarStyleV2, EditableTitleBarStyleV2Options } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(options?: EditableSaveButtonV2Options)
```

A constructor used to create an **EditableSaveButtonV2** instance.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableSaveButtonV2-constructor(options?: EditableSaveButtonV2Options)--><!--Device-EditableSaveButtonV2-constructor(options?: EditableSaveButtonV2Options)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [EditableSaveButtonV2Options](arkts-arkui-arkui-advanced-editabletitlebarv2-editablesavebuttonv2options-i.md) | No | Save button configuration options.<br>Default value: **undefined**, which means the default configuration is used when this parameter is not passed. |

## onAction

```TypeScript
public onAction?: OnActionCallback
```

Callback triggered when the save button is tapped. If not set, tapping the button does not respond.

**Decorator:** @Trace

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableSaveButtonV2-public onAction?: OnActionCallback--><!--Device-EditableSaveButtonV2-public onAction?: OnActionCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## defaultFocus

```TypeScript
public defaultFocus: boolean
```

Whether to obtain focus by default.

**true**: yes.

**false**: no.

Default value: **false**.

If multiple operable areas in the title bar are set as the default focus, the first operable area in display order among those set as the default focus is the default focus.

**Decorator:** @Trace

**Type:** boolean

**Default:** false

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableSaveButtonV2-public defaultFocus: boolean--><!--Device-EditableSaveButtonV2-public defaultFocus: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isRequired

```TypeScript
public isRequired: boolean
```

Whether to display the save button.

**true**: yes.

**false**: no.

Default value: **true**.

**Decorator:** @Trace

**Type:** boolean

**Default:** true

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableSaveButtonV2-public isRequired: boolean--><!--Device-EditableSaveButtonV2-public isRequired: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
