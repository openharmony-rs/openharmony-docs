# GestureGroupHandler

手势组处理器对象类型。

**继承/实现关系：** GestureGroupHandler extends [GestureHandler<GestureGroupHandler>](GestureHandler<GestureGroupHandler>)

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

<!--Device-unnamed-declare class GestureGroupHandler extends GestureHandler<GestureGroupHandler>--><!--Device-unnamed-declare class GestureGroupHandler extends GestureHandler<GestureGroupHandler>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(options?: GestureGroupGestureHandlerOptions)
```

手势组处理器的构造函数。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GestureGroupHandler-constructor(options?: GestureGroupGestureHandlerOptions)--><!--Device-GestureGroupHandler-constructor(options?: GestureGroupGestureHandlerOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 手势组处理器配置参数。 |

## onCancel

```TypeScript
onCancel(event: Callback<void>): GestureGroupHandler
```

设置手势组处理器取消回调。顺序组合手势（[GestureMode]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_.Sequence）取消后触发回调。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GestureGroupHandler-onCancel(event: Callback<void>): GestureGroupHandler--><!--Device-GestureGroupHandler-onCancel(event: Callback<void>): GestureGroupHandler-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 手势组处理器取消回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回当前手势组处理器对象。 |

