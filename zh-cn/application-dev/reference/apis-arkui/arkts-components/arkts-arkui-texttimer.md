# TextTimer

TextTimer是通过文本显示计时信息并控制其计时器状态的组件，支持正向计时与倒计时两种模式，可自定义显示格式，适用于秒表、活动倒计时等需要展示时间流逝的场景。常用于倒计时场景，如考试倒计时、限时活动、运动计时等。 组件不可见（非锁屏状态和应用后台状态）时，UI时间变动将停止（即该组件此时不会绘制），onTimer仍然会正常触发。

## 子组件 无

## TextTimer

```TypeScript
TextTimer(options?: TextTimerOptions)
```

创建文本计时器组件。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-TextTimerInterface-(options?: TextTimerOptions): TextTimerAttribute--><!--Device-TextTimerInterface-(options?: TextTimerOptions): TextTimerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [TextTimerOptions](arkts-arkui-texttimeroptions-i.md) | 否 | 通过文本显示计时信息并控制其计时器状态的组件参数。当需要自定义计时器配置（如设置倒计时开关、计时时间、初始时间、控制器等）时传入此参数；不传入时使用 TextTimerOptions的默认配置。 <br>默认值继承[TextTimerOptions](arkts-arkui-texttimeroptions-i.md) 。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [TextTimerConfiguration](arkts-arkui-texttimerconfiguration-i.md) | ContentModifier接口使用的TextTimer配置。 开发者需要自定义class实现ContentModifier接口。 |
| [TextTimerOptions](arkts-arkui-texttimeroptions-i.md) | 用于构建TextTimer组件的选项。 |

