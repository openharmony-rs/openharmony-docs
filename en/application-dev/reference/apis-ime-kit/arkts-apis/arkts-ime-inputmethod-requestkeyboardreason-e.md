# RequestKeyboardReason

```TypeScript
export enum RequestKeyboardReason
```

Enumerates the reasons for requesting the keyboard.

**Since:** 15

<!--Device-inputMethod-export enum RequestKeyboardReason--><!--Device-inputMethod-export enum RequestKeyboardReason-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## MOUSE

```TypeScript
MOUSE = 1
```

Indicates that the keyboard request is triggered by a mouse operation. <br> <br>Usage scenarios: used when the user clicks the edit box with a mouse to trigger the keyboard to pop up.

**Since:** 15

<!--Device-RequestKeyboardReason-MOUSE = 1--><!--Device-RequestKeyboardReason-MOUSE = 1-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## NONE

```TypeScript
NONE = 0
```

Indicates that no specific reason triggers the keyboard request. <br> <br>Usage scenarios: default value, used when no specific trigger reason is specified.

**Since:** 15

<!--Device-RequestKeyboardReason-NONE = 0--><!--Device-RequestKeyboardReason-NONE = 0-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## OTHER

```TypeScript
OTHER = 20
```

Indicates that the keyboard request is triggered by other reasons. <br> <br>Usage scenarios: used when the trigger reason for the keyboard to pop up is neither mouse nor touch.

**Since:** 15

<!--Device-RequestKeyboardReason-OTHER = 20--><!--Device-RequestKeyboardReason-OTHER = 20-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## TOUCH

```TypeScript
TOUCH = 2
```

Indicates that the keyboard request is triggered by a touch operation. <br> <br>Usage scenarios: used when the user taps the edit box to trigger the keyboard to pop up.

**Since:** 15

<!--Device-RequestKeyboardReason-TOUCH = 2--><!--Device-RequestKeyboardReason-TOUCH = 2-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework
