# setSurfaceId（系统接口）

## 导入模块

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
```

## setSurfaceId

```TypeScript
function setSurfaceId(streamId: number, surfaceId: string, param: SurfaceParam): void
```

设置传输流与Surface的绑定关系。Surface用于承载音视频数据的显示或采集， 绑定后传输流的音视频数据将直接渲染到Surface上或从Surface采集数据。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| streamId | number | 是 | 表示传输流ID，需通过createStream接口创建传输流后获取。 |
| surfaceId | string | 是 | 表示Surface的唯一标识符，需通过getSurfaceId接口获取。 |
| param | [SurfaceParam](arkts-distributedservice-abilityconnectionmanager-surfaceparam-i-sys.md) | 是 | 表示Surface的配置参数，包括编码宽度、高度、像素格式等。 配置后Surface将按照指定参数进行视频帧的编码和渲染。需在流启动前完成绑定。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**示例**

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

hilog.info(0x0000, 'testTag', 'setSurfaceId');
let sessionId = 100;
abilityConnectionManager.createStream(sessionId, {name: 'receive', role: 0}).then(async (streamId) => {
  let surfaceParam: abilityConnectionManager.SurfaceParam = {
    width: 640,
    height: 480,
    format: 1
  }
  let surfaceId = abilityConnectionManager.getSurfaceId(streamId, surfaceParam);
  // 设置传输流与Surface的绑定关系
  abilityConnectionManager.setSurfaceId(streamId, surfaceId, surfaceParam);
})
```
