# SipAddress

联系人的会话发起协议(SIP)地址类。

**起始版本：** 7

<!--Device-contact-class SipAddress--><!--Device-contact-class SipAddress-End-->

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

<!--Device-SipAddress-static readonly CUSTOM_LABEL: 0--><!--Device-SipAddress-static readonly CUSTOM_LABEL: 0-End-->

**系统能力：** SystemCapability.Applications.ContactsData

## INVALID_LABEL_ID

```TypeScript
static readonly INVALID_LABEL_ID: -1
```

无效邮箱类型，默认值为-1。

**类型：** -1

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SipAddress-static readonly INVALID_LABEL_ID: -1--><!--Device-SipAddress-static readonly INVALID_LABEL_ID: -1-End-->

**系统能力：** SystemCapability.Applications.ContactsData

## SIP_HOME

```TypeScript
static readonly SIP_HOME: 1
```

家庭会话发起协议(SIP)地址类型，默认值为1。

**类型：** 1

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SipAddress-static readonly SIP_HOME: 1--><!--Device-SipAddress-static readonly SIP_HOME: 1-End-->

**系统能力：** SystemCapability.Applications.ContactsData

## SIP_OTHER

```TypeScript
static readonly SIP_OTHER: 3
```

其它会话发起协议(SIP)地址类型，默认值为3。

**类型：** 3

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SipAddress-static readonly SIP_OTHER: 3--><!--Device-SipAddress-static readonly SIP_OTHER: 3-End-->

**系统能力：** SystemCapability.Applications.ContactsData

## SIP_WORK

```TypeScript
static readonly SIP_WORK: 2
```

工作会话发起协议(SIP)地址类型，默认值为2。

**类型：** 2

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SipAddress-static readonly SIP_WORK: 2--><!--Device-SipAddress-static readonly SIP_WORK: 2-End-->

**系统能力：** SystemCapability.Applications.ContactsData

## labelId

```TypeScript
labelId?: number
```

邮箱的类型。

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SipAddress-labelId?: number--><!--Device-SipAddress-labelId?: number-End-->

**系统能力：** SystemCapability.Applications.ContactsData

## labelName

```TypeScript
labelName?: string
```

邮箱的类型名称。

**类型：** string

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SipAddress-labelName?: string--><!--Device-SipAddress-labelName?: string-End-->

**系统能力：** SystemCapability.Applications.ContactsData

## sipAddress

```TypeScript
sipAddress: string
```

会话发起协议(SIP)地址。

**类型：** string

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SipAddress-sipAddress: string--><!--Device-SipAddress-sipAddress: string-End-->

**系统能力：** SystemCapability.Applications.ContactsData

