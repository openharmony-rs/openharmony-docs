# PhotoAsset

```TypeScript
interface PhotoAsset extends lang.ISendable
```

提供封装文件属性的方法。

**继承/实现关系：** PhotoAsset extends [lang.ISendable](../../apis-arkts/arkts-apis/arkts-arkts-lang-isendable-i.md)

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { sendablePhotoAccessHelper } from '@kit.MediaLibraryKit';
```

## getAnalysisData

```TypeScript
getAnalysisData(analysisType: photoAccessHelper.AnalysisType): Promise<string>
```

根据智慧分析类型获取指定分析结果数据。使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.READ_IMAGEVIDEO

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| analysisType | [photoAccessHelper.AnalysisType](arkts-medialibrary-photoaccesshelper-analysistype-e-sys.md) | 是 | 需要获取的智慧分析类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回指定分析数据结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | Internal system error |

**示例**

phAccessHelper的创建请参考[@ohos.file.sendablePhotoAccessHelper (基于Sendable对象的相册管理模块)](arkts-medialibrary-file-sendablephotoaccesshelper.md)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { common } from '@kit.AbilityKit';

async function example(phAccessHelper: sendablePhotoAccessHelper.PhotoAccessHelper) {
  try {
    console.info('getAnalysisDataDemo')
    let fetchOptions: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: new dataSharePredicates.DataSharePredicates()
    }
    let fetchResult: sendablePhotoAccessHelper.FetchResult<sendablePhotoAccessHelper.PhotoAsset> =
      await phAccessHelper.getAssets(fetchOptions);
    let photoAsset: sendablePhotoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    if (photoAsset != undefined) {
      let analysisData: string = await photoAsset.getAnalysisData(
        photoAccessHelper.AnalysisType.ANALYSIS_OCR);
      console.info('get ocr result: ' + JSON.stringify(analysisData));
    }
    fetchResult.close();
  } catch (err) {
    console.error(`getAnalysisDataDemofailed with error: ${err.code}, ${err.message}`);
  }
}
```

## requestSource

```TypeScript
requestSource(): Promise<number>
```

打开源文件并返回fd（文件描述符）。使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.READ_IMAGEVIDEO

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回源文件fd。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| 14000011 | Internal system error |

**示例**

phAccessHelper的创建请参考[@ohos.file.sendablePhotoAccessHelper (基于Sendable对象的相册管理模块)](arkts-medialibrary-file-sendablephotoaccesshelper.md)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { common } from '@kit.AbilityKit';

async function example(phAccessHelper: sendablePhotoAccessHelper.PhotoAccessHelper) {
  try {
    console.info('requestSourcePromiseDemo')
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOptions: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let fetchResult: sendablePhotoAccessHelper.FetchResult<sendablePhotoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOptions);
    if (fetchResult === undefined) {
      console.error('requestSourcePromise fetchResult is undefined');
      return;
    }
    let photoAsset: sendablePhotoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    let fd = await photoAsset.requestSource();
    console.info('Source fd is ' + fd);
  } catch (err) {
    console.error(`requestSourcePromiseDemo failed with error: ${err.code}, ${err.message}`);
  }
}
```
