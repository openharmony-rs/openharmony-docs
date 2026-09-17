# NetUidRule (System API)

Enumerates the metered network rules.

**Since:** 10

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.

## NET_RULE_NONE

```TypeScript
NET_RULE_NONE = 0
```

Default rule.

**Since:** 10

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.

## NET_RULE_ALLOW_METERED_FOREGROUND

```TypeScript
NET_RULE_ALLOW_METERED_FOREGROUND = 1 << 0
```

Applications running in the foreground are allowed to access a metered network.

**Since:** 10

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.

## NET_RULE_ALLOW_METERED

```TypeScript
NET_RULE_ALLOW_METERED = 1 << 1
```

Applications are allowed to access a metered network.

**Since:** 10

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.

## NET_RULE_REJECT_METERED

```TypeScript
NET_RULE_REJECT_METERED = 1 << 2
```

Applications are not allowed to access a metered network.

**Since:** 10

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.

## NET_RULE_ALLOW_ALL

```TypeScript
NET_RULE_ALLOW_ALL = 1 << 5
```

Applications are allowed to access all networks (metered or non-metered).

**Since:** 10

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.

## NET_RULE_REJECT_ALL

```TypeScript
NET_RULE_REJECT_ALL = 1 << 6
```

Applications are not allowed to access any networks (metered or non-metered).

**Since:** 10

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.
