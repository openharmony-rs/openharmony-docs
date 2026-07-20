# Text

文本类型数据，是[UnifiedRecord](arkts-arkdata-unifieddatachannel-unifiedrecord-c.md)的子类，也是文本类型数据的基类，用于描述文本类数据，推荐开发者优先使用Text的子类描述数据，如[PlainText](arkts-arkdata-unifieddatachannel-plaintext-c.md)、[Hyperlink](arkts-arkdata-unifieddatachannel-hyperlink-c.md)、[HTML](arkts-arkdata-unifieddatachannel-html-c.md)等具体子类。

**继承/实现关系：** Text extends [UnifiedRecord](arkts-arkdata-unifieddatachannel-unifiedrecord-c.md)

**起始版本：** 10

<!--Device-unifiedDataChannel-class Text extends UnifiedRecord--><!--Device-unifiedDataChannel-class Text extends UnifiedRecord-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## 导入模块

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
```

## details

```TypeScript
details?: Record<string, string>
```

是一个字典类型对象，key和value都是string类型，用于描述文本内容。例如，可生成一个details内容为

{

"title":"标题",

"content":"内容"

}

的数据对象，用于描述一篇文章。非必填字段，默认值为空字典对象。

**类型：** Record&lt;string, string&gt;

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Text-details?: Record<string, string>--><!--Device-Text-details?: Record<string, string>-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

