# VideoStateType (System API)

```TypeScript
export enum VideoStateType
```

Video state type.

**Since:** 7

<!--Device-call-export enum VideoStateType--><!--Device-call-export enum VideoStateType-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## TYPE_VOICE

```TypeScript
TYPE_VOICE = 0
```

Voice state.

**Since:** 7

<!--Device-VideoStateType-TYPE_VOICE = 0--><!--Device-VideoStateType-TYPE_VOICE = 0-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## TYPE_VIDEO

```TypeScript
TYPE_VIDEO = 1
```

Video state.

**Since:** 7

**Deprecated since:** 11

**Substitutes:** [TYPE_VIDEO_BIDIRECTIONAL](#type_video_bidirectional)

<!--Device-VideoStateType-TYPE_VIDEO = 1--><!--Device-VideoStateType-TYPE_VIDEO = 1-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## TYPE_VIDEO_SEND_ONLY

```TypeScript
TYPE_VIDEO_SEND_ONLY = 1
```

Data sending only during a video call.

**Since:** 11

<!--Device-VideoStateType-TYPE_VIDEO_SEND_ONLY = 1--><!--Device-VideoStateType-TYPE_VIDEO_SEND_ONLY = 1-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## TYPE_VIDEO_RECEIVE_ONLY

```TypeScript
TYPE_VIDEO_RECEIVE_ONLY = 2
```

Data receiving only during a video call.

**Since:** 11

<!--Device-VideoStateType-TYPE_VIDEO_RECEIVE_ONLY = 2--><!--Device-VideoStateType-TYPE_VIDEO_RECEIVE_ONLY = 2-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## TYPE_VIDEO_BIDIRECTIONAL

```TypeScript
TYPE_VIDEO_BIDIRECTIONAL = 3
```

Data receiving/sending status during a video call.

**Since:** 11

<!--Device-VideoStateType-TYPE_VIDEO_BIDIRECTIONAL = 3--><!--Device-VideoStateType-TYPE_VIDEO_BIDIRECTIONAL = 3-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.
