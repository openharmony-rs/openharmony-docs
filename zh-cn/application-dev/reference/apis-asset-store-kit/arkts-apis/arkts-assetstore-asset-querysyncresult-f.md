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
| [24000001](../../errorcode-universal.md#24000001-The) | The ASSET service is unavailable. |
| [24000006](../../errorcode-universal.md#24000006-Insufficient) | Insufficient memory. |
| [24000010](../../errorcode-universal.md#24000010-IPC) | IPC failed. |
| [24000011](../../errorcode-universal.md#24000011-Calling) | Calling the Bundle Manager service failed. |
| [24000012](../../errorcode-universal.md#24000012-Calling) | Calling the OS Account service failed. |
| [24000013](../../errorcode-universal.md#24000013-Calling) | Calling the Access Token service failed. |
| [24000014](../../errorcode-universal.md#24000014-The) | The file operation failed. |
| [24000018](../../errorcode-universal.md#24000018-Parameter) | Parameter verification failed. |

**示例：**

```TypeScript
import { asset } from '@kit.AssetStoreKit';

let query: asset.AssetMap = new Map();
asset.querySyncResult(query).then((res: asset.SyncResult) => {
  console.info(`Succeeded in querying sync result: ${JSON.stringify(res)}`);
});

```

