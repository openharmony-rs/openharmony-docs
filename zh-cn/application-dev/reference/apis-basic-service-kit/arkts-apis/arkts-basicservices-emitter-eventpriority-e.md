# EventPriority

表示事件的优先级。

**起始版本：** 7

<!--Device-emitter-export enum EventPriority--><!--Device-emitter-export enum EventPriority-End-->

**系统能力：** SystemCapability.Notification.Emitter

## IMMEDIATE

```TypeScript
IMMEDIATE = 0
```

表示事件先于HIGH优先级投递。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-EventPriority-IMMEDIATE = 0--><!--Device-EventPriority-IMMEDIATE = 0-End-->

**系统能力：** SystemCapability.Notification.Emitter

## HIGH

```TypeScript
HIGH
```

表示事件先于LOW优先级投递。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-EventPriority-HIGH--><!--Device-EventPriority-HIGH-End-->

**系统能力：** SystemCapability.Notification.Emitter

## LOW

```TypeScript
LOW
```

表示事件优于IDLE优先级投递，事件的默认优先级是LOW。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-EventPriority-LOW--><!--Device-EventPriority-LOW-End-->

**系统能力：** SystemCapability.Notification.Emitter

## IDLE

```TypeScript
IDLE
```

表示在没有其他事件的情况下，才投递该事件。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-EventPriority-IDLE--><!--Device-EventPriority-IDLE-End-->

**系统能力：** SystemCapability.Notification.Emitter

