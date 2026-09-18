# getServiceDump

## Modules to Import

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## getServiceDump

```TypeScript
function getServiceDump(serviceid : number, fd : number, args : Array<string>) : void
```

Obtains system service information.

**Since:** 9

**Required permissions:** ohos.permission.DUMP

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| serviceid | number | Yes | Service ID used to obtain system service information. |
| fd | number | Yes | File descriptor to which data is written by the API. |
| args | Array&lt;string&gt; | Yes | Parameter list of the **Dump** API of the system service. The maximum length of a string is 254 characters. The excess part will be truncated. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | the parameter check failed, Possible causes: 1.the parameter type error 2.the args parameter is not string array |
| [11400101](../errorcode-hiviewdfx-hidebug.md#11400101-failed-to-obtain-the-system-service) | ServiceId invalid. The system ability does not exist. |

**Examples**

```TypeScript
import { fileIo } from '@kit.CoreFileKit';
import { hidebug } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

let fileFd = -1;
try {
  // Obtain the context from the component and ensure that the return value of this.getUiContext().getHostContext() is UIAbilityContext.
  let path: string = this.getUIContext().getHostContext()!.filesDir + "/serviceInfo.txt";
  console.info("output path: " + path);
  fileFd = fileIo.openSync(path, fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE).fd;
  let serviceId: number = 10;
  let args: Array<string> = new Array("allInfo");
  hidebug.getServiceDump(serviceId, fileFd, args);
} catch (error) {
  console.error(`error code: ${(error as BusinessError).code}, error msg: ${(error as BusinessError).message}`);
}

if (fileFd >= 0) {
  fileIo.closeSync(fileFd);
}
```
