# FormInfoFilter

```TypeScript
interface FormInfoFilter
```

卡片信息过滤器，仅将符合过滤器内要求的卡片信息返回。

**起始版本：** 9

<!--Device-formInfo-interface FormInfoFilter--><!--Device-formInfo-interface FormInfoFilter-End-->

**系统能力：** SystemCapability.Ability.Form

## 导入模块

```TypeScript
import { formInfo } from '@kit.FormKit';
```

## moduleName

```TypeScript
moduleName?: string
```

卡片所属模块的名称，用于过滤卡片信息。仅保留含moduleName与提供值相符的卡片信息，未填写时则不通过moduleName进行过滤。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

<!--Device-FormInfoFilter-moduleName?: string--><!--Device-FormInfoFilter-moduleName?: string-End-->

**系统能力：** SystemCapability.Ability.Form
