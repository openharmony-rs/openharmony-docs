# ContactAttributes

联系人属性列表，一般作为入参用来标识希望查询的联系人属性。 当传入为null时，默认查询全部属性。

**起始版本：** 7

**系统能力：** SystemCapability.Applications.ContactsData

## 导入模块

```TypeScript
import { contact } from '@kit.ContactsKit';
```

## attributes

```TypeScript
attributes: Attribute[]
```

联系人的属性列表，如果为空，则查询联系人的所有属性字段（包括姓名、电话、邮箱等）。

**类型：** [Attribute](arkts-contacts-contact-attribute-e.md)[]

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Applications.ContactsData

**示例**

通过JSON格式创建数据。

```TypeScript
let contactAttributes: contact.ContactAttributes = {
    attributes: [
        contact.Attribute.ATTR_EMAIL,
        contact.Attribute.ATTR_NAME,
        contact.Attribute.ATTR_PHONE
    ]
};
```
