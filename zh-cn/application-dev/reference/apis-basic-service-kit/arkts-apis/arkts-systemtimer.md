# @ohos.systemTimer

本模块主要由系统定时器功能组成。开发者可以使用定时功能实现定时服务，如闹钟等。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare namespace systemTimer--><!--Device-unnamed-declare namespace systemTimer-End-->

**系统能力：** SystemCapability.MiscServices.Time

**系统接口：** 此接口为系统接口。

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [createTimer](arkts-basicservices-systemtimer-createtimer-f-sys.md#createTimer) | 创建定时器，使用callback异步回调。 > **注意：** > > 需与[systemTimer.destroyTimer](arkts-basicservices-systemtimer-destroytimer-f-sys.md#destroyTimer（系统接口）)结合使用，否则会造 > 成内存泄漏 |
| [createTimer](arkts-basicservices-systemtimer-createtimer-f-sys.md#createTimer（系统接口）) | 创建定时器，使用Promise异步回调返回定时器的ID。 > **注意：** > > 需与[systemTimer.destroyTimer](arkts-basicservices-systemtimer-destroytimer-f-sys.md#destroyTimer（系统接口）)结合使用，否则会造 > 成内存泄漏 |
| [destroyTimer](arkts-basicservices-systemtimer-destroytimer-f-sys.md#destroyTimer) | 销毁定时器，使用callback异步回调。 |
| [destroyTimer](arkts-basicservices-systemtimer-destroytimer-f-sys.md#destroyTimer（系统接口）) | 销毁定时器，使用Promise进行异步回调。 |
| [startTimer](arkts-basicservices-systemtimer-starttimer-f-sys.md#startTimer) | 开启定时器，使用callback异步回调。 |
| [startTimer](arkts-basicservices-systemtimer-starttimer-f-sys.md#startTimer（系统接口）) | 开启定时器，使用Promise进行异步回调。 |
| [stopTimer](arkts-basicservices-systemtimer-stoptimer-f-sys.md#stopTimer) | 该方法停止定时器，并使用callback进行异步回调。 |
| [stopTimer](arkts-basicservices-systemtimer-stoptimer-f-sys.md#stopTimer（系统接口）) | 此方法用于停止定时器，并使用Promise异步回调。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [TimerOptions](arkts-basicservices-systemtimer-timeroptions-i-sys.md) | 创建系统定时器的初始化选项。 |
<!--DelEnd-->

<!--Del-->
### 常量（系统接口）

| 名称 | 说明 |
| --- | --- |
| [TIMER_TYPE_EXACT](arkts-basicservices-systemtimer-con-sys.md#TIMER_TYPE_EXACT) | 精准定时器（系统时间修改的情况下，可能会出现最多1s的前后偏移误差）。 |
| [TIMER_TYPE_IDLE](arkts-basicservices-systemtimer-con-sys.md#TIMER_TYPE_IDLE) | IDLE模式定时器（仅支持系统服务配置，不支持应用配置）。 |
| [TIMER_TYPE_REALTIME](arkts-basicservices-systemtimer-con-sys.md#TIMER_TYPE_REALTIME) | 系统启动时间定时器（定时器启动时间不能晚于当前设置的系统时间）。 |
| [TIMER_TYPE_WAKEUP](arkts-basicservices-systemtimer-con-sys.md#TIMER_TYPE_WAKEUP) | 唤醒定时器（如果未配置为唤醒定时器，则系统处于休眠状态下不会触发，直到退出休眠状态）。 |
<!--DelEnd-->

