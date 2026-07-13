# destroyPort

## destroyPort

```TypeScript
function destroyPort(uuid: string): void
```

根据UUID销毁监听端口并释放相关资源。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uuid | string | 是 | 应用服务UUID<br>长度必须为36，由16进制数字字符和连字符共36个字符组成，形如“FFFFFFFF-1234-5678-ABCD-000000001234”，代表128比特标识。<br>不允许使用NearLink标准UUID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported because the chip does not support it. |
| 36100003 | NearLink disabled. |
| 36100022 | The UUID is not registered. |
| 36100043 | Invalid UUID. |
| 36100044 | NearLink standard UUID not allowed. |
| 36100099 | Operation failed. |

