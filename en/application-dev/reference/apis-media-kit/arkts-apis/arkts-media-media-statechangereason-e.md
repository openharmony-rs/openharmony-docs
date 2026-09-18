# StateChangeReason

Enumerates the reasons for the state transition of the AVPlayer or AVRecorder instance. The enum value is reported together with **state**.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Media.Core

## USER

```TypeScript
USER = 1
```

State transition triggered by user behavior. It happens when a user or the client calls an API.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.Core

## BACKGROUND

```TypeScript
BACKGROUND = 2
```

State transition caused by background system behavior. For example, if an application does not have the permission of Media Controller, the application is forcibly suspended or stopped by the system when it switches to the background.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.Core
