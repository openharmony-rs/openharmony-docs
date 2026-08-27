# Holder

创建联系人的应用信息类。

**起始版本：** 7

**系统能力：** SystemCapability.Applications.ContactsData

## 导入模块

```TypeScript
import { contact } from '@kit.ContactsKit';
```

## bundleName

```TypeScript
readonly bundleName: string
```

Bundle名称，默认值为com.ohos.contacts。

**类型：** string

**起始版本：** 7

**系统能力：** SystemCapability.Applications.ContactsData

## displayName

```TypeScript
readonly displayName?: string
```

应用名称，默认值为空。

**类型：** string

**起始版本：** 7

**系统能力：** SystemCapability.Applications.ContactsData

## holderId

```TypeScript
holderId?: number
```

应用Id，默认值为空。

**类型：** number

**起始版本：** 7

**系统能力：** SystemCapability.Applications.ContactsData

**示例**

使用JSON格式创建数据。

```TypeScript
let holder: contact.Holder = {
  bundleName: 'com.ohos.contacts',
  displayName: 'displayName',
  holderId: 1
};
```
