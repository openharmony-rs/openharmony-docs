# ProgressSignal

定义进度取消的函数，在粘贴过程中可选择取消任务，且仅当进度指示选项[ProgressIndicator](arkts-basicservices-pasteboard-progressindicator-e.md)设置为NONE时此参数才生效。

**起始版本：** 23

<!--Device-pasteboard-export class ProgressSignal--><!--Device-pasteboard-export class ProgressSignal-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

## 导入模块

```TypeScript
import { pasteboard } from '@kit.BasicServicesKit';
```

## cancel

```TypeScript
cancel(): void
```

取消正在进行的拷贝粘贴任务。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ProgressSignal-cancel(): void--><!--Device-ProgressSignal-cancel(): void-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

**示例**

ArkTS-Dyn示例：

```TypeScript
import { BusinessError, pasteboard } from '@kit.BasicServicesKit';
@Entry
@Component
struct PasteboardTest {
 build() {
   RelativeContainer() {
     Column() {
       Column() {
         Button("Copy txt")
           .onClick(async ()=>{
              let text = "test";
              let pasteData = pasteboard.createData(pasteboard.MIMETYPE_TEXT_PLAIN, text);
              let systemPasteboard = pasteboard.getSystemPasteboard();
              await systemPasteboard.setData(pasteData);
              let signal = new pasteboard.ProgressSignal;
              let ProgressListener = (progress: pasteboard.ProgressInfo) => {
                console.info('progressListener success, progress:' + progress.progress);
                signal.cancel();
              }
              let params: pasteboard.GetDataParams = {
                destUri: '/data/storage/el2/base/haps/entry/files/dstFile.txt',
                fileConflictOptions: pasteboard.FileConflictOptions.OVERWRITE,
                progressIndicator: pasteboard.ProgressIndicator.DEFAULT,
                progressListener: ProgressListener
              };
              systemPasteboard.getDataWithProgress(params).then((pasteData: pasteboard.PasteData) => {
                console.info('getDataWithProgress success');
              }).catch((err: BusinessError) => {
                console.error('Failed to get PasteData. Cause: ' + err.message);
              })
          })
        }
      }
    }
  }
}
```

ArkTS-Sta示例：

```TypeScript
import pasteboard from '@ohos.pasteboard'
import { Entry, Component,RelativeContainer,Column ,Button} from '@ohos.arkui.component';
import { BusinessError } from '@kit.BasicServicesKit';
import { fileUri } from '@kit.CoreFileKit';
@Entry
@Component
struct PasteboardTest {
 build() {
   RelativeContainer() {
     Column() {
       Column() {
         Button("Copy txt")
           .onClick(async ()=>{
              let text = "test";
              let pasteData = pasteboard.createData(pasteboard.MIMETYPE_TEXT_PLAIN, text);
              let systemPasteboard = pasteboard.getSystemPasteboard();
              await systemPasteboard.setData(pasteData);
              let signal = new pasteboard.ProgressSignal;
              let progressListenerInfo = (progress: pasteboard.ProgressInfo) => {
                console.info('progressListener success, progress:' + progress.progress);
                signal.cancel();
              };
              let destPath: string = '/data/storage/el2/base/files/';
              let destUri : string = fileUri.getUriFromPath(destPath);
              let params: pasteboard.GetDataParams = {
                destUri: destUri,
                fileConflictOptions: pasteboard.FileConflictOptions.OVERWRITE,
                progressIndicator: pasteboard.ProgressIndicator.DEFAULT,
                progressListener: progressListenerInfo,
              };
              systemPasteboard.getDataWithProgress(params).then((pasteData: pasteboard.PasteData) => {
                console.info('getDataWithProgress success');
              }).catch((err: BusinessError) => {
                console.error('Failed to get PasteData. Cause: ' + err.message);
              })
          })
        }
      }
    }
  }
}
```

