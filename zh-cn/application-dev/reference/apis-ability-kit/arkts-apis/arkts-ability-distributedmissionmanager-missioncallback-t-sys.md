# MissionCallback（系统接口）

```TypeScript
export type MissionCallback = _MissionCallback
```

作为可以 [registerMissionListener](arkts-ability-distributedmissionmanager-registermissionlistener-f-sys.md) 的入参，用于监听任务状态变化的回调函数，包含任务列表变化通知、任务快照通知和断开连接通知等功能。表示注册监听后建立的回调函数。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**属性类型：** _MissionCallback
