# CustomComponentLifecycle

CustomComponentLifecycle用于监控自定义组件生命周期的变化， 开发者可以通过[UIUtils.getLifecycle]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_获取CustomComponentLifecycle实例。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

<!--Device-unnamed-export declare interface CustomComponentLifecycle--><!--Device-unnamed-export declare interface CustomComponentLifecycle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## addObserver

```TypeScript
addObserver(observer: CustomComponentLifecycleObserver): void
```

addObserver函数用于注册自定义组件生命周期监听器。调用此方法前， 需先通过[UIUtils.getLifecycle]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_获取CustomComponentLifecycle实例。 当自定义组件的生命周期发生变化时，会触发监听器中相应的生命周期回调函数。 调用addObserver注册监听器后，必须在组件销毁或不再需要监听时调用[removeObserver]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_移除监听器，两者需成对使用。 若未调用removeObserver移除监听器，可能导致监听器持续触发回调并引发内存泄漏。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-CustomComponentLifecycle-addObserver(observer: CustomComponentLifecycleObserver): void--><!--Device-CustomComponentLifecycle-addObserver(observer: CustomComponentLifecycleObserver): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| observer | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 自定义组件生命周期的监听器。 |

## getCurrentState

```TypeScript
getCurrentState(): CustomComponentLifecycleState
```

getCurrentState函数用于获取自定义组件当前的生命周期状态。调用此方法前， 需先通过[UIUtils.getLifecycle]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_获取CustomComponentLifecycle实例。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-CustomComponentLifecycle-getCurrentState(): CustomComponentLifecycleState--><!--Device-CustomComponentLifecycle-getCurrentState(): CustomComponentLifecycleState-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | - 自定义组件当前的生命周期状态。 |

## removeObserver

```TypeScript
removeObserver(observer: CustomComponentLifecycleObserver): void
```

removeObserver函数用于移除自定义组件生命周期监听器。调用此方法前， 需先通过[UIUtils.getLifecycle]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_获取CustomComponentLifecycle实例。解除注册后，即使自定义组件的生命周期状态发生变化， 也不会触发监听器中相应的生命周期回调函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-CustomComponentLifecycle-removeObserver(observer: CustomComponentLifecycleObserver): void--><!--Device-CustomComponentLifecycle-removeObserver(observer: CustomComponentLifecycleObserver): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| observer | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 自定义组件生命周期的监听器。 |

