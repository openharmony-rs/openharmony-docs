# NumberMarkInfo（系统接口）

电话号码的标记信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-call-export interface NumberMarkInfo--><!--Device-call-export interface NumberMarkInfo-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## isCloud

```TypeScript
isCloud?: boolean
```

号码的标记是否来自云端，默认为false。 -true：是 -false：否

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-NumberMarkInfo-isCloud?: boolean--><!--Device-NumberMarkInfo-isCloud?: boolean-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## markContent

```TypeScript
markContent?: string
```

号码的标记内容，markType为MARK_TYPE_ENTERPRISE时，该字段返回信息为“姓名 工号”。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-NumberMarkInfo-markContent?: string--><!--Device-NumberMarkInfo-markContent?: string-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## markCount

```TypeScript
markCount?: int
```

号码的标记次数。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-NumberMarkInfo-markCount?: int--><!--Device-NumberMarkInfo-markCount?: int-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## markDetails

```TypeScript
markDetails?: string
```

号码标记的详细信息，markType为MARK_TYPE_ENTERPRISE时，该字段返回信息为“部门 职位”。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-NumberMarkInfo-markDetails?: string--><!--Device-NumberMarkInfo-markDetails?: string-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## markSource

```TypeScript
markSource?: string
```

号码的标记来源供应商。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-NumberMarkInfo-markSource?: string--><!--Device-NumberMarkInfo-markSource?: string-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## markType

```TypeScript
markType: MarkType
```

号码的标记类型。

**类型：** [MarkType](arkts-telephony-call-marktype-e-sys.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-NumberMarkInfo-markType: MarkType--><!--Device-NumberMarkInfo-markType: MarkType-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

