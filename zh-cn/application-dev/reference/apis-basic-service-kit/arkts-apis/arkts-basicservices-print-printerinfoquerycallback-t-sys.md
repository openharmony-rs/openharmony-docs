# PrinterInfoQueryCallback（系统接口）

```TypeScript
type PrinterInfoQueryCallback = (printerInfo: PrinterInformation, ppdInfo: PpdInfo[]) => void
```

定义注册监听printInfoQuery事件的回调类型。printInfo的值表示打印机信息。ppdInfo的值表示所有打印机的ppd信息。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-print-type PrinterInfoQueryCallback = (printerInfo: PrinterInformation, ppdInfo: PpdInfo[]) => void--><!--Device-print-type PrinterInfoQueryCallback = (printerInfo: PrinterInformation, ppdInfo: PpdInfo[]) => void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| printerInfo | PrinterInformation | 是 | 打印机信息<br>打印机信息。 |
| ppdInfo | PpdInfo[] | 是 | 所有打印机ppd信息<br>所有打印机ppd信息。 |

