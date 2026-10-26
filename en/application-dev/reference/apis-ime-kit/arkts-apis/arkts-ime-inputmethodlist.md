# @ohos.inputMethodList(Input Method List)

The **@ohos.inputMethodList** module is a UI control module oriented to system apps and input method apps. It
 provides an input method list dialog component.
 <br>
 <br>This module is a declarative UI component module. It provides the `InputMethodListDialog`
 custom dialog component, which is used to display the default input method subtypes and the list of
 third-party input method apps. It optionally provides an entry for switching input method modes
 (such as one-handed mode and full-screen mode).
 <br>
 <br>Through the dialog component provided by this module, users can view all input methods installed in the current
 system in the input method list and switch from the default input method to another input method. For preset system
 input methods, mode options (such as one-handed mode and full-screen mode) can also be displayed in the list for
 users to switch the display mode of the input method keyboard.
 <br>
 <br>This module is used when a system app or an input method app needs to provide an entry for
 input method switching. Typical scenarios include the input method management page in the system settings app,
 the settings interface of an input method app, or other system-level interfaces that require users to select and
 switch input methods. This component can be called only by system apps and input method apps. The `patternOptions`
 parameter is supported only by preset system input methods.
 <br>
 <br>The relationship between this module and other modules in the input method framework is as follows:
 <br>
 <br>- [@ohos.inputMethod](arkts-ime-inputmethod.md): Targeted at general foreground apps. Provides input
 method control and management capabilities (such as showing/hiding the soft keyboard and switching input methods).
 It can switch input methods through the `switchInputMethod` API, and is suitable for scenarios that do not require
 an interactive selection interface.
 <br>- [@ohos.inputMethodEngine](arkts-ime-inputmethodengine.md):
 Targeted at input method apps. Provides input method server capabilities such as creating soft keyboard windows and
 inserting/deleting characters.
 <br>- **@ohos.inputMethodList** (this module): Targeted at system apps and input method apps.
 Provides a visualized input method list dialog component, and is suitable for scenarios that require
 an interactive selection interface.
 <br>
 <br> > NOTE
 <br> >
 <br> > This component is supported since API version 11. New APIs in later versions are marked with a superscript to
 <br> > indicate their initial version.
 <br> > This module contains the following key components and interfaces:
 <br>
 | Interface/Struct | Description |
 |---|---|
 | InputMethodListDialog | Input method list dialog component, declared using the `@CustomDialog` decorator.
 Displays the input method list and an optional mode switching entry, which is the core UI component of this module.
 A `CustomDialogController` must be passed in to control the opening and closing of the dialog,
 and `PatternOptions` can be optionally passed in to configure the mode switching feature. |
 | PatternOptions | Input method mode option configuration interface, which defines the resource array of
 mode options, the index of the mode selected by default, and the mode switching callback.
 Only preset system input methods support passing in this parameter. |
 | Pattern | Icon definition interface for a single input method mode,
 containing two resource properties: the default icon and the selected-state icon. |
 <br>
 <br>Using `InputMethodListDialog` requires the combination of multiple APIs: create a `CustomDialogController` >
 configure `PatternOptions` (optional) > build `InputMethodListDialog` in the builder of `CustomDialogController` >
 open the dialog through `CustomDialogController.open()`.
 <br>
 <br>

## Attributes

<br><br>The [universal attributes](../../apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md) are not supported.<br><br>

## Events

<br><br>The [universal events](../../apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md) are not supported.

## Modules to Import

```TypeScript
import { InputMethodListDialog, PatternOptions, Pattern } from '@kit.IMEKit';
```

## Summary

### Structs

| Name | Description |
| --- | --- |
| [InputMethodListDialog](arkts-ime-inputmethodlist-inputmethodlistdialog-s.md) | InputMethodListDialog({controller: CustomDialogController, patternOptions?: PatternOptions}) <br> <br>Represents the input method list dialog component. It displays the list of input method apps installed in the current system in the form of a dialog, allowing users to switch between input methods. For the default input method, it also provides an entry for switching keyboard modes (such as one-handed mode and full-screen mode). <br> <br>Usage scenarios: This component is used when a system app or an input method app needs to provide users with a visualized input method selection and switching feature. For example, in the system settings app, users are allowed to select different input methods, or in an input method app, users are allowed to switch to another input method or switch the keyboard mode of the current input method. <br> <br>Use effect: After this component is invoked, an input method list dialog is displayed. After the user selects an input method in the dialog, the system switches to the specified input method. If the user selects a mode option of the default input method, the system displays the keyboard layout in the specified mode. <br> <br>Differences between similar APIs and selection principles: Compared with the [inputMethod.switchInputMethod](arkts-ime-inputmethod-switchinputmethod-f.md) API, this component provides a visualized input method selection interface, which is suitable for scenarios that require an interactive selection interface. The **switchInputMethod** API is suitable for scenarios where the input method is switched programmatically without requiring manual selection by the user. <br> <br>Usage restrictions: This component can be called only by system apps and input method apps. The **patternOptions** parameter is supported only by preset input methods. <br> <br>NOTE <br> <br>- Preconditions: Create a [CustomDialogController](../../apis-arkui/arkts-apis/arkts-arkui-customdialogcontroller-c.md) instance and associate it with **InputMethodListDialog**, and then open the dialog through the **open()** method of the **controller**. <br>- This component does not support universal attributes and universal events. |

### Interfaces

| Name | Description |
| --- | --- |
| [Pattern](arkts-ime-inputmethodlist-pattern-i.md) | Represents the definition of the icon resources for input method mode options, used to configure the visual representation of keyboard modes in the dialog. Available only to the current input method (that is, the preset system input method). |
| [PatternOptions](arkts-ime-inputmethodlist-patternoptions-i.md) | Represents the configuration of input method mode options, used to define the switching options for keyboard modes. |

## Examples

```TypeScript
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
