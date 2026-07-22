# print

## 导入模块

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## print

```TypeScript
function print(files: Array<string>, callback: AsyncCallback<PrintTask>): void
```

打印接口，传入文件进行打印，使用callback异步回调。拉起系统打印预览界面，需要使用[print](arkts-basicservices-print-f.md#print)接口，传入context。

**起始版本：** 10

**需要权限：** ohos.permission.PRINT

<!--Device-print-function print(files: Array<string>, callback: AsyncCallback<PrintTask>): void--><!--Device-print-function print(files: Array<string>, callback: AsyncCallback<PrintTask>): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| files | Array&lt;string&gt; | 是 | 待打印文件列表，支持图片（.jpg .png .gif .bmp .webp）和pdf。文件需先保存到应用沙箱，通过fileUri.getUriFromPath获取到沙箱uri，再作为参数传入到本接口。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;PrintTask&gt; | 是 | 异步获取打印完成之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { fileUri } from '@kit.CoreFileKit';

// 传入文件的uri
let filePath = '/data/storage/el2/base/haps/entry/files/test.pdf';
print.print([fileUri.getUriFromPath(filePath)], (err: BusinessError, printTask: print.PrintTask) => {
    if (err) {
        console.error('print err ' + JSON.stringify(err));
    } else {
        printTask.on('succeed', () => {
            console.info('print state is succeed');
        })
        // ...
    }
})

```


## print

```TypeScript
function print(files: Array<string>): Promise<PrintTask>
```

打印接口，传入文件进行打印，使用Promise异步回调。拉起系统打印预览界面，需要使用[print](arkts-basicservices-print-f.md#print)接口，传入context。

**起始版本：** 10

**需要权限：** ohos.permission.PRINT

<!--Device-print-function print(files: Array<string>): Promise<PrintTask>--><!--Device-print-function print(files: Array<string>): Promise<PrintTask>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| files | Array&lt;string&gt; | 是 | 待打印文件列表，支持图片（.jpg .png .gif .bmp .webp）和pdf。文件需先保存到应用沙箱，通过fileUri.getUriFromPath获取到沙箱uri，再作为参数传入到本接口。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;PrintTask&gt; | Promise对象，返回[PrintTask](arkts-basicservices-print-printtask-i.md)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { fileUri } from '@kit.CoreFileKit';

// 传入文件的uri
let filePath = '/data/storage/el2/base/haps/entry/files/test.pdf';
print.print([fileUri.getUriFromPath(filePath)]).then((printTask: print.PrintTask) => {
    printTask.on('succeed', () => {
        console.info('print state is succeed');
    })
    // ...
}).catch((error: BusinessError) => {
    console.error('print err ' + JSON.stringify(error));
})

```


## print

```TypeScript
function print(files: Array<string>, context: Context, callback: AsyncCallback<PrintTask>): void
```

打印接口，传入文件进行打印，使用callback异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.PRINT

<!--Device-print-function print(files: Array<string>, context: Context, callback: AsyncCallback<PrintTask>): void--><!--Device-print-function print(files: Array<string>, context: Context, callback: AsyncCallback<PrintTask>): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| files | Array&lt;string&gt; | 是 | 待打印文件列表，当前支持的文件类型：".bm", ".bmp", ".doc", ".docm", ".docx", ".dot", ".dotm", ".dotx", ".gif", ".jfif", ".jpe", ".jpeg", ".jpg", "pdf", ".pot", ".potm", ".potx", ".pps", ".ppsm", ".ppsx", ".ppt",".pptm", ".pptx", ".png", ".rtf", ".txt", ".webp", ".wps", ".xls", ".xlsb", ".xlsm", ".xlsx", ".xlt", ".xltx",".xml"。文件需先保存到应用沙箱，通过fileUri.getUriFromPath获取到沙箱uri，再作为参数传入到本接口。 |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 用于拉起系统打印界面的UIAbilityContext。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;PrintTask&gt; | 是 | 异步获取打印完成之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { fileUri } from '@kit.CoreFileKit';

@Entry
@Component
struct Index {
    build() {
        Scroll() {
            Column({ space: 10 }) {
                Button("打印").width('90%').height(50).onClick(() => {
                    let filePath = '/data/storage/el2/base/haps/entry/files/test.pdf';
                    let context = this.getUIContext().getHostContext();
                    print.print([fileUri.getUriFromPath(filePath)], context, (err: BusinessError, printTask: print.PrintTask) => {
                        if (err) {
                            console.error('print err ' + JSON.stringify(err));
                        } else {
                            printTask.on('succeed', () => {
                                console.info('print state is succeed');
                            })
                            // ...
                        }
                    })
                })
            }
            .justifyContent(FlexAlign.Center)
            .constraintSize({ minHeight: '100%' })
            .width('100%')
        }
        .height('100%')
    }
}

```


## print

```TypeScript
function print(files: Array<string>, context: Context): Promise<PrintTask>
```

打印接口，传入文件进行打印，使用Promise异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.PRINT

<!--Device-print-function print(files: Array<string>, context: Context): Promise<PrintTask>--><!--Device-print-function print(files: Array<string>, context: Context): Promise<PrintTask>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| files | Array&lt;string&gt; | 是 | 待打印文件列表，当前支持的文件类型：".bm", ".bmp", ".doc", ".docm", ".docx", ".dot", ".dotm", ".dotx", ".gif", ".jfif", ".jpe", ".jpeg", ".jpg", "pdf", ".pot", ".potm", ".potx", ".pps", ".ppsm", ".ppsx", ".ppt",".pptm", ".pptx", ".png", ".rtf", ".txt", ".webp", ".wps", ".xls", ".xlsb", ".xlsm", ".xlsx", ".xlt", ".xltx",".xml"。文件需先保存到应用沙箱，通过fileUri.getUriFromPath获取到沙箱uri，再作为参数传入到本接口。 |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 用于拉起系统打印界面的UIAbilityContext。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;PrintTask&gt; | Promise对象，返回[PrintTask](arkts-basicservices-print-printtask-i.md)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { fileUri } from '@kit.CoreFileKit';

@Entry
@Component
struct Index {
    build() {
        Scroll() {
            Column({ space: 10 }) {
                Button("打印").width('90%').height(50).onClick(() => {
                    let filePath = '/data/storage/el2/base/haps/entry/files/test.pdf';
                    let context = this.getUIContext().getHostContext();
                    print.print([fileUri.getUriFromPath(filePath)], context).then((printTask: print.PrintTask) => {
                        printTask.on('succeed', () => {
                            console.info('print state is succeed');
                        })
                        // ...
                    }).catch((error: BusinessError) => {
                        console.error('print err ' + JSON.stringify(error));
                    })
                })
            }
            .justifyContent(FlexAlign.Center)
            .constraintSize({ minHeight: '100%' })
            .width('100%')
        }
        .height('100%')
    }
}

```


## print

```TypeScript
function print(jobName: string, printAdapter: PrintDocumentAdapter, printAttributes: PrintAttributes,
    context: Context): Promise<PrintTask>
```

打印接口，传入文件进行打印，三方应用需要更新打印文件，使用Promise异步回调。当前支持的文件类型：".pdf"。

**起始版本：** 11

**需要权限：** ohos.permission.PRINT

<!--Device-print-function print(jobName: string, printAdapter: PrintDocumentAdapter, printAttributes: PrintAttributes,    context: Context): Promise<PrintTask>--><!--Device-print-function print(jobName: string, printAdapter: PrintDocumentAdapter, printAttributes: PrintAttributes,    context: Context): Promise<PrintTask>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| jobName | string | 是 | 表示待打印文件名称，例如：test.pdf。当前仅支持".pdf"文件类型。打印侧会通过[onStartLayoutWrite](arkts-basicservices-print-printdocumentadapter-i.md#onstartlayoutwrite)接口将空的pdf文件的fd传给接口调用方，由调用方使用新的打印参数更新待打印文件。 |
| printAdapter | [PrintDocumentAdapter](arkts-basicservices-print-printdocumentadapter-i.md) | 是 | 表示三方应用实现的[PrintDocumentAdapter](arkts-basicservices-print-printdocumentadapter-i.md)接口实例。 |
| printAttributes | [PrintAttributes](arkts-basicservices-print-printattributes-i.md) | 是 | 表示打印参数。 |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 用于拉起系统打印界面的UIAbilityContext。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;PrintTask&gt; | Promise对象，返回[PrintTask](arkts-basicservices-print-printtask-i.md)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
    build() {
        Scroll() {
            Column({ space: 10 }) {
                Button("打印").width('90%').height(50).onClick(() => {
                    let jobName : string = "jobName";
                    let printAdapter : print.PrintDocumentAdapter | null = null;
                    let printAttributes : print.PrintAttributes = {
                        copyNumber: 1,
                        pageRange: {
                            startPage: 0,
                            endPage: 5,
                            pages: []
                        },
                        pageSize: print.PrintPageType.PAGE_ISO_A3,
                        directionMode: print.PrintDirectionMode.DIRECTION_MODE_AUTO,
                        colorMode: print.PrintColorMode.COLOR_MODE_MONOCHROME,
                        duplexMode: print.PrintDuplexMode.DUPLEX_MODE_NONE
                    }
                    let context = this.getUIContext().getHostContext();

                    print.print(jobName, printAdapter, printAttributes, context).then((printTask: print.PrintTask) => {
                        printTask.on('succeed', () => {
                            console.info('print state is succeed');
                        })
                        // ...
                    }).catch((error: BusinessError) => {
                        console.error('print err ' + JSON.stringify(error));
                    })
                })
            }
            .justifyContent(FlexAlign.Center)
            .constraintSize({ minHeight: '100%' })
            .width('100%')
        }
        .height('100%')
    }
}

```

