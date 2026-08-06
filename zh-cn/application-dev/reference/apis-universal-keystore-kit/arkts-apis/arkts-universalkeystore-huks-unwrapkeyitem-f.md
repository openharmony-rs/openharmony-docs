# unwrapKeyItem

## unwrapKeyItem

```TypeScript
function unwrapKeyItem(keyAlias: string, params: HuksOptions, wrappedKey: Uint8Array): Promise<HuksReturnResult>
```

加密导入密钥。使用Promise异步回调。 > **说明：** > > 加密导入[HuksKeySecurityLevel]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_中定义的SE安全级别密钥需要ohos.permission.ACCESS\_SE\_KEY权限。 \_\_\_MD\_COMMENT\_DESC\_USD\_1\_\_\_该功能暂不支持。\_\_\_MD\_COMMENT\_DESC\_USD\_2\_\_\_

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-huks-function unwrapKeyItem(keyAlias: string, params: HuksOptions, wrappedKey: Uint8Array): Promise<HuksReturnResult>--><!--Device-huks-function unwrapKeyItem(keyAlias: string, params: HuksOptions, wrappedKey: Uint8Array): Promise<HuksReturnResult>-End-->

**系统能力：** SystemCapability.Security.Huks.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyAlias | string | 是 | 密钥别名，指定导入密钥的密钥别名。 |
| params | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 用于指定导入密钥时的加密类型。 |
| wrappedKey | Uint8Array | 是 | 加密导出密钥的密文。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HuksReturnResult&gt; | Promise对象，返回调用接口的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application permissions are insufficient, possibly because the ohos.permission.ACCESS\_\_\_ESCAPED\_UNDERSCORE\_\_\_SE\_\_\_ESCAPED\_UNDERSCORE\_\_\_KEY permission is missing.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 26.0.0+ |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | api is not supported |
| [12000004](../errorcode-huks.md#12000004-文件错误) | operating file failed |
| [12000005](../errorcode-huks.md#12000005-进程通信错误) | IPC communication failed |
| [12000012](../errorcode-huks.md#12000012-外部错误) | Device environment or input parameter abnormal |
| [12000014](../errorcode-huks.md#12000014-内存不足) | memory is insufficient |
| [12000015](../errorcode-huks.md#12000015-调用其他系统服务失败) | Failed to obtain the security information via UserIAM |
| [12000018](../errorcode-huks.md#12000018-输入参数非法) | the input parameter is invalid |
| [12000026](../errorcode-huks.md#12000026-安全元件故障) | the secure element is not available\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 26.0.0+ |

