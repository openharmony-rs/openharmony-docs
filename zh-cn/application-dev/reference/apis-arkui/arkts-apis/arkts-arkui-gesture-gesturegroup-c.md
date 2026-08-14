# GestureGroup

手势识别组合，即两种及以上手势组合为复合手势，支持顺序识别、并发识别和互斥识别。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare class GestureGroup--><!--Device-unnamed-export declare class GestureGroup-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## $_instantiate

```TypeScript
static $_instantiate(factory: () => GestureGroup, mode: GestureMode, ...gesture: GestureType[]): GestureGroup
```

设置组合手势事件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GestureGroup-static $_instantiate(factory: () => GestureGroup, mode: GestureMode, ...gesture: GestureType[]): GestureGroup--><!--Device-GestureGroup-static $_instantiate(factory: () => GestureGroup, mode: GestureMode, ...gesture: GestureType[]): GestureGroup-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| factory | () =&gt; GestureGroup | 是 |  |
| mode | [GestureMode](arkts-arkui-gesture-gesturemode-e.md) | 是 | 设置组合手势识别模式。&lt;br/&gt;默认值：GestureMode.Sequence |
| gesture | [GestureType](arkts-arkui-gesturetype-t.md)[] | 是 | 设置一个或者多个基础手势类型时，这些手势会被识别为组合手势。 若此参数不填则组合手势识别功能不生效。&lt;br/&gt;**说明：**&lt;br/&gt;当需要为一个组件同时添加单击和双击手势时，可在组合手势中添加两个[TapGesture](arkts-arkui-gesture-tapgesture-c.md#TapGesture)， 需要双击手势在前，单击手势在后，否则不生效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [GestureGroup](arkts-arkui-gesture-gesturegroup-c.md) |  |

## onCancel

```TypeScript
onCancel(event: VoidCallback): GestureGroup
```

手势识别成功，接收到触摸取消事件，触发回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GestureGroup-onCancel(event: VoidCallback): GestureGroup--><!--Device-GestureGroup-onCancel(event: VoidCallback): GestureGroup-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [VoidCallback](arkts-arkui-voidcallback-t.md) | 是 | 手势事件回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [GestureGroup](arkts-arkui-gesture-gesturegroup-c.md) |  |

