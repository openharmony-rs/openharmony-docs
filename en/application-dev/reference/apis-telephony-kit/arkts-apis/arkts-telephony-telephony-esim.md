# @ohos.telephony.esim(eSIM Management)

The **esim** module provides basic eSIM management capabilities, including checking whether a specified card slot supports the eSIM function.

**Since:** 18

<!--Device-unnamed-declare namespace eSIM--><!--Device-unnamed-declare namespace eSIM-End-->

**System capability:** SystemCapability.Telephony.CoreService.Esim

## Modules to Import

```TypeScript
import { eSIM } from '@kit.TelephonyKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [addProfile](arkts-telephony-esim-addprofile-f.md#addprofile) | Launches the download page for the user to add a single profile. This API uses a promise to return the result. |
| [isSupported](arkts-telephony-esim-issupported-f.md#issupported) | Checks whether the specified card slot supports the eSIM function. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [cancelSession](arkts-telephony-esim-cancelsession-f-sys.md#cancelsession) | Cancels a session. This API uses a promise to return the result. |
| [deleteProfile](arkts-telephony-esim-deleteprofile-f-sys.md#deleteprofile) | Deletes a profile. This API uses a promise to return the result. |
| [downloadProfile](arkts-telephony-esim-downloadprofile-f-sys.md#downloadprofile) | Downloads a profile. This API uses a promise to return the result. |
| [getContractInfo](arkts-telephony-esim-getcontractinfo-f-sys.md#getcontractinfo) | Obtains the encrypted eSIM ID and other information required for enabling eSIM. |
| [getDefaultSmdpAddress](arkts-telephony-esim-getdefaultsmdpaddress-f-sys.md#getdefaultsmdpaddress) | Obtains the default SM-DP+ address stored in the eUICC. This API uses a promise to return the result. |
| [getDownloadableProfileMetadata](arkts-telephony-esim-getdownloadableprofilemetadata-f-sys.md#getdownloadableprofilemetadata) | Obtains the metadata of the downloadable profile. This API uses a promise to return the result. |
| [getDownloadableProfiles](arkts-telephony-esim-getdownloadableprofiles-f-sys.md#getdownloadableprofiles) | Obtains the list of downloadable profiles. This API uses a promise to return the result. |
| [getEid](arkts-telephony-esim-geteid-f-sys.md#geteid) | Obtains the equipment identifier (EID) of the eUICC hardware in a specified card slot. |
| [getEsimFreeStorage](arkts-telephony-esim-getesimfreestorage-f-sys.md#getesimfreestorage) | This API is used to obtain the remaining storage space of the eUICC hardware. This API uses a promise to return the result. |
| [getEuiccInfo](arkts-telephony-esim-geteuiccinfo-f-sys.md#geteuiccinfo) | Obtains eUICC information. This API uses a promise to return the result. |
| [getEuiccProfileInfoList](arkts-telephony-esim-geteuiccprofileinfolist-f-sys.md#geteuiccprofileinfolist) | Obtains the profile information list. This API uses a promise to return the result. |
| [getOsuStatus](arkts-telephony-esim-getosustatus-f-sys.md#getosustatus) | Obtains the OS upgrade status for the eSIM in the specified slot. This API uses a promise to return the result. |
| [getSupportedPkids](arkts-telephony-esim-getsupportedpkids-f-sys.md#getsupportedpkids) | Obtains the public key ID information supported by the phone. |
| [reserveProfilesForFactoryRestore](arkts-telephony-esim-reserveprofilesforfactoryrestore-f-sys.md#reserveprofilesforfactoryrestore) | Restores factory settings and retains profiles. This API uses a promise to return the result. |
| [resetMemory](arkts-telephony-esim-resetmemory-f-sys.md#resetmemory) | Clears all specific profiles and resets the eUICC. This API uses a promise to return the result. |
| [setDefaultSmdpAddress](arkts-telephony-esim-setdefaultsmdpaddress-f-sys.md#setdefaultsmdpaddress) | Sets or updates the default SM-DP+ address stored in the eUICC. This API uses a promise to return the result. |
| [setProfileNickname](arkts-telephony-esim-setprofilenickname-f-sys.md#setprofilenickname) | Sets a nickname for the specified profile. This API uses a promise to return the result. |
| [startOsu](arkts-telephony-esim-startosu-f-sys.md#startosu) | Upgrades the OS if the OS version of the eSIM in the specified slot is not the latest. This API uses a promise to return the result. |
| [switchToProfile](arkts-telephony-esim-switchtoprofile-f-sys.md#switchtoprofile) | Switches to the specified profile. This API uses a promise to return the result. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [AccessRule](arkts-telephony-esim-accessrule-i.md) | Establishes a single UICC access rule pursuant to the GlobalPlatform Secure Element Access Control specification. |
| [DownloadableProfile](arkts-telephony-esim-downloadableprofile-i.md) | Defines a downloadable profile. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [ContractRequestData](arkts-telephony-esim-contractrequestdata-i-sys.md) | Information required for encryption. |
| [DownloadConfiguration](arkts-telephony-esim-downloadconfiguration-i-sys.md) | Defines the download configuration. |
| [DownloadProfileResult](arkts-telephony-esim-downloadprofileresult-i-sys.md) | Defines the profile download result. |
| [EuiccInfo](arkts-telephony-esim-euiccinfo-i-sys.md) | Defines the eUICC information. |
| [EuiccProfile](arkts-telephony-esim-euiccprofile-i-sys.md) | Profile information. |
| [GetDownloadableProfileMetadataResult](arkts-telephony-esim-getdownloadableprofilemetadataresult-i-sys.md) | Obtains the metadata of the downloadable profile. |
| [GetDownloadableProfilesResult](arkts-telephony-esim-getdownloadableprofilesresult-i-sys.md) | Obtains the list of default downloadable profiles. |
| [GetEuiccProfileInfoListResult](arkts-telephony-esim-geteuiccprofileinfolistresult-i-sys.md) | Obtains the profile information list. |
| [OperatorId](arkts-telephony-esim-operatorid-i-sys.md) | Obtains information about the eUICC chip or device. |
<!--DelEnd-->

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [CancelReason](arkts-telephony-esim-cancelreason-e-sys.md) | Reason for canceling the session. |
| [OsuStatus](arkts-telephony-esim-osustatus-e-sys.md) | Defines the OS upgrade status. |
| [PolicyRules](arkts-telephony-esim-policyrules-e-sys.md) | Enumerates the profile policy rules. |
| [ProfileClass](arkts-telephony-esim-profileclass-e-sys.md) | Enumerates the profile classes. |
| [ProfileState](arkts-telephony-esim-profilestate-e-sys.md) | Enumerates the profile states. |
| [ResetOption](arkts-telephony-esim-resetoption-e-sys.md) | Defines the reset options. |
| [ResultCode](arkts-telephony-esim-resultcode-e-sys.md) | Enumerates the result codes. |
| [SolvableErrors](arkts-telephony-esim-solvableerrors-e-sys.md) | Enumerates the solvable errors. |
<!--DelEnd-->
