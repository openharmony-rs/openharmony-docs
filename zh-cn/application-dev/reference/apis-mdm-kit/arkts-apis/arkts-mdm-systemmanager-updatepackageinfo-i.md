# UpdatePackageInfo

系统更新包信息。

**起始版本：** 12

<!--Device-systemManager-export interface UpdatePackageInfo--><!--Device-systemManager-export interface UpdatePackageInfo-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 导入模块

```TypeScript
import { systemManager } from '@kit.MDMKit';
```

## authInfo

```TypeScript
authInfo?: string
```

系统更新包的鉴权信息。

**类型：** string

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UpdatePackageInfo-authInfo?: string--><!--Device-UpdatePackageInfo-authInfo?: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## description

```TypeScript
description?: PackageDescription
```

系统更新包描述信息。

**类型：** PackageDescription

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UpdatePackageInfo-description?: PackageDescription--><!--Device-UpdatePackageInfo-description?: PackageDescription-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## packages

```TypeScript
packages: Array<Package>
```

系统更新包详情。

**类型：** Array&lt;Package&gt;

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UpdatePackageInfo-packages: Array<Package>--><!--Device-UpdatePackageInfo-packages: Array<Package>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## version

```TypeScript
version: string
```

系统更新包版本号。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UpdatePackageInfo-version: string--><!--Device-UpdatePackageInfo-version: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

