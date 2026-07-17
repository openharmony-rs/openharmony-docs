# ContactSelectionOptions

选择联系人条件。

**起始版本：** 10

<!--Device-contact-interface ContactSelectionOptions--><!--Device-contact-interface ContactSelectionOptions-End-->

**系统能力：** SystemCapability.Applications.Contacts

## 导入模块

```TypeScript
import { contact } from '@kit.ContactsKit';
```

## filter

```TypeScript
filter?: ContactSelectionFilter
```

联系人查询过滤器。从API version 15 开始，该接口支持在原子化服务中使用。

**类型：** ContactSelectionFilter

**起始版本：** 15

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-ContactSelectionOptions-filter?: ContactSelectionFilter--><!--Device-ContactSelectionOptions-filter?: ContactSelectionFilter-End-->

**系统能力：** SystemCapability.Applications.Contacts

## isAutoDismissOnNavigation

```TypeScript
isAutoDismissOnNavigation?: boolean
```

联系人picker发生页面路由时是否自动关闭，比如应用退后台场景默认值为false

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ContactSelectionOptions-isAutoDismissOnNavigation?: boolean--><!--Device-ContactSelectionOptions-isAutoDismissOnNavigation?: boolean-End-->

**系统能力：** SystemCapability.Applications.Contacts

## isDisplayedByName

```TypeScript
isDisplayedByName?: boolean
```

是否按联系人姓名维度展示，true:按联系人姓名维度展示，false:按联系人号码维度展示，默认值为false。从API version 15 开始，该接口支持在原子化服务中使用。

**类型：** boolean

**起始版本：** 15

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-ContactSelectionOptions-isDisplayedByName?: boolean--><!--Device-ContactSelectionOptions-isDisplayedByName?: boolean-End-->

**系统能力：** SystemCapability.Applications.Contacts

## isMultiSelect

```TypeScript
isMultiSelect?: boolean
```

是否为多选，true:多选，false:单选。默认值为false。

**类型：** boolean

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ContactSelectionOptions-isMultiSelect?: boolean--><!--Device-ContactSelectionOptions-isMultiSelect?: boolean-End-->

**系统能力：** SystemCapability.Applications.Contacts

## maxSelectable

```TypeScript
maxSelectable?: number
```

联系人数量上限。默认值为10000，超出上限则以默认值筛选。从API version 15 开始，该接口支持在原子化服务中使用。

**类型：** number

**起始版本：** 15

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-ContactSelectionOptions-maxSelectable?: number--><!--Device-ContactSelectionOptions-maxSelectable?: number-End-->

**系统能力：** SystemCapability.Applications.Contacts

