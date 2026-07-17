# TextClock

TextClock组件通过文本将当前系统时间显示在设备上。支持不同时区的时间显示，最高精度到秒级。

组件不可见时，时间变动将停止。组件的可见状态基于
[onVisibleAreaChange]{@link CommonMethod#onVisibleAreaChange(ratios: Array<number>, event: VisibleAreaChangeCallback)}
处理，可见阈值ratios大于0即视为可见状态。

## 子组件

无

## TextClock

```TypeScript
TextClock(options?: TextClockOptions)
```

创建文本时钟组件。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-TextClockInterface-(options?: TextClockOptions): TextClockAttribute--><!--Device-TextClockInterface-(options?: TextClockOptions): TextClockAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | TextClockOptions | 否 | 通过文本显示当前系统时间的组件参数。 |

## 汇总

- [TextClockConfiguration](arkts-arkui-textclock-textclockconfiguration-i.md)
- [TextClockOptions](arkts-arkui-textclock-textclockoptions-i.md)
