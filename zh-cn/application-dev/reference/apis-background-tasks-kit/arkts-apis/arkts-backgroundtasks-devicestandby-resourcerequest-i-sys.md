# ResourceRequest（系统接口）

待机资源请求体。

**起始版本：** 23

<!--Device-deviceStandby-export interface ResourceRequest--><!--Device-deviceStandby-export interface ResourceRequest-End-->

**系统能力：** SystemCapability.ResourceSchedule.DeviceStandby

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { deviceStandby } from '@kit.BackgroundTasksKit';
```

## duration

```TypeScript
duration: int
```

豁免时长。 单位：s

**类型：** int

**起始版本：** 23

<!--Device-ResourceRequest-duration: int--><!--Device-ResourceRequest-duration: int-End-->

**系统能力：** SystemCapability.ResourceSchedule.DeviceStandby

**系统接口：** 此接口为系统接口。

## name

```TypeScript
name: string
```

应用名。

**类型：** string

**起始版本：** 23

<!--Device-ResourceRequest-name: string--><!--Device-ResourceRequest-name: string-End-->

**系统能力：** SystemCapability.ResourceSchedule.DeviceStandby

**系统接口：** 此接口为系统接口。

## reason

```TypeScript
reason: string
```

申请原因。

**类型：** string

**起始版本：** 23

<!--Device-ResourceRequest-reason: string--><!--Device-ResourceRequest-reason: string-End-->

**系统能力：** SystemCapability.ResourceSchedule.DeviceStandby

**系统接口：** 此接口为系统接口。

## resourceTypes

```TypeScript
resourceTypes: int
```

资源类型，类型具体说明请参考[ResourceType](arkts-backgroundtasks-devicestandby-resourcetype-e-sys.md)。

**类型：** int

**起始版本：** 23

<!--Device-ResourceRequest-resourceTypes: int--><!--Device-ResourceRequest-resourceTypes: int-End-->

**系统能力：** SystemCapability.ResourceSchedule.DeviceStandby

**系统接口：** 此接口为系统接口。

## uid

```TypeScript
uid: int
```

应用uid。

**类型：** int

**起始版本：** 23

<!--Device-ResourceRequest-uid: int--><!--Device-ResourceRequest-uid: int-End-->

**系统能力：** SystemCapability.ResourceSchedule.DeviceStandby

**系统接口：** 此接口为系统接口。

