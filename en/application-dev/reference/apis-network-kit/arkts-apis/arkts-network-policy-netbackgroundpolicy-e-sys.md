# NetBackgroundPolicy (System API)

```TypeScript
export enum NetBackgroundPolicy
```

Enumerates the background network policies.

**Since:** 10

<!--Device-policy-export enum NetBackgroundPolicy--><!--Device-policy-export enum NetBackgroundPolicy-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.

## NET_BACKGROUND_POLICY_DISABLE

```TypeScript
NET_BACKGROUND_POLICY_DISABLE = 2
```

The application cannot use the metered network in the background.

**Since:** 10

<!--Device-NetBackgroundPolicy-NET_BACKGROUND_POLICY_DISABLE = 2--><!--Device-NetBackgroundPolicy-NET_BACKGROUND_POLICY_DISABLE = 2-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.

## NET_BACKGROUND_POLICY_ENABLE

```TypeScript
NET_BACKGROUND_POLICY_ENABLE = 1
```

The application can use the metered network in the background.

**Since:** 10

<!--Device-NetBackgroundPolicy-NET_BACKGROUND_POLICY_ENABLE = 1--><!--Device-NetBackgroundPolicy-NET_BACKGROUND_POLICY_ENABLE = 1-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.

## NET_BACKGROUND_POLICY_NONE

```TypeScript
NET_BACKGROUND_POLICY_NONE = 0
```

No background network policy is specified. This is the default value.

**Since:** 10

<!--Device-NetBackgroundPolicy-NET_BACKGROUND_POLICY_NONE = 0--><!--Device-NetBackgroundPolicy-NET_BACKGROUND_POLICY_NONE = 0-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.

## NET_BACKGROUND_POLICY_TRUSTLIST

```TypeScript
NET_BACKGROUND_POLICY_TRUSTLIST = 3
```

Only applications on the trustlist are allowed to access metered networks when they are running in the background.

**Since:** 10

<!--Device-NetBackgroundPolicy-NET_BACKGROUND_POLICY_TRUSTLIST = 3--><!--Device-NetBackgroundPolicy-NET_BACKGROUND_POLICY_TRUSTLIST = 3-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.
