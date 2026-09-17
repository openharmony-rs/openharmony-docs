# getAttestStatus (System API)

## Modules to Import

```TypeScript
import { deviceAttest } from '@kit.BasicServicesKit';
```

## getAttestStatus

```TypeScript
function getAttestStatus(callback: AsyncCallback<AttestResultInfo>): void
```

Obtains the AttestResultInfo object.

**Since:** 9

**System capability:** SystemCapability.XTS.DeviceAttest

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;[AttestResultInfo](arkts-basicservices-deviceattest-attestresultinfo-i-sys.md)&gt; | Yes | Indicates the callback containing the AttestResultInfo object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | This api is system api, Please use the system application to call this api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Input parameters wrong, the number of parameters is incorrect, or the type of parameters is incorrect. |
| [20000001](../errorcode-deviceAttest.md#20000001-system-service-abnormal) | System service exception, please try again or reboot your device. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    deviceAttest.getAttestStatus((error: BusinessError, value: deviceAttest.AttestResultInfo) => {
    if (typeof error != 'undefined') {
        console.error("error code:" + error.code + " message:" + error.message);
    } else {
        console.info("auth:" + value.authResult + " software:" + value.softwareResult + " ticket:" + value.ticket);
        console.info("versionIdResult:" + value.softwareResultDetail[0],
        " patchLevelResult:" + value.softwareResultDetail[1],
        " rootHashResult:" + value.softwareResultDetail[2],
        " PCIDResult:" + value.softwareResultDetail[3],
        " reserved:" + value.softwareResultDetail[4]);
    }
    })
} catch (error) {
    let code: number = (error as BusinessError).code;
    let message: string = (error as BusinessError).message;
    console.error("error code:" + code + " message:" + message);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    deviceAttest.getAttestStatus().then((value: deviceAttest.AttestResultInfo) => {
    console.info("auth:" + value.authResult + " software:" + value.softwareResult + " ticket:" + value.ticket);
    console.info("versionIdResult:" + value.softwareResultDetail[0],
        " patchLevelResult:" + value.softwareResultDetail[1],
        " rootHashResult:" + value.softwareResultDetail[2],
        " PCIDResult:" + value.softwareResultDetail[3],
        " reserved:" + value.softwareResultDetail[4]);
    }).catch((error: BusinessError) => {
        console.error("error code:" + error.code + " message:" + error.message);
    });
} catch (error) {
    let code: number = (error as BusinessError).code;
    let message: string = (error as BusinessError).message;
    console.error("error code:" + code + " message:" + message);
}
```


## getAttestStatus

```TypeScript
function getAttestStatus(): Promise<AttestResultInfo>
```

Obtains the AttestResultInfo object.

**Since:** 9

**System capability:** SystemCapability.XTS.DeviceAttest

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AttestResultInfo](arkts-basicservices-deviceattest-attestresultinfo-i-sys.md)&gt; | Returns that the AttestResultInfo object is returned in Promise mode. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | This api is system api, Please use the system application to call this api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Input parameters wrong, the number of parameters is incorrect, or the type of parameters is incorrect. |
| [20000001](../errorcode-deviceAttest.md#20000001-system-service-abnormal) | System service exception, please try again or reboot your device. |

**Examples**

See [getAttestStatus](#getatteststatus)
