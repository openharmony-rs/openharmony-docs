# Email

联系人的邮箱。

**起始版本：** 7

**系统能力：** SystemCapability.Applications.ContactsData

## 导入模块

```TypeScript
import { contact } from '@kit.ContactsKit';
```

## CUSTOM_LABEL

```TypeScript
static readonly CUSTOM_LABEL: 0
```

自定义邮箱类型，默认值为0。

**类型：** 0

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Applications.ContactsData

## displayName

```TypeScript
displayName?: string
```

邮箱的显示名称。

**类型：** string

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Applications.ContactsData

## email

```TypeScript
email: string
```

联系人的邮箱地址。

**类型：** string

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Applications.ContactsData

## EMAIL_HOME

```TypeScript
static readonly EMAIL_HOME: 1
```

家庭邮箱类型，默认值为1。

**类型：** 1

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Applications.ContactsData

## EMAIL_OTHER

```TypeScript
static readonly EMAIL_OTHER: 3
```

其它邮箱类型，默认值为3。

**类型：** 3

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Applications.ContactsData

## EMAIL_WORK

```TypeScript
static readonly EMAIL_WORK: 2
```

工作邮箱类型，默认值为2。

**类型：** 2

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Applications.ContactsData

## INVALID_LABEL_ID

```TypeScript
static readonly INVALID_LABEL_ID: -1
```

无效邮箱类型，默认值为-1。

**类型：** -1

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Applications.ContactsData

## labelId

```TypeScript
labelId?: number
```

邮箱的类型。

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Applications.ContactsData

## labelName

```TypeScript
labelName?: string
```

邮箱的类型名称。

**类型：** string

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Applications.ContactsData

**示例**

使用JSON格式创建数据。

```TypeScript
import { contact } from '@kit.ContactsKit';

let email: contact.Email = {
    email: 'xxx@email.com',
    displayName: 'displayName'
}
```

或使用new一个Email对象的方式创建数据。

```TypeScript
let email = new contact.Email();
email.email = 'xxx@email.com';
```
