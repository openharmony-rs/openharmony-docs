# SystemPasteboard

系统剪贴板对象。 在调用SystemPasteboard的接口前，需要先通过[getSystemPasteboard](arkts-basicservices-pasteboard-getsystempasteboard-f.md#getSystemPasteboard)获取系统剪贴板。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-pasteboard-interface SystemPasteboard--><!--Device-pasteboard-interface SystemPasteboard-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

## clear

```TypeScript
clear(callback: AsyncCallback<void>): void
```

清空系统剪贴板内容，使用callback异步回调。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [clearData](#clearData)(callback: AsyncCallback&lt;void&gt;)

<!--Device-SystemPasteboard-clear(callback: AsyncCallback<void>): void--><!--Device-SystemPasteboard-clear(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当成功清空时，err为undefined；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |

## 示例

```TypeScript
const systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
systemPasteboard.clear((err, data) => {
    if (err) {
        console.error(`Failed to clear the PasteData. Cause: ${err.message}`);
        return;
    }
    console.info('Succeeded in clearing the PasteData.');
});
```

## clear

```TypeScript
clear(): Promise<void>
```

清空系统剪贴板内容，使用Promise异步回调。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [clearData](#clearData)()

<!--Device-SystemPasteboard-clear(): Promise<void>--><!--Device-SystemPasteboard-clear(): Promise<void>-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
systemPasteboard.clear().then((data) => {
    console.info('Succeeded in clearing the PasteData.');
}).catch((err: BusinessError) => {
    console.error(`Failed to clear the PasteData. Cause: ${err.message}`);
});
```

## clearData

```TypeScript
clearData(callback: AsyncCallback<void>): void
```

清空系统剪贴板内容，使用callback异步回调。调用此方法后，系统将删除剪贴板中的所有数据，触发已注册的'update'监听回调。 清空成功后，剪贴板中将没有任何数据，hasData方法将返回false。适用于需要异步清空剪贴板且不阻塞主线程的场景，如UI响应优先的交互流程。 与同步接口[clearDataSync](#clearDataSync)不同，此接口不会阻塞UI线程，更适合在UI交互中使用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SystemPasteboard-clearData(callback: AsyncCallback<void>): void--><!--Device-SystemPasteboard-clearData(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当成功清空时，err为undefined；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |

## 示例

```TypeScript
const systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
systemPasteboard.clearData((err, data) => {
    if (err) {
        console.error(`Failed to clear the pasteboard. Cause: ${err.message}`);
        return;
    }
    console.info('Succeeded in clearing the pasteboard.');
});
```

## clearData

```TypeScript
clearData(): Promise<void>
```

清空系统剪贴板内容，使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SystemPasteboard-clearData(): Promise<void>--><!--Device-SystemPasteboard-clearData(): Promise<void>-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
systemPasteboard.clearData().then((data: void) => {
    console.info('Succeeded in clearing the pasteboard.');
}).catch((err: BusinessError) => {
    console.error(`Failed to clear the pasteboard. Cause: ${err.message}`);
});
```

## clearDataSync

```TypeScript
clearDataSync(): void
```

清空系统剪贴板内容，此接口为同步接口。适用于需要在关键业务流程中同步清空剪贴板数据，或需要立即确认清空结果的场景。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-SystemPasteboard-clearDataSync(): void--><!--Device-SystemPasteboard-clearDataSync(): void-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12900005](../../apis-basic-services-kit/errorcode-pasteboard.md#12900005-请求超时) | Excessive processing time for internal data. |

## 示例

```TypeScript
const systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
try {
    systemPasteboard.clearDataSync();
    console.info('Succeeded in clearing the pasteboard.');
} catch (err) {
    console.error('Failed to clear the pasteboard. Cause:' + err.message);
};
```

## detectPatterns

```TypeScript
detectPatterns(patterns: Array<Pattern>): Promise<Array<Pattern>>
```

检测**本地**剪贴板中存在的[Pattern](arkts-basicservices-pasteboard-pattern-e.md#Pattern)模式，使用Promise异步回调。 本地剪贴板指当前设备上的剪贴板数据，不包括跨设备传输的远端剪贴板数据。 适用于应用在粘贴数据前需要检测剪贴板内容是否包含特定类型的数据(如URL、邮箱、电话号码等)，以便进行相应处理或提供智能提示的场景。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-SystemPasteboard-detectPatterns(patterns: Array<Pattern>): Promise<Array<Pattern>>--><!--Device-SystemPasteboard-detectPatterns(patterns: Array<Pattern>): Promise<Array<Pattern>>-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| patterns | Array&lt;Pattern&gt; | 是 | 需要在剪贴板中检测的模式，用于检查剪贴板数据是否符合特定格式。 可选值包括：URL(URL类型)、NUMBER(数字类型)、EMAIL_ADDRESS(邮箱地址类型)等。 取值范围：数组元素数量不限，元素值只能为Pattern枚举值。传入无效值时返回错误码401。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;Pattern&gt;&gt; | Promise对象，返回检测到的模式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { pasteboard } from '@kit.BasicServicesKit'

const systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
let patterns: Array<pasteboard.Pattern> = [pasteboard.Pattern.URL, pasteboard.Pattern.EMAIL_ADDRESS];

systemPasteboard.detectPatterns(patterns).then((data: Array<pasteboard.Pattern>) => {
    if (patterns.sort().join('')==data.sort().join('')) {
      console.info('All needed patterns detected, next get data');
      try {
        let result: pasteboard.PasteData = systemPasteboard.getDataSync();
        console.info('Succeeded in getting PasteData.');
      } catch (err) {
        console.error('Failed to get PasteData. Cause:' + err.message);
      };
    } else {
      console.info("Not all needed patterns detected, no need to get data.");
    }
});
```

ArkTS-Sta示例：

```TypeScript
import { pasteboard } from '@kit.BasicServicesKit'
import { BusinessError } from '@kit.BasicServicesKit';

let systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
let patterns: Array<pasteboard.Pattern> = [pasteboard.Pattern.URL, pasteboard.Pattern.EMAIL_ADDRESS];

systemPasteboard.detectPatterns(patterns).then((data: Array<pasteboard.Pattern>) => {
    if (patterns.sort().join('')==data.sort().join('')) {
        console.info('All needed patterns detected, next get data');
        try {
            let result: pasteboard.PasteData = systemPasteboard.getDataSync();
            console.info('Succeeded in getting PasteData.');
        } catch (err: BusinessError) {
            console.error('Failed to get PasteData. Cause:' + err.message);
        };
    } else {
        console.info("Not all needed patterns detected, no need to get data.");
    }
});
```

## getChangeCount

```TypeScript
getChangeCount(): long
```

获取剪贴板内容的变化次数。执行成功时返回剪贴板内容的变化次数，否则返回0。 当剪贴板内容过期或调用[clearDataSync](#clearDataSync)等接口导致剪贴板内容为空时，内容变化次数不会因此改变。 系统重启或剪贴板服务异常重启时，剪贴板内容变化次数重新从0开始计数。对同一内容连续多次复制会被记录为多次更改，每次复制均会导致内容变化次数增加。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-SystemPasteboard-getChangeCount(): long--><!--Device-SystemPasteboard-getChangeCount(): long-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 返回读取到的剪贴板内容变化次数。 |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError, pasteboard } from '@kit.BasicServicesKit';

const systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
try {
    let result : number = systemPasteboard.getChangeCount();
    console.info(`Succeeded in getting the ChangeCount. Result: ${result}`);
} catch (err) {
    console.error(`Failed to get the ChangeCount. Cause: ${err.message}`);
};
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError, pasteboard } from '@kit.BasicServicesKit';

let systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
try {
    let result : long = systemPasteboard.getChangeCount();
    console.info(`Succeeded in getting the ChangeCount. Result: ${result}`);
} catch (err) {
    console.error(`Failed to get the ChangeCount. Cause: ${err.message}`);
};
```

## getData

```TypeScript
getData(callback: AsyncCallback<PasteData>): void
```

读取系统剪贴板内容，使用callback异步回调。将剪贴板数据封装为PasteData对象返回。调用此方法后，系统将从剪贴板服务读取当前内容，通过callback返回PasteData对象。 读取成功后，应用可以通过PasteData对象的方法获取具体的数据内容（如文本、HTML、URI等）。适用于需要异步读取剪贴板内容的场景，如UI响应优先、避免阻塞主线程。 与[getDataSync](#getDataSync)相比，getData不会阻塞UI线程，适合处理大量数据或远端数据。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** 
- API版本12+：ohos.permission.READ_PASTEBOARD

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SystemPasteboard-getData(callback: AsyncCallback<PasteData>): void--><!--Device-SystemPasteboard-getData(callback: AsyncCallback<PasteData>): void-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-asynccallback-t.md)&lt;[PasteData](arkts-basicservices-pasteboard-pastedata-i.md)&gt; | 是 | 回调函数。当读取成功，err为undefined，data为返回的系统剪贴板数据；否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| [27787277](../../apis-basic-services-kit/errorcode-pasteboard.md#27787277-另外一个复制或粘贴正在进行) | Another copy or paste operation is in progress. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API.<br>**适用版本：** 12+ |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
systemPasteboard.getData((err: BusinessError, pasteData: pasteboard.PasteData) => {
    if (err) {
        console.error('Failed to get PasteData. Cause: ' + err.message);
        return;
    }
    let text: string = pasteData.getPrimaryText();
});
```

## getData

```TypeScript
getData(): Promise<PasteData>
```

读取系统剪贴板内容，将剪贴板数据封装为PasteData对象返回，使用Promise异步回调。适用于需要异步读取剪贴板内容的场景，如UI响应优先、避免阻塞主线程。 适用于应用需要使用标准化数据结构[UnifiedData](../../apis-arkdata/arkts-apis/arkts-arkdata-unifieddatachannel-unifieddata-c.md#UnifiedData)读取剪贴板数据的场景。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** 
- API版本12+：ohos.permission.READ_PASTEBOARD

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SystemPasteboard-getData(): Promise<PasteData>--><!--Device-SystemPasteboard-getData(): Promise<PasteData>-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[PasteData](arkts-basicservices-pasteboard-pastedata-i.md)&gt; | Promise对象，返回系统剪贴板数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [27787277](../../apis-basic-services-kit/errorcode-pasteboard.md#27787277-另外一个复制或粘贴正在进行) | Another copy or paste operation is in progress. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API.<br>**适用版本：** 12+ |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
systemPasteboard.getData().then((pasteData: pasteboard.PasteData) => {
    let text: string = pasteData.getPrimaryText();
}).catch((err: BusinessError) => {
    console.error('Failed to get PasteData. Cause: ' + err.message);
});
```

## getDataSource

```TypeScript
getDataSource(): string
```

获取剪贴板数据的来源应用名称。适用于安全审计、数据追踪或向用户提示数据来源等场景。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-SystemPasteboard-getDataSource(): string--><!--Device-SystemPasteboard-getDataSource(): string-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 数据来源的应用名称。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12900005](../../apis-basic-services-kit/errorcode-pasteboard.md#12900005-请求超时) | Excessive processing time for internal data. |

## 示例

```TypeScript
const systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
try {
    let result: string = systemPasteboard.getDataSource();
    console.info(`Succeeded in getting DataSource. Result: ${result}`);
} catch (err) { 
    console.error('Failed to get DataSource. Cause:' + err.message);
};
```

## getDataSync

```TypeScript
getDataSync(): PasteData
```

读取系统剪贴板内容，此接口为同步接口。适用于应用需要在关键业务流程中同步获取剪贴板数据，或需要立即处理剪贴板内容的场景。 避免在UI线程调用此接口，以免阻塞界面；处理大量数据或远端数据时，建议使用异步接口[getData](arkts-basicservices-pasteboard-pastedatarecord-i.md#getData)。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** 
- API版本12+：ohos.permission.READ_PASTEBOARD

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-SystemPasteboard-getDataSync(): PasteData--><!--Device-SystemPasteboard-getDataSync(): PasteData-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PasteData](arkts-basicservices-pasteboard-pastedata-i.md) | 返回系统剪贴板数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12900005](../../apis-basic-services-kit/errorcode-pasteboard.md#12900005-请求超时) | Excessive processing time for internal data. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API.<br>**适用版本：** 12+ |

## 示例

```TypeScript
const systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
try {
    let result: pasteboard.PasteData = systemPasteboard.getDataSync();
    console.info('Succeeded in getting PasteData.');
} catch (err) {
    console.error('Failed to get PasteData. Cause:' + err.message);
};
```

## getDataWithProgress

```TypeScript
getDataWithProgress(params: GetDataParams): Promise<PasteData>
```

获取剪贴板的内容和进度，使用Promise异步回调，不支持对文件夹的拷贝。 对于大文件拷贝操作，建议设置进度监听以跟踪拷贝进度，避免在UI线程长时间等待；建议合理设置目标路径以确保有足够的存储空间。 适用于大文件粘贴场景。在此场景下，可通过此回调显示拷贝进度，或监听拷贝过程以便在必要时取消操作。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.READ_PASTEBOARD

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-SystemPasteboard-getDataWithProgress(params: GetDataParams): Promise<PasteData>--><!--Device-SystemPasteboard-getDataWithProgress(params: GetDataParams): Promise<PasteData>-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | GetDataParams | 是 | 应用在使用剪贴板提供的文件拷贝能力的情况下需要的参数，包含目标路径、文件冲突选项、进度条类型等。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[PasteData](arkts-basicservices-pasteboard-pastedata-i.md)&gt; | Promise对象，返回系统剪贴板数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [12900007](../../apis-basic-services-kit/errorcode-pasteboard.md#12900007-文件拷贝失败) | Invalid destUri or file system error. |
| [12900003](../../apis-basic-services-kit/errorcode-pasteboard.md#12900003-另外一个复制或粘贴正在进行) | Another copy or paste operation is in progress. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [12900008](../../apis-basic-services-kit/errorcode-pasteboard.md#12900008-启动进度条hap失败) | Failed to start progress. |
| [12900009](../../apis-basic-services-kit/errorcode-pasteboard.md#12900009-进度上报异常) | Progress exits abnormally. |
| [12900010](../../apis-basic-services-kit/errorcode-pasteboard.md#12900010-获取粘贴数据失败) | System error occurred during paste execution. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError, pasteboard } from '@kit.BasicServicesKit';
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
              let progressListenerInfo = (progress: pasteboard.ProgressInfo) => {
                console.info('progressListener success, progress:' + progress.progress);
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

ArkTS-Sta示例：

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
              let ProgressListener = (progress: pasteboard.ProgressInfo) => {
                console.info('progressListener success, progress:' + progress.progress);
              }
              let params: pasteboard.GetDataParams = {
                destUri: '/data/storage/el2/base/haps/entry/files/dstFile.txt',
                fileConflictOptions: pasteboard.FileConflictOptions.OVERWRITE,
                progressIndicator: pasteboard.ProgressIndicator.DEFAULT,
                progressListener: ProgressListener
              };
              systemPasteboard.getDataWithProgress(params).then((pasteData: pasteboard.PasteData) => {
                console.info('getDataWithProgress success');
              }).catch((err: BusinessError): void => {
                console.error('Failed to get PasteData. Cause: ' + err.message);
              })
          })
        }
      }
    }
  }
}
```

## getMimeTypes

```TypeScript
getMimeTypes(): Promise<Array<string>>
```

读取剪贴板中存在的MIME类型，使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-SystemPasteboard-getMimeTypes(): Promise<Array<string>>--><!--Device-SystemPasteboard-getMimeTypes(): Promise<Array<string>>-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise对象，返回读取到的MIME类型。 |

## 示例

```TypeScript
import { pasteboard, BusinessError } from '@kit.BasicServicesKit'

const systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
systemPasteboard.getMimeTypes().then((data: Array<string>) => {
    console.info('Succeeded in getting mimeTypes. mimeTypes: ' + data.sort().join(','));
}).catch((err: BusinessError) => {
    console.error('Failed to get mimeTypes. Cause:' + err.message);
});
```

## getPasteData

```TypeScript
getPasteData(callback: AsyncCallback<PasteData>): void
```

读取系统剪贴板内容，使用callback异步回调。

**起始版本：** 6

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为6。

**废弃版本：** 9

**替代接口：** [getData](#getData)(callback: AsyncCallback&lt;PasteData&gt;)

<!--Device-SystemPasteboard-getPasteData(callback: AsyncCallback<PasteData>): void--><!--Device-SystemPasteboard-getPasteData(callback: AsyncCallback<PasteData>): void-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-asynccallback-t.md)&lt;[PasteData](arkts-basicservices-pasteboard-pastedata-i.md)&gt; | 是 | 回调函数。当读取成功，err为undefined，data为返回的系统剪贴板数据；否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
systemPasteboard.getPasteData((err: BusinessError, pasteData: pasteboard.PasteData) => {
    if (err) {
        console.error('Failed to get PasteData. Cause: ' + err.message);
        return;
    }
    let text: string = pasteData.getPrimaryText();
});
```

## getPasteData

```TypeScript
getPasteData(): Promise<PasteData>
```

读取系统剪贴板内容，使用Promise异步回调。

**起始版本：** 6

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为6。

**废弃版本：** 9

**替代接口：** [getData](#getData)()

<!--Device-SystemPasteboard-getPasteData(): Promise<PasteData>--><!--Device-SystemPasteboard-getPasteData(): Promise<PasteData>-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[PasteData](arkts-basicservices-pasteboard-pastedata-i.md)&gt; | Promise对象，返回系统剪贴板数据。 |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
systemPasteboard.getPasteData().then((pasteData: pasteboard.PasteData) => {
    let text: string = pasteData.getPrimaryText();
}).catch((err: BusinessError) => {
    console.error('Failed to get PasteData. Cause: ' + err.message);
});
```

## getUnifiedData

```TypeScript
getUnifiedData(): Promise<unifiedDataChannel.UnifiedData>
```

读取系统剪贴板内容，使用Promise异步回调。 适用于需要使用标准化数据结构[UnifiedData](../../apis-arkdata/arkts-apis/arkts-arkdata-unifieddatachannel-unifieddata-c.md#UnifiedData)进行跨应用数据交换的场景。 当应用需要与其他支持UnifiedData的应用进行数据共享，或需要处理复杂的多类型数据时，使用本接口。 与[getData](#getData)相比，getUnifiedData提供了更标准化的数据格式。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.READ_PASTEBOARD

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-SystemPasteboard-getUnifiedData(): Promise<unifiedDataChannel.UnifiedData>--><!--Device-SystemPasteboard-getUnifiedData(): Promise<unifiedDataChannel.UnifiedData>-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;unifiedDataChannel.UnifiedData&gt; | Promise对象，返回系统剪贴板数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [27787277](../../apis-basic-services-kit/errorcode-pasteboard.md#27787277-另外一个复制或粘贴正在进行) | Another copy or paste operation is in progress. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { unifiedDataChannel, uniformDataStruct, uniformTypeDescriptor } from '@kit.ArkData';

const systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
systemPasteboard.getUnifiedData().then((data) => {
    let records: Array<unifiedDataChannel.UnifiedRecord> = data.getRecords();
    for (let j = 0; j < records.length; j++) {
        if (records[j].getType() === uniformTypeDescriptor.UniformDataType.PLAIN_TEXT) {
            let text = records[j].getValue() as uniformDataStruct.PlainText;
            console.info(`${j + 1}.${text.textContent}`);
        }
    }
}).catch((err: BusinessError) => {
    console.error('Failed to get UnifiedData. Cause: ' + err.message);
});
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { unifiedDataChannel, uniformDataStruct, uniformTypeDescriptor } from '@kit.ArkData';

let systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
systemPasteboard.getUnifiedData().then((data) => {
  let records: Array<unifiedDataChannel.UnifiedRecord> = data.getRecords();
  for (let j = 0; j < records.length; j++) {
    if (records[j].getType() === uniformTypeDescriptor.UniformDataType.PLAIN_TEXT.toString()) {
      let text = records[j].getValue() as uniformDataStruct.PlainText;
      console.info(`${j + 1}.${text.textContent}`);
    }
  }
}).catch((err: BusinessError): void => {
  console.error('Failed to get UnifiedData. Cause: ' + err.message);
});
```

## getUnifiedDataSync

```TypeScript
getUnifiedDataSync(): unifiedDataChannel.UnifiedData
```

读取系统剪贴板内容，此接口为同步接口。适用于需要同步使用标准化数据结构UnifiedData进行跨应用数据交换的场景。 当应用需要在关键业务流程中立即获取剪贴板数据，且需要与其他支持UnifiedData的应用进行数据共享时使用。 由于获取剪贴板中数据的时延受数据量大小与网络环境的影响，调用此接口可能耗时较长，建议开发者在非UI线程调用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.READ_PASTEBOARD

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-SystemPasteboard-getUnifiedDataSync(): unifiedDataChannel.UnifiedData--><!--Device-SystemPasteboard-getUnifiedDataSync(): unifiedDataChannel.UnifiedData-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

**返回值：**

| 类型 | 说明 |
| --- | --- |
| unifiedDataChannel.UnifiedData | 返回系统剪贴板数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12900005](../../apis-basic-services-kit/errorcode-pasteboard.md#12900005-请求超时) | Excessive processing time for internal data. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |

## 示例

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';

const systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
try {
    let result: unifiedDataChannel.UnifiedData = systemPasteboard.getUnifiedDataSync();
    console.info('Succeeded in getting UnifiedData.');
} catch (err) {
    console.error('Failed to get UnifiedData. Cause:' + err.message);
};
```

## hasData

```TypeScript
hasData(callback: AsyncCallback<boolean>): void
```

判断系统剪贴板中是否有内容，使用callback异步回调。适用于需要异步判断剪贴板是否有内容且不阻塞主线程的场景，如UI响应优先的交互流程。 与同步接口[hasDataSync](#hasDataSync)不同，此接口不会阻塞UI线程，更适合在UI交互中调用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SystemPasteboard-hasData(callback: AsyncCallback<boolean>): void--><!--Device-SystemPasteboard-hasData(callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-asynccallback-t.md)&lt;boolean&gt; | 是 | 回调函数，用于接收剪贴板是否有内容的判断结果。返回true表示系统剪贴板中有内容，返回false表示系统剪贴板中没有内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
systemPasteboard.hasData((err: BusinessError, data: boolean) => {
    if (err) {
        console.error(`Failed to check the PasteData. Cause: ${err.message}`);
        return;
    }
    console.info(`Succeeded in checking the PasteData. Data: ${data}`);
});
```

## hasData

```TypeScript
hasData(): Promise<boolean>
```

判断系统剪贴板中是否有内容，使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SystemPasteboard-hasData(): Promise<boolean>--><!--Device-SystemPasteboard-hasData(): Promise<boolean>-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | 返回true表示系统剪贴板中有内容，返回false表示系统剪贴板中没有内容。 |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
systemPasteboard.hasData().then((data: boolean) => {
    console.info(`Succeeded in checking the PasteData. Data: ${data}`);
}).catch((err: BusinessError) => {
    console.error(`Failed to check the PasteData. Cause: ${err.message}`);
});
```

## hasDataSync

```TypeScript
hasDataSync(): boolean
```

判断系统剪贴板中是否有内容，此接口为同步接口。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-SystemPasteboard-hasDataSync(): boolean--><!--Device-SystemPasteboard-hasDataSync(): boolean-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示系统剪贴板中有内容，返回false表示系统剪贴板中没有内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12900005](../../apis-basic-services-kit/errorcode-pasteboard.md#12900005-请求超时) | Excessive processing time for internal data. |

## 示例

```TypeScript
const systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
try {
    let result: boolean = systemPasteboard.hasDataSync();
    console.info(`Succeeded in checking the PasteData. Result: ${result}`);
} catch (err) {
    console.error('Failed to check the PasteData. Cause:' + err.message);
};
```

## hasDataType

```TypeScript
hasDataType(mimeType: string): boolean
```

检查剪贴板内容中是否有指定类型的数据。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-SystemPasteboard-hasDataType(mimeType: string): boolean--><!--Device-SystemPasteboard-hasDataType(mimeType: string): boolean-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mimeType | string | 是 | 数据类型，设置后用于检查剪贴板内容中是否存在该类型的特定数据。其长度不能超过1024字节，超出范围时返回错误码401。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查剪贴板内容中是否有指定类型的数据。剪贴板内容中有指定类型的数据返回true；剪贴板内容中没有指定类型的数据返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| [12900005](../../apis-basic-services-kit/errorcode-pasteboard.md#12900005-请求超时) | Excessive processing time for internal data. |

## 示例

```TypeScript
const systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
try {
    let result: boolean = systemPasteboard.hasDataType(pasteboard.MIMETYPE_TEXT_PLAIN);
    console.info(`Succeeded in checking the DataType. Result: ${result}`);
} catch (err) {
    console.error('Failed to check the DataType. Cause:' + err.message);
};
```

## hasPasteData

```TypeScript
hasPasteData(callback: AsyncCallback<boolean>): void
```

判断系统剪贴板中是否有内容，使用callback异步回调。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [hasData](#hasData)(callback: AsyncCallback&lt;boolean&gt;)

<!--Device-SystemPasteboard-hasPasteData(callback: AsyncCallback<boolean>): void--><!--Device-SystemPasteboard-hasPasteData(callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-asynccallback-t.md)&lt;boolean&gt; | 是 | 返回true表示系统剪贴板中有内容，返回false表示系统剪贴板中没有内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
systemPasteboard.hasPasteData((err: BusinessError, data: boolean) => {
    if (err) {
        console.error(`Failed to check the PasteData. Cause: ${err.message}`);
        return;
    }
    console.info(`Succeeded in checking the PasteData. Data: ${data}`);
});
```

## hasPasteData

```TypeScript
hasPasteData(): Promise<boolean>
```

判断系统剪贴板中是否有内容，使用Promise异步回调。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [hasData](#hasData)()

<!--Device-SystemPasteboard-hasPasteData(): Promise<boolean>--><!--Device-SystemPasteboard-hasPasteData(): Promise<boolean>-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | 返回true表示系统剪贴板中有内容，返回false表示系统剪贴板中没有内容。 |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
systemPasteboard.hasPasteData().then((data: boolean) => {
    console.info(`Succeeded in checking the PasteData. Data: ${data}`);
}).catch((err: BusinessError) => {
    console.error(`Failed to check the PasteData. Cause: ${err.message}`);
});
```

## hasRemoteData

```TypeScript
hasRemoteData(): boolean
```

判断剪贴板数据是否在远端设备上。由于数据跨端传输耗时较大，如果剪贴板数据在远端设备上，不建议在UI线程执行检查剪贴板数据中是否包含自定义数据类型，或读取剪贴板数据。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-SystemPasteboard-hasRemoteData(): boolean--><!--Device-SystemPasteboard-hasRemoteData(): boolean-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回指示剪贴板数据是否在远端设备上的结果。true表示剪贴板数据在远端设备上；false表示剪贴板数据不在远端设备上。默认为false。 |

## 示例

```TypeScript
const systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();

let result: boolean = systemPasteboard.hasRemoteData();
console.info(`Succeeded in checking the remote data. Result: ${result}`);
```

## isRemoteData

```TypeScript
isRemoteData(): boolean
```

判断剪贴板中的数据是否来自其他设备。由于数据跨端传输耗时较大，如果剪贴板数据在远端设备上，不建议在UI线程执行检查剪贴板数据中是否包含自定义数据类型，或读取剪贴板数据。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-SystemPasteboard-isRemoteData(): boolean--><!--Device-SystemPasteboard-isRemoteData(): boolean-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 判断剪贴板中的数据是否来自其他设备。剪贴板数据来自其他设备返回true；剪贴板数据来自本设备返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12900005](../../apis-basic-services-kit/errorcode-pasteboard.md#12900005-请求超时) | Excessive processing time for internal data. |

## 示例

ArkTS-Dyn示例：

```TypeScript
const systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
try {
    let result: boolean = systemPasteboard.isRemoteData();
    console.info(`Succeeded in checking the RemoteData. Result: ${result}`);
} catch (err) {
    console.error('Failed to check the RemoteData. Cause:' + err.message);
};
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
let systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
try {
    let result: boolean = systemPasteboard.isRemoteData();
    console.info(`Succeeded in checking the RemoteData. Result: ${result}`);
} catch (err: BusinessError ) {
    console.error('Failed to check the RemoteData. Cause:' + err.message);
};
```

## offRemoteUpdate

```TypeScript
offRemoteUpdate(callback?: UpdateCallback): void
```

取消订阅跨设备剪贴板内容变化事件。 - 与onRemoteUpdate()方法配合使用，取消订阅的是通过onRemoteUpdate()订阅的事件监听。 - 必须在已订阅的情况下才能调用。 - 如果callback参数未填，清除本应用的所有远端监听回调；否则清除指定远端监听回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-SystemPasteboard-offRemoteUpdate(callback?: UpdateCallback): void--><!--Device-SystemPasteboard-offRemoteUpdate(callback?: UpdateCallback): void-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [UpdateCallback](arkts-basicservices-pasteboard-updatecallback-t.md) | 否 | 远端设备剪贴板中内容变化时触发的用户程序的回调。如果此参数未填，表明清除本应用的所有远端监听回调，否则表示清除指定远端监听回调。 |

## 示例

```TypeScript
const systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
let listener = () => {
    console.info('The remote pasteboard has changed.');
};
systemPasteboard.offRemoteUpdate(listener);
```

## offUpdate

```TypeScript
offUpdate(callback?: UpdateCallback): void
```

取消订阅系统剪贴板内容变化事件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-SystemPasteboard-offUpdate(callback?: UpdateCallback): void--><!--Device-SystemPasteboard-offUpdate(callback?: UpdateCallback): void-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [UpdateCallback](arkts-basicservices-pasteboard-updatecallback-t.md) | 否 | 剪贴板中内容变化时触发的用户程序的回调。如果此参数未填，表明清除本应用的所有监听回调，否则表示清除指定监听回调。 |

## 示例

```TypeScript
let systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
let listener = () => {
    console.info('The system pasteboard has changed.');
};
systemPasteboard.offUpdate(listener);
```

## off_update

```TypeScript
off(type: 'update', callback?: () => void): void
```

取消订阅系统剪贴板内容变化事件。 - 与on('update')方法配合使用，取消订阅的是通过on('update')订阅的事件监听。 - 必须在已订阅的情况下才能调用。 - 如果callback参数未填，清除本应用的所有监听回调；否则清除指定监听回调。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

<!--Device-SystemPasteboard-off(type: 'update', callback?: () => void): void--><!--Device-SystemPasteboard-off(type: 'update', callback?: () => void): void-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'update' | 是 | 取值为'update'，表示系统剪贴板内容变化事件。 |
| callback | () =&gt; void | 否 | 剪贴板中内容变化时触发的用户程序的回调。如果此参数未填，表明清除本应用的所有监听回调，否则表示清除指定监听回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |

## 示例

```TypeScript
const systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
let listener = () => {
    console.info('The system pasteboard has changed.');
};
systemPasteboard.off('update', listener);
```

## onRemoteUpdate

```TypeScript
onRemoteUpdate(callback: UpdateCallback): void
```

订阅跨设备剪贴板内容变化事件，当远端设备系统剪贴板中内容变化时触发用户程序的回调。 - 订阅后必须在不再需要监听时调用 [offRemoteUpdate](#offRemoteUpdate) 取消订阅。 - 未取消订阅会导致回调函数持续监听远端变化，造成内存泄漏。 - 建议在组件/页面销毁时取消订阅。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-SystemPasteboard-onRemoteUpdate(callback: UpdateCallback): void--><!--Device-SystemPasteboard-onRemoteUpdate(callback: UpdateCallback): void-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [UpdateCallback](arkts-basicservices-pasteboard-updatecallback-t.md) | 是 | 剪贴板中内容变化时触发的用户程序的回调，无参数。用于监听跨设备剪贴板内容更新事件，当远端设备剪贴板内容发生变化时触发此回调。 |

## 示例

```TypeScript
const systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
let listener = () => {
    console.info('The remote pasteboard has changed.');
};
systemPasteboard.onRemoteUpdate(listener);
```

## onUpdate

```TypeScript
onUpdate(callback: UpdateCallback): void
```

订阅系统剪贴板内容变化事件，当系统剪贴板中内容变化时触发用户程序的回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-SystemPasteboard-onUpdate(callback: UpdateCallback): void--><!--Device-SystemPasteboard-onUpdate(callback: UpdateCallback): void-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [UpdateCallback](arkts-basicservices-pasteboard-updatecallback-t.md) | 是 | 剪贴板中内容变化时触发的用户程序的回调。 |

## 示例

```TypeScript
let systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
let listener = () => {
    console.info('The system pasteboard has changed.');
};
systemPasteboard.onUpdate(listener);
```

## on_update

```TypeScript
on(type: 'update', callback: () => void): void
```

订阅系统剪贴板内容变化事件，当系统剪贴板中内容变化时触发用户程序的回调。调用此方法后，系统将在剪贴板服务中注册监听器，剪贴板内容被写入、清空或修改时触发回调。 可注册多个监听器，需在适当时机调用off取消监听以释放资源。当应用需要实时响应剪贴板内容变化时使用，如自动检测剪贴板中的特定格式数据、实现智能粘贴建议等场景。 - 订阅后必须在不再需要监听时调用off('update')取消订阅。 - 未取消订阅会导致回调函数持续监听剪贴板变化，可能造成内存泄漏或多次回调触发。 - 建议在组件/页面销毁时取消订阅。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

<!--Device-SystemPasteboard-on(type: 'update', callback: () => void): void--><!--Device-SystemPasteboard-on(type: 'update', callback: () => void): void-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'update' | 是 | 取值为'update'，表示系统剪贴板内容变化事件，其他值无效。 |
| callback | () =&gt; void | 是 | 剪贴板中内容变化时触发的用户程序的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |

## 示例

```TypeScript
const systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
let listener = () => {
    console.info('The system pasteboard has changed.');
};
systemPasteboard.on('update', listener);
```

## setData

```TypeScript
setData(data: PasteData, callback: AsyncCallback<void>): void
```

将数据写入系统剪贴板，使用callback异步回调。调用此方法后，系统会将PasteData对象写入到系统剪贴板中。写入成功后，其他应用可以读取该剪贴板数据。 写入的数据会替换剪贴板中已有的内容。适用于需要异步写入剪贴板内容的场景，如UI响应优先、避免阻塞主线程。 与[setDataSync](#setDataSync)相比，setData不会阻塞UI线程。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SystemPasteboard-setData(data: PasteData, callback: AsyncCallback<void>): void--><!--Device-SystemPasteboard-setData(data: PasteData, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | [PasteData](arkts-basicservices-pasteboard-pastedata-i.md) | 是 | PasteData对象，设置后会将该数据写入系统剪贴板，供应用读取和粘贴使用。 |
| callback | [AsyncCallback](arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当写入成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| [27787277](../../apis-basic-services-kit/errorcode-pasteboard.md#27787277-另外一个复制或粘贴正在进行) | Another copy or paste operation is in progress. |
| [27787278](../../apis-basic-services-kit/errorcode-pasteboard.md#27787278-禁止复制) | Replication is prohibited. |

## 示例

```TypeScript
let pasteData: pasteboard.PasteData = pasteboard.createData(pasteboard.MIMETYPE_TEXT_PLAIN, 'content');
const systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
systemPasteboard.setData(pasteData, (err, data) => {
    if (err) {
        console.error('Failed to set PasteData. Cause: ' + err.message);
        return;
    }
    console.info('Succeeded in setting PasteData.');
});
```

## setData

```TypeScript
setData(data: PasteData): Promise<void>
```

将数据写入系统剪贴板，使用Promise异步回调。适用于需要异步写入剪贴板且不阻塞主线程的场景，如UI响应优先的交互流程。 与同步接口[setDataSync](#setDataSync)不同，此接口不会阻塞UI线程，更适合在UI交互中调用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SystemPasteboard-setData(data: PasteData): Promise<void>--><!--Device-SystemPasteboard-setData(data: PasteData): Promise<void>-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | [PasteData](arkts-basicservices-pasteboard-pastedata-i.md) | 是 | PasteData对象。调用本接口前，需确保无其他拷贝或粘贴操作正在进行。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| [27787277](../../apis-basic-services-kit/errorcode-pasteboard.md#27787277-另外一个复制或粘贴正在进行) | Another copy or paste operation is in progress. |
| [27787278](../../apis-basic-services-kit/errorcode-pasteboard.md#27787278-禁止复制) | Replication is prohibited. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let pasteData: pasteboard.PasteData = pasteboard.createData(pasteboard.MIMETYPE_TEXT_PLAIN, 'content');
const systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
systemPasteboard.setData(pasteData).then((data: void) => {
    console.info('Succeeded in setting PasteData.');
}).catch((err: BusinessError) => {
    console.error('Failed to set PasteData. Cause: ' + err.message);
});
```

## setDataSync

```TypeScript
setDataSync(data: PasteData): void
```

将数据写入系统剪贴板，此接口为同步接口。适用于应用需要在关键业务流程中同步完成剪贴板数据写入，或需要立即确认写入结果的场景。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-SystemPasteboard-setDataSync(data: PasteData): void--><!--Device-SystemPasteboard-setDataSync(data: PasteData): void-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | [PasteData](arkts-basicservices-pasteboard-pastedata-i.md) | 是 | 需要写入剪贴板中的数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| [12900005](../../apis-basic-services-kit/errorcode-pasteboard.md#12900005-请求超时) | Excessive processing time for internal data. |

## 示例

ArkTS-Dyn示例：

```TypeScript
let pasteData: pasteboard.PasteData = pasteboard.createData(pasteboard.MIMETYPE_TEXT_PLAIN, 'hello');
const systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
try {
    systemPasteboard.setDataSync(pasteData);
    console.info('Succeeded in setting PasteData.');
} catch (err) {
    console.error('Failed to set PasteData. Cause:' + err.message);
};
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
let pasteData: pasteboard.PasteData = pasteboard.createData(pasteboard.MIMETYPE_TEXT_PLAIN, 'hello');
let systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
try {
    systemPasteboard.setDataSync(pasteData);
    console.info('Succeeded in setting PasteData.');
} catch (err: BusinessError) {
    console.error('Failed to set PasteData. Cause:' + err.message);
};
```

## setPasteData

```TypeScript
setPasteData(data: PasteData, callback: AsyncCallback<void>): void
```

将数据写入系统剪贴板，使用callback异步回调。

**起始版本：** 6

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为6。

**废弃版本：** 9

**替代接口：** [setData](#setData)(data: PasteData, callback: AsyncCallback&lt;void&gt;)

<!--Device-SystemPasteboard-setPasteData(data: PasteData, callback: AsyncCallback<void>): void--><!--Device-SystemPasteboard-setPasteData(data: PasteData, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | [PasteData](arkts-basicservices-pasteboard-pastedata-i.md) | 是 | PasteData对象。 |
| callback | [AsyncCallback](arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当写入成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |

## 示例

```TypeScript
let pasteData: pasteboard.PasteData = pasteboard.createPlainTextData('content');
const systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
systemPasteboard.setPasteData(pasteData, (err, data) => {
    if (err) {
        console.error('Failed to set PasteData. Cause: ' + err.message);
        return;
    }
    console.info('Succeeded in setting PasteData.');
});
```

## setPasteData

```TypeScript
setPasteData(data: PasteData): Promise<void>
```

将数据写入系统剪贴板，使用Promise异步回调。

**起始版本：** 6

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为6。

**废弃版本：** 9

**替代接口：** [setData](#setData)(data: PasteData)

<!--Device-SystemPasteboard-setPasteData(data: PasteData): Promise<void>--><!--Device-SystemPasteboard-setPasteData(data: PasteData): Promise<void>-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | [PasteData](arkts-basicservices-pasteboard-pastedata-i.md) | 是 | PasteData对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let pasteData: pasteboard.PasteData = pasteboard.createPlainTextData('content');
const systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
systemPasteboard.setPasteData(pasteData).then((data: void) => {
    console.info('Succeeded in setting PasteData.');
}).catch((err: BusinessError) => {
    console.error('Failed to set PasteData. Cause: ' + err.message);
});
```

## setUnifiedData

```TypeScript
setUnifiedData(data: unifiedDataChannel.UnifiedData): Promise<void>
```

将数据写入系统剪贴板，使用Promise异步回调。适用于需要异步写入剪贴板且不阻塞主线程的场景，如UI响应优先的交互流程。 与同步接口[setUnifiedDataSync](#setUnifiedDataSync)不同，此接口不会阻塞UI线程，更适合在UI交互中调用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-SystemPasteboard-setUnifiedData(data: unifiedDataChannel.UnifiedData): Promise<void>--><!--Device-SystemPasteboard-setUnifiedData(data: unifiedDataChannel.UnifiedData): Promise<void>-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | unifiedDataChannel.UnifiedData | 是 | 需要写入剪贴板中的数据。调用本接口前，需确保无其他拷贝或粘贴操作正在进行。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| [27787277](../../apis-basic-services-kit/errorcode-pasteboard.md#27787277-另外一个复制或粘贴正在进行) | Another copy or paste operation is in progress. |
| [27787278](../../apis-basic-services-kit/errorcode-pasteboard.md#27787278-禁止复制) | Replication is prohibited. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { unifiedDataChannel, uniformDataStruct, uniformTypeDescriptor } from '@kit.ArkData';

let plainText : uniformDataStruct.PlainText = {
    uniformDataType: uniformTypeDescriptor.UniformDataType.PLAIN_TEXT,
    textContent : 'PLAINTEXT_CONTENT',
    abstract : 'PLAINTEXT_ABSTRACT',
}
let record = new unifiedDataChannel.UnifiedRecord(uniformTypeDescriptor.UniformDataType.PLAIN_TEXT, plainText);
let data = new unifiedDataChannel.UnifiedData();
data.addRecord(record);

const systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
systemPasteboard.setUnifiedData(data).then((data: void) => {
    console.info('Succeeded in setting UnifiedData.');
}).catch((err: BusinessError) => {
    console.error('Failed to setUnifiedData. Cause: ' + err.message);
});
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { unifiedDataChannel, uniformDataStruct, uniformTypeDescriptor } from '@kit.ArkData';

let plainText : uniformDataStruct.PlainText = {
  uniformDataType: uniformTypeDescriptor.UniformDataType.PLAIN_TEXT,
  textContent : 'PLAINTEXT_CONTENT',
}
let record = new unifiedDataChannel.UnifiedRecord(uniformTypeDescriptor.UniformDataType.PLAIN_TEXT, plainText);
let data = new unifiedDataChannel.UnifiedData();
data.addRecord(record);

const systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
systemPasteboard.setUnifiedData(data).then(() => {
  console.info('Succeeded in setting UnifiedData.');
}).catch((err: BusinessError): void => {
  console.error('Failed to setUnifiedData. Cause: ' + err.message);
});
```

## setUnifiedDataSync

```TypeScript
setUnifiedDataSync(data: unifiedDataChannel.UnifiedData): void
```

将数据写入系统剪贴板，此接口为同步接口。适用于需要同步使用标准化数据结构UnifiedData进行跨应用数据交换的场景。当应用需要在关键业务流程中立即写入剪贴板数据， 且需要与其他支持[UnifiedData](../../apis-arkdata/arkts-apis/arkts-arkdata-unifieddatachannel-unifieddata-c.md#UnifiedData)的应用进行数据共享时使用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-SystemPasteboard-setUnifiedDataSync(data: unifiedDataChannel.UnifiedData): void--><!--Device-SystemPasteboard-setUnifiedDataSync(data: unifiedDataChannel.UnifiedData): void-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | unifiedDataChannel.UnifiedData | 是 | 需要写入剪贴板中的数据内容。支持跨应用数据交换，其他应用可通过统一数据结构读取该内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| [12900005](../../apis-basic-services-kit/errorcode-pasteboard.md#12900005-请求超时) | Excessive processing time for internal data. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';

let plainTextData = new unifiedDataChannel.UnifiedData();
let plainText = new unifiedDataChannel.PlainText();
plainText.details = {
    Key: 'delayPlaintext',
    Value: 'delayPlaintext',
};
plainText.textContent = 'delayTextContent';
plainText.abstract = 'delayTextContent';
plainTextData.addRecord(plainText);

const systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
try {
    systemPasteboard.setUnifiedDataSync(plainTextData);
    console.info('Succeeded in setting UnifiedData.');
} catch (err) {
    console.error('Failed to set UnifiedData. Cause:' + err.message);
};
```

ArkTS-Sta示例：

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

let plainTextData = new unifiedDataChannel.UnifiedData();
let plainText = new unifiedDataChannel.PlainText();

plainText.textContent = 'delayTextContent';
plainTextData.addRecord(plainText);

const systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
try {
  systemPasteboard.setUnifiedDataSync(plainTextData);
  console.info('Succeeded in setting UnifiedData.');
} catch (err: BusinessError) {
  console.error('Failed to set UnifiedData. Cause:' + err.message);
};
```

