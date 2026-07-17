# FilterClause

联系人过滤条件。多个筛选条件之间是“或者”的关系，如果参数是数组类型，数组最多只能包含3个元素。

**起始版本：** 15

<!--Device-contact-interface FilterClause--><!--Device-contact-interface FilterClause-End-->

**系统能力：** SystemCapability.Applications.Contacts

## 导入模块

```TypeScript
import { contact } from '@kit.ContactsKit';
```

## dataItem

```TypeScript
dataItem?: DataFilter
```

联系人数据过滤项。

**类型：** DataFilter

**起始版本：** 15

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-FilterClause-dataItem?: DataFilter--><!--Device-FilterClause-dataItem?: DataFilter-End-->

**系统能力：** SystemCapability.Applications.Contacts

## focusModeList

```TypeScript
focusModeList?: Array<FilterOptions>
```

专注模式。

**类型：** Array<FilterOptions>

**起始版本：** 15

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-FilterClause-focusModeList?: Array<FilterOptions>--><!--Device-FilterClause-focusModeList?: Array<FilterOptions>-End-->

**系统能力：** SystemCapability.Applications.Contacts

## id

```TypeScript
id?: Array<FilterOptions>
```

联系人id。

**类型：** Array<FilterOptions>

**起始版本：** 15

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-FilterClause-id?: Array<FilterOptions>--><!--Device-FilterClause-id?: Array<FilterOptions>-End-->

**系统能力：** SystemCapability.Applications.Contacts

## name

```TypeScript
name?: Array<FilterOptions>
```

联系人姓名。

**类型：** Array<FilterOptions>

**起始版本：** 15

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-FilterClause-name?: Array<FilterOptions>--><!--Device-FilterClause-name?: Array<FilterOptions>-End-->

**系统能力：** SystemCapability.Applications.Contacts

