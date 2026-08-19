# DialOptions

拨打电话的可选参数。

**起始版本：** 23

<!--Device-call-export interface DialOptions--><!--Device-call-export interface DialOptions-End-->

**系统能力：** SystemCapability.Telephony.CallManager

## 导入模块

```TypeScript
import { call } from '@kit.TelephonyKit';
```

## accountId

```TypeScript
accountId?: int
```

帐户Id。 - 0：卡槽1。 - 1：卡槽2。 。此接口为系统接口。

**类型：** int

**起始版本：** 23

<!--Device-DialOptions-accountId?: int--><!--Device-DialOptions-accountId?: int-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## dialScene

```TypeScript
dialScene?: DialScene
```

拨号场景。此接口为系统接口。

**类型：** [DialScene](arkts-telephony-call-dialscene-e-sys.md)

**起始版本：** 23

<!--Device-DialOptions-dialScene?: DialScene--><!--Device-DialOptions-dialScene?: DialScene-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## dialType

```TypeScript
dialType?: DialType
```

拨号类型。此接口为系统接口。

**类型：** [DialType](arkts-telephony-call-dialtype-e-sys.md)

**起始版本：** 23

<!--Device-DialOptions-dialType?: DialType--><!--Device-DialOptions-dialType?: DialType-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## videoState

```TypeScript
videoState?: VideoStateType
```

视频状态类型。此接口为系统接口。

**类型：** [VideoStateType](arkts-telephony-call-videostatetype-e-sys.md)

**起始版本：** 23

<!--Device-DialOptions-videoState?: VideoStateType--><!--Device-DialOptions-videoState?: VideoStateType-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

