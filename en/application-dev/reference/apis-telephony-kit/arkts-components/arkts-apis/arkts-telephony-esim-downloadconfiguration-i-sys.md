# DownloadConfiguration (System API)

Defines the download configuration.

**Since:** 18

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { eSIM } from '@kit.TelephonyKit';
```

## forceDisableProfile

```TypeScript
forceDisableProfile: boolean
```

Whether to forcibly deactivate the current profile during profile switching.

**true**: The current profile is forcibly deactivated, and profile switching can be directly performed.

**false**: An error is returned, and profile switching can be performed only after the user authorization is obtained.

**Type:** boolean

**Since:** 18

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.

## isPprAllowed

```TypeScript
isPprAllowed: boolean
```

Whether user authorization is obtained to implement the profile policy rule. The value **true** indicates that user authorization is obtained, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 18

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.

## switchAfterDownload

```TypeScript
switchAfterDownload: boolean
```

Whether to enable the profile after successful download. The value **true** means to enable the default profile, and the value **false** means the opposite.

**Type:** boolean

**Since:** 18

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.
