# SystemWindowOptions（系统接口）

系统窗口的创建参数。

**起始版本：** 23

<!--Device-window-interface SystemWindowOptions--><!--Device-window-interface SystemWindowOptions-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { floatingBall } from '@kit.ArkUI';
import { floatView } from '@kit.ArkUI';
import { window } from '@kit.ArkUI';
```

## windowType

```TypeScript
windowType: WindowType
```

窗口类型。无默认类型，不配置会导致窗口创建失败。不支持TYPE_DIALOG类型。

**类型：** WindowType

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SystemWindowOptions-windowType: WindowType--><!--Device-SystemWindowOptions-windowType: WindowType-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

