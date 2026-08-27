# BackRouterOptions

定义路由器返回的选项。

**起始版本：** 7

**废弃版本：** 8

**替代接口：** RouterOptions

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { SystemRouter, BackRouterOptions, DisableAlertBeforeBackPageOptions, EnableAlertBeforeBackPageOptions, RouterOptions, RouterState } from '@kit.ArkUI';
```

## params

```TypeScript
params?: Object
```

返回时要同时传递到目标页面的数据。

**类型：** Object

**起始版本：** 7

**废弃版本：** 8

**替代接口：** params

**系统能力：** SystemCapability.ArkUI.ArkUI.Lite

## uri

```TypeScript
uri?: string
```

返回到指定uri的界面，如果页面栈上没有uri页面，则不响应该情况。如果uri未设置，则返回上一页。

**类型：** string

**起始版本：** 7

**废弃版本：** 8

**替代接口：** url

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
