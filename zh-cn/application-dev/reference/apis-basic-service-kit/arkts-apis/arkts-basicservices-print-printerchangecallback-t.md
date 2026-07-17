# PrinterChangeCallback

```TypeScript
type PrinterChangeCallback = (event: PrinterEvent, printerInformation: PrinterInformation) => void
```

将打印机事件和打印机信息作为参数的回调方法。

**起始版本：** 18

<!--Device-print-type PrinterChangeCallback = (event: PrinterEvent, printerInformation: PrinterInformation) => void--><!--Device-print-type PrinterChangeCallback = (event: PrinterEvent, printerInformation: PrinterInformation) => void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | PrinterEvent | 是 | 表示打印机事件。 |
| printerInformation | PrinterInformation | 是 | 表示打印机信息。 |

