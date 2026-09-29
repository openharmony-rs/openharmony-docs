# ConnectionReason

```TypeScript
enum ConnectionReason
```

Enum for the connection reason.

**Since:** 26.0.0

<!--Device-remoteDevice-enum ConnectionReason--><!--Device-remoteDevice-enum ConnectionReason-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

## CONNECTION_SUCCESS

```TypeScript
CONNECTION_SUCCESS = 0
```

Connection succeeded.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ConnectionReason-CONNECTION_SUCCESS = 0--><!--Device-ConnectionReason-CONNECTION_SUCCESS = 0-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

## CONNECTION_FAILURE

```TypeScript
CONNECTION_FAILURE = 1
```

Connection failed.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ConnectionReason-CONNECTION_FAILURE = 1--><!--Device-ConnectionReason-CONNECTION_FAILURE = 1-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

## CONNECTION_LOCAL_DISCONNECT

```TypeScript
CONNECTION_LOCAL_DISCONNECT = 2
```

Local device initiated disconnection.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ConnectionReason-CONNECTION_LOCAL_DISCONNECT = 2--><!--Device-ConnectionReason-CONNECTION_LOCAL_DISCONNECT = 2-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

## CONNECTION_REMOTE_DISCONNECT

```TypeScript
CONNECTION_REMOTE_DISCONNECT = 3
```

Remote device initiated disconnection.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ConnectionReason-CONNECTION_REMOTE_DISCONNECT = 3--><!--Device-ConnectionReason-CONNECTION_REMOTE_DISCONNECT = 3-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

## CONNECTION_FAIL_ACB_CONNECTION

```TypeScript
CONNECTION_FAIL_ACB_CONNECTION = 4
```

Connection failed: ACB connection failed. The remote device may be powered off or out of range.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ConnectionReason-CONNECTION_FAIL_ACB_CONNECTION = 4--><!--Device-ConnectionReason-CONNECTION_FAIL_ACB_CONNECTION = 4-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

## CONNECTION_FAIL_SERVICE_DISCOVERY

```TypeScript
CONNECTION_FAIL_SERVICE_DISCOVERY = 5
```

Connection failed: Service discovery failed.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ConnectionReason-CONNECTION_FAIL_SERVICE_DISCOVERY = 5--><!--Device-ConnectionReason-CONNECTION_FAIL_SERVICE_DISCOVERY = 5-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

## CONNECTION_FAIL_NO_AVAILABLE_SERVICE

```TypeScript
CONNECTION_FAIL_NO_AVAILABLE_SERVICE = 6
```

Connection failed: No available services found on the remote device.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ConnectionReason-CONNECTION_FAIL_NO_AVAILABLE_SERVICE = 6--><!--Device-ConnectionReason-CONNECTION_FAIL_NO_AVAILABLE_SERVICE = 6-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

## CONNECTION_FAIL_CONNECTION_NUM_LIMITED

```TypeScript
CONNECTION_FAIL_CONNECTION_NUM_LIMITED = 7
```

Connection failed: Connection limit exceeded.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ConnectionReason-CONNECTION_FAIL_CONNECTION_NUM_LIMITED = 7--><!--Device-ConnectionReason-CONNECTION_FAIL_CONNECTION_NUM_LIMITED = 7-End-->

**System capability:** SystemCapability.Communication.NearLink.Base
