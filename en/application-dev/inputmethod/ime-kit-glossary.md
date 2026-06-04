# IME Kit Glossary

<!--Kit: IME Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @codexu62-->
<!--Designer: @andeszhang-->
<!--Tester: @murphy84-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=444d4b7458e1317b3c2f1a471488b9c4b8344c2e translatedAt=2026-06-03T06:18:42.620Z pushedAt=2026-06-03T09:33:26.389Z -->

## B

### Base experience mode

A mode constraint for security control over input method applications, strictly adhering to providing only basic typing functionality.

## C

### CustomInput

A text input control customized by developers, which is bound to the input method by integrating [InputMethodController](../reference/apis-ime-kit/js-apis-inputmethod.md#inputmethodcontroller).

## D

### DARK_IMMERSIVE

A type of input method immersive mode that makes the input method panel present an immersive effect with a dark theme.

## E

### EditorAttribute

Characteristic attributes of an editor, including fields such as textInputType, enterKeyType, and immersiveMode.

### ExtensionContext

The context environment for ExtensionAbility, providing the ability to start, stop, bind, and unbind an Ability.

## F

### FLAG_FIXED

A state type where the input method panel is fixed at the bottom of the screen.

### FLAG_FLOATING

A state type where the input method panel can float and be moved.

### FLAG_CANDIDATE

The state type in which the input method panel displays user input candidates.

### Full experience mode

The full access mode of the input method application, providing complete input method functionality.

## I

### IME Kit

A service that establishes a communication channel between the application where the edit box resides and the input method application, ensuring collaboration for text input functionality, and also provides system applications with the ability to manage input method applications.

### ImmersiveEffect

The visual presentation effect of the input method panel, including gradient mode and flow mode.

### ImmersiveMode

An immersive display mode for the input method panel, including light immersive and dark immersive, set by the input method application.

### InputMethodExtensionAbility

The input method ExtensionAbility component, enabling developers to create their own input method applications.

### InputMethodSubtype

Different input modes or languages of an input method, such as Chinese keyboard and English keyboard.

### input_method_config.json

A JSON file that configures input method subtype information, containing a subtypes array that defines attributes such as icon, id, label, and locale for each subtype.

### IME command tool

Use IME commands to manage input methods, including querying input methods, enabling/disabling input methods, switching input method access modes, and switching the current input method.

## K

### KeyboardAppearance

The keyboard display mode expected by the edit box, including immersive mode and non-immersive mode.

### KeyboardController

A controller class in the input method that controls soft keyboard display, event listening, and text operations.

## L

### LIGHT_IMMERSIVE

A type of input method immersive mode that renders the input method panel with a light theme immersive effect.

## P

### Panel

A window component created by the input method application, used to display the soft keyboard or status bar.

### PanelFlag

Enumeration of input method panel state types, including fixed (FLAG_FIXED), floating (FLAG_FLOATING), and candidate (FLAG_CANDIDATE).

### PanelInfo

Configuration information when creating an input method panel, including type (panel type) and flag (panel state).

### PanelType

Enumeration of input method panel types, including soft keyboard (SOFT_KEYBOARD) and status bar (STATUS_BAR).

### PreviewText

A preview function that displays the input text before the user confirms the input.

## S

### SOFT_KEYBOARD

A virtual keyboard composed of keys, a panel type used for text input.

### SystemPanel

The input method soft keyboard window is displayed in the system input method panel, and the input method soft keyboard window has an offset area relative to the system panel.