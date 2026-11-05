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
| [addProfile](arkts-telephony-esim-addprofile-f.md#addprofile-1) | When a user needs to activate a new eSIM (for example, registering a new SIM card or changing a SIM card), this interface is invoked to guide the process of downloading and adding a configuration file. Use Promise asynchronous callbacks. |
| [isSupported](arkts-telephony-esim-issupported-f.md#issupported-1) | Checks whether the specified card slot supports the eSIM function. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [cancelSession](arkts-telephony-esim-cancelsession-f-sys.md#cancelsession-1) | canceling an ongoing eSIM service session (for example, a configuration file download session) with the SM-DP+ server. Transfer the service ID and cancellation reason to terminate the ongoing session operation. Use Promise asynchronous callbacks. |
| [deleteProfile](arkts-telephony-esim-deleteprofile-f-sys.md#deleteprofile-1) | Delete configuration file. Use Promise asynchronous callback. |
| [downloadProfile](arkts-telephony-esim-downloadprofile-f-sys.md#downloadprofile-1) | Downloads a profile. This API uses a promise to return the result. |
| [getContractInfo](arkts-telephony-esim-getcontractinfo-f-sys.md#getcontractinfo-1) | Obtain the encrypted EID required for enabling the eSIM. |
| [getDefaultSmdpAddress](arkts-telephony-esim-getdefaultsmdpaddress-f-sys.md#getdefaultsmdpaddress-1) | Obtains the default SM-DP+ address stored in the eUICC. This API uses a promise to return the result. |
| [getDownloadableProfileMetadata](arkts-telephony-esim-getdownloadableprofilemetadata-f-sys.md#getdownloadableprofilemetadata-1) | Obtains the metadata of the downloadable profile. This API uses a promise to return the result. |
| [getDownloadableProfiles](arkts-telephony-esim-getdownloadableprofiles-f-sys.md#getdownloadableprofiles-1) | Obtains the list of downloadable profiles. This API uses a promise to return the result. |
| [getEid](arkts-telephony-esim-geteid-f-sys.md#geteid-1) | Obtains the equipment identifier (EID) of the eUICC hardware in a specified card slot. |
| [getEsimFreeStorage](arkts-telephony-esim-getesimfreestorage-f-sys.md#getesimfreestorage-1) | obtain remaining storage space of the eUICC hardware. Use Promise asynchronous callbacks. |
| [getEuiccInfo](arkts-telephony-esim-geteuiccinfo-f-sys.md#geteuiccinfo-1) | Obtains eUICC information. This API uses a promise to return the result. |
| [getEuiccProfileInfoList](arkts-telephony-esim-geteuiccprofileinfolist-f-sys.md#geteuiccprofileinfolist-1) | Obtains the profile information list. This API uses a promise to return the result. |
| [getOsuStatus](arkts-telephony-esim-getosustatus-f-sys.md#getosustatus-1) | Obtains the OS upgrade status of a specified card slot. Using Promise Asynchronous Callbacks. |
| [getSupportedPkids](arkts-telephony-esim-getsupportedpkids-f-sys.md#getsupportedpkids-1) | This interface is used to obtain the public key ID information supported by the mobile phone for security authentication in the eSIM activation process. Before calling the getContractInfo interface for encryption authentication, you need to call this interface to obtain the available public key ID. |
| [reserveProfilesForFactoryRestore](arkts-telephony-esim-reserveprofilesforfactoryrestore-f-sys.md#reserveprofilesforfactoryrestore-1) | Restore factory settings and retain the configuration file. Use Promise asynchronous callbacks. |
| [resetMemory](arkts-telephony-esim-resetmemory-f-sys.md#resetmemory-1) | Clear all specific profiles and reset the eUICC. Different from reserveProfilesForFactoryRestore, this interface clears configuration files. To restore factory settings and retain existing configuration files, use reserveProfilesForFactoryRestore. Use Promise asynchronous callbacks. |
| [setDefaultSmdpAddress](arkts-telephony-esim-setdefaultsmdpaddress-f-sys.md#setdefaultsmdpaddress-1) | Sets or updates the default SM-DP+ address stored in the eUICC. This API uses a promise to return the result. |
| [setProfileNickname](arkts-telephony-esim-setprofilenickname-f-sys.md#setprofilenickname-1) | Sets a nickname for the specified profile. This API uses a promise to return the result. |
| [startOsu](arkts-telephony-esim-startosu-f-sys.md#startosu-1) | If the operating system of the specified card slot is not the latest, perform the operating system upgrade. After the upgrade, you can use the getOsuStatus interface to query the upgrade status. (for example, the upgrade is in progress, the upgrade is successful, or the upgrade fails.) Use Promise asynchronous callback. |
| [switchToProfile](arkts-telephony-esim-switchtoprofile-f-sys.md#switchtoprofile-1) | Switches to the specified profile. This API uses a promise to return the result. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [AccessRule](arkts-telephony-esim-accessrule-i.md) | Defines access rules. |
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
| [OperatorId](arkts-telephony-esim-operatorid-i-sys.md) | Carrier ID. |
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
