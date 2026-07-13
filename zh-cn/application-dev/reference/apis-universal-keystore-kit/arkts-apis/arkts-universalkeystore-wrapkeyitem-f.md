# wrapKeyItem

## wrapKeyItem

```TypeScript
function wrapKeyItem(keyAlias: string, params: HuksOptions): Promise<HuksReturnResult>
```

加密导出密钥。使用Promise异步回调。

<!--Del-->该功能暂不支持。<!--DelEnd-->

**起始版本：** 20

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyAlias | string | 是 | 密钥别名，应与所用密钥生成时使用的别名相同。 |
| params | HuksOptions | 是 | 用于指定导出密钥时的加密类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HuksReturnResult&gt; | Promise对象，返回调用接口的结果。当调用成功时，HuksReturnResult的outData成员为导出的密钥密文。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | api is not supported |
| [12000004](../errorcode-huks.md#12000004-文件错误) | operating file failed |
| [12000005](../errorcode-huks.md#12000005-进程通信错误) | IPC communication failed |
| [12000011](../errorcode-huks.md#12000011-目标对象不存在) | queried entity does not exist |
| [12000012](../errorcode-huks.md#12000012-外部错误) | Device environment or input parameter abnormal |
| [12000014](../errorcode-huks.md#12000014-内存不足) | memory is insufficient |
| [12000018](../errorcode-huks.md#12000018-输入参数非法) | the input parameter is invalid |
| [12000026](../errorcode-huks.md#12000026-安全元件故障) | the secure element is not available<br>**适用版本：** 26.0.0+ |

