# Hyperlink

[Text](arkts-arkdata-unifieddatachannel-text-c.md)的子类，用于描述超链接类型数据。

**继承/实现关系：** Hyperlink extends [Text](arkts-arkdata-unifieddatachannel-text-c.md)

**起始版本：** 10

<!--Device-unifiedDataChannel-class Hyperlink extends Text--><!--Device-unifiedDataChannel-class Hyperlink extends Text-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## 导入模块

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
```

## description

```TypeScript
description?: string
```

链接内容描述，非必填字段，默认值为空字符串。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Hyperlink-description?: string--><!--Device-Hyperlink-description?: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## url

```TypeScript
set url(value: string)
```

链接url。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Hyperlink-set url(value: string)--><!--Device-Hyperlink-set url(value: string)-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

