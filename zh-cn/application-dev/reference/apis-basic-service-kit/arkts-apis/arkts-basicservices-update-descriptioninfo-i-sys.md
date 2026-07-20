# DescriptionInfo（系统接口）

版本描述文件信息。

**起始版本：** 9

<!--Device-update-export interface DescriptionInfo--><!--Device-update-export interface DescriptionInfo-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## content

```TypeScript
content: string
```

描述文件内容。

**类型：** string

**起始版本：** 9

<!--Device-DescriptionInfo-content: string--><!--Device-DescriptionInfo-content: string-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## descriptionType

```TypeScript
descriptionType: DescriptionType
```

描述文件类型，取值原则：CONTENT为内容，适用于描述内容较短或需要即时展示的场景；URI为链接，适用于描述内容较长或需要从外部资源获取的场景。应根据描述内容长度和展示方式选择。

**类型：** DescriptionType

**起始版本：** 9

<!--Device-DescriptionInfo-descriptionType: DescriptionType--><!--Device-DescriptionInfo-descriptionType: DescriptionType-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

