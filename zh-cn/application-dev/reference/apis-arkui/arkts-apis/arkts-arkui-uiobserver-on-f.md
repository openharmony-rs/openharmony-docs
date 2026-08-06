# on

## on('navDestinationUpdate')

```TypeScript
export function on(type: 'navDestinationUpdate', options: { navigationId: ResourceStr }, callback: Callback<NavDestinationInfo>): void
```

监听NavDestination组件的状态变化。与 * [uiObserver.on]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_相比，新增了options参数，即支持指定监听的Navigation的id。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-uiObserver-export function on(type: 'navDestinationUpdate', options: { navigationId: ResourceStr }, callback: Callback<NavDestinationInfo>): void--><!--Device-uiObserver-export function on(type: 'navDestinationUpdate', options: { navigationId: ResourceStr }, callback: Callback<NavDestinationInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'navDestinationUpdate' | 是 | 监听事件，固定为'navDestinationUpdate'，即NavDestination组件的状态变化。 |
| options | { navigationId: ResourceStr } | 是 | 指定监听的Navigation的id。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;NavDestinationInfo&gt; | 是 | 回调函数。返回当前的NavDestination组件状态。 |

**示例：**

```TypeScript
// Index.ets
// 演示 uiObserver.on('navDestinationUpdate', navigationId, callback)
// uiObserver.off('navDestinationUpdate', navigationId, callback)
import { uiObserver } from '@kit.ArkUI';

@Component
struct PageOne {
  build() {
    NavDestination() {
      Text("pageOne")
    }.title("pageOne")
  }
}

@Entry
@Component
struct Index {
  private stack: NavPathStack = new NavPathStack();

  @Builder
  PageBuilder(name: string) {
    PageOne()
  }

  aboutToAppear() {
    // 注册监听，指定Navigation的id
    uiObserver.on('navDestinationUpdate', { navigationId: "testId" }, (info) => {
      console.info(`NavDestination state update ${JSON.stringify(info)}`);
    });
  }

  aboutToDisappear() {
    // 注销监听
    uiObserver.off('navDestinationUpdate', { navigationId: "testId" });
  }

  build() {
    Column() {
      Navigation(this.stack) {
        Button("push").onClick(() => {
          this.stack.pushPath({ name: "pageOne" });
        })
      }
      .id("testId")
      .title("Navigation")
      .navDestination(this.PageBuilder)
    }
    .width('100%')
    .height('100%')
  }
}
```


## on('navDestinationUpdate')

```TypeScript
export function on(type: 'navDestinationUpdate', callback: Callback<NavDestinationInfo>): void
```

监听NavDestination组件的状态变化。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-uiObserver-export function on(type: 'navDestinationUpdate', callback: Callback<NavDestinationInfo>): void--><!--Device-uiObserver-export function on(type: 'navDestinationUpdate', callback: Callback<NavDestinationInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'navDestinationUpdate' | 是 | 监听事件，固定为'navDestinationUpdate'，即NavDestination组件的状态变化。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;NavDestinationInfo&gt; | 是 | 回调函数。返回当前的NavDestination组件状态。 |


## on('scrollEvent')

```TypeScript
export function on(type: 'scrollEvent', options: ObserverOptions, callback: Callback<ScrollEventInfo>): void
```

Registers a callback function to be called when the scroll event start or stop.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-uiObserver-export function on(type: 'scrollEvent', options: ObserverOptions, callback: Callback<ScrollEventInfo>): void--><!--Device-uiObserver-export function on(type: 'scrollEvent', options: ObserverOptions, callback: Callback<ScrollEventInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'scrollEvent' | 是 | The type of event to listen for. Must be 'scrollEvent'. |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | The options object. |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;ScrollEventInfo&gt; | 是 | The callback function to be called when the scroll event start or stop. |


## on('scrollEvent')

```TypeScript
export function on(type: 'scrollEvent', callback: Callback<ScrollEventInfo>): void
```

Registers a callback function to be called when the scroll event start or stop.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-uiObserver-export function on(type: 'scrollEvent', callback: Callback<ScrollEventInfo>): void--><!--Device-uiObserver-export function on(type: 'scrollEvent', callback: Callback<ScrollEventInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'scrollEvent' | 是 | The type of event to listen for. Must be 'scrollEvent'. |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;ScrollEventInfo&gt; | 是 | The callback function to be called when the scroll event start or stop. |


## on('routerPageUpdate')

```TypeScript
export function on(type: 'routerPageUpdate', context: UIAbilityContext | UIContext, callback: Callback<RouterPageInfo>): void
```

监听router中page页面的状态变化。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-uiObserver-export function on(type: 'routerPageUpdate', context: UIAbilityContext | UIContext, callback: Callback<RouterPageInfo>): void--><!--Device-uiObserver-export function on(type: 'routerPageUpdate', context: UIAbilityContext | UIContext, callback: Callback<RouterPageInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'routerPageUpdate' | 是 | 监听事件，固定为'routerPageUpdate'，即router中page页面的状态变化。 |
| context | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| UIContext | 是 | 上下文信息，用以指定监听页面的范围。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;RouterPageInfo&gt; | 是 | 回调函数。携带pageInfo，返回当前的page页面状态。 |


## on('densityUpdate')

```TypeScript
export function on(type: 'densityUpdate', context: UIContext, callback: Callback<DensityInfo>): void
```

监听屏幕像素密度变化。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-uiObserver-export function on(type: 'densityUpdate', context: UIContext, callback: Callback<DensityInfo>): void--><!--Device-uiObserver-export function on(type: 'densityUpdate', context: UIContext, callback: Callback<DensityInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'densityUpdate' | 是 | 监听事件，固定为'densityUpdate'，即屏幕像素密度变化。 |
| context | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 上下文信息，用以指定监听页面的范围。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;DensityInfo&gt; | 是 | 回调函数。携带DensityInfo，返回变化后的屏幕像素密度。 |

**示例：**

```TypeScript
import { uiObserver } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State density: number = 0;
  @State message: string = '未注册监听';

  densityUpdateCallback = (info: uiObserver.DensityInfo) => {
    this.density = info.density;
    this.message = '变化后的DPI：' + this.density.toString();
  }

  build() {
    Column() {
      Text(this.message)
        .fontSize(24)
        .fontWeight(FontWeight.Bold)
      Button('注册屏幕像素密度变化监听')
        .onClick(() => {
          this.message = '已注册监听'
          uiObserver.on('densityUpdate', this.getUIContext(), this.densityUpdateCallback);
        })
    }
  }
}
```


## on('willDraw')

```TypeScript
export function on(type: 'willDraw', context: UIContext, callback: Callback<void>): void
```

监听每一帧绘制指令下发情况。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-uiObserver-export function on(type: 'willDraw', context: UIContext, callback: Callback<void>): void--><!--Device-uiObserver-export function on(type: 'willDraw', context: UIContext, callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'willDraw' | 是 | 监听事件，固定为'willDraw'，即是否将要绘制。 |
| context | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 上下文信息，用以指定监听页面的范围。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 回调函数。 |

**示例：**

```TypeScript
import { uiObserver } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  willDrawCallback = () => {
    console.info("willDraw指令下发");
  }
  build() {
    Column() {
      Button('注册绘制指令下发监听')
        .onClick(() => {
          uiObserver.on('willDraw', this.getUIContext(), this.willDrawCallback);
        })
    }
  }
}
```


## on('didLayout')

```TypeScript
export function on(type: 'didLayout', context: UIContext, callback: Callback<void>): void
```

监听每一帧布局完成情况。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-uiObserver-export function on(type: 'didLayout', context: UIContext, callback: Callback<void>): void--><!--Device-uiObserver-export function on(type: 'didLayout', context: UIContext, callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'didLayout' | 是 | 监听事件，固定为'didLayout'，即是否布局完成。 |
| context | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 上下文信息，用以指定监听页面的范围。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 回调函数。 |

**示例：**

```TypeScript
import { uiObserver } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  didLayoutCallback = () => {
    console.info("Layout布局完成");
  }
  build() {
    Column() {
      Button('注册布局完成监听')
        .onClick(() => {
          uiObserver.on('didLayout', this.getUIContext(), this.didLayoutCallback);
        })
    }
  }
}
```


## on('tabContentUpdate')

```TypeScript
export function on(type: 'tabContentUpdate', options: ObserverOptions, callback: Callback<TabContentInfo>): void
```

监听指定Tabs组件id的TabContent页面切换事件。相比[on('tabChange')]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_，本接口不支持监听Tabs组件初始化时，显示首个页签的事件。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-uiObserver-export function on(type: 'tabContentUpdate', options: ObserverOptions, callback: Callback<TabContentInfo>): void--><!--Device-uiObserver-export function on(type: 'tabContentUpdate', options: ObserverOptions, callback: Callback<TabContentInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'tabContentUpdate' | 是 | 监听事件，固定为'tabContentUpdate'，即TabContent页面的切换事件。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 指定监听的Tabs组件的id。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;TabContentInfo&gt; | 是 | 回调函数。携带TabContentInfo，返回TabContent页面切换事件的信息。 |


## on('tabContentUpdate')

```TypeScript
export function on(type: 'tabContentUpdate', callback: Callback<TabContentInfo>): void
```

监听TabContent页面的切换事件。相比[on('tabChange')]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_，本接口不支持监听Tabs组件初始化时，显示首个页签的事件。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-uiObserver-export function on(type: 'tabContentUpdate', callback: Callback<TabContentInfo>): void--><!--Device-uiObserver-export function on(type: 'tabContentUpdate', callback: Callback<TabContentInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'tabContentUpdate' | 是 | 监听事件，固定为'tabContentUpdate'，即TabContent页面的切换事件。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;TabContentInfo&gt; | 是 | 回调函数。携带TabContentInfo，返回TabContent页面切换事件的信息。 |


## on('navDestinationSwitch')

```TypeScript
export function on(
    type: 'navDestinationSwitch',
    context: UIAbilityContext | UIContext,
    callback: Callback<NavDestinationSwitchInfo>
  ): void
```

监听Navigation的页面切换事件。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-uiObserver-export function on(    type: 'navDestinationSwitch',    context: UIAbilityContext | UIContext,    callback: Callback<NavDestinationSwitchInfo>  ): void--><!--Device-uiObserver-export function on(    type: 'navDestinationSwitch',    context: UIAbilityContext | UIContext,    callback: Callback<NavDestinationSwitchInfo>  ): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'navDestinationSwitch' | 是 | 监听事件，固定为'navDestinationSwitch'，即Navigation的页面切换事件。 |
| context | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| UIContext | 是 | 上下文信息，用以指定监听页面切换事件的范围。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;NavDestinationSwitchInfo&gt; | 是 | 回调函数。携带NavDestinationSwitchInfo，返回页面切换事件的信息。 |


## on('navDestinationSwitch')

```TypeScript
export function on(
    type: 'navDestinationSwitch',
    context: UIAbilityContext | UIContext,
    observerOptions: NavDestinationSwitchObserverOptions,
    callback: Callback<NavDestinationSwitchInfo>
  ): void
```

监听Navigation的页面切换事件。与[uiObserver.on]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_相比，新增了observerOptions参数，即支持设置监听选项。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-uiObserver-export function on(    type: 'navDestinationSwitch',    context: UIAbilityContext | UIContext,    observerOptions: NavDestinationSwitchObserverOptions,    callback: Callback<NavDestinationSwitchInfo>  ): void--><!--Device-uiObserver-export function on(    type: 'navDestinationSwitch',    context: UIAbilityContext | UIContext,    observerOptions: NavDestinationSwitchObserverOptions,    callback: Callback<NavDestinationSwitchInfo>  ): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'navDestinationSwitch' | 是 | 监听事件，固定为'navDestinationSwitch'，即Navigation的页面切换事件。 |
| context | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| UIContext | 是 | 上下文信息，用以指定监听页面切换事件的范围。 |
| observerOptions | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 监听选项。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;NavDestinationSwitchInfo&gt; | 是 | 回调函数。携带NavDestinationSwitchInfo，返回页面切换事件的信息。 |

