# NetUidPolicy (System API)

```TypeScript
export enum NetUidPolicy
```

Enumerates network access policies for the application.

**Since:** 10

<!--Device-policy-export enum NetUidPolicy--><!--Device-policy-export enum NetUidPolicy-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.

## NET_POLICY_NONE

```TypeScript
NET_POLICY_NONE = 0
```

Default network policy.

**Since:** 10

<!--Device-NetUidPolicy-NET_POLICY_NONE = 0--><!--Device-NetUidPolicy-NET_POLICY_NONE = 0-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.

## NET_POLICY_ALLOW_METERED_BACKGROUND

```TypeScript
NET_POLICY_ALLOW_METERED_BACKGROUND = 1 << 0
```

Background applications are allowed to access a metered network.

**Since:** 10

<!--Device-NetUidPolicy-NET_POLICY_ALLOW_METERED_BACKGROUND = 1 << 0--><!--Device-NetUidPolicy-NET_POLICY_ALLOW_METERED_BACKGROUND = 1 << 0-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.

## NET_POLICY_REJECT_METERED_BACKGROUND

```TypeScript
NET_POLICY_REJECT_METERED_BACKGROUND = 1 << 1
```

Applications running in the background are not allowed to access a metered network.

**Since:** 10

<!--Device-NetUidPolicy-NET_POLICY_REJECT_METERED_BACKGROUND = 1 << 1--><!--Device-NetUidPolicy-NET_POLICY_REJECT_METERED_BACKGROUND = 1 << 1-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.
