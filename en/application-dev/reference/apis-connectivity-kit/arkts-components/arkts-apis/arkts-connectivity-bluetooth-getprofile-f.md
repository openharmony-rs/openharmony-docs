# getProfile

## Modules to Import

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## getProfile

```TypeScript
function getProfile(profileId: ProfileId): A2dpSourceProfile | HandsFreeAudioGatewayProfile
```

Obtains the instance of profile.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getProfileInstance](arkts-connectivity-bluetoothmanager-getprofileinstance-f.md)

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| profileId | [ProfileId](arkts-connectivity-bluetooth-profileid-e.md) | Yes | The profile id.. |

**Return value:**

| Type | Description |
| --- | --- |
| [A2dpSourceProfile](arkts-connectivity-bluetooth-a2dpsourceprofile-i.md) &#124; [HandsFreeAudioGatewayProfile](arkts-connectivity-bluetooth-handsfreeaudiogatewayprofile-i.md) | Returns instance of profile. |

**Examples**

```TypeScript
let a2dpSrc : bluetooth.A2dpSourceProfile = bluetooth.getProfile(bluetooth.ProfileId.PROFILE_A2DP_SOURCE) as bluetooth.A2dpSourceProfile;
```
