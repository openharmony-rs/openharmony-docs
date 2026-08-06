# offTabContentUpdate

## offTabContentUpdate

```TypeScript
export function offTabContentUpdate(options: ObserverOptions, callback?: Callback<TabContentInfo>): void
```

取消监听TabContent页面的切换事件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-uiObserver-export function offTabContentUpdate(options: ObserverOptions, callback?: Callback<TabContentInfo>): void--><!--Device-uiObserver-export function offTabContentUpdate(options: ObserverOptions, callback?: Callback<TabContentInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 指定监听的Tabs组件的id。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;TabContentInfo&gt; | 否 | 需要被注销的回调函数。 |


## offTabContentUpdate

```TypeScript
export function offTabContentUpdate(callback?: Callback<TabContentInfo>): void
```

取消监听TabContent页面的切换事件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-uiObserver-export function offTabContentUpdate(callback?: Callback<TabContentInfo>): void--><!--Device-uiObserver-export function offTabContentUpdate(callback?: Callback<TabContentInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;TabContentInfo&gt; | 否 | 需要被注销的回调函数。 |

