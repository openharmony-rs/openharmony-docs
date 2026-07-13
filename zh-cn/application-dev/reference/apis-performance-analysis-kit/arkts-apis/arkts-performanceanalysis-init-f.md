# init

## init

```TypeScript
function init(): void
```

初始化应用灰度模块。多实例应用不支持调用此接口。

**起始版本：** 26.0.0

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.HiviewDFX.HiRetrieval

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 36000002 | Multi-instance applications not supported error.Possibly caused by invoking this function in a multi-instance application. |

