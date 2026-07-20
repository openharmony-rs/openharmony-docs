# ScreenOnVisibleOptions

定义屏幕上可见接口的选项。

**起始版本：** 3

<!--Device-unnamed-export interface ScreenOnVisibleOptions--><!--Device-unnamed-export interface ScreenOnVisibleOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AppResponse, ScreenOnVisibleOptions, RequestFullWindowOptions } from '@kit.ArkUI';
```

## complete

```TypeScript
complete?: () => void
```

接口调用结束的回调函数。

**类型：** () =&gt; void

**起始版本：** 3

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScreenOnVisibleOptions-complete?: () => void--><!--Device-ScreenOnVisibleOptions-complete?: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fail

```TypeScript
fail?: (data: string, code: number) => void
```

接口调用失败的回调函数。

**类型：** (data: string, code: number) =&gt; void

**起始版本：** 3

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScreenOnVisibleOptions-fail?: (data: string, code: number) => void--><!--Device-ScreenOnVisibleOptions-fail?: (data: string, code: number) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## success

```TypeScript
success?: () => void
```

接口调用成功的回调函数。

**类型：** () =&gt; void

**起始版本：** 3

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScreenOnVisibleOptions-success?: () => void--><!--Device-ScreenOnVisibleOptions-success?: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## visible

```TypeScript
visible?: boolean
```

是否启动保活，默认值false。

**类型：** boolean

**起始版本：** 3

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScreenOnVisibleOptions-visible?: boolean--><!--Device-ScreenOnVisibleOptions-visible?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

