# Contact

联系人对象类。

**起始版本：** 7

**系统能力：** SystemCapability.Applications.ContactsData

## INVALID_CONTACT_ID

```TypeScript
static readonly INVALID_CONTACT_ID: -1
```

默认联系人的id，值为-1。

**类型：** -1

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Applications.ContactsData

## contactAttributes

```TypeScript
contactAttributes?: ContactAttributes
```

联系人的属性列表，如果为空，则查询联系人的所有属性字段（包括姓名、电话、邮箱等）。

**类型：** ContactAttributes

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Applications.ContactsData

## emails

```TypeScript
emails?: Email[]
```

联系人的邮箱地址列表。

**类型：** Email[]

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Applications.ContactsData

## events

```TypeScript
events?: Event[]
```

联系人的生日、周年纪念等重要日期列表。

**类型：** Event[]

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Applications.ContactsData

## groups

```TypeScript
groups?: Group[]
```

联系人的群组列表。

**类型：** Group[]

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Applications.ContactsData

## id

```TypeScript
readonly id?: number
```

联系人的id，由系统自动生成。

**类型：** number

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Applications.ContactsData

## imAddresses

```TypeScript
imAddresses?: ImAddress[]
```

联系人的即时消息地址列表。

**类型：** ImAddress[]

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Applications.ContactsData

## key

```TypeScript
readonly key?: string
```

联系人的唯一查询键key，由系统自动生成。

**类型：** string

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Applications.ContactsData

## name

```TypeScript
name?: Name
```

联系人的姓名。

**类型：** Name

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Applications.ContactsData

## nickName

```TypeScript
nickName?: NickName
```

联系人的昵称。

**类型：** NickName

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Applications.ContactsData

## note

```TypeScript
note?: Note
```

联系人的备注。

**类型：** Note

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Applications.ContactsData

## organization

```TypeScript
organization?: Organization
```

联系人的组织信息。

**类型：** Organization

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Applications.ContactsData

## phoneNumbers

```TypeScript
phoneNumbers?: PhoneNumber[]
```

联系人的电话号码列表。

**类型：** PhoneNumber[]

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Applications.ContactsData

## portrait

```TypeScript
portrait?: Portrait
```

联系人的头像。

**类型：** Portrait

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Applications.ContactsData

## postalAddresses

```TypeScript
postalAddresses?: PostalAddress[]
```

联系人的邮政地址列表。

**类型：** PostalAddress[]

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Applications.ContactsData

## relations

```TypeScript
relations?: Relation[]
```

联系人的关系列表。

**类型：** Relation[]

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Applications.ContactsData

## sipAddresses

```TypeScript
sipAddresses?: SipAddress[]
```

联系人的会话发起协议(SIP)地址列表。

**类型：** SipAddress[]

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Applications.ContactsData

## websites

```TypeScript
websites?: Website[]
```

联系人的网站列表。

**类型：** Website[]

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Applications.ContactsData

