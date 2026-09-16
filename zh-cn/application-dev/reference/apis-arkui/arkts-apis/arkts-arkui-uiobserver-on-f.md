# on

## 导入模块

```TypeScript
import { uiObserver } from '@kit.ArkUI';
```

## on('navDestinationUpdate')

```TypeScript
export function on(type: 'navDestinationUpdate', options: { navigationId: ResourceStr }, callback: Callback<NavDestinationInfo>): void
```

监听NavDestination组件的状态变化。与  
* [uiObserver.on](#onnavdestinationupdate)相比，新增了options参数，即支持指定监听的Navigation的id。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'navDestinationUpdate' | 是 | 监听事件，固定为'navDestinationUpdate'，即NavDestination组件的状态变化。 |
| options | { navigationId: ResourceStr } | 是 | 指定监听的Navigation的id。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[NavDestinationInfo](arkts-arkui-uiobserver-navdestinationinfo-i.md)&gt; | 是 | 回调函数。返回当前的NavDestination组件状态。 |


## on('navDestinationUpdate')

```TypeScript
export function on(type: 'navDestinationUpdate', callback: Callback<NavDestinationInfo>): void
```

监听NavDestination组件的状态变化。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'navDestinationUpdate' | 是 | 监听事件，固定为'navDestinationUpdate'，即NavDestination组件的状态变化。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[NavDestinationInfo](arkts-arkui-uiobserver-navdestinationinfo-i.md)&gt; | 是 | 回调函数。返回当前的NavDestination组件状态。 |


## on('scrollEvent')

```TypeScript
export function on(type: 'scrollEvent', options: ObserverOptions, callback: Callback<ScrollEventInfo>): void
```

Registers a callback function to be called when the scroll event start or stop.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'scrollEvent' | 是 | The type of event to listen for. Must be 'scrollEvent'. |
| options | [ObserverOptions](arkts-arkui-uiobserver-observeroptions-i.md) | 是 | The options object. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ScrollEventInfo](arkts-arkui-uiobserver-scrolleventinfo-i.md)&gt; | 是 | The callback function to be called when the scroll event start or stop. |


## on('scrollEvent')

```TypeScript
export function on(type: 'scrollEvent', callback: Callback<ScrollEventInfo>): void
```

Registers a callback function to be called when the scroll event start or stop.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'scrollEvent' | 是 | The type of event to listen for. Must be 'scrollEvent'. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ScrollEventInfo](arkts-arkui-uiobserver-scrolleventinfo-i.md)&gt; | 是 | The callback function to be called when the scroll event start or stop. |


## on('routerPageUpdate')

```TypeScript
export function on(type: 'routerPageUpdate', context: UIAbilityContext | UIContext, callback: Callback<RouterPageInfo>): void
```

监听router中page页面的状态变化。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'routerPageUpdate' | 是 | 监听事件，固定为'routerPageUpdate'，即router中page页面的状态变化。 |
| context | [UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext-c.md) &#124; UIContext | 是 | 上下文信息，用以指定监听页面的范围。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[RouterPageInfo](arkts-arkui-uiobserver-routerpageinfo-c.md)&gt; | 是 | 回调函数。携带pageInfo，返回当前的page页面状态。 |


## on('densityUpdate')

```TypeScript
export function on(type: 'densityUpdate', context: UIContext, callback: Callback<DensityInfo>): void
```

监听屏幕像素密度变化。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'densityUpdate' | 是 | 监听事件，固定为'densityUpdate'，即屏幕像素密度变化。 |
| context | UIContext | 是 | 上下文信息，用以指定监听页面的范围。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[DensityInfo](arkts-arkui-uiobserver-densityinfo-c.md)&gt; | 是 | 回调函数。携带DensityInfo，返回变化后的屏幕像素密度。 |


## on('willDraw')

```TypeScript
export function on(type: 'willDraw', context: UIContext, callback: Callback<void>): void
```

监听每一帧绘制指令下发情况。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'willDraw' | 是 | 监听事件，固定为'willDraw'，即是否将要绘制。 |
| context | UIContext | 是 | 上下文信息，用以指定监听页面的范围。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 是 | 回调函数。 |


## on('didLayout')

```TypeScript
export function on(type: 'didLayout', context: UIContext, callback: Callback<void>): void
```

监听每一帧布局完成情况。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'didLayout' | 是 | 监听事件，固定为'didLayout'，即是否布局完成。 |
| context | UIContext | 是 | 上下文信息，用以指定监听页面的范围。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 是 | 回调函数。 |


## on('tabContentUpdate')

```TypeScript
export function on(type: 'tabContentUpdate', options: ObserverOptions, callback: Callback<TabContentInfo>): void
```

监听指定Tabs组件id的TabContent页面切换事件。相比[on('tabChange')](arkts-arkui-arkui-uicontext-uiobserver-c.md#ontabchange)，本接口不支持监听Tabs组件初始化时，显示首个页签的事件。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'tabContentUpdate' | 是 | 监听事件，固定为'tabContentUpdate'，即TabContent页面的切换事件。 |
| options | [ObserverOptions](arkts-arkui-uiobserver-observeroptions-i.md) | 是 | 指定监听的Tabs组件的id。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[TabContentInfo](arkts-arkui-uiobserver-tabcontentinfo-i.md)&gt; | 是 | 回调函数。携带TabContentInfo，返回TabContent页面切换事件的信息。 |


## on('tabContentUpdate')

```TypeScript
export function on(type: 'tabContentUpdate', callback: Callback<TabContentInfo>): void
```

监听TabContent页面的切换事件。相比[on('tabChange')](arkts-arkui-arkui-uicontext-uiobserver-c.md#ontabchange)，本接口不支持监听Tabs组件初始化时，显示首个页签的事件。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'tabContentUpdate' | 是 | 监听事件，固定为'tabContentUpdate'，即TabContent页面的切换事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[TabContentInfo](arkts-arkui-uiobserver-tabcontentinfo-i.md)&gt; | 是 | 回调函数。携带TabContentInfo，返回TabContent页面切换事件的信息。 |


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

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'navDestinationSwitch' | 是 | 监听事件，固定为'navDestinationSwitch'，即Navigation的页面切换事件。 |
| context | [UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext-c.md) &#124; UIContext | 是 | 上下文信息，用以指定监听页面切换事件的范围。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[NavDestinationSwitchInfo](arkts-arkui-uiobserver-navdestinationswitchinfo-i.md)&gt; | 是 | 回调函数。携带NavDestinationSwitchInfo，返回页面切换事件的信息。 |


## on('navDestinationSwitch')

```TypeScript
export function on(
    type: 'navDestinationSwitch',
    context: UIAbilityContext | UIContext,
    observerOptions: NavDestinationSwitchObserverOptions,
    callback: Callback<NavDestinationSwitchInfo>
  ): void
```

监听Navigation的页面切换事件。与[uiObserver.on](#onnavdestinationswitch)相比，新增了observerOptions参数，即支持设置监听选项。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'navDestinationSwitch' | 是 | 监听事件，固定为'navDestinationSwitch'，即Navigation的页面切换事件。 |
| context | [UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext-c.md) &#124; UIContext | 是 | 上下文信息，用以指定监听页面切换事件的范围。 |
| observerOptions | [NavDestinationSwitchObserverOptions](arkts-arkui-uiobserver-navdestinationswitchobserveroptions-i.md) | 是 | 监听选项。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[NavDestinationSwitchInfo](arkts-arkui-uiobserver-navdestinationswitchinfo-i.md)&gt; | 是 | 回调函数。携带NavDestinationSwitchInfo，返回页面切换事件的信息。 |
