# PrinterStateChangeCallback（系统接口）

```TypeScript
type PrinterStateChangeCallback = (state: PrinterState, info: PrinterInfo) => void
```

Defines the callback type used in registering to listen for PrinterState. The value of state indicates the state of printer. The value of info indicates the latest printer info.

**起始版本：** 23

<!--Device-print-type PrinterStateChangeCallback = (state: PrinterState, info: PrinterInfo) => void--><!--Device-print-type PrinterStateChangeCallback = (state: PrinterState, info: PrinterInfo) => void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| state | [PrinterState](arkts-basicservices-print-printerstate-e.md) | 是 | the state of printer |
| info | [PrinterInfo](arkts-basicservices-print-printerinfo-i-sys.md) | 是 | the information of the latest printer |

