# PrintExtensionAbility (System API)

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

## onRequestPreview

```TypeScript
onRequestPreview(jobInfo: print.PrintJob): string
```

Defines a method called when the system print service requests a preview. You need to inherit the **PrintExtensionAbility** class and implement this method to return the preview result to the system print service.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-PrintExtensionAbility-onRequestPreview(jobInfo: print.PrintJob): string--><!--Device-PrintExtensionAbility-onRequestPreview(jobInfo: print.PrintJob): string-End-->

**System capability:** SystemCapability.Print.PrintFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| jobInfo | [print.PrintJob](arkts-basicservices-print-printjob-i.md) | Yes | Information about the print job. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Preview result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | not system application |

<!--Del-->
**Examples**

```TypeScript
import { print, PrintExtensionAbility } from '@kit.BasicServicesKit';

export default class HWPrintExtension extends PrintExtensionAbility {
    onRequestPreview(jobInfo: print.PrintJob): string {
        console.info('onRequestPreview enter');
        // ...
        let previewResult: string = '';
        return previewResult;
    }
}
```

<!--DelEnd-->
