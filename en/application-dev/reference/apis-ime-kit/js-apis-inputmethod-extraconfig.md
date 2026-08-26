# @ohos.inputMethod.ExtraConfig (Input Method Extension Information)

<!--Kit: IME Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @codexu62-->
<!--Designer: @andeszhang-->
<!--Tester: @murphy1984-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=95b635b2657acaf53c78b86c96c7e9bdaf7f7668 translatedAt=2026-08-25T01:24:52.296Z pushedAt=2026-08-26T09:18:16.867Z -->

The **@ohos.inputMethod.ExtraConfig** module provides data definitions for input method extension information. It enables the ArkUI edit box to pass custom configuration information to the input method app when the input method is launched.

This module is the extension information data module of the input method framework. It defines the **InputMethodExtraConfig** and **CustomValueType** APIs which carry the custom key-value configuration data passed from the edit box app to the input method app.

This module provides the capability for the edit box app to pass personalized configuration to the input method app. The edit box app can encapsulate custom information such as the user's input habits, shortcut key settings, theme color, and input mode preferences into key-value pairs, and pass them to the input method app when attaching to the input method app. This enables the input method app to provide a personalized experience. The total length of the information cannot exceed 32 KB.

This module is used when the edit box app needs to pass additional configuration information to the input method app to customize input behavior. Typical scenarios include: a chat app that expects the input method to display the emoji panel by default, a search app that expects the input method to use a specific input mode, and a note app that is expected to configure the shortcut key behavior of the input method.

> **NOTE**
>
>The initial APIs of this module are supported since API version 22. Newly added APIs will be marked with a superscript to indicate their earliest API version.

This module defines the data structure of input method extension information, which is used by the edit box app to pass custom configuration to the input method app. **InputMethodExtraConfig**, as a data type, must be used in combination with the APIs of the **@ohos.inputMethod** module. In the **InputMethodController.attach()** method, the extension information is passed to the input method app through the **extraConfig** property of **TextConfig**. The input method app obtains and processes this extension information via **InputClient** of the **@ohos.inputMethodEngine** module, and adjusts the input behavior accordingly (such as switching the input mode or changing the theme). This implements personalized configuration coordination between the edit box app and the input method app.

Typical usage process: the edit box app constructs **InputMethodExtraConfig** → assigns it to **TextConfig.extraConfig** → passes it through **attach()** → the input method app receives it through **InputClient** → the input method app adjusts its behavior accordingly.

Key interfaces and data types defined in this module are as follows:

| Interface/Type | Description |
|---|---|
| InputMethodExtraConfig | Input method extension information interface, containing the **customSettings** property and used to store custom key-value pairs. These key-value pairs can be any input method-related configuration information (such as user input habits, shortcut key settings, and theme color), which will be loaded when the input method app is attached to provide a personalized user experience. The total length of the information cannot exceed 32 KB. |
| CustomValueType | Union type of extension information values, supporting three value types: **number**, **string**, and **boolean**. The specific type of the parameter depends on its functionality. |

This module is a pure data definition module. **InputMethodExtraConfig**, as a data type, must be used in combination with APIs of other modules. A typical combination is: in the **InputMethodController.attach()** method of the **@ohos.inputMethod** module, pass **InputMethodExtraConfig** to the input method app through **TextConfig**.

```javascript
// The following is pseudocode for illustrating the calling logic.

// 1. Construct the input method extension information.
let extraConfig = {
  customSettings: {
    'inputMode': 'chat',
    'showEmojiPanel': true,
    'themeColor': 'dark',
    'autoCapitalize': false
  }
};

// 2. Assign the extension information to TextConfig.
let textConfig = {
  inputAttribute: { textInputType: 0, enterKeyType: 0 },
  cursorInfo: { left: 100, top: 200, width: 2, height: 20 },
  extraConfig: extraConfig
};

// 3. Pass the extension information when attaching to the input method.
let controller = inputMethod.getController();
controller.attach(true, textConfig);
```

## Modules to Import

```ts
import { InputMethodExtraConfig, CustomValueType } from '@kit.IMEKit';
```

## CustomValueType<sup>22+</sup>

type CustomValueType = number | string | boolean

