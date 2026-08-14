# KeyItem

其他按键信息。当前[KeyCode](arkts-mdm-systemmanager-keycode-e.md#KeyCode)事件发生时，其他已被按下的按键信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-systemManager-interface KeyItem--><!--Device-systemManager-interface KeyItem-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## downTime

```TypeScript
downTime: number
```

按键动作发生时间，系统开机后微秒级时间戳。导航按键不支持组合扩展，发生时间显示为0。

**类型：** number

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KeyItem-downTime: number--><!--Device-KeyItem-downTime: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## keyCode

```TypeScript
keyCode: KeyCode
```

按键编码。

**类型：** KeyCode

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KeyItem-keyCode: KeyCode--><!--Device-KeyItem-keyCode: KeyCode-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## pressed

```TypeScript
pressed: boolean
```

按键动作。按键是否被按下。true：按下；false：抬起

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KeyItem-pressed: boolean--><!--Device-KeyItem-pressed: boolean-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

