# AVMetadata

音视频元数据，包含各个元数据字段。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## gltf_offset

```TypeScript
gltf_offset?: string
```

GLTF 3D模型在媒体文件中的偏移。不支持AVRecorder设置该属性。如果媒体文件没有GLTF 3D模型，则gltf_offset是undefined。

**类型：** string

**起始版本：** 21

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

**系统接口：** 此接口为系统接口。
