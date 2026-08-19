# HTML

HTML类型数据，是[Text](arkts-arkdata-unifieddatachannel-text-c.md)的子类，用于描述超文本标记语言数据。

**继承/实现关系：** HTML extends [Text](arkts-arkdata-unifieddatachannel-text-c.md)

**起始版本：** 23

<!--Device-unifiedDataChannel-class HTML--><!--Device-unifiedDataChannel-class HTML-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## 导入模块

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
```

## plainContent

```TypeScript
plainContent?: string
```

去除html标签后的纯文本内容，非必填字段，默认值为空字符串。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-HTML-plainContent?: string--><!--Device-HTML-plainContent?: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

