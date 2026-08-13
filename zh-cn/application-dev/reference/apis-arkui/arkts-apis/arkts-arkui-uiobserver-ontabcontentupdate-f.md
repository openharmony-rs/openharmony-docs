# on_tabContentUpdate

## on_tabContentUpdate

```TypeScript
export function on(type: 'tabContentUpdate', options: ObserverOptions, callback: Callback<TabContentInfo>): void
```

监听指定Tabs组件id的TabContent页面切换事件。相比[on('tabChange')](arkts-arkui-arkui-uicontext-uiobserver-c.md#on_navDestinationUpdate)，本接口不支持监听Tabs组件初始化时，显示首个页签的事件。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-uiObserver-export function on(type: 'tabContentUpdate', options: ObserverOptions, callback: Callback<TabContentInfo>): void--><!--Device-uiObserver-export function on(type: 'tabContentUpdate', options: ObserverOptions, callback: Callback<TabContentInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'tabContentUpdate' | 是 | 监听事件，固定为'tabContentUpdate'，即TabContent页面的切换事件。 |
| options | ObserverOptions | 是 | 指定监听的Tabs组件的id。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[TabContentInfo](arkts-arkui-uiobserver-tabcontentinfo-i.md)&gt; | 是 | 回调函数。携带TabContentInfo，返回TabContent页面切换事件的信息。 |


## on_tabContentUpdate

```TypeScript
export function on(type: 'tabContentUpdate', callback: Callback<TabContentInfo>): void
```

监听TabContent页面的切换事件。相比[on('tabChange')](arkts-arkui-arkui-uicontext-uiobserver-c.md#on_navDestinationUpdate)，本接口不支持监听Tabs组件初始化时，显示首个页签的事件。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-uiObserver-export function on(type: 'tabContentUpdate', callback: Callback<TabContentInfo>): void--><!--Device-uiObserver-export function on(type: 'tabContentUpdate', callback: Callback<TabContentInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'tabContentUpdate' | 是 | 监听事件，固定为'tabContentUpdate'，即TabContent页面的切换事件。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[TabContentInfo](arkts-arkui-uiobserver-tabcontentinfo-i.md)&gt; | 是 | 回调函数。携带TabContentInfo，返回TabContent页面切换事件的信息。 |

