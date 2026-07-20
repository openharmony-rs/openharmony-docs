# DescriptionOptions（系统接口）

描述文件选项，用于指定描述文件的格式和语言。对象包含format(描述文件格式，可选STANDARD或SIMPLIFIED)和language(语言代码，如'zh-cn')字段。

**起始版本：** 9

<!--Device-update-export interface DescriptionOptions--><!--Device-update-export interface DescriptionOptions-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## format

```TypeScript
format: DescriptionFormat
```

描述文件格式。取值原则：STANDARD适合需要完整描述信息的场景，SIMPLIFIED适合仅需精简描述信息的场景。

**类型：** DescriptionFormat

**起始版本：** 9

<!--Device-DescriptionOptions-format: DescriptionFormat--><!--Device-DescriptionOptions-format: DescriptionFormat-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## language

```TypeScript
language: string
```

描述文件语言，格式如'zh-cn'(中文)、'en-us'(英文)、'ja-jp'(日文)等，长度范围[2，10]，单位：字符。有效字符包括字母（区分大小写）和连字符（-），建议使用小写格式。超出范围或包含无效字符时抛出异常。

**类型：** string

**起始版本：** 9

<!--Device-DescriptionOptions-language: string--><!--Device-DescriptionOptions-language: string-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

