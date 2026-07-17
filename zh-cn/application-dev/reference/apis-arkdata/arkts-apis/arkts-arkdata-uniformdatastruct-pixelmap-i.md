# PixelMap

系统定义的像素图类型数据，用于描述图像像素数据。创建PixelMap对象后，可用于图像拖拽、图像共享等场景，实现跨应用的图像数据传递。

**起始版本：** 15

<!--Device-uniformDataStruct-interface PixelMap--><!--Device-uniformDataStruct-interface PixelMap-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## 导入模块

```TypeScript
import { uniformDataStruct } from '@kit.ArkData';
```

## details

```TypeScript
details?: Record<string, number | number | number | string | Uint8Array>
```

字典类型对象，key为string类型，value可包含number（数值类型）、string（字符串类型）或Uint8Array（二进制字节数组）类型数据。非必填字段，默认值为空字典对象。

**类型：** Record<string, number | number | number | string | Uint8Array>

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PixelMap-details?: Record<string, int | long | double | string | Uint8Array>--><!--Device-PixelMap-details?: Record<string, int | long | double | string | Uint8Array>-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## pixelMap

```TypeScript
pixelMap: image.PixelMap
```

像素图对象。

**类型：** image.PixelMap

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PixelMap-pixelMap: image.PixelMap--><!--Device-PixelMap-pixelMap: image.PixelMap-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## uniformDataType

```TypeScript
readonly uniformDataType: 'openharmony.pixel-map'
```

统一数据类型标识为像素图类型数据，固定为"openharmony.pixel-map"，数据类型描述信息见[UniformDataType](arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md)。

**类型：** 'openharmony.pixel-map'

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PixelMap-readonly uniformDataType: 'openharmony.pixel-map'--><!--Device-PixelMap-readonly uniformDataType: 'openharmony.pixel-map'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

