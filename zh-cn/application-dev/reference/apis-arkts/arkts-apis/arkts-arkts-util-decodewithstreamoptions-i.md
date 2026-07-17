# DecodeWithStreamOptions

定义解码是否跟随数据块。

**起始版本：** 11

<!--Device-util-interface DecodeWithStreamOptions--><!--Device-util-interface DecodeWithStreamOptions-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { util } from '@kit.ArkTS';
```

## stream

```TypeScript
stream?: boolean
```

是否允许后续的 **decodeWithStream()** 处理数据块。如果按块处理数据，请将此参数设置为 **true**。如果这是要处理的最后一个数据块或数据未分块，请将此参数设置为 **false**。默认值为 **false**。

**类型：** boolean

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DecodeWithStreamOptions-stream?: boolean--><!--Device-DecodeWithStreamOptions-stream?: boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

