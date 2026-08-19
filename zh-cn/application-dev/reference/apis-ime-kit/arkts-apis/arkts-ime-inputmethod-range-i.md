# Range

文本的选中范围。

**起始版本：** 23

<!--Device-inputMethod-export interface Range--><!--Device-inputMethod-export interface Range-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## 导入模块

```TypeScript
import { inputMethod } from '@kit.IMEKit';
import { inputMethodEngine } from '@kit.IMEKit';
import { InputMethodListDialog, PatternOptions, Pattern } from '@kit.IMEKit';
import { PanelInfo, PanelType, PanelFlag } from '@kit.IMEKit';
import { InputMethodExtraConfig } from '@kit.IMEKit';
import { inputMethodSystemPanelManager } from '@kit.IMEKit';
```

## end

```TypeScript
end: int
```

选中文本的末字符在编辑框的索引值。该参数应为大于或等于0的整数，不超过文本实际长度，end值要大于start值。

**类型：** int

**起始版本：** 23

<!--Device-Range-end: int--><!--Device-Range-end: int-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## start

```TypeScript
start: int
```

选中文本的首字符在编辑框的索引值。该参数应为大于或等于0的整数，不超过文本实际长度。

**类型：** int

**起始版本：** 23

<!--Device-Range-start: int--><!--Device-Range-start: int-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

