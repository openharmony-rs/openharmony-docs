# startPrint

## startPrint

```TypeScript
function startPrint(job: PrintJobData): Promise<void>
```

打印接口，传入文件或者二进制数据进行打印，使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**需要权限：** ohos.permission.PRINT

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-print-function startPrint(job: PrintJobData): Promise<void>--><!--Device-print-function startPrint(job: PrintJobData): Promise<void>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| job | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 打印任务数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |

**示例：**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@ohos.base';
import fs from "@ohos.file.fs";

let tempPath = '/data/stroage/el2/base/haps/entry/files/note.jpg';
let file: fs.File;
file = fs.openSync(tempPath, 4);

let printJobData: print.PrintJobData = {
    printerId: "printerId",
    jobName: "jobName",
    documentFormat: print.PrintDocumentFormat.DOCUMENT_FORMAT_AUTO,
    docFlavor: print.DocFlavor.FILE_DESCRIPTOR,
    copyNumber: 1,
    isLandscape: false,
    colorMode: print.PrintColorMode.COLOR_MODE_MONOCHROME,
    duplexMode: print.PrintDuplexMode.DUPLEX_MODE_NONE,
    pageSize: {id: "ISO_A4", name: "ISO_A4", width:8268, height: 11692},
    fdList: [file.fd],
}
print.startPrint(printJobData).then(() => {
    console.info('start print success');
}).catch((error: BusinessError) => {
    console.error('failed to print because : ' + JSON.stringify(error));
})
```

