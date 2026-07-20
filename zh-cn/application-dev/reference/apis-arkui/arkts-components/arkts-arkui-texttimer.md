# TextTimer

通过文本显示计时信息并控制其计时器状态的组件。

组件不可见（非锁屏状态和应用后台状态）时，UI时间变动将停止（即该组件此时不会绘制），[onTimer]{@link TextTimerAttribute#onTimer}仍然会正常触发。

## 子组件

无

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
| options | [TextTimerOptions](arkts-arkui-texttimeroptions-i.md) | 否 | 通过文本显示计时信息并控制其计时器状态的组件参数。  |

## 汇总

- [TextTimerConfiguration](arkts-arkui-texttimer-texttimerconfiguration-i.md)
- [TextTimerOptions](arkts-arkui-texttimer-texttimeroptions-i.md)
