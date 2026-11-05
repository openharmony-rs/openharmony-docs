# PrintExtensionAbility (System API)

```TypeScript
declare class PrintExtensionAbility
```

This module provides the APIs for calling the print extension ability. **PrintExtensionAbility** runs based on the lifecycle callback mechanism. The system invokes the corresponding callback methods to connect to the print extension, discover printers, connect to or disconnect from printers, query printer capabilities, and start or cancel print jobs. You need to implement the print extension logic in each callback.

**Since:** 14

<!--Device-unnamed-declare class PrintExtensionAbility--><!--Device-unnamed-declare class PrintExtensionAbility-End-->

**System capability:** SystemCapability.Print.PrintFramework

## ExtensionAbility Usage Restrictions

To ensure system security and stability, PrintExtensionAbility is restricted from abusing system resources. The system controls its capabilities and does not support referencing some modules. For details, see [Appendix](#appendix).

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

## Appendix

PrintExtensionAbility does not support referencing the following modules.

| Kit | Module |
| --- | --- |
| Contacts Kit | [@ohos.contact](../../apis-contacts-kit/arkts-apis/arkts-contacts-contact.md) |
| Location Kit | [@ohos.geolocation](../../apis-location-kit/arkts-apis/arkts-location-geolocation.md) |
| Location Kit | [@ohos.geoLocationManager](../../apis-location-kit/arkts-apis/arkts-location-geolocationmanager.md) |
| Camera Kit | [@ohos.multimedia.camera](../../apis-camera-kit/arkts-apis/arkts-camera-multimedia-camera.md) |
| Audio Kit | [@ohos.multimedia.audio](../../apis-audio-kit/arkts-apis/arkts-audio-multimedia-audio.md) |
| Media Kit | [@ohos.multimedia.media](../../apis-media-kit/arkts-apis/arkts-media-multimedia-media.md) |
| Telephony Kit | [@ohos.telephony.call](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-call.md) |
| Telephony Kit | [@ohos.telephony.sim](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-sim.md) |
| Telephony Kit | [@ohos.telephony.sms](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-sms.md) |
