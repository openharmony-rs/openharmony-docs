# createPictureByHdrAndSdrPixelMap（系统接口）

## createPictureByHdrAndSdrPixelMap

```TypeScript
function createPictureByHdrAndSdrPixelMap(hdrPixelMap: PixelMap, sdrPixelMap: PixelMap): Promise<Picture>
```

根据HDR PixelMap和SDR PixelMap创建Picture对象。系统将使用HDR和SDR PixelMap生成一个增益图（gainmap），返回的Picture对象将包含SDR PixelMap和生成的gainmap
PixelMap，像素格式为RGBA8888。使用Promise异步回调。

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.Image.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hdrPixelMap | PixelMap | 是 | HDR PixelMap，位深16bit或10bit，像素格式为FP16/RGBA1010102/YCBCR_P010，色彩空间是BT2020_HLG。 |
| sdrPixelMap | PixelMap | 是 | SDR PixelMap，位深8bit，像素格式为RGBA8888/NV21，色彩空间是P3。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Picture&gt; | 返回Picture包含sdr和gainmap，像素格式为RGBA8888。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600201](../errorcode-image.md#7600201-不支持的操作) | Unsupported operation. HdrPixelMap's PixelMapFormat is notRGBA_F16\RGBA_1010102\YCBCR_P010, or its color space is not BT2020_HLG. Or sdrPixelMap's PixelMapFormat is notRGBA_8888\NV21\NV12, or its color space is not P3. |

**示例：**

```TypeScript
import { fileIo } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function CreatePictureTest(context: Context) {
  const resourceMgr = context.resourceManager;
  const rawFile = await resourceMgr.getRawFileContent("test.jpg"); // SDR
  let imageSource: image.ImageSource = image.createImageSource(rawFile);
  let options1: image.DecodingOptions = {
    desiredDynamicRange : image.DecodingDynamicRange.SDR,
  }
  let options2: image.DecodingOptions = {
    desiredDynamicRange : image.DecodingDynamicRange.HDR, // 通过AIHDR将SDR解码为HDR。
  }
  let sdrPixelMap = await imageSource.createPixelMap(options1);
  let hdrPixelMap = await imageSource.createPixelMap(options2);

  // 获取计算生成的gainmap并编码。
  let picture: image.Picture = await image.createPictureByHdrAndSdrPixelMap(hdrPixelMap, sdrPixelMap);
  if (picture != null) {
    console.info('Create picture succeeded');
  } else {
    console.error('Create picture failed');
  }
  const imagePackerObj = image.createImagePacker();
  let packOpts : image.PackingOption = { format : "image/jpeg", quality: 98};
  packOpts.desiredDynamicRange = image.PackingDynamicRange.AUTO;
  const path: string = context.filesDir + "/hdr-test.jpg";
  let file = fileIo.openSync(path, fileIo.OpenMode.CREATE | fileIo.OpenMode.READ_WRITE);
  imagePackerObj.packToFile(picture, file.fd, packOpts).then(() => {
  }).catch((error : BusinessError) => {
    console.error('Failed to pack the image. And the error is: ' + error);
  })
}

```


## createPictureByHdrAndSdrPixelMap

```TypeScript
function createPictureByHdrAndSdrPixelMap(hdrPixelMap: PixelMap, sdrPixelMap: PixelMap, 
      params: GainmapParams): Promise<Picture>
```

根据HDR PixelMap和SDR PixelMap创建Picture对象。系统将使用HDR和SDR PixelMap生成一个Gainmap（增益图），返回的Picture对象将包含SDR PixelMap和生成的Gainmap
PixelMap，像素格式为RGBA8888。Gainmap PixelMap的尺寸可以通过设置params进行选择。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hdrPixelMap | PixelMap | 是 | HDR PixelMap，位深16bit或10bit，像素格式为RGBA_F16/RGBA_1010102/YCBCR_P010，色彩空间是BT2020_HLG。 |
| sdrPixelMap | PixelMap | 是 | SDR PixelMap，位深8bit，像素格式为RGBA_8888/NV21，色彩空间是P3。 |
| params | GainmapParams | 是 | Gainmap Params，增益图参数设置选项，决定是否使用全尺寸增益图。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Picture&gt; | Promise对象，返回Picture包含SDR和Gainmap，像素格式为RGBA_8888。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs. |
| [7600201](../errorcode-image.md#7600201-不支持的操作) | Unsupported operation. HdrPixelMap's PixelMapFormat is notRGBA_F16\RGBA_1010102\YCBCR_P010, or its color space is not BT2020_HLG. Or sdrPixelMap's PixelMapFormat isnot RGBA_8888\NV21\NV12, or its color space is not P3. |

**示例：**

```TypeScript
import { fileIo } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

async function CreatePictureTest(context: Context) {
  const resourceMgr = context.resourceManager;
  const rawFile = await resourceMgr.getRawFileContent("test.jpg"); // 获取SDR图片。
  let imageSource: image.ImageSource = image.createImageSource(rawFile);
  let decodingOptionsForSDR: image.DecodingOptions = {
    desiredDynamicRange : image.DecodingDynamicRange.SDR,
  }
  let decodingOptionsForHDR: image.DecodingOptions = {
    desiredDynamicRange : image.DecodingDynamicRange.HDR, // 通过AIHDR将SDR解码为HDR。
  }
  let sdrPixelMap = await imageSource.createPixelMap(decodingOptionsForSDR);
  let hdrPixelMap = await imageSource.createPixelMap(decodingOptionsForHDR);
  let params : image.GainmapParams = {
    isFullSizeGainmap: true
  }

  // 获取计算生成的gainmap并编码。
  let picture: image.Picture = await image.createPictureByHdrAndSdrPixelMap(hdrPixelMap, sdrPixelMap, params);
  if (picture != null) {
    console.info('Succeeded in creating picture');
  } else {
    console.error('Create picture failed');
  }
  const imagePackerObj = image.createImagePacker();
  let packOpts : image.PackingOption = { format : "image/jpeg", quality: 98};
  packOpts.desiredDynamicRange = image.PackingDynamicRange.AUTO;
  const path: string = context.filesDir + "/hdr-test.jpg";
  let file = fileIo.openSync(path, fileIo.OpenMode.CREATE | fileIo.OpenMode.READ_WRITE);
  imagePackerObj.packToFile(picture, file.fd, packOpts).then(() => {
  }).catch((error : BusinessError) => {
    console.error('Failed to pack the image. And the error is: ' + error);
  })
}

```

