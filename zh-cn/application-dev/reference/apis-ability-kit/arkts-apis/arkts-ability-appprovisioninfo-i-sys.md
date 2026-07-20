# AppProvisionInfo（系统接口）

应用[HarmonyAppProvision配置文件](docroot://security/app-provision-structure.md)中的信息。

**起始版本：** 10

<!--Device-unnamed-export interface AppProvisionInfo--><!--Device-unnamed-export interface AppProvisionInfo-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## apl

```TypeScript
readonly apl: string
```

配置文件中的apl字段，为normal、system_basic和system_core其中之一。

**类型：** string

**起始版本：** 10

<!--Device-AppProvisionInfo-readonly apl: string--><!--Device-AppProvisionInfo-readonly apl: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## appDistributionType

```TypeScript
readonly appDistributionType: string
```

配置文件中的[分发类型](docroot://security/app-provision-structure.md)。

**类型：** string

**起始版本：** 10

<!--Device-AppProvisionInfo-readonly appDistributionType: string--><!--Device-AppProvisionInfo-readonly appDistributionType: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## appIdentifier

```TypeScript
readonly appIdentifier: string
```

应用的唯一标识，详情信息可参考[什么是appIdentifier](docroot://quick-start/common-problem-of-application.md#什么是appidentifier)。

**类型：** string

**起始版本：** 11

<!--Device-AppProvisionInfo-readonly appIdentifier: string--><!--Device-AppProvisionInfo-readonly appIdentifier: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## bundleName

```TypeScript
readonly bundleName?: string
```

应用的包名。

**类型：** string

**起始版本：** 23

<!--Device-AppProvisionInfo-readonly bundleName?: string--><!--Device-AppProvisionInfo-readonly bundleName?: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## certificate

```TypeScript
readonly certificate: string
```

配置文件中的证书信息。

**类型：** string

**起始版本：** 10

<!--Device-AppProvisionInfo-readonly certificate: string--><!--Device-AppProvisionInfo-readonly certificate: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## developerId

```TypeScript
readonly developerId: string
```

配置文件中的开发者ID。

**类型：** string

**起始版本：** 10

<!--Device-AppProvisionInfo-readonly developerId: string--><!--Device-AppProvisionInfo-readonly developerId: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## issuer

```TypeScript
readonly issuer: string
```

配置文件中的发行者名称。

**类型：** string

**起始版本：** 10

<!--Device-AppProvisionInfo-readonly issuer: string--><!--Device-AppProvisionInfo-readonly issuer: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## organization

```TypeScript
readonly organization: string
```

应用的组织信息。

**类型：** string

**起始版本：** 12

<!--Device-AppProvisionInfo-readonly organization: string--><!--Device-AppProvisionInfo-readonly organization: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## type

```TypeScript
readonly type: string
```

配置文件的类型，为debug或release。

**类型：** string

**起始版本：** 10

<!--Device-AppProvisionInfo-readonly type: string--><!--Device-AppProvisionInfo-readonly type: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## uuid

```TypeScript
readonly uuid: string
```

配置文件中的uuid。

**类型：** string

**起始版本：** 10

<!--Device-AppProvisionInfo-readonly uuid: string--><!--Device-AppProvisionInfo-readonly uuid: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## validity

```TypeScript
readonly validity: Validity
```

配置文件中的有效期。

**类型：** Validity

**起始版本：** 10

<!--Device-AppProvisionInfo-readonly validity: Validity--><!--Device-AppProvisionInfo-readonly validity: Validity-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## versionCode

```TypeScript
readonly versionCode: number
```

配置文件的版本号。

**类型：** number

**起始版本：** 10

<!--Device-AppProvisionInfo-readonly versionCode: long--><!--Device-AppProvisionInfo-readonly versionCode: long-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## versionName

```TypeScript
readonly versionName: string
```

配置文件的版本名称。

**类型：** string

**起始版本：** 10

<!--Device-AppProvisionInfo-readonly versionName: string--><!--Device-AppProvisionInfo-readonly versionName: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

