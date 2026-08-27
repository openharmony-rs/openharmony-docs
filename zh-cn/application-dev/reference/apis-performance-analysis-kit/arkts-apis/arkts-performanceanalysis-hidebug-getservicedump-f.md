# getServiceDump

## 导入模块

```TypeScript
```

## getServiceDump

```TypeScript
function getServiceDump(serviceid : number, fd : number, args : Array<string>) : void
```

获取系统服务信息。

**起始版本：** 9

**需要权限：** ohos.permission.DUMP

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| serviceid | number | 是 | 系统服务ID，用于标识要获取信息的系统服务。取值由系统定义，取值范围[0, 255]。传入无效值时返回错误码401。 |
| fd | number | 是 | 文件描述符，接口会向该fd写入数据。传入无效文件描述符时返回错误码401。 |
| args | Array & lt;string & gt; | 是 | 系统服务的dump接口参数列表。string长度的最大值为254，超出部分将会被截断。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | the parameter check failed, Possible causes: 1.the parameter type error 2.the args parameter is not string array |
| [11400101](../errorcode-hiviewdfx-hidebug.md#11400101-系统服务获取失败) | ServiceId invalid. The system ability does not exist. |

**示例**

```TypeScript
import { fileIo } from '@kit.CoreFileKit';
import { hidebug } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

let fileFd = -1;
try {
  // 请在组件内获取context，确保this.getUiContext().getHostContext()返回结果为UIAbilityContext。
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
