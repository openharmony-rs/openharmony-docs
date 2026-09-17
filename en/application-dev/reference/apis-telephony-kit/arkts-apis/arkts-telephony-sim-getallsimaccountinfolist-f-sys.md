# getAllSimAccountInfoList (System API)

## Modules to Import

```TypeScript
import { sim } from '@kit.TelephonyKit';
```

## getAllSimAccountInfoList

```TypeScript
function getAllSimAccountInfoList(callback: AsyncCallback<Array<IccAccountInfo>>): void
```

Get the list of all SIM card account information.

**Since:** 20

**Required permissions:** ohos.permission.GET_TELEPHONY_STATE

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[IccAccountInfo](arkts-telephony-sim-iccaccountinfo-i.md)&gt;&gt; | Yes | The callback is used to return the array of [IccAccountInfo](arkts-telephony-sim-iccaccountinfo-i.md). The ICCID and phone number will be null if has no ohos.permission.GET_TELEPHONY_STATE. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [8300001](../errorcode-telephony.md#8300001-input-parameter-value-out-of-range) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-service-connection-error) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-system-internal-error) | System internal error. |
| [8300004](../errorcode-telephony.md#8300004-sim-card-not-detected) | Do not have sim card. |
| [8300999](../errorcode-telephony.md#8300999-internal-error) | Unknown error code. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.getAllSimAccountInfoList((err: BusinessError) => {
    console.info(`callback: err->${JSON.stringify(err)}`);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

async getAllSimAccountInfoList(): Promise<ResponseData<sim.IccAccountInfo[] | null>> {
    try {
      const accountInfoList: sim.IccAccountInfo[] =
        await sim.getAllSimAccountInfoList();
      return { success: true, code: CommonConstant.DEFAULT_SUCCESS_CODE, data: accountInfoList };
    } catch (err) {
      return this.handleError(this.getAllSimAccountInfoList.name, err);
    }
  }
```


## getAllSimAccountInfoList

```TypeScript
function getAllSimAccountInfoList(): Promise<Array<IccAccountInfo>>
```

Get the list of all SIM card account information.

**Since:** 20

**Required permissions:** ohos.permission.GET_TELEPHONY_STATE

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[IccAccountInfo](arkts-telephony-sim-iccaccountinfo-i.md)&gt;&gt; | Returns the array of [IccAccountInfo](arkts-telephony-sim-iccaccountinfo-i.md). The ICCID and phone number will be null if has no ohos.permission.GET_TELEPHONY_STATE. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [8300002](../errorcode-telephony.md#8300002-service-connection-error) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-system-internal-error) | System internal error. |
| [8300004](../errorcode-telephony.md#8300004-sim-card-not-detected) | Do not have sim card. |
| [8300999](../errorcode-telephony.md#8300999-internal-error) | Unknown error code. |

**Examples**

See [getAllSimAccountInfoList](#getallsimaccountinfolist)
