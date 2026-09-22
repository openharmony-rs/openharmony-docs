# @ohos.deviceInfo(Device Information)

This module provides APIs for querying terminal device information, including the device type, brand, model, system version, security patch tag, and unique device ID. It is applicable to scenarios such as device adaptation, version compatibility check, device identification, and statistical analysis, helping you quickly obtain device information for application adaptation and optimization. You cannot configure this information.

> **NOTE:** 
> 
> The initial APIs of this module are supported since API version 6. New APIs added in later versions are marked with superscripts to indicate their initial version.
> The return values **hardwareProfile**, **incrementalVersion**, **buildType**, **buildUser**, **buildHost**, **buildTime**, and **buildRootHash** are **default**. These parameters will be configured in the official commercial version of the device.
> The APIs of this module return information about device constants. It is recommended that your app call the APIs only once.

**Since:** 6

**System capability:** SystemCapability.Startup.SystemInfo

## Modules to Import

```TypeScript
import { deviceInfo } from '@kit.BasicServicesKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [apiAvailable](arkts-basicservices-deviceinfo-apiavailable-f.md) | Checks whether a specified API version is available on the current device. This API provides compatibility check across different OpenHarmony/Distribution OS versions. A suitable version check method is automatically selected based on the input format and supported API versions. |

### Enums

| Name | Description |
| --- | --- |
| [DeviceTypes](arkts-basicservices-deviceinfo-devicetypes-e.md) | Enumerates device types, which can be used to verify the return value of **deviceType**. |
| [PerformanceClassLevel](arkts-basicservices-deviceinfo-performanceclasslevel-e.md) | Enumerates the device capability levels. |

### Constants

| Name | Description |
| --- | --- |
| [abiList](arkts-basicservices-deviceinfo-con.md#abilist) | Application binary interface (Abi) list. |
| [bootCount](arkts-basicservices-deviceinfo-con.md#bootcount) | Number of device reboots. If the number cannot be obtained, **-1** is returned. |
| [bootloaderVersion](arkts-basicservices-deviceinfo-con.md#bootloaderversion) | Bootloader version, which identifies the version of the device bootloader. |
| [brand](arkts-basicservices-deviceinfo-con.md#brand) | Device brand. |
| [buildHost](arkts-basicservices-deviceinfo-con.md#buildhost) | Build host. |
| [buildRootHash](arkts-basicservices-deviceinfo-con.md#buildroothash) | Build root hash. |
| [buildTime](arkts-basicservices-deviceinfo-con.md#buildtime) | Build time. |
| [buildType](arkts-basicservices-deviceinfo-con.md#buildtype) | Build type. |
| [buildUser](arkts-basicservices-deviceinfo-con.md#builduser) | Build user. |
| [buildVersion](arkts-basicservices-deviceinfo-con.md#buildversion) | Build version number, which identifies the build version. The value is the fourth digit in **osFullName**. You are advised to use **deviceInfo.buildVersion** instead of parsing **osFullName** to obtain the value, facilitating efficiency improvement. |
| [chipType](arkts-basicservices-deviceinfo-con.md#chiptype) | CPU chip model of the device. |
| [deviceColor](arkts-basicservices-deviceinfo-con.md#devicecolor) | Device color. If the value cannot be obtained, an empty string is returned. |
| [deviceType](arkts-basicservices-deviceinfo-con.md#devicetype) | Device type. For details, see [deviceTypes](../../../quick-start/module-configuration-file.md#devicetypes). |
| [diskSN](arkts-basicservices-deviceinfo-con.md#disksn) | Serial number of the disk. This API will start a temporary process during execution. When the system load is high, blocking may occur. To ensure the response of the main thread of your application, you are advised not to call this API in the main thread. This value varies depending on the device and is fixed. To improve performance, you can store this information on a local device after obtaining it for the first time. |
| [displayVersion](arkts-basicservices-deviceinfo-con.md#displayversion) | Product version.&lt;!--RP14--&gt;&lt;!--RP14End--&gt; |
| [distributionOSApiName](arkts-basicservices-deviceinfo-con.md#distributionosapiname) | Distribution OS API name.<!--Del--> It is defined by the issuer.<!--DelEnd-->.&lt;!--RP16-- |
| [distributionOSApiVersion](arkts-basicservices-deviceinfo-con.md#distributionosapiversion) | Distribution OS API version.<!--Del--> It is defined by the issuer.<!--DelEnd-->.&lt;!--RP15--&gt;&lt;!--RP15End--&gt; |
| [distributionOSName](arkts-basicservices-deviceinfo-con.md#distributionosname) | Distribution OS name<!--Del-->, which is defined by the issuer<!--DelEnd-->. |
| [distributionOSReleaseType](arkts-basicservices-deviceinfo-con.md#distributionosreleasetype) | Distribution OS release type<!--Del-->, which is defined by the issuer<!--DelEnd-->. |
| [distributionOSVersion](arkts-basicservices-deviceinfo-con.md#distributionosversion) | Distribution OS version<!--Del-->, which is defined by the issuer<!--DelEnd-->.&lt;!--RP11--&gt;&lt;!--RP11End--&gt; |
| [featureVersion](arkts-basicservices-deviceinfo-con.md#featureversion) | Feature version number, which identifies the planned new feature version. The value is the third digit in **osFullName**. You are advised to use **deviceInfo.featureVersion** instead of parsing **osFullName** to obtain the value, facilitating efficiency improvement. |
| [firstApiVersion](arkts-basicservices-deviceinfo-con.md#firstapiversion) | First API version. |
| [hardwareModel](arkts-basicservices-deviceinfo-con.md#hardwaremodel) | Hardware model. |
| [hardwareProfile](arkts-basicservices-deviceinfo-con.md#hardwareprofile) | Hardware profile. |
| [incrementalVersion](arkts-basicservices-deviceinfo-con.md#incrementalversion) | Incremental version, which is the Ohos version number generated during compilation. |
| [majorVersion](arkts-basicservices-deviceinfo-con.md#majorversion) | Major version number, which increments with the main version. The value is the first digit in **osFullName**. You are advised to use **deviceInfo.majorVersion** instead of parsing **osFullName** to obtain the value, facilitating efficiency improvement. |
| [manufacture](arkts-basicservices-deviceinfo-con.md#manufacture) | Device manufacturer. |
| [marketName](arkts-basicservices-deviceinfo-con.md#marketname) | Marketing name. |
| [ODID](arkts-basicservices-deviceinfo-con.md#odid) | Open device identifier (ODID). |
| [osFullName](arkts-basicservices-deviceinfo-con.md#osfullname) | System version. The version number is in the format of **&lt;!--RP12--&gt;OpenHarmony-x.x.x.x**, where **x** is a placeholder for digits. &lt;!--RP12End--&gt;To obtain the value of a segment in the version number, you are advised to use **majorVersion**, **seniorVersion**, **featureVersion**, or **buildVersion**, which can improve efficiency. Parsing **osFullName** is not recommended. |
| [osReleaseType](arkts-basicservices-deviceinfo-con.md#osreleasetype) | OS release type. The options are as follows: |
| [performanceClass](arkts-basicservices-deviceinfo-con.md#performanceclass) | Device capability level, which is evaluated based on factors such as CPU, memory, storage read/write performance, and screen resolution. |
| [productModel](arkts-basicservices-deviceinfo-con.md#productmodel) | Product model. |
| [productModelAlias](arkts-basicservices-deviceinfo-con.md#productmodelalias) | Product model alias. |
| [productSeries](arkts-basicservices-deviceinfo-con.md#productseries) | Product series. |
| [sdkApiVersion](arkts-basicservices-deviceinfo-con.md#sdkapiversion) | SDK API version. |
| [sdkMinorApiVersion](arkts-basicservices-deviceinfo-con.md#sdkminorapiversion) | Starting from API version 26.0.0, the minor version is introduced as part of semantic versioning. It is the middle field in the semantic version and is an integer. The complete API version is represented by sdkApiVersion.sdkMinorApiVersion.sdkPatchApiVersion. |
| [sdkPatchApiVersion](arkts-basicservices-deviceinfo-con.md#sdkpatchapiversion) | Starting from API version 26.0.0, the patch version is introduced as part of semantic versioning. It is the third field in the semantic version and is an integer. The complete API version is represented by sdkApiVersion.sdkMinorApiVersion.sdkPatchApiVersion. |
| [securityPatchTag](arkts-basicservices-deviceinfo-con.md#securitypatchtag) | Security patch tag. |
| [seniorVersion](arkts-basicservices-deviceinfo-con.md#seniorversion) | Senior version number, which increments with architecture and feature updates. The value is the second digit in **osFullName**. You are advised to use **deviceInfo.seniorVersion** instead of parsing **osFullName** to obtain the value, facilitating efficiency improvement. |
| [serial](arkts-basicservices-deviceinfo-con.md#serial) | Serial number of the device. This API will start a temporary process during execution. When the system load is high, blocking may occur. To ensure the response of the main thread of your application, you are advised not to call this API in the main thread. This value varies depending on the device and is fixed. To improve performance, you can store this information on a local device after obtaining it for the first time. |
| [softwareModel](arkts-basicservices-deviceinfo-con.md#softwaremodel) | Software model. |
| [udid](arkts-basicservices-deviceinfo-con.md#udid) | UDID of the device. This API will start a temporary process during execution. When the system load is high, blocking may occur. To ensure the response of the main thread of your application, you are advised not to call this API in the main thread. This value varies depending on the device and is fixed. To improve performance, you can store this information on a local device after obtaining it for the first time. |
| [versionId](arkts-basicservices-deviceinfo-con.md#versionid) | Version ID, which is a concatenation of **deviceType**, **manufacture**, **brand**, **productSeries**, **osFullName**, **productModel**, **softwareModel**, **sdkApiVersion**, **incrementalVersion**, and **buildType**. To obtain a specific field value, you are advised to use the corresponding field directly (such as **deviceType** and **manufacture**) instead of parsing **versionId**, facilitating efficiency improvement. |
