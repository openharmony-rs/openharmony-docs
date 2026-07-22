# InputAttribute

编辑框属性，包含文本输入类型和Enter键功能类型。

**起始版本：** 10

<!--Device-inputMethod-export interface InputAttribute--><!--Device-inputMethod-export interface InputAttribute-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## 导入模块

```TypeScript
import { inputMethod } from '@kit.IMEKit';
```

## abilityName

```TypeScript
abilityName?: string
```

编辑框设置的ability名称。

- 编辑框设置ability名称时，长度不超过127个字符（如果超出将会自动截断为127个字符）。  
- 编辑框未设置ability名称时，默认为空字符串。  
- 该字段在调用绑定[attach](arkts-ime-inputmethod-inputmethodcontroller-i.md#attach)时提供给输入法应用。

**类型：** string

**起始版本：** 20

<!--Device-InputAttribute-abilityName?: string--><!--Device-InputAttribute-abilityName?: string-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## consumeKeyEvents

```TypeScript
consumeKeyEvents?: boolean
```

编辑框是否具有完整处理字母、字符、功能等按键的能力。默认值为false。

- 值为true，表示具备此能力。  
- 值为false，表示不具备此能力。  
- 该字段在调用[attach](arkts-ime-inputmethod-inputmethodcontroller-i.md#attach)/ [InputAttribute](arkts-ime-inputmethod-inputattribute-i.md)时提供给输入法应用。

**类型：** boolean

**默认值：** false

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-InputAttribute-consumeKeyEvents?: boolean--><!--Device-InputAttribute-consumeKeyEvents?: boolean-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## enterKeyType

```TypeScript
enterKeyType: EnterKeyType
```

Enter键功能类型。

**类型：** EnterKeyType

**起始版本：** 10

<!--Device-InputAttribute-enterKeyType: EnterKeyType--><!--Device-InputAttribute-enterKeyType: EnterKeyType-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## placeholder

```TypeScript
placeholder?: string
```

编辑框设置的占位符信息。

- 编辑框设置占位符信息时，长度不超过255个字符（如果超出将会自动截断为255个字符），用于提示或引导用户输入临时性文本或符号。（例如：提示输入项为"必填"或"非必填"的输入结果反馈。）  
- 编辑框没有设置占位符信息时，默认为空字符串。  
- 该字段在调用[attach](arkts-ime-inputmethod-inputmethodcontroller-i.md#attach)时提供给输入法应用。

**类型：** string

**起始版本：** 20

<!--Device-InputAttribute-placeholder?: string--><!--Device-InputAttribute-placeholder?: string-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## textInputType

```TypeScript
textInputType: TextInputType
```

文本输入类型。

**类型：** TextInputType

**起始版本：** 10

<!--Device-InputAttribute-textInputType: TextInputType--><!--Device-InputAttribute-textInputType: TextInputType-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

