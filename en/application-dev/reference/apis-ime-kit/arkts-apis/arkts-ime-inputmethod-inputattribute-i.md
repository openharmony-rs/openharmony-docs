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

Ability name set for the text box. <br> <br>- When the text box sets an ability name, the length does not exceed 127 characters (if it exceeds, it is automatically truncated to 127 characters). <br>- When the text box does not set an ability name, it defaults to an empty string. <br>- This field is provided to the input method application when [attach](arkts-ime-inputmethod-inputmethodcontroller-i.md#attach) is called.

**Type:** string

**Since:** 20

<!--Device-InputAttribute-abilityName?: string--><!--Device-InputAttribute-abilityName?: string-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## consumeKeyEvents

```TypeScript
consumeKeyEvents?: boolean
```

Whether the text box has full capability to handle keys such as letters, characters, and function keys. The default value is **false**. <br> <br>- The value **true** indicates that this capability is available. <br>- The value **false** indicates that this capability is not available. <br>- This field is provided to the input method application when [attach](arkts-ime-inputmethod-inputmethodcontroller-i.md#attach) / [updateAttribute](arkts-ime-inputmethod-inputmethodcontroller-i.md#updateattribute) is called. <br> <br>**Model restriction:** This parameter can be used only in the stage model.

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

Enter key function type.

**Type:** [EnterKeyType](arkts-ime-inputmethod-enterkeytype-e.md)

**Since:** 10

<!--Device-InputAttribute-enterKeyType: EnterKeyType--><!--Device-InputAttribute-enterKeyType: EnterKeyType-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## placeholder

```TypeScript
placeholder?: string
```

Placeholder information set for the text box. <br> <br>- When the text box sets placeholder information, the length does not exceed 255 characters (if it exceeds, it is automatically truncated to 255 characters), used to prompt or guide the user to enter temporary text or symbols. (For example, prompting the input result feedback of an input item being "mandatory" or "optional".) <br>- When the text box does not set placeholder information, it defaults to an empty string. <br>- This field is provided to the input method application when [attach](arkts-ime-inputmethod-inputmethodcontroller-i.md#attach) is called.

**Type:** string

**Since:** 20

<!--Device-InputAttribute-placeholder?: string--><!--Device-InputAttribute-placeholder?: string-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## textInputType

```TypeScript
textInputType: TextInputType
```

Text input type.

**Type:** [TextInputType](arkts-ime-inputmethod-textinputtype-e.md)

**Since:** 10

<!--Device-InputAttribute-textInputType: TextInputType--><!--Device-InputAttribute-textInputType: TextInputType-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework
