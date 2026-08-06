# onScrollEvent

## onScrollEvent

```TypeScript
export function onScrollEvent(options: ObserverOptions, callback: Callback<ScrollEventInfo>): void
```

Registers a callback function to be called when the scroll event starts or stops.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-uiObserver-export function onScrollEvent(options: ObserverOptions, callback: Callback<ScrollEventInfo>): void--><!--Device-uiObserver-export function onScrollEvent(options: ObserverOptions, callback: Callback<ScrollEventInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | The options object. |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;ScrollEventInfo&gt; | 是 | The callback function to be called when the scroll event start or stop. |


## onScrollEvent

```TypeScript
export function onScrollEvent(callback: Callback<ScrollEventInfo>): void
```

Registers a callback function to be called when the scroll event starts or stops.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-uiObserver-export function onScrollEvent(callback: Callback<ScrollEventInfo>): void--><!--Device-uiObserver-export function onScrollEvent(callback: Callback<ScrollEventInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;ScrollEventInfo&gt; | 是 | The callback function to be called when the scroll event start or stop. |

