# AttachOptions

绑定输入法的附加选项。

**起始版本：** 23

<!--Device-inputMethod-export interface AttachOptions--><!--Device-inputMethod-export interface AttachOptions-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## 导入模块

```TypeScript
import { inputMethod } from '@kit.IMEKit';
```

## requestKeyboardReason

```TypeScript
requestKeyboardReason?: RequestKeyboardReason
```

请求键盘输入的原因。

**类型：** RequestKeyboardReason

**默认值：** RequestKeyboardReason.NONE

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AttachOptions-requestKeyboardReason?: RequestKeyboardReason--><!--Device-AttachOptions-requestKeyboardReason?: RequestKeyboardReason-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## showKeyboard

```TypeScript
showKeyboard?: boolean
```

绑定输入法成功后，是否拉起输入法键盘。

- true表示拉起。  
- false表示不拉起。

**类型：** boolean

**默认值：** true

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AttachOptions-showKeyboard?: boolean--><!--Device-AttachOptions-showKeyboard?: boolean-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

