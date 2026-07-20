# AutoStartupCallback（系统接口）

应用设置为开机自启动时的回调函数。

**起始版本：** 11

<!--Device-unnamed-export interface AutoStartupCallback--><!--Device-unnamed-export interface AutoStartupCallback-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

<a id="onautostartupoff"></a>
## onAutoStartupOff

```TypeScript
onAutoStartupOff(info: AutoStartupInfo): void
```

取消应用开机自启动时调用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AutoStartupCallback-onAutoStartupOff(info: AutoStartupInfo): void--><!--Device-AutoStartupCallback-onAutoStartupOff(info: AutoStartupInfo): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [AutoStartupInfo](arkts-ability-common-autostartupinfo-t-sys.md) | 是 | 取消开机自启动的应用组件信息。 |

<a id="onautostartupon"></a>
## onAutoStartupOn

```TypeScript
onAutoStartupOn(info: AutoStartupInfo): void
```

应用设置为开机自启动时调用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AutoStartupCallback-onAutoStartupOn(info: AutoStartupInfo): void--><!--Device-AutoStartupCallback-onAutoStartupOn(info: AutoStartupInfo): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [AutoStartupInfo](arkts-ability-common-autostartupinfo-t-sys.md) | 是 | 设置为开机自启动的应用组件信息。 |

