# uploadFile

## 导入模块

```TypeScript
import { request } from '@kit.BasicServicesKit';
```

## uploadFile

```TypeScript
function uploadFile(context: BaseContext, config: UploadConfig, callback: AsyncCallback<UploadTask>): void
```

创建并启动一个上传任务，使用callback异步回调，支持HTTP协议。通过[on('complete'|'fail')](request.UploadTask.on(type: 'complete' | 'fail', callback: Callback&lt;Array<TaskState>&gt;))可获取任务上传时的成功信息或错误信息。
> **说明：**  
>  
> 示例中context的获取方式请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

**起始版本：** 9

**需要权限：** ohos.permission.INTERNET

<!--Device-request-function uploadFile(context: BaseContext, config: UploadConfig, callback: AsyncCallback<UploadTask>): void--><!--Device-request-function uploadFile(context: BaseContext, config: UploadConfig, callback: AsyncCallback<UploadTask>): void-End-->

**系统能力：** SystemCapability.MiscServices.Upload

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-basecontext-t.md) | 是 | 基于应用程序的上下文。 |
| config | [UploadConfig](arkts-basicservices-request-uploadconfig-i.md) | 是 | 上传的配置信息。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;UploadTask&gt; | 是 | 回调函数，异步返回UploadTask对象。当上传成功，err为undefined，data为获取到的UploadTask对象；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The permissions check fails. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameters check fails. Possible causes:<br> 1. Missing mandatory parameters.<br> 2. Incorrect parameter type.<br> 3. Parameter verification failed. |
| [13400002](../../apis-basic-services-kit/errorcode-request.md#13400002-文件路径异常) | File path not supported or invalid. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let uploadTask: request.UploadTask;
let uploadConfig: request.UploadConfig = {
  url: 'http://www.example.com', // 需要手动将url替换为真实服务器的HTTP协议地址
  header: { 'Accept': '*/*' },
  method: 'POST',
  files: [{ filename: 'test', name: 'test', uri: 'internal://cache/test.jpg', type: 'image/jpeg' }], // 建议type填写HTTP协议规范的MIME类型
  data: [{ name: 'name123', value: '123' }],
};
try {
  request.uploadFile(context, uploadConfig, (err: BusinessError, data: request.UploadTask) => {
    if (err) {
      console.error(`Failed to request the upload. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    uploadTask = data;
  });
} catch (err) {
  console.error(`Failed to request the upload. Code: ${err.code}, message: ${err.message}`);
}

```


## uploadFile

```TypeScript
function uploadFile(context: BaseContext, config: UploadConfig): Promise<UploadTask>
```

创建并启动一个上传任务，使用Promise异步回调，支持HTTP协议。通过[on('complete'|'fail')](request.UploadTask.on(type: 'complete' | 'fail', callback: Callback&lt;Array<TaskState>&gt;))可获取任务上传时的成功信息或错误信息。
> **说明：**  
>  
> 示例中context的获取方式请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

**起始版本：** 9

**需要权限：** ohos.permission.INTERNET

<!--Device-request-function uploadFile(context: BaseContext, config: UploadConfig): Promise<UploadTask>--><!--Device-request-function uploadFile(context: BaseContext, config: UploadConfig): Promise<UploadTask>-End-->

**系统能力：** SystemCapability.MiscServices.Upload

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-basecontext-t.md) | 是 | 基于应用程序的上下文。 |
| config | [UploadConfig](arkts-basicservices-request-uploadconfig-i.md) | 是 | 上传的配置信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;UploadTask&gt; | 使用Promise方式，异步返回上传任务UploadTask的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The permissions check fails. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameters check fails. Possible causes:<br> 1. Missing mandatory parameters.<br> 2. Incorrect parameter type.<br> 3. Parameter verification failed. |
| [13400002](../../apis-basic-services-kit/errorcode-request.md#13400002-文件路径异常) | File path not supported or invalid. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let uploadTask: request.UploadTask;
let uploadConfig: request.UploadConfig = {
  url: 'http://www.example.com', // 需要手动将url替换为真实服务器的HTTP协议地址
  header: { 'Accept': '*/*' },
  method: 'POST',
  files: [{ filename: 'test', name: 'test', uri: 'internal://cache/test.jpg', type: 'image/jpeg' }], // 建议type填写HTTP协议规范的MIME类型
  data: [{ name: 'name123', value: '123' }],
};
try {
  request.uploadFile(context, uploadConfig).then((data: request.UploadTask) => {
    uploadTask = data;
  }).catch((err: BusinessError) => {
    console.error(`Failed to request the upload. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  console.error(`Failed to request the upload. Code: ${err.code}, message: ${err.message}`);
}

```

