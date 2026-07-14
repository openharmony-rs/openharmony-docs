# AppProvisionInfo（系统接口）

应用[HarmonyAppProvision配置文件](../../../../security/app-provision-structure.md)中的信息。

**起始版本：** 10

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## apl

```TypeScript
readonly apl: string
```

配置文件中的apl字段，为normal、system_basic和system_core其中之一。

**类型：** string

**起始版本：** 10

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## appDistributionType

```TypeScript
readonly appDistributionType: string
```

配置文件中的[分发类型](../../../../security/app-provision-structure.md)。

**类型：** string

**起始版本：** 10

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## appIdentifier

```TypeScript
readonly appIdentifier: string
```

应用的唯一标识，详情信息可参考[什么是appIdentifier](../../../../quick-start/common-problem-of-application.md#什么是appidentifier)。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## bundleName

```TypeScript
readonly bundleName?: string
```

应用的包名。

**类型：** string

**起始版本：** 23

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## certificate

```TypeScript
readonly certificate: string
```

配置文件中的证书信息。

**类型：** string

**起始版本：** 10

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## developerId

```TypeScript
readonly developerId: string
```

配置文件中的开发者ID。

**类型：** string

**起始版本：** 10

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## issuer

```TypeScript
readonly issuer: string
```

配置文件中的发行者名称。

**类型：** string

**起始版本：** 10

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## organization

```TypeScript
readonly organization: string
```

应用的组织信息。

**类型：** string

**起始版本：** 12

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## type

```TypeScript
readonly type: string
```

配置文件的类型，为debug或release。

**类型：** string

**起始版本：** 10

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## uuid

```TypeScript
readonly uuid: string
```

配置文件中的uuid。

**类型：** string

**起始版本：** 10

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## validity

```TypeScript
readonly validity: Validity
```

配置文件中的有效期。

**类型：** Validity

**起始版本：** 10

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## versionCode

```TypeScript
readonly versionCode: number
```

配置文件的版本号。

**类型：** number

**起始版本：** 10

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## versionName

```TypeScript
readonly versionName: string
```

配置文件的版本名称。

**类型：** string

**起始版本：** 10

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

