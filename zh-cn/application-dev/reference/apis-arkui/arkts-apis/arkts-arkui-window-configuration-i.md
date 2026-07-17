# Configuration

创建子窗口或系统窗口时的参数。

**起始版本：** 9

<!--Device-window-interface Configuration--><!--Device-window-interface Configuration-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## 导入模块

```TypeScript
import { window } from '@kit.ArkUI';
```

## ctx

```TypeScript
ctx?: BaseContext
```

当前应用上下文信息。不设置，则默认为空。<br>FA模型下不需要使用该参数，即可创建子窗口，使用该参数时会报错。<br>Stage模型必须使用该参数，用于创建全局悬浮窗、模态窗或系统窗口。 <br>

**类型：** BaseContext

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Configuration-ctx?: BaseContext--><!--Device-Configuration-ctx?: BaseContext-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## decorEnabled

```TypeScript
decorEnabled?: boolean
```

是否显示窗口装饰，仅在windowType为TYPE_DIALOG时生效。true表示显示，false表示不显示。此参数默认值为false。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Configuration-decorEnabled?: boolean--><!--Device-Configuration-decorEnabled?: boolean-End-->

**系统能力：** SystemCapability.Window.SessionManager

## displayId

```TypeScript
displayId?: number
```

当前屏幕ID。不设置，则默认为父窗口屏幕ID。<br>该参数应为非负整数，且对应屏幕ID存在。<br>扩展屏、异源虚拟屏场景下，全局悬浮窗可通过设置屏幕ID显示在指定屏幕上。<br>模态窗、系统窗设置屏幕ID无效，默认为父窗口屏幕ID。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Configuration-displayId?: long--><!--Device-Configuration-displayId?: long-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## name

```TypeScript
name: string
```

窗口名称。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Configuration-name: string--><!--Device-Configuration-name: string-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## parentId

```TypeScript
parentId?: number
```

父窗口ID。不设置，则默认为-1，默认父窗为当前应用上下文对应主窗。<br>FA模型下，该参数应为非负整数，且对应父窗口ID存在。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Configuration-parentId?: int--><!--Device-Configuration-parentId?: int-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## title

```TypeScript
title?: string
```

`decorEnabled`属性设置为true时，窗口的标题内容。标题显示区域最右端不超过系统三键区域最左端，超过部分以省略号表示。不设置，则默认为空字符串。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Configuration-title?: string--><!--Device-Configuration-title?: string-End-->

**系统能力：** SystemCapability.Window.SessionManager

## windowType

```TypeScript
windowType: WindowType
```

窗口类型。

**类型：** WindowType

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Configuration-windowType: WindowType--><!--Device-Configuration-windowType: WindowType-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

