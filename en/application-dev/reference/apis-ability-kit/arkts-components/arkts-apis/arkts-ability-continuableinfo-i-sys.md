# ContinuableInfo (System API)

```TypeScript
export interface ContinuableInfo
```

The module provides the mission continuation information to be returned when the listener for listening for the mission continuation state is registered. For details about the registration, see [on('continueStateChange')](arkts-ability-distributedmissionmanager-on-f-sys.md#oncontinuestatechange).

**Since:** 10

<!--Device-unnamed-export interface ContinuableInfo--><!--Device-unnamed-export interface ContinuableInfo-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

## bundleName

```TypeScript
bundleName: string
```

Bundle name of the target application to which the mission belongs.

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-ContinuableInfo-bundleName: string--><!--Device-ContinuableInfo-bundleName: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

## continueType

```TypeScript
continueType?: string
```

Continuation type of the application to which the mission belongs.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-ContinuableInfo-continueType?: string--><!--Device-ContinuableInfo-continueType?: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

## srcBundleName

```TypeScript
srcBundleName?: string
```

Bundle name of the source application to which the mission belongs. The value is the same as that of **bundleName** by default.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-ContinuableInfo-srcBundleName?: string--><!--Device-ContinuableInfo-srcBundleName?: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

## srcDeviceId

```TypeScript
srcDeviceId: string
```

ID of the source device.

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-ContinuableInfo-srcDeviceId: string--><!--Device-ContinuableInfo-srcDeviceId: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

## targetAppIds

```TypeScript
targetAppIds?: Array<string>
```

Target AppId list of the application to which the mission belongs.

**Type:** Array&lt;string&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ContinuableInfo-targetAppIds?: Array<string>--><!--Device-ContinuableInfo-targetAppIds?: Array<string>-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.
