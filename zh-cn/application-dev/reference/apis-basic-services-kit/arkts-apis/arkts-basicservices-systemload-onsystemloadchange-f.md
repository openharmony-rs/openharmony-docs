# onSystemLoadChange

## 导入模块

```TypeScript
import { systemLoad } from '@kit.BasicServicesKit';
```

## onSystemLoadChange

```TypeScript
function onSystemLoadChange(callback: Callback<SystemLoadLevel>): void
```

Register system load callback for perception system load change

**起始版本：** 23

<!--Device-systemLoad-function onSystemLoadChange(callback: Callback<SystemLoadLevel>): void--><!--Device-systemLoad-function onSystemLoadChange(callback: Callback<SystemLoadLevel>): void-End-->

**系统能力：** SystemCapability.ResourceSchedule.SystemLoad

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](arkts-basicservices-callback-t.md)&lt;[SystemLoadLevel](arkts-basicservices-systemload-systemloadlevel-e.md)&gt; | 是 | Asynchronous callback interface. |

