# C2PASignatureConfig

```TypeScript
interface C2PASignatureConfig
```

描述C2PA签名配置，包含用于生成C2PA签名的作者名称和作者ID。

**起始版本：** 26.0.1

<!--Device-cameraPicker-interface C2PASignatureConfig--><!--Device-cameraPicker-interface C2PASignatureConfig-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
import { cameraPicker } from '@kit.CameraKit';
```

## authorID

```TypeScript
authorID?: string
```

C2PA签名的作者ID。该字段可选。如果不设置，C2PA签名中将不包含作者ID。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-C2PASignatureConfig-authorID?: string--><!--Device-C2PASignatureConfig-authorID?: string-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## authorName

```TypeScript
authorName?: string
```

C2PA签名的作者名称。该字段可选。如果不设置，C2PA签名中将不包含作者名称。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-C2PASignatureConfig-authorName?: string--><!--Device-C2PASignatureConfig-authorName?: string-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core
