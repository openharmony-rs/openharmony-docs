# AVSessionDescriptor

The description of the session

**Since:** 23

**System capability:** SystemCapability.Multimedia.AVSession.Manager

## Modules to Import

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## outputDevice

```TypeScript
outputDevice: OutputDeviceInfo
```

The current output device information. It will be undefined if this is a local session.

**Type:** [OutputDeviceInfo](arkts-avsession-avsession-outputdeviceinfo-i.md)

**Since:** 9

**System capability:** SystemCapability.Multimedia.AVSession.Manager

**System API:** This is a system API.

## userId

```TypeScript
userId?: number
```

The userId to which this session belongs. The value should be an integer.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.Manager

**System API:** This is a system API.
