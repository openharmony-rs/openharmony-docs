# Component Keyboard Shortcut Event
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=9430c77017ca73641537d932a3d7d8a4c99c078b translatedAt=2026-09-02T12:29:53.475Z -->

Developers can set custom key combinations for a component. Each component can be configured with multiple key combinations. This is applicable to scenarios where component operations need to be triggered quickly through the keyboard, improving keyboard operation efficiency.

A component will still respond to the set custom shortcuts even if it is not in focus or visible on the active page, as long as it is part of the component tree within a window that has focus.

Better yet, you can set custom events for custom keyboard shortcuts, so that when the defined keys of a keyboard shortcut are pressed, the custom event is triggered. If no custom event is set, the behavior of a keyboard shortcut is the same as that of a click.

>  **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.

## keyboardShortcut

keyboardShortcut(value: string | FunctionKey, keys: Array\<ModifierKey>, action?: () => void): T

Sets custom key combinations for a component. The response, binding, and ineffective scenarios of keyboard shortcuts must meet the constraints in [Precautions for Using Keyboard Shortcuts](#precautions-for-using-keyboard-shortcuts) and [System-Defined Keyboard Shortcuts That Cannot Be Bound](#system-defined-keyboard-shortcuts-that-cannot-be-bound).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                                 | Mandatory  | Description                                    |
| ----- | ------------------------------------- | ---- | ---------------------------------------- |
| value | string \| [FunctionKey](ts-appendix-enums.md#functionkey10) | Yes | Single character of the hotkey (a character that can be entered through the keyboard) or [FunctionKey](ts-appendix-enums.md#functionkey10).<br>An empty string means to cancel the keyboard shortcut binding; a component with multiple keyboard shortcuts bound cannot unbind a keyboard shortcut.<br>When value contains multiple characters, the key combination is not bound, and the previously bound key combination remains valid.<br> |
| keys  | Array\<[ModifierKey](ts-appendix-enums.md#modifierkey10)> | Yes | Key combination.<br>The value of keys can be empty only when value is [FunctionKey](ts-appendix-enums.md#functionkey10).<br>When keys contains duplicate modifier keys, the key combination is not bound, and the previously bound key combination remains valid.<br> |
| action  | () => void    | No    | Callback for the custom event triggered after the key combination shortcut is successfully triggered. If this parameter is not set, the behavior of the key combination shortcut is the same as that of click.<br>                               |

**Return value**

| Type| Description|
| -------- | -------- |
| T | Current component, used to support subsequent chained calls. |

## Precautions for Using Keyboard Shortcuts

A keyboard shortcut is a response to system keys and takes precedence over the common key event `onKeyEvent`. For details about the logic of key event triggering, see [Key Event Data Flow](../../../ui/arkts-interaction-development-guide-keyboard.md#key-event-data-flow).

| Scenario                                      | Processing Logic                           | Example                                      |
| ---------------------------------------- | ---------------------------------- | ---------------------------------------- |
| All components that support the onClick event | Support custom key combinations. | Not supported |
| Custom key combination requirements | The control keys Ctrl, Shift, Alt and their combinations, plus a single character of the hotkey (a character that can be entered through the keyboard) or [FunctionKey](ts-appendix-enums.md#functionkey10). | Button('button1').keyboardShortcut('a',[ModifierKey.CTRL]) |
| Multiple different components set with the same key combination | Only the component at the shallowest depth in the node tree responds, and other components do not respond to the keyboard shortcut. | Button('button1').keyboardShortcut('a',[ModifierKey.CTRL])<br>Button('button2').keyboardShortcut('a',[ModifierKey.CTRL]) |
| Regardless of whether the component has focus | As long as the window has focus, the keyboard shortcut responds. | Not supported |
| Using a single `FunctionKey` to trigger the keyboard shortcut | A single `FunctionKey` without a `ModifierKey` can be bound as a keyboard shortcut. | Button('button1').keyboardShortcut(FunctionKey.F2,[]) |
| The input parameter `value` of `keyboardShortcut` is empty | Unbinds the keyboard shortcut.<br>A component bound with multiple keyboard shortcuts cannot unbind the keyboard shortcuts. | Button('button1').keyboardShortcut('',[ModifierKey.CTRL])<br>Button('button2').keyboardShortcut('',[]) |
| Ctrl, Shift, and Alt in the keys parameter of the keyboardShortcut API | Responds regardless of whether the left or right key is pressed. | Button('button1').keyboardShortcut('a',[ModifierKey.CTRL, ModifierKey.ALT]) |
| A single character in the value parameter of the keyboardShortcut API | Responds regardless of case. | Button('button1').keyboardShortcut('a',[ModifierKey.CTRL])<br>Button('button2').keyboardShortcut('A',[ModifierKey.CTRL]) |
| Response of the keyboard shortcut | The `keys` key is in the pressed state and the `value` key triggers the down event (a long press responds continuously). | Not supported |
| Hidden component<br> | Responds to the keyboard shortcut. | Not supported |
| Component in the non-interactive state ([enabled](ts-universal-attributes-enable.md#enabled) set to false) | Does not respond to the keyboard shortcut. | Not supported |
| 1. When the key combinations of components (including system predefined keyboard shortcuts) are the same<br>2. When the value parameter of the API has multiple characters<br>3. When the keys parameter of the API has duplicate control keys | In these cases, the key combination is not bound, and the previously bound key combination remains valid. | Button('button1').keyboardShortcut(FunctionKey.F4,[ModifierKey.ALT])<br>Button('button2').keyboardShortcut('ab',[ModifierKey.CTRL])<br>Button('button3').keyboardShortcut('a',[ModifierKey.CTRL,ModifierKey.CTRL]) |

### System-Defined Keyboard Shortcuts That Cannot Be Bound

The following key combinations cannot function as keyboard shortcuts:

- `Alt` + `F4`
- `Alt` + `Shift` + `F4`
- `Alt` + `TAB`
- `Alt` + `Shift` + `TAB`
- `Ctrl` + `Shift` + `ESC`

### Predefined Key Events

The following table lists the predefined key events.

The predefined key events and custom key events have priorities. Events with higher priorities intercept those with lower priorities. For details about the response priorities, see [Key Event Data Flow](../../../ui/arkts-interaction-development-guide-keyboard.md#key-event-data-flow).

| Keyboard Shortcut| Focused Component| Usage| Event Handling Category|
| ----- | ---- | ---- | ---- |
| Arrow keys, **Shift** + Arrow keys| Text box component| Moves the cursor.| Input method|
| Arrow keys, **Shift** + Arrow keys| Universal component| Moves focus in navigation.| System keys|
| **Tab**, **Shift** + **Tab**| Universal component| Triggers focus navigation or moves focus in navigation.| System keys|

## Examples

### Example 1: Setting Component Keyboard Shortcuts

This example demonstrates how to set up keyboard shortcuts for components. This allows users to press the modifier key and accompanying key at the same time to trigger the component to respond to the shortcut and trigger the **onClick** event or a custom event.

```ts
@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  build() {
    Row() {
      Column({ space: 5 }) {
        Text(this.message);
        Button('Test short cut 1').onClick(() => {
          this.message = 'I clicked Button 1';
          console.info('I clicked 1');
        }).keyboardShortcut('.', [ModifierKey.SHIFT, ModifierKey.CTRL, ModifierKey.ALT])
          .onKeyEvent((event: KeyEvent) => {
            console.info('event.keyCode: ' + JSON.stringify(event));
          });
        Button('Test short cut 2').onClick(() => {
          this.message = 'I clicked Button 2';
          console.info('I clicked 2');
        }).keyboardShortcut('1', [ModifierKey.CTRL]);
        Button('Test short cut 3').onClick(() => {
          this.message = 'I clicked Button 3';
          console.info('I clicked 3');
        }).keyboardShortcut('A', [ModifierKey.SHIFT]);
        Button('Test short cut 4').onClick(() => {
          this.message = 'I clicked Button 4';
          console.info('I clicked 4');
        }).keyboardShortcut(FunctionKey.F5, [], () => {
          this.message = 'I clicked Button 4';
          console.info('I clicked user callback.');
        }).keyboardShortcut(FunctionKey.F3, []);
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

 ![keyEvent](figures/keyboard-shortcut.gif)

### Example 2: Binding and Unbinding Keyboard Shortcuts

This example demonstrates how to bind and unbind keyboard shortcuts.

```ts
@Entry
@Component
struct Index {
  @State message: string = 'disable';
  @State shortCutEnable: boolean = false;
  @State keyValue: string = '';

  build() {
    Row() {
      Column({ space: 5 }) {
        Text('Ctrl+A is ' + this.message);
        Button('Test short cut').onClick(() => {
          this.message = 'I clicked Button';
          console.info('I clicked');
        }).keyboardShortcut(this.keyValue, [ModifierKey.CTRL]);
        Button(this.message + 'shortCut').onClick(() => {
          this.shortCutEnable = !this.shortCutEnable;
          this.message = this.shortCutEnable ? 'enable' : 'disable';
          this.keyValue = this.shortCutEnable ? 'a' : '';
        });
        Button('multi-shortcut').onClick(() => {
          console.info('Trigger keyboard shortcut success.');
        }).keyboardShortcut('q', [ModifierKey.CTRL])
          .keyboardShortcut('w', [ModifierKey.CTRL])
          .keyboardShortcut('', []); // Does not take effect. A component bound with multiple keyboard shortcuts cannot unbind them.
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

 ![keyEvent](figures/keyboard-shortcut-cancel.gif)