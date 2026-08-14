# offScanDeviceAdd（系统接口）

## offScanDeviceAdd

```TypeScript
function offScanDeviceAdd(callback?: Callback<ScannerDevice>): void
```

Unregister event callback for scanner device add (system API).

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

<!--Device-scan-function offScanDeviceAdd(callback?: Callback<ScannerDevice>): void--><!--Device-scan-function offScanDeviceAdd(callback?: Callback<ScannerDevice>): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](arkts-basicservices-callback-t.md)&lt;[ScannerDevice](arkts-basicservices-scan-scannerdevice-i.md)&gt; | 否 | Optional callback to unregister. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |

