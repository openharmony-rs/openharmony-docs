# @ohos.advertising.AdsServiceExtensionAbility (ExtensionAbility for Ads)
<!--Kit: Ads Kit-->
<!--Subsystem: Advertising-->
<!--Owner: @ctssss-->
<!--Designer: @zhansf1988-->
<!--Tester: @hongmei_may-->
<!--Adviser: @RayShih-->
<!-- md-trans-meta sourceCommit=3af2c2640a0dfa1285ceb6197505adab556ff3bb translatedAt=2026-09-02T02:13:35.507Z pushedAt=2026-09-03T02:02:25.082Z -->


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