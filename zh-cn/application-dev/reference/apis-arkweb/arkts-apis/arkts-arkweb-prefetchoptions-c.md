# PrefetchOptions

Defines the PrefetchOptions class.

**起始版本：** 21

**系统能力：** SystemCapability.Web.Webview.Core

## constructor

```TypeScript
constructor()
```

Constructor for PrefetchOptions.

**起始版本：** 21

**系统能力：** SystemCapability.Web.Webview.Core

## ignoreCacheControlNoStore

```TypeScript
ignoreCacheControlNoStore: boolean
```

设置是否忽略响应头中的Cache-Control: no-store。默认值：false。
<p><strong>API 说明</strong>:<br>
此设置控制预取操作是否绕过 HTTP Cache-Control: no-store 指令。
重要提示：默认行为（false）符合 HTTP 安全标准。若要覆盖默认行为（设置为 true），必须对非敏感资源进行明确的**风险评估**。

**类型：** boolean

**起始版本：** 21

**系统能力：** SystemCapability.Web.Webview.Core

## minTimeBetweenPrefetchesMs

```TypeScript
minTimeBetweenPrefetchesMs: number
```

设置两次网页预取的最小时间间隔。

每次预取时会计算和上次预取的间隔时间，若小于设置值，则取消本次预取。

该间隔用于限制预取的频率，以平衡性能和资源使用。

默认为500，最大值为500。单位: ms。

设置为负数时，默认为0。

**类型：** number

**起始版本：** 21

**系统能力：** SystemCapability.Web.Webview.Core

