# Text

```TypeScript
class Text extends UnifiedRecord
```

Represents text data. It is a subclass of [UnifiedRecord](arkts-arkdata-unifieddatachannel-unifiedrecord-c.md) and the base class of text data, used to describe text data. You are advised to use subclasses of Text, such as [PlainText](arkts-arkdata-unifieddatachannel-plaintext-c.md), [Hyperlink](arkts-arkdata-unifieddatachannel-hyperlink-c.md), and [HTML](arkts-arkdata-unifieddatachannel-html-c.md), to describe data.

**Inheritance/Implementation:** Text extends [UnifiedRecord](arkts-arkdata-unifieddatachannel-unifiedrecord-c.md)

**Since:** 10

<!--Device-unifiedDataChannel-class Text extends UnifiedRecord--><!--Device-unifiedDataChannel-class Text extends UnifiedRecord-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## Modules to Import

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
```

## details

```TypeScript
details?: Record<string, string>
```

A dictionary object whose keys and values are both strings, used to describe the text content. For example, you can create a data object whose details are

{

"title":"Title",

"content":"Content"

}

to describe an article. This is an optional field, and the default value is an empty dictionary object.

**Type:** Record&lt;string, string&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-Text-details?: Record<string, string>--><!--Device-Text-details?: Record<string, string>-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
