# AVSessionDescriptor

```TypeScript
interface AVSessionDescriptor
```

会话的相关描述信息。

**起始版本：** 23

<!--Device-avSession-interface AVSessionDescriptor--><!--Device-avSession-interface AVSessionDescriptor-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Manager

## 导入模块

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## elementName

```TypeScript
elementName: ElementName
```

会话所属应用的信息（包含bundleName、abilityName等）。

**类型：** [ElementName](../../apis-ability-kit/arkts-apis/arkts-ability-elementname-i.md)

**起始版本：** 23

<!--Device-AVSessionDescriptor-elementName: ElementName--><!--Device-AVSessionDescriptor-elementName: ElementName-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Manager

## isActive

```TypeScript
isActive: boolean
```

会话是否被激活。

true：已被激活。

false：没有被激活。

**类型：** boolean

**起始版本：** 23

<!--Device-AVSessionDescriptor-isActive: boolean--><!--Device-AVSessionDescriptor-isActive: boolean-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Manager

## isTopSession

```TypeScript
isTopSession: boolean
```

会话是否为最新的会话。

true：是最新的会话。

false：不是最新的会话。

**类型：** boolean

**起始版本：** 23

<!--Device-AVSessionDescriptor-isTopSession: boolean--><!--Device-AVSessionDescriptor-isTopSession: boolean-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Manager

## sessionId

```TypeScript
sessionId: string
```

会话ID。

**类型：** string

**起始版本：** 23

<!--Device-AVSessionDescriptor-sessionId: string--><!--Device-AVSessionDescriptor-sessionId: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Manager

## sessionTag

```TypeScript
sessionTag: string
```

会话的自定义名称。

**类型：** string

**起始版本：** 23

<!--Device-AVSessionDescriptor-sessionTag: string--><!--Device-AVSessionDescriptor-sessionTag: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Manager

## type

```TypeScript
type: AVSessionType
```

会话类型。

**类型：** [AVSessionType](arkts-avsession-avsession-avsessiontype-t.md)

**起始版本：** 23

<!--Device-AVSessionDescriptor-type: AVSessionType--><!--Device-AVSessionDescriptor-type: AVSessionType-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Manager
