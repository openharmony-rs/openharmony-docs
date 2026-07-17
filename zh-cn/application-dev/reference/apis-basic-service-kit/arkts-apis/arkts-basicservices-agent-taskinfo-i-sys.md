# TaskInfo

查询结果的任务信息数据结构，提供普通查询和系统查询，两种字段的可见范围不同。

**起始版本：** 10

<!--Device-agent-interface TaskInfo--><!--Device-agent-interface TaskInfo-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## 导入模块

```TypeScript
import { request } from '@kit.BasicServicesKit';
```

## bundle

```TypeScript
readonly bundle?: string
```

The bundle name.For system query only.

**类型：** string

**起始版本：** 10

<!--Device-TaskInfo-readonly bundle?: string--><!--Device-TaskInfo-readonly bundle?: string-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

**系统接口：** 此接口为系统接口。

## uid

```TypeScript
readonly uid?: string
```

The UID of an application.For system query only.

**类型：** string

**起始版本：** 10

<!--Device-TaskInfo-readonly uid?: string--><!--Device-TaskInfo-readonly uid?: string-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

**系统接口：** 此接口为系统接口。

