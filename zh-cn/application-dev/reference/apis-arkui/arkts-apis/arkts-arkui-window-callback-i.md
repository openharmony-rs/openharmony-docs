# Callback

Defines the window callback.

**起始版本：** 15

<!--Device-unnamed-declare interface Callback<T, V = void>--><!--Device-unnamed-declare interface Callback<T, V = void>-End-->

**系统能力：** SystemCapability.Window.SessionManager

## 导入模块

```TypeScript
import { window } from '@kit.ArkUI';
```

<a id="constructor"></a>
## constructor

```TypeScript
(data: T): V
```

Defines the callback info.

**起始版本：** 15

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-Callback-(data: T): V--><!--Device-Callback-(data: T): V-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | T | 是 | the data will be used in the callback. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| V | - Returns result of the callback. |

