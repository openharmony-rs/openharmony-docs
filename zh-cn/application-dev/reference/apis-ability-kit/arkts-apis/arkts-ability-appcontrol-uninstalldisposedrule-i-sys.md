# UninstallDisposedRule（系统接口）

标识卸载处置规则。

**起始版本：** 15

<!--Device-appControl-export interface UninstallDisposedRule--><!--Device-appControl-export interface UninstallDisposedRule-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { appControl } from '@kit.AbilityKit';
```

## priority

```TypeScript
priority: number
```

拦截规则的优先级，用于规则列表查询结果排序。取值为整数，数值越小，优先级越高，排序越靠前。

**类型：** number

**起始版本：** 15

<!--Device-UninstallDisposedRule-priority: int--><!--Device-UninstallDisposedRule-priority: int-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。

## uninstallComponentType

```TypeScript
uninstallComponentType: UninstallComponentType
```

拦截时将拉起能力的类型。

**类型：** UninstallComponentType

**起始版本：** 15

<!--Device-UninstallDisposedRule-uninstallComponentType: UninstallComponentType--><!--Device-UninstallDisposedRule-uninstallComponentType: UninstallComponentType-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。

## want

```TypeScript
want: Want
```

指定应用被拦截时，跳转到的组件。

**类型：** Want

**起始版本：** 15

<!--Device-UninstallDisposedRule-want: Want--><!--Device-UninstallDisposedRule-want: Want-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。

