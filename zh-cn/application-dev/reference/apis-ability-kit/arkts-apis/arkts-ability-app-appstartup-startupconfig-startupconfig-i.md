# StartupConfig

本模块提供[应用启动框架](../../../application-models/app-startup.md)配置信息的定义。

**起始版本：** 12

**系统能力：** SystemCapability.Ability.AppStartup

## 导入模块

```TypeScript
import { StartupConfig } from '@kit.AbilityKit';
```

## startupListener

```TypeScript
startupListener?: StartupListener
```

启动框架的监听器，该监听器将在所有启动任务完成时调用。未设置该参数时，不进行回调通知。

**类型：** [StartupListener](arkts-ability-app-appstartup-startuplistener-startuplistener-c.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AppStartup

## timeoutMs

```TypeScript
timeoutMs?: number
```

执行所有启动任务的超时时间（单位：ms），默认值为10000ms。超时后启动框架会停止等待，并通过startupListener.onCompleted回调返回超时错误。超时不会中断正在执行的启动任务，但会影响后续任务的执行。

**类型：** number

**默认值：** 10000

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AppStartup
