# setScreenOffTime（系统接口）

## setScreenOffTime

```TypeScript
function setScreenOffTime(timeout: number): void
```

设置熄屏超时时间。

**起始版本：** 12

**需要权限：** ohos.permission.POWER_MANAGER

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timeout | number | 是 | 熄屏超时时间，单位是毫秒，大于0代表熄屏超时时间，-1代表恢复默认超时时间，其它是无效值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Parameter verification failed. |
| [4900101](../../errorcode-universal.md#4900101-Failed) | Failed to connect to the service. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API.&lt;br&gt;**适用版本：** 19+ |

**示例：**

```TypeScript
try {
    power.setScreenOffTime(30000);
} catch(err) {
    console.error('set screen off time failed, err: ' + err);
}

```

