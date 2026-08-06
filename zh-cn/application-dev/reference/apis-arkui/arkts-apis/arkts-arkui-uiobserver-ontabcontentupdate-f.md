# onTabContentUpdate

## onTabContentUpdate

```TypeScript
export function onTabContentUpdate(options: ObserverOptions, callback: Callback<TabContentInfo>): void
```

监听TabContent页面的切换事件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-uiObserver-export function onTabContentUpdate(options: ObserverOptions, callback: Callback<TabContentInfo>): void--><!--Device-uiObserver-export function onTabContentUpdate(options: ObserverOptions, callback: Callback<TabContentInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 指定监听的Tabs组件的id。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;TabContentInfo&gt; | 是 | 回调函数。携带TabContentInfo，返回TabContent页面切换事件的信息。 |


## onTabContentUpdate

```TypeScript
export function onTabContentUpdate(callback: Callback<TabContentInfo>): void
```

监听TabContent页面的切换事件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-uiObserver-export function onTabContentUpdate(callback: Callback<TabContentInfo>): void--><!--Device-uiObserver-export function onTabContentUpdate(callback: Callback<TabContentInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;TabContentInfo&gt; | 是 | 回调函数。携带TabContentInfo，返回TabContent页面切换事件的信息。 |

