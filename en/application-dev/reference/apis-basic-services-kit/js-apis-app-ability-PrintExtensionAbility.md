# @ohos.app.ability.PrintExtensionAbility (PrintExtensionAbility)

<!--Kit: Basic Services Kit-->
<!--Subsystem: Print-->
<!--Owner: @guoshengbang-->
<!--Designer: @baozewei-->
<!--Tester: @baozewei-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=2dd275ce017b43144b8b5631392ae3d24fe5affc translatedAt=2026-09-01T03:31:10.243Z pushedAt=2026-09-05T05:55:39.419Z -->

This module provides the APIs for calling the print extension ability. **PrintExtensionAbility** runs based on the lifecycle callback mechanism. The system invokes the corresponding callback methods to connect to the print extension, discover printers, connect to or disconnect from printers, query printer capabilities, and start or cancel print jobs. You need to implement the print extension logic in each callback.

> **NOTE**
> The initial APIs of this module are supported since API version 14. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { PrintExtensionAbility } from '@kit.BasicServicesKit';
```

## Properties

**System capability**: SystemCapability.Print.PrintFramework

| Name | Type | Read-only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| context | [PrintExtensionContext](js-apis-PrintExtensionContext.md) | No | No | Context of the print extension ability.<br>**Since:** 26.0.0<br> |

## PrintExtensionAbility

### onCreate

onCreate(want: Want): void

Define an API called when the system connects to the print extension ability for the first time. You need complete the initialization of the print extension ability in this callback, such as initializing necessary resources and states.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](../apis-ability-kit/js-apis-application-want.md#want) | Yes | Want information passed in when the print extension is created, including the information specified by the caller (such as **action** and **uri**), used to initialize the print extension ability. |

**Example**

```ts
import { PrintExtensionAbility } from '@kit.BasicServicesKit';
import { Want } from '@kit.AbilityKit';

export default class CustomPrintExtension extends PrintExtensionAbility {
    onCreate(want: Want): void {
        console.info('onCreate');
        // ...
    }
}
```

### onStartDiscoverPrinter

onStartDiscoverPrinter(): void

Defines an API called when printer discovery starts. You need to implement the printer discovery logic in this callback, and report the discovered printer information to the system through [addPrinterToDiscovery](js-apis-print.md#printaddprintertodiscovery14).

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Print.PrintFramework

**Example**

```ts
import { PrintExtensionAbility } from '@kit.BasicServicesKit';

export default class CustomPrintExtension extends PrintExtensionAbility {
    onStartDiscoverPrinter(): void {
        console.info('onStartDiscoverPrinter enter');
        // ...
    }
}
```

### onStopDiscoverPrinter

onStopDiscoverPrinter(): void

Defines an API called when printer discovery stops. You need to stop the printer discovery process and release related resources in this callback.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Print.PrintFramework

**Example**

```ts
import { PrintExtensionAbility } from '@kit.BasicServicesKit';

export default class CustomPrintExtension extends PrintExtensionAbility {
    onStopDiscoverPrinter(): void {
        console.info('onStopDiscoverPrinter enter');
        // ...
    }
}
```

### onConnectPrinter

onConnectPrinter(printerId: number): void

Defines an API called when the device connects to the specified printer. You need to implement the logic for connecting to the specified printer (identified by **printerId**) in this callback.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| printerId | number | Yes | ID of the discovered printer, which should be a valid printer ID reported during the printer discovery process. |

**Example**

```ts
import { PrintExtensionAbility } from '@kit.BasicServicesKit';

export default class CustomPrintExtension extends PrintExtensionAbility {
    onConnectPrinter(printerId: number): void {
        console.info('onConnectPrinter enter');
        // ...
    }
}
```

### onDisconnectPrinter

onDisconnectPrinter(printerId: number): void

Defines an API called when the device disconnects from the specified printer. You need to implement the logic for disconnecting from the printer and release related resources in this callback.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| printerId | number | Yes | ID of the connected printer, which should be a valid printer ID reported during the printer discovery process. |

**Example**

```ts
import { PrintExtensionAbility } from '@kit.BasicServicesKit';

export default class CustomPrintExtension extends PrintExtensionAbility {
    onDisconnectPrinter(printerId: number): void {
        console.info('onDisconnectPrinter enter');
        // ...
    }
}
```

### onStartPrintJob<sup>24+</sup>

onStartPrintJob(jobInfo: print.PrintJob): void

Defines an API called when the print job starts. You need to process the print operation based on the job information in **jobInfo**, such as parsing the print job parameters and executing the corresponding print process.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| jobInfo | [print.PrintJob](js-apis-print.md#printjob24) | Yes | Information about the print job, including detailed configuration and status such as the job ID, printer ID, and document information, used to specify the print job to start. |

**Example**

```ts
import { print, PrintExtensionAbility } from '@kit.BasicServicesKit';

export default class CustomPrintExtension extends PrintExtensionAbility {
    onStartPrintJob(jobInfo: print.PrintJob): void {
        console.info('onStartPrintJob, jobId is: ' + jobInfo.jobId);
        // ...
    }
}
```

### onCancelPrintJob<sup>24+</sup>

onCancelPrintJob(jobInfo: print.PrintJob): void

Defines an API called when the started print job is canceled. You need to implement the logic for canceling the print job in this callback, stop the ongoing print operation, and clear related resources.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| jobInfo | [print.PrintJob](js-apis-print.md#printjob24) | Yes | Information about the print job, including detailed configuration and status such as the job ID, printer ID, and document information. The print job has been started by calling **onStartPrintJob**, and this parameter can be used to locate the target print job to be cancelled. |

**Example**

```ts
import { print, PrintExtensionAbility } from '@kit.BasicServicesKit';

export default class CustomPrintExtension extends PrintExtensionAbility {
    onCancelPrintJob(jobInfo: print.PrintJob): void {
        console.info('onCancelPrintJob, jobId is: ' + jobInfo.jobId);
        // ...
    }
}
```

### onRequestPrinterCapability<sup>24+</sup>

onRequestPrinterCapability(printerId: number): print.PrinterCapability

Defines an API called when the capabilities supported by the printer (such as color mode, duplex mode, and paper size) are requested. For example, this callback is triggered when the system needs to obtain the capability information supported by a printer after the user selects the printer in the print settings page. In this callback, you need to query and return **print.PrinterCapability** of the corresponding printer based on **printerId**.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| printerId | number | Yes | Printer ID, which is a valid printer ID reported during the printer discovery process. |

**Return value**
| **Type** | **Description**|
| -------- | -------- |
| [print.PrinterCapability](js-apis-print.md#printercapability24) | Capability supported by the printer, such as the color mode, duplex mode, and paper size. |

**Example**

```ts
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

### onDestroy

onDestroy(): void

Defines an API called when the print extension ability ends. In this callback, you need to release related resources and complete the necessary clearance work.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Print.PrintFramework

**Example**

```ts
import { PrintExtensionAbility } from '@kit.BasicServicesKit';

export default class CustomPrintExtension extends PrintExtensionAbility {
    onDestroy(): void {
        console.info('onDestroy');
    }
}
```
