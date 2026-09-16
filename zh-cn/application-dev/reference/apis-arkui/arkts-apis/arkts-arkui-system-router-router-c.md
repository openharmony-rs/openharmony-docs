# Router

通过不同的uri访问不同的页面。

**起始版本：** 3

**废弃版本：** 8

**替代接口：** [router](arkts-arkui-router.md)

**系统能力：** SystemCapability.ArkUI.ArkUI.Lite

## 导入模块

```TypeScript
import { SystemRouter, BackRouterOptions, DisableAlertBeforeBackPageOptions, EnableAlertBeforeBackPageOptions, RouterOptions, RouterState } from '@kit.ArkUI';
```

## back

```TypeScript
static back(options?: BackRouterOptions): void
```

返回上一页面或指定的页面。

**起始版本：** 3

**废弃版本：** 8

**替代接口：** back

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [BackRouterOptions](arkts-arkui-system-router-backrouteroptions-i.md) | 否 | 详细请参考BackRouterOptions。 |

## clear

```TypeScript
static clear(): void
```

清空页面栈中的所有历史页面，仅保留当前页面作为栈顶页面。

**起始版本：** 3

**废弃版本：** 8

**替代接口：** clear

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## disableAlertBeforeBackPage

```TypeScript
static disableAlertBeforeBackPage(options?: DisableAlertBeforeBackPageOptions): void
```

禁用页面返回询问对话框。

**起始版本：** 6

**废弃版本：** 8

**替代接口：** hideAlertBeforeBackPage

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [DisableAlertBeforeBackPageOptions](arkts-arkui-system-router-disablealertbeforebackpageoptions-i.md) | 否 | 详细请参见DisableAlertBeforeBackPageOptions。 |

## enableAlertBeforeBackPage

```TypeScript
static enableAlertBeforeBackPage(options: EnableAlertBeforeBackPageOptions): void
```

开启页面返回询问对话框。

**起始版本：** 6

**废弃版本：** 8

**替代接口：** showAlertBeforeBackPage

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [EnableAlertBeforeBackPageOptions](arkts-arkui-system-router-enablealertbeforebackpageoptions-i.md) | 是 | 详细请参见EnableAlertBeforeBackPageOptions。 |

## getLength

```TypeScript
static getLength(): string
```

获取当前在页面栈内的页面数量。

**起始版本：** 3

**废弃版本：** 8

**替代接口：** getLength

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

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RouterState](arkts-arkui-system-router-routerstate-i.md) | 详细请参见RouterState。 |

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

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [RouterOptions](arkts-arkui-system-router-routeroptions-i.md) | 是 | 页面路由参数，详细请参考RouterOptions。 |

## replace

```TypeScript
static replace(options: RouterOptions): void
```

用应用内的某个页面替换当前页面，并销毁被替换的页面。

**起始版本：** 3

**废弃版本：** 8

**替代接口：** replace

**系统能力：** SystemCapability.ArkUI.ArkUI.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [RouterOptions](arkts-arkui-system-router-routeroptions-i.md) | 是 | 页面路由参数，详细请参考RouterOptions。 |
