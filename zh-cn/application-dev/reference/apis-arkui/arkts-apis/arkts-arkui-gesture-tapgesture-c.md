# TapGesture

支持单击、双击和多次点击事件的识别。 > **说明：** > > 当组件同时绑定双击和单击手势且双击手势先绑定时，单击手势会有300ms的延时。

**继承/实现关系：** TapGesture extends [Gesture](arkts-arkui-gesture-gesture-c.md#Gesture)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare class TapGesture--><!--Device-unnamed-export declare class TapGesture-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## $_instantiate

```TypeScript
static $_instantiate(factory: () => TapGesture, value?: TapGestureParameters): TapGesture
```

创建点击手势对象。继承自[Gesture](arkts-arkui-gesture-gesture-c.md#Gesture)。 触发点击手势事件的设备类型为键盘或手柄时，事件的SourceTool值为Unknown，事件的SourceType值为KEY或JOYSTICK。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TapGesture-static $_instantiate(factory: () => TapGesture, value?: TapGestureParameters): TapGesture--><!--Device-TapGesture-static $_instantiate(factory: () => TapGesture, value?: TapGestureParameters): TapGesture-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| factory | () =&gt; TapGesture | 是 |  |
| value | [TapGestureParameters](arkts-arkui-gesture-tapgestureparameters-i.md) | 否 | 点击手势的相关参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TapGesture](arkts-arkui-gesture-tapgesture-c.md) |  |

## onAction

```TypeScript
onAction(event: Callback<GestureEvent>): this
```

点击手势识别成功回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TapGesture-onAction(event: Callback<GestureEvent>): this--><!--Device-TapGesture-onAction(event: Callback<GestureEvent>): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;[GestureEvent](arkts-arkui-gesture-gestureevent-i.md)&gt; | 是 | 手势事件回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

