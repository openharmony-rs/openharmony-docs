# component/textTimer

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [TextTimerController](texttimer-texttimercontroller-c.md) | TextTimer组件的控制器，用于控制文本计时器。一个TextTimer组件仅支持绑定一个控制器，组件创建完成后相关指令才能被调用。一个TextTimerController只能控制最后一个绑定此 TextTimerController的TextTimer组件。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [TextTimerConfiguration](texttimer-texttimerconfiguration-i.md) | ContentModifier接口使用的TextTimer配置。 开发者需要自定义class实现ContentModifier接口。 |
| [TextTimerOptions](texttimer-texttimeroptions-i.md) | 用于构建TextTimer组件的选项。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [TimerCallback](arkts-arkui-timercallback-t.md) | 时间文本发生变化时触发该事件。锁屏状态和应用后台状态下不会触发该事件。设置高精度的format（SSS、SS）时，回调间隔可能会出现波动。 |

