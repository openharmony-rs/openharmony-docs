# KeyEvent

按键事件。 [EnterpriseAdminExtensionAbility.onKeyEvent]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ 按键事件回调触发时，传递当前按键事件信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

<!--Device-systemManager-interface KeyEvent--><!--Device-systemManager-interface KeyEvent-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## actionTime

```TypeScript
actionTime: number
```

按键动作发生时间，系统开机后微秒级时间戳。当按键长按时后续按键事件该参数不发生改变，应用可以通过该时间来判断该事件是否属于长按事件，以执行长按事件逻辑处理。

**类型：** number

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KeyEvent-actionTime: number--><!--Device-KeyEvent-actionTime: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## keyAction

```TypeScript
keyAction: KeyAction
```

按键动作。

**类型：** KeyAction

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KeyEvent-keyAction: KeyAction--><!--Device-KeyEvent-keyAction: KeyAction-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## keyCode

```TypeScript
keyCode: KeyCode
```

按键编码。

**类型：** KeyCode

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KeyEvent-keyCode: KeyCode--><!--Device-KeyEvent-keyCode: KeyCode-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## keyItems

```TypeScript
keyItems: Array<KeyItem>
```

其他按键信息，当前按键事件发生时，其他正在被按下的按键信息。

**类型：** Array&lt;KeyItem&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KeyEvent-keyItems: Array<KeyItem>--><!--Device-KeyEvent-keyItems: Array<KeyItem>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

