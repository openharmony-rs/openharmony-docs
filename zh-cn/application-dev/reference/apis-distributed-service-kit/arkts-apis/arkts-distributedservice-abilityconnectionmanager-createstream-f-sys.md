# createStream（系统接口）

## 导入模块

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
```

<a id="createstream"></a>
## createStream

```TypeScript
function createStream(sessionId: number, param: StreamParam): Promise<number>
```

Creating a Stream.

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-abilityConnectionManager-function createStream(sessionId: int, param: StreamParam): Promise<int>--><!--Device-abilityConnectionManager-function createStream(sessionId: int, param: StreamParam): Promise<int>-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sessionId | number | 是 | Ability connection Session id. |
| param | [StreamParam](arkts-distributedservice-abilityconnectionmanager-streamparam-i-sys.md) | 是 | Transport Stream Parameters |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | The promise returned by the function, contain the ID of a transport stream. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [32300001](../../apis-distributedservice-kit/errorcode-device-manager.md#32300001-重复创建传输流) | Only one stream can be created for the current session. |
| [32300003](../../apis-distributedservice-kit/errorcode-device-manager.md#32300003-比特率不支持) | Bitrate not supported. |
| [32300004](../../apis-distributedservice-kit/errorcode-device-manager.md#32300004-色彩空间不支持) | Color space not supported. |

**示例：**

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

hilog.info(0x0000, 'testTag', 'startStream');
let sessionId = 100;
// 创建传输流，配置名称为'receive'，角色为SOURCE（发送流）
abilityConnectionManager.createStream(sessionId, {name: 'receive', role: 0}).then(async (streamId) => {
  // 配置Surface参数
  let surfaceParam: abilityConnectionManager.SurfaceParam = {
    width: 640,
    height: 480,
    format: 1
  }
  // 获取Surface唯一标识符
  let surfaceId = abilityConnectionManager.getSurfaceId(streamId, surfaceParam);
  hilog.info(0x0000, 'testTag', 'surfaceId is ' + surfaceId);
  // 将SurfaceID存储到全局状态管理中，供后续UI组件使用
  AppStorage.setOrCreate<string>('surfaceId', surfaceId);
  // 启动传输流
  abilityConnectionManager.startStream(streamId);
})

```

