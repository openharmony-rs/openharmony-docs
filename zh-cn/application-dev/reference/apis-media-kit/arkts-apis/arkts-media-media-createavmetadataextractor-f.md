# createAVMetadataExtractor

## createAVMetadataExtractor

```TypeScript
function createAVMetadataExtractor(): Promise<AVMetadataExtractor>
```

创建AVMetadataExtractor实例。使用Promise异步回调。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

<!--Device-media-function createAVMetadataExtractor(): Promise<AVMetadataExtractor>--><!--Device-media-function createAVMetadataExtractor(): Promise<AVMetadataExtractor>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;AVMetadataExtractor&gt; | Promise对象。异步返回元数据获取类对象（AVMetadataExtractor）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400101](../errorcode-media.md#5400101-内存分配失败) | No memory. Returned by promise. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let avMetadataExtractor: media.AVMetadataExtractor;
media.createAVMetadataExtractor().then((extractor: media.AVMetadataExtractor) => {
  if (extractor) {
    avMetadataExtractor = extractor;
    console.info('Succeeded in creating AVMetadataExtractor');
  } else {
    console.error(`Failed to create AVMetadataExtractor`);
  }
}).catch((error: BusinessError) => {
  console.error(`Failed to create AVMetadataExtractor, error message:${error.message}`);
});
```


## createAVMetadataExtractor

```TypeScript
function createAVMetadataExtractor(): Promise<AVMetadataExtractor | undefined>
```

Creates an **AVMetadataExtractor** instance. This API uses a promise to return the result.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-media-function createAVMetadataExtractor(): Promise<AVMetadataExtractor | undefined>--><!--Device-media-function createAVMetadataExtractor(): Promise<AVMetadataExtractor | undefined>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;AVMetadataExtractor \| undefined&gt; | A Promise instance used to return AVMetadataExtractor |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400101](../errorcode-media.md#5400101-内存分配失败) | No memory. Returned by promise. |


## createAVMetadataExtractor

```TypeScript
function createAVMetadataExtractor(callback: AsyncCallback<AVMetadataExtractor>): void
```

创建AVMetadataExtractor实例。使用callback异步回调。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

<!--Device-media-function createAVMetadataExtractor(callback: AsyncCallback<AVMetadataExtractor>): void--><!--Device-media-function createAVMetadataExtractor(callback: AsyncCallback<AVMetadataExtractor>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;AVMetadataExtractor&gt; | 是 | 回调函数。当创建AVMetadataExtractor实例成功，err为undefined，data为获取到的AVMetadataExtractor实例，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400101](../errorcode-media.md#5400101-内存分配失败) | No memory. Returned by callback. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let avMetadataExtractor: media.AVMetadataExtractor;
media.createAVMetadataExtractor((error: BusinessError, extractor: media.AVMetadataExtractor) => {
  if (extractor) {
    avMetadataExtractor = extractor;
    console.info('Succeeded in creating AVMetadataExtractor');
  } else {
    console.error(`Failed to create AVMetadataExtractor, error message:${error.message}`);
  }
});
```


## createAVMetadataExtractor

```TypeScript
function createAVMetadataExtractor(callback: AsyncCallback<AVMetadataExtractor | undefined>): void
```

Creates an **AVMetadataExtractor** instance. This API uses an asynchronous callback to return the result.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-media-function createAVMetadataExtractor(callback: AsyncCallback<AVMetadataExtractor | undefined>): void--><!--Device-media-function createAVMetadataExtractor(callback: AsyncCallback<AVMetadataExtractor | undefined>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;AVMetadataExtractor \| undefined&gt; | 是 | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the **AVMetadataExtractor** instance created;otherwise, **err** is an error object. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400101](../errorcode-media.md#5400101-内存分配失败) | No memory. Returned by callback. |

