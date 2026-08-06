# SmartGestureController

类SmartGestureController。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare class SmartGestureController--><!--Device-unnamed-export declare class SmartGestureController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## clearMonitors

```TypeScript
clearMonitors(): void
```

清除监听手势事件的回调函数。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SmartGestureController-clearMonitors(): void--><!--Device-SmartGestureController-clearMonitors(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## clearSelected

```TypeScript
clearSelected(): void
```

清除当前智能手势选择。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SmartGestureController-clearSelected(): void--><!--Device-SmartGestureController-clearSelected(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableSmartTapAndSlideGestures

```TypeScript
enableSmartTapAndSlideGestures(enabled: boolean): void
```

开启或关闭手表的智能点击和滑动手势。此开关控制点击和滑动手势的新实现。启用后，将使用新的智能手势处理流水线。禁用时，将使用传统实现以实现兼容性。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SmartGestureController-enableSmartTapAndSlideGestures(enabled: boolean): void--><!--Device-SmartGestureController-enableSmartTapAndSlideGestures(enabled: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 是否启用智能点击和滑动手势处理。 |

## registerMonitor

```TypeScript
registerMonitor(monitorCallback: Callback<BaseGestureHandlingProposal, GestureHandlingResolution>): void
```

注册一个回调函数来监听手势事件。在系统处理手势事件之前，应用程序可以接收到当前手势的处理意图，并进行自定义干预。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SmartGestureController-registerMonitor(monitorCallback: Callback<BaseGestureHandlingProposal, GestureHandlingResolution>): void--><!--Device-SmartGestureController-registerMonitor(monitorCallback: Callback<BaseGestureHandlingProposal, GestureHandlingResolution>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| monitorCallback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;BaseGestureHandlingProposal, GestureHandlingResolution&gt; | 是 | 手势识别时调用的回调函数。 |

## requestSelected

```TypeScript
requestSelected(id: string): void
```

通过节点的标识符请求智能手势选择节点。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SmartGestureController-requestSelected(id: string): void--><!--Device-SmartGestureController-requestSelected(id: string): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 要选择的节点的标识符。 |

## unregisterMonitor

```TypeScript
unregisterMonitor(monitorCallback: Callback<BaseGestureHandlingProposal, GestureHandlingResolution>): void
```

注销监听手势事件的回调函数。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SmartGestureController-unregisterMonitor(monitorCallback: Callback<BaseGestureHandlingProposal, GestureHandlingResolution>): void--><!--Device-SmartGestureController-unregisterMonitor(monitorCallback: Callback<BaseGestureHandlingProposal, GestureHandlingResolution>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| monitorCallback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;BaseGestureHandlingProposal, GestureHandlingResolution&gt; | 是 | 识别手势时调用的回调函数。 |

