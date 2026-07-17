# Package

系统更新包详情。

**起始版本：** 12

<!--Device-systemManager-interface Package--><!--Device-systemManager-interface Package-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 导入模块

```TypeScript
import { systemManager } from '@kit.MDMKit';
```

## fd

```TypeScript
fd?: number
```

系统更新包文件句柄。当前不支持只传入path参数，需要传入fd。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Package-fd?: number--><!--Device-Package-fd?: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## path

```TypeScript
path: string
```

系统更新包文件路径。若传入fd参数，该参数传入更新包文件名。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Package-path: string--><!--Device-Package-path: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## type

```TypeScript
type: PackageType
```

系统更新包类型。

**类型：** PackageType

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Package-type: PackageType--><!--Device-Package-type: PackageType-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

