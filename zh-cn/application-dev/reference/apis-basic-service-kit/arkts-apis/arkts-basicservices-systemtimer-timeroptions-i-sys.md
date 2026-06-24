# TimerOptions（系统接口）

创建系统定时器的初始化选项。

**起始版本：** 7

**系统能力：** SystemCapability.MiscServices.Time

**系统接口：** 此接口为系统接口。

## autoRestore

```TypeScript
autoRestore?: boolean
```

是否在设备重启后恢复。

true为重启后恢复，false为重启后不恢复。

仅支持非`TIMER_TYPE_REALTIME`类型且配置了wantAgent的定时器配置为true。

默认值为false。

**类型：** boolean

**起始版本：** 15

**系统能力：** SystemCapability.MiscServices.Time

**系统接口：** 此接口为系统接口。

## callback

```TypeScript
callback?: () => void
```

用户需要执行的回调函数。

默认值为空。

**类型：** () => void

**起始版本：** 7

**系统能力：** SystemCapability.MiscServices.Time

**系统接口：** 此接口为系统接口。

## interval

```TypeScript
interval?: number
```

定时器时间间隔，单位：毫秒。

如果是循环定时器，interval值最小为1s，最大为365天，建议interval值不小于5000毫秒；

单次定时器interval值为0。

默认值为0。

**类型：** number

**起始版本：** 7

**系统能力：** SystemCapability.MiscServices.Time

**系统接口：** 此接口为系统接口。

## name

```TypeScript
name?: string
```

定时器名称，长度不超过64字节。

同一个UID中不可以同时存在两个同名定时器。如果创建了一个和之前已创建的定时器名字相同的定时器，先创建的定时器会被销毁。

默认值为空字符串。

**类型：** string

**起始版本：** 15

**系统能力：** SystemCapability.MiscServices.Time

**系统接口：** 此接口为系统接口。

## repeat

```TypeScript
repeat: boolean
```

是否为循环定时器。true表示循环定时器，false表示单次定时器。

**类型：** boolean

**起始版本：** 7

**系统能力：** SystemCapability.MiscServices.Time

**系统接口：** 此接口为系统接口。

## type

```TypeScript
type: number
```

定时器类型，可以使用 '|' 多选。

取值为1，表示为系统启动时间定时器（定时器启动时间不能晚于当前设置的系统时间）；

取值为2，表示为唤醒定时器；

取值为4，表示为精准定时器（APP被冻结时，定时器也会被冻结，并且定时器受统一心跳管控，因此即使是精准定时器也不能确保在指定时间点触发）；

取值为8，表示为IDLE模式定时器（仅支持系统服务配置，不支持应用配置）。

**类型：** number

**起始版本：** 7

**系统能力：** SystemCapability.MiscServices.Time

**系统接口：** 此接口为系统接口。

## wantAgent

```TypeScript
wantAgent?: WantAgent
```

设置通知的WantAgent，定时器到期后通知（支持拉起应用MainAbility，不支持拉起ServiceAbility）。

默认值为空。

**类型：** WantAgent

**起始版本：** 7

**系统能力：** SystemCapability.MiscServices.Time

**系统接口：** 此接口为系统接口。

