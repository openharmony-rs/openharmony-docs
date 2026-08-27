# ProcessData

进程数据的对象定义。使用接口 [appManager.on('applicationState')](arkts-ability-appmanager-on-f.md#onapplicationstate) 注册生命周期变化监听后，当应用或组件的生命周期变化时，系统通过ApplicationStateObserver的 [onProcessCreated](../../../reference/apis-ability-kit/js-apis-inner-application-applicationStateObserver.md#applicationstateobserveronprocesscreated) 等方法回调给开发者。

> **说明：**
> 
> 本模块首批接口从API version 14开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
## 导入模块  
```ts
import { appManager } from '@kit.AbilityKit';
```

**起始版本：** 14

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## bundleName

```TypeScript
bundleName: string
```

应用包名。

**类型：** string

**起始版本：** 14

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## isContinuousTask

```TypeScript
isContinuousTask: boolean
```

是否为长时任务，true表示是，false表示不是。

**类型：** boolean

**起始版本：** 14

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## isKeepAlive

```TypeScript
isKeepAlive: boolean
```

是否为常驻进程，true表示是，false表示不是。

**类型：** boolean

**起始版本：** 14

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## pid

```TypeScript
pid: number
```

进程ID。

**类型：** number

**起始版本：** 14

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## state

```TypeScript
state: number
```

进程的状态，取值及对应的状态为：0 - 初始化状态，进程正在初始化，1 - 就绪状态，进程已初始化完毕，2 - 前台，4 - 后台，5 - 已终止。

**类型：** number

**起始版本：** 14

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## uid

```TypeScript
uid: number
```

应用的uid。

**类型：** number

**起始版本：** 14

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core
