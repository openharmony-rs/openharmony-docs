# PrinterChangeCallback

```TypeScript
type PrinterChangeCallback = (event: PrinterEvent, printerInformation: PrinterInformation) => void
```

Defines a callback that takes the printer event and printer information as parameters.

**Since:** 18

**System capability:** SystemCapability.Print.PrintFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [PrinterEvent](arkts-basicservices-print-printerevent-e.md) | Yes | Printer event. |
| printerInformation | [PrinterInformation](arkts-basicservices-print-printerinformation-i.md) | Yes | Printer information. |
