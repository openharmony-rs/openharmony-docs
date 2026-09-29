# ManualExposureQuery

```TypeScript
interface ManualExposureQuery
```

Provides APIs to obtain the manual exposure range supported.

**Since:** 24

<!--Device-camera-interface ManualExposureQuery--><!--Device-camera-interface ManualExposureQuery-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## getExposureBiasStep

```TypeScript
getExposureBiasStep(): number
```

Get exposure bias step.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 24.

<!--Device-ManualExposureQuery-getExposureBiasStep(): double--><!--Device-ManualExposureQuery-getExposureBiasStep(): double-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | exposure bias step. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-invalid-operation) | Operation not allowed, session or inputdevice maybe abnormal. |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |

## getSupportedExposureDurationRange

```TypeScript
getSupportedExposureDurationRange(): Array<number>
```

Gets the supported manual exposure duration range, units: microseconds.

**Since:** 24

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 24.

<!--Device-ManualExposureQuery-getSupportedExposureDurationRange(): Array<int>--><!--Device-ManualExposureQuery-getSupportedExposureDurationRange(): Array<int>-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;number&gt; | The array of manual exposure range. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-invalid-operation) | Operation not allowed, session or inputdevice maybe abnormal. |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config, only throw in session usage. |
