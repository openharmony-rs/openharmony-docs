# UploadTask

上传任务，使用下列方法前，需要先获取UploadTask对象，promise形式通过 [request.uploadFile](arkts-basicservices-request-uploadfile-f.md#uploadFile)获取，callback形式通过 [request.uploadFile](arkts-basicservices-request-uploadfile-f.md#uploadFile) 获取。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-request-interface UploadTask--><!--Device-request-interface UploadTask-End-->

**系统能力：** SystemCapability.MiscServices.Download

## delete

```TypeScript
delete(callback: AsyncCallback<boolean>): void
```

移除上传的任务，使用callback异步回调。 > **说明：** > > 由于不存在401报错场景，在api12中 `401 the parameters check fails` 这个错误码被移除。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.INTERNET

<!--Device-UploadTask-delete(callback: AsyncCallback<boolean>): void--><!--Device-UploadTask-delete(callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.MiscServices.Upload

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-asynccallback-t.md)&lt;boolean&gt; | 是 | 回调函数。返回true表示移除上传任务成功；返回false表示移除上传任务失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The permissions check fails. |

## 示例

```TypeScript
uploadTask.delete((err: BusinessError, result: boolean) => {
  if (err) {
    console.error(`Failed to delete the upload task. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in deleting the upload task.');
});
```

## delete

```TypeScript
delete(): Promise<boolean>
```

移除上传的任务，使用Promise异步回调。 > **说明：** > > 由于不存在401报错场景，在api12中 `401 the parameters check fails` 这个错误码被移除。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.INTERNET

<!--Device-UploadTask-delete(): Promise<boolean>--><!--Device-UploadTask-delete(): Promise<boolean>-End-->

**系统能力：** SystemCapability.MiscServices.Upload

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示移除上传任务成功；返回false表示移除上传任务失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The permissions check fails. |

## 示例

ArkTS-Dyn示例：

```TypeScript
uploadTask.delete().then((result: boolean) => {
  console.info('Succeeded in deleting the upload task.');
}).catch((err: BusinessError) => {
  console.error(`Failed to delete the upload task. Code: ${err.code}, message: ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let uploadTask: request.UploadTask;
let uploadConfig: request.UploadConfig = {
  url: 'http://www.example.com', // 需要手动将url替换为真实服务器的HTTP协议地址
  header: { 'Accept': '*/*' },
  method: "POST",
  files: [{ filename: "test", name: "test", uri: "internal://cache/test.jpg", type: "image/jpeg" }], // 建议type填写HTTP协议规范的MIME类型
  data: [{ name: "name123", value: "123" }],
};
try {
  request.uploadFile(context, uploadConfig, (err: Error, data: request.UploadTask): void => {
    if (err) {
      console.error(`Failed to request the upload. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    uploadTask = data;
  });
} catch (err) {
  console.error(`Failed to request the upload. Code: ${err.code}, message: ${err.message}`);
}
uploadTask.delete().then((result: boolean) => {
  console.info('Succeeded in deleting the upload task.');
}).catch((err: Error) => {
  console.error(`Failed to delete the upload task. Code: ${err.code}, message: ${err.message}`);
});
```

## offComplete

```TypeScript
offComplete(callback?: Callback<Array<TaskState>>): void
```

Called when the current upload session complete.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-UploadTask-offComplete(callback?: Callback<Array<TaskState>>): void--><!--Device-UploadTask-offComplete(callback?: Callback<Array<TaskState>>): void-End-->

**系统能力：** SystemCapability.MiscServices.Upload

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](arkts-basicservices-callback-t.md)&lt;Array&lt;[TaskState](arkts-basicservices-request-taskstate-i.md)&gt;&gt; | 否 | The callback function for the upload complete event. |

## 示例

```TypeScript
// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let uploadTask: request.UploadTask;
let uploadConfig: request.UploadConfig = {
  url: 'http://www.example.com', // 需要手动将url替换为真实服务器的HTTP协议地址
  header: { 'Accept': '*/*' },
  method: "POST",
  files: [{ filename: "test", name: "test", uri: "internal://cache/test.jpg", type: "image/jpeg" }], // 建议type填写HTTP协议规范的MIME类型
  data: [{ name: "name123", value: "123" }],
};
let upCompleteCallback1 = (taskStates: Array<request.TaskState>) => {
  console.info('Upload delete complete notification.');
  for (let i = 0; i < taskStates.length; i++) {
    console.info('taskState:' + JSON.stringify(taskStates[i]));
  }
};
let upCompleteCallback2 = (taskStates: Array<request.TaskState>) => {
  console.info('Upload delete complete notification.');
  for (let i = 0; i < taskStates.length; i++) {
    console.info('taskState:' + JSON.stringify(taskStates[i]));
  }
};
try {
  request.uploadFile(context, uploadConfig, (err: Error, uploadTask: request.UploadTask): void => {
    if (err) {
      console.error(`Failed to request the upload. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    uploadTask.onComplete(upCompleteCallback1);
    uploadTask.onComplete(upCompleteCallback2);
    // 表示取消headerCallback1的订阅
    uploadTask.offComplete(upCompleteCallback1);
    // 表示取消订阅上传任务完成的所有回调
    uploadTask.offComplete();
  });
} catch (err) {
  console.error(`Failed to request the upload. Code: ${err.code}, message: ${err.message}`);
}
```

## offFail

```TypeScript
offFail(callback?: Callback<Array<TaskState>>): void
```

Called when the current upload session fail.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-UploadTask-offFail(callback?: Callback<Array<TaskState>>): void--><!--Device-UploadTask-offFail(callback?: Callback<Array<TaskState>>): void-End-->

**系统能力：** SystemCapability.MiscServices.Upload

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](arkts-basicservices-callback-t.md)&lt;Array&lt;[TaskState](arkts-basicservices-request-taskstate-i.md)&gt;&gt; | 否 | The callback function for the upload fail change event. |

## 示例

```TypeScript
// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let uploadTask: request.UploadTask;
let uploadConfig: request.UploadConfig = {
  url: 'http://www.example.com', // 需要手动将url替换为真实服务器的HTTP协议地址
  header: { 'Accept': '*/*' },
  method: "POST",
  files: [{ filename: "test", name: "test", uri: "internal://cache/test.jpg", type: "image/jpeg" }], // 建议type填写HTTP协议规范的MIME类型
  data: [{ name: "name123", value: "123" }],
};
let upFailCallback1 = (taskStates: Array<request.TaskState>) => {
  console.info('Upload delete fail notification.');
  for (let i = 0; i < taskStates.length; i++) {
    console.info('taskState:' + JSON.stringify(taskStates[i]));
  }
};
let upFailCallback2 = (taskStates: Array<request.TaskState>) => {
  console.info('Upload delete fail notification.');
  for (let i = 0; i < taskStates.length; i++) {
    console.info('taskState:' + JSON.stringify(taskStates[i]));
  }
};
try {
  request.uploadFile(context, uploadConfig, (err: Error, uploadTask: request.UploadTask): void => {
    if (err) {
      console.error(`Failed to request the upload. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    uploadTask.onFail(upFailCallback1);
    uploadTask.onFail(upFailCallback2);
    // 表示取消headerCallback1的订阅
    uploadTask.offFail(upFailCallback1);
    // 表示取消订阅上传任务失败的所有回调
    uploadTask.offFail();
  });
} catch (err) {
  console.error(`Failed to request the upload. Code: ${err.code}, message: ${err.message}`);
}
```

## offHeaderReceive

```TypeScript
offHeaderReceive(callback?: UploadHeaderReceiveCallback): void
```

Called when the header of the current upload session has been received.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-UploadTask-offHeaderReceive(callback?: UploadHeaderReceiveCallback): void--><!--Device-UploadTask-offHeaderReceive(callback?: UploadHeaderReceiveCallback): void-End-->

**系统能力：** SystemCapability.MiscServices.Upload

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [UploadHeaderReceiveCallback](arkts-basicservices-request-uploadheaderreceivecallback-t.md) | 否 | The callback function for the HTTP Response Header event. |

## 示例

```TypeScript
// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let uploadTask: request.UploadTask;
let uploadConfig: request.UploadConfig = {
  url: 'http://www.example.com', // 需要手动将url替换为真实服务器的HTTP协议地址
  header: { 'Accept': '*/*' },
  method: "POST",
  files: [{ filename: "test", name: "test", uri: "internal://cache/test.jpg", type: "image/jpeg" }], // 建议type填写HTTP协议规范的MIME类型
  data: [{ name: "name123", value: "123" }],
};
let headerCallback1 = (header: object) => {
  console.info(`Upload delete headerReceive notification. header: ${JSON.stringify(header)}`);
};
let headerCallback2 = (header: object) => {
  console.info(`Upload delete headerReceive notification. header: ${JSON.stringify(header)}`);
};
try {
  request.uploadFile(context, uploadConfig, (err: Error, uploadTask: request.UploadTask): void => {
    if (err) {
      console.error(`Failed to request the upload. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    uploadTask.onHeaderReceive(headerCallback1);
    uploadTask.onHeaderReceive(headerCallback2);
    // 表示取消headerCallback1的订阅
    uploadTask.offHeaderReceive(headerCallback1);
    // 表示取消订阅上传任务HTTP标头事件的所有回调
    uploadTask.offHeaderReceive();
  });
} catch (err) {
  console.error(`Failed to request the upload. Code: ${err.code}, message: ${err.message}`);
}
```

## offProgress

```TypeScript
offProgress(callback?: UploadProgressCallback): void
```

Called when the current upload session is in process.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-UploadTask-offProgress(callback?: UploadProgressCallback): void--><!--Device-UploadTask-offProgress(callback?: UploadProgressCallback): void-End-->

**系统能力：** SystemCapability.MiscServices.Upload

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [UploadProgressCallback](arkts-basicservices-request-uploadprogresscallback-t.md) | 否 | The callback function for the upload progress event. |

## 示例

```TypeScript
// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let uploadTask: request.UploadTask;
let uploadConfig: request.UploadConfig = {
  url: 'http://www.example.com', // 需要手动将url替换为真实服务器的HTTP协议地址
  header: { 'Accept': '*/*' },
  method: "POST",
  files: [{ filename: "test", name: "test", uri: "internal://cache/test.jpg", type: "image/jpeg" }], // 建议type填写HTTP协议规范的MIME类型
  data: [{ name: "name123", value: "123" }],
};
let upProgressCallback1 = (uploadedSize: long, totalSize: long) => {
  console.info('Upload delete progress notification.' + 'totalSize:' + totalSize + 'uploadedSize:' + uploadedSize);
};
let upProgressCallback2 = (uploadedSize: long, totalSize: long) => {
  console.info('Upload delete progress notification.' + 'totalSize:' + totalSize + 'uploadedSize:' + uploadedSize);
};
try {
  request.uploadFile(context, uploadConfig, (err: Error, uploadTask: request.UploadTask): void => {
    if (err) {
      console.error(`Failed to request the upload. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    uploadTask.onProgress(upProgressCallback1);
    uploadTask.onProgress(upProgressCallback2);
    // 表示取消upProgressCallback1的订阅
    uploadTask.offProgress(upProgressCallback1);
    // 表示取消订阅上传任务进度事件的所有回调
    uploadTask.offProgress();
  });
} catch (err) {
  console.error(`Failed to request the upload. Code: ${err.code}, message: ${err.message}`);
}
```

## off_complete

```TypeScript
off(type: 'complete' | 'fail', callback?: Callback<Array<TaskState>>): void
```

取消订阅上传任务的完成或失败事件。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

<!--Device-UploadTask-off(type: 'complete' | 'fail', callback?: Callback<Array<TaskState>>): void--><!--Device-UploadTask-off(type: 'complete' | 'fail', callback?: Callback<Array<TaskState>>): void-End-->

**系统能力：** SystemCapability.MiscServices.Upload

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'complete' \| 'fail' | 是 | 取消订阅的事件类型。&lt;br&gt;- 取值为'complete'，表示上传任务完成。&lt;br&gt;- 取值为'fail'，表示上传任务失败。 |
| callback | [Callback](arkts-basicservices-callback-t.md)&lt;Array&lt;[TaskState](arkts-basicservices-request-taskstate-i.md)&gt;&gt; | 否 | 需要取消订阅的回调函数。若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | the parameters check fails. Possible causes: &lt;br&gt; 1. Missing mandatory parameters. &lt;br&gt; 2. Incorrect parameter type. &lt;br&gt; 3. Parameter verification failed.<br>**适用版本：** 12+ |

## 示例

```TypeScript
let upCompleteCallback1 = (taskStates: Array<request.TaskState>) => {
  console.info('Upload delete complete notification.');
  for (let i = 0; i < taskStates.length; i++) {
    console.info('taskState:' + JSON.stringify(taskStates[i]));
  }
};
let upCompleteCallback2 = (taskStates: Array<request.TaskState>) => {
  console.info('Upload delete complete notification.');
  for (let i = 0; i < taskStates.length; i++) {
    console.info('taskState:' + JSON.stringify(taskStates[i]));
  }
};
uploadTask.on('complete', upCompleteCallback1);
uploadTask.on('complete', upCompleteCallback2);
// 表示取消headerCallback1的订阅
uploadTask.off('complete', upCompleteCallback1);
// 表示取消订阅上传任务完成的所有回调
uploadTask.off('complete');

let upFailCallback1 = (taskStates: Array<request.TaskState>) => {
  console.info('Upload delete fail notification.');
  for (let i = 0; i < taskStates.length; i++) {
    console.info('taskState:' + JSON.stringify(taskStates[i]));
  }
};
let upFailCallback2 = (taskStates: Array<request.TaskState>) => {
  console.info('Upload delete fail notification.');
  for (let i = 0; i < taskStates.length; i++) {
    console.info('taskState:' + JSON.stringify(taskStates[i]));
  }
};
uploadTask.on('fail', upFailCallback1);
uploadTask.on('fail', upFailCallback2);
// 表示取消headerCallback1的订阅
uploadTask.off('fail', upFailCallback1);
// 表示取消订阅上传任务失败的所有回调
uploadTask.off('fail');
```

## off_fail

```TypeScript
off(type: 'complete' | 'fail', callback?: Callback<Array<TaskState>>): void
```

取消订阅上传任务的完成或失败事件。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

<!--Device-UploadTask-off(type: 'complete' | 'fail', callback?: Callback<Array<TaskState>>): void--><!--Device-UploadTask-off(type: 'complete' | 'fail', callback?: Callback<Array<TaskState>>): void-End-->

**系统能力：** SystemCapability.MiscServices.Upload

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'complete' \| 'fail' | 是 | 取消订阅的事件类型。&lt;br&gt;- 取值为'complete'，表示上传任务完成。&lt;br&gt;- 取值为'fail'，表示上传任务失败。 |
| callback | [Callback](arkts-basicservices-callback-t.md)&lt;Array&lt;[TaskState](arkts-basicservices-request-taskstate-i.md)&gt;&gt; | 否 | 需要取消订阅的回调函数。若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | the parameters check fails. Possible causes: &lt;br&gt; 1. Missing mandatory parameters. &lt;br&gt; 2. Incorrect parameter type. &lt;br&gt; 3. Parameter verification failed.<br>**适用版本：** 12+ |

## 示例

```TypeScript
let upCompleteCallback1 = (taskStates: Array<request.TaskState>) => {
  console.info('Upload delete complete notification.');
  for (let i = 0; i < taskStates.length; i++) {
    console.info('taskState:' + JSON.stringify(taskStates[i]));
  }
};
let upCompleteCallback2 = (taskStates: Array<request.TaskState>) => {
  console.info('Upload delete complete notification.');
  for (let i = 0; i < taskStates.length; i++) {
    console.info('taskState:' + JSON.stringify(taskStates[i]));
  }
};
uploadTask.on('complete', upCompleteCallback1);
uploadTask.on('complete', upCompleteCallback2);
// 表示取消headerCallback1的订阅
uploadTask.off('complete', upCompleteCallback1);
// 表示取消订阅上传任务完成的所有回调
uploadTask.off('complete');

let upFailCallback1 = (taskStates: Array<request.TaskState>) => {
  console.info('Upload delete fail notification.');
  for (let i = 0; i < taskStates.length; i++) {
    console.info('taskState:' + JSON.stringify(taskStates[i]));
  }
};
let upFailCallback2 = (taskStates: Array<request.TaskState>) => {
  console.info('Upload delete fail notification.');
  for (let i = 0; i < taskStates.length; i++) {
    console.info('taskState:' + JSON.stringify(taskStates[i]));
  }
};
uploadTask.on('fail', upFailCallback1);
uploadTask.on('fail', upFailCallback2);
// 表示取消headerCallback1的订阅
uploadTask.off('fail', upFailCallback1);
// 表示取消订阅上传任务失败的所有回调
uploadTask.off('fail');
```

## off_headerReceive

```TypeScript
off(type: 'headerReceive', callback?: (header: object) => void): void
```

取消订阅上传任务HTTP响应事件。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

<!--Device-UploadTask-off(type: 'headerReceive', callback?: (header: object) => void): void--><!--Device-UploadTask-off(type: 'headerReceive', callback?: (header: object) => void): void-End-->

**系统能力：** SystemCapability.MiscServices.Upload

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'headerReceive' | 是 | 取消订阅的事件类型。&lt;br&gt;- 取值为'headerReceive'，表示HTTP请求接收到响应。 |
| callback | (header: object) =&gt; void | 否 | 需要取消订阅的回调函数。若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameters check fails. Possible causes: &lt;br&gt; 1. Missing mandatory parameters. &lt;br&gt; 2. Incorrect parameter type. &lt;br&gt; 3. Parameter verification failed.<br>**适用版本：** 12+ |

## 示例

```TypeScript
let headerCallback1 = (header: object) => {
  console.info(`Upload delete headerReceive notification. header: ${JSON.stringify(header)}`);
};
let headerCallback2 = (header: object) => {
  console.info(`Upload delete headerReceive notification. header: ${JSON.stringify(header)}`);
};
uploadTask.on('headerReceive', headerCallback1);
uploadTask.on('headerReceive', headerCallback2);
// 表示取消headerCallback1的订阅
uploadTask.off('headerReceive', headerCallback1);
// 表示取消订阅上传任务HTTP标头事件的所有回调
uploadTask.off('headerReceive');
```

## off_progress

```TypeScript
off(type: 'progress', callback?: (uploadedSize: long, totalSize: long) => void): void
```

取消订阅上传任务进度事件。

**起始版本：** 6

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为6。

**废弃版本：** -1

<!--Device-UploadTask-off(type: 'progress', callback?: (uploadedSize: long, totalSize: long) => void): void--><!--Device-UploadTask-off(type: 'progress', callback?: (uploadedSize: long, totalSize: long) => void): void-End-->

**系统能力：** SystemCapability.MiscServices.Upload

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'progress' | 是 | 取消订阅的事件类型。&lt;br&gt;- 取值为'progress'，表示上传的进度信息。 |
| callback | (uploadedSize: long, totalSize: long) =&gt; void | 否 | 需要取消订阅的回调函数。若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameters check fails. Possible causes: &lt;br&gt; 1. Missing mandatory parameters. &lt;br&gt; 2. Incorrect parameter type. &lt;br&gt; 3. Parameter verification failed.<br>**适用版本：** 12+ |

## 示例

```TypeScript
let upProgressCallback1 = (uploadedSize: number, totalSize: number) => {
  console.info('Upload delete progress notification.' + 'totalSize:' + totalSize + 'uploadedSize:' + uploadedSize);
};
let upProgressCallback2 = (uploadedSize: number, totalSize: number) => {
  console.info('Upload delete progress notification.' + 'totalSize:' + totalSize + 'uploadedSize:' + uploadedSize);
};
uploadTask.on('progress', upProgressCallback1);
uploadTask.on('progress', upProgressCallback2);
// 表示取消upProgressCallback1的订阅
uploadTask.off('progress', upProgressCallback1);
// 表示取消订阅上传任务进度事件的所有回调
uploadTask.off('progress');
```

## onComplete

```TypeScript
onComplete(callback: Callback<Array<TaskState>>): void
```

Called when the current upload session complete.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-UploadTask-onComplete(callback: Callback<Array<TaskState>>): void--><!--Device-UploadTask-onComplete(callback: Callback<Array<TaskState>>): void-End-->

**系统能力：** SystemCapability.MiscServices.Upload

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](arkts-basicservices-callback-t.md)&lt;Array&lt;[TaskState](arkts-basicservices-request-taskstate-i.md)&gt;&gt; | 是 | The callback function for the upload complete event. |

## 示例

```TypeScript
// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let uploadTask: request.UploadTask;
let uploadConfig: request.UploadConfig = {
  url: 'http://www.example.com', // 需要手动将url替换为真实服务器的HTTP协议地址
  header: { 'Accept': '*/*' },
  method: "POST",
  files: [{ filename: "test", name: "test", uri: "internal://cache/test.jpg", type: "image/jpeg" }], // 建议type填写HTTP协议规范的MIME类型
  data: [{ name: "name123", value: "123" }],
};
let upCompleteCallback = (taskStates: Array<request.TaskState>) => {
  for (let i = 0; i < taskStates.length; i++) {
    console.info("upOnComplete taskState:" + JSON.stringify(taskStates[i]));
  }
};
try {
  request.uploadFile(context, uploadConfig, (err: Error, uploadTask: request.UploadTask): void => {
    if (err) {
      console.error(`Failed to request the upload. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    uploadTask.onComplete(upCompleteCallback);
  });
} catch (err) {
  console.error(`Failed to request the upload. Code: ${err.code}, message: ${err.message}`);
}
```

## onFail

```TypeScript
onFail(callback: Callback<Array<TaskState>>): void
```

Called when the current upload session fail.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-UploadTask-onFail(callback: Callback<Array<TaskState>>): void--><!--Device-UploadTask-onFail(callback: Callback<Array<TaskState>>): void-End-->

**系统能力：** SystemCapability.MiscServices.Upload

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](arkts-basicservices-callback-t.md)&lt;Array&lt;[TaskState](arkts-basicservices-request-taskstate-i.md)&gt;&gt; | 是 | The callback function for the upload fail event. |

## 示例

```TypeScript
// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let uploadTask: request.UploadTask;
let uploadConfig: request.UploadConfig = {
  url: 'http://www.example.com', // 需要手动将url替换为真实服务器的HTTP协议地址
  header: { 'Accept': '*/*' },
  method: "POST",
  files: [{ filename: "test", name: "test", uri: "internal://cache/test.jpg", type: "image/jpeg" }], // 建议type填写HTTP协议规范的MIME类型
  data: [{ name: "name123", value: "123" }],
};
let upFailCallback = (taskStates: Array<request.TaskState>) => {
  for (let i = 0; i < taskStates.length; i++) {
    console.info("upOnFail taskState:" + JSON.stringify(taskStates[i]));
  }
};
try {
  request.uploadFile(context, uploadConfig, (err: Error, uploadTask: request.UploadTask): void => {
    if (err) {
      console.error(`Failed to request the upload. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    uploadTask.onFail(upFailCallback);
  });
} catch (err) {
  console.error(`Failed to request the upload. Code: ${err.code}, message: ${err.message}`);
}
```

## onHeaderReceive

```TypeScript
onHeaderReceive(callback: UploadHeaderReceiveCallback): void
```

Called when the header of the current upload session has been received.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-UploadTask-onHeaderReceive(callback: UploadHeaderReceiveCallback): void--><!--Device-UploadTask-onHeaderReceive(callback: UploadHeaderReceiveCallback): void-End-->

**系统能力：** SystemCapability.MiscServices.Upload

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [UploadHeaderReceiveCallback](arkts-basicservices-request-uploadheaderreceivecallback-t.md) | 是 | The callback function for the HTTP Response Header event. |

## 示例

```TypeScript
// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let uploadTask: request.UploadTask;
let uploadConfig: request.UploadConfig = {
  url: 'http://www.example.com', // 需要手动将url替换为真实服务器的HTTP协议地址
  header: { 'Accept': '*/*' },
  method: "POST",
  files: [{ filename: "test", name: "test", uri: "internal://cache/test.jpg", type: "image/jpeg" }], // 建议type填写HTTP协议规范的MIME类型
  data: [{ name: "name123", value: "123" }],
};
let headerCallback = (headers: object) => {
  console.info("upOnHeader headers:" + JSON.stringify(headers));
};
try {
  request.uploadFile(context, uploadConfig, (err: Error, uploadTask: request.UploadTask): void => {
    if (err) {
      console.error(`Failed to request the upload. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    uploadTask.onHeaderReceive(headerCallback);
  });
} catch (err) {
  console.error(`Failed to request the upload. Code: ${err.code}, message: ${err.message}`);
}
```

## onProgress

```TypeScript
onProgress(callback: UploadProgressCallback): void
```

Called when the current upload session is in process.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-UploadTask-onProgress(callback: UploadProgressCallback): void--><!--Device-UploadTask-onProgress(callback: UploadProgressCallback): void-End-->

**系统能力：** SystemCapability.MiscServices.Upload

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [UploadProgressCallback](arkts-basicservices-request-uploadprogresscallback-t.md) | 是 | The callback function for the upload progress event. |

## 示例

```TypeScript
// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let uploadTask: request.UploadTask;
let uploadConfig: request.UploadConfig = {
  url: 'http://www.example.com', // 需要手动将url替换为真实服务器的HTTP协议地址
  header: { 'Accept': '*/*' },
  method: "POST",
  files: [{ filename: "test", name: "test", uri: "internal://cache/test.jpg", type: "image/jpeg" }], // 建议type填写HTTP协议规范的MIME类型
  data: [{ name: "name123", value: "123" }],
};
let upProgressCallback = (uploadedSize: long, totalSize: long) => {
  console.info("upload totalSize:" + totalSize + "  uploadedSize:" + uploadedSize);
};
try {
  request.uploadFile(context, uploadConfig, (err: Error, uploadTask: request.UploadTask): void => {
    if (err) {
      console.error(`Failed to request the upload. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    uploadTask.onProgress(upProgressCallback);
  });
} catch (err) {
  console.error(`Failed to request the upload. Code: ${err.code}, message: ${err.message}`);
}
```

## on_complete

```TypeScript
on(type: 'complete' | 'fail', callback: Callback<Array<TaskState>>): void
```

订阅上传任务完成或失败事件，使用callback异步回调。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

<!--Device-UploadTask-on(type: 'complete' | 'fail', callback: Callback<Array<TaskState>>): void--><!--Device-UploadTask-on(type: 'complete' | 'fail', callback: Callback<Array<TaskState>>): void-End-->

**系统能力：** SystemCapability.MiscServices.Upload

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'complete' \| 'fail' | 是 | 订阅的事件类型，支持的事件包括：`'complete'`\|`'fail'`。&lt;br/&gt;- `'complete'`：表示上传任务完成，任务完成时触发该 事件。 &lt;br/&gt;- `'fail'`：表示上传任务失败，任务失败时触发该事件。 |
| callback | [Callback](arkts-basicservices-callback-t.md)&lt;Array&lt;[TaskState](arkts-basicservices-request-taskstate-i.md)&gt;&gt; | 是 | 上传任务完成或失败的回调函数。返回上传任务的任务状态信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameters check fails. Possible causes: &lt;br&gt; 1. Missing mandatory parameters. &lt;br&gt; 2. Incorrect parameter type. &lt;br&gt; 3. Parameter verification failed.<br>**适用版本：** 12+ |

## 示例

```TypeScript
let upCompleteCallback = (taskStates: Array<request.TaskState>) => {
  for (let i = 0; i < taskStates.length; i++) {
    console.info("upOnComplete taskState:" + JSON.stringify(taskStates[i]));
  }
};
uploadTask.on('complete', upCompleteCallback);

let upFailCallback = (taskStates: Array<request.TaskState>) => {
  for (let i = 0; i < taskStates.length; i++) {
    console.info("upOnFail taskState:" + JSON.stringify(taskStates[i]));
  }
};
uploadTask.on('fail', upFailCallback);
```

## on_fail

```TypeScript
on(type: 'complete' | 'fail', callback: Callback<Array<TaskState>>): void
```

订阅上传任务完成或失败事件，使用callback异步回调。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

<!--Device-UploadTask-on(type: 'complete' | 'fail', callback: Callback<Array<TaskState>>): void--><!--Device-UploadTask-on(type: 'complete' | 'fail', callback: Callback<Array<TaskState>>): void-End-->

**系统能力：** SystemCapability.MiscServices.Upload

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'complete' \| 'fail' | 是 | 订阅的事件类型，支持的事件包括：`'complete'`\|`'fail'`。&lt;br/&gt;- `'complete'`：表示上传任务完成，任务完成时触发该 事件。 &lt;br/&gt;- `'fail'`：表示上传任务失败，任务失败时触发该事件。 |
| callback | [Callback](arkts-basicservices-callback-t.md)&lt;Array&lt;[TaskState](arkts-basicservices-request-taskstate-i.md)&gt;&gt; | 是 | 上传任务完成或失败的回调函数。返回上传任务的任务状态信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameters check fails. Possible causes: &lt;br&gt; 1. Missing mandatory parameters. &lt;br&gt; 2. Incorrect parameter type. &lt;br&gt; 3. Parameter verification failed.<br>**适用版本：** 12+ |

## 示例

```TypeScript
let upCompleteCallback = (taskStates: Array<request.TaskState>) => {
  for (let i = 0; i < taskStates.length; i++) {
    console.info("upOnComplete taskState:" + JSON.stringify(taskStates[i]));
  }
};
uploadTask.on('complete', upCompleteCallback);

let upFailCallback = (taskStates: Array<request.TaskState>) => {
  for (let i = 0; i < taskStates.length; i++) {
    console.info("upOnFail taskState:" + JSON.stringify(taskStates[i]));
  }
};
uploadTask.on('fail', upFailCallback);
```

## on_headerReceive

```TypeScript
on(type: 'headerReceive', callback: (header: object) => void): void
```

订阅上传任务HTTP响应事件，使用callback异步回调。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

<!--Device-UploadTask-on(type: 'headerReceive', callback: (header: object) => void): void--><!--Device-UploadTask-on(type: 'headerReceive', callback: (header: object) => void): void-End-->

**系统能力：** SystemCapability.MiscServices.Upload

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'headerReceive' | 是 | 订阅的事件类型。&lt;br&gt;- 取值为'headerReceive'，HTTP请求接收到响应时触发该事件。 |
| callback | (header: object) =&gt; void | 是 | HTTP Response事件的回调函数，返回响应请求内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameters check fails. Possible causes: &lt;br&gt; 1. Missing mandatory parameters. &lt;br&gt; 2. Incorrect parameter type. &lt;br&gt; 3. Parameter verification failed.<br>**适用版本：** 12+ |

## 示例

```TypeScript
let headerCallback = (headers: object) => {
  console.info("upOnHeader headers:" + JSON.stringify(headers));
};
uploadTask.on('headerReceive', headerCallback);
```

## on_progress

```TypeScript
on(type: 'progress', callback: (uploadedSize: long, totalSize: long) => void): void
```

订阅上传任务进度事件，使用callback异步回调。 > **说明：** > > 应用处于后台时，为满足功耗性能要求，不支持调用此接口进行回调。

**起始版本：** 6

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为6。

**废弃版本：** -1

<!--Device-UploadTask-on(type: 'progress', callback: (uploadedSize: long, totalSize: long) => void): void--><!--Device-UploadTask-on(type: 'progress', callback: (uploadedSize: long, totalSize: long) => void): void-End-->

**系统能力：** SystemCapability.MiscServices.Upload

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'progress' | 是 | 订阅的事件类型。取值为'progress'，表示上传的进度信息，任务进度有进展时触发该事件。 |
| callback | (uploadedSize: long, totalSize: long) =&gt; void | 是 | 上传任务进度的回调函数，返回已上传文件大小和上传文件总大小，单位为字节（B）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameters check fails. Possible causes: &lt;br&gt; 1. Missing mandatory parameters. &lt;br&gt; 2. Incorrect parameter type. &lt;br&gt; 3. Parameter verification failed.<br>**适用版本：** 12+ |

## 示例

```TypeScript
let upProgressCallback = (uploadedSize: number, totalSize: number) => {
  console.info("upload totalSize:" + totalSize + "  uploadedSize:" + uploadedSize);
};
uploadTask.on('progress', upProgressCallback);
```

## remove

```TypeScript
remove(callback: AsyncCallback<boolean>): void
```

移除上传的任务，使用callback异步回调。 > **说明：** > > 从API version 6开始支持，从API version 9开始废弃，建议使用 > [delete](#delete)替代。

**起始版本：** 6

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为6。

**废弃版本：** 9

**替代接口：** [delete](#delete)(callback: AsyncCallback&lt;boolean&gt;)

**需要权限：** ohos.permission.INTERNET

<!--Device-UploadTask-remove(callback: AsyncCallback<boolean>): void--><!--Device-UploadTask-remove(callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.MiscServices.Upload

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-asynccallback-t.md)&lt;boolean&gt; | 是 | 回调函数。返回true表示移除上传任务成功；返回false表示移除上传任务失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The permissions check fails. |

## 示例

```TypeScript
uploadTask.remove((err: BusinessError, result: boolean) => {
  if (err) {
    console.error(`Failed to remove the upload task. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  if (result) {
    console.info('Succeeded in removing the upload task.');
  }
});
```

## remove

```TypeScript
remove(): Promise<boolean>
```

移除上传的任务，使用Promise异步回调。 > **说明：** > > 从API version 6开始支持，从API version 9开始废弃，建议使用[delete](#delete)替代。

**起始版本：** 6

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为6。

**废弃版本：** 9

**替代接口：** [delete](#delete)()

**需要权限：** ohos.permission.INTERNET

<!--Device-UploadTask-remove(): Promise<boolean>--><!--Device-UploadTask-remove(): Promise<boolean>-End-->

**系统能力：** SystemCapability.MiscServices.Upload

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | 使用Promise方式异步回调，返回true表示移除上传任务成功；返回false表示移除上传任务失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The permissions check fails. |

## 示例

```TypeScript
uploadTask.remove().then((result: boolean) => {
  console.info('Succeeded in removing the upload task.');
}).catch((err: BusinessError) => {
  console.error(`Failed to remove the upload task. Code: ${err.code}, message: ${err.message}`);
});
```

