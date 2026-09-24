# print

## Modules to Import

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## print

```TypeScript
function print(files: Array<string>, callback: AsyncCallback<PrintTask>): void
```

Prints files. This API uses an asynchronous callback to return the result. To start the system print preview page, call the [print](#print-3) API and pass in context.

**Since:** 10

**Deprecated since:** 26.0.0

**Substitutes:** [print](arkts-basicservices-print-f.md)

**Required permissions:** ohos.permission.PRINT

**System capability:** SystemCapability.Print.PrintFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| files | Array&lt;string&gt; | Yes | List of files to print. Images (in .jpg,png,gif,bmp, or .webp format) and PDF files are supported. You should save the files to the application sandbox, obtain the sandbox URI through **fileUri.getUriFromPath**, and then pass this URI as a parameter to this API. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;[PrintTask](arkts-basicservices-print-printtask-i.md)&gt; | Yes | Callback to be invoked when the print job is finished. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | the application does not have permission to call this function. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Examples**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { fileUri } from '@kit.CoreFileKit';

// Pass in the URIs of the files.
let filePath = '/data/storage/el2/base/haps/entry/files/test.pdf';
print.print([fileUri.getUriFromPath(filePath)], (error: BusinessError, printTask: print.PrintTask) => {
    if (error) {
        console.error(`Failed to print. Code: ${error.code}, message: ${error.message}`);
    } else {
        printTask.on('succeed', () => {
            console.info('print state is succeed');
        })
        // ...
    }
})
```


<a id="print-1"></a>

## print

```TypeScript
function print(files: Array<string>): Promise<PrintTask>
```

Prints files. This API uses a promise to return the result. To start the system print preview page, call the [print](#print-3) API and pass in context.

**Since:** 10

**Deprecated since:** 26.0.0

**Substitutes:** [print](arkts-basicservices-print-f.md)

**Required permissions:** ohos.permission.PRINT

**System capability:** SystemCapability.Print.PrintFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| files | Array&lt;string&gt; | Yes | List of files to print. Images (in .jpg,png,gif,bmp, or .webp format) and PDF files are supported. You should save the files to the application sandbox, obtain the sandbox URI through **fileUri.getUriFromPath**, and then pass this URI as a parameter to this API. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[PrintTask](arkts-basicservices-print-printtask-i.md)&gt; | Promise used to return a [PrintTask](arkts-basicservices-print-printtask-i.md) object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | the application does not have permission to call this function. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Examples**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { fileUri } from '@kit.CoreFileKit';

// Pass in the URIs of the files.
let filePath = '/data/storage/el2/base/haps/entry/files/test.pdf';
print.print([fileUri.getUriFromPath(filePath)]).then((printTask: print.PrintTask) => {
    printTask.on('succeed', () => {
        console.info('print state is succeed');
    })
    // ...
}).catch((error: BusinessError) => {
    console.error(`Failed to print. Code: ${error.code}, message: ${error.message}`);
})
```


<a id="print-2"></a>

## print

```TypeScript
function print(files: Array<string>, context: Context, callback: AsyncCallback<PrintTask>): void
```

Prints files. This API uses an asynchronous callback to return the result.

**Since:** 11

**Required permissions:** ohos.permission.PRINT

**System capability:** SystemCapability.Print.PrintFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| files | Array&lt;string&gt; | Yes | List of files to be printed. Currently, the following file types are supported: ".bm", ".bmp", ".doc", ".docm", ".docx", ".dot", ".dotm", ".dotx", ".gif", ".jfif", ".jpe", ".jpeg", ".jpg", "pdf", ".pot", ".potm", ".potx", ".pps", ".ppsm", ".ppsx", ".ppt", ".pptm", ".pptx", ".png", ".rtf", ".txt", ".webp", ".wps", ".xls", ".xlsb", ".xlsm", ".xlsx", ".xlt", ".xltx", and ".xml". You should save the files tothe application sandbox, obtain the sandbox URI through **fileUri.getUriFromPath**, and then pass this URI as a parameter to this API. |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | UIAbilityContext used to start the system print UI. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;[PrintTask](arkts-basicservices-print-printtask-i.md)&gt; | Yes | Callback to be invoked when the print job is finished. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | the application does not have permission to call this function. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Examples**

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
                Button("Print").width('90%').height(50).onClick(() => {
                    let filePath = '/data/storage/el2/base/haps/entry/files/test.pdf';
                    let context = this.getUIContext().getHostContext();
                    print.print([fileUri.getUriFromPath(filePath)], context, (error: BusinessError, printTask: print.PrintTask) => {
                        if (error) {
                            console.error(`Failed to print. Code: ${error.code}, message: ${error.message}`);
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


<a id="print-3"></a>

## print

```TypeScript
function print(files: Array<string>, context: Context): Promise<PrintTask>
```

Prints files. This API uses a promise to return the result.

**Since:** 11

**Required permissions:** ohos.permission.PRINT

**System capability:** SystemCapability.Print.PrintFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| files | Array&lt;string&gt; | Yes | List of files to be printed. Currently, the following file types are supported: ".bm", ".bmp", ".doc", ".docm", ".docx", ".dot", ".dotm", ".dotx", ".gif", ".jfif", ".jpe", ".jpeg", ".jpg", "pdf", ".pot", ".potm", ".potx", ".pps", ".ppsm", ".ppsx", ".ppt", ".pptm", ".pptx", ".png", ".rtf", ".txt", ".webp", ".wps", ".xls", ".xlsb", ".xlsm", ".xlsx", ".xlt", ".xltx", and ".xml". You should save the files tothe application sandbox, obtain the sandbox URI through **fileUri.getUriFromPath**, and then pass this URI as a parameter to this API. |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | UIAbilityContext used to start the system print UI. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[PrintTask](arkts-basicservices-print-printtask-i.md)&gt; | Promise used to return a [PrintTask](arkts-basicservices-print-printtask-i.md) object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | the application does not have permission to call this function. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Examples**

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
                Button("Print").width('90%').height(50).onClick(() => {
                    let filePath = '/data/storage/el2/base/haps/entry/files/test.pdf';
                    let context = this.getUIContext().getHostContext();
                    print.print([fileUri.getUriFromPath(filePath)], context).then((printTask: print.PrintTask) => {
                        printTask.on('succeed', () => {
                            console.info('print state is succeed');
                        })
                        // ...
                    }).catch((error: BusinessError) => {
                        console.error(`Failed to print. Code: ${error.code}, message: ${error.message}`);
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


<a id="print-4"></a>

## print

```TypeScript
function print(jobName: string, printAdapter: PrintDocumentAdapter, printAttributes: PrintAttributes,
    context: Context): Promise<PrintTask>
```

Prints a file. This API uses a promise to return the result.

**Since:** 11

**Required permissions:** ohos.permission.PRINT

**System capability:** SystemCapability.Print.PrintFramework

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| jobName | string | Yes | Name of the file to print, for example, **test.pdf**. The printer uses the [onStartLayoutWrite](arkts-basicservices-print-printdocumentadapter-i.md#onstartlayoutwrite) API to send the **fd** of the empty PDF file to the API caller. The API caller uses the new print attributes to update the file to print. |
| printAdapter | [PrintDocumentAdapter](arkts-basicservices-print-printdocumentadapter-i.md) | Yes | [PrintDocumentAdapter](arkts-basicservices-print-printdocumentadapter-i.md) API instance implemented by a third-party application. |
| printAttributes | [PrintAttributes](arkts-basicservices-print-printattributes-i.md) | Yes | Print attributes. |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | UIAbilityContext used to start the system print UI. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[PrintTask](arkts-basicservices-print-printtask-i.md)&gt; | Promise used to return a [PrintTask](arkts-basicservices-print-printtask-i.md) object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | the application does not have permission to call this function. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Examples**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
    build() {
        Scroll() {
            Column({ space: 10 }) {
                Button("Print").width('90%').height(50).onClick(() => {
                    let jobName : string = 'jobName';
                    // The PrintDocumentAdapter API needs to be implemented for printAdapter. The following is a simple example for reference.
                    let printAdapter : print.PrintDocumentAdapter = new MyPrintDocumentAdapter();
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
                    };
                    let context = this.getUIContext().getHostContext();

                    print.print(jobName, printAdapter, printAttributes, context).then((printTask: print.PrintTask) => {
                        printTask.on('succeed', () => {
                            console.info('print state is succeed');
                        })
                        // ...
                    }).catch((error: BusinessError) => {
                        console.error(`Failed to print. Code: ${error.code}, message: ${error.message}`);
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

class MyPrintDocumentAdapter implements print.PrintDocumentAdapter {
    onStartLayoutWrite(jobId: string, oldAttrs: print.PrintAttributes, newAttrs: print.PrintAttributes, fd: number,
        writeResultCallback: (jobId: string, writeResult: print.PrintFileCreationState) => void) {
        writeResultCallback(jobId, print.PrintFileCreationState.PRINT_FILE_CREATED);
    }
    onJobStateChanged(jobId: string, state: print.PrintDocumentAdapterState) {
        if (state === print.PrintDocumentAdapterState.PREVIEW_DESTROY) {
            console.info('PREVIEW_DESTROY');
        } else if (state === print.PrintDocumentAdapterState.PRINT_TASK_SUCCEED) {
            console.info('PRINT_TASK_SUCCEED');
        } else if (state === print.PrintDocumentAdapterState.PRINT_TASK_FAIL) {
            console.info('PRINT_TASK_FAIL');
        } else if (state === print.PrintDocumentAdapterState.PRINT_TASK_CANCEL) {
            console.info('PRINT_TASK_CANCEL');
        } else if (state === print.PrintDocumentAdapterState.PRINT_TASK_BLOCK) {
            console.info('PRINT_TASK_BLOCK');
        }
    }
}
```
