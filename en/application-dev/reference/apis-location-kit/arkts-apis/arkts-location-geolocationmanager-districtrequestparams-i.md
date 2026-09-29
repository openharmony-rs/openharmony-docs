# DistrictRequestParams

```TypeScript
export interface DistrictRequestParams
```

Indicates request parameters for obtaining the district information.

**Since:** 26.0.0

<!--Device-geoLocationManager-export interface DistrictRequestParams--><!--Device-geoLocationManager-export interface DistrictRequestParams-End-->

**System capability:** SystemCapability.Location.Location.Geocoder

## Modules to Import

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## locale

```TypeScript
locale?: string
```

Indicates the language area information. ISO 639 alpha-2 or alpha-3 language code. Example: "zh" (Chinese), "en" (English). The default value is obtained from the language settings of the device (settings/system/Language & region /Language).

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-DistrictRequestParams-locale?: string--><!--Device-DistrictRequestParams-locale?: string-End-->

**System capability:** SystemCapability.Location.Location.Geocoder

## timeoutMs

```TypeScript
timeoutMs?: number
```

Indicates the timeout period. The default value is 5000 ms. The value range is all integers.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-DistrictRequestParams-timeoutMs?: int--><!--Device-DistrictRequestParams-timeoutMs?: int-End-->

**System capability:** SystemCapability.Location.Location.Geocoder
