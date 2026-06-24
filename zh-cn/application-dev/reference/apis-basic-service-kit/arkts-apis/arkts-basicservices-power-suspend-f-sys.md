# suspend（系统接口）

## suspend

```TypeScript
function suspend(isImmediate?: boolean): void
```

使设备进入睡眠状态。

**起始版本：** 9

**需要权限：** ohos.permission.POWER_MANAGER

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isImmediate | boolean | 否 | 是否直接使设备进入睡眠状态。true表示灭屏后立即进入睡眠，不填该参数则默认为false，表示灭屏后由系统自动检测何时进入睡眠。如果只想做灭屏操作，建议不填参数。**说明：** 从API version 10开始，支持该参数。 [since 10] |

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
    power.suspend();
} catch(err) {
    console.error('suspend failed, err: ' + err);
}

```

