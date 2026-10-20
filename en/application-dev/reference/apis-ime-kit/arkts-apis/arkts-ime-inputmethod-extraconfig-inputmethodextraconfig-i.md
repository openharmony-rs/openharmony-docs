# InputMethodExtraConfig

```TypeScript
export interface InputMethodExtraConfig
```

Represents input method extension information. It is used by the edit box app to pass custom key-value pair configuration data to the input method app, enabling the edit box app to personalize input method behaviors. <br> <br>- Meaning/Function: Defines custom configuration key‑value pairs passed from the edit box app to the input method app, stored in the **Record<string, CustomValueType>** format. A **key** is the name of a configuration item, and a **value** is the content of the configuration item. Values support three types: number, string, and boolean. <br>- Usage scenarios: Used when an edit box app needs to pass additional personalized configuration information to the input method app to customize input behaviors. Examples include a chat app that expects the input method to display the emoji panel by default, a search app that expects the input method to use a specific input mode, and a note app that is expected to configure the shortcut key behavior of the input method. <br>- Use effect: The configured extension information is loaded and delivered to the input method app when the input method app attaches to the edit box app. The input method app can adjust input behaviors accordingly to deliver a personalized user experience. If no extension information is set, the input method app uses the default configuration. <br> <br>Suggestions for the **customSettings** parameter: <br> <br>- Value range: A key is any non-empty string. The value type is [CustomValueType](arkts-ime-customvaluetype-t.md) which can be number, string, or boolean. A key can correspond to only one value. <br>- Specification limits: The total size of information cannot exceed 32 KB. Any data exceeding the 32 KB limit will not be transmitted. You can determine whether the limit is exceeded by calculating the JSON‑serialized length of all key‑value pairs. <br>- Take‑effect mechanism: The extension information takes effect when the edit box app attaches to the input method via **InputMethodController.attach()** of the **@ohos.inputMethod** module. It is passed to the input method app together with **TextConfig.extraConfig**. The extension information will not be transmitted if **attach()** is not invoked or **extraConfig** is not set in **TextConfig**. <br>- **NOTE:** <br>- Development suggestions: Use meaningful naming conventions for key names (such as **'inputMode'** and **'showEmojiPanel'**) so that the input method app can parse and use them easily. Avoid using overly short or meaningless key names (such as **'a'** and **'x1'**), which reduces readability and maintainability. <br>- Development suggestions: Prevent key names from conflicting with those used internally by the input method framework. Use app‑specific prefixes (for example, **'com.example.chat.inputMode'**) to avoid naming conflicts. <br>- Usage with related APIs: A typical combination is to pass `InputMethodExtraConfig` to the input method app through `IMEClient.setExtraConfig` in the `onWillAttachIME` method of the `TextInput` component. The input method app then receives and processes the configuration through the `EditorAttribute` of the `@ohos.inputMethodEngine` module.

**Since:** 22

<!--Device-unnamed-export interface InputMethodExtraConfig--><!--Device-unnamed-export interface InputMethodExtraConfig-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## Modules to Import

```TypeScript
import { InputMethodExtraConfig } from '@kit.IMEKit';
```

## customSettings

```TypeScript
customSettings: Record<string, CustomValueType>
```

Input method extension information for storing custom key‑value pairs. These key‑value pairs can hold any input method‑related configuration information, such as user input habits, shortcut key settings, and theme colors. These settings are loaded when the input method app attaches, to deliver a personalized user experience. If this field is not set, the input method app uses the default configuration.

**Type:** Record&lt;string, [CustomValueType](arkts-ime-customvaluetype-t.md)&gt;

**Since:** 22

<!--Device-InputMethodExtraConfig-customSettings: Record<string, CustomValueType>--><!--Device-InputMethodExtraConfig-customSettings: Record<string, CustomValueType>-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Examples**

```TypeScript
// The following code must be executed on the page of EntryAbility.
@Entry
@Component
struct Index2 {
  // 1. Construct the input method extension information.
  private extraConfig: InputMethodExtraConfig = {
    customSettings: {
      'inputMode': 'chat',
      'showEmojiPanel': true,
      'themeColor': 'dark',
      'autoCapitalize': false
    }
  };

  build() {
    Column() {
      TextInput()
        .onWillAttachIME((client: IMEClient): void => {
          client.setExtraConfig(this.extraConfig);
        })
    }
    .height('100%')
    .width('100%')
  }
}
```
