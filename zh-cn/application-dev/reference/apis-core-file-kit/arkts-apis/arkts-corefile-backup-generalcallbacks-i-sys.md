# GeneralCallbacks（系统接口）

备份和恢复过程中的通用回调。 备份服务通过这些回调向客户端通知备份或恢复阶段。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-backup-interface GeneralCallbacks--><!--Device-backup-interface GeneralCallbacks-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

## onProcess

```TypeScript
onProcess(bundleName: string, process: string): void
```

备份服务返回结果或进度信息时触发的回调。 返回应用的处理结果或进度信息。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GeneralCallbacks-onProcess(bundleName: string, process: string): void--><!--Device-GeneralCallbacks-onProcess(bundleName: string, process: string): void-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 触发回调的应用名称。 |
| process | string | 是 | 应用备份或恢复的进度信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |
| 13900005 | I/O error |
| 13500008 | Untar error |
| 13900001 | Operation not permitted |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| 13500006 | Tar error |
| 13900025 | No space left on device |
| 13600001 | IPC error |
| 13900011 | Out of memory |

## 示例

```TypeScript
import { backup } from '@kit.CoreFileKit';

onProcess: (bundleName: string, process: string) => {
  console.info('onProcess bundleName : ' + bundleName);
  console.info('onProcess processInfo : ' + process);
}
```

## onResultReport

```TypeScript
onResultReport(bundleName: string, result: string): void
```

备份服务返回结果信息时触发的回调。 第一个字符串参数表示触发回调的应用名称。 第二个字符串参数表示应用的处理结果。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GeneralCallbacks-onResultReport(bundleName: string, result: string): void--><!--Device-GeneralCallbacks-onResultReport(bundleName: string, result: string): void-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 触发回调的应用名称。 |
| result | string | 是 | 应用备份或恢复的结果信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |
| 13900005 | I/O error |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| 13900025 | No space left on device |
| 13600001 | IPC error |
| 13900042 | Unknown error |
| 13900011 | Out of memory |

## onAllBundlesEnd

```TypeScript
onAllBundlesEnd: AsyncCallback<undefined>
```

所有应用的备份或恢复完成或异常中止时触发的回调。

**类型：** [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;undefined&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-GeneralCallbacks-onAllBundlesEnd: AsyncCallback<undefined>--><!--Device-GeneralCallbacks-onAllBundlesEnd: AsyncCallback<undefined>-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

## onBackupServiceDied

```TypeScript
onBackupServiceDied: Callback<undefined>
```

备份服务异常死亡时触发的回调。

**类型：** [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;undefined&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-GeneralCallbacks-onBackupServiceDied: Callback<undefined>--><!--Device-GeneralCallbacks-onBackupServiceDied: Callback<undefined>-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

## onBackupSizeReport

```TypeScript
onBackupSizeReport?: OnBackupSizeReport
```

备份服务返回结果或进度信息时触发的回调。 返回框架扫描到的应用待备份数据量信息。

**类型：** [OnBackupSizeReport](arkts-corefile-backup-onbackupsizereport-t-sys.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-GeneralCallbacks-onBackupSizeReport?: OnBackupSizeReport--><!--Device-GeneralCallbacks-onBackupSizeReport?: OnBackupSizeReport-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

## onBundleBegin

```TypeScript
onBundleBegin: AsyncCallback<string, BundlePara>
```

应用备份或恢复开始时触发的回调。 第一个字符串参数表示应用名称。 发生BusinessError时，第二个字符串参数 返回对应的应用名称。

**类型：** [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;string, [BundlePara](arkts-corefile-backup-bundlepara-t-sys.md)&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GeneralCallbacks-onBundleBegin: AsyncCallback<string, BundlePara>--><!--Device-GeneralCallbacks-onBundleBegin: AsyncCallback<string, BundlePara>-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

## onBundleEnd

```TypeScript
onBundleEnd: AsyncCallback<string, BundlePara>
```

应用备份或恢复成功结束或异常中止时触发的回调。 第一个字符串参数表示应用名称。 发生BusinessError时，第二个字符串参数 返回对应的应用名称。

**类型：** [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;string, [BundlePara](arkts-corefile-backup-bundlepara-t-sys.md)&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GeneralCallbacks-onBundleEnd: AsyncCallback<string, BundlePara>--><!--Device-GeneralCallbacks-onBundleEnd: AsyncCallback<string, BundlePara>-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

## onFileReady

```TypeScript
onFileReady: AsyncCallback<File>
```

备份服务向客户端发送文件时触发的回调。 File参数表示发送给客户端的文件。 返回的文件归备份服务所有，客户端关闭文件句柄后由备份服务清理。

**类型：** [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;File&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-GeneralCallbacks-onFileReady: AsyncCallback<File>--><!--Device-GeneralCallbacks-onFileReady: AsyncCallback<File>-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

## onFileReadyBatch

```TypeScript
onFileReadyBatch?: OnFileReadyBatch
```

备份服务向客户端发送文件时触发的回调。 File参数表示发送给客户端的文件。 返回的文件归备份服务所有，客户端关闭文件句柄后由备份服务清理。

**类型：** [OnFileReadyBatch](arkts-corefile-backup-onfilereadybatch-t-sys.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GeneralCallbacks-onFileReadyBatch?: OnFileReadyBatch--><!--Device-GeneralCallbacks-onFileReadyBatch?: OnFileReadyBatch-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

## onMigrateResult

```TypeScript
onMigrateResult?: AsyncCallback<string, void | string>
```

文件迁移流程结束时触发的回调。 第一个字符串参数表示应用名称。 发生BusinessError时，第二个字符串参数 返回对应的应用名称。

**类型：** [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;string, void \| string&gt;

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GeneralCallbacks-onMigrateResult?: AsyncCallback<string, void | string>--><!--Device-GeneralCallbacks-onMigrateResult?: AsyncCallback<string, void | string>-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

## onProcess

```TypeScript
onProcess: OnProcess
```

备份服务返回结果或进度信息时触发的回调。 返回应用的处理结果或进度信息。

**类型：** [OnProcess](arkts-corefile-backup-onprocess-t-sys.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GeneralCallbacks-onProcess: OnProcess--><!--Device-GeneralCallbacks-onProcess: OnProcess-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

## onResultReport

```TypeScript
onResultReport: OnResultReport
```

备份服务返回结果信息时触发的回调。 第一个字符串参数表示触发回调的应用名称。 第二个字符串参数表示应用的处理结果。

**类型：** [OnResultReport](arkts-corefile-backup-onresultreport-t-sys.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GeneralCallbacks-onResultReport: OnResultReport--><!--Device-GeneralCallbacks-onResultReport: OnResultReport-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

