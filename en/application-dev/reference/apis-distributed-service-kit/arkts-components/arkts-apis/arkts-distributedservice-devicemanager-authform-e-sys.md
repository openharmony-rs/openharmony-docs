# AuthForm (System API)

```TypeScript
enum AuthForm
```

Enumerates the device authentication types.

**Since:** 10

**Deprecated since:** 11

<!--Device-deviceManager-enum AuthForm--><!--Device-deviceManager-enum AuthForm-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## INVALID_TYPE

```TypeScript
INVALID_TYPE = -1
```

No authentication.

**Since:** 10

**Deprecated since:** 11

<!--Device-AuthForm-INVALID_TYPE = -1--><!--Device-AuthForm-INVALID_TYPE = -1-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## PEER_TO_PEER

```TypeScript
PEER_TO_PEER = 0
```

Point-to-point authentication for devices without accounts.

**Since:** 10

**Deprecated since:** 11

<!--Device-AuthForm-PEER_TO_PEER = 0--><!--Device-AuthForm-PEER_TO_PEER = 0-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## IDENTICAL_ACCOUNT

```TypeScript
IDENTICAL_ACCOUNT = 1
```

Authentication for devices using the same account.

**Since:** 10

**Deprecated since:** 11

<!--Device-AuthForm-IDENTICAL_ACCOUNT = 1--><!--Device-AuthForm-IDENTICAL_ACCOUNT = 1-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## ACROSS_ACCOUNT

```TypeScript
ACROSS_ACCOUNT = 2
```

Authentication for devices using different accounts.

**Since:** 10

**Deprecated since:** 11

<!--Device-AuthForm-ACROSS_ACCOUNT = 2--><!--Device-AuthForm-ACROSS_ACCOUNT = 2-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.
