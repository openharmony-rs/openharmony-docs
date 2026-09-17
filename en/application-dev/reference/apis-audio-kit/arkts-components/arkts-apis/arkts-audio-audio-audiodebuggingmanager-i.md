# AudioDebuggingManager

Provides audio debug management capabilities.

**Since:** 26.0.0

**System capability:** SystemCapability.Multimedia.Audio.Core

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## printAppInfo

```TypeScript
printAppInfo(fd: number): void
```

Prints full audio runtime snapshot for current app process. The snapshot will contain all audio renderers, capturers, audio session information. Note that the information details and format may vary from different version, it can only be used for manual debugging, user should not rely on the information for actual function realization or file content extraction.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fd | number | Yes | fd is a file descriptor, indicates the location that the snapshot information will be written to. If the fd is less than 0 or no writable, the snapshot information will be printed into the running log, otherwise the snapshot will be written into the file. |

## printCapturerInfo

```TypeScript
printCapturerInfo(capturer: AudioCapturer, fd: number): void
```

Prints full audio runtime snapshot for target audio capturer instance. The snapshot will contain the stream, pipe, volume and device information. Note that the information details and format may vary from different version, it can only be used for manual debugging, user should not rely on the information for actual function realization or file content extraction.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| capturer | [AudioCapturer](arkts-audio-audio-audiocapturer-i.md) | Yes | target audio capturer instance to print snapshot. |
| fd | number | Yes | fd is a file descriptor, indicates the location that the snapshot information will be written to. If the fd is less than 0 or no writable, the snapshot information will be printed into the running log, otherwise the snapshot will be written into the file. |

## printLoopbackInfo

```TypeScript
printLoopbackInfo(loopback: AudioLoopback, fd: number): void
```

Prints full audio runtime snapshot for target audio loopback instance. The snapshot will contain the loopback status, device and effect information. Note that the information details and format may vary from different version, it can only be used for manual debugging, user should not rely on the information for actual function realization or file content extraction.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| loopback | [AudioLoopback](arkts-audio-audio-audioloopback-i.md) | Yes | target audio loopback instance to print snapshot. |
| fd | number | Yes | fd is a file descriptor, indicates the location that the snapshot information will be written to. If the fd is less than 0 or no writable, the snapshot information will be printed into the running log, otherwise the snapshot will be written into the file. |

## printRendererInfo

```TypeScript
printRendererInfo(renderer: AudioRenderer, fd: number): void
```

Prints full audio runtime snapshot for target audio renderer instance. The snapshot will contain the stream, pipe, volume and device information. Note that the information details and format may vary from different version, it can only be used for manual debugging, user should not rely on the information for actual function realization or file content extraction.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| renderer | [AudioRenderer](arkts-audio-audio-audiorenderer-i.md) | Yes | target audio renderer instance to print snapshot. |
| fd | number | Yes | fd is a file descriptor, indicates the location that the snapshot information will be written to. If the fd is less than 0 or no writable, the snapshot information will be printed into the running log, otherwise the snapshot will be written into the file. |

## printSessionInfo

```TypeScript
printSessionInfo(session: AudioSessionManager, fd: number): void
```

Prints full audio runtime snapshot for target audio session manager instance. The snapshot will contain the session status, scene, strategy and device information. Note that the information details and format may vary from different version, it can only be used for manual debugging, user should not rely on the information for actual function realization or file content extraction.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| session | [AudioSessionManager](arkts-audio-audio-audiosessionmanager-i.md) | Yes | target audio session manager instance to print snapshot. |
| fd | number | Yes | fd is a file descriptor, indicates the location that the snapshot information will be written to. If the fd is less than 0 or no writable, the snapshot information will be printed into the running log, otherwise the snapshot will be written into the file. |
