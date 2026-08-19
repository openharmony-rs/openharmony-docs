# UIScrollableCommonEvent

Defines a UIScrollableCommonEvent which is used to set event to target component.

**继承/实现关系：** UIScrollableCommonEvent extends [UICommonEvent](arkts-na-common-uicommonevent-i.md)

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare interface UIScrollableCommonEvent--><!--Device-unnamed-export declare interface UIScrollableCommonEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## setOnReachEnd

```TypeScript
setOnReachEnd(callback: VoidCallback | undefined): void
```

Set or reset the callback which is triggered when the scrolling reaches the end position.

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIScrollableCommonEvent-setOnReachEnd(callback: VoidCallback | undefined): void--><!--Device-UIScrollableCommonEvent-setOnReachEnd(callback: VoidCallback | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [VoidCallback](../../apis-arkui/arkts-apis/arkts-arkui-voidcallback-t.md) \| undefined | 是 | callback function, triggered when the scrolling reaches the end position. <br>Passing undefined will unregister the callback. |

## setOnReachStart

```TypeScript
setOnReachStart(callback: VoidCallback | undefined): void
```

Set or reset the callback which is triggered when the scrolling reaches the start position.

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIScrollableCommonEvent-setOnReachStart(callback: VoidCallback | undefined): void--><!--Device-UIScrollableCommonEvent-setOnReachStart(callback: VoidCallback | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [VoidCallback](../../apis-arkui/arkts-apis/arkts-arkui-voidcallback-t.md) \| undefined | 是 | callback function, triggered when the scrolling reaches the start position. <br>Passing undefined will unregister the callback. |

## setOnScrollFrameBegin

```TypeScript
setOnScrollFrameBegin(callback: OnScrollFrameBeginCallback | undefined): void
```

Set or reset the callback which is triggered when scrolling begin each frame.

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIScrollableCommonEvent-setOnScrollFrameBegin(callback: OnScrollFrameBeginCallback | undefined): void--><!--Device-UIScrollableCommonEvent-setOnScrollFrameBegin(callback: OnScrollFrameBeginCallback | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnScrollFrameBeginCallback](../../apis-arkui/arkts-components/arkts-arkui-onscrollframebegincallback-t.md) \| undefined | 是 | callback function, triggered when the scrolling begin each frame. <br>Passing undefined will unregister the callback. |

## setOnScrollStart

```TypeScript
setOnScrollStart(callback: VoidCallback | undefined): void
```

Set or reset the callback which is triggered when the scrolling started.

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIScrollableCommonEvent-setOnScrollStart(callback: VoidCallback | undefined): void--><!--Device-UIScrollableCommonEvent-setOnScrollStart(callback: VoidCallback | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [VoidCallback](../../apis-arkui/arkts-apis/arkts-arkui-voidcallback-t.md) \| undefined | 是 | callback function, triggered when the scrolling started. <br>Passing undefined will unregister the callback. |

## setOnScrollStop

```TypeScript
setOnScrollStop(callback: VoidCallback | undefined): void
```

Set or reset the callback which is triggered when the scrolling stopped.

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIScrollableCommonEvent-setOnScrollStop(callback: VoidCallback | undefined): void--><!--Device-UIScrollableCommonEvent-setOnScrollStop(callback: VoidCallback | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [VoidCallback](../../apis-arkui/arkts-apis/arkts-arkui-voidcallback-t.md) \| undefined | 是 | callback function, triggered when the scrolling stopped. <br>Passing undefined will unregister the callback. |

