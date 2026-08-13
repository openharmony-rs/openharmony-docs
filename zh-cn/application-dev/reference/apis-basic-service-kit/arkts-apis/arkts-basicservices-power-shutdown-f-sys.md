# shutdown（系统接口）

## shutdown

```TypeScript
function shutdown(reason: string): void
```

系统关机。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.REBOOT

<!--Device-power-function shutdown(reason: string): void--><!--Device-power-function shutdown(reason: string): void-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| reason | string | 是 | 关机原因；该参数必须为字符串类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Incorrect parameter types; |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [4900101](../../apis-basic-services-kit/errorcode-power.md#4900101-连接服务失败) | Failed to connect to the service. |

## 示例

```TypeScript
try {
    power.shutdown('shutdown_test');
} catch(err) {
    console.error('shutdown failed, err: ' + err);
}
```

