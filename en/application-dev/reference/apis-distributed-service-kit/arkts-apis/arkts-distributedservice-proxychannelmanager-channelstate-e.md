# ChannelState

Enumerates the connection states of the proxy channel.

**Since:** 20

**System capability:** SystemCapability.DistributedSched.AppCollaboration

## CHANNEL_WAIT_RESUME

```TypeScript
CHANNEL_WAIT_RESUME = 0
```

The connection is disconnected, and the channel is unavailable.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedSched.AppCollaboration

## CHANNEL_RESUME

```TypeScript
CHANNEL_RESUME = 1
```

The connection is restored, and the channel is available.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedSched.AppCollaboration

## CHANNEL_EXCEPTION_SOFTWARE_FAILED

```TypeScript
CHANNEL_EXCEPTION_SOFTWARE_FAILED = 2
```

The channel is unavailable due to a software exception, for example, an internal protocol stack error or resource allocation failure. Check the logs to locate the specific cause.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedSched.AppCollaboration

## CHANNEL_BR_NO_PAIRED

```TypeScript
CHANNEL_BR_NO_PAIRED = 3
```

The Bluetooth pairing relationship is deleted, and the channel is unavailable.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedSched.AppCollaboration
