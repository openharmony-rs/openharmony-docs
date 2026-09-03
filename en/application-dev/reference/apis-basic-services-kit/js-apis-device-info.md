# @ohos.deviceInfo (Device Information)
<!--Kit: Basic Services Kit-->
<!--Subsystem: Startup-->
<!--Owner: @chenjinxiang3-->
<!--Designer: @chenjinxiang3-->
<!--Tester: @liuhaonan2-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=dedb6730301e201bd92e89c565e2c1a291211a57 translatedAt=2026-09-01T03:43:17.501Z pushedAt=2026-09-01T08:15:36.231Z -->

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
| deviceType | string | Yes | Device type. For details, see [deviceTypes](../../quick-start/module-configuration-file.md#devicetypes).<br>**Atomic service API**: This API can be used in atomic services since API version 11.<br>Example: <!--RP1-->wearable<!--RP1End--> |
| manufacture | string | Yes | Device manufacturer. |
| brand | string | Yes | Device brand.<br>**Atomic service API**: This API can be used in atomic services since API version 11. |
| marketName | string | Yes | Marketing name.<br>Example: <!--RP2-->Mate XX<!--RP2End--> |
| productSeries | string | Yes | Product series.<br>Example: <!--RP3-->TAS<!--RP3End--> |
| productModel | string | Yes | Product model.<br>**Atomic service API**: This API can be used in atomic services since API version 11.<br>Example: <!--RP4-->TAS-AL00<!--RP4End--> |
| productModelAlias<sup>14+</sup> | string | Yes | Product model alias.<br>**Atomic service API**: This API can be used in atomic services since API version 14.<br>Example: TAS-AL00 |
| softwareModel | string | Yes | Software model.<br>Example: <!--RP5-->TAS-AL00<!--RP5End--> |
| hardwareModel | string | Yes | Hardware model.<br>Example: <!--RP6-->TASA00CVN1<!--RP6End--> |
| hardwareProfile<sup>(deprecated) </sup> | string | Yes | Hardware profile.<br>NOTE<br>This API is supported since API version 6 and deprecated since API version 9. You are advised to use [SystemCapability](../syscap.md) instead.<br>Example: default |
| serial | string | Yes | Serial number of the device. This API will start a temporary process during execution. When the system load is high, blocking may occur. To ensure the response of the main thread of your application, you are advised not to call this API in the main thread. This value varies depending on the device and is fixed. To improve performance, you can store this information on a local device after obtaining it for the first time.<br>Note: The device serial number can be used as the unique identifier of a device.<br>**Required permissions**: ohos.permission.sec.ACCESS_UDID(for system applications and enterprise applications only)<br>Example: The serial number varies with the device. |
| bootloaderVersion | string | Yes | Bootloader version, which identifies the version of the device bootloader.<br>Example: bootloader |
| abiList | string | Yes | Application binary interface (Abi) list.<br>Example: arm64-v8a |
| securityPatchTag | string | Yes | Security patch tag.<br>Example: <!--RP7-->2021/01/01<!--RP7End--> |
| displayVersion | string | Yes | Product version.<!--RP14--><!--RP14End--><br>Example: <!--RP8-->XXX X.X.X.X<!--RP8End--> |
| incrementalVersion | string | Yes | Incremental version, which is the Ohos version number generated during compilation. <br>Example: 6.1.1.120 |
| osReleaseType | string | Yes | OS release type. The options are as follows:<br>-&nbsp;**Canary**: Preliminary release open only to specific developers. This release does not promise API stability and may require tolerance of instability.<br>-&nbsp;**Beta**: Release open to all developers. This release does not promise API stability and may require tolerance of instability.<br>-&nbsp;**Release**: Official release open to all developers. This release promises that all APIs are stable.<br>Example: <!--RP9-->Canary/Beta/Release<!--RP9End--> |
| osFullName | string | Yes | System version. The version number is in the format of **<!--RP12-->OpenHarmony-x.x.x.x**, where **x** is a placeholder for digits. <!--RP12End-->To obtain the value of a segment in the version number, you are advised to use **majorVersion**, **seniorVersion**, **featureVersion**, or **buildVersion**, which can improve efficiency. Parsing **osFullName** is not recommended.<br>**Atomic service API**: This API can be used in atomic services since API version 11.<br>Example: <!--RP10-->OpenHarmony-5.0.0.1<!--RP10End--> |
| majorVersion | number | Yes | Major version number, which increments with the main version. The value is the first digit in **osFullName**. You are advised to use **deviceInfo.majorVersion** instead of parsing **osFullName** to obtain the value, facilitating efficiency improvement.<br>Example: 5 |
| seniorVersion | number | Yes | Senior version number, which increments with architecture and feature updates. The value is the second digit in **osFullName**. You are advised to use **deviceInfo.seniorVersion** instead of parsing **osFullName** to obtain the value, facilitating efficiency improvement.<br>Example: 0 |
| featureVersion | number | Yes | Feature version number, which identifies the planned new feature version. The value is the third digit in **osFullName**. You are advised to use **deviceInfo.featureVersion** instead of parsing **osFullName** to obtain the value, facilitating efficiency improvement.<br>Example: 0 |
| buildVersion | number | Yes | Build version number, which identifies the build version. The value is the fourth digit in **osFullName**. You are advised to use **deviceInfo.buildVersion** instead of parsing **osFullName** to obtain the value, facilitating efficiency improvement.<br>Example: 1 |
| sdkApiVersion | number | Yes | SDK API version.<br>**Atomic service API**: This API can be used in atomic services since API version 14.<br>Example: 12 |
| sdkMinorApiVersion | number | Yes | SDK minor API version. Starting from API version 26.0.0, the system API version is in the format of **sdkApiVersion.sdkMinorApiVersion.sdkPatchApiVersion**.<br>**Model restriction**: This API can be used only in the stage model.<br>**Since**: 26.0.0<br>**Atomic service API**: This API can be used in atomic services since API version 26.0.0.<br>Example: 0 |
| sdkPatchApiVersion | number | Yes | SDK patch API version. Starting from API version 26.0.0, the system API version is in the format of **sdkApiVersion.sdkMinorApiVersion.sdkPatchApiVersion**.<br>**Model restriction**: This API can be used only in the stage model.<br>**Since**: 26.0.0<br>**Atomic service API**: This API can be used in atomic services since API version 26.0.0.<br>Example: 0 |
| firstApiVersion | number | Yes | First API version.<br>Example: 3 |
| versionId | string | Yes | Version ID, which is a concatenation of **deviceType**, **manufacture**, **brand**, **productSeries**, **osFullName**, **productModel**, **softwareModel**, **sdkApiVersion**, **incrementalVersion**, and **buildType**. To obtain a specific field value, you are advised to use the corresponding field directly (such as **deviceType** and **manufacture**) instead of parsing **versionId**, facilitating efficiency improvement. |
| buildType | string | Yes | Build type.<br>Example: default |
| buildUser | string | Yes | Build user.<br>Example: default |
| buildHost | string | Yes | Build host.<br>Example: default |
| buildTime | string | Yes | Build time.<br>Example: default |
| buildRootHash | string | Yes | Build root hash.<br>Example: default |
| udid<sup>7+</sup> | string | Yes | UDID of the device. This API will start a temporary process during execution. When the system load is high, blocking may occur. To ensure the response of the main thread of your application, you are advised not to call this API in the main thread. This value varies depending on the device and is fixed. To improve performance, you can store this information on a local device after obtaining it for the first time.<br>**Note:** The data length is 65 bytes (including the terminator). The UDID can be used as the unique identifier of a device.<br>**Required permissions**: ohos.permission.sec.ACCESS_UDID(for system applications and enterprise applications only)<br>Example: 9D6AABD147XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXE5536412 |
| distributionOSName<sup>10+</sup> | string | Yes | Distribution OS name<!--Del-->, which is defined by the issuer<!--DelEnd-->.<br>Example: OpenHarmony |
| distributionOSVersion<sup>10+</sup> | string | Yes | Distribution OS version<!--Del-->, which is defined by the issuer<!--DelEnd-->.<!--RP11--><!--RP11End--><br>Example: 5.0.0 |
| distributionOSApiVersion<sup>10+</sup> | number | Yes | Distribution OS API version.<!--Del--> It is defined by the issuer.<!--DelEnd-->.<!--RP15--><!--RP15End--><br>Example: 50001 |
| distributionOSApiName<sup>13+</sup> | string | Yes | Distribution OS API name.<!--Del--> It is defined by the issuer.<!--DelEnd-->.<!--RP16--><br>**Note:** It is not recommended that this field be used to determine the version number.<br>Example: 5.0.1<!--RP16End--> |
| distributionOSReleaseType<sup>10+</sup> | string | Yes | Distribution OS release type<!--Del-->, which is defined by the issuer<!--DelEnd-->.<br>Example: Release |
| ODID<sup>12+</sup> | string | Yes | Open device identifier (ODID).<br>An ODID will be regenerated in the following scenarios:<br>Restore a phone to its factory settings.<br>Uninstall and reinstall all apps with the same **developerId** on one device.<br>An ODID is generated based on the following rules:<br>The value is generated based on the **groupId** parsed from the **developerId** in the signature information. As **groupId.developerId** is the rule, if no **groupId** exists, the **developerId** is used as the **groupId**.<br>Applications with the same **developerId** use the same ODID on one device.<br>Applications with different **developerId**s use different ODIDs on one device.<br>Applications with the same **developerId** use different ODIDs on different devices.<br>Applications with different **developerId**s use different ODIDs on different devices.<br>Note: The data length is 37 bytes (including the terminator).<br>Example: 1234a567-XXXX-XXXX-XXXX-XXXXXXXXXXXX |
| diskSN<sup>15+</sup> | string | Yes | Serial number of the disk. This API will start a temporary process during execution. When the system load is high, blocking may occur. To ensure the response of the main thread of your application, you are advised not to call this API in the main thread. This value varies depending on the device and is fixed. To improve performance, you can store this information on a local device after obtaining it for the first time.<br>Note: This field can be queried only on some 2-in-1 devices. The query result is empty on other devices.<br>**Required permissions**: ohos.permission.ACCESS_DISK_PHY_INFO(for system applications and enterprise applications only)<br>Example: 2502EM400567 |
| performanceClass<sup>19+</sup> | [PerformanceClassLevel](#performanceclasslevel19) | Yes | Device capability level, which is evaluated based on factors such as CPU, memory, storage read/write performance, and screen resolution.<br>**Use scenarios**: This parameter can be used for performance adaptation based on device capabilities, such as adjusting animation complexity, selecting resources of different quality, and dynamically controlling features.<br>Example: 0 |
| chipType<sup>21+</sup> | string | Yes | CPU chip model of the device.<br>**Use scenarios**: This parameter can be used for performance adaptation, device feature identification, and compatibility check based on the chip model. Different chip models may have different GPU performance and AI acceleration capabilities.<br>Example: xxxxx |
| bootCount<sup>21+</sup> | number | Yes | Number of device reboots. If the number cannot be obtained, **-1** is returned.<br>Example: 100 |
| deviceColor | string | Yes | Device color. If the value cannot be obtained, an empty string is returned.<br>**Model restriction:** This API can only be used in the stage model.<br> **Since:** 26.0.0<br> Example: gold |

**Error codes**

For details about the error codes, see [deviceInfo Error Codes](errorcode-device-info.md) and [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message   |
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
    // Output: the value of the serial is :The SN varies with the device.
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

    let distributionOSName: string = deviceInfo.distributionOSName
    // Output: the value of the distributionOSName is :OpenHarmony
    console.info('the value of the deviceInfo distributionOSName is :' + distributionOSName);

    let distributionOSVersion: string = deviceInfo.distributionOSVersion
    // Output: the value of the distributionOSVersion is :5.0.0
    console.info('the value of the deviceInfo distributionOSVersion is :' + distributionOSVersion);

    let distributionOSApiVersion: number = deviceInfo.distributionOSApiVersion
    // Output: the value of the distributionOSApiVersion is :500001
    console.info('the value of the deviceInfo distributionOSApiVersion is :' + distributionOSApiVersion);

    let distributionOSApiName: string = deviceInfo.distributionOSApiName
// Output: the value of the deviceInfo distributionOSApiName is :OpenHarmony-API
    console.info('the value of the deviceInfo distributionOSApiName is :' + distributionOSApiName);

    let distributionOSReleaseType: string = deviceInfo.distributionOSReleaseType
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

    let bootCount: number = deviceInfo.bootCount
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
    // Output: the value of the DeviceTypes is :phone-type 
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
This API provides compatibility check for OpenHarmony and its released versions. A suitable version check method is automatically selected based on the input format and supported API versions.

**Since**: 26.0.0

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.Startup.SystemInfo

**Parameters**

| Name   | Type                                     | Mandatory| Description                              |
| --------- | ----------------------------------------- | ---- | ---------------------------------- |
| version | string \| number | Yes | API version to be verified. Supports both integer and string formats. The string uses the M.S.F format (for example, "26.0.0" and "5.0.1"): for API 26.0.0 and later (version >= 26.0.0), it represents the OpenHarmony and distribution system API version. For API earlier than 26.0.0 (version < 26.0.0), it represents the distribution system API version. The integer format (for example, 13) represents the OpenHarmony SDK API version. (Only API earlier than 26 is supported.) M>=26, 0<=S<=99, 0<=F<=99. A compilation error occurs when an invalid literal is passed. |

**Return value**

| Type                                      | Description                                           |
| ------------------------------------------ | ----------------------------------------------- |
| boolean                                     | Boolean value. If **true** is returned, the API version of the device is the version specified in the input parameter or a later version. If **false** is returned, the API version is earlier than the version specified in the input parameter, the version format is invalid, or the version does not exist.  |

**Example**

```ts
import { deviceInfo } from '@kit.BasicServicesKit';

// For OpenHarmony base and distribution APIs of API version 26.0.0 or later
if (deviceInfo.apiAvailable("26.0.0")) {
   // Method that requires version isolation
}


// For Distribution OS-specific APIs, that is, APIs marked with since M.S.F(N)
if (deviceInfo.apiAvailable("5.0.1")) {
   // Method that requires version isolation
}


// For OpenHarmony base public APIs, that is, APIs marked with since N
if (deviceInfo.apiAvailable(13)) {
   // Method that requires version isolation
}

```
