# registerForegroundDispatch

## Modules to Import

```TypeScript
import { tag } from '@kit.ConnectivityKit';
```

## registerForegroundDispatch

```TypeScript
function registerForegroundDispatch(elementName: ElementName, discTech: number[], callback: AsyncCallback<TagInfo>): void
```

Registers a listener for the NFC tag read event so that the tag can be preferentially dispatched to a foreground application. You can set the supported NFC tag technologies in **discTech**. The [TagInfo](arkts-connectivity-tag-taginfo-i.md) read is returned through a callback. This API can be called only by an application running in the foreground. It must be used with [tag.unregisterForegroundDispatch](arkts-connectivity-tag-unregisterforegrounddispatch-f.md) in pairs. The registered callback must be unregistered before the tag reading page exits the foreground or is destroyed. This API uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** ohos.permission.NFC_TAG

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| elementName | [ElementName](../../apis-ability-kit/arkts-apis/arkts-ability-elementname-i.md) | Yes | Information about the tag reading page of the application. It cannot be empty and must contain at least **bundleName** and **abilityName**. |
| discTech | number[] | Yes | NFC tag technologies supported by the foreground application. It cannot be empty. At least one NFC tag technology must be specified. Each number indicates the constant value of an NFC tag technology. The tag technologies are polled based on the specified value, which contains one or more of [NFC_A](arkts-connectivity-tag-con.md#nfc_a), [NFC_B](arkts-connectivity-tag-con.md#nfc_b), [NFC_F](arkts-connectivity-tag-con.md#nfc_f), and [NFC_V](arkts-connectivity-tag-con.md#nfc_v), only. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[TagInfo](arkts-connectivity-tag-taginfo-i.md)&gt; | Yes | Callback used to return the tag information read. It cannot be empty. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [3100201](../errorcode-nfc.md#3100201-tag-readwrite-error) | The tag running state is abnormal in the service.<br>**Applicable version:** 12 and later |
| [3100202](../errorcode-nfc.md#3100202-application-status-error) | The element state is invalid.<br>**Applicable version:** 12 and later |
