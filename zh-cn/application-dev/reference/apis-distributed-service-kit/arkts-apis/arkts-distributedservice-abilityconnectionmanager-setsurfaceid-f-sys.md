# setSurfaceId（系统接口）

## setSurfaceId

```TypeScript
function setSurfaceId(streamId: int, surfaceId: string, param: SurfaceParam): void
```

Sets the transmission surface.

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-abilityConnectionManager-function setSurfaceId(streamId: int, surfaceId: string, param: SurfaceParam): void--><!--Device-abilityConnectionManager-function setSurfaceId(streamId: int, surfaceId: string, param: SurfaceParam): void-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| streamId | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | Indicates the ID of a transport stream. |
| surfaceId | string | 是 | Surface ID. |
| param | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Surface Parameters |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**示例：**

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

hilog.info(0x0000, 'testTag', 'setSurfaceId');
let sessionId = 100;
abilityConnectionManager.createStream(sessionId ,{name: 'receive', role: 0}).then(async (streamId) => {
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

