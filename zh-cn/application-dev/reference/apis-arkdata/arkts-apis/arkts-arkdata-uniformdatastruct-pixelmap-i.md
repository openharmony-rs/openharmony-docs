# PixelMap

系统定义的像素图类型数据，用于描述图像像素数据。创建PixelMap对象后，可用于图像拖拽、图像共享等场景，实现跨应用的图像数据传递。

**起始版本：** 15

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

**类型：** Record&lt;string, number \| number \| number \| string \| Uint8Array&gt;

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## pixelMap

```TypeScript
pixelMap: image.PixelMap
```

像素图对象。

**类型：** image.PixelMap

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## uniformDataType

```TypeScript
readonly uniformDataType: 'openharmony.pixel-map'
```

统一数据类型标识为像素图类型数据，固定为"openharmony.pixel-map"，数据类型描述信息见 [UniformDataType](arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md)。

**类型：** 'openharmony.pixel-map'

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**示例**

```TypeScript
import { unifiedDataChannel, uniformTypeDescriptor } from '@kit.ArkData';
import { image } from '@kit.ImageKit';

let u8Array = new Uint8Array([1, 2, 3, 4, 5, 6, 7, 8, 9, 10]);
let arrayBuffer = new ArrayBuffer(4 * 200 * 200);
let opt: image.InitializationOptions = {
  editable: true,
  pixelFormat: 3,
  size: { height: 200, width: 200 },
  alphaType: 3
};
let pixelMapDetails: Record<string, number | string | Uint8Array> = {
  'pixelMapKey1': 123,
  'pixelMapKey2': 'pixelMapValue',
  'pixelMapKey3': u8Array
};
let pixelMap: uniformDataStruct.PixelMap = {
  uniformDataType: 'openharmony.pixel-map',
  pixelMap: image.createPixelMapSync(arrayBuffer, opt),
  details: pixelMapDetails
};
console.info('pixelMap.uniformDataType: ' + pixelMap.uniformDataType);
let record = new unifiedDataChannel.UnifiedRecord(uniformTypeDescriptor.UniformDataType.OPENHARMONY_PIXEL_MAP, pixelMap);
```
