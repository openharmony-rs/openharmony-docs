# KeyEvent

按键事件。
[EnterpriseAdminExtensionAbility.onKeyEvent](arkts-mdm-enterpriseadminextensionability-c.md#onkeyevent-1)
按键事件回调触发时，传递当前按键事件信息。

**起始版本：** 23

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## actionTime

```TypeScript
actionTime: number
```

按键动作发生时间，系统开机后微秒级时间戳。当按键长按时后续按键事件该参数不发生改变，应用可以通过该时间来判断该事件是否属于长按事件，以执行长按事件逻辑处理。
取值范围为全体整数。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## keyAction

```TypeScript
keyAction: KeyAction
```

按键动作。

**类型：** KeyAction

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## keyCode

```TypeScript
keyCode: KeyCode
```

按键编码。

**类型：** KeyCode

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## keyItems

```TypeScript
keyItems: Array<KeyItem>
```

其他按键信息，当前按键事件发生时，其他正在被按下的按键信息。

**类型：** Array<KeyItem>

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

