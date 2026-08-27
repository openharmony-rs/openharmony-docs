# createStream（系统接口）

## 导入模块

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
```

## createStream

```TypeScript
function createStream(sessionId: number, param: StreamParam): Promise<number>
```

应用连接成功后，设备A或设备B可创建传输流，发送图片和视频流，使用Promise异步回调。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sessionId | number | 是 | 表示协同会话ID，需先创建协同会话后获取。 |
| param | [StreamParam](arkts-distributedservice-abilityconnectionmanager-streamparam-i-sys.md) | 是 | 表示传输流的配置信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;number & gt; | 返回传输流ID的Promise对象。后续操作传输流的接口（如setSurfaceId、getSurfaceId、 startStream、stopStream、destroyStream等）需要使用此ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [32300001](../errorcode-device-manager.md#32300001-重复创建传输流) | Only one stream can be created for the current session. |
| [32300003](../errorcode-device-manager.md#32300003-比特率不支持) | Bitrate not supported. |
| [32300004](../errorcode-device-manager.md#32300004-色彩空间不支持) | Color space not supported. |

**示例**

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
