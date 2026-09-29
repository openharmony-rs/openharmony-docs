# VideoMode

```TypeScript
export enum VideoMode
```

Enumerates the log modes of video files.

**Since:** 22

<!--Device-photoAccessHelper-export enum VideoMode--><!--Device-photoAccessHelper-export enum VideoMode-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## DEFAULT

```TypeScript
DEFAULT = 0
```

Default type.

A value of **0** indicates that the video is either not in log mode or its type has not yet been determined. This value may later be updated to **1** for some videos after type determination, so it is not recommended for use in queries.

**Since:** 22

<!--Device-VideoMode-DEFAULT = 0--><!--Device-VideoMode-DEFAULT = 0-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## LOG_VIDEO

```TypeScript
LOG_VIDEO = 1
```

Video file in log mode.

**Since:** 22

<!--Device-VideoMode-LOG_VIDEO = 1--><!--Device-VideoMode-LOG_VIDEO = 1-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core
