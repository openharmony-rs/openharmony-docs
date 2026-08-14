# offTabContentUpdate

## offTabContentUpdate

```TypeScript
export function offTabContentUpdate(options: ObserverOptions, callback?: Callback<TabContentInfo>): void
```

取消监听TabContent页面的切换事件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-uiObserver-export function offTabContentUpdate(options: ObserverOptions, callback?: Callback<TabContentInfo>): void--><!--Device-uiObserver-export function offTabContentUpdate(options: ObserverOptions, callback?: Callback<TabContentInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | ObserverOptions | 是 | 指定监听的Tabs组件的id。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[TabContentInfo](../../apis-arkui/arkts-apis/arkts-arkui-uiobserver-tabcontentinfo-i.md)&gt; | 否 | 需要被注销的回调函数。 |


## offTabContentUpdate

```TypeScript
export function offTabContentUpdate(callback?: Callback<TabContentInfo>): void
```

取消监听TabContent页面的切换事件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-uiObserver-export function offTabContentUpdate(callback?: Callback<TabContentInfo>): void--><!--Device-uiObserver-export function offTabContentUpdate(callback?: Callback<TabContentInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[TabContentInfo](../../apis-arkui/arkts-apis/arkts-arkui-uiobserver-tabcontentinfo-i.md)&gt; | 否 | 需要被注销的回调函数。 |

