# RouterState

定义路由器的状态。

**起始版本：** 3

**废弃版本：** 8

**替代接口：** RouterState

<!--Device-unnamed-export interface RouterState--><!--Device-unnamed-export interface RouterState-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { BackRouterOptions, DisableAlertBeforeBackPageOptions, RouterOptions, RouterState, EnableAlertBeforeBackPageOptions } from '@kit.ArkUI';
```

## index

```TypeScript
index: number
```

表示当前页面在页面栈中的索引。从栈底到栈顶，index从1开始递增。

**类型：** number

**起始版本：** 3

**废弃版本：** 8

**替代接口：** index

<!--Device-RouterState-index: number--><!--Device-RouterState-index: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## name

```TypeScript
name: string
```

表示当前页面的名称，即对应文件名。

**类型：** string

**起始版本：** 3

**废弃版本：** 8

**替代接口：** name

<!--Device-RouterState-name: string--><!--Device-RouterState-name: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## path

```TypeScript
path: string
```

表示当前页面的路径。

**类型：** string

**起始版本：** 3

**废弃版本：** 8

**替代接口：** path

<!--Device-RouterState-path: string--><!--Device-RouterState-path: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

