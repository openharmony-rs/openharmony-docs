# PrintExtensionAbility

```TypeScript
declare class PrintExtensionAbility
```

This module provides the APIs for calling the print extension ability. **PrintExtensionAbility** runs based on the lifecycle callback mechanism. The system invokes the corresponding callback methods to connect to the print extension, discover printers, connect to or disconnect from printers, query printer capabilities, and start or cancel print jobs. You need to implement the print extension logic in each callback.

**Since:** 14

<!--Device-unnamed-declare class PrintExtensionAbility--><!--Device-unnamed-declare class PrintExtensionAbility-End-->

**System capability:** SystemCapability.Print.PrintFramework

## Modules to Import

```TypeScript
import { PrintExtensionAbility } from '@kit.BasicServicesKit';
```

## onCancelPrintJob

```TypeScript
public onCancelPrintJob(jobInfo: print.PrintJob): void
```

Defines an API called when the started print job is canceled. You need to implement the logic for canceling the print job in this callback, stop the ongoing print operation, and clear related resources.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-PrintExtensionAbility-public onCancelPrintJob(jobInfo: print.PrintJob): void--><!--Device-PrintExtensionAbility-public onCancelPrintJob(jobInfo: print.PrintJob): void-End-->

**System capability:** SystemCapability.Print.PrintFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| jobInfo | [print.PrintJob](arkts-basicservices-print-printjob-i.md) | Yes | Information about the print job, including detailed configuration and status such as the job ID, printer ID, and document information. The print job has been started by calling **onStartPrintJob**, and this parameter can be used to locate the target print job to be cancelled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |

**Examples**

```TypeScript
import { print, PrintExtensionAbility } from '@kit.BasicServicesKit';

export default class CustomPrintExtension extends PrintExtensionAbility {
    onCancelPrintJob(jobInfo: print.PrintJob): void {
        console.info('onCancelPrintJob, jobId is: ' + jobInfo.jobId);
        // ...
    }
}
```

## onConnectPrinter

```TypeScript
onConnectPrinter(printerId: number): void
```

Defines an API called when the device connects to the specified printer. You need to implement the logic for connecting to the specified printer (identified by **printerId**) in this callback.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

<!--Device-PrintExtensionAbility-onConnectPrinter(printerId: int): void--><!--Device-PrintExtensionAbility-onConnectPrinter(printerId: int): void-End-->

**System capability:** SystemCapability.Print.PrintFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| printerId | number | Yes | ID of the discovered printer, which should be a valid printer ID reported during the printer discovery process. |

**Examples**

```TypeScript
import { PrintExtensionAbility } from '@kit.BasicServicesKit';

export default class CustomPrintExtension extends PrintExtensionAbility {
    onConnectPrinter(printerId: number): void {
        console.info('onConnectPrinter enter');
        // ...
    }
}
```

## onCreate

```TypeScript
onCreate(want: Want): void
```

Define an API called when the system connects to the print extension ability for the first time. You need complete the initialization of the print extension ability in this callback, such as initializing necessary resources and states.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

<!--Device-PrintExtensionAbility-onCreate(want: Want): void--><!--Device-PrintExtensionAbility-onCreate(want: Want): void-End-->

**System capability:** SystemCapability.Print.PrintFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | Want information passed in when the print extension is created, including the information specified by the caller (such as **action** and **uri**), used to initialize the print extension ability. |

**Examples**

```TypeScript
import { PrintExtensionAbility } from '@kit.BasicServicesKit';
import { Want } from '@kit.AbilityKit';

export default class CustomPrintExtension extends PrintExtensionAbility {
    onCreate(want: Want): void {
        console.info('onCreate');
        // ...
    }
}
```

## onDestroy

```TypeScript
onDestroy(): void
```

Defines an API called when the print extension ability ends. In this callback, you need to release related resources and complete the necessary clearance work.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

<!--Device-PrintExtensionAbility-onDestroy(): void--><!--Device-PrintExtensionAbility-onDestroy(): void-End-->

**System capability:** SystemCapability.Print.PrintFramework

**Examples**

```TypeScript
import { PrintExtensionAbility } from '@kit.BasicServicesKit';

export default class CustomPrintExtension extends PrintExtensionAbility {
    onDestroy(): void {
        console.info('onDestroy');
    }
}
```

## onDisconnectPrinter

```TypeScript
onDisconnectPrinter(printerId: number): void
```

Defines an API called when the device disconnects from the specified printer. You need to implement the logic for disconnecting from the printer and release related resources in this callback.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

<!--Device-PrintExtensionAbility-onDisconnectPrinter(printerId: int): void--><!--Device-PrintExtensionAbility-onDisconnectPrinter(printerId: int): void-End-->

**System capability:** SystemCapability.Print.PrintFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| printerId | number | Yes | ID of the connected printer, which should be a valid printer ID reported during the printer discovery process. |

