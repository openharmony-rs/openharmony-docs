# AbilityFormInfo (System API)

```TypeScript
export interface AbilityFormInfo
```

AbilityFormInfo: the form info of an ability.

**Since:** 9

<!--Device-unnamed-export interface AbilityFormInfo--><!--Device-unnamed-export interface AbilityFormInfo-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.FreeInstall

**System API:** This is a system API.

## defaultDimension

```TypeScript
readonly defaultDimension: string
```

Default dimensions of the widget. The value must be available in the **supportDimensions** array of the widget.

**Type:** string

**Since:** 9

<!--Device-AbilityFormInfo-readonly defaultDimension: string--><!--Device-AbilityFormInfo-readonly defaultDimension: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.FreeInstall

**System API:** This is a system API.

## name

```TypeScript
readonly name: string
```

Widget name.

**Type:** string

**Since:** 9

<!--Device-AbilityFormInfo-readonly name: string--><!--Device-AbilityFormInfo-readonly name: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.FreeInstall

**System API:** This is a system API.

## scheduledUpdateTime

```TypeScript
readonly scheduledUpdateTime: string
```

Indicates the time for scheduled refresh of the card, in 24-hour format and accurate to the minute. This parameter and the periodic refresh parameter are mutually exclusive. If both are configured, the scheduled refresh takes precedence.

**Type:** string

**Since:** 9

<!--Device-AbilityFormInfo-readonly scheduledUpdateTime: string--><!--Device-AbilityFormInfo-readonly scheduledUpdateTime: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.FreeInstall

**System API:** This is a system API.

## supportDimensions

```TypeScript
readonly supportDimensions: Array<string>
```

Dimensions of the widget. The value can be **1*2**, **2*2**, **2*4**, **4*4**, or a combination of these options. At least one option must be specified when defining the widget.

**Type:** Array&lt;string&gt;

**Since:** 9

<!--Device-AbilityFormInfo-readonly supportDimensions: Array<string>--><!--Device-AbilityFormInfo-readonly supportDimensions: Array<string>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.FreeInstall

**System API:** This is a system API.

## type

```TypeScript
readonly type: string
```

Widget type.

**Type:** string

**Since:** 9

<!--Device-AbilityFormInfo-readonly type: string--><!--Device-AbilityFormInfo-readonly type: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.FreeInstall

**System API:** This is a system API.

## updateDuration

```TypeScript
readonly updateDuration: number
```

Indicates the update frequency for periodic refresh of the card, in minutes. The value must be a multiple of 30. The maximum refresh frequency of the card is once every 30 minutes. This parameter and the scheduled refresh parameter are mutually exclusive. If both are configured, the scheduled refresh takes precedence.

**Type:** number

**Since:** 9

<!--Device-AbilityFormInfo-readonly updateDuration: int--><!--Device-AbilityFormInfo-readonly updateDuration: int-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.FreeInstall

**System API:** This is a system API.

## updateEnabled

```TypeScript
readonly updateEnabled: boolean
```

Whether the widget supports periodic update. **true** if the widget supports periodic update, **false** otherwise.

**Type:** boolean

**Since:** 9

<!--Device-AbilityFormInfo-readonly updateEnabled: boolean--><!--Device-AbilityFormInfo-readonly updateEnabled: boolean-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.FreeInstall

**System API:** This is a system API.
