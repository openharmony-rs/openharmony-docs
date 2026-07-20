# decomposeToPicture（系统接口）

## 导入模块

```TypeScript
import { image } from '@kit.ImageKit';
```

<a id="decomposetopicture"></a>
## decomposeToPicture

```TypeScript
function decomposeToPicture(hdrPixelMap : PixelMap, options?: HdrDecomposeOptions): Promise<Picture | undefined>
```

将HDR PixelMap分解为包含SDR PixelMap和增益图（gainmap）的Picture对象。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-image-function decomposeToPicture(hdrPixelMap : PixelMap, options?: HdrDecomposeOptions): Promise<Picture | undefined>--><!--Device-image-function decomposeToPicture(hdrPixelMap : PixelMap, options?: HdrDecomposeOptions): Promise<Picture | undefined>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hdrPixelMap | [PixelMap](arkts-image-image-pixelmap-i.md) | 是 | HDR PixelMap，像素格式需为RGBA_F16、RGBA_1010102、YCBCR_P010或YCRCB_P010。 |
| options | [HdrDecomposeOptions](arkts-image-image-hdrdecomposeoptions-i-sys.md) | 否 | HDR分解配置选项，包含增益图尺寸和像素格式设置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Picture \| undefined&gt; | Promise对象。返回包含SDR PixelMap和增益图的Picture对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs. |
| [7600201](../errorcode-image.md#7600201-不支持的操作) | Unsupported operation. hdrPixelMap's PixelMapFormat is not RGBA_F16\RGBA_1010102\YCBCR_P010\YCRCB_P010. |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid parameter. Possible cause: hdrPixelMap is empty. |
| [7600208](../errorcode-image.md#7600208-hdr图片分解失败) | HDR image decomposition failed. Possible causes: 1. Decomposition processing is not supported. 2. Processing error occurs. |
| [7600301](../errorcode-image.md#7600301-申请内存失败) | Alloc memory failed. |

**示例：**

```TypeScript
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function DecomposeToPictureTest(context: Context) {
  const resourceMgr = context.resourceManager;
  const rawFile = await resourceMgr.getRawFileContent("test.jpg");
  let imageSource: image.ImageSource = image.createImageSource(rawFile);
  let decodingOptions: image.DecodingOptions = {
    desiredDynamicRange: image.DecodingDynamicRange.HDR,
  };
  let hdrPixelMap = await imageSource.createPixelMap(decodingOptions);
  // 指定gainmap为全尺寸，像素格式为NV12。
  let options: image.HdrDecomposeOptions = {
    isFullSizeGainmap: true,
    desiredPixelFormat: image.PixelMapFormat.NV12,
  };
  let picture: image.Picture | undefined = await image.decomposeToPicture(hdrPixelMap, options);
  if (picture != undefined) {
    console.info('Decompose to picture with options successfully');
  } else {
    console.error('Decompose to picture with options failed');
  }
}

```

