# @ohos.deviceInfo (Device Information)
<!--Kit: Basic Services Kit-->
<!--Subsystem: Startup-->
<!--Owner: @chenjinxiang3-->
<!--Designer: @chenjinxiang3-->
<!--Tester: @liuhaonan2-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=4bd4d7af2f792068967875825ce666c8757dd996 translatedAt=2026-11-04T08:53:40.694Z pushedAt=2026-11-04T08:59:23.309Z nl=1 -->

This module provides APIs for querying terminal device information, including the device type, brand, model, system version, security patch tag, and unique device ID. It is applicable to scenarios such as device adaptation, version compatibility check, device identification, and statistical analysis, helping you quickly obtain device information for application adaptation and optimization. You cannot configure this information.

> **NOTE**
>
> The initial APIs of this module are supported since API version 6. New APIs added in later versions are marked with superscripts to indicate their initial version.
> The return values **hardwareProfile**, **incrementalVersion**, **buildType**, **buildUser**, **buildHost**, **buildTime**, and **buildRootHash** are **default**. These parameters will be configured in the official commercial version of the device.
> The APIs of this module return information about device constants. It is recommended that your app call the APIs only once.

## Modules to Import

```ts
import { deviceInfo } from '@kit.BasicServicesKit';
```

## Constants
> **NOTE**
> Unless otherwise specified, the maximum data length is 96 bytes.

**System capability**: SystemCapability.Startup.SystemInfo

**Required permissions**: The items in the table below require different system capabilities.

