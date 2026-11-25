# @ohos.advertising.AdsServiceExtensionAbility (ExtensionAbility for Ads)
<!--Kit: Ads Kit-->
<!--Subsystem: Advertising-->
<!--Owner: @ctssss-->
<!--Designer: @zhansf1988-->
<!--Tester: @hongmei_may-->
<!--Adviser: @RayShih-->
<!-- md-trans-meta sourceCommit=6493b14494a6c6b34e36a2da0a181b6e9e0f901d translatedAt=2026-11-23T09:10:43.781Z pushedAt=2026-11-25T02:48:27.838Z nl=1 -->


The AdsServiceExtensionAbility module provides ExtensionAbilities for the ads service. Device vendors can implement the callbacks for ads requests.


> **NOTE**
> 
> The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.


## Constraints

To ensure system security and stability and prevent AdsServiceExtensionAbility from abusing system resources, the system manages and controls its capabilities and does not support references to the following modules:
- [@ohos.multimedia.camera (Camera Management)](../apis-camera-kit/arkts-apis-camera.md)
- [@ohos.file.photoAccessHelper (Album Management Module)](../apis-media-library-kit/arkts-apis-photoAccessHelper.md)
- [@ohos.telephony.sim (SIM Card Management)](../apis-telephony-kit/js-apis-sim.md)
- [@ohos.telephony.sms (SMS Service)](../apis-telephony-kit/js-apis-sms.md)
- [@ohos.contact (Contacts)](../apis-contacts-kit/js-apis-contact.md)


## Modules to Import

```typescript
import { RespCallback } from '@kit.AdsKit';
```


## RespCallback

(respData: Map&lt;string, Array&lt;advertising.Advertisement&gt;&gt;): void

Ad request callback.

**System capability**: SystemCapability.Advertising.Ads

**Parameters**

| **Name** | **Type** | Mandatory | Description | 
| -------- | -------- | -------- | -------- |
| respData | Map&lt;string, Array&lt;advertising.[Advertisement](js-apis-advertisement.md#advertisement)&gt;&gt; | Yes | Ad request callback data, which is a mapping set that uses ad slot IDs as keys and stores the requested ad content. |

**Example**

```typescript
import { advertising, RespCallback } from '@kit.AdsKit';

function setRespCallback(respCallback: RespCallback) {
  const respData: Map<string, Array<advertising.Advertisement>> = new Map();
  // Set the returned ad data.
  // ...
  respCallback(respData);
}
```