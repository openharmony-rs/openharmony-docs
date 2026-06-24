# wakeup（系统接口）

## wakeup

```TypeScript
function wakeup(detail: string): void
```

唤醒设备。

**起始版本：** 9

**需要权限：** ohos.permission.POWER_MANAGER

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| detail | string | 是 | 唤醒原因；该参数必须为字符串类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Incorrect parameter types; |
| [4900101](../../errorcode-universal.md#4900101-Failed) | Failed to connect to the service. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API.&lt;br&gt;**适用版本：** 19+ |

**示例：**

```TypeScript
try {
    power.wakeup('wakeup_test');
} catch(err) {
    console.error('wakeup failed, err: ' + err);
}

```

