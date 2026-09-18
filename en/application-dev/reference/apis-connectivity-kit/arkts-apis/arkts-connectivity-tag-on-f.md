# on

## Modules to Import

```TypeScript
import { tag } from '@kit.ConnectivityKit';
```

## on('readerMode')

```TypeScript
function on(type: 'readerMode', elementName: ElementName, discTech: number[], callback: AsyncCallback<TagInfo>): void
```

Subscribes to the NFC tag read event to implement dispatch of the tag to a foreground application preferentially. The device enters the reader mode and disables card emulation. You can set the supported NFC tag technologies in **discTech**. The [TagInfo](arkts-connectivity-tag-taginfo-i.md) read is returned through a callback. This API must be used with [tag.off](arkts-connectivity-tag-off-f.md#offreadermode) in pairs. If the NFC reader mode is enabled by **tag.on**, [tag.off](arkts-connectivity-tag-off-f.md#offreadermode) must be called when the application page exits the foreground or is destroyed. This API uses an asynchronous callback to return the result. This API and tag.on are mutually exclusive.

**Since:** 11

**Required permissions:** ohos.permission.NFC_TAG

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'readerMode' | Yes | Event type, which has a fixed value of **readerMode**. |
| elementName | [ElementName](../../apis-ability-kit/arkts-apis/arkts-ability-elementname-i.md) | Yes | Information about the tag reading page of the application. It cannot be empty and must contain at least **bundleName** and **abilityName**. |
| discTech | number[] | Yes | NFC tag technologies supported by the foreground application. It cannot be empty. At least one NFC tag technology must be specified. Each number indicates the constant value of an NFC tag technology. The tag technologies are polled based on the specified value, which contains one or more of [NFC_A](arkts-connectivity-tag-con.md#nfc_a), [NFC_B](arkts-connectivity-tag-con.md#nfc_b), [NFC_F](arkts-connectivity-tag-con.md#nfc_f), [NFC_V](arkts-connectivity-tag-con.md#nfc_v), and [SKIP_NDEF](arkts-connectivity-tag-con.md#skip_ndef) only. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[TagInfo](arkts-connectivity-tag-taginfo-i.md)&gt; | Yes | Callback used to return the tag information read. It cannot be empty. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [3100202](../errorcode-nfc.md#3100202-application-status-error) | The element state is invalid. |
| [3100201](../errorcode-nfc.md#3100201-tag-readwrite-error) | The tag running state is abnormal in the service.<br>**Applicable version:** 12 and later |


## on('readerModeWithInterval')

```TypeScript
function on(
    type: 'readerModeWithInterval',
    elementName: ElementName,
    discTech: number[],
    callback: Callback<TagInfo>,
    interval: number
  ): void
```

Subscribes to the NFC tag read event so that the tag can be preferentially dispatched to a foreground application. You can also set the interval for detecting whether a card is present. This API uses an asynchronous callback to return the result.

- The device enters the reader mode and disables card emulation.  
- You can set the supported NFC tag technologies in **discTech** and set the interval for detecting whether a card  
is present. The callback returns [TagInfo](arkts-connectivity-tag-taginfo-i.md) read.  
- This API must be used with [tag.off](arkts-connectivity-tag-off-f.md#offreadermodewithinterval) in pairs. If the NFC reader mode is enabled by **tag.on**, [tag.off](arkts-connectivity-tag-off-f.md#offreadermodewithinterval) must be called when the application page exits the foreground or is destroyed.  
- This API and tag.on are mutually exclusive.

**Since:** 23

**Required permissions:** ohos.permission.NFC_TAG

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Communication.NFC.Tag

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'readerModeWithInterval' | Yes | Event type, which has a fixed value of **readerModeWithInterval**. |
| elementName | [ElementName](../../apis-ability-kit/arkts-apis/arkts-ability-elementname-i.md) | Yes | Information about the tag reading page of the application. It must contain at least **bundleName** and **abilityName**. |
| discTech | number[] | Yes | NFC tag technologies supported by the foreground application. At least one NFC tag technology must be specified. Each number indicates the constant value of an NFC tag technology. The tag technologies are polled based on the specified value, which contains one or more of [NFC_A](arkts-connectivity-tag-con.md#nfc_a), [NFC_B](arkts-connectivity-tag-con.md#nfc_b), [NFC_F](arkts-connectivity-tag-con.md#nfc_f), [NFC_V](arkts-connectivity-tag-con.md#nfc_v), and [SKIP_NDEF](arkts-connectivity-tag-con.md#skip_ndef) only. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[TagInfo](arkts-connectivity-tag-taginfo-i.md)&gt; | Yes | Callback used to listen for the card reader mode, which returns the tag information read. |
| interval | number | Yes | Interval for checking whether a card is present, in milliseconds. The recommended value range is 100 to 2000. If a negative value is passed, the value does not take effect. The system uses the default interval (150 ms). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [3100201](../errorcode-nfc.md#3100201-tag-readwrite-error) | The tag running state is abnormal in the service. |
| [3100202](../errorcode-nfc.md#3100202-application-status-error) | The element state is invalid. |
