# showAd

## Modules to Import

```TypeScript
import { advertising } from '@kit.AdsKit';
```

## showAd

```TypeScript
function showAd(ad: Advertisement, options: AdDisplayOptions, context?: common.UIAbilityContext): void
```

Shows a full-screen ad.

> **NOTE:** 
> 
> 1. To ensure that ads can be displayed correctly, this API must be used together with the ad request API.
> 
> 2. This API only supports displaying rewarded ads and interstitial ads.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Advertising.Ads

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ad | [Advertisement](arkts-ads-advertising-advertisement-t.md) | Yes | Ad object. |
| options | [AdDisplayOptions](arkts-ads-advertising-addisplayoptions-i.md) | Yes | Ad display parameters. |
| context | [common.UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-uiabilitycontext-t.md) | No | Context of the UIAbility. If this parameter is not set, the value is obtained from @ohos.app.ability.common.<br>**Since:** 12 |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. |
| [21800001](../errorcode-ads.md#21800001-internal-system-error) | System internal error. |
| [21800004](../errorcode-ads.md#21800004-ad-display-failure) | Failed to display the ad. |

**Examples**

For details about how to obtain the context, see [Acquisition of Context](../../../application-models/application-context-stage.md#acquisition-of-context).

```TypeScript
import { common } from '@kit.AbilityKit';
import { advertising } from '@kit.AdsKit';

function showAd(ad: advertising.Advertisement, context?: common.UIAbilityContext): void {
  // Ad display parameters. You can set the parameters based on the project requirements.
  const adDisplayOptions: advertising.AdDisplayOptions = {};
  // Show the ad.
  advertising.showAd(ad, adDisplayOptions, context);
}
```
