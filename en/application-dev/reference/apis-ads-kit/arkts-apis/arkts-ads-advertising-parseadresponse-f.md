# parseAdResponse

## Modules to Import

```TypeScript
import { advertising } from '@kit.AdsKit';
```

## parseAdResponse

```TypeScript
function parseAdResponse(adResponse: string, listener: MultiSlotsAdLoadListener, 
    context: common.UIAbilityContext): void
```

Parses and processes the body of an ad response (this API is only open to some pre-installed system applications).

**Since:** 12

**System capability:** SystemCapability.Advertising.Ads

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| adResponse | string | Yes | Ad response body. |
| listener | [MultiSlotsAdLoadListener](arkts-ads-advertising-multislotsadloadlistener-i.md) | Yes | Callback listener for ad requests. |
| context | [common.UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-uiabilitycontext-t.md) | Yes | Context of the UIAbility. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../errorcode-ads.md#401-incorrect-ads-request-parameter) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../errorcode-ads.md#801-ad-request-failure) | Capability not supported. |
| [21800001](../errorcode-ads.md#21800001-internal-system-error) | System internal error. |
| [21800005](../errorcode-ads.md#21800005-ad-data-parsing-failure) | Failed to parse the ad response. |

**Examples**

```TypeScript
For details about how to obtain the context, see [Acquisition of Context](../../../application-models/application-context-stage.md#acquisition-of-context).
```
