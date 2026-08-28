# @ohos.inputMethod.Panel (Input Method Panel)

<!--Kit: IME Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @codexu62-->
<!--Designer: @andeszhang-->
<!--Tester: @murphy84-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=c9f68a28229d3fb5da602baa0bfb8e542d407a50 translatedAt=2026-08-25T01:24:57.620Z pushedAt=2026-08-26T09:18:14.732Z -->

The **@ohos.inputMethod.Panel** module provides data definitions for input method panel attributes, supporting configuration of the panel type and display state. It is applicable to scenarios that require fine-grained control over the display behavior of the input method panel.

This module serves as a data module for input method panel attributes. It defines the **PanelInfo** interface and two enum types, **PanelType** and **PanelFlag**, to specify the input method panel type (soft keyboard or status bar) and display state (fixed, floating, or candidate).


This module offers capabilities to configure input method panel attributes. An input method app can specify the panel type and state via **PanelInfo** to implement panels in different forms: fixed soft keyboard (default, anchored at the bottom of the screen), floating soft keyboard (freely draggable), and candidate panel (displays candidate words in an independent window, with visibility controlled by you).

Use this module when an input method app needs to create and configure an input method panel. Typical scenarios include creating a default fixed soft keyboard panel, creating a floating keyboard that supports free dragging, or creating a candidate word panel to show input candidates.

> **NOTE**
>
>The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.

The data type must be used in combination with the APIs of the **@ohos.inputMethodEngine** module. Pass **PanelInfo** when creating a panel using **InputMethodAbility.createPanel()**, to specify the panel type and state. Typical usage process: construct **PanelInfo** → pass it through **createPanel()** → the system creates a panel of the corresponding type accordingly. Different **PanelFlag** values correspond to distinct panel behaviors: a fixed panel stays anchored at the screen bottom, a floating panel can be dragged freely, and the visibility of a candidate panel is controlled by you.

Key interfaces and enums defined in this module are as follows:

| Interface/Type | Description |
|---|---|
| PanelInfo | Interface for input method panel attribute information. Contains two **properties**: **type** (panel type) and **flag** (panel state type, default value: **FLAG_FIXED**), used to describe the type and display form of an input method panel. |
| PanelType | Enum for input method panel types, which defines panel categories: **SOFT_KEYBOARD** (soft keyboard, value **0**) and **STATUS_BAR** (status bar, value **1**). |
| PanelFlag | Enum for input method panel state types, which defines panel display states: **FLAG_FIXED** (fixed, value **0**), **FLAG_FLOATING** (floating, value **1**), **FLAG_CANDIDATE** (candidate, value **2**). The visibility of a candidate‑state panel is controlled by you. |

This module is a pure data definition module. **PanelInfo**, as the panel attribute configuration, must be used in combination with APIs of other modules. A typical combination is: in the **@ohos.inputMethodEngine** module, pass **PanelInfo** to specify the panel type and state when creating a panel through **InputMethodAbility.createPanel()**.

```typescript
// The following is pseudocode for illustrating the calling logic.
import { PanelType, PanelFlag } from '@kit.IMEKit';

// 1. Configure attributes for a fixed soft‑keyboard panel.
let softKeyboardFixed = {
  type: PanelType.SOFT_KEYBOARD,
  flag: PanelFlag.FLAG_FIXED
};

// 2. Configure attributes for a floating soft‑keyboard panel.
let softKeyboardFloating = {
  type: PanelType.SOFT_KEYBOARD,
  flag: PanelFlag.FLAG_FLOATING
};

// 3. Configure attributes for a candidate‑state panel.
let candidatePanel = {
  type: PanelType.SOFT_KEYBOARD,
  flag: PanelFlag.FLAG_CANDIDATE
};
```

> **NOTE**
>
> The visibility of a **FLAG_CANDIDATE** (candidate-state) panel is not controlled by the system. You need to manage the timing for showing and hiding the candidate word panel based on app scenarios.

## Modules to Import

```ts
import { PanelInfo, PanelType, PanelFlag } from '@kit.IMEKit';
```

