# HyperSnapErrorInfo

描述Hyper Snap的错误信息。

**起始版本：** 26.1.0

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { hyperSnapManager } from '@kit.AbilityKit';
```

## code

```TypeScript
code: HyperSnapErrorCode
```

错误码。

**类型：** [HyperSnapErrorCode](arkts-ability-hypersnapmanager-hypersnaperrorcode-e.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## msg

```TypeScript
msg: string
```

错误消息。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## occurTimeStamp

```TypeScript
occurTimeStamp: number
```

自发生错误时Unix历元以来经过的时间。单位为：毫秒。取值限定为整数。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core
