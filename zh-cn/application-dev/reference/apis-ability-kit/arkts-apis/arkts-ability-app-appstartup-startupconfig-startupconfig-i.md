# StartupConfig

本模块提供[应用启动框架](../../../application-models/app-startup.md)配置信息的定义。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export default interface StartupConfig--><!--Device-unnamed-export default interface StartupConfig-End-->

**系统能力：** SystemCapability.Ability.AppStartup

## startupListener

```TypeScript
startupListener?: StartupListener
```

表示启动框架的监听器，该监听器将在所有启动任务完成时调用。

**类型：** [StartupListener](arkts-ability-app-appstartup-startuplistener-startuplistener-c.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StartupConfig-startupListener?: StartupListener--><!--Device-StartupConfig-startupListener?: StartupListener-End-->

**系统能力：** SystemCapability.Ability.AppStartup

## timeoutMs

```TypeScript
timeoutMs?: int
```

执行所有启动任务的超时时间（单位：毫秒），默认值为10000毫秒。

**类型：** int

**默认值：** 10000

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StartupConfig-timeoutMs?: int--><!--Device-StartupConfig-timeoutMs?: int-End-->

**系统能力：** SystemCapability.Ability.AppStartup

