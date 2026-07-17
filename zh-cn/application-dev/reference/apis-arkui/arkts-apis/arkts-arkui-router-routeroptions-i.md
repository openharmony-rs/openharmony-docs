# RouterOptions

定义路由器的选项。

**起始版本：** 3

**废弃版本：** 8

**替代接口：** RouterOptions

<!--Device-unnamed-export interface RouterOptions--><!--Device-unnamed-export interface RouterOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Lite

## 导入模块

```TypeScript
import { BackRouterOptions, DisableAlertBeforeBackPageOptions, RouterOptions, RouterState, EnableAlertBeforeBackPageOptions } from '@kit.ArkUI';
```

## params

```TypeScript
params?: Object
```

表示路由跳转时要同时传递到目标页面的数据。跳转到目标页面后，使用getParams()获取传递的参数，此外，在类web范式中，参数也可以在页面中直接使用，如this.keyValue(keyValue为跳转时params参数中的key值)，如果目标页面中已有该字段，则其值会被传入的字段值覆盖。

**类型：** Object

**起始版本：** 3

**废弃版本：** 8

**替代接口：** params

<!--Device-RouterOptions-params?: Object--><!--Device-RouterOptions-params?: Object-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Lite

## uri

```TypeScript
uri: string
```

目标页面的uri，可以是以下的两种格式：

1. 页面的绝对路径，由config.json文件中的页面列表提供。例如：

- pages/index/index  
- pages/detail/detail

2. 特定路径。如果URI为斜杠（/），则显示主页。

**类型：** string

**起始版本：** 3

**废弃版本：** 8

**替代接口：** url

<!--Device-RouterOptions-uri: string--><!--Device-RouterOptions-uri: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Lite

