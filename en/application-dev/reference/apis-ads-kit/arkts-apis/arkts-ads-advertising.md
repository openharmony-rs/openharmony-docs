# @ohos.advertising(Ads Service Framework)

The advertising module provides APIs for requesting and displaying ads.

> **NOTE:** 
> The initial APIs of this module are supported since API version 11.
> Newly added APIs will be marked with a superscript to indicate their earliest API version.

**Since:** 11

**System capability:** SystemCapability.Advertising.Ads

## Modules to Import

```TypeScript
import { advertising } from '@kit.AdsKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [deleteWebAdInterface](arkts-ads-advertising-deletewebadinterface-f.md) | Deletes the ad JavaScript object injected through **registerWebAdInterface** (this API is only open to some pre-installed system applications). |
| [getAdRequestBody](arkts-ads-advertising-getadrequestbody-f.md) | Obtains the body of an ad request. This API uses a promise to return the result (this API is only open to some pre-installed system applications). |
| [parseAdResponse](arkts-ads-advertising-parseadresponse-f.md) | Parses and processes the body of an ad response (this API is only open to some pre-installed system applications). |
| [registerWebAdInterface](arkts-ads-advertising-registerwebadinterface-f.md) | Injects an ad JavaScript object to the **Web** component (this API is only open to some pre-installed system applications). |
| [registerWebAdInterface](arkts-ads-advertising-registerwebadinterface-f.md) | Injects an ad JavaScript object to the **Web** component (this API is only open to some pre-installed system applications). |
| [showAd](arkts-ads-advertising-showad-f.md) | Shows a full-screen ad. |

### Classes

| Name | Description |
| --- | --- |
| [AdLoader](arkts-ads-advertising-adloader-c.md) | Provides the APIs for loading ads. |

### Interfaces

| Name | Description |
| --- | --- |
| [AdDisplayOptions](arkts-ads-advertising-addisplayoptions-i.md) | Defines the ad display parameters. |
| [AdInteractionListener](arkts-ads-advertising-adinteractionlistener-i.md) | Defines the ad status change callback. |
| [AdLoadListener](arkts-ads-advertising-adloadlistener-i.md) | Enumerates the callbacks used for the request for loading an ad. |
| [AdOptions](arkts-ads-advertising-adoptions-i.md) | Defines the ad configuration. |
| [AdRequestParams](arkts-ads-advertising-adrequestparams-i.md) | Defines the ad request parameters. |
| [MultiSlotsAdLoadListener](arkts-ads-advertising-multislotsadloadlistener-i.md) | Enumerates the callbacks used for the request for loading multiple ads. |

### Types

| Name | Description |
| --- | --- |
| [Advertisement](arkts-ads-advertising-advertisement-t.md) | Defines the requested ad content. |
