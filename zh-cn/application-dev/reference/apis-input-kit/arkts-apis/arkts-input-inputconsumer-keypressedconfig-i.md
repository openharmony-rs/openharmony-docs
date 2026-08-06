# KeyPressedConfig

按键事件消费设置。

**起始版本：** 16

**ArkTS模式：** ArkTS-Dyn起始版本为16；ArkTS-Sta起始版本为23。

<!--Device-inputConsumer-interface KeyPressedConfig--><!--Device-inputConsumer-interface KeyPressedConfig-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputConsumer

## action

```TypeScript
action: int
```

订阅指定的按键事件。 **说明：** 从API version 21开始，支持取值为1和2，取值为1表示订阅按键按下事件，取值为2表示同时订阅按键按下事件和按键抬起事件。 对于API version 20及之前的版本，仅支持取值为1，表示订阅按键按下事件。

**类型：** int

**起始版本：** 16

**ArkTS模式：** ArkTS-Dyn起始版本为16；ArkTS-Sta起始版本为23。

<!--Device-KeyPressedConfig-action: int--><!--Device-KeyPressedConfig-action: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputConsumer

## isRepeat

```TypeScript
isRepeat: boolean
```

是否上报重复的按键事件。true表示上报，false表示不上报，默认值为true。

**类型：** boolean

**起始版本：** 16

**ArkTS模式：** ArkTS-Dyn起始版本为16；ArkTS-Sta起始版本为23。

<!--Device-KeyPressedConfig-isRepeat: boolean--><!--Device-KeyPressedConfig-isRepeat: boolean-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputConsumer

## key

```TypeScript
key: int
```

按键键值。 **说明：** 从API version 26.0.0开始，新增支持[KEYCODE\_FINGERPRINT\_SLIDE\_UP]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_键和 [KEYCODE\_FINGERPRINT\_SLIDE\_DOWN]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_键，非设备通用键值，使用前请判断当前设备是否支持相关按键事件上报，请参考 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。 从API version 21开始，新增支持[KEYCODE\_MEDIA\_PLAY\_PAUSE]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_键、 [KEYCODE\_MEDIA\_NEXT]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_键和 [KEYCODE\_MEDIA\_PREVIOUS]\_\_\_JSDOC\_LINK\_DESC\_USD\_5\_\_\_键。 对于API version 20及之前的版本，仅支持[KEYCODE\_VOLUME\_UP]\_\_\_JSDOC\_LINK\_DESC\_USD\_6\_\_\_键和 [KEYCODE\_VOLUME\_DOWN]\_\_\_JSDOC\_LINK\_DESC\_USD\_7\_\_\_键。

**类型：** int

**起始版本：** 16

**ArkTS模式：** ArkTS-Dyn起始版本为16；ArkTS-Sta起始版本为23。

<!--Device-KeyPressedConfig-key: int--><!--Device-KeyPressedConfig-key: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputConsumer

