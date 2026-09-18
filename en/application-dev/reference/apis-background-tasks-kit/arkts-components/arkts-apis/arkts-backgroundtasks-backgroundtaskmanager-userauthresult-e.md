# UserAuthResult

Represents the user authorization result.

**Since:** 22

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## NOT_SUPPORTED

```TypeScript
NOT_SUPPORTED = 0
```

The authorization is not supported. For example, if the main type of the requested continuous task is not **MODE_SPECIAL_SCENARIO_PROCESSING**, continuous task running in the background is not supported.

**Since:** 22

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## NOT_DETERMINED

```TypeScript
NOT_DETERMINED = 1
```

No user operation.

**Since:** 22

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## DENIED

```TypeScript
DENIED = 2
```

The authorization is denied.

**Since:** 22

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## GRANTED_ONCE

```TypeScript
GRANTED_ONCE = 3
```

The authorization is granted this time.

Note: The authorization record will be cleared when the application exits.

**Since:** 22

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## GRANTED_ALWAYS

```TypeScript
GRANTED_ALWAYS = 4
```

The authorization is granted always.

**NOTE:** 

When the following common events are received, the related authorization records will be cleared:

[COMMON_EVENT_PACKAGE_ADDED](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-commoneventmanager-support-e.md#common_event_package_added), [COMMON_EVENT_PACKAGE_REMOVED](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-commoneventmanager-support-e.md#common_event_package_removed), [COMMON_EVENT_BUNDLE_REMOVED](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-commoneventmanager-support-e.md#common_event_bundle_removed), [COMMON_EVENT_PACKAGE_FULLY_REMOVED](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-commoneventmanager-support-e.md#common_event_package_fully_removed), [COMMON_EVENT_PACKAGE_CHANGED](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-commoneventmanager-support-e.md#common_event_package_changed).

**Since:** 22

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask
