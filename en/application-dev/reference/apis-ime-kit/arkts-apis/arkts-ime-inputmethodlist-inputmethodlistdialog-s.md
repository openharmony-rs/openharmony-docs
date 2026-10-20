# InputMethodListDialog

```TypeScript
export declare struct InputMethodListDialog
```

InputMethodListDialog({controller: CustomDialogController, patternOptions?: PatternOptions}) <br> <br>Represents the input method list dialog component. It displays the list of input method apps installed in the current system in the form of a dialog, allowing users to switch between input methods. For the default input method, it also provides an entry for switching keyboard modes (such as one-handed mode and full-screen mode). <br> <br>Usage scenarios: This component is used when a system app or an input method app needs to provide users with a visualized input method selection and switching feature. For example, in the system settings app, users are allowed to select different input methods, or in an input method app, users are allowed to switch to another input method or switch the keyboard mode of the current input method. <br> <br>Use effect: After this component is invoked, an input method list dialog is displayed. After the user selects an input method in the dialog, the system switches to the specified input method. If the user selects a mode option of the default input method, the system displays the keyboard layout in the specified mode. <br> <br>Differences between similar APIs and selection principles: Compared with the [inputMethod.switchInputMethod](arkts-ime-inputmethod-switchinputmethod-f.md) API, this component provides a visualized input method selection interface, which is suitable for scenarios that require an interactive selection interface. The **switchInputMethod** API is suitable for scenarios where the input method is switched programmatically without requiring manual selection by the user. <br> <br>Usage restrictions: This component can be called only by system apps and input method apps. The **patternOptions** parameter is supported only by preset input methods. <br> <br>NOTE <br> <br>- Preconditions: Create a [CustomDialogController](../../apis-arkui/arkts-apis/arkts-arkui-customdialogcontroller-c.md) instance and associate it with **InputMethodListDialog**, and then open the dialog through the **open()** method of the **controller**. <br>- This component does not support universal attributes and universal events.

**Since:** 11

**Decorator:** @CustomDialog

<!--Device-unnamed-export declare struct InputMethodListDialog--><!--Device-unnamed-export declare struct InputMethodListDialog-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## Modules to Import

```TypeScript
import { InputMethodListDialog, PatternOptions, Pattern } from '@kit.IMEKit';
```

## controller

```TypeScript
controller: CustomDialogController
```

Sets the controller.

**Type:** CustomDialogController

**Since:** 11

<!--Device-InputMethodListDialog-controller: CustomDialogController--><!--Device-InputMethodListDialog-controller: CustomDialogController-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## patternOptions

```TypeScript
patternOptions?: PatternOptions
```

Sets the pattern options. This parameter can be left blank when it is not default input method.

**Type:** [PatternOptions](arkts-ime-inputmethodlist-patternoptions-i.md)

**Since:** 11

<!--Device-InputMethodListDialog-patternOptions?: PatternOptions--><!--Device-InputMethodListDialog-patternOptions?: PatternOptions-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework
