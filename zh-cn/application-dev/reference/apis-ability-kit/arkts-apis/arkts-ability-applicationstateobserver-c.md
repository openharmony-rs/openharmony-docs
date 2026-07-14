# ApplicationStateObserver

应用状态监听器，可以作为入参传入
[on('applicationState')](arkts-ability-on-f.md#on-1)
方法，监听应用的生命周期变化。

**起始版本：** 14

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## onAbilityStateChanged

```TypeScript
onAbilityStateChanged(abilityStateData: AbilityStateData): void
```

Ability状态发生变化时执行的回调函数。

**起始版本：** 14

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| abilityStateData | AbilityStateData | 是 | Ability状态信息。 |

## onAppStarted

```TypeScript
onAppStarted(appStateData: AppStateData): void
```

应用第一个进程创建时执行的回调函数。

**起始版本：** 14

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appStateData | AppStateData | 是 | 应用状态信息。 |

## onAppStopped

```TypeScript
onAppStopped(appStateData: AppStateData): void
```

应用最后一个进程销毁时执行的回调函数。

**起始版本：** 14

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appStateData | AppStateData | 是 | 应用状态信息。 |

## onForegroundApplicationChanged

```TypeScript
onForegroundApplicationChanged(appStateData: AppStateData): void
```

应用前后台状态发生变化时执行的回调函数。

**起始版本：** 14

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appStateData | AppStateData | 是 | 应用状态信息。 |

## onProcessCreated

```TypeScript
onProcessCreated(processData: ProcessData): void
```

进程创建时执行的回调函数。

**起始版本：** 14

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| processData | ProcessData | 是 | 进程数据信息。 |

## onProcessDied

```TypeScript
onProcessDied(processData: ProcessData): void
```

进程销毁时执行的回调函数。

**起始版本：** 14

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| processData | ProcessData | 是 | 进程数据信息。 |

## onProcessStateChanged

```TypeScript
onProcessStateChanged(processData: ProcessData): void
```

进程状态更新时执行的回调函数。

**起始版本：** 14

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| processData | ProcessData | 是 | 进程数据信息。 |

