# TextDecoderOptions

描述解码相关的选项，包含 **fatal** 和 **ignoreBOM**。

**起始版本：** 11

<!--Device-util-interface TextDecoderOptions--><!--Device-util-interface TextDecoderOptions-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { util } from '@kit.ArkTS';
```

## fatal

```TypeScript
fatal?: boolean
```

是否显示致命错误。值为 **true** 表示显示致命错误，值为 **false** 表示相反的情况。默认值为 **false**。

**类型：** boolean

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextDecoderOptions-fatal?: boolean--><!--Device-TextDecoderOptions-fatal?: boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

## ignoreBOM

```TypeScript
ignoreBOM?: boolean
```

是否忽略 BOM。值为 **true** 表示忽略 BOM，值为 **false** 表示相反的情况。默认值为 **false**。

**类型：** boolean

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextDecoderOptions-ignoreBOM?: boolean--><!--Device-TextDecoderOptions-ignoreBOM?: boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

