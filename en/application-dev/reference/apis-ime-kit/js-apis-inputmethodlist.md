# @ohos.inputMethodList (Input Method List)
<!--Kit: IME Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @codexu62-->
<!--Designer: @zhaolinglan-->
<!--Tester: @murphy84-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=fb10dfeff9355a629d7174d0cb2422acdfc59b6a translatedAt=2026-09-14T01:57:47.324Z pushedAt=2026-09-14T06:21:03.569Z -->

The **@ohos.inputMethodList** module is a UI control module oriented to system apps and input method apps. It provides an input method list dialog component.

This module is a declarative UI component module. It provides the `InputMethodListDialog` custom dialog component, which is used to display the default input method subtypes and the list of third-party input method apps. It optionally provides an entry for switching input method modes (such as one-handed mode and full-screen mode).

Through the dialog component provided by this module, users can view all input methods installed in the current system in the input method list and switch from the default input method to another input method. For preset system input methods, mode options (such as one-handed mode and full-screen mode) can also be displayed in the list for users to switch the display mode of the input method keyboard.

This module is used when a system app or an input method app needs to provide an entry for input method switching. Typical scenarios include the input method management page in the system settings app, the settings interface of an input method app, or other system-level interfaces that require users to select and switch input methods. This component can be called only by system apps and input method apps. The `patternOptions` parameter is supported only by preset system input methods.

The relationship between this module and other modules in the input method framework is as follows:

- [@ohos.inputMethod](js-apis-inputmethod.md): Targeted at general foreground apps. Provides input method control and management capabilities (such as showing/hiding the soft keyboard and switching input methods). It can switch input methods through the `switchInputMethod` API, and is suitable for scenarios that do not require an interactive selection interface.

- [@ohos.inputMethodEngine](js-apis-inputmethodengine.md): Targeted at input method apps. Provides input method server capabilities such as creating soft keyboard windows and inserting/deleting characters.

- **@ohos.inputMethodList** (this module): Targeted at system apps and input method apps. Provides a visualized input method list dialog component, and is suitable for scenarios that require an interactive selection interface.

> **NOTE**
>
> This component is supported since API version 11. New APIs in later versions are marked with a superscript to indicate their initial version.

This module contains the following key components and interfaces:

| Interface/Struct | Description |
|---|---|
| InputMethodListDialog | Input method list dialog component, declared using the `@CustomDialog` decorator. Displays the input method list and an optional mode switching entry, which is the core UI component of this module. A `CustomDialogController` must be passed in to control the opening and closing of the dialog, and `PatternOptions` can be optionally passed in to configure the mode switching feature. |
| PatternOptions | Input method mode option configuration interface, which defines the resource array of mode options, the index of the mode selected by default, and the mode switching callback. Only preset system input methods support passing in this parameter. |
| Pattern | Icon definition interface for a single input method mode, containing two resource properties: the default icon and the selected-state icon. |

Using `InputMethodListDialog` requires the combination of multiple APIs: create a `CustomDialogController` > configure `PatternOptions` (optional) > build `InputMethodListDialog` in the builder of `CustomDialogController` > open the dialog through `CustomDialogController.open()`.

```javascript
// The following is pseudocode for illustrating the calling logic.

// 1. Define the mode options (required only for preset system input methods).
let patternOptions = {
  defaultSelected: 1, // Index of the mode selected by default.
  patterns: [ // Array of mode option resources.
    { icon: one-handed mode icon, selectedIcon: selected icon in one-handed mode },
    { icon: full-screen mode icon, selectedIcon: selected icon in full-screen mode }
  ],
  action: (index) => { // Mode switching callback.
    // Handle the mode switching logic.
  }
};

// 2. Create a CustomDialogController and build InputMethodListDialog in the builder.
let listController = new CustomDialogController({
  builder: InputMethodListDialog({ patternOptions: patternOptions }),
  customStyle: true
});

// 3. Open the dialog in a user interaction event.
listController.open();
```

## Modules to Import

```ts
import { InputMethodListDialog } from '@kit.IMEKit';
```

## Attributes
The [universal attributes](../apis-arkui/arkui-ts/ts-component-general-attributes.md) are not supported.

##  Events

