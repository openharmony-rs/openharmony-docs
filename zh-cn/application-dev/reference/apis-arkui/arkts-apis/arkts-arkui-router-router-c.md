# Router

通过不同的uri访问不同的页面。

**起始版本：** 3

**废弃版本：** 8

**替代接口：** router

<!--Device-unnamed-export default class Router--><!--Device-unnamed-export default class Router-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Lite

## 导入模块

```TypeScript
import { BackRouterOptions, DisableAlertBeforeBackPageOptions, RouterOptions, RouterState, EnableAlertBeforeBackPageOptions } from '@kit.ArkUI';
```

## back

```TypeScript
static back(options?: BackRouterOptions): void
```

返回上一页面或指定的页面。

**起始版本：** 3

**废弃版本：** 8

**替代接口：** back

<!--Device-Router-static back(options?: BackRouterOptions): void--><!--Device-Router-static back(options?: BackRouterOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [BackRouterOptions](arkts-arkui-router-backrouteroptions-i.md) | 否 | 详细请参考BackRouterOptions。 |

## clear

```TypeScript
static clear(): void
```

清空页面栈中的所有历史页面，仅保留当前页面作为栈顶页面。

**起始版本：** 3

**废弃版本：** 8

**替代接口：** clear

<!--Device-Router-static clear(): void--><!--Device-Router-static clear(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## disableAlertBeforeBackPage

```TypeScript
static disableAlertBeforeBackPage(options?: DisableAlertBeforeBackPageOptions): void
```

禁用页面返回询问对话框。

**起始版本：** 6

**废弃版本：** 8

**替代接口：** hideAlertBeforeBackPage

<!--Device-Router-static disableAlertBeforeBackPage(options?: DisableAlertBeforeBackPageOptions): void--><!--Device-Router-static disableAlertBeforeBackPage(options?: DisableAlertBeforeBackPageOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [DisableAlertBeforeBackPageOptions](arkts-arkui-router-disablealertbeforebackpageoptions-i.md) | 否 | 详细请参见DisableAlertBeforeBackPageOptions。 |

## enableAlertBeforeBackPage

```TypeScript
static enableAlertBeforeBackPage(options: EnableAlertBeforeBackPageOptions): void
```

开启页面返回询问对话框。

**起始版本：** 6

**废弃版本：** 8

**替代接口：** showAlertBeforeBackPage

<!--Device-Router-static enableAlertBeforeBackPage(options: EnableAlertBeforeBackPageOptions): void--><!--Device-Router-static enableAlertBeforeBackPage(options: EnableAlertBeforeBackPageOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [EnableAlertBeforeBackPageOptions](arkts-arkui-router-enablealertbeforebackpageoptions-i.md) | 是 | 详细请参见EnableAlertBeforeBackPageOptions。 |

## getLength

```TypeScript
static getLength(): string
```

获取当前在页面栈内的页面数量。

**起始版本：** 3

**废弃版本：** 8

**替代接口：** getLength

<!--Device-Router-static getLength(): string--><!--Device-Router-static getLength(): string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 页面数量，页面栈支持最大数值是32。 |

## getParams

```TypeScript
static getParams(): ParamsInterface
```

获取当前页面的参数信息。

**起始版本：** 7

**废弃版本：** 8

**替代接口：** getParams

<!--Device-Router-static getParams(): ParamsInterface--><!--Device-Router-static getParams(): ParamsInterface-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ParamsInterface](arkts-arkui-paramsinterface-t.md) | 详细请参见ParamsInterface。 |

## getState

```TypeScript
static getState(): RouterState
```

获取当前页面的状态信息。

**起始版本：** 3

**废弃版本：** 8

**替代接口：** getState

<!--Device-Router-static getState(): RouterState--><!--Device-Router-static getState(): RouterState-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RouterState](arkts-arkui-router-routerstate-i.md) | 详细请参见RouterState。 |

## push

```TypeScript
static push(options: RouterOptions): void
```

跳转到应用内的指定页面。
> **说明：**  
>  
> 页面路由栈支持的最大Page数量为32。

**起始版本：** 3

**废弃版本：** 8

**替代接口：** push

<!--Device-Router-static push(options: RouterOptions): void--><!--Device-Router-static push(options: RouterOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [RouterOptions](arkts-arkui-router-routeroptions-i.md) | 是 | 页面路由参数，详细请参考RouterOptions。 |

## replace

```TypeScript
static replace(options: RouterOptions): void
```

用应用内的某个页面替换当前页面，并销毁被替换的页面。

**起始版本：** 3

**废弃版本：** 8

**替代接口：** replace

<!--Device-Router-static replace(options: RouterOptions): void--><!--Device-Router-static replace(options: RouterOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [RouterOptions](arkts-arkui-router-routeroptions-i.md) | 是 | 页面路由参数，详细请参考RouterOptions。 |

