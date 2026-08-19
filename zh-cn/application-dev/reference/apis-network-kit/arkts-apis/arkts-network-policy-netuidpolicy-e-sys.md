# NetUidPolicy（系统接口）

应用对应的网络策略。

**起始版本：** 10

<!--Device-policy-export enum NetUidPolicy--><!--Device-policy-export enum NetUidPolicy-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

## NET_POLICY_NONE

```TypeScript
NET_POLICY_NONE = 0
```

默认网络策略。

**起始版本：** 10

<!--Device-NetUidPolicy-NET_POLICY_NONE = 0--><!--Device-NetUidPolicy-NET_POLICY_NONE = 0-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

## NET_POLICY_ALLOW_METERED_BACKGROUND

```TypeScript
NET_POLICY_ALLOW_METERED_BACKGROUND = 1 << 0
```

应用在后台可以使用计量网路。

**起始版本：** 10

<!--Device-NetUidPolicy-NET_POLICY_ALLOW_METERED_BACKGROUND = 1 << 0--><!--Device-NetUidPolicy-NET_POLICY_ALLOW_METERED_BACKGROUND = 1 << 0-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

## NET_POLICY_REJECT_METERED_BACKGROUND

```TypeScript
NET_POLICY_REJECT_METERED_BACKGROUND = 1 << 1
```

应用在后台不可以使用计量网路。

**起始版本：** 10

<!--Device-NetUidPolicy-NET_POLICY_REJECT_METERED_BACKGROUND = 1 << 1--><!--Device-NetUidPolicy-NET_POLICY_REJECT_METERED_BACKGROUND = 1 << 1-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

