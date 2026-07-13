# querySyncResult

## querySyncResult

```TypeScript
function querySyncResult(query: AssetMap): Promise<SyncResult>
```

执行同步操作后，查询同步执行结果。使用Promise异步回调。

**起始版本：** 20

**系统能力：** SystemCapability.Security.Asset

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| query | AssetMap | 是 | 同步结果查询条件，如关键资产所属群组、业务自定义属性信息是否加密。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;SyncResult&gt; | Promise对象，返回同步执行结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [24000001](../errorcode-asset.md#24000001-关键资产服务不可用) | The ASSET service is unavailable. |
| [24000006](../errorcode-asset.md#24000006-系统内存不足) | Insufficient memory. |
| [24000010](../errorcode-asset.md#24000010-进程通信错误) | IPC failed. |
| [24000011](../errorcode-asset.md#24000011-包管理服务异常) | Calling the Bundle Manager service failed. |
| [24000012](../errorcode-asset.md#24000012-账号系统服务异常) | Calling the OS Account service failed. |
| [24000013](../errorcode-asset.md#24000013-访问控制服务异常) | Calling the Access Token service failed. |
| [24000014](../errorcode-asset.md#24000014-文件操作失败) | The file operation failed. |
| [24000018](../errorcode-asset.md#24000018-参数校验失败) | Parameter verification failed. |

**示例：**

```TypeScript
import { asset } from '@kit.AssetStoreKit';

let query: asset.AssetMap = new Map();
asset.querySyncResult(query).then((res: asset.SyncResult) => {
  console.info(`Succeeded in querying sync result: ${JSON.stringify(res)}`);
});

```

