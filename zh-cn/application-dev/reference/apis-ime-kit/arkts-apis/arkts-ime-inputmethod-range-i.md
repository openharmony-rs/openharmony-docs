# Range

文本的选中范围。

**起始版本：** 10

<!--Device-inputMethod-export interface Range--><!--Device-inputMethod-export interface Range-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## 导入模块

```TypeScript
import { inputMethod } from '@kit.IMEKit';
```

## end

```TypeScript
end: number
```

选中文本的末字符在编辑框的索引值。该参数应为大于或等于0的整数，不超过文本实际长度，end值要大于start值。

**类型：** number

**起始版本：** 10

<!--Device-Range-end: int--><!--Device-Range-end: int-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## start

```TypeScript
start: number
```

选中文本的首字符在编辑框的索引值。该参数应为大于或等于0的整数，不超过文本实际长度。

**类型：** number

**起始版本：** 10

<!--Device-Range-start: int--><!--Device-Range-start: int-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