Represents the value type of extension information. The specific type of the parameter depends on its function. You can select an appropriate value type based on the meaning of the configuration item: numeric configurations (such as font size and weight coefficient) use the number type; text configurations (such as input mode name and theme identifier) use the string type; switch configurations (such as whether to enable a feature and whether to display a panel) use the boolean type.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

| Type   | Description                |
| ------- | -------------------- |
| number  | Number.   |
| string  | String. |
| boolean | Boolean. |

## InputMethodExtraConfig

Represents input method extension information. It is used by the edit box app to pass custom key-value pair configuration data to the input method app, enabling the edit box app to personalize input method behaviors.

- Meaning/Function: Defines custom configuration key‑value pairs passed from the edit box app to the input method app, stored in the **Record<string, CustomValueType>** format. A **key** is the name of a configuration item, and a **value** is the content of the configuration item. Values support three types: number, string, and boolean.

- Usage scenarios: Used when an edit box app needs to pass additional personalized configuration information to the input method app to customize input behaviors. Examples include a chat app that expects the input method to display the emoji panel by default, a search app that expects the input method to use a specific input mode, and a note app that is expected to configure the shortcut key behavior of the input method.

- Use effect after use: The configured extension information is loaded and delivered to the input method app when the input method app attaches to the edit box app. The input method app can adjust input behaviors accordingly to deliver a personalized user experience. If no extension information is set, the input method app uses the default configuration.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

| Name  |Type   |Read-Only   |Optional   |Description   |
|---------|----------|----------|--------|--------|
| customSettings |Record&lt;string, [CustomValueType](#customvaluetype22)&gt;    | No   | No    |Input‑method extension information for storing custom key‑value pairs. These key‑value pairs can hold any input method‑related configuration information, such as user input habits, shortcut key settings, and theme colors. These settings are loaded when the input method app attaches, to deliver a personalized user experience. If this field is not set, the input method app uses the default configuration.|

Suggestions for the **customSettings** parameter:

- Value range: A key is any non-empty string. The value type is [CustomValueType](#customvaluetype22) which can be number, string, or boolean. A key can correspond to only one value.

- Specification limits: The total size of information cannot exceed 32 KB. Any data exceeding the 32 KB limit will not be transmitted. You can determine whether the limit is exceeded by calculating the JSON‑serialized length of all key‑value pairs.

- Take‑effect mechanism: The extension information takes effect when the edit box app attaches to the input method via **InputMethodController.attach()** of the **@ohos.inputMethod** module. It is passed to the input method app together with **TextConfig.extraConfig**. The extension information will not be transmitted if **attach()** is not invoked or **extraConfig** is not set in **TextConfig**.

- Notes:

  - Preconditions: You need to first construct an **InputMethodExtraConfig** object, assign it to **TextConfig.extraConfig**, and then pass it through **InputMethodController.attach()**.

  - Development suggestions: Use meaningful naming conventions for key names (such as **'inputMode'** and **'showEmojiPanel'**) so that the input method app can parse and use them easily. Avoid using overly short or meaningless key names (such as **'a'** and **'x1'**), which reduces readability and maintainability.

  - Development suggestions: Prevent key names from conflicting with those used internally by the input method framework. Use app‑specific prefixes (for example, **'com.example.chat.inputMode'**) to avoid naming conflicts.

- Usage with related APIs: **customSettings** must be used together with the **TextConfig.extraConfig** property of the **@ohos.inputMethod** module. The process consists of assigning the **InputMethodExtraConfig** object to **TextConfig.extraConfig**, and then passing it through **InputMethodController.attach()**. The input method app receives and processes the configuration through **InputClient** of the **@ohos.inputMethodEngine** module.

**Example:**

```ts
import { InputMethodExtraConfig, inputMethod } from '@kit.IMEKit';

// Construct the input method extension information.
let extraConfig: InputMethodExtraConfig = {
  customSettings: {
    'inputMode': 'chat',
    'showEmojiPanel': true,
    'themeColor': 'dark',
    'autoCapitalize': false,
    'fontSize': 16
  }
};

// Assign the extension information to TextConfig (used with the @ohos.inputMethod module).
let textConfig = {
  inputAttribute: { textInputType: 0, enterKeyType: 0 },
  cursorInfo: { left: 100, top: 200, width: 2, height: 20 },
  extraConfig: extraConfig
};

// Pass it to the input method app through attach.
let controller = inputMethod.getController();
controller.attach(true, textConfig);
```