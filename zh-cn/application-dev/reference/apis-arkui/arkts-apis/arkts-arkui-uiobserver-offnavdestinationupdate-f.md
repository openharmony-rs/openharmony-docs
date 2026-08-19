# off_navDestinationUpdate

## 导入模块

```TypeScript
import { uiObserver } from '@kit.ArkUI';
```

## off('navDestinationUpdate')

```TypeScript
export function off(type: 'navDestinationUpdate', options: { navigationId: ResourceStr }, callback?: Callback<NavDestinationInfo>): void
```

取消监听NavDestination组件的状态变化。与[uiObserver.off](#offnavdestinationupdate)相比，新增了options参数，即支持指定监听的Navigation的id。

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
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;NavDestinationInfo&gt; | 否 | 回调函数。返回当前的NavDestination组件状态。 |


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
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;NavDestinationInfo&gt; | 否 | 回调函数。返回当前的NavDestination组件状态。 |

