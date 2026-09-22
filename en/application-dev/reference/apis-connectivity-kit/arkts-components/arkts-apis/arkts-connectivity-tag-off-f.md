# off

## Modules to Import

```TypeScript
import { tag } from '@kit.ConnectivityKit';
```

## off('readerMode')

```TypeScript
function off(type: 'readerMode', elementName: ElementName, callback?: AsyncCallback<TagInfo>): void
```

Unsubscribes from the NFC tag card read event. The device exits the reader mode and resumes card emulation. If the NFC reader mode is enabled by tag.on, this API must be used when the application page exits the foreground or is destroyed.

**Since:** 11

**Required permissions:** ohos.permission.NFC_TAG

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'readerMode' | Yes | Event type, which has a fixed value of **readerMode**. |
| elementName | [ElementName](../../apis-ability-kit/arkts-apis/arkts-ability-elementname-i.md) | Yes | Information about the tag reading page of the application. It cannot be empty and must contain at least **bundleName** and **abilityName**. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[TagInfo](arkts-connectivity-tag-taginfo-i.md)&gt; | No | Callback to unregister. If this parameter is not set, this API unregisters the tag reading callback for the specified **type**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [3100203](../errorcode-nfc.md#3100203-incorrect-api-call-sequence) | The off() API can be called only when the on() has been called. |
| [3100201](../errorcode-nfc.md#3100201-tag-readwrite-error) | The tag running state is abnormal in the service.<br>**Applicable version:** 12 and later |


## off('readerModeWithInterval')

```TypeScript
function off(type: 'readerModeWithInterval', elementName: ElementName, callback?: Callback<TagInfo>): void
```

Unsubscribes from the NFC tag card read event. The device exits the reader mode and resumes card emulation. If the NFC reader mode is enabled by tag.on, this API must be used when the application page exits the foreground or is destroyed. This API uses an asynchronous callback to return the result.

**Since:** 23

**Required permissions:** ohos.permission.NFC_TAG

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Communication.NFC.Tag

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'readerModeWithInterval' | Yes | Event type, which has a fixed value of **readerModeWithInterval**. |
| elementName | [ElementName](../../apis-ability-kit/arkts-apis/arkts-ability-elementname-i.md) | Yes | Information about the tag reading page of the application. It must contain at least **bundleName** and **abilityName**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[TagInfo](arkts-connectivity-tag-taginfo-i.md)&gt; | No | Callback to unregister. If this parameter is not set, this API unregisters the tag reading callback for the specified **type**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [3100201](../errorcode-nfc.md#3100201-tag-readwrite-error) | The tag running state is abnormal in the service. |
| [3100203](../errorcode-nfc.md#3100203-incorrect-api-call-sequence) | The off() API can be called only when the on() has been called. |

**Examples**

```TypeScript
import { tag } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { AbilityConstant, UIAbility, Want, bundleManager } from '@kit.AbilityKit';

let discTech : number[] = [tag.NFC_A, tag.NFC_B]; // Specify the technology required for foreground ability.
let elementName : bundleManager.ElementName;
let interval : number = 200;

function readerModeCb(tagInfo: tag.TagInfo) {
    if (tagInfo == null) {
      console.error('readerModeWithInterval tagInfo is invalid');
      return;
    }
    console.info("readerModeWithInterval: tag found tagInfo = ", JSON.stringify(tagInfo));
  // Other operations on taginfo
}

export default class MainAbility extends UIAbility {
    OnCreate(want : Want, launchParam : AbilityConstant.LaunchParam) {
        console.info("OnCreate");
        elementName = {
            bundleName: want.bundleName as string,
            abilityName: want.abilityName as string,
            moduleName: want.moduleName as string
        }
    }

    onForeground() {
        console.info("on start");
        try {
            tag.on('readerModeWithInterval', elementName, discTech, readerModeCb, interval);
        } catch (e) {
            console.error("tag.on error: " + (e as BusinessError).message);
        }
    }

    onBackground() {
        console.info("onBackground");
        try {
            tag.off('readerModeWithInterval', elementName, readerModeCb);
        } catch (e) {
            console.error("tag.off error: " + (e as BusinessError).message);
        }
    }

    onWindowStageDestroy() {
        console.info("onWindowStageDestroy");
        try {
            tag.off('readerModeWithInterval', elementName, readerModeCb);
        } catch (e) {
            console.error("tag.off error: " + (e as BusinessError).message);
        }
    }

  // Other functions in the ability lifecycle
}
```
