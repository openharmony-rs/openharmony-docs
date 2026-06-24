# hibernate（系统接口）

## hibernate

```TypeScript
function hibernate(clearMemory: boolean): void
```

休眠设备。

**起始版本：** 12

**需要权限：** ohos.permission.POWER_MANAGER

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| clearMemory | boolean | 是 | true 代表在进入休眠之前清理内存，否则为false。 |

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
    power.hibernate(true);
} catch(err) {
    console.error('hibernate failed, err: ' + err);
}

```

