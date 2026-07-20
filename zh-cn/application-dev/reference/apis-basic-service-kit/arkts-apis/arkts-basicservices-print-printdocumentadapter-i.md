# PrintDocumentAdapter

第三方应用程序实现此接口来渲染要打印的文件。

**起始版本：** 11

<!--Device-print-interface PrintDocumentAdapter--><!--Device-print-interface PrintDocumentAdapter-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## 导入模块

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

<a id="onjobstatechanged"></a>
## onJobStateChanged

```TypeScript
onJobStateChanged(jobId: string, state: PrintDocumentAdapterState): void
```

实现这个接口来监听打印任务状态的改变。

**起始版本：** 11

**需要权限：** ohos.permission.PRINT

<!--Device-PrintDocumentAdapter-onJobStateChanged(jobId: string, state: PrintDocumentAdapterState): void--><!--Device-PrintDocumentAdapter-onJobStateChanged(jobId: string, state: PrintDocumentAdapterState): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| jobId | string | 是 | 表示打印任务ID。 |
| state | [PrintDocumentAdapterState](arkts-basicservices-print-printdocumentadapterstate-e.md) | 是 | 表示打印任务更改为该状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

class MyPrintDocumentAdapter implements print.PrintDocumentAdapter {
    onStartLayoutWrite(jobId: string, oldAttrs: print.PrintAttributes, newAttrs: print.PrintAttributes, fd: number,
        writeResultCallback: (jobId: string, writeResult: print.PrintFileCreationState) => void) {
        writeResultCallback(jobId, print.PrintFileCreationState.PRINT_FILE_CREATED);
    };
    onJobStateChanged(jobId: string, state: print.PrintDocumentAdapterState) {
        if (state == print.PrintDocumentAdapterState.PREVIEW_DESTROY) {
            console.info('PREVIEW_DESTROY');
        } else if (state == print.PrintDocumentAdapterState.PRINT_TASK_SUCCEED) {
            console.info('PRINT_TASK_SUCCEED');
        } else if (state == print.PrintDocumentAdapterState.PRINT_TASK_FAIL) {
            console.info('PRINT_TASK_FAIL');
        } else if (state == print.PrintDocumentAdapterState.PRINT_TASK_CANCEL) {
            console.info('PRINT_TASK_CANCEL');
        } else if (state == print.PrintDocumentAdapterState.PRINT_TASK_BLOCK) {
            console.info('PRINT_TASK_BLOCK');
        }
    }
}

```

<a id="onstartlayoutwrite"></a>
## onStartLayoutWrite

```TypeScript
onStartLayoutWrite(jobId: string, oldAttrs: PrintAttributes, newAttrs: PrintAttributes, fd: number,
      writeResultCallback: (jobId: string, writeResult: PrintFileCreationState) => void): void
```

打印服务会通过本接口将一个空的pdf文件的文件描述符传给三方应用，由三方应用使用新的打印参数更新待打印文件，更新文件完成后通过本接口的回调方法writeResultCallback通知打印服务。

**起始版本：** 11

**需要权限：** ohos.permission.PRINT

<!--Device-PrintDocumentAdapter-onStartLayoutWrite(jobId: string, oldAttrs: PrintAttributes, newAttrs: PrintAttributes, fd: int,
      writeResultCallback: (jobId: string, writeResult: PrintFileCreationState) => void): void--><!--Device-PrintDocumentAdapter-onStartLayoutWrite(jobId: string, oldAttrs: PrintAttributes, newAttrs: PrintAttributes, fd: int,
      writeResultCallback: (jobId: string, writeResult: PrintFileCreationState) => void): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| jobId | string | 是 | 表示打印任务ID。 |
| oldAttrs | [PrintAttributes](arkts-basicservices-print-printattributes-i.md) | 是 | 表示旧打印参数。 |
| newAttrs | [PrintAttributes](arkts-basicservices-print-printattributes-i.md) | 是 | 表示新打印参数。 |
| fd | number | 是 | 表示打印文件传给接口调用方的pdf文件的文件描述符。 |
| writeResultCallback | (jobId: string, writeResult: PrintFileCreationState) =&gt; void | 是 | 表示三方应用使用新的打印参数更新待打印文件完成后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```TypeScript
import { print } from '@kit.BasicServicesKit';

class MyPrintDocumentAdapter implements print.PrintDocumentAdapter {
    onStartLayoutWrite(jobId: string, oldAttrs: print.PrintAttributes, newAttrs: print.PrintAttributes, fd: number,
        writeResultCallback: (jobId: string, writeResult: print.PrintFileCreationState) => void) {
        writeResultCallback(jobId, print.PrintFileCreationState.PRINT_FILE_CREATED);
    };
    onJobStateChanged(jobId: string, state: print.PrintDocumentAdapterState) {
        if (state == print.PrintDocumentAdapterState.PREVIEW_DESTROY) {
            console.info('PREVIEW_DESTROY');
        } else if (state == print.PrintDocumentAdapterState.PRINT_TASK_SUCCEED) {
            console.info('PRINT_TASK_SUCCEED');
        } else if (state == print.PrintDocumentAdapterState.PRINT_TASK_FAIL) {
            console.info('PRINT_TASK_FAIL');
        } else if (state == print.PrintDocumentAdapterState.PRINT_TASK_CANCEL) {
            console.info('PRINT_TASK_CANCEL');
        } else if (state == print.PrintDocumentAdapterState.PRINT_TASK_BLOCK) {
            console.info('PRINT_TASK_BLOCK');
        }
    }
}

```

