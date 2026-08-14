# startGettingPrintFile（系统接口）

## startGettingPrintFile

```TypeScript
function startGettingPrintFile(jobId: string, printAttributes: PrintAttributes, fd: int,
    onFileStateChanged: Callback<PrintFileCreationState>): void
```

开始获取打印文件，使用Callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

<!--Device-print-function startGettingPrintFile(jobId: string, printAttributes: PrintAttributes, fd: int,    onFileStateChanged: Callback<PrintFileCreationState>): void--><!--Device-print-function startGettingPrintFile(jobId: string, printAttributes: PrintAttributes, fd: int,    onFileStateChanged: Callback<PrintFileCreationState>): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| jobId | string | 是 | 表示打印任务ID。 |
| printAttributes | [PrintAttributes](arkts-basicservices-print-printattributes-i.md) | 是 | 表示打印参数。 |
| fd | int | 是 | 表示打印文件描述符。 |
| onFileStateChanged | [Callback](arkts-basicservices-callback-t.md)&lt;[PrintFileCreationState](arkts-basicservices-print-printfilecreationstate-e.md)&gt; | 是 | 表示更新文件状态的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application |

## 示例

```TypeScript
import { print } from '@kit.BasicServicesKit';

let jobId : string= '1';
class MyPrintAttributes implements print.PrintAttributes {
    copyNumber?: number;
    pageRange?: print.PrintPageRange;
    pageSize?: print.PrintPageSize | print.PrintPageType;
    directionMode?: print.PrintDirectionMode;
    colorMode?: print.PrintColorMode;
    duplexMode?: print.PrintDuplexMode;
}

class MyPrintPageRange implements print.PrintPageRange {
    startPage?: number;
    endPage?: number;
    pages?: Array<number>;
}

class MyPrintPageSize implements print.PrintPageSize {
    id: string = '0';
    name: string = '0';
    width: number = 210;
    height: number = 297;
}

let printAttributes = new MyPrintAttributes();
printAttributes.copyNumber = 2;
printAttributes.pageRange = new MyPrintPageRange();
printAttributes.pageRange.pages = [1, 3];
printAttributes.pageSize = print.PrintPageType.PAGE_ISO_A3;
printAttributes.directionMode = print.PrintDirectionMode.DIRECTION_MODE_AUTO;
printAttributes.colorMode = print.PrintColorMode.COLOR_MODE_MONOCHROME;
printAttributes.duplexMode = print.PrintDuplexMode.DUPLEX_MODE_NONE;

let fd : number = 1;
print.startGettingPrintFile(jobId, printAttributes, fd, (state: print.PrintFileCreationState) => {
    console.info('onFileStateChanged success, data : ' + JSON.stringify(state));
})
```

