# downloadFile

## downloadFile

```TypeScript
function downloadFile(context: BaseContext, config: DownloadConfig, callback: AsyncCallback<DownloadTask>): void
```

创建并启动一个下载任务，使用callback异步回调，支持HTTP协议。通过 on('complete'|'pause'|'remove') 可获取任务下载时的状态信息，包括任务完成、暂停或移除。通过 on('fail')可获取任务下载时的错误信息。 > **说明：** > > 示例中context的获取方式请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.INTERNET

<!--Device-request-function downloadFile(context: BaseContext, config: DownloadConfig, callback: AsyncCallback<DownloadTask>): void--><!--Device-request-function downloadFile(context: BaseContext, config: DownloadConfig, callback: AsyncCallback<DownloadTask>): void-End-->

**系统能力：** SystemCapability.MiscServices.Download

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-basecontext-c.md) | 是 | 基于应用程序的上下文。 |
| config | [DownloadConfig](arkts-basicservices-request-downloadconfig-i.md) | 是 | 下载的配置信息。 |
| callback | [AsyncCallback](arkts-basicservices-asynccallback-t.md)&lt;[DownloadTask](arkts-basicservices-request-downloadtask-i.md)&gt; | 是 | 回调函数。当下载任务成功，err为undefined，data为获取到的DownloadTask对象；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameters check fails. Possible causes: &lt;br&gt; 1. Missing mandatory parameters. &lt;br&gt; 2. Incorrect parameter type. &lt;br&gt; 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | The permissions check fails. |
| [13400001](../../apis-basic-services-kit/errorcode-request.md#13400001-文件操作异常) | Invalid file or file system error. |
| [13400002](../../apis-basic-services-kit/errorcode-request.md#13400002-文件路径异常) | File path not supported or invalid. |
| [13400003](../../apis-basic-services-kit/errorcode-request.md#13400003-服务异常) | Task service ability error. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
try {
  // 需要手动将url替换为真实服务器的HTTP协议地址
  request.downloadFile(context, {
    url: 'https://xxxx/xxxxx.hap',
    filePath: 'xxx/xxxxx.hap'
  }, (err: BusinessError, data: request.DownloadTask) => {
    if (err) {
      console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
      return;
    }
  });
} catch (err) {
  console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
}
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
try {
  // 需要手动将url替换为真实服务器的HTTP协议地址
  request.downloadFile(context, {
    url: 'https://xxxx/xxxxx.hap',
    filePath: 'xxx/xxxxx.hap'
  }, (err: Error, data: request.DownloadTask): void => {
    if (err) {
      console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
      return;
    }
  });
} catch (err) {
  console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
}
```


## downloadFile

```TypeScript
function downloadFile(context: BaseContext, config: DownloadConfig): Promise<DownloadTask>
```

创建并启动一个下载任务，使用Promise异步回调，支持HTTP协议。通过 on('complete'|'pause'|'remove') 可以获取任务下载时的状态信息，包括任务完成、暂停或移除。通过 on('fail')可以获取任务下载时的错误信息。 > **说明：** > > 示例中context的获取方式请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.INTERNET

<!--Device-request-function downloadFile(context: BaseContext, config: DownloadConfig): Promise<DownloadTask>--><!--Device-request-function downloadFile(context: BaseContext, config: DownloadConfig): Promise<DownloadTask>-End-->

**系统能力：** SystemCapability.MiscServices.Download

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-basecontext-c.md) | 是 | 基于应用程序的上下文。 |
| config | [DownloadConfig](arkts-basicservices-request-downloadconfig-i.md) | 是 | 下载的配置信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[DownloadTask](arkts-basicservices-request-downloadtask-i.md)&gt; | 使用Promise方式，异步返回下载任务DownloadTask的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameters check fails. Possible causes: &lt;br&gt; 1. Missing mandatory parameters. &lt;br&gt; 2. Incorrect parameter type. &lt;br&gt; 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | The permissions check fails. |
| [13400001](../../apis-basic-services-kit/errorcode-request.md#13400001-文件操作异常) | Invalid file or file system error. |
| [13400002](../../apis-basic-services-kit/errorcode-request.md#13400002-文件路径异常) | File path not supported or invalid. |
| [13400003](../../apis-basic-services-kit/errorcode-request.md#13400003-服务异常) | Task service ability error. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
try {
  // 需要手动将url替换为真实服务器的HTTP协议地址
  request.downloadFile(context, { url: 'https://xxxx/xxxx.hap' }).then((data: request.DownloadTask) => {
     let downloadTask: request.DownloadTask = data;
  }).catch((err: BusinessError) => {
    console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
  })
} catch (err) {
  console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
}
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  try {
    // 需要手动将url替换为真实服务器的HTTP协议地址
    request.downloadFile(context, { url: 'https://xxxx/xxxx.hap' }).then((data: request.DownloadTask) => {
      let downloadTask: request.DownloadTask = data;
    }).catch((err: Error) => {
      console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
    })
  } catch (err) {
    console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
  }
```

