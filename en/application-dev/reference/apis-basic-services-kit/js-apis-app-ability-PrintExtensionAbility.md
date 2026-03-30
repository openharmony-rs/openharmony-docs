# @ohos.app.ability.PrintExtensionAbility (PrintExtensionAbility)

<!--Kit: Basic Services Kit-->
<!--Subsystem: Print-->
<!--Owner: @guoshengbang-->
<!--Designer: @gcw_4D6e0BBd-->
<!--Tester: @guoshengbang-->
<!--Adviser: @RayShih-->

The **PrintExtensionAbility** module provides operation APIs of the print extension ability.

> **NOTE** 
> The initial APIs of this module are supported since API version 14. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { PrintExtensionAbility } from '@kit.BasicServicesKit';
```

## PrintExtensionAbility

### onCreate

onCreate(want: Want): void

Called to initialize the print extension when the system connects to the extension for the first time.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](../apis-ability-kit/js-apis-application-want.md#want) | Yes| Parameters required for invoking the print page.|

**Example**

```ts
import { PrintExtensionAbility } from '@kit.BasicServicesKit';
import { Want } from '@kit.AbilityKit';

export default class HWPrintExtension extends PrintExtensionAbility {
    onCreate(want: Want): void {
        console.info('onCreate');
        // ...
    }
}
```

### onStartDiscoverPrinter

onStartDiscoverPrinter(): void

Called when an attempt to discover printers starts.

**System capability**: SystemCapability.Print.PrintFramework

**Example**

```ts
import { PrintExtensionAbility } from '@kit.BasicServicesKit';

export default class HWPrintExtension extends PrintExtensionAbility {
    onStartDiscoverPrinter(): void {
        console.info('onStartDiscoverPrinter enter');
        // ...
    }
}
```

### onStopDiscoverPrinter

onStopDiscoverPrinter(): void

Called when the attempt to discover printers stops.

**System capability**: SystemCapability.Print.PrintFramework

**Example**

```ts
import { PrintExtensionAbility } from '@kit.BasicServicesKit';

export default class HWPrintExtension extends PrintExtensionAbility {
    onStopDiscoverPrinter(): void {
        console.info('onStopDiscoverPrinter enter');
        // ...
    }
}
```

### onConnectPrinter

onConnectPrinter(printerId: number): void

Called when the device connects to the specified printer.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| printerId | number | Yes| Printer ID.|

**Example**

```ts
import { PrintExtensionAbility } from '@kit.BasicServicesKit';

export default class HWPrintExtension extends PrintExtensionAbility {
    onConnectPrinter(printerId: number): void {
        console.info('onConnectPrinter enter');
        // ...
    }
}
```

### onDisconnectPrinter

onDisconnectPrinter(printerId: number): void

Called when the device disconnects from the specified printer.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| printerId | number | Yes| Printer ID.|

**Example**

```ts
import { PrintExtensionAbility } from '@kit.BasicServicesKit';

export default class HWPrintExtension extends PrintExtensionAbility {
    onDisconnectPrinter(printerId: number): void {
        console.info('onDisconnectPrinter enter');
        // ...
    }
}
```

### onStartPrintJob

onStartPrintJob(jobInfo: print.PrintJob): void

Called when the specified print job starts.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| jobInfo | [print.PrintJob](js-apis-print.md#printjob24) | Yes| Information about the print job.|

**Example**

```ts
import { print, PrintExtensionAbility } from '@kit.BasicServicesKit';

export default class HWPrintExtension extends PrintExtensionAbility {
    onStartPrintJob(jobInfo: print.PrintJob): void {
        console.info('onStartPrintJob, jobId is: ' + jobInfo.jobId);
        // ...
    }
}
```

### onCancelPrintJob

onCancelPrintJob(jobInfo: print.PrintJob): void

Called when the specified print job is canceled.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| jobInfo | [print.PrintJob](js-apis-print.md#printjob24) | Yes| Information about the print job.|

**Example**

```ts
import { print, PrintExtensionAbility } from '@kit.BasicServicesKit';

export default class HWPrintExtension extends PrintExtensionAbility {
    onCancelPrintJob(jobInfo: print.PrintJob): void {
        console.info('onCancelPrintJob, jobId is: ' + jobInfo.jobId);
        // ...
    }
}
```

### onRequestPrinterCapability

onRequestPrinterCapability(printerId: number): print.PrinterCapability

Called when a request is sent to check the capability of the specified printer.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| printerId | number | Yes| Printer ID.|

**Return value**
| **Type** | **Description**|
| -------- | -------- |
| [print.PrinterCapability](js-apis-print.md#printercapability24) | Capability of the printer.|

**Example**

```ts
import { print, PrintExtensionAbility } from '@kit.BasicServicesKit';

export default class HWPrintExtension extends PrintExtensionAbility {
    onRequestPrinterCapability(printerId: number): print.PrinterCapability {
        console.info('onRequestPrinterCapability enter');
        // ...
        let tmp : print.PrinterCapability = {
            colorMode : 1,
            duplexMode : 1,
            pageSize : []
        };
        return tmp;
    }
}
```

### onDestroy

onDestroy(): void

Called when the print extension ability is stopped.

**System capability**: SystemCapability.Print.PrintFramework

**Example**

```ts
import { PrintExtensionAbility } from '@kit.BasicServicesKit';

export default class HWPrintExtension extends PrintExtensionAbility {
    onDestroy(): void {
        console.info('onDestroy');
    }
}
```
