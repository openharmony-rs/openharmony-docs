# Troubleshooting Volume Change Callback Issues
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @songshenke-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=ea4476ea9af04ed93f71f60a679bb01129d68719 translatedAt=2026-09-18T04:22:13.076Z pushedAt=2026-09-18T09:18:27.419Z -->

When implementing volume change listening, you may encounter issues such as errors when registering a callback, the callback never being triggered, or the callback continuing to trigger after it is canceled. This document describes common issues related to the [on('streamVolumeChange')](../../reference/apis-audio-kit/arkts-apis-audio-AudioVolumeManager.md#onstreamvolumechange20)/[off('streamVolumeChange')](../../reference/apis-audio-kit/arkts-apis-audio-AudioVolumeManager.md#offstreamvolumechange20) callback APIs, including the relevant background knowledge, issue symptoms, and locating methods, and provides a directly comparable locating process to help you quickly troubleshoot and resolve issues.

## Symptom

When an application listens for volume changes, the common issues are as follows:

- An exception is thrown when calling `on` to register a callback.
- Calling `on` to register does not report an error, but the callback is never triggered after a volume change.
- The callback continues to trigger after calling `off` to cancel the callback.

## Possible Causes

**1. The registration parameters do not meet the requirements.**

   The same callback function cannot be repeatedly registered to different `streamUsage` values; otherwise, an exception is thrown during registration.

**2. The callback has been accidentally removed by the `off` operation of another service.**

   When the `callback` parameter is not passed, the `off` API clears all callbacks of `streamVolumeChange` on this `AudioVolumeManager` instance, rather than only the callback registered by the caller. If multiple services in the same application share the same `AudioVolumeManager` instance, when one service calls `off` without passing `callback`, the callbacks registered by other services are also removed.

**3. The `streamUsage` does not match the stream type whose volume actually changes.**

   The callback is triggered only when the volume of the stream type corresponding to the registered `streamUsage` changes. For example, if the application registers to listen for `STREAM_USAGE_MUSIC` but the volume that actually changes is `STREAM_USAGE_RINGTONE`, the callback is not triggered.

**4. The `callback` is destroyed along with the lifecycle of the `AudioVolumeManager` instance.**

   The lifecycle of the `streamVolumeChange` callback is bound to the `AudioVolumeManager` instance, and the `callback` follows the lifecycle of the instance. When the lifecycle of the instance ends, the callbacks registered on it are also destroyed, and subsequent volume changes no longer trigger the callback.

**5. `on` and `off` are not called on the same `AudioVolumeManager` instance.**

   The registration `on` and cancellation `off` of the `streamVolumeChange` callback must be called on the same `AudioVolumeManager` object instance. If the callback is registered through `on` on instance A but `off` is called on instance B, the cancellation is actually ineffective because the internal listener list of instance B does not contain this callback, and the callback continues to trigger. In multi-instance scenarios, save the instance reference used at registration and use the same reference when canceling.

## Troubleshooting Process

Troubleshoot the issue in the following order. At each step, first check the observable result, and then proceed to the next step based on the result. You can also start from the step that corresponds to the symptom you encounter: start from step 1 if an exception is thrown when `on` is called to register a callback; start from step 2 if `on` does not report an error but the callback is never triggered; go directly to step 6 if the callback continues to be triggered after `off` is called to unregister it.

1. Confirm whether the registration parameters are correct.

   The `on('streamVolumeChange')` callback does not support registering the same callback function to different `streamUsage` values repeatedly. If the callback function has already been registered to a certain `streamUsage` (such as `STREAM_USAGE_MUSIC`), calling `on` again to register it to another `streamUsage` (such as `STREAM_USAGE_RINGTONE`) throws an exception. To listen for multiple stream types, use different callback function instances to register separately.

   The check items are as follows:

   - `streamUsage` conflict: Confirm that the same callback function has not been registered to another `streamUsage`. If the same function has already been registered to another `streamUsage`, the error "Parameter verification failed. Invalid callback." is thrown. Search logs for "callback exists for another streamUsage" to confirm the conflicting `streamUsage` value.
   - Duplicate registration: Registering the same callback function to the same `streamUsage` multiple times is equivalent to registering it only once, and no error is reported. Search logs for "callback already exists for streamUsage" to confirm whether the callback is registered repeatedly.


2. Confirm whether the callback reference is actually saved.

   If the `on` call does not report an error but the callback never triggers, check in the following order: registration log → `off` log → callback list status.

   The check items are as follows:

   - Registration log: Search logs for "save callback ref success, list size=X", where X is the number of callbacks saved under the current `streamUsage`.
   - `on` call log: Search logs for "On callbackName: streamVolumeChange" to confirm that the registration request has been received by the framework layer.
   - Whether the callback list is cleared: Search logs for "no JS callback registered return". If this log appears, the callback reference list is empty and the callback has been cleared.

3. Confirm whether the callback was accidentally removed by the `off` call of another service.

   If the callback list has been cleared but the current service did not actively call `off`, troubleshoot whether it was accidentally removed by the `off` operation of another service on the same instance.

   The check items are as follows:

   - Whether an `off` operation exists: Search logs for "Off callbackName: streamVolumeChange" to confirm whether any service called `off`.
   - `off` call timeline: Based on the timestamps of the "Off callbackName: streamVolumeChange" logs, confirm which service called `off` before the current service's callback became invalid.
   - Full deregistration identifier: search logs for "remove all js callback success". This log indicates that a service called `off` without passing `callback`, clearing all callback references.
   - Comparison of the two deregistration methods: if `off` passes the `callback` parameter, the log should be "remove js callback success, list size=X", where X is the remaining number of callbacks and decreases. If the log is "remove all js callback success", it indicates that the `callback` parameter was not passed.

   The typical timeline of the accidental removal scenario is as follows:

   | Timeline | Service A | Service B | Expected Log |
   |---|---|---|---|
   | T1 | `on` registers a `STREAM_USAGE_MUSIC` listener. | — | `save callback ref success, list size=1` |
   | T2 | — | `on` registers a `STREAM_USAGE_NOTIFICATION` listener. | `save callback ref success, list size=2` |
   | T3 | — | `off('streamVolumeChange')` does not pass `callback`. | `remove all js callback success` |
   | T4 | The volume changes, and a callback is expected. | — | `no JS callback registered return` |

4. Confirm whether `streamUsage` matches the actual volume change.

   If the callback is not accidentally removed but still does not trigger, you need to confirm whether the registered `streamUsage` is consistent with the stream type in which the volume change actually occurs.

   The check items are as follows:

   - Registered `streamUsage`: confirm whether the `streamUsage` value passed when calling `on` is correct. For example, use `STREAM_USAGE_MUSIC` to listen for media volume and `STREAM_USAGE_RINGTONE` to listen for ringtone volume.
   - Actual change scenario: confirm whether the `streamUsage` actually affected by the operation that triggers the volume change (such as pressing the volume key or adjusting settings) is the same as the `streamUsage` registered for listening. If the two are inconsistent, the callback will naturally not be triggered.

5. Confirm the lifecycle of the `AudioVolumeManager` instance.

   If the callback no longer triggers after a period of time, you need to confirm whether the `AudioVolumeManager` instance that registered the callback is still within its lifecycle. The `callback` follows the lifecycle of the instance. When the instance lifecycle ends (for example, the instance is released, or the page or component is destroyed), the callbacks registered on it are also destroyed, and subsequent volume changes no longer trigger the callback.

6. Confirm whether `on` and `off` are called on the same `AudioVolumeManager` instance.

   If the callback continues to trigger after `off` is called, you need to confirm whether `on` and `off` are called on the same `AudioVolumeManager` instance. `on` and `off` must be based on the same instance; otherwise, the cancellation does not take effect and the callback still triggers.

   The check items are as follows:

   - Instance consistency of `on`/`off`: If `on` is registered on instance A and `off` is called on instance B, the cancellation does not take effect and the callback still triggers. During troubleshooting, confirm whether the instance references saved by the service are consistent.
   - Multiple-instance scenario: If multiple `AudioVolumeManager` instances are created in the same application, ensure that each instance manages its callbacks independently and avoid mixing `on` and `off` across instances.