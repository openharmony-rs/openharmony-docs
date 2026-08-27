# ProcessInformation

运行进程信息，可以通过appManager的 [getRunningProcessInformation](arkts-ability-appmanager-getrunningprocessinformation-f.md)来获取运行进程信息 。

> **说明：**
> 
> 本模块首批接口从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
## 导入模块  
```ts
import { appManager } from '@kit.AbilityKit';
```

**起始版本：** 9

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## appCloneIndex

```TypeScript
appCloneIndex?: number
```

分身应用索引，用于标识不同的分身应用实例。0表示主应用，正整数表示对应的分身实例索引。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## bundleNames

```TypeScript
bundleNames: Array<string>
```

进程中所有运行的Bundle名称。

**类型：** Array&lt;string&gt;

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## bundleType

```TypeScript
bundleType: bundleManager.BundleType
```

当前进程运行的包类型。

**类型：** bundleManager.BundleType

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## isPreload

```TypeScript
isPreload?: boolean
```

进程是否为预加载。当进程是预加载且还未被某个组件启动请求所使用时为true；反之为false。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## pid

```TypeScript
pid: number
```

进程ID。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## processName

```TypeScript
processName: string
```

进程名称。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## state

```TypeScript
state: appManager.ProcessState
```

当前进程运行状态。

**类型：** appManager.ProcessState

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## uid

```TypeScript
uid: number
```

应用程序的UID。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core