**Examples**

```TypeScript
import { PrintExtensionAbility } from '@kit.BasicServicesKit';

export default class CustomPrintExtension extends PrintExtensionAbility {
    onDisconnectPrinter(printerId: number): void {
        console.info('onDisconnectPrinter enter');
        // ...
    }
}
```

## onRequestPrinterCapability

```TypeScript
public onRequestPrinterCapability(printerId: number): print.PrinterCapability
```

Defines an API called when the capabilities supported by the printer (such as color mode, duplex mode, and paper size) are requested. For example, this callback is triggered when the system needs to obtain the capability information supported by a printer after the user selects the printer in the print settings page. In this callback, you need to query and return **print.PrinterCapability** of the corresponding printer based on **printerId**.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-PrintExtensionAbility-public onRequestPrinterCapability(printerId: int): print.PrinterCapability--><!--Device-PrintExtensionAbility-public onRequestPrinterCapability(printerId: int): print.PrinterCapability-End-->

**System capability:** SystemCapability.Print.PrintFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| printerId | number | Yes | Printer ID, which is a valid printer ID reported during the printer discovery process. |

**Return value:**

| Type | Description |
| --- | --- |
| [print.PrinterCapability](arkts-basicservices-print-printercapability-i.md) | Capability supported by the printer, such as the color mode, duplex mode, and paper size. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |

**Examples**

```TypeScript
import { print, PrintExtensionAbility } from '@kit.BasicServicesKit';

export default class CustomPrintExtension extends PrintExtensionAbility {
    onRequestPrinterCapability(printerId: number): print.PrinterCapability {
        console.info('onRequestPrinterCapability enter');
        // ...
        const printerCapability: print.PrinterCapability = {
            colorMode: 1,
            duplexMode: 1,
            pageSize: []
        };
        return printerCapability;
    }
}
```

## onStartDiscoverPrinter

```TypeScript
onStartDiscoverPrinter(): void
```

Defines an API called when printer discovery starts. You need to implement the printer discovery logic in this callback, and report the discovered printer information to the system through [addPrinterToDiscovery](arkts-basicservices-print-addprintertodiscovery-f.md).

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

<!--Device-PrintExtensionAbility-onStartDiscoverPrinter(): void--><!--Device-PrintExtensionAbility-onStartDiscoverPrinter(): void-End-->

**System capability:** SystemCapability.Print.PrintFramework

**Examples**

```TypeScript
import { PrintExtensionAbility } from '@kit.BasicServicesKit';

export default class CustomPrintExtension extends PrintExtensionAbility {
    onStartDiscoverPrinter(): void {
        console.info('onStartDiscoverPrinter enter');
        // ...
    }
}
```

## onStartPrintJob

```TypeScript
public onStartPrintJob(jobInfo: print.PrintJob): void
```

Defines an API called when the print job starts. You need to process the print operation based on the job information in **jobInfo**, such as parsing the print job parameters and executing the corresponding print process.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-PrintExtensionAbility-public onStartPrintJob(jobInfo: print.PrintJob): void--><!--Device-PrintExtensionAbility-public onStartPrintJob(jobInfo: print.PrintJob): void-End-->

**System capability:** SystemCapability.Print.PrintFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| jobInfo | [print.PrintJob](arkts-basicservices-print-printjob-i.md) | Yes | Information about the print job, including detailed configuration and status such as the job ID, printer ID, and document information, used to specify the print job to start. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |

**Examples**

```TypeScript
import { print, PrintExtensionAbility } from '@kit.BasicServicesKit';

export default class CustomPrintExtension extends PrintExtensionAbility {
    onStartPrintJob(jobInfo: print.PrintJob): void {
        console.info('onStartPrintJob, jobId is: ' + jobInfo.jobId);
        // ...
    }
}
```

## onStopDiscoverPrinter

```TypeScript
onStopDiscoverPrinter(): void
```

Defines an API called when printer discovery stops. You need to stop the printer discovery process and release related resources in this callback.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

<!--Device-PrintExtensionAbility-onStopDiscoverPrinter(): void--><!--Device-PrintExtensionAbility-onStopDiscoverPrinter(): void-End-->

**System capability:** SystemCapability.Print.PrintFramework

**Examples**

```TypeScript
import { PrintExtensionAbility } from '@kit.BasicServicesKit';

export default class CustomPrintExtension extends PrintExtensionAbility {
    onStopDiscoverPrinter(): void {
        console.info('onStopDiscoverPrinter enter');
        // ...
    }
}
```

## context

```TypeScript
context: PrintExtensionContext
```

Context of the print extension ability.

**Type:** [PrintExtensionContext](arkts-basicservices-printextensioncontext-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-PrintExtensionAbility-context: PrintExtensionContext--><!--Device-PrintExtensionAbility-context: PrintExtensionContext-End-->

**System capability:** SystemCapability.Print.PrintFramework
