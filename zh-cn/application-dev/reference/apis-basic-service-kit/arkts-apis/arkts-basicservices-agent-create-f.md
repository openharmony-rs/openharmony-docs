# create

## create

```TypeScript
function create(context: BaseContext, config: Config, callback: AsyncCallback<Task>): void
```

创建需要上传或下载的任务，并将其排入队列。支持HTTP/HTTPS协议，使用callback异步回调。 > **说明：** > > 示例中context的获取方式请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.INTERNET

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-agent-function create(context: BaseContext, config: Config, callback: AsyncCallback<Task>): void--><!--Device-agent-function create(context: BaseContext, config: Config, callback: AsyncCallback<Task>): void-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-basecontext-c.md) | 是 | 基于应用程序的上下文。 |
| config | Config | 是 | 上传/下载任务的配置信息。 |
| callback | [AsyncCallback](arkts-basicservices-asynccallback-t.md)&lt;Task&gt; | 是 | 回调函数。当创建上传或下载任务成功，err为undefined，data为获取到的Task对象；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt; 1. Missing mandatory parameters. &lt;br&gt; 2. Incorrect parameter type. &lt;br&gt; 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [21900004](../../apis-basic-services-kit/errorcode-request.md#21900004-应用任务队列已满) | The application task queue is full. |
| [21900005](../../apis-basic-services-kit/errorcode-request.md#21900005-任务模式错误) | Operation with wrong task mode. |
| [13400001](../../apis-basic-services-kit/errorcode-request.md#13400001-文件操作异常) | Invalid file or file system error. |
| [13400003](../../apis-basic-services-kit/errorcode-request.md#13400003-服务异常) | Task service ability error. |

## 示例

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let attachments: Array<request.agent.FormItem> = [{
  name: "createTest",
  value: {
    filename: "createTest.avi",
    path: "./createTest.avi",
  }
}];
let config: request.agent.Config = {
  action: request.agent.Action.UPLOAD,
  url: 'http://127.0.0.1', // 需要手动将url替换为真实服务器的HTTP协议地址
  title: 'createTest',
  description: 'Sample code for create task',
  mode: request.agent.Mode.BACKGROUND,
  overwrite: false,
  method: "PUT",
  data: attachments,
  saveas: "./",
  network: request.agent.Network.CELLULAR,
  metered: false,
  roaming: true,
  retry: true,
  redirect: true,
  index: 0,
  begins: 0,
  ends: -1,
  gauge: false,
  precise: false,
  token: "it is a secret"
};
request.agent.create(context, config, async (err: BusinessError, task: request.agent.Task) => {
  console.info(`Succeeded in creating a download task. result: ${task.config}`);
  await task.start();
  // 用户需要手动调用remove从而结束task对象的生命周期
  request.agent.remove(task.tid);
});
```


## create

```TypeScript
function create(context: BaseContext, config: Config): Promise<Task>
```

创建需要上传或下载的任务，并将其排入队列。支持HTTP/HTTPS协议，使用Promise异步回调。 > **说明：** > > 示例中context的获取方式请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.INTERNET

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-agent-function create(context: BaseContext, config: Config): Promise<Task>--><!--Device-agent-function create(context: BaseContext, config: Config): Promise<Task>-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-basecontext-c.md) | 是 | 基于应用程序的上下文。 |
| config | Config | 是 | 上传/下载任务的配置信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Task&gt; | Promise对象。返回任务配置信息的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt; 1. Missing mandatory parameters. &lt;br&gt; 2. Incorrect parameter type. &lt;br&gt; 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [21900004](../../apis-basic-services-kit/errorcode-request.md#21900004-应用任务队列已满) | The application task queue is full. |
| [21900005](../../apis-basic-services-kit/errorcode-request.md#21900005-任务模式错误) | Operation with wrong task mode. |
| [13400001](../../apis-basic-services-kit/errorcode-request.md#13400001-文件操作异常) | Invalid file or file system error. |
| [13400003](../../apis-basic-services-kit/errorcode-request.md#13400003-服务异常) | Task service ability error. |

## 示例

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let attachments: Array<request.agent.FormItem> = [{
  name: "createTest",
  value: {
    filename: "createTest.avi",
    path: "./createTest.avi",
  }
}];
let config: request.agent.Config = {
  action: request.agent.Action.UPLOAD,
  url: 'http://127.0.0.1', // 需要手动将url替换为真实服务器的HTTP协议地址
  title: 'createTest',
  description: 'Sample code for create task',
  mode: request.agent.Mode.BACKGROUND,
  overwrite: false,
  method: "PUT",
  data: attachments,
  saveas: "./",
  network: request.agent.Network.CELLULAR,
  metered: false,
  roaming: true,
  retry: true,
  redirect: true,
  index: 0,
  begins: 0,
  ends: -1,
  gauge: false,
  precise: false,
  token: "it is a secret"
};
request.agent.create(context, config).then(async (task: request.agent.Task) => {
  console.info(`Succeeded in creating a download task. result: ${task.config}`);
  await task.start();
  // 用户需要手动调用remove从而结束task对象的生命周期
  request.agent.remove(task.tid);
}).catch((err: Error) => {
  console.error(`Failed to create a download task, Code: ${err.code}, message: ${err.message}`);
});
```

