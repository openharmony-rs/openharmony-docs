# getSurfaceId（系统接口）

## 导入模块

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
```

## getSurfaceId

```TypeScript
function getSurfaceId(streamId: number, param: SurfaceParam): string
```

获取指定传输流绑定的Surface的唯一标识符。Surface ID可用于将Surface与组件关联，实现音视频数据的显示。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| streamId | number | 是 | 表示传输流ID，需通过createStream接口创建传输流后获取。 |
| param | [SurfaceParam](arkts-distributedservice-abilityconnectionmanager-surfaceparam-i-sys.md) | 是 | 表示Surface的配置参数。需在流启动前完成Surface绑定。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Surface的唯一标识符，可用于后续setSurfaceId等操作。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**示例**

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

hilog.info(0x0000, 'testTag', 'getSurfaceId');
let sessionId = 100;
abilityConnectionManager.createStream(sessionId, {name: 'receive', role: 0}).then(async (streamId) => {
  let surfaceParam: abilityConnectionManager.SurfaceParam = {
    width: 640,
    height: 480,
    format: 1
  }
  let surfaceId = abilityConnectionManager.getSurfaceId(streamId, surfaceParam);
})
```
