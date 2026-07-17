# createAVImageGenerator

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## createAVImageGenerator

```TypeScript
function createAVImageGenerator(): Promise<AVImageGenerator>
```

创建AVImageGenerator对象。使用Promise异步回调。

**起始版本：** 12

<!--Device-media-function createAVImageGenerator(): Promise<AVImageGenerator>--><!--Device-media-function createAVImageGenerator(): Promise<AVImageGenerator>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVImageGenerator

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<AVImageGenerator> | Promise对象。异步返回AVImageGenerator实例，失败时返回null。可用于获取视频缩略图。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400101](../errorcode-media.md#5400101-内存分配失败) | No memory. Returned by promise. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let avImageGenerator: media.AVImageGenerator;
media.createAVImageGenerator().then((generator: media.AVImageGenerator) => {
  if (generator) {
    avImageGenerator = generator;
    console.info('Succeeded in creating AVImageGenerator');
  } else {
    console.error('Failed to create AVImageGenerator');
  }
}).catch((error: BusinessError) => {
  console.error(`Failed to create AVImageGenerator, error message:${error.message}`);
});

```


## createAVImageGenerator

```TypeScript
function createAVImageGenerator(callback: AsyncCallback<AVImageGenerator>): void
```

创建AVImageGenerator实例。使用callback异步回调。

**起始版本：** 12

<!--Device-media-function createAVImageGenerator(callback: AsyncCallback<AVImageGenerator>): void--><!--Device-media-function createAVImageGenerator(callback: AsyncCallback<AVImageGenerator>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVImageGenerator

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<AVImageGenerator> | 是 | 回调函数。异步返回AVImageGenerator实例，失败时返回null。可用于获取视频缩略图。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400101](../errorcode-media.md#5400101-内存分配失败) | No memory. Returned by callback. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let avImageGenerator: media.AVImageGenerator;
media.createAVImageGenerator((error: BusinessError, generator: media.AVImageGenerator) => {
  if (generator) {
    avImageGenerator = generator;
    console.info('Succeeded in creating AVImageGenerator');
  } else {
    console.error(`Failed to create AVImageGenerator, error message:${error.message}`);
  }
});

```

