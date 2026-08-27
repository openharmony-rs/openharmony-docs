# EntityInfoItem

实体信息属性。

**起始版本：** 11

**系统能力：** SystemCapability.Global.I18n

## 导入模块

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## begin

```TypeScript
begin: number
```

实体在输入字符串中的起始位置。

**类型：** number

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Global.I18n

## end

```TypeScript
end: number
```

实体在输入字符串中的终止位置。

**类型：** number

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Global.I18n

## type

```TypeScript
type: string
```

实体的类型，当前支持phone_number和date类型。phone_number表示实体类型是电话号码，date表示实体类型是时间日期。

**类型：** string

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Global.I18n
