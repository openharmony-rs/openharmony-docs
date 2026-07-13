# MinSpeed

任务的最低限速配置。若任务速度持续低于设定值并达到指定时长，则任务失败，失败原因为
[LOW_SPEED](arkts-basicservices-faults-e.md)。

**起始版本：** 20

**系统能力：** SystemCapability.Request.FileTransferAgent

## duration

```TypeScript
duration: number
```

允许低于最低速度的持续时间，单位为秒。若任务速度持续低于设定值达到该时长，则任务失败。设置为0表示不启用最低速度限制。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.Request.FileTransferAgent

## speed

```TypeScript
speed: number
```

任务最低速度，单位为字节每秒（B/s）。若任务速度持续低于该值达到指定时长，则任务失败。设置为0表示不启用最低速度限制。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.Request.FileTransferAgent

