# AppProvisionInfo (System API)

```TypeScript
export interface AppProvisionInfo
```

The module provides information in the [HarmonyAppProvision configuration file](../../../security/app-provision-structure.md).

**Since:** 10

<!--Device-unnamed-export interface AppProvisionInfo--><!--Device-unnamed-export interface AppProvisionInfo-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## additionalInfo

```TypeScript
readonly additionalInfo?: string
```

Additional of the application.

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-AppProvisionInfo-readonly additionalInfo?: string--><!--Device-AppProvisionInfo-readonly additionalInfo?: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## apl

```TypeScript
readonly apl: string
```

APL in the configuration file, which can be **normal**, **system_basic**, or **system_core**.

**Type:** string

**Since:** 10

<!--Device-AppProvisionInfo-readonly apl: string--><!--Device-AppProvisionInfo-readonly apl: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## appDistributionType

```TypeScript
readonly appDistributionType: string
```

[Distribution type](../../../security/app-provision-structure.md) in the configuration file.

**Type:** string

**Since:** 10

<!--Device-AppProvisionInfo-readonly appDistributionType: string--><!--Device-AppProvisionInfo-readonly appDistributionType: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## appIdentifier

```TypeScript
readonly appIdentifier: string
```

Unique ID of the application. For details, see [What Is appIdentifier](../../../quick-start/common_problem_of_application.md#what-is-appidentifier).

**Type:** string

**Since:** 11

<!--Device-AppProvisionInfo-readonly appIdentifier: string--><!--Device-AppProvisionInfo-readonly appIdentifier: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## appIndex

```TypeScript
readonly appIndex?: number
```

Index of the application.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-AppProvisionInfo-readonly appIndex?: int--><!--Device-AppProvisionInfo-readonly appIndex?: int-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## appServiceCapabilities

```TypeScript
readonly appServiceCapabilities?: string
```

ServiceCapabilities of the application.

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-AppProvisionInfo-readonly appServiceCapabilities?: string--><!--Device-AppProvisionInfo-readonly appServiceCapabilities?: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## bundleName

```TypeScript
readonly bundleName?: string
```

Bundle name of the application.

**Type:** string

**Since:** 23

<!--Device-AppProvisionInfo-readonly bundleName?: string--><!--Device-AppProvisionInfo-readonly bundleName?: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## certificate

```TypeScript
readonly certificate: string
```

Certificate information in the configuration file.

**Type:** string

**Since:** 10

<!--Device-AppProvisionInfo-readonly certificate: string--><!--Device-AppProvisionInfo-readonly certificate: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## developerId

```TypeScript
readonly developerId: string
```

Developer ID in the configuration file.

**Type:** string

**Since:** 10

<!--Device-AppProvisionInfo-readonly developerId: string--><!--Device-AppProvisionInfo-readonly developerId: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## issuer

```TypeScript
readonly issuer: string
```

Issuer name in the configuration file.

**Type:** string

**Since:** 10

<!--Device-AppProvisionInfo-readonly issuer: string--><!--Device-AppProvisionInfo-readonly issuer: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## organization

```TypeScript
readonly organization: string
```

Organization of the application.

**Type:** string

**Since:** 12

<!--Device-AppProvisionInfo-readonly organization: string--><!--Device-AppProvisionInfo-readonly organization: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## specifiedDistributionType

```TypeScript
readonly specifiedDistributionType?: string
```

Specified distribution type of the application.

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-AppProvisionInfo-readonly specifiedDistributionType?: string--><!--Device-AppProvisionInfo-readonly specifiedDistributionType?: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## type

```TypeScript
readonly type: string
```

Type of the configuration file, which can be **debug** or **release**.

**Type:** string

**Since:** 10

<!--Device-AppProvisionInfo-readonly type: string--><!--Device-AppProvisionInfo-readonly type: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## uuid

```TypeScript
readonly uuid: string
```

UUID in the configuration file.

**Type:** string

**Since:** 10

<!--Device-AppProvisionInfo-readonly uuid: string--><!--Device-AppProvisionInfo-readonly uuid: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## validity

```TypeScript
readonly validity: Validity
```

Validity period in the configuration file.

**Type:** [Validity](arkts-ability-appprovisioninfo-validity-i-sys.md)

**Since:** 10

<!--Device-AppProvisionInfo-readonly validity: Validity--><!--Device-AppProvisionInfo-readonly validity: Validity-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## versionCode

```TypeScript
readonly versionCode: number
```

Version number of the configuration file.

**Type:** number

**Since:** 10

<!--Device-AppProvisionInfo-readonly versionCode: long--><!--Device-AppProvisionInfo-readonly versionCode: long-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## versionName

```TypeScript
readonly versionName: string
```

Version name of the configuration file.

**Type:** string

**Since:** 10

<!--Device-AppProvisionInfo-readonly versionName: string--><!--Device-AppProvisionInfo-readonly versionName: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.
