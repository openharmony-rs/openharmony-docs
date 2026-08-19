# DesktopLyricState

桌面歌词状态。

**起始版本：** 23

<!--Device-avSession-interface DesktopLyricState--><!--Device-avSession-interface DesktopLyricState-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## 导入模块

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## isLocked

```TypeScript
isLocked: boolean
```

桌面歌词位置是否锁定。true表示已锁定，false表示未锁定。若已锁定，桌面显示歌词后，固定当前位置，不可被拖拽。

**类型：** boolean

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DesktopLyricState-isLocked: boolean--><!--Device-DesktopLyricState-isLocked: boolean-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

