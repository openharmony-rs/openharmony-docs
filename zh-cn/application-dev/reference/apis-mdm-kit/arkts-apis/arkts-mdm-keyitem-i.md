# KeyItem

其他按键信息。当前[KeyCode](arkts-mdm-keycode-e.md)事件发生时，其他已被按下的按键信息。

**起始版本：** 23

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## downTime

```TypeScript
downTime: number
```

按键动作发生时间，系统开机后微秒级时间戳。导航按键不支持组合扩展，发生时间显示为0。
取值范围为全体整数。

**类型：** number

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

## pressed

```TypeScript
pressed: boolean
```

按键动作。按键是否被按下。true：按下；false：抬起

**类型：** boolean

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

