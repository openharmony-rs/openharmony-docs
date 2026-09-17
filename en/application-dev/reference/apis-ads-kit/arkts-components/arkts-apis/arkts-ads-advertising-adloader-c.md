# AdLoader

Provides the APIs for loading ads.

**Since:** 11

**System capability:** SystemCapability.Advertising.Ads

## Modules to Import

```TypeScript
import { advertising } from '@kit.AdsKit';
```

## constructor

```TypeScript
constructor(context: common.Context)
```

Constructor.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Advertising.Ads

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [common.Context](../../apis-ability-kit/arkts-apis/arkts-ability-common-context-t.md) | Yes | Context of the ability or application. |

**Examples**

```TypeScript
For details about how to obtain the context, see [Acquisition of Various Contexts](../../../application-models/application-context-stage.md#acquisition-of-context).
```

## loadAd

```TypeScript
loadAd(adParam: AdRequestParams, adOptions: AdOptions, listener: AdLoadListener): void
```

Loads an ad.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Advertising.Ads

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| adParam | [AdRequestParams](arkts-ads-advertising-adrequestparams-i.md) | Yes | Ad request parameters. |
| adOptions | [AdOptions](arkts-ads-advertising-adoptions-i.md) | Yes | Ad configuration parameters. |
| listener | [AdLoadListener](arkts-ads-advertising-adloadlistener-i.md) | Yes | Callback listener for ad requests. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../errorcode-ads.md#401-incorrect-ads-request-parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. 3.Parameter verification failed |
| [21800001](../errorcode-ads.md#21800001-internal-system-error) | System internal error. |
| [21800003](../errorcode-ads.md#21800003-ad-loading-failure) | Failed to load the ad request. |
| [801](../errorcode-ads.md#801-ad-request-failure) | Capability not supported.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
For details about how to obtain the context, see [Acquisition of Various Contexts](../../../application-models/application-context-stage.md#acquisition-of-context).
```

## loadAdWithMultiSlots

```TypeScript
loadAdWithMultiSlots(adParams: AdRequestParams[], adOptions: AdOptions, listener: MultiSlotsAdLoadListener): void
```

Loads multiple ads.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Advertising.Ads

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| adParams | [AdRequestParams](arkts-ads-advertising-adrequestparams-i.md)[] | Yes | Ad request parameters. |
| adOptions | [AdOptions](arkts-ads-advertising-adoptions-i.md) | Yes | Ad configuration parameters. |
| listener | [MultiSlotsAdLoadListener](arkts-ads-advertising-multislotsadloadlistener-i.md) | Yes | Callback listener for ad requests. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../errorcode-ads.md#401-incorrect-ads-request-parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. 3.Parameter verification failed |
| [21800001](../errorcode-ads.md#21800001-internal-system-error) | System internal error. |
| [21800003](../errorcode-ads.md#21800003-ad-loading-failure) | Failed to load the ad request. |
| [801](../errorcode-ads.md#801-ad-request-failure) | Capability not supported.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
For details about how to obtain the context, see [Acquisition of Context](../../../application-models/application-context-stage.md#acquisition-of-context).
```
