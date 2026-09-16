# CustomComponentLifecycle

CustomComponentLifecycle用于监控自定义组件生命周期的变化，开发者可以通过[UIUtils.getLifecycle](arkts-arkui-arkui-statemanagement-uiutils-c.md#getlifecycle)获取CustomComponentLifecycle实例。

**起始版本：** 23

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AppStorageV2, PersistenceV2, Type, UIUtils, ConnectOptions, Binding, MutableBinding, CustomComponentLifecycle, CustomComponentLifecycleObserver, CustomComponentLifecycleState, ComponentInit, ComponentAppear, ComponentBuilt, ComponentReuse, ComponentActive, ComponentInactive, ComponentRecycle, ComponentDisappear, CollectionType, ConnectOptionsCollections, CustomComponentContext, IReusePool, IReusableInfo, StorageDefaultCreator, TypeConstructorWithArgs, PersistenceErrorCallback, TypeConstructor, TypeDecorator, MonitorCallback, MonitorOptions, GetterCallback, SetterCallback, ObservedResult, DecoratorInfo, ElementInfo } from '@kit.ArkUI';
```

## addObserver

```TypeScript
addObserver(observer: CustomComponentLifecycleObserver): void
```

addObserver函数用于注册自定义组件生命周期监听器。调用此方法前，需先通过[UIUtils.getLifecycle](arkts-arkui-arkui-statemanagement-uiutils-c.md#getlifecycle)获取CustomComponentLifecycle实例。当自定义组件的生命周期发生变化时，会触发监听器中相应的生命周期回调函数。

调用addObserver注册监听器后，必须在组件销毁或不再需要监听时调用[removeObserver](#removeobserver)移除监听器，两者需成对使用。若未调用removeObserver移除监听器，可能导致监听器持续触发回调并引发内存泄漏。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| observer | [CustomComponentLifecycleObserver](arkts-arkui-arkui-statemanagement-customcomponentlifecycleobserver-i.md) | 是 | 自定义组件生命周期的监听器。 |

## getCurrentState

```TypeScript
getCurrentState(): CustomComponentLifecycleState
```

getCurrentState函数用于获取自定义组件当前的生命周期状态。调用此方法前，需先通过[UIUtils.getLifecycle](arkts-arkui-arkui-statemanagement-uiutils-c.md#getlifecycle)获取CustomComponentLifecycle实例。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CustomComponentLifecycleState](arkts-arkui-arkui-statemanagement-customcomponentlifecyclestate-e.md) | 自定义组件当前的生命周期状态。 |

**示例**

```TypeScript
import { UIUtils, ComponentBuilt } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';
@Entry
@Component
struct Index {
  @ComponentBuilt
  myBuilt() {
    // CustomComponentLifecycle.getCurrentState用于获得自定义组件当前的生命周期状态
    hilog.info(0x0000, 'testTag', 'Index Lifecycle is %{public}d', UIUtils.getLifecycle(this).getCurrentState());
  }
  build() {
    Column() {
      Text(`HelloWorld`)
    }
    .height('100%')
    .width('100%')
  }
}
```

## removeObserver

```TypeScript
removeObserver(observer: CustomComponentLifecycleObserver): void
```

removeObserver函数用于移除自定义组件生命周期监听器。调用此方法前，需先通过[UIUtils.getLifecycle](arkts-arkui-arkui-statemanagement-uiutils-c.md#getlifecycle)获取CustomComponentLifecycle实例。解除注册后，即使自定义组件的生命周期状态发生变化，也不会触发监听器中相应的生命周期回调函数。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| observer | [CustomComponentLifecycleObserver](arkts-arkui-arkui-statemanagement-customcomponentlifecycleobserver-i.md) | 是 | 自定义组件生命周期的监听器。 |
