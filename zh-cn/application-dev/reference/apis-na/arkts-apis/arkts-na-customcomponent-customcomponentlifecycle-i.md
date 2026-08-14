# CustomComponentLifecycle

CustomComponentLifecycle用于监控自定义组件生命周期的变化，开发者可以通过 [UIUtils.getLifecycle](../../apis-arkui/arkts-apis/arkts-arkui-arkui-statemanagement-uiutils-c.md#getLifecycle)获取CustomComponentLifecycle实例。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

<!--Device-unnamed-export declare interface CustomComponentLifecycle--><!--Device-unnamed-export declare interface CustomComponentLifecycle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## addObserver

```TypeScript
addObserver(observer: CustomComponentLifecycleObserver): void
```

addObserver函数用于注册自定义组件生命周期监听器。当自定义组件的生命周期发生变化时，会触发监听器中相应的生命周期回调函数。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomComponentLifecycle-addObserver(observer: CustomComponentLifecycleObserver): void--><!--Device-CustomComponentLifecycle-addObserver(observer: CustomComponentLifecycleObserver): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| observer | [CustomComponentLifecycleObserver](arkts-na-customcomponent-customcomponentlifecycleobserver-i.md) | 是 | 监听自定义组件的监听器。 |

## getCurrentState

```TypeScript
getCurrentState(): CustomComponentLifecycleState
```

getCurrentState函数用于获得自定义组件当前的生命周期状态。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomComponentLifecycle-getCurrentState(): CustomComponentLifecycleState--><!--Device-CustomComponentLifecycle-getCurrentState(): CustomComponentLifecycleState-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CustomComponentLifecycleState](arkts-na-customcomponent-customcomponentlifecyclestate-e.md) | 自定义组件当前的生命周期状态。 |

## removeObserver

```TypeScript
removeObserver(observer: CustomComponentLifecycleObserver): void
```

removeObserver函数用于移除自定义组件生命周期监听器。解除注册后，即使自定义组件的生命周期状态发生变化，也不会触发监听器中相应的生命周期回调函数。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomComponentLifecycle-removeObserver(observer: CustomComponentLifecycleObserver): void--><!--Device-CustomComponentLifecycle-removeObserver(observer: CustomComponentLifecycleObserver): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| observer | [CustomComponentLifecycleObserver](arkts-na-customcomponent-customcomponentlifecycleobserver-i.md) | 是 | 监听自定义组件的监听器。 |

