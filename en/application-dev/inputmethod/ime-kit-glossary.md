# IME Kit Glossary

<!--Kit: IME Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @codexu62-->
<!--Designer: @andeszhang-->
<!--Tester: @murphy84-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=444d4b7458e1317b3c2f1a471488b9c4b8344c2e translatedAt=2026-06-03T06:18:42.620Z pushedAt=2026-06-05T06:19:55.739Z -->

## B

### Basic Access Mode

A restricted security mode for input method applications. In this mode, only basic typing functions are provided.

## C

### Custom Input Box

A custom text input control developed by developers. It integrates [InputMethodController](../reference/apis-ime-kit/js-apis-inputmethod.md#inputmethodcontroller) to bind to an input method.

## D

### Dark Immersive Mode

An immersive mode that applies a dark immersive effect to the input method panel.

## E

### Editor Box Attribute

Attributes that describe the characteristics of an editor box, including **textInputType**, **enterKeyType**, and **immersiveMode**.

### Extension Ability Context

The context of an Extension ability, which provides capabilities for starting, stopping, connecting to, and disconnecting from an Ability.

## F

### Fixed State

A state in which the input method panel is fixed at the bottom of the screen.

### Floating State

A state in which the input method panel can float and move.

### Candidate State

A state in which the input method panel displays candidate words for user input.

### Full Access Mode

A full-access mode for input method applications, providing complete input method functions.

## I

### IME Kit

IME Kit establishes a communication channel between the application that contains the editor box and the input method application to support text input collaboration. It also provides input method application management capabilities for system applications.

### Immersive Effect

The visual effect of the input method panel, including gradient mode and streamer mode.

### Immersive Mode

The immersive display mode of the input method panel, including light immersive mode and dark immersive mode. This mode is set by the input method application.

### Input Method Extension Ability

An input method Extension ability component that allows you to develop input method applications.

### Input Method Subtype

A specific input mode or language of an input method, such as a Chinese keyboard or English keyboard.

### Subtype Configuration File

A JSON file that configures input method subtype information. It contains the subtypes array, which defines properties such as `icon`, `id`, `label`, and `locale` for each subtype.

### IME Command Tool

A command-line tool for managing input methods, including querying input methods, enabling or disabling input methods, switching input method access modes, and switching the current input method.

## K

### Keyboard Appearance Mode

The expected keyboard display mode for an editor box, including immersive and non-immersive modes.

### Keyboard Controller

A controller class in an input method that controls soft keyboard display, event listening, and text operations.

## L

### Light Immersive Mode

An immersive mode that applies a light immersive effect to the input method panel.

## P

### Input Method Panel

A window component created by an input method app to display the soft keyboard or status bar.

### Panel State Type

An enum for input method panel states, including fixed (`FLAG_FIXED`), floating (`FLAG_FLOATING`), and candidate (`FLAG_CANDIDATE`) states.

### Panel Configuration Information

Configuration information for creating an input method panel, including `type` (panel type) and `flag` (panel state).

### Panel Type

An enum for input method panel types, including soft keyboard (`SOFT_KEYBOARD`) and status bar (`STATUS_BAR`).

### Preview Text

A preview function that displays input text before the user confirms the input.

## S

### Soft Keyboard

A virtual keyboard consisting of keys. It is a panel type used for text input.

### System Panel

A system input method panel in which the input method soft keyboard window is displayed. The soft keyboard window has an offset area relative to the system panel.