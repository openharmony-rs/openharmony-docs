# ExemptedAppInfo（系统接口）

豁免应用信息，未进入待机管控的应用信息。

**起始版本：** 10

**系统能力：** SystemCapability.ResourceSchedule.DeviceStandby

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { deviceStandby } from '@kit.BackgroundTasksKit';
```

## duration

```TypeScript
duration: number
```

豁免时长。单位：s

**类型：** number

**起始版本：** 10

**系统能力：** SystemCapability.ResourceSchedule.DeviceStandby

**系统接口：** 此接口为系统接口。

## name

```TypeScript
name: string
```

应用名。

**类型：** string

**起始版本：** 10

**系统能力：** SystemCapability.ResourceSchedule.DeviceStandby

**系统接口：** 此接口为系统接口。

## resourceTypes

```TypeScript
resourceTypes: number
```

资源类型，类型具体说明请参考[ResourceType](arkts-backgroundtasks-devicestandby-resourcetype-e-sys.md)。

**类型：** number

**起始版本：** 10

**系统能力：** SystemCapability.ResourceSchedule.DeviceStandby

**系统接口：** 此接口为系统接口。
