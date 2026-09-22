# InputMethodExtraConfig

```TypeScript
export interface InputMethodExtraConfig
```

Represents the extension information of an input method.

**Since:** 22

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## Modules to Import

```TypeScript
import { InputMethodExtraConfig } from '@kit.IMEKit';
```

## customSettings

```TypeScript
customSettings: Record<string, CustomValueType>
```

Input method extension information, which is used to store custom key-value pairs. These key-value pairs can be any configuration information related to the input method, such as user input habits, shortcut key settings, theme colors, and more. The settings are loaded when the input method application is bound to the system, delivering a personalized user experience. The total length of the information cannot exceed 32 KB.

**Type:** Record&lt;string, [CustomValueType](arkts-ime-customvaluetype-t.md)&gt;

**Since:** 22

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
