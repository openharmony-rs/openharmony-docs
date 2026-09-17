# PrintExtensionAbility

class of print extension ability.

**Since:** 14

**System capability:** SystemCapability.Print.PrintFramework

## Modules to Import

```TypeScript
import { PrintExtensionAbility } from '@kit.BasicServicesKit';
```

## onCancelPrintJob

```TypeScript
public onCancelPrintJob(jobInfo: print.PrintJob): void
```

Called once to remove the print job has been started.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Print.PrintFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| jobInfo | [print.PrintJob](arkts-basicservices-print-printjob-i.md) | Yes | Indicates the information of print job. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | not system application<br>**Applicable version:** 10 - 23 |

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

Called once to connect to the specific printer.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Print.PrintFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| printerId | number | Yes | connect the printerId. |

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

Called once to initialize the extensionAbility.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Print.PrintFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | call print page want params. |

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

Called once to finalize the extensionAbility.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

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

Called once to disconnect to the specific printer.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Print.PrintFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| printerId | number | Yes | connect the printerId. |

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

Called once to request the printer's capabilities.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Print.PrintFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| printerId | number | Yes | Indicates the information of printer. |

**Return value:**

| Type | Description |
| --- | --- |
| [print.PrinterCapability](arkts-basicservices-print-printercapability-i.md) | printer capability. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | not system application<br>**Applicable version:** 10 - 23 |

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

Called once to start to discover the printers connected with the device.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

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

Called once to start print job.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Print.PrintFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| jobInfo | [print.PrintJob](arkts-basicservices-print-printjob-i.md) | Yes | Indicates the information of print job. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | not system application<br>**Applicable version:** 10 - 23 |

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

Called once to stop discovering the printer.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

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

Indicates print service extension ability context.

**Type:** [PrintExtensionContext](arkts-basicservices-printextensioncontext-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Print.PrintFramework
