# PrinterInfoQueryCallback (System API)

```TypeScript
type PrinterInfoQueryCallback = (printerInfo: PrinterInformation, ppdInfo: PpdInfo[]) => void
```

Defines the callback type used in registering to listen for printerInfoQuery event. The value of printerInfo indicates the printer info. The value of ppdInfo indicates all the printer ppd info.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Print.PrintFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| printerInfo | [PrinterInformation](arkts-basicservices-print-printerinformation-i.md) | Yes | the printer info<br>Printer Information. |
| ppdInfo | [PpdInfo](arkts-basicservices-print-ppdinfo-i.md)[] | Yes | all the printer ppd info<br>All the printer ppd info. |
