# createServer

## createServer

```TypeScript
function createServer(name: string): Server
```

在服务端设备上，应用创建服务。通过start()开启后，该设备可作为服务端被其他设备连接。

**起始版本：** 20

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 自定义的非空字符串，标识应用的服务名，最大长度255字节。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Server | 创建成功的服务对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported<br/>because the linkEnhance function has been trimmed.&lt;br&gt;**适用版本：** 26.0.0+ |
| [32390206](../../errorcode-universal.md#32390206-Invalid) | Invalid parameter. |
| [32390203](../../errorcode-universal.md#32390203-Duplicate) | Duplicate server name. |

**示例：**

```TypeScript
import { linkEnhance } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG = "testDemo";

try {
  let name: string = "demo";
  hilog.info(0x0000, TAG, 'start server name = ' + name);
  // 使用服务名构造Server
  let server: linkEnhance.Server = linkEnhance.createServer(name);
} catch (err) {
  hilog.error(0x0000, TAG, 'start server errCode: ' + (err as BusinessError).code + ', errMessage: ' +
  (err as BusinessError).message);
}

```

