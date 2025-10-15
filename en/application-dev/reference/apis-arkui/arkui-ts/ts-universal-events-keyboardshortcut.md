# Component Keyboard Shortcut Event
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiangtao92-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @HelloCrease-->

You can set custom keyboard shortcuts for components, with the flexibility to define multiple shortcuts per component.

A component will still respond to the set custom shortcuts even if it is not in focus or visible on the active page, as long as it is part of the component tree within a window that has focus.

Better yet, you can set custom events for custom keyboard shortcuts, so that when the defined keys of a keyboard shortcut are pressed, the custom event is triggered. If no custom event is set, the behavior of a keyboard shortcut is the same as that of a click.

>  **NOTE**
>
>  The initial APIs of this module are supported since API version 10. Updates will be marked with a superscript to indicate their earliest API version.

## keyboardShortcut

keyboardShortcut(value: string | FunctionKey, keys: Array\<ModifierKey>, action?: () => void): T

Sets a keyboard shortcut for the component.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                                 | Mandatory  | Description                                    |
| ----- | ------------------------------------- | ---- | ---------------------------------------- |
| value | string \| [FunctionKey](ts-appendix-enums.md#functionkey10) | Yes| Character of a hotkey (characters that can be entered through the keyboard) or [FunctionKey](ts-appendix-enums.md#functionkey10).<br>An empty string means to disable the keyboard shortcut.<br>|
| keys  | Array\<[ModifierKey](ts-appendix-enums.md#modifierkey10)> | Yes| Modifier keys.<br>The value of keys can be empty only when value is [FunctionKey](ts-appendix-enums.md#functionkey10).<br>|
| action  | () => void    | No   | Callback for a custom event after the keyboard shortcut is triggered.<br>                              |

**Return value**

| Type| Description|
| -------- | -------- |
| T | Current component.|

## Precautions for Using Keyboard Shortcuts

Keyboard shortcuts respond to system key combinations and take precedence over standard **OnKeyEvent** handlers. For details about key event processing logic, see [Key Event Data Flow](../../../ui/arkts-interaction-development-guide-keyboard.md#key-event-data-flow).

| Scenario                                      | Processing Logic                           | Example                                      |
| ---------------------------------------- | ---------------------------------- | ---------------------------------------- |
| All components that support the **onClick** event                        | Custom keyboard shortcuts are supported.                          | –                                       |
| Requirements for custom keyboard shortcuts                                | Control keys Ctrl, Shift, Alt, and their combinations plus a single character (a character that can be entered on the keyboard) or [FunctionKey](ts-appendix-enums.md#functionkey10) of the hot key| Button('button1').keyboardShortcut('a',[ModifierKey.CTRL]) |
| Setting one custom keyboard shortcut for multiple components                           | Only the component with the shallowest depth in the node tree responds to the shortcut key. Other components do not respond to the shortcut key.         | Button('button1').keyboardShortcut('a',[ModifierKey.CTRL])<br>Button('button2').keyboardShortcut('a',[ModifierKey.CTRL]) |
| When the component is focused or not                              | The component responds to the custom keyboard shortcut as long as the window has focus.                     | –                                       |
| Using a single function key to trigger a keyboard shortcut| A keyboard shortcut can consist of a single function key without any modifier keys.| Button('button1').keyboardShortcut(FunctionKey.F2,[])                                        |
| The input parameter **value** of **keyboardShortcut** is empty| The keyboard shortcut is disabled.<br>Shortcut keys that are bound to multiple shortcut keys cannot be unbound.| Button('button1').keyboardShortcut('',[ModifierKey.CTRL])<br>Button('button2').keyboardShortcut('',[]) |
| Ctrl, Shift, and Alt in the keys command in **keyboardShortcut**| Both the keys on the left or right sides of the keyboard work.                         | Button('button1').keyboardShortcut('a',[ModifierKey.CTRL, ModifierKey.ALT]) |
| Character key in the **value** parameter of the **keyboardShortcut** API           | The response is case-insensitive.                         | Button('button1').keyboardShortcut('a',[ModifierKey.CTRL])<br>Button('button2').keyboardShortcut('A',[ModifierKey.CTRL]) |
| Response to keyboard shortcuts                                  | The component responds to a keyboard shortcut when the keys specified by **keys** are pressed and the key specified by **value** triggers a down event. (Long-pressing leads to continuous response.)             | –                                       |
| The component is hidden<br>                              | The component still responds to keyboard shortcuts.                             | –                                       |
| Components in the [enable](ts-universal-attributes-enable.md) state                             | The component does not respond to keyboard shortcuts.                            | –                                       |
| 1. The keyboard shortcut is the same as an existing one (including the system-defined ones).<br>2. The **value** parameter contains multiple character keys.<br>3. The **key** parameter has a duplicate modifier key.| In these cases, the keyboard shortcut is not added, and the previously added keyboard shortcuts still work.         | Button('button1').keyboardShortcut(FunctionKey.F4,[ModifierKey.ALT])<br>Button('button2').keyboardShortcut('ab',[ModifierKey.CTRL])<br>Button('button3').keyboardShortcut('ab',[ModifierKey.CTRL,ModifierKey.CTRL]) |

### System-defined Keyboard Shortcuts That Cannot Be Bound

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

## Example

### Example 1: Setting Component Keyboard Shortcuts

This example demonstrates how to set up keyboard shortcuts for components. This allows users to press the modifier key and accompanying key at the same time to trigger the component to respond to the shortcut and trigger the **onClick** event or a custom event.

```ts
@Entry
@Component
struct Index {
  @State message: string = 'Hello World'

  build() {
    Row() {
      Column({ space: 5 }) {
        Text(this.message)
        Button("Test short cut 1").onClick((event: ClickEvent) => {
          this.message = "I clicked Button 1";
          console.info("I clicked 1");
        }).keyboardShortcut('.', [ModifierKey.SHIFT, ModifierKey.CTRL, ModifierKey.ALT])
          .onKeyEvent((event: KeyEvent)=>{
            console.info("event.keyCode: " + JSON.stringify(event));
          })
        Button("Test short cut 2").onClick((event: ClickEvent) => {
          this.message = "I clicked Button 2";
          console.info("I clicked 2");
        }).keyboardShortcut('1', [ModifierKey.CTRL])
        Button("Test short cut 3").onClick((event: ClickEvent) => {
          this.message = "I clicked Button 3";
          console.info("I clicked 3");
        }).keyboardShortcut('A', [ModifierKey.SHIFT])
        Button("Test short cut 4").onClick((event: ClickEvent) => {
          this.message = "I clicked Button 4";
          console.info("I clicked 4");
        }).keyboardShortcut(FunctionKey.F5, [], () => {
          this.message = "I clicked Button 4";
          console.info("I clicked user callback.");
        }).keyboardShortcut(FunctionKey.F3, [])
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

 ![keyEvent](figures/keyboard-shortcut.gif)

### Example 2: Binding and Unbinding Keyboard Shortcuts

This example demonstrates how to bind and unbind shortcut keys.

```ts
@Entry
@Component
struct Index {
  @State message: string = 'disable'
  @State shortCutEnable: boolean = false
  @State keyValue: string = ''

  build() {
    Row() {
      Column({ space: 5 }) {
        Text('Ctrl+A is ' + this.message)
        Button("Test short cut").onClick((event: ClickEvent) => {
          this.message = "I clicked Button";
          console.info("I clicked");
        }).keyboardShortcut(this.keyValue, [ModifierKey.CTRL])
        Button(this.message + 'shortCut').onClick((event: ClickEvent) => {
          this.shortCutEnable = !this.shortCutEnable;
          this.message = this.shortCutEnable ? 'enable' : 'disable';
          this.keyValue = this.shortCutEnable ? 'a' : '';
        })
        Button('multi-shortcut').onClick((event: ClickEvent) => {
          console.info('Trigger keyboard shortcut success.')
        }).keyboardShortcut('q', [ModifierKey.CTRL])
          .keyboardShortcut('w', [ModifierKey.CTRL])
          .keyboardShortcut('', []) // Unbinding does not work when there are multiple keyboard shortcuts.
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

 ![keyEvent](figures/keyboard-shortcut-cancel.gif)
