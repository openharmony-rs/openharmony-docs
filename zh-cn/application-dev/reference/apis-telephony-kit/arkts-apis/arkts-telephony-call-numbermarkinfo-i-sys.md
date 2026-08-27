# NumberMarkInfo（系统接口）

电话号码的标记信息。

**起始版本：** 12

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
```

## isCloud

```TypeScript
isCloud?: boolean
```

号码的标记是否来自云端，默认为false。  
-true：是  
-false：否

**类型：** boolean

**起始版本：** 12

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## markContent

```TypeScript
markContent?: string
```

号码的标记内容，markType为MARK_TYPE_ENTERPRISE时，该字段返回信息为“姓名 工号”。

**类型：** string

**起始版本：** 12

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## markCount

```TypeScript
markCount?: number
```

号码的标记次数。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## markDetails

```TypeScript
markDetails?: string
```

号码标记的详细信息，markType为MARK_TYPE_ENTERPRISE时，该字段返回信息为“部门 职位”。

**类型：** string

**起始版本：** 14

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## markSource

```TypeScript
markSource?: string
```

号码的标记来源供应商。

**类型：** string

**起始版本：** 12

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## markType

```TypeScript
markType: MarkType
```

号码的标记类型。

**类型：** [MarkType](arkts-telephony-call-marktype-e-sys.md)

**起始版本：** 12

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。
