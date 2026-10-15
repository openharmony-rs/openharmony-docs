# InputAttribute

```TypeScript
export interface InputAttribute
```

Describes the attributes of the edit box, including the text input type and Enter key function type.

**Since:** 10

<!--Device-inputMethod-export interface InputAttribute--><!--Device-inputMethod-export interface InputAttribute-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## Modules to Import

```TypeScript
import { inputMethod } from '@kit.IMEKit';
```

## abilityName

```TypeScript
abilityName?: string
```

Ability name set for the edit box. <br> <br>- If the ability name is set for the edit box, the length cannot exceed 127 characters. (A name longer than 127 characters will be automatically truncated to 127 characters.) <br>- If the ability name is not set for the edit box, the value is an empty string by default. <br>- This field is provided for the input method application when [attach](arkts-ime-inputmethod-inputmethodcontroller-i.md#attach1) is called.

**Type:** string

**Since:** 20

<!--Device-InputAttribute-abilityName?: string--><!--Device-InputAttribute-abilityName?: string-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## consumeKeyEvents

```TypeScript
consumeKeyEvents?: boolean
```

Whether the editor supports consuming key events.

**Type:** boolean

**Default:** false

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-InputAttribute-consumeKeyEvents?: boolean--><!--Device-InputAttribute-consumeKeyEvents?: boolean-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## enterKeyType

```TypeScript
enterKeyType: EnterKeyType
```

Function type represented by the Enter key.

**Type:** [EnterKeyType](arkts-ime-inputmethod-enterkeytype-e.md)

**Since:** 10

<!--Device-InputAttribute-enterKeyType: EnterKeyType--><!--Device-InputAttribute-enterKeyType: EnterKeyType-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## placeholder

```TypeScript
placeholder?: string
```

Placeholder information set for the edit box. <br> <br>- When placeholder information is set for the edit box, the length cannot exceed 255 characters (a placeholder longer than 255 characters will be automatically truncated to 255 characters). It is used to prompt or guide users to enter temporary text or symbols. (For example, the placeholder prompts whether the input item is mandatory.) <br>- If no placeholder is set for the edit box, the value is an empty string by default. <br>- This field is provided for the input method application when [attach](arkts-ime-inputmethod-inputmethodcontroller-i.md#attach1) is called.

**Type:** string

**Since:** 20

<!--Device-InputAttribute-placeholder?: string--><!--Device-InputAttribute-placeholder?: string-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## textInputType

```TypeScript
textInputType: TextInputType
```

Enumerates the text input types.

**Type:** [TextInputType](arkts-ime-inputmethod-textinputtype-e.md)

**Since:** 10

<!--Device-InputAttribute-textInputType: TextInputType--><!--Device-InputAttribute-textInputType: TextInputType-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework
