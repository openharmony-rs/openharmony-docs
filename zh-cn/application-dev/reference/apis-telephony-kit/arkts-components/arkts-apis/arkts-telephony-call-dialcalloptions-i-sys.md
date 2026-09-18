# DialCallOptions（系统接口）

拨打电话的可选参数。

**起始版本：** 9

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { call } from '@kit.TelephonyKit';
```

## accountId

```TypeScript
accountId?: number
```

帐户Id。

- 0：卡槽1。  
- 1：卡槽2。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## dialScene

```TypeScript
dialScene?: DialScene
```

拨号场景。

**类型：** [DialScene](arkts-telephony-call-dialscene-e-sys.md)

**起始版本：** 9

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## dialType

```TypeScript
dialType?: DialType
```

拨号类型。

**类型：** [DialType](arkts-telephony-call-dialtype-e-sys.md)

**起始版本：** 9

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## extraParams

```TypeScript
extraParams?: Record<string, Object>
```

Indicates the extra call parameters.

**类型：** Record&lt;string, Object&gt;

**起始版本：** 14

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## videoState

```TypeScript
videoState?: VideoStateType
```

视频状态类型。

**类型：** [VideoStateType](arkts-telephony-call-videostatetype-e-sys.md)

**起始版本：** 9

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## xCallType

```TypeScript
xCallType?: XCallType
```

XCALL类型。

**起始版本:** 26.0.0

**类型：** [XCallType](arkts-telephony-call-xcalltype-e-sys.md)

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。
