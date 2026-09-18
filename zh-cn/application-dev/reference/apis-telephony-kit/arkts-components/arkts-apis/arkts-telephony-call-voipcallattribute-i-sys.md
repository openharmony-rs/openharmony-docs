# VoipCallAttribute（系统接口）

VoIP通话信息。

**起始版本：** 11

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { call } from '@kit.TelephonyKit';
```

## abilityName

```TypeScript
abilityName: string
```

需加载的三方应用的界面ability。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## extensionId

```TypeScript
extensionId: string
```

三方应用进程Id。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## isConferenceCall

```TypeScript
isConferenceCall?: boolean
```

上报是否是电话会议。

**类型：** boolean

**起始版本：** 12

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## isVoiceAnswerSupported

```TypeScript
isVoiceAnswerSupported?: boolean
```

上报来电时是否支持语音接听。

**类型：** boolean

**起始版本：** 12

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## showBannerForIncomingCall

```TypeScript
showBannerForIncomingCall?: boolean
```

上报来电时是否显示来电横幅。

**类型：** boolean

**起始版本：** 12

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## userName

```TypeScript
userName: string
```

用户昵称。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## userProfile

```TypeScript
userProfile: image.PixelMap
```

用户头像图片。

**类型：** [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)

**起始版本：** 11

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## voipBundleName

```TypeScript
voipBundleName: string
```

三方应用包名。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## voipCallId

```TypeScript
voipCallId: string
```

VoIP通话唯一Id。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。
