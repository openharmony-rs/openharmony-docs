# createAVMetadataExtractor

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

<a id="createavmetadataextractor"></a>
## createAVMetadataExtractor

```TypeScript
function createAVMetadataExtractor(): Promise<AVMetadataExtractor>
```

创建AVMetadataExtractor实例。使用Promise异步回调。

**起始版本：** 11

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


<a id="createavmetadataextractor-1"></a>
## createAVMetadataExtractor

```TypeScript
function createAVMetadataExtractor(callback: AsyncCallback<AVMetadataExtractor>): void
```

创建AVMetadataExtractor实例。使用callback异步回调。

**起始版本：** 11

<!--Device-media-function createAVMetadataExtractor(callback: AsyncCallback<AVMetadataExtractor>): void--><!--Device-media-function createAVMetadataExtractor(callback: AsyncCallback<AVMetadataExtractor>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;AVMetadataExtractor&gt; | 是 | 回调函数。当创建AVMetadataExtractor实例成功，err为undefined，data为获取到的AVMetadataExtractor实例，否则为错误对象。 |

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

