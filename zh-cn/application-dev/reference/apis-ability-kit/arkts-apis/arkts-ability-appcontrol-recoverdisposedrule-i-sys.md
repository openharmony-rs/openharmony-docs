# RecoverDisposedRule（系统接口）

```TypeScript
export interface RecoverDisposedRule
```

描述应用恢复处置规则。

**起始版本：** 26.1.0

<!--Device-appControl-export interface RecoverDisposedRule--><!--Device-appControl-export interface RecoverDisposedRule-End-->

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

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RecoverDisposedRule-priority: int--><!--Device-RecoverDisposedRule-priority: int-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。

## recoverComponentType

```TypeScript
recoverComponentType: RecoverComponentType
```

拦截时将拉起能力的类型。

**类型：** [RecoverComponentType](arkts-ability-appcontrol-recovercomponenttype-e-sys.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RecoverDisposedRule-recoverComponentType: RecoverComponentType--><!--Device-RecoverDisposedRule-recoverComponentType: RecoverComponentType-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。

## want

```TypeScript
want: Want
```

指定应用被处置时展示的组件。

**类型：** [Want](arkts-ability-app-ability-want-want-c.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RecoverDisposedRule-want: Want--><!--Device-RecoverDisposedRule-want: Want-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。
