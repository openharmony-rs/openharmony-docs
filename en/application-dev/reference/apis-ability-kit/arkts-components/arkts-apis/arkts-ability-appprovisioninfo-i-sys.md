# AppProvisionInfo (System API)

The module provides information in the [HarmonyAppProvision configuration file](../../../security/app-provision-structure.md).

**Since:** 10

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## additionalInfo

```TypeScript
readonly additionalInfo?: string
```

Additional of the application.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## apl

```TypeScript
readonly apl: string
```

APL in the configuration file, which can be **normal**, **system_basic**, or **system_core**.

**Type:** string

**Since:** 10

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## appDistributionType

```TypeScript
readonly appDistributionType: string
```

[Distribution type](../../../security/app-provision-structure.md) in the configuration file.

**Type:** string

**Since:** 10

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## appIdentifier

```TypeScript
readonly appIdentifier: string
```

Unique ID of the application. For details, see [What Is appIdentifier](../../../quick-start/common_problem_of_application.md#what-is-appidentifier).

**Type:** string

**Since:** 11

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## appIndex

```TypeScript
readonly appIndex?: number
```

Index of the application.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## appServiceCapabilities

```TypeScript
readonly appServiceCapabilities?: string
```

ServiceCapabilities of the application.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## bundleName

```TypeScript
readonly bundleName?: string
```

Bundle name of the application.

**Type:** string

**Since:** 23

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## certificate

```TypeScript
readonly certificate: string
```

Certificate information in the configuration file.

**Type:** string

**Since:** 10

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## developerId

```TypeScript
readonly developerId: string
```

Developer ID in the configuration file.

**Type:** string

**Since:** 10

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## issuer

```TypeScript
readonly issuer: string
```

Issuer name in the configuration file.

**Type:** string

**Since:** 10

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## organization

```TypeScript
readonly organization: string
```

Organization of the application.

**Type:** string

**Since:** 12

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## specifiedDistributionType

```TypeScript
readonly specifiedDistributionType?: string
```

Specified distribution type of the application.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## type

```TypeScript
readonly type: string
```

Type of the configuration file, which can be **debug** or **release**.

**Type:** string

**Since:** 10

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## uuid

```TypeScript
readonly uuid: string
```

UUID in the configuration file.

**Type:** string

**Since:** 10

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## validity

```TypeScript
readonly validity: Validity
```

Validity period in the configuration file.

**Type:** [Validity](arkts-ability-appprovisioninfo-validity-i-sys.md)

**Since:** 10

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## versionCode

```TypeScript
readonly versionCode: number
```

Version number of the configuration file.

**Type:** number

**Since:** 10

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## versionName

```TypeScript
readonly versionName: string
```

Version name of the configuration file.

**Type:** string

**Since:** 10

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.
