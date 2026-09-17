# Constants

## abiList

```TypeScript
const abiList: string
```

Application binary interface (Abi) list.

Example: arm64-v8a

**Type:** string

**Since:** 6

**System capability:** SystemCapability.Startup.SystemInfo

## bootCount

```TypeScript
const bootCount: number
```

Number of device reboots. If the number cannot be obtained, **-1** is returned.

Example: 100

**Type:** number

**Since:** 21

**System capability:** SystemCapability.Startup.SystemInfo

## bootloaderVersion

```TypeScript
const bootloaderVersion: string
```

Bootloader version, which identifies the version of the device bootloader.

Example: bootloader

**Type:** string

**Since:** 6

**System capability:** SystemCapability.Startup.SystemInfo

## brand

```TypeScript
const brand: string
```

Device brand.

**Type:** string

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Startup.SystemInfo

## buildHost

```TypeScript
const buildHost: string
```

Build host.

Example: default

**Type:** string

**Since:** 6

**System capability:** SystemCapability.Startup.SystemInfo

## buildRootHash

```TypeScript
const buildRootHash: string
```

Build root hash.

Example: default

**Type:** string

**Since:** 6

**System capability:** SystemCapability.Startup.SystemInfo

## buildTime

```TypeScript
const buildTime: string
```

Build time.

Example: default

**Type:** string

**Since:** 6

**System capability:** SystemCapability.Startup.SystemInfo

## buildType

```TypeScript
const buildType: string
```

Build type.

Example: default

**Type:** string

**Since:** 6

**System capability:** SystemCapability.Startup.SystemInfo

## buildUser

```TypeScript
const buildUser: string
```

Build user.

Example: default

**Type:** string

**Since:** 6

**System capability:** SystemCapability.Startup.SystemInfo

## buildVersion

```TypeScript
const buildVersion: number
```

Build version number. The value is the fourth digit in **osFullName**. You are advised to use **deviceInfo.buildVersion** instead of parsing **osFullName** to obtain the value, facilitating efficiency improvement.

Example: 1

**Type:** number

**Since:** 6

**System capability:** SystemCapability.Startup.SystemInfo

## chipType

```TypeScript
const chipType: string
```

Obtains the device CPU chipType by a string.

Example: xxxxx

**Type:** string

**Since:** 21

**System capability:** SystemCapability.Startup.SystemInfo

## deviceColor

```TypeScript
const deviceColor: string
```

Device color. If the value cannot be obtained, an empty string is returned.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Startup.SystemInfo

## deviceType

```TypeScript
const deviceType: string
```

