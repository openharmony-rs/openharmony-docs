# PlainText

[Text](arkts-arkdata-unifieddatachannel-text-c.md)的子类，用于描述纯文本类数据。

**继承/实现关系：** PlainText extends [Text](arkts-arkdata-unifieddatachannel-text-c.md)

**起始版本：** 10

<!--Device-unifiedDataChannel-class PlainText extends Text--><!--Device-unifiedDataChannel-class PlainText extends Text-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## 导入模块

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
```

## abstract

```TypeScript
abstract?: string
```

纯文本摘要，非必填字段，默认值为空字符串。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PlainText-abstract?: string--><!--Device-PlainText-abstract?: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## textContent

```TypeScript
set textContent(value: string)
```

纯文本内容。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PlainText-set textContent(value: string)--><!--Device-PlainText-set textContent(value: string)-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

