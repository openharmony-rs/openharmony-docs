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

**起始版本：** 12

**系统能力：** SystemCapability.ResourceSchedule.SystemLoad

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[SystemLoadLevel](arkts-basicservices-systemload-systemloadlevel-e.md)&gt; | Promise对象，返回系统负载融合档位。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { systemLoad } from '@kit.BasicServicesKit';

systemLoad.getLevel().then((res: systemLoad.SystemLoadLevel) => {
    console.info(`getLevel promise succeeded. result: ` + JSON.stringify(res));
}).catch((err: BusinessError) => {
    console.error(`getLevel promise failed. code is ${err.code} message is ${err.message}`);
})
```
