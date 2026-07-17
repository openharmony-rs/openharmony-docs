# ShowWindowOptions

显示子窗口或系统窗口时的参数。

**起始版本：** 20

<!--Device-window-interface ShowWindowOptions--><!--Device-window-interface ShowWindowOptions-End-->

**系统能力：** SystemCapability.Window.SessionManager

## 导入模块

```TypeScript
import { window } from '@kit.ArkUI';
```

## focusOnShow

```TypeScript
focusOnShow?: boolean
```

窗口调用[showWindow()](arkts-arkui-window-window-i.md#showwindow-3)显示时是否自动获焦，默认为true。该参数对主窗、模态窗、dialog窗口不生效。

**类型：** boolean

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-ShowWindowOptions-focusOnShow?: boolean--><!--Device-ShowWindowOptions-focusOnShow?: boolean-End-->

**系统能力：** SystemCapability.Window.SessionManager

