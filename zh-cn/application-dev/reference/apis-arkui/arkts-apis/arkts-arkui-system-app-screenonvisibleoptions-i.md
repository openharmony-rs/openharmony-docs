# ScreenOnVisibleOptions

定义屏幕上可见接口的选项。

**起始版本：** 3

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { App, AppResponse, RequestFullWindowOptions, ScreenOnVisibleOptions } from '@kit.ArkUI';
```

## complete

```TypeScript
complete?: () => void
```

接口调用结束的回调函数。

**起始版本：** 3

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fail

```TypeScript
fail?: (data: string, code: number) => void
```

接口调用失败的回调函数。

**起始版本：** 3

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | string | 是 |  |
| code | number | 是 |  |

## success

```TypeScript
success?: () => void
```

接口调用成功的回调函数。

**起始版本：** 3

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## visible

```TypeScript
visible?: boolean
```

是否启动保活，默认值false。

**类型：** boolean

**起始版本：** 3

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
