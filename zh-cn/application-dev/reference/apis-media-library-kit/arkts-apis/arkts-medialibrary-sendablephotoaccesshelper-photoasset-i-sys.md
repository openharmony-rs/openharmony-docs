# PhotoAsset

提供封装文件属性的方法。

**继承/实现关系：** PhotoAsset extends lang.ISendable

**起始版本：** 12

<!--Device-sendablePhotoAccessHelper-interface PhotoAsset--><!--Device-sendablePhotoAccessHelper-interface PhotoAsset-End-->

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

<!--Device-PhotoAsset-getAnalysisData(analysisType: photoAccessHelper.AnalysisType): Promise<string>--><!--Device-PhotoAsset-getAnalysisData(analysisType: photoAccessHelper.AnalysisType): Promise<string>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| analysisType | photoAccessHelper.AnalysisType | 是 | 需要获取的智慧分析类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回指定分析数据结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 14000011 | Internal system error |

## requestSource

```TypeScript
requestSource(): Promise<number>
```

打开源文件并返回fd（文件描述符）。使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAsset-requestSource(): Promise<number>--><!--Device-PhotoAsset-requestSource(): Promise<number>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回源文件fd。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| 14000011 | Internal system error |

**示例**

phAccessHelper的创建请参考[@ohos.file.sendablePhotoAccessHelper (基于Sendable对象的相册管理模块)](arkts-file-sendablephotoaccesshelper.md)的示例使用。

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

