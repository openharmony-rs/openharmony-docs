# Usage

```TypeScript
type Usage = 'unknown' | 'alarm' | 'ring' | 'notification' | 'communication' |
  'touch' | 'media' | 'physicalFeedback' | 'simulateReality'
```

振动使用场景。不同usage值对应不同的系统振动开关管控规则，开发者需根据实际业务场景选择合适的usage值。<!--RP1End-->

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Sensors.MiscDevice

| 类型 | 说明 |
| --- | --- |
| 'unknown' | 没有明确使用场景，最低优先级，值固定为'unknown'字符串。不受特定振动开关管控。 |
| 'alarm' | 用于警报场景，值固定为'alarm'字符串。受闹钟振动开关管控。 |
| 'ring' | 用于铃声场景，值固定为'ring'字符串。受铃声振动开关管控。 |
| 'notification' | 用于通知场景，值固定为'notification'字符串。受通知振动开关管控。 |
| 'communication' | 用于通信场景，值固定为'communication'字符串。受通信振动开关管控。 |
| 'touch' | 用于触摸场景，值固定为'touch'字符串。受触摸振动开关管控。 |
| 'media' | 用于多媒体场景，值固定为'media'字符串。受多媒体振动开关管控。 |
| 'physicalFeedback' | 用于物理反馈场景，值固定为'physicalFeedback'字符串。受物理反馈振动开关管控。 |
| 'simulateReality' | 用于模拟现实场景，值固定为'simulateReality'字符串。受模拟现实振动开关管控。 |
