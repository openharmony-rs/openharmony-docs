# NotifyType（系统接口）

枚举，通知类型。

**起始版本：** 10

**废弃版本：** 23

**系统能力：** SystemCapability.FileManagement.UserFileService

**系统接口：** 此接口为系统接口。

## NOTIFY_ADD

```TypeScript
NOTIFY_ADD = 0
```

表示新增文件（详见registerObserver接口的示例2、示例3）。

**起始版本：** 10

**废弃版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.UserFileService

**系统接口：** 此接口为系统接口。

## NOTIFY_DELETE

```TypeScript
NOTIFY_DELETE = 1
```

表示删除文件（详见unregisterObserver(uri: string, callback: Callback<NotifyMessage>)接口的示例1、示例2）。

**起始版本：** 10

**废弃版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.UserFileService

**系统接口：** 此接口为系统接口。

## NOTIFY_MOVED_TO

```TypeScript
NOTIFY_MOVED_TO = 2
```

表示移动至该文件（对目录下子文件或目录执行rename操作，或外部文件或目录执行move操作到本文件。详见registerObserver接口的示例1，及unregisterObserver(uri: string)接口的示例
1）。

**起始版本：** 10

**废弃版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.UserFileService

**系统接口：** 此接口为系统接口。

## NOTIFY_MOVED_FROM

```TypeScript
NOTIFY_MOVED_FROM = 3
```

表示自该文件移出（对目录下子文件或目录执行rename操作，或子文件（夹）执行move操作从该文件夹内移出。详见registerObserver接口的示例1，及unregisterObserver(uri: string)接口
的示例1）。

**起始版本：** 10

**废弃版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.UserFileService

**系统接口：** 此接口为系统接口。

## NOTIFY_MOVE_SELF

```TypeScript
NOTIFY_MOVE_SELF = 4
```

表示本文件被移动（如对文件或文件夹执行rename或move操作时，监听该文件（夹）的callback收到该事件，详见registerObserver接口的示例1）。

**起始版本：** 10

**废弃版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.UserFileService

**系统接口：** 此接口为系统接口。

## NOTIFY_DEVICE_ONLINE

```TypeScript
NOTIFY_DEVICE_ONLINE = 5
```

表示设备上线。

**起始版本：** 11

**废弃版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.UserFileService

**系统接口：** 此接口为系统接口。

## NOTIFY_DEVICE_OFFLINE

```TypeScript
NOTIFY_DEVICE_OFFLINE = 6
```

表示设备下线。

**起始版本：** 11

**废弃版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.UserFileService

**系统接口：** 此接口为系统接口。

