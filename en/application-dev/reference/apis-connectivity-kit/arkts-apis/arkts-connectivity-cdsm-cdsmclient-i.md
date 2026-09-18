# CdsmClient

Defines a CDSM client class, which provides APIs for obtaining the CDSM information of a remote device.

- Before using the methods of this class, call [cdsm.createCdsmClient](arkts-connectivity-cdsm-createcdsmclient-f.md) to construct an  
instance of this class.

This class is applicable to scenarios where you need to obtain the member devices and connection status changes of a group of NearLink devices (CDSM) and perform service coordination accordingly. For example, after a phone is paired with earphones, the phone can use the CDSM to query the left and right earphones and detect their connection status changes.

An app only needs to create one [CdsmClient](arkts-connectivity-cdsm-cdsmclient-i.md) instance for a remote device. Repeated creation will increase unnecessary resource overhead.

**Since:** 26.0.0

**System capability:** SystemCapability.Communication.NearLink.Base

## Modules to Import

```TypeScript
import { cdsm } from '@kit.ConnectivityKit';
```

## getCdsmInfo

```TypeScript
getCdsmInfo(): CdsmInfo
```

Queries information about the coordinated devices set of a remote device.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESS_NEARLINK

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

**Return value:**

| Type | Description |
| --- | --- |
| [CdsmInfo](arkts-connectivity-cdsm-cdsminfo-i.md) | Information about the coordinated devices set of a remote device. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [36100003](../errorcode-nearlink-service.md#36100003-nearlink-disabled) | NearLink disabled. |
| [36100099](../errorcode-nearlink-service.md#36100099-operation-failed) | Operation failed. |

## offCdsmInfoChange

```TypeScript
offCdsmInfoChange(callback?: Callback<CdsmInfo>): void
```

Unsubscribes from the CDSM information change event. This API uses an asynchronous callback to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[CdsmInfo](arkts-connectivity-cdsm-cdsminfo-i.md)&gt; | No | Callback used to return the CDSM information.<br>If this parameter is specified, the current callback is unregistered. If this parameter is not specified, all callbacks used to listen for CDSM information change events are unregistered. |

## onCdsmInfoChange

```TypeScript
onCdsmInfoChange(callback: Callback<CdsmInfo>): void
```

Subscribes to the CDSM information change event. This API uses an asynchronous callback to return the result.

The app must have the **ohos.permission.ACCESS_NEARLINK** permission to receive this event.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[CdsmInfo](arkts-connectivity-cdsm-cdsminfo-i.md)&gt; | Yes | Callback used to return the CDSM information. |
