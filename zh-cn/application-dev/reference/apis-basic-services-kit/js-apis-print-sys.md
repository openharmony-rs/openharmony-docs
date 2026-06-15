# @ohos.print (打印)(系统接口)

<!--Kit: Basic Services Kit-->
<!--Subsystem: Print-->
<!--Owner: @guoshengbang-->
<!--Designer: @gcw_4D6e0BBd-->
<!--Tester: @guoshengbang-->
<!--Adviser: @RayShih-->

该模块为基本打印的操作API，提供调用基础打印功能的接口。

> **说明：**
> 本模块首批接口从API version 10开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> 当前界面仅包含本模块的系统接口，其他公开接口参见[@ohos.print (打印)](js-apis-print.md)。

## 导入模块

```ts
import { print } from '@kit.BasicServicesKit';
```

## PrinterExtensionInfo

定义打印扩展信息的接口。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**属性：**

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| extensionId | string | 否 | 否 | 表示打印机扩展的扩展ID。 |
| vendorId | string | 否 | 否 | 表示扩展的供应商ID。 |
| vendorName | string | 否 | 否 | 表示供应商名称。 |
| vendorIcon | number | 否 | 否 | 表示供应商图标。 |
| version | string | 否 | 否 | 表示当前打印机扩展的版本。 |

## print.queryAllPrinterExtensionInfos

queryAllPrinterExtensionInfos(callback: AsyncCallback&lt;Array&lt;PrinterExtensionInfo&gt;&gt;): void