The [universal events](../apis-arkui/arkui-ts/ts-component-general-events.md) are not supported.

## InputMethodListDialog

InputMethodListDialog({controller: CustomDialogController, patternOptions?: PatternOptions})

Represents the input method list dialog component. It displays the list of input method apps installed in the current system in the form of a dialog, allowing users to switch between input methods. For the default input method, it also provides an entry for switching keyboard modes (such as one-handed mode and full-screen mode).

Usage scenarios: This component is used when a system app or an input method app needs to provide users with a visualized input method selection and switching feature. For example, in the system settings app, users are allowed to select different input methods, or in an input method app, users are allowed to switch to another input method or switch the keyboard mode of the current input method.

Use effect: After this component is invoked, an input method list dialog is displayed. After the user selects an input method in the dialog, the system switches to the specified input method. If the user selects a mode option of the default input method, the system displays the keyboard layout in the specified mode.

Differences between similar APIs and selection principles: Compared with the [inputMethod.switchInputMethod](js-apis-inputmethod.md#inputmethodswitchinputmethod9) API, this component provides a visualized input method selection interface, which is suitable for scenarios that require an interactive selection interface. The **switchInputMethod** API is suitable for scenarios where the input method is switched programmatically without requiring manual selection by the user.

Usage restrictions: This component can be called only by system apps and input method apps. The **patternOptions** parameter is supported only by preset input methods.

**NOTE**
- Preconditions: Create a [CustomDialogController](../apis-arkui/arkui-ts/ts-methods-custom-dialog-box.md#customdialogcontroller) instance and associate it with **InputMethodListDialog**, and then open the dialog through the **open()** method of the **controller**.
- This component does not support universal attributes and universal events.

**Decorator type**: @CustomDialog

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name | Type | Mandatory | Decorator Type | Description |
| -------- | -------- | -------- | -------- | -------- |
| controller | [CustomDialogController](../apis-arkui/arkui-ts/ts-methods-custom-dialog-box.md#customdialogcontroller) | Yes | - | Controller of the input method list dialog, used to control the opening and closing of the dialog.<br>Usage scenario: This parameter must be provided when the display and hiding of the input method list dialog need to be controlled through code.<br>Use effect: After being set, the dialog can be opened by calling the [open()](../apis-arkui/arkui-ts/ts-methods-custom-dialog-box.md#open) method of the controller, and closed by calling the [close()](../apis-arkui/arkui-ts/ts-methods-custom-dialog-box.md#close) method.<br>Note: Create a **CustomDialogController** instance and associate it with InputMethodListDialog first, and then open the dialog through controller.open(). |
| patternOptions | [PatternOptions](#patternoptions) | No | - | Input method mode option configuration. Supported only by preset system input methods.<br>Usage scenario: Pass this parameter when a preset system input method needs to support mode switching (such as one-handed mode and full-screen mode), to configure the mode icon resources and switching callback.<br>Default value: When not passed, the control displays only the input method list and does not provide the mode switching function.<br>Note: Third-party input method applications cannot use this parameter. |

## PatternOptions

Represents the configuration of input method mode options, used to define the switching options for keyboard modes.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

| Name | Type | Read-only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| defaultSelected | number | No | Yes | Index of the mode selected by default, corresponding to the index value in the patterns array.<br>Usage scenario: Use this parameter when the default input method needs to preset an initially selected keyboard mode.<br>Use effect: After being set, the mode option corresponding to this index is selected by default when the input method list dialog opens.<br>Value range: [0, **patterns.length** - 1]. If the value is out of this range, it does not take effect, and no mode option is selected when the dialog opens.<br>Default value: If not set, no mode option is selected when the dialog opens.<br>Note: This index value must be within the valid range of the **patterns** array; otherwise, the setting does not take effect. |
| patterns   | Array<[Pattern](#pattern)> | No | No | Array of mode option resources. Each **Pattern** defines the icon and selected-state icon of a keyboard mode.<br>Usage scenario: Configure this parameter when the default input method needs to provide multiple keyboard modes (such as one-handed mode and full-screen mode) for users to choose from.<br>Use effect: After being set, all mode options defined in this array are displayed in the default input method area of the input method list dialog for users to select.<br>Note: The **icon** and **selectedIcon** of each **Pattern** in the **patterns** array must be valid [Resource](../apis-arkui/arkui-ts/ts-types.md#resource) resource references. It is recommended that you configure at least two mode options to provide a meaningful selection function. |
| action | (index: number) => void | No | No | Callback function invoked when the mode option changes.<br>Usage scenario: Set this callback when corresponding logic (such as updating the keyboard layout or saving user preferences) needs to be executed when the user switches the keyboard mode.<br>Use effect: When the user taps a mode option in the input method list dialog, the system invokes this callback and passes the index value of the selected mode in the **patterns** array.<br>Note: The callback parameter index is the index value of the selected mode in the **patterns** array, consistent with the value range of **defaultSelected**. In the callback, **defaultSelected** can be updated based on the index value to keep the selected state consistent with the user's choice the next time the dialog opens. |

## Pattern

Represents the definition of the icon resources for input method mode options, used to configure the visual representation of keyboard modes in the dialog. Available only to the current input method (that is, the preset system input method).

**System capability**: SystemCapability.MiscServices.InputMethodFramework

| Name | Type | Read-only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| icon | [Resource](../apis-arkui/arkui-ts/ts-types.md#resource) | No | No | Icon resource for the default (unselected) state of the input method mode option.<br>Usage scenarios: Identify the visual representation of each keyboard mode when it is unselected, allowing users to recognize different mode options in the dialog.<br>Use effect: After setting, this icon is displayed for the mode option in the dialog when it is in the unselected state.<br>Note: A Resource type reference such as **$r('app.media.xxx')** must be used, and the corresponding icon resource file must be added to the project's resource directory. Image resources of the string and PixelMap types are not supported. |
| selectedIcon | [Resource](../apis-arkui/arkui-ts/ts-types.md#resource) | No | No | Icon resource for the selected state of the input method mode option.<br>Usage scenarios: Identify the visual representation of each keyboard mode when it is selected, forming a selected/unselected visual distinction with **icon** to help users recognize the currently selected mode.<br>Use effect: After setting, this icon is displayed for the mode option in the dialog when it is in the selected state.<br>Usage with related parameters: **selectedIcon** should remain visually consistent with **icon**, differing only by the selected state indicator (such as adding highlighting or a border), so users can recognize the currently selected mode. The **icon** and **selectedIcon** in each **Pattern** must be set at the same time; neither can be omitted. |

##  Example

```ts
import { PatternOptions, InputMethodListDialog } from '@kit.IMEKit';

@Entry
// Set the component.
@Component
struct SettingsItem {
  @State defaultPattern: number = 1;
  private oneHandAction: PatternOptions = {
    defaultSelected: this.defaultPattern,
    patterns: [ // The icons in patterns can be used only after the corresponding icon resources are added to the resource directory of the project.
      {
        icon: $r('app.media.hand_icon'), // This is the icon resource of the input method mode option, for example, the one-handed mode icon.
        selectedIcon: $r('app.media.hand_icon_selected') // This is the selected state of the icon resource of the input method mode option, for example, the selected state icon of the one-handed mode.
      },
      {
        icon: $r('app.media.hand_icon1'),
        selectedIcon: $r('app.media.hand_icon_selected1')
      },
      {
        icon: $r('app.media.hand_icon2'),
        selectedIcon: $r('app.media.hand_icon_selected2')
      }],
    // Callback function invoked when the mode option changes.
    action: (index: number) => {
      console.info(`pattern is changed, current is ${index}`);
      this.defaultPattern = index; // Update the default selected mode.
    }
  };
  // Create a custom dialog controller.
  private listController: CustomDialogController = new CustomDialogController({
    builder: InputMethodListDialog({ patternOptions: this.oneHandAction }), // Build the input method list dialog.
    customStyle: true,
    maskColor: '#00000000'
  });

  build() {
    Column() {
      Flex({
        direction: FlexDirection.Column,
        alignItems: ItemAlign.Center, 
        justifyContent: FlexAlign.Center 
      }) {
        Text('Input method switching list').fontSize(20)
      }
    }
    .width('13%')
    .id('bindInputMethod')
    .onClick((event?: ClickEvent) => {
      this.listController.open();
    })
  }
}
```

Effect

![Effect](./figures/effect.png)
