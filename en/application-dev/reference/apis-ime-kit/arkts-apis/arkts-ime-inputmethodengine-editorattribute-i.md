# EditorAttribute

```TypeScript
interface EditorAttribute
```

Represents the attributes of the edit box.

**Since:** 8

<!--Device-inputMethodEngine-interface EditorAttribute--><!--Device-inputMethodEngine-interface EditorAttribute-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## Modules to Import

```TypeScript
import { inputMethodEngine } from '@kit.IMEKit';
```

## abilityName

```TypeScript
readonly abilityName?: string
```

Ability name set for the edit box.

**Type:** string

**Since:** 20

<!--Device-EditorAttribute-readonly abilityName?: string--><!--Device-EditorAttribute-readonly abilityName?: string-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## bundleName

```TypeScript
readonly bundleName?: string
```

Name of the application package to which the edit box belongs. The value may be **""**. Handle this scenario when using the attribute.

**Type:** string

**Since:** 14

<!--Device-EditorAttribute-readonly bundleName?: string--><!--Device-EditorAttribute-readonly bundleName?: string-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## capitalizeMode

```TypeScript
readonly capitalizeMode?: CapitalizeMode
```

Whether to capitalize the first letter in the edit box. If it is not set or is set to an invalid value, the first letter is not capitalized by default.

**Type:** [CapitalizeMode](arkts-ime-inputmethodengine-capitalizemode-e.md)

**Since:** 20

<!--Device-EditorAttribute-readonly capitalizeMode?: CapitalizeMode--><!--Device-EditorAttribute-readonly capitalizeMode?: CapitalizeMode-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## consumeKeyEvents

```TypeScript
readonly consumeKeyEvents?: boolean
```

Whether the editor supports consuming key events.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-EditorAttribute-readonly consumeKeyEvents?: boolean--><!--Device-EditorAttribute-readonly consumeKeyEvents?: boolean-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## displayId

```TypeScript
readonly displayId?: number
```

Screen ID of the window corresponding to the edit box. If window ID is not set, the screen ID of the focused window is used.

**Type:** number

**Since:** 18

<!--Device-EditorAttribute-readonly displayId?: long--><!--Device-EditorAttribute-readonly displayId?: long-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## enterKeyType

```TypeScript
readonly enterKeyType: number
```

Function attributes of the edit box. For details, see [function key definitions in constants](../../../reference/apis-ime-kit/js-apis-inputmethodengine.md#工具不太能识别具体链接到的是哪个常量。让人工处理。咨询黄山）).

**Type:** number

**Since:** 8

<!--Device-EditorAttribute-readonly enterKeyType: int--><!--Device-EditorAttribute-readonly enterKeyType: int-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## extraConfig

```TypeScript
readonly extraConfig?: InputMethodExtraConfig
```

Extra information about the input method.

**Type:** [InputMethodExtraConfig](arkts-ime-inputmethod-extraconfig-inputmethodextraconfig-i.md)

**Since:** 22

<!--Device-EditorAttribute-readonly extraConfig?: InputMethodExtraConfig--><!--Device-EditorAttribute-readonly extraConfig?: InputMethodExtraConfig-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## gradientMode

```TypeScript
readonly gradientMode?: GradientMode
```

Gradient mode.

**Type:** [GradientMode](arkts-ime-inputmethodengine-gradientmode-e.md)

**Since:** 20

<!--Device-EditorAttribute-readonly gradientMode?: GradientMode--><!--Device-EditorAttribute-readonly gradientMode?: GradientMode-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## immersiveMode

```TypeScript
readonly immersiveMode?: ImmersiveMode
```

Immersive mode of the input method.

**Type:** [ImmersiveMode](arkts-ime-inputmethodengine-immersivemode-e.md)

**Since:** 15

<!--Device-EditorAttribute-readonly immersiveMode?: ImmersiveMode--><!--Device-EditorAttribute-readonly immersiveMode?: ImmersiveMode-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## inputPattern

```TypeScript
readonly inputPattern: number
```

Text attribute of the edit box. For details, see [edit box definitions in constants](../../../reference/apis-ime-kit/js-apis-inputmethodengine.md#工具不太能识别具体链接到的是哪个常量。让人工处理。咨询黄山）).

**Type:** number

**Since:** 8

<!--Device-EditorAttribute-readonly inputPattern: int--><!--Device-EditorAttribute-readonly inputPattern: int-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## isTextPreviewSupported

```TypeScript
isTextPreviewSupported: boolean
```

Whether text preview is supported. <br> <br>- **true**: Supported. <br>- **false**: Unsupported.

**Type:** boolean

**Since:** 12

<!--Device-EditorAttribute-isTextPreviewSupported: boolean--><!--Device-EditorAttribute-isTextPreviewSupported: boolean-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## placeholder

```TypeScript
readonly placeholder?: string
```

Placeholder information set for the edit box.

**Type:** string

**Since:** 20

<!--Device-EditorAttribute-readonly placeholder?: string--><!--Device-EditorAttribute-readonly placeholder?: string-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## windowId

```TypeScript
readonly windowId?: number
```

ID of the window where the edit box is located.

**Type:** number

**Since:** 18

<!--Device-EditorAttribute-readonly windowId?: int--><!--Device-EditorAttribute-readonly windowId?: int-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework
