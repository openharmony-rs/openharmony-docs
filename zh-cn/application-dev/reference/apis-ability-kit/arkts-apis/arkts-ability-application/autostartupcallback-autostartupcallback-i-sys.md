# AutoStartupCallback（系统接口）

应用设置为开机自启动时的回调函数。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-unnamed-export interface AutoStartupCallback--><!--Device-unnamed-export interface AutoStartupCallback-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## onAutoStartupOff

```TypeScript
onAutoStartupOff(info: AutoStartupInfo): void
```

取消应用开机自启动时调用。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AutoStartupCallback-onAutoStartupOff(info: AutoStartupInfo): void--><!--Device-AutoStartupCallback-onAutoStartupOff(info: AutoStartupInfo): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 取消开机自启动的应用组件信息。 |

## onAutoStartupOn

```TypeScript
onAutoStartupOn(info: AutoStartupInfo): void
```

应用设置为开机自启动时调用。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AutoStartupCallback-onAutoStartupOn(info: AutoStartupInfo): void--><!--Device-AutoStartupCallback-onAutoStartupOn(info: AutoStartupInfo): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 设置为开机自启动的应用组件信息。 |

