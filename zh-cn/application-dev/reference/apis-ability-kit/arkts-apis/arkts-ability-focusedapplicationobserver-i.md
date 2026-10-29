# FocusedApplicationObserver

```TypeScript
declare interface FocusedApplicationObserver
```

定义用于监听获焦应用变化的观察者。可以作为[appManager.onFocusedApplicationChanged](arkts-ability-appmanager-onfocusedapplicationchanged-f.md)的入参监听获焦应用变化。

**起始版本：** 26.1.0

<!--Device-unnamed-declare interface FocusedApplicationObserver--><!--Device-unnamed-declare interface FocusedApplicationObserver-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## onFocusedApplicationChanged

```TypeScript
onFocusedApplicationChanged(info: FocusedApplicationInfo): void
```

获焦应用发生变化时调用。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FocusedApplicationObserver-onFocusedApplicationChanged(info: FocusedApplicationInfo): void--><!--Device-FocusedApplicationObserver-onFocusedApplicationChanged(info: FocusedApplicationInfo): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [FocusedApplicationInfo](arkts-ability-focusedapplicationinfo-i.md) | 是 | 获焦应用信息。 |