| Name| Type| Read-Only| Description|
| -------- | -------- | -------- | -------- |
| deviceType | string | Yes | Device type. For details, see [deviceTypes tag](../../quick-start/module-configuration-file.md#devicetypes).<br>**Atomic service API**: This API can be used in atomic services since API version 11.<br>Example: wearable |
| manufacture | string | Yes | Manufacturer name. |
| brand | string | Yes | Device brand name.<br>**Atomic service API**: This API can be used in atomic services since API version 11. |
| marketName | string | Yes | External product series.<br>Example: <!--RP2-->Mate XX<!--RP2End--> |
| productSeries | string | Yes | Product series.<br>Example: <!--RP3-->TAS<!--RP3End--> |
| productModel | string | Yes | Certified model.<br>**Atomic service API**: This API can be used in atomic services since API version 11.<br>Example: <!--RP4-->TAS-AL00<!--RP4End--> |
| productModelAlias<sup>14+</sup> | string | Yes | Alias of the certified model.<br>**Atomic service API**: This API can be used in atomic services since API version 14.<br>Example: TAS-AL00 |
| softwareModel | string | Yes | Internal software submodel.<br>Example: <!--RP5-->TAS-AL00<!--RP5End--> |
| hardwareModel | string | Yes | Hardware version number.<br>Example: <!--RP6-->TASA00CVN1<!--RP6End--> |
| hardwareProfile<sup>(deprecated) </sup> | string | Yes | Hardware profile.<br>**NOTE**<br>This API is supported since API version 6 and deprecated since API version 9. You are advised to use [SystemCapability Usage Guide](../syscap.md) instead.<br>Example: default |
| serial | string | Yes | Device serial number (SN). This API will start a temporary process during execution. When system load is high, it may cause a blocking risk. To ensure main thread responsiveness, it is recommended to avoid calling this API on the main thread. The device information varies by device and is fixed, so it can be cached after first retrieval and stored locally to avoid repeating each use, to improve performance.<br>**NOTE**<br>It can be used as the unique device identifier.<br>**Requires permission**: [ohos.permission.sec.ACCESS_UDID](../../security/AccessToken/permissions-for-enterprise-apps.md#ohospermissionsecaccess_udid) <br>Example: The serial number varies by device. |
| bootloaderVersion | string | Yes | Bootloader version number, used to identify the version information of the device bootloader.<br>Example: bootloader |
| abiList | string | Yes | Application binary interface (ABI).<br>Example: arm64-v8a |
| securityPatchTag | string | Yes | Security patch level.<br>Example: 2021/01/01 |
| displayVersion | string | Yes | Product version. <!--RP14--><!--RP14End--><br>Example: <!--RP8-->XXX X.X.X.X<!--RP8End--> |
| incrementalVersion | string | Yes | Incremental version number, which is the version number of OHOS generated at build time. <br>Example: 6.1.1.120 |
| osReleaseType | string | Yes | Release type of the system. The value can be:<br>-&nbsp;Canary: an early preview version released to specific developers, with no commitment to API stability.<br>-&nbsp;Beta: a beta version publicly released to developers, with no commitment to API stability.<br>-&nbsp;Release: a formal version publicly released to developers, with commitment to API stability.<br>Example: <!--RP9-->Canary/Beta/Release<!--RP9End--> |
| osFullName | string | Yes | OS full name. The version number is in the format of <!--RP12-->OpenHarmony-x.x.x.x where x is a placeholder for digits. <!--RP12End-->To obtain the value of a segment in the version number, it is recommended to directly use the **majorVersion**, **seniorVersion**, **featureVersion**, or **buildVersion** field, which can improve efficiency. Parsing **osFullName** is not recommended.<br>**Atomic service API**: This API can be used in atomic services since API version 11.<br>Example: <!--RP10-->OpenHarmony-5.0.0.1<!--RP10End--> |
| majorVersion | number | Yes | Major version number, which increases with major version updates. Its value is the first digit in **osFullName**. It is recommended to directly use **deviceInfo.majorVersion** to obtain it, which can improve efficiency. It is not recommended for developers to independently parse **osFullName** to obtain it.<br>Example: 5 |
| seniorVersion | number | Yes | Senior version number, which increases with partial architecture and major feature updates. Its value is the second digit in **osFullName**. It is recommended to directly use **deviceInfo.seniorVersion** to obtain it, which can improve efficiency. It is not recommended for developers to independently parse **osFullName** to obtain it.<br>Example: 0 |
| featureVersion | number | Yes | Feature version number, which identifies the planned new feature version. Its value is the third digit in **osFullName**. It is recommended to directly use **deviceInfo.featureVersion** to obtain it, which can improve efficiency. It is not recommended for developers to independently parse **osFullName** to obtain it.<br>Example: 0 |
| buildVersion | number | Yes | Build version number, which identifies the version number of the build. Its value is the fourth digit in **osFullName**. It is recommended to directly use **deviceInfo.buildVersion** to obtain it, which can improve efficiency. It is not recommended for developers to independently parse **osFullName** to obtain it.<br>Example: 1 |
| sdkApiVersion | number | Yes | System software API version.<br>**Atomic service API**: This API can be used in atomic services since API version 14.<br>Example: 12 |
| sdkMinorApiVersion | number | Yes | System software minor API version. Since API version 26.0.0, the system API version format is sdkApiVersion.sdkMinorApiVersion.sdkPatchApiVersion.<br>**Model restriction**: This API is only used under the Stage model.<br>**Since version**: 26.0.0<br>**Atomic service API**: This API can be used in atomic services since API version 26.0.0.<br>Example: 0 |
| sdkPatchApiVersion | number | Yes | System software patch API version. Since API version 26.0.0, the system API version format is sdkApiVersion.sdkMinorApiVersion.sdkPatchApiVersion.<br>**Model restriction**: This API is only used under the Stage model.<br>**Since version**: 26.0.0<br>**Atomic service API**: This API can be used in atomic services since API version 26.0.0.<br>Example: 0 |
| firstApiVersion | number | Yes | System software API version of the first version.<br>Example: 3 |
| versionId | string | Yes | Version ID. It consists of the following fields: **deviceType**, **manufacture**, **brand**, **productSeries**, **osFullName**, **productModel**, **softwareModel**, **sdkApiVersion**, **incrementalVersion**, and **buildType**. To obtain the value of a specific field, it is recommended to directly use the corresponding field (such as **deviceType** or **manufacture**), which can improve efficiency. Parsing **versionId** is not recommended. |
| buildType | string | Yes | Build type.<br>Example: default |
| buildUser | string | Yes | Build user.<br>Example: default |
| buildHost | string | Yes | Build host.<br>Example: default |
| buildTime | string | Yes | Build time.<br>Example: default |
| buildRootHash | string | Yes | Build version hash.<br>Example: default |
| udid<sup>7+</sup> | string | Yes | Device UDID. This API will start a temporary process during execution. When system load is high, it may cause a blocking risk. To ensure main thread responsiveness, it is recommended to avoid calling this API on the main thread. The device information varies by device and is fixed, so it can be cached after first retrieval and stored locally to avoid repeating each use, to improve performance.<br>**NOTE**<br>The data length is 65 bytes (including the terminator). It can be used as the unique device identifier.<br>**Requires permission**: [ohos.permission.sec.ACCESS_UDID](../../security/AccessToken/permissions-for-enterprise-apps.md#ohospermissionsecaccess_udid)<br>Example: 9D6AABD147XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXE5536412  |
| distributionOSName<sup>10+</sup> | string | Yes | Distribution system name<!--Del-->, defined by the distributor<!--DelEnd-->.<br>Example: OpenHarmony |
| distributionOSVersion<sup>10+</sup> | string | Yes | Distribution system version number<!--Del-->, defined by the distributor<!--DelEnd-->. <!--RP11--><!--RP11End--><br>Example: 5.0.0  |
| distributionOSApiVersion<sup>10+</sup> | number| Yes | Distribution system API version<!--Del-->, defined by the distributor<!--DelEnd-->. <!--RP15--><!--RP15End--><br>Example: 50001 |
| distributionOSApiName<sup>13+</sup> | string | Yes | Distribution system API version name<!--Del-->, defined by the distributor<!--DelEnd-->. <!--RP16--><br>**NOTE**<br>It is not recommended to use it for version number judgment.<br>Example: 5.0.1<!--RP16End--> |
| distributionOSReleaseType<sup>10+</sup> | string | Yes | Distribution system type<!--Del-->, defined by the distributor<!--DelEnd-->.<br>Example: Release |
| ODID<sup>12+</sup> | string | Yes | ODID (Open Developer Identifier), an anonymous device identifier for developers.<br>**The ODID value is regenerated in the following scenarios**:<br>The phone is restored to factory settings.<br>All applications of the same developer (with the same developerId) on the same device are uninstalled and then reinstalled.<br>**ODID generation rules**:<br>It is generated based on the groupId parsed from the developerId in the signature information. The developerId rule is groupId.developerId. If there is no groupId, the entire developerId is used as the groupId.<br>Applications of the same developer (with the same developerId) running on the same device have the same ODID.<br>Applications of different developers (with different developerIds) on the same device have different ODIDs.<br>Applications of the same developer (with the same developerId) on different devices have different ODIDs.<br>Applications of different developers (with different developerIds) on different devices have different ODIDs.<br>**NOTE**<br>The data length is 37 bytes (including the terminator).<br>Example: 1234a567-XXXX-XXXX-XXXX-XXXXXXXXXXXX |
| diskSN<sup>15+</sup> | string | Yes | Disk serial number. This API will start a temporary process during execution. When system load is high, it may cause a blocking risk. To ensure main thread responsiveness, it is recommended to avoid calling this API on the main thread. The device information varies by device and is fixed, so it can be cached after first retrieval and stored locally to avoid repeating each use, to improve performance.<br> **NOTE**<br>This field can be queried only on some 2-in-1 devices. The query result is empty on other devices.<br> **Requires permission**: [ohos.permission.ACCESS_DISK_PHY_INFO](../../security/AccessToken/restricted-permissions.md#ohospermissionaccess_disk_phy_info) <br> Example: 2502EM400567 |
| performanceClass<sup>19+</sup> | [PerformanceClassLevel](#performanceclasslevel19) | Yes | Describes the device capability rating, which is comprehensively evaluated based on factors such as CPU, memory, storage read/write performance, and screen resolution.<br>**Usage scenario**: Used for performance adaptation based on device capabilities, such as adjusting animation complexity, selecting resources of different quality, and dynamically controlling features.<br>Example: 0 |
| chipType<sup>21+</sup> | string | Yes | CPU chip model of the current device.<br>**Usage scenario**: Used for scenarios such as performance adaptation based on the chip model, device feature identification, and compatibility check. Different chip models may have different features such as GPU performance and AI acceleration capabilities.<br> Example: xxxxx |
| bootCount<sup>21+</sup> | number | Yes | Number of restarts of the current device. The value -1 is returned if the retrieval fails.<br> Example: 100 |
| deviceColor | string | Yes | Color of the current device. An empty string is returned if it cannot be obtained.<br>**Model restriction**: This API is only used under the Stage model.<br> **Since version**: 26.0.0<br> Example: gold |

**Error codes**

For details about the error codes, see [deviceInfo Error Codes](errorcode-device-info.md) and [Universal Error Codes](../errorcode-universal.md).

| ID   | Error Message    |
|---------|---------|
| 14700103 | Permission verification failed. System permission operation permission denied |
| 401     | Parameter error. Possible causes: 1. Incorrect parameter types. |

**Example**

```ts
import { deviceInfo } from '@kit.BasicServicesKit';

let deviceTypeInfo: string = deviceInfo.deviceType;
// Output: the value of the deviceType is :wearable
console.info('the value of the deviceType is :' + deviceTypeInfo);

let manufactureInfo: string = deviceInfo.manufacture;
// Output: the value of the manufactureInfo is :XXXX
console.info('the value of the manufactureInfo is :' + manufactureInfo);

let brandInfo: string = deviceInfo.brand;
// Output: the value of the brand is :XXXX
console.info('the value of the device brand is :' + brandInfo);

let marketNameInfo: string = deviceInfo.marketName;
// Output: the value of the marketName is :Mate XX
console.info('the value of the deviceInfo marketName is :' + marketNameInfo);

let productSeriesInfo: string = deviceInfo.productSeries;
// Output: the value of the productSeries is :TAS
console.info('the value of the deviceInfo productSeries is :' + productSeriesInfo);

let productModelInfo: string = deviceInfo.productModel;
// Output: the value of the productModel is :TAS-AL00
console.info('the value of the deviceInfo productModel is :' + productModelInfo);

let productModelAliasInfo: string = deviceInfo.productModelAlias;
console.info('the value of the deviceInfo productModelAlias is :' + productModelAliasInfo);

let softwareModelInfo: string = deviceInfo.softwareModel;
// Output: the value of the softwareModel is :TAS-AL00
console.info('the value of the deviceInfo softwareModel is :' + softwareModelInfo);

let hardwareModelInfo: string = deviceInfo.hardwareModel;
// Output: the value of the hardwareModel is :TASA00CVN1
console.info('the value of the deviceInfo hardwareModel is :' + hardwareModelInfo);

let serialInfo: string = deviceInfo.serial;
// Output: the value of the serial is :the serial number varies by device
console.info('the value of the deviceInfo serial is :' + serialInfo);

let bootloaderVersionInfo: string = deviceInfo.bootloaderVersion;
// Output: the value of the bootloaderVersion is :bootloader
console.info('the value of the deviceInfo bootloaderVersion is :' + bootloaderVersionInfo);

let abiListInfo: string = deviceInfo.abiList;
// Output: the value of the abiList is :arm64-v8a
console.info('the value of the deviceInfo abiList is :' + abiListInfo);

let securityPatchTagInfo: string = deviceInfo.securityPatchTag;
// Output: the value of the securityPatchTag is :2021/01/01
console.info('the value of the deviceInfo securityPatchTag is :' + securityPatchTagInfo);

let displayVersionInfo: string = deviceInfo.displayVersion;
// Output: the value of the displayVersion is :XXX X.X.X.X
console.info('the value of the deviceInfo displayVersion is :' + displayVersionInfo);

let incrementalVersionInfo: string = deviceInfo.incrementalVersion;
// Output: the value of the incrementalVersion is :default
console.info('the value of the deviceInfo incrementalVersion is :' + incrementalVersionInfo);

let osReleaseTypeInfo: string = deviceInfo.osReleaseType;
// Output: the value of the osReleaseType is :Release
console.info('the value of the deviceInfo osReleaseType is :' + osReleaseTypeInfo);

let osFullNameInfo: string = deviceInfo.osFullName;
// Output: the value of the osFullName is :OpenHarmony-5.0.0.1
console.info('the value of the deviceInfo osFullName is :' + osFullNameInfo);

let majorVersionInfo: number = deviceInfo.majorVersion;
// Output: the value of the majorVersion is :5
console.info('the value of the deviceInfo majorVersion is :' + majorVersionInfo);

let seniorVersionInfo: number = deviceInfo.seniorVersion;
// Output: the value of the seniorVersion is :0
console.info('the value of the deviceInfo seniorVersion is :' + seniorVersionInfo);

let featureVersionInfo: number = deviceInfo.featureVersion;
// Output: the value of the featureVersion is :0
console.info('the value of the deviceInfo featureVersion is :' + featureVersionInfo);

let buildVersionInfo: number = deviceInfo.buildVersion;
// Output: the value of the buildVersion is :1
console.info('the value of the deviceInfo buildVersion is :' + buildVersionInfo);

let sdkApiVersionInfo: number = deviceInfo.sdkApiVersion;
// Output: the value of the sdkApiVersion is :12
console.info('the value of the deviceInfo sdkApiVersion is :' + sdkApiVersionInfo);

let sdkMinorApiVersionInfo: number = deviceInfo.sdkMinorApiVersion;
// Output: the value of the sdkMinorApiVersion is :0
console.info('the value of the deviceInfo sdkMinorApiVersion is :' + sdkMinorApiVersionInfo);

let sdkPatchApiVersionInfo: number = deviceInfo.sdkPatchApiVersion;
// Output: the value of the sdkPatchApiVersion is :0
console.info('the value of the deviceInfo sdkPatchApiVersion is :' + sdkPatchApiVersionInfo);

let firstApiVersionInfo: number = deviceInfo.firstApiVersion;
// Output: the value of the firstApiVersion is :3
console.info('the value of the deviceInfo firstApiVersion is :' + firstApiVersionInfo);

let versionIdInfo: string = deviceInfo.versionId;
// Output: the value of the versionId is :wearable/XXXX/XXXX/TAS/OpenHarmony-5.0.0.1/TAS-AL00/TAS-AL00/12/default/release:nolog
console.info('the value of the deviceInfo versionId is :' + versionIdInfo);

let buildTypeInfo: string = deviceInfo.buildType;
// Output: the value of the buildType is :default
console.info('the value of the deviceInfo buildType is :' + buildTypeInfo);

let buildUserInfo: string = deviceInfo.buildUser;
// Output: the value of the buildUser is :default
console.info('the value of the deviceInfo buildUser is :' + buildUserInfo);

let buildHostInfo: string = deviceInfo.buildHost;
// Output: the value of the buildHost is :default
console.info('the value of the deviceInfo buildHost is :' + buildHostInfo);

let buildTimeInfo: string = deviceInfo.buildTime;
// Output: the value of the buildTime is :default
console.info('the value of the deviceInfo buildTime is :' + buildTimeInfo);

let buildRootHashInfo: string = deviceInfo.buildRootHash;
// Output: the value of the buildRootHash is :default
console.info('the value of the deviceInfo buildRootHash is :' + buildRootHashInfo);

let udid: string = deviceInfo.udid;
// Output: the value of the udid is :9D6AABD147XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXE5536412
console.info('the value of the deviceInfo udid is :' + udid);

let distributionOSName: string = deviceInfo.distributionOSName;
// Output: the value of the distributionOSName is :OpenHarmony
console.info('the value of the deviceInfo distributionOSName is :' + distributionOSName);

let distributionOSVersion: string = deviceInfo.distributionOSVersion;
// Output: the value of the distributionOSVersion is :5.0.0
console.info('the value of the deviceInfo distributionOSVersion is :' + distributionOSVersion);

let distributionOSApiVersion: number = deviceInfo.distributionOSApiVersion;
// Output: the value of the distributionOSApiVersion is :50001
console.info('the value of the deviceInfo distributionOSApiVersion is :' + distributionOSApiVersion);

let distributionOSApiName: string = deviceInfo.distributionOSApiName;
// Output: the value of the deviceInfo distributionOSApiName is :5.0.1
console.info('the value of the deviceInfo distributionOSApiName is :' + distributionOSApiName);

let distributionOSReleaseType: string = deviceInfo.distributionOSReleaseType;
// Output: the value of the distributionOSReleaseType is :Release
console.info('the value of the deviceInfo distributionOSReleaseType is :' + distributionOSReleaseType);

let odid: string = deviceInfo.ODID;
// Output: the value of the deviceInfo odid is :1234a567-XXXX-XXXX-XXXX-XXXXXXXXXXXX
console.info('the value of the deviceInfo odid is :' + odid);

let diskSN: string = deviceInfo.diskSN;
// Output: the value of the deviceInfo diskSN is :2502EM400567
console.info('the value of the deviceInfo diskSN is :' + diskSN);

let performanceClass = deviceInfo.performanceClass;
// Output: the value of the deviceInfo performanceClass is :0
console.info('the value of the deviceInfo performanceClass is :' + performanceClass);

let chipType: string = deviceInfo.chipType;
// Output: the value of the deviceInfo chipType is :xxxxx
console.info('the value of the deviceInfo chipType is :' + chipType);

let bootCount: number = deviceInfo.bootCount;
// Output: the value of the bootCount is :100
console.info('the value of the deviceInfo bootCount is :' + bootCount);

let deviceColor: string = deviceInfo.deviceColor;
// Output: the value of the deviceColor is :blue
console.info('the value of the deviceColor is :' + deviceColor);
```

## PerformanceClassLevel<sup>19+</sup>

Enumerates the device capability levels.

**System capability**: SystemCapability.Startup.SystemInfo

| Name                 | Value | Description          |
| ---------------------| ---- | -------------- |
| CLASS_LEVEL_HIGH     | 0    | High    |
| CLASS_LEVEL_MEDIUM   | 1    | Medium  |
| CLASS_LEVEL_LOW      | 2    | Low  |

## DeviceTypes<sup>20+</sup>

Enumerates device types, which can be used to verify the return value of **deviceType**.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Startup.SystemInfo

| Name| Value  | Description                      |
| ---- | ---- | -------------------------- |
| TYPE_DEFAULT | 'default' | Default device|
| TYPE_PHONE | 'phone' | Smartphone|
| TYPE_TABLET | 'tablet' | Tablet|
| TYPE_2IN1 | '2in1' | PC/2-in-1 device|
| TYPE_TV | 'tv' | Smart TV|
| TYPE_WEARABLE | 'wearable' | Wearable|
| TYPE_CAR | 'car' | Head unit|

**Example**

```ts
let deviceTypesInfoDefault: string = deviceInfo.DeviceTypes.TYPE_DEFAULT;
// Output: the value of the DeviceTypes is :default
console.info('the value of the DeviceTypes is :' + deviceTypesInfoDefault);

let deviceTypesInfoPhone: string = deviceInfo.DeviceTypes.TYPE_PHONE;
// Output: the value of the DeviceTypes is :phone
console.info('the value of the DeviceTypes is :' + deviceTypesInfoPhone);

let deviceTypesInfoTablet: string = deviceInfo.DeviceTypes.TYPE_TABLET;
// Output: the value of the DeviceTypes is :tablet
console.info('the value of the DeviceTypes is :' + deviceTypesInfoTablet);

let deviceTypesInfo2IN1: string = deviceInfo.DeviceTypes.TYPE_2IN1;
// Output: the value of the DeviceTypes is :2in1
console.info('the value of the DeviceTypes is :' + deviceTypesInfo2IN1);

let deviceTypesInfoTV: string = deviceInfo.DeviceTypes.TYPE_TV;
// Output: the value of the DeviceTypes is :tv
console.info('the value of the DeviceTypes is :' + deviceTypesInfoTV);

let deviceTypesInfoWearable: string = deviceInfo.DeviceTypes.TYPE_WEARABLE;
// Output: the value of the DeviceTypes is :wearable
console.info('the value of the DeviceTypes is :' + deviceTypesInfoWearable);

let deviceTypesInfoCar: string = deviceInfo.DeviceTypes.TYPE_CAR;
// Output: the value of the DeviceTypes is :car
console.info('the value of the DeviceTypes is :' + deviceTypesInfoCar);
```


## deviceInfo.apiAvailable

apiAvailable(version: string | number): boolean;

Checks whether a specified API version is available on the current device.<br>
This API provides compatibility check for OpenHarmony and its distribution OS API versions. A suitable version check method is automatically selected based on the input format and supported API versions.

**Since:** 26.0.0

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.Startup.SystemInfo

**Parameters**

| Name    | Type      | Mandatory | Description                               |
| --------- | ---------| ---- | ---------------------------------- |
| version | string \| number | Yes | API version number to be verified. Both integer and string formats are supported. The string uses the M.S.F format (for example, "26.0.0" and "5.0.1"): for API 26.0.0 and later (version >= 26.0.0), it represents the OpenHarmony and distribution system API version. For versions earlier than API 26.0.0 (version < 26.0.0), it represents the distribution system API version. The integer format (for example, 13) represents the OpenHarmony SDK API version. (Only API versions earlier than 26 are supported.) M>=26, 0<=S<=99, 0<=F<=99. A compilation error is reported when an invalid literal is passed in. |

**Return value**

| Type                                       | Description                                            |
| ------------------------------------------ | ----------------------------------------------- |
| boolean                                     | Boolean value. If **true** is returned, the API version of the device is the version specified in the input parameter or a later version. If **false** is returned, the API version is earlier than the version specified in the input parameter, the version format is invalid, or the version does not exist.  |

**Example**

```ts
import { deviceInfo } from '@kit.BasicServicesKit';

// For OpenHarmony base and distribution APIs of API version 26.0.0 or later
if (deviceInfo.apiAvailable('26.0.0')) {
  // Method that requires version isolation
}


// For Distribution OS-specific APIs, that is, APIs marked with since M.S.F(N)
if (deviceInfo.apiAvailable('5.0.1')) {
  // Method that requires version isolation
}


// For OpenHarmony base public APIs, that is, APIs marked with since N
if (deviceInfo.apiAvailable(13)) {
  // Method that requires version isolation
}

```
