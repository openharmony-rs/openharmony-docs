# 常量（系统接口）

## TIMER_TYPE_EXACT

```TypeScript
const TIMER_TYPE_EXACT: number
```

精准定时器（系统时间修改的情况下，可能会出现最多1s的前后偏移误差）。

**起始版本：** 7

<!--Device-systemTimer-const TIMER_TYPE_EXACT: int--><!--Device-systemTimer-const TIMER_TYPE_EXACT: int-End-->

**系统能力：** SystemCapability.MiscServices.Time

**系统接口：** 此接口为系统接口。

## TIMER_TYPE_IDLE

```TypeScript
const TIMER_TYPE_IDLE: number
```

IDLE模式定时器（仅支持系统服务配置，不支持应用配置）。

**起始版本：** 7

<!--Device-systemTimer-const TIMER_TYPE_IDLE: int--><!--Device-systemTimer-const TIMER_TYPE_IDLE: int-End-->

**系统能力：** SystemCapability.MiscServices.Time

**系统接口：** 此接口为系统接口。

## TIMER_TYPE_REALTIME

```TypeScript
const TIMER_TYPE_REALTIME: number
```

系统启动时间定时器（定时器启动时间不能晚于当前设置的系统时间）。

**起始版本：** 7

<!--Device-systemTimer-const TIMER_TYPE_REALTIME: int--><!--Device-systemTimer-const TIMER_TYPE_REALTIME: int-End-->

**系统能力：** SystemCapability.MiscServices.Time

**系统接口：** 此接口为系统接口。

## TIMER_TYPE_WAKEUP

```TypeScript
const TIMER_TYPE_WAKEUP: number
```

唤醒定时器（如果未配置为唤醒定时器，则系统处于休眠状态下不会触发，直到退出休眠状态）。

**起始版本：** 7

<!--Device-systemTimer-const TIMER_TYPE_WAKEUP: int--><!--Device-systemTimer-const TIMER_TYPE_WAKEUP: int-End-->

**系统能力：** SystemCapability.MiscServices.Time

**系统接口：** 此接口为系统接口。

