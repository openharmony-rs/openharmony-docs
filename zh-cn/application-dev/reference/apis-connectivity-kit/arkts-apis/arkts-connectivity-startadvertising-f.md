# startAdvertising

## startAdvertising

```TypeScript
function startAdvertising(advertisingParams: AdvertisingParams): Promise<number>
```

开始广播。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| advertisingParams | AdvertisingParams | 是 | 表示广播参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | 返回广播句柄promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported because the chip does not support it. |
| 36100003 | NearLink disabled. |
| 36100040 | Integer out of range. |
| 36100043 | Invalid UUID. |
| 36100099 | Operation failed. |

