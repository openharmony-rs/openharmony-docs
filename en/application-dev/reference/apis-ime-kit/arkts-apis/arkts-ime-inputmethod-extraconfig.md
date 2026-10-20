# @ohos.inputMethod.ExtraConfig(Input Method Extension Information)

The **@ohos.inputMethod.ExtraConfig** module provides data definitions for input method extension information. It
 enables the ArkUI edit box to pass custom configuration information to the input method app when the input method is
 launched.
 <br>
 <br>This module is the extension information data module of the input method framework. It defines the
 **InputMethodExtraConfig** and **CustomValueType** APIs which carry the custom key-value configuration data passed
 from the edit box app to the input method app.
 <br>
 <br>This module provides the capability for the edit box app to pass personalized configuration to the input method app.
 The edit box app can encapsulate custom information such as the user's input habits, shortcut key settings, theme
 color, and input mode preferences into key-value pairs, and pass them to the input method app when attaching to the
 input method app. This enables the input method app to provide a personalized experience. The total length of the
 information cannot exceed 32 KB.
 <br>
 <br>This module is used when the edit box app needs to pass additional configuration information to the input method app
 to customize input behaviors. Typical scenarios include: a chat app that expects the input method to display the
 emoji panel by default, a search app that expects the input method to use a specific input mode, and a note app that
 is expected to configure the shortcut key behavior of the input method.
 <br>
 <br>Key interfaces and data types defined in this module are as follows:
 <br>
 | Interface/Type | Description |
 |---|---|
 | InputMethodExtraConfig | Input method extension information interface,
 containing the **customSettings** property and used to store custom key-value pairs.
 These key-value pairs can be any input method-related configuration information (such as user input habits, shortcut key settings, and theme color),
 which will be loaded when the input method app is attached to provide a personalized user experience.
 The total length of the information cannot exceed 32 KB. |
 | CustomValueType | Union type of extension information values, supporting three value types: **number**,
 **string**, and **boolean**. The specific type of the parameter depends on its functionality. |
 <br>
 <br>This module is a pure data definition module. As a data type, `InputMethodExtraConfig` must be used in combination
 with APIs from other modules. A typical combination is as follows: in the `onWillAttachIME` method of the `TextInput`
 component, pass `InputMethodExtraConfig` to the input method app through `IMEClient.setExtraConfig`. On the input
 method app side, the configuration is received and processed through `EditorAttribute` of the
 `@ohos.inputMethodEngine` module.



## Modules to Import

```TypeScript
import { InputMethodExtraConfig } from '@kit.IMEKit';
```

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [InputMethodExtraConfig](arkts-ime-inputmethod-extraconfig-inputmethodextraconfig-i.md) | Represents input method extension information. It is used by the edit box app to pass custom key-value pair configuration data to the input method app, enabling the edit box app to personalize input method behaviors. <br> <br>- Meaning/Function: Defines custom configuration key‑value pairs passed from the edit box app to the input method app, stored in the **Record<string, CustomValueType>** format. A **key** is the name of a configuration item, and a **value** is the content of the configuration item. Values support three types: number, string, and boolean. <br>- Usage scenarios: Used when an edit box app needs to pass additional personalized configuration information to the input method app to customize input behaviors. Examples include a chat app that expects the input method to display the emoji panel by default, a search app that expects the input method to use a specific input mode, and a note app that is expected to configure the shortcut key behavior of the input method. <br>- Use effect: The configured extension information is loaded and delivered to the input method app when the input method app attaches to the edit box app. The input method app can adjust input behaviors accordingly to deliver a personalized user experience. If no extension information is set, the input method app uses the default configuration. <br> <br>Suggestions for the **customSettings** parameter: <br> <br>- Value range: A key is any non-empty string. The value type is [CustomValueType](arkts-ime-customvaluetype-t.md) which can be number, string, or boolean. A key can correspond to only one value. <br>- Specification limits: The total size of information cannot exceed 32 KB. Any data exceeding the 32 KB limit will not be transmitted. You can determine whether the limit is exceeded by calculating the JSON‑serialized length of all key‑value pairs. <br>- Take‑effect mechanism: The extension information takes effect when the edit box app attaches to the input method via **InputMethodController.attach()** of the **@ohos.inputMethod** module. It is passed to the input method app together with **TextConfig.extraConfig**. The extension information will not be transmitted if **attach()** is not invoked or **extraConfig** is not set in **TextConfig**. <br>- |

### Types

| Name | Description |
| --- | --- |
| [CustomValueType](arkts-ime-customvaluetype-t.md) | Represents the value type of extension information. The specific type of the parameter depends on its function. You can select an appropriate value type based on the meaning of the configuration item: numeric configurations (such as font size and weight coefficient) use the number type; text configurations (such as input mode name and theme identifier) use the string type; switch configurations (such as whether to enable a feature and whether to display a panel) use the boolean type. |
