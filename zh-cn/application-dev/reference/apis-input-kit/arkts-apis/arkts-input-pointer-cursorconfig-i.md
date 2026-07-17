# CursorConfig

自定义光标配置。

**起始版本：** 15

<!--Device-pointer-interface CursorConfig--><!--Device-pointer-interface CursorConfig-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Pointer

## 导入模块

```TypeScript
import { pointer } from '@kit.InputKit';
```

## followSystem

```TypeScript
followSystem : boolean
```

是否根据系统设置调整光标大小。false表示使用自定义光标样式大小，true表示根据系统设置调整光标大小，可调整范围为：[光标资源图大小，256×256]。

**类型：** boolean

**起始版本：** 15

<!--Device-CursorConfig-followSystem : boolean--><!--Device-CursorConfig-followSystem : boolean-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Pointer

