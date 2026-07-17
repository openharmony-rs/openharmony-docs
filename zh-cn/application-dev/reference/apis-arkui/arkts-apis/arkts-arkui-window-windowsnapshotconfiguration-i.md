# WindowSnapshotConfiguration

主窗口截图的配置项。

**起始版本：** 21

<!--Device-window-interface WindowSnapshotConfiguration--><!--Device-window-interface WindowSnapshotConfiguration-End-->

**系统能力：** SystemCapability.Window.SessionManager

## 导入模块

```TypeScript
import { window } from '@kit.ArkUI';
```

## useCache

```TypeScript
useCache?: boolean
```

是否使用主窗口的已有截图。默认值为true。 true表示使用主窗口的已有截图，若主窗口无保存的截图，则使用主窗口的最新截图。false表示使用主窗口的最新截图。

**类型：** boolean

**起始版本：** 21

<!--Device-WindowSnapshotConfiguration-useCache?: boolean--><!--Device-WindowSnapshotConfiguration-useCache?: boolean-End-->

**系统能力：** SystemCapability.Window.SessionManager

