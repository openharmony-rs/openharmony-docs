# off

## 导入模块

```TypeScript
import { uiObserver } from '@kit.ArkUI';
```

## off('navDestinationUpdate')

```TypeScript
export function off(type: 'navDestinationUpdate', options: { navigationId: ResourceStr }, callback?: Callback<NavDestinationInfo>): void
```

取消监听NavDestination组件的状态变化。与[uiObserver.off](arkts-arkui-uiobserver-off-f.md#off-2)相比，新增了options参数，即支持指定监听的Navigation的id。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-uiObserver-export function off(type: 'navDestinationUpdate', options: { navigationId: ResourceStr }, callback?: Callback<NavDestinationInfo>): void--><!--Device-uiObserver-export function off(type: 'navDestinationUpdate', options: { navigationId: ResourceStr }, callback?: Callback<NavDestinationInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'navDestinationUpdate' | 是 | 监听事件，固定为'navDestinationUpdate'，即NavDestination组件的状态变化。 |
| options | { navigationId: ResourceStr } | 是 | 指定监听的Navigation的id。 |
| callback | [Callback](../arkts-components/arkts-arkui-common-callback-i.md)<NavDestinationInfo> | 否 | 回调函数。返回当前的NavDestination组件状态。 |


## off('navDestinationUpdate')

```TypeScript
export function off(type: 'navDestinationUpdate', callback?: Callback<NavDestinationInfo>): void
```

取消监听NavDestination组件的状态变化。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-uiObserver-export function off(type: 'navDestinationUpdate', callback?: Callback<NavDestinationInfo>): void--><!--Device-uiObserver-export function off(type: 'navDestinationUpdate', callback?: Callback<NavDestinationInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'navDestinationUpdate' | 是 | 监听事件，固定为'navDestinationUpdate'，即NavDestination组件的状态变化。 |
| callback | [Callback](../arkts-components/arkts-arkui-common-callback-i.md)<NavDestinationInfo> | 否 | 回调函数。返回当前的NavDestination组件状态。 |


## off('scrollEvent')

```TypeScript
export function off(type: 'scrollEvent', options: ObserverOptions, callback?: Callback<ScrollEventInfo>): void
```

Removes a callback function that was previously registered with `on()`.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-uiObserver-export function off(type: 'scrollEvent', options: ObserverOptions, callback?: Callback<ScrollEventInfo>): void--><!--Device-uiObserver-export function off(type: 'scrollEvent', options: ObserverOptions, callback?: Callback<ScrollEventInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'scrollEvent' | 是 | The type of event to remove the listener for. Must be 'scrollEvent'. |
| options | [ObserverOptions](arkts-arkui-uiobserver-observeroptions-i.md) | 是 | The options object. |
| callback | [Callback](../arkts-components/arkts-arkui-common-callback-i.md)<ScrollEventInfo> | 否 | The callback function to remove. If not provided, all callbacks for the given event type and scroll ID will be removed. |

**示例：**

```TypeScript
import { uiObserver } from '@kit.ArkUI'

@Entry
@Component
struct Index {
  scroller: Scroller = new Scroller();
  options: uiObserver.ObserverOptions = { id: 'testId' };
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7]

  build() {
    Column() {
      Column() {
        Scroll(this.scroller) {
          Column() {
            ForEach(this.arr, (item: number) => {
              Text(item.toString())
                .width('90%')
                .height(150)
                .backgroundColor(0xFFFFFF)
                .borderRadius(15)
                .fontSize(16)
                .textAlign(TextAlign.Center)
                .margin({ top: 10 })
            }, (item: string) => item)
          }.width('100%')
        }
        .id('testId')
        .height('80%')
      }
      .width('100%')

      Row() {
        Button('UIObserver on')
          .onClick(() => {
            // 注册监听
            uiObserver.on('scrollEvent', (info) => {
              console.info(`scrollEventInfo ${JSON.stringify(info)}`);
            });
          })
        Button('UIObserver off')
          .onClick(() => {
            // 注销监听
            uiObserver.off('scrollEvent');
          })
      }

      Row() {
        Button('UIObserverWithId on')
          .onClick(() => {
            // 注册监听，指定组件的id
            uiObserver.on('scrollEvent', this.options, (info) => {
              console.info(`scrollEventInfo ${JSON.stringify(info)}`);
            });
          })
        Button('UIObserverWithId off')
          .onClick(() => {
            // 注销监听
            uiObserver.off('scrollEvent',this.options);
          })
      }
    }
    .height('100%')
  }
}

```


## off('scrollEvent')

```TypeScript
export function off(type: 'scrollEvent', callback?: Callback<ScrollEventInfo>): void
```

Removes a callback function that was previously registered with `on()`.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-uiObserver-export function off(type: 'scrollEvent', callback?: Callback<ScrollEventInfo>): void--><!--Device-uiObserver-export function off(type: 'scrollEvent', callback?: Callback<ScrollEventInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'scrollEvent' | 是 | The type of event to remove the listener for. Must be 'scrollEvent'. |
| callback | [Callback](../arkts-components/arkts-arkui-common-callback-i.md)<ScrollEventInfo> | 否 | The callback function to remove. If not provided, all callbacks for the given event type will be removed. |


## off('routerPageUpdate')

```TypeScript
export function off(type: 'routerPageUpdate', context: UIAbilityContext | UIContext, callback?: Callback<RouterPageInfo>): void
```

取消监听router中page页面的状态变化。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-uiObserver-export function off(type: 'routerPageUpdate', context: UIAbilityContext | UIContext, callback?: Callback<RouterPageInfo>): void--><!--Device-uiObserver-export function off(type: 'routerPageUpdate', context: UIAbilityContext | UIContext, callback?: Callback<RouterPageInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'routerPageUpdate' | 是 | 监听事件，固定为'routerPageUpdate'，即router中page页面的状态变化。 |
| context | UIAbilityContext \| UIContext | 是 | 上下文信息，用以指定监听页面的范围。 |
| callback | [Callback](../arkts-components/arkts-arkui-common-callback-i.md)<RouterPageInfo> | 否 | 需要被注销的回调函数。 |

**示例：**

```TypeScript
// used in UIAbility
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { uiObserver, UIContext } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // 实际使用前uiContext需要被赋值。参见示例uiObserver.on('routerPageUpdate')
  private uiContext: UIContext | null = null;

  onDestroy(): void {
    // 注销当前abilityContext上的所有routerPageUpdate监听
    uiObserver.off('routerPageUpdate', this.context)
  }

  onWindowStageDestroy(): void {
    // 注销在uiContext上的所有routerPageUpdate监听
    if (this.uiContext) {
      uiObserver.off('routerPageUpdate', this.uiContext);
    }
  }

  // ... other function in EntryAbility
}

```


## off('densityUpdate')

```TypeScript
export function off(type: 'densityUpdate', context: UIContext, callback?: Callback<DensityInfo>): void
```

取消监听屏幕像素密度的变化。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-uiObserver-export function off(type: 'densityUpdate', context: UIContext, callback?: Callback<DensityInfo>): void--><!--Device-uiObserver-export function off(type: 'densityUpdate', context: UIContext, callback?: Callback<DensityInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'densityUpdate' | 是 | 监听事件，固定为'densityUpdate'，即屏幕像素密度变化。 |
| context | [UIContext](../arkts-components/arkts-arkui-uicontext-t.md) | 是 | 上下文信息，用以指定监听页面的范围。 |
| callback | [Callback](../arkts-components/arkts-arkui-common-callback-i.md)<DensityInfo> | 否 | 需要被注销的回调函数。若不指定具体的回调函数，则注销指定UIContext下所有densityUpdate事件监听。 |


## off('willDraw')

```TypeScript
export function off(type: 'willDraw', context: UIContext, callback?: Callback<void>): void
```

取消监听每一帧绘制指令下发情况。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-uiObserver-export function off(type: 'willDraw', context: UIContext, callback?: Callback<void>): void--><!--Device-uiObserver-export function off(type: 'willDraw', context: UIContext, callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'willDraw' | 是 | 监听事件，固定为'willDraw'，即是否将要绘制。 |
| context | [UIContext](../arkts-components/arkts-arkui-uicontext-t.md) | 是 | 上下文信息，用以指定监听页面的范围。 |
| callback | [Callback](../arkts-components/arkts-arkui-common-callback-i.md)<void> | 否 | 需要被注销的回调函数。 |


## off('didLayout')

```TypeScript
export function off(type: 'didLayout', context: UIContext, callback?: Callback<void>): void
```

取消监听每一帧布局完成情况。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-uiObserver-export function off(type: 'didLayout', context: UIContext, callback?: Callback<void>): void--><!--Device-uiObserver-export function off(type: 'didLayout', context: UIContext, callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'didLayout' | 是 | 监听事件，固定为'didLayout'，即是否布局完成。 |
| context | [UIContext](../arkts-components/arkts-arkui-uicontext-t.md) | 是 | 上下文信息，用以指定监听页面的范围。 |
| callback | [Callback](../arkts-components/arkts-arkui-common-callback-i.md)<void> | 否 | 需要被注销的回调函数。 |


## off('tabContentUpdate')

```TypeScript
export function off(type: 'tabContentUpdate', options: ObserverOptions, callback?: Callback<TabContentInfo>): void
```

取消监听指定Tabs组件id的TabContent页面切换事件。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-uiObserver-export function off(type: 'tabContentUpdate', options: ObserverOptions, callback?: Callback<TabContentInfo>): void--><!--Device-uiObserver-export function off(type: 'tabContentUpdate', options: ObserverOptions, callback?: Callback<TabContentInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'tabContentUpdate' | 是 | 监听事件，固定为'tabContentUpdate'，即TabContent页面的切换事件。 |
| options | [ObserverOptions](arkts-arkui-uiobserver-observeroptions-i.md) | 是 | 指定监听的Tabs组件的id。 |
| callback | [Callback](../arkts-components/arkts-arkui-common-callback-i.md)<TabContentInfo> | 否 | 需要被注销的回调函数。 |


## off('tabContentUpdate')

```TypeScript
export function off(type: 'tabContentUpdate', callback?: Callback<TabContentInfo>): void
```

取消监听TabContent页面的切换事件。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-uiObserver-export function off(type: 'tabContentUpdate', callback?: Callback<TabContentInfo>): void--><!--Device-uiObserver-export function off(type: 'tabContentUpdate', callback?: Callback<TabContentInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'tabContentUpdate' | 是 | 监听事件，固定为'tabContentUpdate'，即TabContent页面的切换事件。 |
| callback | [Callback](../arkts-components/arkts-arkui-common-callback-i.md)<TabContentInfo> | 否 | 需要被注销的回调函数。 |


## off('navDestinationSwitch')

```TypeScript
export function off(
    type: 'navDestinationSwitch',
    context: UIAbilityContext | UIContext,
    callback?: Callback<NavDestinationSwitchInfo>
  ): void
```

取消监听Navigation的页面切换事件。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-uiObserver-export function off(
    type: 'navDestinationSwitch',
    context: UIAbilityContext | UIContext,
    callback?: Callback<NavDestinationSwitchInfo>
  ): void--><!--Device-uiObserver-export function off(
    type: 'navDestinationSwitch',
    context: UIAbilityContext | UIContext,
    callback?: Callback<NavDestinationSwitchInfo>
  ): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'navDestinationSwitch' | 是 | 监听事件，固定为'navDestinationSwitch'，即Navigation的页面切换事件。 |
| context | UIAbilityContext \| UIContext | 是 | 上下文信息，用以指定监听页面切换事件的范围。 |
| callback | [Callback](../arkts-components/arkts-arkui-common-callback-i.md)<NavDestinationSwitchInfo> | 否 | 需要被注销的回调函数。 |


## off('navDestinationSwitch')

```TypeScript
export function off(
    type: 'navDestinationSwitch',
    context: UIAbilityContext | UIContext,
    observerOptions: NavDestinationSwitchObserverOptions,
    callback?: Callback<NavDestinationSwitchInfo>
  ): void
```

取消监听Navigation的页面切换事件。与[uiObserver.off](arkts-arkui-uiobserver-off-f.md#off-11)相比，新增了observerOptions参数，即支持设置监听选项。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-uiObserver-export function off(
    type: 'navDestinationSwitch',
    context: UIAbilityContext | UIContext,
    observerOptions: NavDestinationSwitchObserverOptions,
    callback?: Callback<NavDestinationSwitchInfo>
  ): void--><!--Device-uiObserver-export function off(
    type: 'navDestinationSwitch',
    context: UIAbilityContext | UIContext,
    observerOptions: NavDestinationSwitchObserverOptions,
    callback?: Callback<NavDestinationSwitchInfo>
  ): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'navDestinationSwitch' | 是 | 监听事件，固定为'navDestinationSwitch'，即Navigation的页面切换事件。 |
| context | UIAbilityContext \| UIContext | 是 | 上下文信息，用以指定监听页面切换事件的范围。 |
| observerOptions | [NavDestinationSwitchObserverOptions](arkts-arkui-uiobserver-navdestinationswitchobserveroptions-i.md) | 是 | 监听选项。 |
| callback | [Callback](../arkts-components/arkts-arkui-common-callback-i.md)<NavDestinationSwitchInfo> | 否 | 需要被注销的回调函数。 |

