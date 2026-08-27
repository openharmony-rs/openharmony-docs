# destroyStream（系统接口）

## 导入模块

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
```

## destroyStream

```TypeScript
function destroyStream(streamId: number): void
```

发送图片和视频流等业务结束后，创建传输流的应用应及时销毁传输流，否则会增加系统功耗。 需与createStream()方法配对使用，在业务结束后必须调用此方法销毁传输流以释放资源。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| streamId | number | 是 | 表示传输流ID，需通过createStream接口创建传输流后获取。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**示例**

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let streamId = 100;
hilog.info(0x0000, 'testTag', 'destroyStream called');
abilityConnectionManager.destroyStream(streamId);
```
