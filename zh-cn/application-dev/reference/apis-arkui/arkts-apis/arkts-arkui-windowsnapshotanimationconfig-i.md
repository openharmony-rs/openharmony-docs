# WindowSnapshotAnimationConfig

窗口截图动效的配置。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Window.SessionManager

## delay

```TypeScript
delay?: number
```

窗口截图淡出动效开始前的延迟时间（毫秒）。
如果未指定，则该参数默认为由系统动效上下文确定的值：
窗口状态在WindowStatusType.FLOATING和WindowStatusType.FULLSCREEN之间转换为50。
350适用于所有其他截图动效场景。
此参数的有效范围为0-350。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Window.SessionManager

## duration

```TypeScript
duration?: number
```

窗口截图淡出动效的持续时间（毫秒）。
如果未指定，则该参数默认为由系统动效上下文确定的值：
窗口状态在WindowStatusType.FLOING和WindowStatusType.FULLSCREEN之间转换为250。
400适用于所有其他屏幕截图动效场景。
此参数的有效范围为0-400。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Window.SessionManager

