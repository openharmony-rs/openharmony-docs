# EditableLeftIconV2

```TypeScript
export declare class EditableLeftIconV2
```

Defines the left icon configuration class, which is decorated with **@ObservedV2** and supports state observation.

**Since:** 26.0.0

**Decorator:** @ObservedV2

<!--Device-unnamed-export declare class EditableLeftIconV2--><!--Device-unnamed-export declare class EditableLeftIconV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { EditableLeftIconTypeV2, EditableTitleBarV2, EditableLeftIconV2, EditableLeftIconV2Options, EditableTitleV2, EditableTitleV2Options, EditableTitleBarItemV2, EditableTitleBarItemV2Options, EditableTitleBarMenuItemV2, EditableTitleBarMenuItemV2Options, EditableSaveButtonV2, EditableSaveButtonV2Options, EditableTitleBarStyleV2, EditableTitleBarStyleV2Options } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(options?: EditableLeftIconV2Options)
```

A constructor used to create an **EditableLeftIconV2** instance.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableLeftIconV2-constructor(options?: EditableLeftIconV2Options)--><!--Device-EditableLeftIconV2-constructor(options?: EditableLeftIconV2Options)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [EditableLeftIconV2Options](arkts-arkui-arkui-advanced-editabletitlebarv2-editablelefticonv2options-i.md) | No | Options for the left icon configuration.<br>Default value: **undefined**. If this parameter is not passed, the default configuration is used. |

## onAction

```TypeScript
public onAction?: OnActionCallback
```

Callback triggered when the left icon is tapped. If not set, the Back type performs route return by default, and the Cancel type has no operation.

**Decorator:** @Trace

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableLeftIconV2-public onAction?: OnActionCallback--><!--Device-EditableLeftIconV2-public onAction?: OnActionCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## defaultFocus

```TypeScript
public defaultFocus: boolean
```

Whether to obtain focus by default.

**true**: Obtains focus.

**false**: Does not obtain focus.

Default value: **false**. If multiple operable areas in the title bar are set as the default focus, the first one in display order among the operable areas set as the default focus is the default focus.

**Decorator:** @Trace

**Type:** boolean

**Default:** false

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableLeftIconV2-public defaultFocus: boolean--><!--Device-EditableLeftIconV2-public defaultFocus: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## iconType

```TypeScript
public iconType: EditableLeftIconTypeV2
```

Type of the left icon, which determines the style and default tap behavior of the left icon. When the type is Back, route return is performed by default on tap. When the type is Cancel, there is no default operation on tap, and a custom callback must be configured through the **onAction** attribute.

Default value: **EditableLeftIconTypeV2.Back**.

**Decorator:** @Trace

**Type:** [EditableLeftIconTypeV2](arkts-arkui-arkui-advanced-editabletitlebarv2-editablelefticontypev2-e.md)

**Default:** EditableLeftIconTypeV2.Back

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableLeftIconV2-public iconType: EditableLeftIconTypeV2--><!--Device-EditableLeftIconV2-public iconType: EditableLeftIconTypeV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
