# MakeCallOptions

```TypeScript
export interface MakeCallOptions
```

Provides an option for determining whether a call is a video call.

**Since:** 24

<!--Device-call-export interface MakeCallOptions--><!--Device-call-export interface MakeCallOptions-End-->

**System capability:** SystemCapability.Applications.Contacts

## Modules to Import

```TypeScript
import { call } from '@kit.TelephonyKit';
```

## isCustomAccessibility

```TypeScript
isCustomAccessibility?: boolean
```

Whether the third-party app supports custom accessibility features. Default value: false.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-MakeCallOptions-isCustomAccessibility?: boolean--><!--Device-MakeCallOptions-isCustomAccessibility?: boolean-End-->

**System capability:** SystemCapability.Applications.Contacts

## isHideDialScreen

```TypeScript
isHideDialScreen?: boolean
```

Whether to hide the dial screen. **true**: yes; **false**: no.

**Type:** boolean

**Since:** 24

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 24.

<!--Device-MakeCallOptions-isHideDialScreen?: boolean--><!--Device-MakeCallOptions-isHideDialScreen?: boolean-End-->

**System capability:** SystemCapability.Applications.Contacts
