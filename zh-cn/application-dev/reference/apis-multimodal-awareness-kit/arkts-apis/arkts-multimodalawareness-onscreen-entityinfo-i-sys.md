# EntityInfo（系统接口）

提供感知到的实体信息，包括内容、链接、图像和其他类型的实体。

**起始版本：** 23

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { onScreen } from '@kit.MultimodalAwarenessKit';
```

## entityInfo

```TypeScript
entityInfo: Record<string, Object>
```

感知结果实体信息，包括内容、链接、图像和其它实体。

**类型：** Record&lt;string, Object&gt;

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## entityName

```TypeScript
entityName: string
```

感知结果实体名称，固定内容。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。
