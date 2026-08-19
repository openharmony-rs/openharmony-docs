# SearchQuery（系统接口）

搜索资产的查询配置。

**起始版本：** 26.1.0

<!--Device-photoAccessHelper-interface SearchQuery--><!--Device-photoAccessHelper-interface SearchQuery-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## offset

```TypeScript
offset: int
```

分页偏移量。 取值限定为整数。

**类型：** int

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SearchQuery-offset: int--><!--Device-SearchQuery-offset: int-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## queryString

```TypeScript
queryString: string
```

由用户输入的LLM分析生成的查询字符串。 最大长度为1000且不能为空。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SearchQuery-queryString: string--><!--Device-SearchQuery-queryString: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## size

```TypeScript
size: int
```

每个查询要返回的结果数。 取值限定为整数。

**类型：** int

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SearchQuery-size: int--><!--Device-SearchQuery-size: int-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

