# setCBConfigList (System API)

## Modules to Import

```TypeScript
import { sms } from '@kit.TelephonyKit';
```

## setCBConfigList

```TypeScript
function setCBConfigList(configs: CBConfigListConfigs): Promise<void>
```

Turn on Cell BroadCast by list.

**Since:** 23

**Required permissions:** ohos.permission.RECEIVE_SMS

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| configs | [CBConfigListConfigs](arkts-telephony-sms-cbconfiglistconfigs-i-sys.md) | Yes | Indicates cell broadcast configuration list configs. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | The promise returned by the setCBConfigList. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [8300001](../errorcode-telephony.md#8300001-input-parameter-value-out-of-range) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-service-connection-error) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-system-internal-error) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-internal-error) | Unknown error code. |
