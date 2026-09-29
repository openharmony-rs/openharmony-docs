# VerifyPinEvent

```TypeScript
declare interface VerifyPinEvent
```

Defines the callback triggered to notify the user of PIN verification.

**Since:** 22

<!--Device-unnamed-declare interface VerifyPinEvent--><!--Device-unnamed-declare interface VerifyPinEvent-End-->

**System capability:** SystemCapability.Web.Webview.Core

## handler

```TypeScript
handler: VerifyPinHandler
```

User operation.

**Type:** [VerifyPinHandler](arkts-arkweb-web-comp-verifypinhandler-c.md)

**Since:** 22

<!--Device-VerifyPinEvent-handler: VerifyPinHandler--><!--Device-VerifyPinEvent-handler: VerifyPinHandler-End-->

**System capability:** SystemCapability.Web.Webview.Core

## identity

```TypeScript
identity: string
```

Certificate credential ID used for verification.

**Type:** string

**Since:** 22

<!--Device-VerifyPinEvent-identity: string--><!--Device-VerifyPinEvent-identity: string-End-->

**System capability:** SystemCapability.Web.Webview.Core
