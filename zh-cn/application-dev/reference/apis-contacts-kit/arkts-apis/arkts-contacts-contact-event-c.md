# Event

联系人事件类。

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

自定义事件类型，默认值为0。

**类型：** 0

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Applications.ContactsData

## EVENT_ANNIVERSARY

```TypeScript
static readonly EVENT_ANNIVERSARY: 1
```

周年纪念事件类型，默认值为1。

**类型：** 1

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Applications.ContactsData

## EVENT_BIRTHDAY

```TypeScript
static readonly EVENT_BIRTHDAY: 3
```

生日事件类型，默认值为3。

**类型：** 3

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Applications.ContactsData

## EVENT_OTHER

```TypeScript
static readonly EVENT_OTHER: 2
```

其它事件类型，默认值为2。

**类型：** 2

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Applications.ContactsData

## eventDate

```TypeScript
eventDate: string
```

事件的日期。

**类型：** string

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Applications.ContactsData

## INVALID_LABEL_ID

```TypeScript
static readonly INVALID_LABEL_ID: -1
```

无效事件类型，默认值为-1。

**类型：** -1

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Applications.ContactsData

## labelId

```TypeScript
labelId?: number
```

事件的类型。

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Applications.ContactsData

## labelName

```TypeScript
labelName?: string
```

事件的类型名称。

**类型：** string

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Applications.ContactsData

**示例**

使用JSON格式创建数据。

```TypeScript
let event: contact.Event = {
    eventDate: '2000-01-01'
};
```

或使用new一个Event对象的方式创建数据。

```TypeScript
let event = new contact.Event();
event.eventDate = '2000-01-01';
```
