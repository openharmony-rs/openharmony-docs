# offSystemLoadChange

## 导入模块

```TypeScript
import { systemLoad } from '@kit.BasicServicesKit';
```

## offSystemLoadChange

```TypeScript
function offSystemLoadChange(callback?: Callback<SystemLoadLevel>): void
```

Unregister system load callback for perception system load change

**起始版本：** 23

<!--Device-systemLoad-function offSystemLoadChange(callback?: Callback<SystemLoadLevel>): void--><!--Device-systemLoad-function offSystemLoadChange(callback?: Callback<SystemLoadLevel>): void-End-->

**系统能力：** SystemCapability.ResourceSchedule.SystemLoad

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](arkts-basicservices-callback-t.md)&lt;[SystemLoadLevel](arkts-basicservices-systemload-systemloadlevel-e.md)&gt; | 否 | Asynchronous callback interface. |