查询所有已安装的打印机扩展服务，使用callback异步回调。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;Array&lt;[PrinterExtensionInfo](#printerextensioninfo)&gt;&gt; | 是 | 异步查询所有已安装的打印机扩展服务之后的回调。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |

**示例：**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

print.queryAllPrinterExtensionInfos((err: BusinessError, extensionInfos: print.PrinterExtensionInfo[]) => {
    if (err) {
        console.error('queryAllPrinterExtensionInfos err ' + JSON.stringify(err));
    } else {
        console.info('queryAllPrinterExtensionInfos success ' + JSON.stringify(extensionInfos));
    }
})
```

## print.queryAllPrinterExtensionInfos

queryAllPrinterExtensionInfos(): Promise&lt;Array&lt;PrinterExtensionInfo&gt;&gt;

查询所有已安装的打印机扩展服务，使用Promise异步回调。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;Array&lt;[PrinterExtensionInfo](#printerextensioninfo)&gt;&gt; | Promise对象，返回包含所有已安装的打印机扩展服务信息的列表。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |

**示例：**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

print.queryAllPrinterExtensionInfos().then((extensionInfos: print.PrinterExtensionInfo[]) => {
    console.info('queryAllPrinterExtensionInfos success ' + JSON.stringify(extensionInfos));
    // ...
}).catch((error: BusinessError) => {
    console.error('failed to get AllPrinterExtension because ' + JSON.stringify(error));
})
```

## print.disconnectPrinter

disconnectPrinter(printerId: string, callback: AsyncCallback&lt;void&gt;): void

断开特定打印机的连接，使用callback异步回调。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| printerId | string | 是 | 打印机ID。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 异步断开特定打印机的连接之后的回调。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let printerId: string = 'printerId_32';
print.disconnectPrinter(printerId, (err: BusinessError) => {
    if (err) {
        console.error('failed to disconnect Printer because : ' + JSON.stringify(err));
    } else {
        console.info('start disconnect Printer success');
    }
})
```

## print.disconnectPrinter

disconnectPrinter(printerId: string): Promise&lt;void&gt;

断开特定打印机的连接，使用Promise异步回调。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| printerId | string | 是 | 打印机ID。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let printerId: string = 'printerId_32';
print.disconnectPrinter(printerId).then(() => {
    console.info('start disconnect Printer success');
}).catch((error: BusinessError) => {
    console.error('failed to disconnect Printer because : ' + JSON.stringify(error));
})
```

## print.queryPrinterCapability

queryPrinterCapability(printerId: string, callback: AsyncCallback&lt;void&gt;): void

查询打印机能力，使用callback异步回调。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| printerId | string | 是 | 打印机ID。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 异步查询打印机能力之后的回调。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let printerId: string = 'printerId_32';
print.queryPrinterCapability(printerId, (err: BusinessError) => {
    if (err) {
        console.error('failed to query Printer Capability because : ' + JSON.stringify(err));
    } else {
        console.info('start query Printer Capability success');
    }
})
```

## print.queryPrinterCapability

queryPrinterCapability(printerId: string): Promise&lt;void&gt;

查询打印机能力，使用Promise异步回调。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| printerId | string | 是 | 打印机ID。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let printerId: string = 'printerId_32';
print.queryPrinterCapability(printerId).then(() => {
    console.info('start query Printer success');
}).catch((error: BusinessError) => {
    console.error('failed to query Printer Capability because : ' + JSON.stringify(error));
})
```

## print.startPrintJob

startPrintJob(jobInfo: PrintJob, callback: AsyncCallback&lt;void&gt;): void

开始打印任务，使用callback异步回调。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| jobInfo | [PrintJob](js-apis-print.md#printjob24) | 是 | 打印任务信息。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 异步开始打印任务之后的回调。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let jobInfo : print.PrintJob = {
    fdList : [44,45],
    jobId : 'jobId_12',
    printerId : 'printerId_32',
    jobState : print.PrintJobState.PRINT_JOB_COMPLETED,
    jobSubstate : print.PrintJobSubState.PRINT_JOB_COMPLETED_SUCCESS,
    copyNumber : 1,
    pageRange : {},
    isSequential : false,
    pageSize : {id : '', name : '', width : 10, height : 20},
    isLandscape : false,
    colorMode : print.PrintColorMode.COLOR_MODE_COLOR,
    duplexMode : print.PrintDuplexMode.DUPLEX_MODE_NONE,
    margin : undefined,
    preview : undefined,
    options : undefined
};
print.startPrintJob(jobInfo, (err: BusinessError) => {
    if (err) {
        console.error('failed to start Print Job because : ' + JSON.stringify(err));
    } else {
        console.info('start Print Job success');
    }
})
```

## print.startPrintJob

startPrintJob(jobInfo: PrintJob): Promise&lt;void&gt;

开始打印任务，使用Promise异步回调。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| jobInfo | [PrintJob](js-apis-print.md#printjob24) | 是 | 打印任务信息。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let jobInfo : print.PrintJob = {
    fdList : [44,45],
    jobId : 'jobId_12',
    printerId : 'printerId_32',
    jobState : print.PrintJobState.PRINT_JOB_COMPLETED,
    jobSubstate : print.PrintJobSubState.PRINT_JOB_COMPLETED_SUCCESS,
    copyNumber : 1,
    pageRange : {},
    isSequential : false,
    pageSize : {id : '', name : '', width : 10, height : 20},
    isLandscape : false,
    colorMode : print.PrintColorMode.COLOR_MODE_COLOR,
    duplexMode : print.PrintDuplexMode.DUPLEX_MODE_NONE,
    margin : undefined,
    preview : undefined,
    options : undefined
};
print.startPrintJob(jobInfo).then(() => {
    console.info('start Print success');
}).catch((error: BusinessError) => {
    console.error('failed to start Print because : ' + JSON.stringify(error));
})
```

## print.cancelPrintJob

cancelPrintJob(jobId: string, callback: AsyncCallback&lt;void&gt;): void

取消已发送到打印机的打印任务，使用callback异步回调。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| jobId | string | 是 | 打印任务ID。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 异步取消已发送到打印机的打印任务之后的回调。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let jobId : string = '121212';
print.cancelPrintJob(jobId, (err: BusinessError) => {
    if (err) {
        console.error('cancelPrintJob failed, because : ' + JSON.stringify(err));
    } else {
        console.info('cancelPrintJob success');
    }
})
```

## print.cancelPrintJob

cancelPrintJob(jobId: string): Promise&lt;void&gt;

取消已发送到打印机的打印任务，使用Promise异步回调。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| jobId | string | 是 | 打印任务ID。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let jobId : string = '121212';
print.cancelPrintJob(jobId).then(() => {
    console.info('cancelPrintJob success');
}).catch((error: BusinessError) => {
    console.error('cancelPrintJob failed, because : ' + JSON.stringify(error));
})
```

## print.restartPrintJob<sup>20+</sup>

restartPrintJob(jobId: string): Promise&lt;void&gt;

重新打印之前打印过的打印任务，使用Promise异步回调。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| jobId | string | 是 | 之前打印过的打印任务ID。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |

**示例：**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let jobId : string = '121212';
print.restartPrintJob(jobId).then(() => {
    console.info('restartPrintJob success');
}).catch((error: BusinessError) => {
    console.error('restartPrintJob failed, because : ' + JSON.stringify(error));
})
```

## print.requestPrintPreview

requestPrintPreview(jobInfo: PrintJob, callback: Callback&lt;number&gt;): void

请求预览打印数据，使用callback回调。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| jobInfo | [PrintJob](js-apis-print.md#printjob24) | 是 | 打印任务信息。 |
| callback | Callback&lt;number&gt; | 是 | 请求预览打印数据之后的回调。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```ts
import { print } from '@kit.BasicServicesKit';

let jobInfo : print.PrintJob = {
    fdList : [44,45],
    jobId : 'jobId_12',
    printerId : 'printerId_32',
    jobState : PRINT_JOB_COMPLETED,
    jobSubstate : print.PrintJobSubState.PRINT_JOB_COMPLETED_SUCCESS,
    copyNumber : 1,
    pageRange : {},
    isSequential : false,
    pageSize : {id : '', name : '', width : 10, height : 20},
    isLandscape : false,
    colorMode : COLOR_MODE_COLOR,
    duplexMode : DUPLEX_MODE_NONE,
    margin : undefined,
    preview : undefined,
    options : undefined
};
print.requestPrintPreview(jobInfo, (num : number) => {
    console.info('requestPrintPreview success, num : ' + JSON.stringify(num));

})
```

## print.requestPrintPreview

requestPrintPreview(jobInfo: PrintJob): Promise&lt;number&gt;

请求预览打印数据，使用Promise异步回调。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| jobInfo | [PrintJob](js-apis-print.md#printjob24) | 是 | 打印任务信息。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;number&gt; | Promise对象，返回预览结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let jobInfo : print.PrintJob = {
    fdList : [44,45],
    jobId : 'jobId_12',
    printerId : 'printerId_32',
    jobState : PRINT_JOB_COMPLETED,
    jobSubstate : print.PrintJobSubState.PRINT_JOB_COMPLETED_SUCCESS,
    copyNumber : 1,
    pageRange : {},
    isSequential : false,
    pageSize : {id : '', name : '', width : 10, height : 20},
    isLandscape : false,
    colorMode : COLOR_MODE_COLOR,
    duplexMode : DUPLEX_MODE_NONE,
    margin : undefined,
    preview : undefined,
    options : undefined
};
print.requestPrintPreview(jobInfo).then((num: number) => {
    console.info('requestPrintPreview success, num : ' + JSON.stringify(num));
}).catch((error: BusinessError) => {
    console.error('requestPrintPreview failed, because : ' + JSON.stringify(error));
})
```

## print.on

on(type: 'printerStateChange', callback: (state: PrinterState, info: PrinterInfo) => void): void

注册打印机状态变化事件回调，使用callback回调。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| type | 'printerStateChange' | 是 | 表示打印机状态改变。 |
| callback | (state: [PrinterState](js-apis-print.md#printerstate14), info: [PrinterInfo](js-apis-print.md#printerinfo24)) => void | 是 | 打印机状态改变之后的回调。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```ts
import { print } from '@kit.BasicServicesKit';

print.on('printerStateChange', (state: print.PrinterState, info: print.PrinterInfo) => {
    if (state === null || info === null) {
        console.error('printer state changed state is null or info is null');
        return;
    } else {
        console.info('on printer state changed, state : ' + JSON.stringify(state));
        console.info('on printer state changed, info : ' + JSON.stringify(info));
    }
})
```

## print.off

off(type: 'printerStateChange', callback?: Callback&lt;boolean&gt;): void

取消注册打印机状态变化事件回调，使用callback回调。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| type | 'printerStateChange' | 是 | 表示打印机状态改变。 |
| callback | Callback&lt;boolean&gt; | 否 | 表示取消注册打印机状态变化事件是否成功。true表示成功，false表示失败。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```ts
import { print } from '@kit.BasicServicesKit';

print.off('printerStateChange', (data: boolean) => {
    console.info('off printerStateChange data : ' + JSON.stringify(data));
})
```

## print.on

on(type: 'jobStateChange', callback: (state: PrintJobState, job: PrintJob) => void): void

注册打印任务状态变化事件回调，使用callback回调。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| type | 'jobStateChange' | 是 | 表示打印任务状态改变。 |
| callback | (state: [PrintJobState](js-apis-print.md#printjobstate14), job: [PrintJob](js-apis-print.md#printjob24)) => void | 是 | 打印任务状态改变之后的回调。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```ts
import { print } from '@kit.BasicServicesKit';

print.on('jobStateChange', (state: print.PrintJobState, job: print.PrintJob) => {
    console.info('onJobStateChange, state : ' + JSON.stringify(state) + ', job : ' + JSON.stringify(job));
})
```

## print.off

off(type: 'jobStateChange', callback?: Callback&lt;boolean&gt;): void

取消注册打印任务状态变化事件回调，使用callback回调。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| type | 'jobStateChange' | 是 | 表示打印任务状态改变。 |
| callback | Callback&lt;boolean&gt; | 否 | 表示取消注册打印任务状态变化事件是否成功。true表示成功，false表示失败。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```ts
import { print } from '@kit.BasicServicesKit';

print.off('jobStateChange', (data: boolean) => {
    console.info('offJobStateChanged data : ' + JSON.stringify(data));
})
```

## print.on

on(type: 'extInfoChange', callback: (extensionId: string, info: string) => void): void

注册打印扩展信息变化事件回调，使用callback回调。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| type | 'extInfoChange' | 是 | 表示打印扩展信息改变。 |
| callback | (extensionId: string, info: string) => void | 是 | 打印扩展信息改变之后的回调。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```ts
import { print } from '@kit.BasicServicesKit';

print.on('extInfoChange', (extensionId: string, info: string) => {
    console.info('onExtInfoChange, extensionId : ' + JSON.stringify(extensionId) + ', info : ' + JSON.stringify(info));
})
```

## print.off

off(type: 'extInfoChange', callback?: Callback&lt;boolean&gt;): void

取消注册打印扩展信息变化事件回调，使用callback回调。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| type | 'extInfoChange' | 是 | 表示打印扩展信息改变。 |
| callback | Callback&lt;boolean&gt; | 否 | 表示取消注册打印扩展信息变化事件是否成功。true表示成功，false表示失败。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```ts
import { print } from '@kit.BasicServicesKit';

print.off('extInfoChange', (data: boolean) => {
    console.info('offExtInfoChange data : ' + JSON.stringify(data));
})
```

## print.addPrinters

addPrinters(printers: Array&lt;PrinterInfo&gt;, callback: AsyncCallback&lt;void&gt;): void

添加打印机，使用callback异步回调。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| printers | Array&lt;[PrinterInfo](js-apis-print.md#printerinfo24)&gt; | 是 | 表示新到达的打印机列表。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 异步添加打印机之后的回调。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let printerInfo : print.PrinterInfo = {
    printerId : '3232',
    printerName : 'hhhhh',
    printerState : 0,
    printerIcon : 12,
    description : 'str',
    capability : undefined,
    options : 'opt'
};
print.addPrinters([printerInfo], (err: BusinessError) => {
    if (err) {
        console.error('addPrinters failed, because : ' + JSON.stringify(err));
    } else {
        console.info('addPrinters success');
    }
})
```

## print.addPrinters

addPrinters(printers: Array&lt;PrinterInfo&gt;): Promise&lt;void&gt;

添加打印机，使用Promise异步回调。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| printers | Array&lt;[PrinterInfo](js-apis-print.md#printerinfo24)&gt; | 是 | 表示新到达的打印机列表。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let printerInfo : print.PrinterInfo = {
    printerId : '3232',
    printerName : 'hhhhh',
    printerState : 0,
    printerIcon : 12,
    description : 'str',
    capability : undefined,
    options : 'opt'
};
print.addPrinters([printerInfo]).then(() => {
    console.info('add printers success.');
}).catch((error: BusinessError) => {
    console.error('add printers error : ' + JSON.stringify(error));
})
```

## print.removePrinters

removePrinters(printerIds: Array&lt;string&gt;, callback: AsyncCallback&lt;void&gt;): void

移除打印机，使用callback异步回调。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| printerIds | Array&lt;string&gt; | 是 | 表示需移除的打印机列表。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 异步移除打印机之后的回调。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let printerId : string = '1212';
print.removePrinters([printerId], (err: BusinessError) => {
    if (err) {
        console.error('removePrinters failed, because : ' + JSON.stringify(err));
    } else {
        console.info('removePrinters success');
    }
})
```

## print.removePrinters

removePrinters(printerIds: Array&lt;string&gt;): Promise&lt;void&gt;

移除打印机，使用Promise异步回调。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| printerIds | Array&lt;string&gt; | 是 | 表示需移除的打印机列表。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let printerId : string = '1212';
print.removePrinters([printerId]).then(() => {
    console.info('remove printers success');
}).catch((error: BusinessError) => {
    console.error('remove printers error : ' + JSON.stringify(error));
})
```

## print.updatePrinters

updatePrinters(printers: Array&lt;PrinterInfo&gt;, callback: AsyncCallback&lt;void&gt;): void

更新特定打印机的信息，使用callback异步回调。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| printers | Array&lt;[PrinterInfo](js-apis-print.md#printerinfo24)&gt; | 是 | 表示待更新的打印机列表。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 异步更新打印机信息之后的回调。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let printerInfo : print.PrinterInfo = {
    printerId : '3232',
    printerName : 'hhhhh',
    printerState : 0,
    printerIcon : 12,
    description : 'str',
    capability : undefined,
    options : 'opt'
};
print.updatePrinters([printerInfo], (err: BusinessError) => {
    if (err) {
        console.error('updatePrinters failed, because : ' + JSON.stringify(err));
    } else {
        console.info('updatePrinters success');
    }
})
```

## print.updatePrinters

updatePrinters(printers: Array&lt;PrinterInfo&gt;): Promise&lt;void&gt;

更新特定打印机的信息，使用Promise异步回调。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| printers | Array&lt;[PrinterInfo](js-apis-print.md#printerinfo24)&gt; | 是 | 表示待更新的打印机列表。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let printerInfo : print.PrinterInfo = {
    printerId : '3232',
    printerName : 'hhhhh',
    printerState : 0,
    printerIcon : 12,
    description : 'str',
    capability : undefined,
    options : 'opt'
};
print.updatePrinters([printerInfo]).then(() => {
    console.info('update printers success');
}).catch((error: BusinessError) => {
    console.error('update printers error : ' + JSON.stringify(error));
})
```

## print.updatePrinterState

updatePrinterState(printerId: string, state: PrinterState, callback: AsyncCallback&lt;void&gt;): void

更新打印机状态，使用callback异步回调。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| printerId | string | 是 | 表示打印机ID。 |
| state | [PrinterState](js-apis-print.md#printerstate14) | 是 | 表示打印机状态。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 异步更新打印机状态之后的回调。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let printerId : string = '1212';
let state : print.PrinterState = print.PrinterState.PRINTER_CONNECTED;
print.updatePrinterState(printerId, state, (err: BusinessError) => {
    if (err) {
        console.error('updatePrinterState failed, because : ' + JSON.stringify(err));
    } else {
        console.info('updatePrinterState success');
    }
})
```

## print.updatePrinterState

updatePrinterState(printerId: string, state: PrinterState): Promise&lt;void&gt;

更新打印机状态，使用Promise异步回调。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| printerId | string | 是 | 表示打印机ID。 |
| state | [PrinterState](js-apis-print.md#printerstate14) | 是 | 表示打印机状态。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let printerId : string = '1212';
let state : print.PrinterState = print.PrinterState.PRINTER_CONNECTED;
print.updatePrinterState(printerId, state).then(() => {
    console.info('update printer state success');
}).catch((error: BusinessError) => {
    console.error('update printer state error : ' + JSON.stringify(error));
})
```

## print.updateExtensionInfo

updateExtensionInfo(info: string, callback: AsyncCallback&lt;void&gt;): void

更新打印扩展状态，使用callback异步回调。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| info | string | 是 | 表示打印扩展变更信息。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 异步更新打印扩展状态之后的回调。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let info : string = 'WIFI_INACTIVE';
print.updateExtensionInfo(info, (err: BusinessError) => {
    if (err) {
        console.error('updateExtensionInfo failed, because : ' + JSON.stringify(err));
    } else {
        console.info('updateExtensionInfo success');
    }
})
```

## print.updateExtensionInfo

updateExtensionInfo(info: string): Promise&lt;void&gt;

更新打印扩展状态，使用Promise异步回调。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| info | string | 是 | 表示打印扩展变更信息。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let info : string = 'WIFI_INACTIVE';
print.updateExtensionInfo(info).then(() => {
    console.info('update print job state success');
}).catch((error: BusinessError) => {
    console.error('update print job state error : ' + JSON.stringify(error));
})
```

## print.queryAllPrintJobs<sup>(deprecated)</sup>

> 从API version 10开始支持，从API version 11开始废弃。
> 建议使用[queryPrintJobList](#printqueryprintjoblist11)替代。

queryAllPrintJobs(callback: AsyncCallback&lt;void&gt;): void

查询所有打印任务，使用callback异步回调。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;void&gt; | 是 | 异步查询所有打印任务之后的回调。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |

**示例：**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

print.queryAllPrintJobs((err: BusinessError) => {
    if (err) {
        console.error('queryAllPrintJobs failed, because : ' + JSON.stringify(err));
    } else {
        console.info('queryAllPrintJobs success');
    }
})
```

## print.queryAllPrintJobs<sup>(deprecated)</sup>

> 从API version 10开始支持，从API version 11开始废弃。
> 建议使用[queryPrintJobList](#printqueryprintjoblist11-1)替代。

queryAllPrintJobs(): Promise&lt;void&gt;

查询所有打印任务，使用Promise异步回调。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |

**示例：**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

print.queryAllPrintJobs().then(() => {
    console.info('queryAllPrintJobs success');
}).catch((error: BusinessError) => {
    console.error('queryAllPrintJobs failed, error : ' + JSON.stringify(error));
})
```

## print.queryAllActivePrintJobs<sup>20+</sup>

queryAllActivePrintJobs(): Promise&lt;[PrintJob](js-apis-print.md#printjob24)[]&gt;

查询所有活跃中的打印任务，使用Promise进行异步回调。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;[PrintJob](js-apis-print.md#printjob24)[]&gt; | Promise对象，返回包含所有活跃中的打印任务的列表。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |

**示例：**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

print.queryAllActivePrintJobs().then((printJobs : print.PrintJob[]) => {
    console.info('queryAllActivePrintJobs success, data : ' + JSON.stringify(printJobs));
}).catch((error: BusinessError) => {
    console.error('queryAllActivePrintJobs failed, error : ' + JSON.stringify(error));
})
```

## print.queryPrintJobList<sup>11+</sup>

queryPrintJobList(callback: AsyncCallback&lt;Array&lt;PrintJob&gt;&gt;): void

查询所有打印任务，使用callback异步回调。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;Array&lt;[PrintJob](js-apis-print.md#printjob24)&gt;&gt; | 是 | 异步查询所有打印任务之后的回调。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |

**示例：**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

print.queryPrintJobList((err: BusinessError, printJobs : print.PrintJob[]) => {
    if (err) {
        console.error('queryPrintJobList failed, because : ' + JSON.stringify(err));
    } else {
        console.info('queryPrintJobList success, data : ' + JSON.stringify(printJobs));
    }
})
```

## print.queryPrintJobList<sup>11+</sup>

queryPrintJobList(): Promise&lt;Array&lt;PrintJob&gt;&gt;

查询所有打印任务，使用Promise异步回调。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;Array&lt;[PrintJob](js-apis-print.md#printjob24)&gt;&gt; | Promise对象，返回包含所有打印任务的列表。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |

**示例：**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

print.queryPrintJobList().then((printJobs : print.PrintJob[]) => {
    console.info('queryPrintJobList success, data : ' + JSON.stringify(printJobs));
}).catch((error: BusinessError) => {
    console.error('queryPrintJobList failed, error : ' + JSON.stringify(error));
})
```

## print.queryPrintJobById<sup>11+</sup>

queryPrintJobById(jobId: string, callback: AsyncCallback&lt;PrintJob&gt;): void

按打印任务ID查询打印任务，使用callback异步回调。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| jobId | string | 是 | 表示打印任务ID。 |
| callback | AsyncCallback&lt;[PrintJob](js-apis-print.md#printjob24)&gt; | 是 | 异步按打印任务ID查询打印任务之后的回调。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let jobId : string = '1';
print.queryPrintJobById(jobId, (err: BusinessError, printJob : print.PrintJob) => {
    if (err) {
        console.error('queryPrintJobById failed, because : ' + JSON.stringify(err));
    } else {
        console.info('queryPrintJobById success, data : ' + JSON.stringify(printJob));
    }
})
```

## print.queryPrintJobById<sup>11+</sup>

queryPrintJobById(jobId: string): Promise&lt;PrintJob&gt;

按打印任务ID查询打印任务，使用Promise异步回调。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| jobId | string | 是 | 表示打印任务ID。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;[PrintJob](js-apis-print.md#printjob24)&gt; | Promise对象，返回查询到的打印任务。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let jobId : string = '1';
print.queryPrintJobById(jobId).then((printJob : print.PrintJob) => {
    console.info('queryPrintJobById data : ' + JSON.stringify(printJob));
}).catch((error: BusinessError) => {
    console.error('queryPrintJobById error : ' + JSON.stringify(error));
})
```

## print.startGettingPrintFile<sup>11+</sup>

startGettingPrintFile(jobId: string, printAttributes: PrintAttributes, fd: number, onFileStateChanged: Callback&lt;PrintFileCreationState&gt;): void

开始获取打印文件，使用Callback异步回调。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| jobId | string | 是 | 表示打印任务ID。 |
| printAttributes | [PrintAttributes](js-apis-print.md#printattributes11) | 是 | 表示打印参数。 |
| fd | number | 是 | 表示打印文件描述符。 |
| onFileStateChanged | Callback&lt;[PrintFileCreationState](js-apis-print.md#printfilecreationstate11)&gt; | 是 | 表示更新文件状态的回调。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```ts
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

## print.notifyPrintService<sup>11+</sup>

notifyPrintService(jobId: string, type: 'spooler_closed_for_cancelled' | 'spooler_closed_for_started', callback: AsyncCallback&lt;void&gt;): void

将spooler关闭信息通知打印服务，使用callback异步回调。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| jobId | string | 是 | 表示打印任务ID。 |
| type | 'spooler_closed_for_cancelled' \| 'spooler_closed_for_started' | 是 | 表示spooler关闭信息。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 异步将spooler关闭信息通知打印服务之后的回调。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let jobId : string = '1';
print.notifyPrintService(jobId, 'spooler_closed_for_started', (err: BusinessError) => {
    if (err) {
        console.error('notifyPrintService failed, because : ' + JSON.stringify(err));
    } else {
        console.info('notifyPrintService success');
    }
})
```

## print.notifyPrintService<sup>11+</sup>

notifyPrintService(jobId: string, type: 'spooler_closed_for_cancelled' | 'spooler_closed_for_started'): Promise&lt;void&gt;

将spooler关闭信息通知打印服务，使用Promise异步回调。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| jobId | string | 是 | 表示打印任务ID。 |
| type | 'spooler_closed_for_cancelled' \| 'spooler_closed_for_started' | 是 | 表示spooler关闭信息。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let jobId : string = '1';
print.notifyPrintService(jobId, 'spooler_closed_for_started').then(() => {
    console.info('notifyPrintService success');
}).catch((error: BusinessError) => {
    console.error('notifyPrintService error : ' + JSON.stringify(error));
})
```

## print.getPrinterInfoById<sup>12+</sup>

getPrinterInfoById(printerId: string): Promise&lt;PrinterInfo&gt;

根据打印机id获取打印机信息，使用Promise异步回调。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| printerId | string | 是 | 表示打印机ID。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;[PrinterInfo](js-apis-print.md#printerinfo24)&gt; | Promise对象，返回查询到的打印机信息。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let printerId : string = '1';
print.getPrinterInfoById(printerId).then((printerInfo : print.PrinterInfo) => {
    console.info('getPrinterInfoById data : ' + JSON.stringify(printerInfo));
}).catch((error: BusinessError) => {
    console.error('getPrinterInfoById error : ' + JSON.stringify(error));
})
```

## print.notifyPrintServiceEvent<sup>12+</sup>

notifyPrintServiceEvent(event: ApplicationEvent): Promise&lt;void&gt;

将打印应用相关事件通知打印服务，使用Promise异步回调。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| event | [ApplicationEvent](js-apis-print.md#applicationevent14) | 是 | 表示打印应用事件。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let event : print.ApplicationEvent = print.ApplicationEvent.APPLICATION_CREATED;
print.notifyPrintServiceEvent(event).then(() => {
    console.info('notifyPrintServiceEvent success');
}).catch((error: BusinessError) => {
    console.error('notifyPrintServiceEvent error : ' + JSON.stringify(error));
})
```

## print.setPrinterPreferences<sup>18+</sup>

setPrinterPreferences(printerId: string, printerPreferences: PrinterPreferences): Promise&lt;void&gt;

设置打印机首选项，使用Promise异步回调。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| printerId | string | 是 | 表示打印机ID。 |
| printerPreferences | [PrinterPreferences](js-apis-print.md#printerpreferences18) | 是 | 表示打印机首选项。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let printerId : string = 'testPrinterId';
let preferences : print.PrinterPreferences = {
    defaultDuplexMode: print.PrintDuplexMode.DUPLEX_MODE_NONE
};
print.setPrinterPreferences(printerId, preferences).then(() => {
    console.info('setPrinterPreferences success');
}).catch((error: BusinessError) => {
    console.error('setPrinterPreferences error : ' + JSON.stringify(error));
})
```

## print.discoverUsbPrinters<sup>18+</sup>

discoverUsbPrinters(): Promise&lt;Array&lt;PrinterInformation&gt;&gt;

发现usb打印机，使用Promise异步回调。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;Array&lt;[PrinterInformation](js-apis-print.md#printerinformation14)&gt;&gt; | Promise对象，返回发现到的usb打印机信息。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |

**示例：**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

print.discoverUsbPrinters().then((printers : print.PrinterInformation[]) => {
    console.info('discoverUsbPrinters data : ' + JSON.stringify(printers));
}).catch((error: BusinessError) => {
    console.error('discoverUsbPrinters error : ' + JSON.stringify(error));
})
```

## print.setDefaultPrinter<sup>18+</sup>

setDefaultPrinter(printerId: string, type: DefaultPrinterType): Promise&lt;void&gt;

设置默认打印机，使用Promise异步回调。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| printerId | string | 是 | 表示打印机ID。 |
| type | [DefaultPrinterType](js-apis-print.md#defaultprintertype18) | 是 | 表示默认打印机类型。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let printerId : string = '1';
let type : print.DefaultPrinterType = print.DefaultPrinterType.DEFAULT_PRINTER_TYPE_SET_BY_USER;
print.setDefaultPrinter(printerId, type).then(() => {
    console.info('setDefaultPrinter success');
}).catch((error: BusinessError) => {
    console.error('setDefaultPrinter error : ' + JSON.stringify(error));
})
```

## print.notifyPrintServiceEvent<sup>18+</sup>

notifyPrintServiceEvent(event: ApplicationEvent, jobId: string): Promise&lt;void&gt;

将打印应用相关事件通知打印服务，使用Promise异步回调。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| event | [ApplicationEvent](js-apis-print.md#applicationevent14) | 是 | 表示打印应用事件。 |
| jobId | string | 是 | 表示打印任务ID。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let event : print.ApplicationEvent = print.ApplicationEvent.APPLICATION_CREATED;
let jobId : string = '1';
print.notifyPrintServiceEvent(event, jobId).then(() => {
    console.info('notifyPrintServiceEvent success');
}).catch((error: BusinessError) => {
    console.error('notifyPrintServiceEvent error : ' + JSON.stringify(error));
})
```

## print.queryPrinterCapabilityByUri<sup>24+</sup>

queryPrinterCapabilityByUri(printerUri: string, printerId: string): Promise&lt;[PrinterCapabilities](js-apis-print.md#printercapabilities14)&gt;

使用打印机的uri查询打印机能力，使用Promise异步回调。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| printerUri | string | 是 | 表示打印机uri。 |
| printerId | string | 是 | 表示打印机ID。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;[PrinterCapabilities](js-apis-print.md#printercapabilities14)&gt; | Promise对象，返回打印机能力。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[打印服务错误码](errorcode-print.md)。

| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 13100005 | Can not find the printer in system. |

**示例：**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let printerUri : string = "testPrinterUri";
let printerId : string = "testPrinterId";
print.queryPrinterCapabilityByUri(printerUri, printerId).then((capabilities: print.PrinterCapabilities) => {
    console.info('queryPrinterCapabilityByUri success' + JSON.stringify(capabilities));
}).catch((error: BusinessError) => {
    console.error('queryPrinterCapabilityByUri error : ' + JSON.stringify(error));
})
```

## print.addPrinterToCups<sup>24+</sup>

addPrinterToCups(printerUri: string, printerName: string, printerMake: string): Promise&lt;boolean&gt;

添加打印机到cups，使用Promise异步回调。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| printerUri | string | 是 | 表示打印机uri。 |
| printerName | string | 是 | 表示打印机名称。 |
| printerMake | string | 是 | 表示打印机型号。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;boolean&gt; | Promise对象，返回true表示添加打印机到cups成功；返回false表示添加打印机到cups失败。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[打印服务错误码](errorcode-print.md)。

| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 13100003 | Add a printer to cups failed. |

**示例：**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let printerUri : string = "testPrinterUri";
let printerName : string = "testPrinterName";
let printerMake : string = "testPrinterMake";

print.addPrinterToCups(printerUri, printerName, printerMake).then((result: boolean) => {
    console.info('addPrinterToCups success' + JSON.stringify(result));
}).catch((error: BusinessError) => {
    console.error('addPrinterToCups error : ' + JSON.stringify(error));
})
```

## print.deletePrinterFromCups<sup>24+</sup>

deletePrinterFromCups(printerName: string): Promise&lt;void&gt;

从cups中删除打印机，使用Promise异步回调。

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Print.PrintFramework

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| printerName | string | 是 | 表示打印机名称。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |

**示例：**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let printerName : string = "testPrinterName";

print.deletePrinterFromCups(printerName).then(() => {
    console.info('deletePrinterFromCups success');
}).catch((error: BusinessError) => {
    console.error('deletePrinterFromCups error : ' + JSON.stringify(error));
})
```