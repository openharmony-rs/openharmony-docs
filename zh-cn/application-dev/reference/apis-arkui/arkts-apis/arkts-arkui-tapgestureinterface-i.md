# TapGestureInterface

支持单击、双击和多次点击事件的识别。 > **说明：** > > 当组件同时绑定双击和单击手势且双击手势先绑定时，单击手势会有300ms的延时。

**继承/实现关系：** TapGestureInterface extends [GestureInterface<TapGestureInterface>](GestureInterface<TapGestureInterface>)

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

<!--Device-unnamed-interface TapGestureInterface extends GestureInterface<TapGestureInterface>--><!--Device-unnamed-interface TapGestureInterface extends GestureInterface<TapGestureInterface>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
(value?: TapGestureParameters): TapGestureInterface
```

创建点击手势对象。继承自[GestureInterface\_\_\_HTML\_TAG\_DESC\_USD\_3\_\_\_]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。 触发点击手势事件的设备类型为键盘或手柄时，事件的[SourceTool]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_值为Unknown，事件的[SourceType]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_值为KEY或JOYSTICK。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TapGestureInterface-(value?: TapGestureParameters): TapGestureInterface--><!--Device-TapGestureInterface-(value?: TapGestureParameters): TapGestureInterface-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 点击手势的相关参数。\_\_\_HTML\_TAG\_USD\_0\_\_\_**起始版本：** 12 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ |  |

## onAction

```TypeScript
onAction(event: (event: GestureEvent) => void): TapGestureInterface
```

点击手势识别成功回调。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TapGestureInterface-onAction(event: (event: GestureEvent) => void): TapGestureInterface--><!--Device-TapGestureInterface-onAction(event: (event: GestureEvent) => void): TapGestureInterface-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (event: GestureEvent) =&gt; void | 是 | 手势事件回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ |  |