Device type. For details, see [deviceTypes tag](../../../quick-start/module-configuration-file.md#devicetypes).

Example: &lt;!--RP1--&gt;wearable&lt;!--RP1End--&gt;

**Type:** string

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Startup.SystemInfo

## diskSN

```TypeScript
const diskSN: string
```

Serial number of the disk. This API will start a temporary process during execution. When the system load is high, blocking may occur. To ensure the response of the main thread of your application, you are advised not to call this API in the main thread. This value varies depending on the device and is fixed. To improve performance, you can store this information on a local device after obtaining it for the first time.

**NOTE:** 

This field can be queried only on the 2-in-1 device. For other devices, the query result is empty.

ohos.permission.ACCESS_DISK_PHY_INFO

Example: 2502EM400567

**Type:** string

**Since:** 15

**Required permissions:** ohos.permission.ACCESS_DISK_PHY_INFO

**System capability:** SystemCapability.Startup.SystemInfo

## displayVersion

```TypeScript
const displayVersion: string
```

Product version.

Example: &lt;!--RP8--&gt;XXX X.X.X.X&lt;!--RP8End--&gt;

**Type:** string

**Since:** 6

**System capability:** SystemCapability.Startup.SystemInfo

## distributionOSApiName

```TypeScript
const distributionOSApiName: string
```

Distribution OS API name.<!--Del--> It is defined by the issuer.<!--DelEnd-->

**Type:** string

**Since:** 13

**System capability:** SystemCapability.Startup.SystemInfo

## distributionOSApiVersion

```TypeScript
const distributionOSApiVersion: number
```

Distribution OS API version.<!--Del--> It is defined by the issuer.<!--DelEnd-->

Example: 50001

**Type:** number

**Since:** 10

**System capability:** SystemCapability.Startup.SystemInfo

## distributionOSName

```TypeScript
const distributionOSName: string
```

Distribution OS name.<!--Del--> It is defined by the issuer.<!--DelEnd-->

Example: OpenHarmony

**Type:** string

**Since:** 10

**System capability:** SystemCapability.Startup.SystemInfo

## distributionOSReleaseType

```TypeScript
const distributionOSReleaseType: string
```

Distribution OS release type.<!--Del--> It is defined by the issuer.<!--DelEnd-->

Example: Release

**Type:** string

**Since:** 10

**System capability:** SystemCapability.Startup.SystemInfo

## distributionOSVersion

```TypeScript
const distributionOSVersion: string
```

Distribution OS version.<!--Del--> It is defined by the issuer.<!--DelEnd-->&lt;!--RP11--&gt;&lt;!--RP11End--&gt;

Example: 5.0.0

**Type:** string

**Since:** 10

**System capability:** SystemCapability.Startup.SystemInfo

## featureVersion

```TypeScript
const featureVersion: number
```

Feature version number. The value is the third digit in **osFullName**. You are advised to use **deviceInfo.featureVersion** instead of parsing **osFullName** to obtain the value, facilitating efficiency improvement.

Example: 0

**Type:** number

**Since:** 6

**System capability:** SystemCapability.Startup.SystemInfo

## firstApiVersion

```TypeScript
const firstApiVersion: number
```

First API version.

Example: 3

**Type:** number

**Since:** 6

**System capability:** SystemCapability.Startup.SystemInfo

## hardwareModel

```TypeScript
const hardwareModel: string
```

Hardware model.

Example: &lt;!--RP6--&gt;TASA00CVN1&lt;!--RP6End--&gt;

**Type:** string

**Since:** 6

**System capability:** SystemCapability.Startup.SystemInfo

## hardwareProfile

```TypeScript
const hardwareProfile: string
```

Hardware profile.

**NOTE:** 

This API is supported since API version 6 and deprecated since API version 9. You are advised to use [SystemCapability](../../../reference/syscap.md) instead.

Example: default

**Type:** string

**Since:** 6

**Deprecated since:** 9

**System capability:** SystemCapability.Startup.SystemInfo

## incrementalVersion

```TypeScript
const incrementalVersion: string
```

Incremental version, which is the Ohos version number generated during compilation.

Example: default

**Type:** string

**Since:** 6

**System capability:** SystemCapability.Startup.SystemInfo

## majorVersion

```TypeScript
const majorVersion: number
```

Major version number, which increments with the main version. The value is the first digit in **osFullName**. You are advised to use **deviceInfo.majorVersion** instead of parsing **osFullName** to obtain the value, facilitating efficiency improvement.

Example: 5

**Type:** number

**Since:** 6

**System capability:** SystemCapability.Startup.SystemInfo

## manufacture

```TypeScript
const manufacture: string
```

Device manufacturer.

**Type:** string

**Since:** 6

**System capability:** SystemCapability.Startup.SystemInfo

## marketName

```TypeScript
const marketName: string
```

Marketing name.

Example: &lt;!--RP2--&gt;Mate XX&lt;!--RP2End--&gt;

**Type:** string

**Since:** 6

**System capability:** SystemCapability.Startup.SystemInfo

## ODID

```TypeScript
const ODID: string
```

Open device identifier.

An ODID will be regenerated in the following scenarios:

Restore a phone to its factory settings.

Uninstall and reinstall all applications with the same **developerId** on one device.

An ODID is generated based on the following rules:

The value is generated based on the **groupId** parsed from the **developerId** in the signature information. As **groupId.developerId** is the rule, if no **groupId** exists, the **developerId** is used as the **groupId**.

Applications with the same **developerId** use the same ODID on one device.

Applications with different **developerId**s use different ODIDs on one device.

Applications with the same **developerId** use different ODIDs on different devices.

Applications with different **developerId**s use different ODIDs on different devices.

**NOTE:** 

The data length is 37 bytes (including the terminator).

Example: 1234a567-XXXX-XXXX-XXXX-XXXXXXXXXXXX

**Type:** string

**Since:** 12

**System capability:** SystemCapability.Startup.SystemInfo

## osFullName

```TypeScript
const osFullName: string
```

System version. The version number is in the format of **&lt;!--RP12--&gt;OpenHarmony-x.x.x.x**, where **x** is a placeholder for digits. &lt;!--RP12End--&gt;To obtain the value of a segment in the version number, you are advised to use **majorVersion**, **seniorVersion**, **featureVersion**, or **buildVersion**, which can improve efficiency. Parsing **osFullName** is not recommended.

Example: &lt;!--RP10--&gt;Openharmony-5.0.0.1&lt;!--RP10End--&gt;

**Type:** string

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Startup.SystemInfo

## osReleaseType

```TypeScript
const osReleaseType: string
```

OS release type. The options are as follows:

- **Canary**: Preliminary release open only to specific developers. This release does not promise API stability  
and may require tolerance of instability.  
- **Beta**: Release open to all developers. This release does not promise API stability and may require tolerance  
of instability.  
- **Release**: Official release open to all developers. This release promises that all APIs are stable.

Example: &lt;!--RP9--&gt;Canary/Beta/Release&lt;!--RP9End--&gt;

**Type:** string

**Since:** 6

**System capability:** SystemCapability.Startup.SystemInfo

## performanceClass

```TypeScript
const performanceClass: PerformanceClassLevel
```

Device capability level, which is evaluated based on factors such as CPU, memory, storage read/write performance, and screen resolution.

Example: 0

**Type:** [PerformanceClassLevel](arkts-basicservices-deviceinfo-performanceclasslevel-e.md)

**Since:** 19

**System capability:** SystemCapability.Startup.SystemInfo

## productModel

```TypeScript
const productModel: string
```

Product model.

Example: &lt;!--RP4--&gt;TAS-AL00&lt;!--RP4End--&gt;

**Type:** string

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Startup.SystemInfo

## productModelAlias

```TypeScript
const productModelAlias: string
```

Product model alias.

Example: TAS-AL00

**Type:** string

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Startup.SystemInfo

## productSeries

```TypeScript
const productSeries: string
```

Product series.

Example: &lt;!--RP3--&gt;TAS&lt;!--RP3End--&gt;

**Type:** string

**Since:** 6

**System capability:** SystemCapability.Startup.SystemInfo

## sdkApiVersion

```TypeScript
const sdkApiVersion: number
```

SDK API version.

Example: 12

**Type:** number

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Startup.SystemInfo

## sdkMinorApiVersion

```TypeScript
const sdkMinorApiVersion: number
```

Starting from API version 26.0.0, the minor version is introduced as part of semantic versioning. It is the middle field in the semantic version and is an integer. The complete API version is represented by sdkApiVersion.sdkMinorApiVersion.sdkPatchApiVersion.

Example: If the API version of the system software is 26.0.1, sdkMinorApiVersion is 0. If the API version of the system software is 26.1.0, sdkMinorApiVersion is 1.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Startup.SystemInfo

## sdkPatchApiVersion

```TypeScript
const sdkPatchApiVersion: number
```

Starting from API version 26.0.0, the patch version is introduced as part of semantic versioning. It is the third field in the semantic version and is an integer. The complete API version is represented by sdkApiVersion.sdkMinorApiVersion.sdkPatchApiVersion.

Example: If the API version of the system software is 26.0.1, sdkPatchApiVersion is 1. If the API version of the system software is 26.1.0, sdkPatchApiVersion is 0.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Startup.SystemInfo

## securityPatchTag

```TypeScript
const securityPatchTag: string
```

Security patch tag.

Example: &lt;!--RP7--&gt;2021/01/01&lt;!--RP7End--&gt;

**Type:** string

**Since:** 6

**System capability:** SystemCapability.Startup.SystemInfo

## seniorVersion

```TypeScript
const seniorVersion: number
```

Senior version number, which increments with architecture and feature updates. The value is the second digit in **osFullName**. You are advised to use **deviceInfo.seniorVersion** instead of parsing **osFullName** to obtain the value, facilitating efficiency improvement.

Example: 0

**Type:** number

**Since:** 6

**System capability:** SystemCapability.Startup.SystemInfo

## serial

```TypeScript
const serial: string
```

Serial number of the device. This API will start a temporary process during execution. When the system load is high, blocking may occur. To ensure the response of the main thread of your application, you are advised not to call this API in the main thread. This value varies depending on the device and is fixed. To improve performance, you can store this information on a local device after obtaining it for the first time..

**NOTE:** 

The device SN can be used as the unique identifier of a device.

**Required permission**: ohos.permission.sec.ACCESS_UDID (for system applications and enterprise applications only)

Example: The SN varies with the device.

**Type:** string

**Since:** 6

**Required permissions:** ohos.permission.sec.ACCESS_UDID

**System capability:** SystemCapability.Startup.SystemInfo

## softwareModel

```TypeScript
const softwareModel: string
```

Software model.

Example: &lt;!--RP5--&gt;TAS-AL00&lt;!--RP5End--&gt;

**Type:** string

**Since:** 6

**System capability:** SystemCapability.Startup.SystemInfo

## udid

```TypeScript
const udid: string
```

UDID of the device. This API will start a temporary process during execution. When the system load is high, blocking may occur. To ensure the response of the main thread of your application, you are advised not to call this API in the main thread. This value varies depending on the device and is fixed. To improve performance, you can store this information on a local device after obtaining it for the first time.

**NOTE:** 

The data length is 65 bytes. The UDID can be used as the unique identifier of a device.

**Required permission**: ohos.permission.sec.ACCESS_UDID (for system applications and enterprise applications only)

Example: 9D6AABD147XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXE5536412

**Type:** string

**Since:** 7

**Required permissions:** ohos.permission.sec.ACCESS_UDID

**System capability:** SystemCapability.Startup.SystemInfo

## versionId

```TypeScript
const versionId: string
```

Version ID, which is a concatenation of **deviceType**, **manufacture**, **brand**, **productSeries**, **osFullName**, **productModel**, **softwareModel**, **sdkApiVersion**, **incrementalVersion**, and **buildType**. To obtain a specific field value, you are advised to use the corresponding field directly (such as **deviceType** and **manufacture**) instead of parsing **versionId**, facilitating efficiency improvement.

**Type:** string

**Since:** 6

**System capability:** SystemCapability.Startup.SystemInfo
