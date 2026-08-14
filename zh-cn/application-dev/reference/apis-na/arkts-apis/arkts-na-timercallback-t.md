# TimerCallback

```TypeScript
export type TimerCallback = (utc: long, elapsedTime: long) => void
```

时间文本发生变化时触发该事件。锁屏状态和应用后台状态下不会触发该事件。设置高精度的format（SSS、SS）时，回调间隔可能会出现波动。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type TimerCallback = (utc: long, elapsedTime: long) => void--><!--Device-unnamed-export type TimerCallback = (utc: long, elapsedTime: long) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| utc | long | 是 |  |
| elapsedTime | long | 是 |  |

