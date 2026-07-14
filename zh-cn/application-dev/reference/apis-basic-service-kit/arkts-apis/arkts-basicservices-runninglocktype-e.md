# RunningLockType

RunningLock锁的类型。

**起始版本：** 7

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

## BACKGROUND

```TypeScript
BACKGROUND = 1
```

阻止系统睡眠的锁。

**说明：** 从API version 7开始支持，从API version 10开始废弃。

**起始版本：** 7

**废弃版本：** 10

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

## PROXIMITY_SCREEN_CONTROL

```TypeScript
PROXIMITY_SCREEN_CONTROL = 2
```

接近光锁，使能接近光传感器，并根据传感器与障碍物的距离远近发起亮灭屏流程。

**起始版本：** 7

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

## BACKGROUND_USER_IDLE

```TypeScript
BACKGROUND_USER_IDLE = 129
```

阻止系统自动睡眠的后台闲时任务锁，持锁能保证一段时间用户不活动后系统不进入自动睡眠。注意：不能阻止如PC合盖等场景系统进入强制睡眠，使用方必须监听
[进入强制睡眠公共事件](../../../../reference/apis-basic-services-kit/common_event/commonEventManager-definitions.md#common_event_enter_force_sleep12)
，监听到事件后释放该锁。该类型锁行为存在设备差异，使用该类型锁请参考
[阻止系统闲时进入睡眠开发指南](../../../../basic-services/powermgr/runningLock/runningLock-dev.md)。

**起始版本：** 23

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

