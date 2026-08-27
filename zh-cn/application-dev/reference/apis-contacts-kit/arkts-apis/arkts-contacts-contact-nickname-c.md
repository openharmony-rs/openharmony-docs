# NickName

联系人的昵称类。

**起始版本：** 7

**系统能力：** SystemCapability.Applications.ContactsData

## 导入模块

```TypeScript
import { contact } from '@kit.ContactsKit';
```

## nickName

```TypeScript
nickName: string
```

联系人的昵称。

**类型：** string

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Applications.ContactsData

**示例**

使用JSON格式创建数据。

```TypeScript
import { contact } from '@kit.ContactsKit';

let nickName: contact.NickName = {
    nickName: 'nickName'
};
```
