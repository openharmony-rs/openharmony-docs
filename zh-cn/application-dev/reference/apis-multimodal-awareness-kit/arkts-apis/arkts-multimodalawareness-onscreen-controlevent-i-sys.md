# ControlEvent（系统接口）

控制事件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-onScreen-export interface ControlEvent--><!--Device-onScreen-export interface ControlEvent-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## eventType

```TypeScript
eventType: EventType
```

控制事件类型。

**类型：** EventType

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ControlEvent-eventType: EventType--><!--Device-ControlEvent-eventType: EventType-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## hookId

```TypeScript
hookId?: long
```

控制事件对应的hook ID。控制事件要操作的hook ID和该次会话对应的session ID都由某次会话获取的[PageContent](arkts-multimodalawareness-onscreen-pagecontent-i-sys.md#PageContent（系统接口）)提供。

**类型：** long

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ControlEvent-hookId?: long--><!--Device-ControlEvent-hookId?: long-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## sessionId

```TypeScript
sessionId: long
```

控制事件要操作的session ID。控制事件要操作的hook ID和该次会话对应的session ID都由某次会话获取的[PageContent](arkts-multimodalawareness-onscreen-pagecontent-i-sys.md#PageContent（系统接口）)提供。

**类型：** long

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ControlEvent-sessionId: long--><!--Device-ControlEvent-sessionId: long-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## windowId

```TypeScript
windowId: int
```

控制事件要操作的窗口的window ID。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ControlEvent-windowId: int--><!--Device-ControlEvent-windowId: int-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

