# NetBackgroundPolicy (System API)

Enumerates the background network policies.

**Since:** 10

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.

## NET_BACKGROUND_POLICY_NONE

```TypeScript
NET_BACKGROUND_POLICY_NONE = 0
```

No background network policy is specified. This is the default value.

**Since:** 10

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.

## NET_BACKGROUND_POLICY_ENABLE

```TypeScript
NET_BACKGROUND_POLICY_ENABLE = 1
```

Background applications are allowed to access a metered network.

**Since:** 10

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.

## NET_BACKGROUND_POLICY_DISABLE

```TypeScript
NET_BACKGROUND_POLICY_DISABLE = 2
```

Applications running in the background are not allowed to access a metered network.

**Since:** 10

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.

## NET_BACKGROUND_POLICY_TRUSTLIST

```TypeScript
NET_BACKGROUND_POLICY_TRUSTLIST = 3
```

Only applications on the allowlist are allowed to access metered networks when they are running in the background.

**Since:** 10

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.