## PanelInfo

Attribute information of the input method panel. It is used to describe the type and display state of the input method panel and is passed as a configuration parameter when you create an input method panel.

- Meaning/Function: Defines the type (soft keyboard or status bar) and display state (fixed, floating, or candidate state) of the input method panel, and serves as the configuration parameter of **InputMethodAbility.createPanel()** to determine the form of the created panel.

- Usage scenarios: Used when an input method app needs to create an input method panel through **createPanel()** and specify its type and state. Examples include creating a default fixed-state soft keyboard panel, creating a freely draggable floating-state soft keyboard panel, and creating a candidate-state panel that displays candidate words in an independent window.

- Use effect: The set **type** and **flag** determine the type and display form of the created panel. After the settings are complete, the system creates the panel according to the specified type and state. The visibility behavior of the panel is determined by **flag**. The fixed state and floating state are controlled by the system, while the candidate state is controlled by you.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| type | [PanelType](#paneltype) | No | No | Input method panel type. Determines whether the panel is a soft keyboard or a status bar. When the parameter is not specified, the default value is **SOFT_KEYBOARD** (**0**). |
| flag | [PanelFlag](#panelflag) | No | Yes | Input method panel state type.<br/>- The default value is **FLAG_FIXED** (**0**), indicating a fixed-state panel type.<br/>- Currently used only to describe the state of a soft-keyboard panel. Setting it for a **STATUS_BAR** type panel has no actual effect.<br/>- The visibility behavior of the panel differs by state type. When the parameter is set to **FLAG_FIXED** or **FLAG_FLOATING**, panel visibility is controlled by the system. When the parameter is set to **FLAG_CANDIDATE**, panel visibility is controlled by you. |

Suggestions for the **PanelInfo** parameter:

- **type** parameter:

  - Value range: [PanelType](#paneltype) enum values, that is, **SOFT_KEYBOARD** (**0**) or **STATUS_BAR** (**1**).

  - Default value: **SOFT_KEYBOARD** (**0**). A soft keyboard panel is created by default if this parameter is not specified.

  - Usage with related APIs: The **flag** property is currently used only to describe the state of a **SOFT_KEYBOARD** panel. Setting **flag** takes no effect when **type** is set to **STATUS_BAR**.

- **flag** parameter:

  - Value range: [PanelFlag](#panelflag) enum values, that is, **FLAG_FIXED** (**0**), **FLAG_FLOATING** (**1**), or **FLAG_CANDIDATE** (**2**).

  - Default value: **FLAG_FIXED** (**0**). A fixed‑state panel is used by default if this parameter is not specified.

  - Usage scenarios: Select different **flag** values for different scenarios:

    - **FLAG_FIXED** (**0**): Applies to most default input scenarios. The panel is anchored at the bottom of the screen, and its visibility is managed by the system.

    - **FLAG_FLOATING** (**1**): Applies to scenarios where the panel position needs to be adjusted freely (for example, landscape‑mode input or multi‑window environments). The panel is draggable, and its visibility is managed by the system.

    - **FLAG_CANDIDATE** (**2**): Applies to scenarios that require candidate words to be displayed independently. The panel serves as a candidate word window, and the timing for showing and hiding it shall be managed by you.

  - Use effect:

    - When **FLAG_FIXED** is set: The panel is anchored at the bottom of the screen, and the system manages its visibility behaviors.

    - When **FLAG_FLOATING** is set: The panel acts as a floating window that can be dragged freely, and the system manages its visibility behaviors.

    - When **FLAG_CANDIDATE** is set: The panel acts as a candidate word window. The system does not actively manage its visibility. You must control the timing for showing and hiding the panel by calling **Panel.show()** and **Panel.hide()**.

  - Specification limits: This parameter applies only to **SOFT_KEYBOARD** panels. Setting **flag** for a **STATUS_BAR** panel takes no effect.

  - Precautions: When **FLAG_CANDIDATE** is selected, you must manage the visibility of the candidate word panel. This includes calling **Panel.show()** to display the panel when the user starts input, and calling **Panel.hide()** to hide the panel after input ends or the user selects a candidate word.

## PanelType

Enumerates the input method panel types. Defines the panel category and determines whether the panel is a soft keyboard or a status bar.

**System capability:** SystemCapability.MiscServices.InputMethodFramework

| Name          | Value | Description   | Use Scenario |
| ------------- | ----- | ------------- | ------------ |
| SOFT_KEYBOARD | 0     | Soft keyboard. | Applies to scenarios that require keyboard input interaction. It is the primary panel type of an input method app. Most input method apps need to create at least one soft keyboard panel. |
| STATUS_BAR    | 1     | Status bar. | Applies to scenarios that require displaying input method status information (such as the current input language and input mode) at the top of the screen. It is usually used as an auxiliary panel together with the soft keyboard panel. |

Suggestions for the **PanelType** parameter:

- Selection principle: An input method app usually needs to create a **SOFT_KEYBOARD** panel as the main keyboard interface. The **STATUS_BAR** panel is optional and is created only when input method status information needs to be displayed.

- Specification limits: A single input method app can create only one panel of the **SOFT_KEYBOARD** type and one panel of the **STATUS_BAR** type. An error will be returned if panels of the same type are created repeatedly.

- Usage with related APIs: **PanelType** must be used together with **PanelFlag**. Currently, **PanelFlag** is only used to describe the state of a **SOFT_KEYBOARD** panel; for a **STATUS_BAR** panel, the setting of **PanelFlag** has no actual effect.

## PanelFlag

Enumerates the input method panel state types. Defines the display form of a panel and determines whether the panel is in fixed, floating, or candidate state.

> **NOTE**
>
>This enumeration applies only to **SOFT_KEYBOARD** panels. Setting **PanelFlag** for a **STATUS_BAR** panel takes no effect.

**System capability:** SystemCapability.MiscServices.InputMethodFramework

| Name | Value | Description | Usage Scenario | Use Effect |
| -------------- | ---- | ------------------------------------------------------------ | -------- | -------- |
| FLAG_FIXED | 0 | Fixed-state panel type. | Applies to most default input scenarios, where the panel is anchored at the bottom of the screen. | The panel is displayed anchored at the bottom of the screen, and its visibility is managed by the system. |
| FLAG_FLOATING | 1 | Floating-state panel type. | Applies to scenarios requiring free adjustment of the panel position (for example, landscape‑mode input, multi‑window environments, or tablet devices). | The panel acts as a floating window that can be dragged freely, and its visibility is managed by the system. |
| FLAG_CANDIDATE | 2 | Candidate-word state panel type.<br/>‑ When the input panel is in candidate-word state, it serves as a window for displaying user input candidates.<br/>‑ The system does not actively control showing and hiding of the candidate‑word state panel. You need to control its visibility based on app scenarios. | Applies to scenarios that require independent display of candidate words, such as search association words and input suggestion lists. | The panel is an independent candidate‑word window. You must control its visibility via **Panel.show()** and **Panel.hide()**. The system does not actively manage its visibility. |

Suggestions for the **PanelFlag** parameter:

- Selection principles:

  - **FLAG_FIXED** (**0**) is preferred for default scenarios. It is the most commonly‑used panel state, with visibility automatically managed by the system and no extra processing required from you.

  - Select **FLAG_FLOATING** (**1**) for flexible‑layout scenarios (such as landscape mode or multi‑window environments). Panel position can be adjusted via **Panel.moveTo()**.

  - Select **FLAG_CANDIDATE** (**2**) when independent candidate word display is required. You are responsible for implementing visibility management logic.

- Default configuration: The default value is **FLAG_FIXED** (**0**). When **flag** is not set in **PanelInfo**, the panel is in the fixed state by default.

- Precautions: When **FLAG_CANDIDATE** is selected, you must implement the visibility management logic of the candidate word panel; otherwise, the panel will not be shown or hidden automatically. You are advised to show the panel when the user starts input and hide it after input ends or a candidate word is selected.