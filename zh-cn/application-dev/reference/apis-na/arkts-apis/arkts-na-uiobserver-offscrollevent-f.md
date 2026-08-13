# offScrollEvent

## offScrollEvent

```TypeScript
export function offScrollEvent(options: ObserverOptions, callback?: Callback<ScrollEventInfo>): void
```

Removes a callback function that was previously registered with `onScrollEvent()`.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-uiObserver-export function offScrollEvent(options: ObserverOptions, callback?: Callback<ScrollEventInfo>): void--><!--Device-uiObserver-export function offScrollEvent(options: ObserverOptions, callback?: Callback<ScrollEventInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | ObserverOptions | 是 | The options object. |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[ScrollEventInfo](../../apis-arkui/arkts-apis/arkts-arkui-uiobserver-scrolleventinfo-i.md)&gt; | 否 | The callback function to remove. If not provided, all callbacks for the given event type and scroll ID will be removed. |


## offScrollEvent

```TypeScript
export function offScrollEvent(callback?: Callback<ScrollEventInfo>): void
```

Removes a callback function that was previously registered with `onScrollEvent()`.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-uiObserver-export function offScrollEvent(callback?: Callback<ScrollEventInfo>): void--><!--Device-uiObserver-export function offScrollEvent(callback?: Callback<ScrollEventInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[ScrollEventInfo](../../apis-arkui/arkts-apis/arkts-arkui-uiobserver-scrolleventinfo-i.md)&gt; | 否 | The callback function to remove. If not provided, all callbacks for the given event type will be removed. |

