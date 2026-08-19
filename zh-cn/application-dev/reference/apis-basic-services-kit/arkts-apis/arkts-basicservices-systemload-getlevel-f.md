# getLevel

## 导入模块

```TypeScript
import { systemLoad } from '@kit.BasicServicesKit';
```

## getLevel

```TypeScript
function getLevel(): Promise<SystemLoadLevel>
```

获取系统负载融合档位，使用promise异步回调。

**起始版本：** 23

<!--Device-systemLoad-function getLevel(): Promise<SystemLoadLevel>--><!--Device-systemLoad-function getLevel(): Promise<SystemLoadLevel>-End-->

**系统能力：** SystemCapability.ResourceSchedule.SystemLoad

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[SystemLoadLevel](arkts-basicservices-systemload-systemloadlevel-e.md)&gt; | Promise对象，返回系统负载融合档位。 |

