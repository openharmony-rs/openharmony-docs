# InputWindowInfo

输入法软键盘的窗口信息。

**起始版本：** 23

<!--Device-inputMethod-export interface InputWindowInfo--><!--Device-inputMethod-export interface InputWindowInfo-End-->

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

## userId

```TypeScript
userId?: int
```

显示输入法窗口的用户ID。 该属性仅系统应用可以使用。

**类型：** int

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-InputWindowInfo-userId?: int--><!--Device-InputWindowInfo-userId?: int-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**系统接口：** 此接口为系统接口。

