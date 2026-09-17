# AbilityFormInfo (System API)

AbilityFormInfo: the form info of an ability.

**Since:** 9

**System capability:** SystemCapability.BundleManager.BundleFramework.FreeInstall

**System API:** This is a system API.

## defaultDimension

```TypeScript
readonly defaultDimension: string
```

Default dimensions of the widget. The value must be available in the **supportDimensions** array of the widget.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.BundleManager.BundleFramework.FreeInstall

**System API:** This is a system API.

## name

```TypeScript
readonly name: string
```

Widget name.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.BundleManager.BundleFramework.FreeInstall

**System API:** This is a system API.

## scheduledUpdateTime

```TypeScript
readonly scheduledUpdateTime: string
```

Scheduled time to update the widget. The value is in 24-hour format and accurate to the minute.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.BundleManager.BundleFramework.FreeInstall

**System API:** This is a system API.

## supportDimensions

```TypeScript
readonly supportDimensions: Array<string>
```

Dimensions of the widget. The value can be **1*2**, **2*2**, **2*4**, **4*4**, or a combination of these options. At least one option must be specified when defining the widget.

**Type:** Array&lt;string&gt;

**Since:** 9

**System capability:** SystemCapability.BundleManager.BundleFramework.FreeInstall

**System API:** This is a system API.

## type

```TypeScript
readonly type: string
```

Widget type.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.BundleManager.BundleFramework.FreeInstall

**System API:** This is a system API.

## updateDuration

```TypeScript
readonly updateDuration: number
```

Interval to update the widget. The unit is 30 minutes. The value is a multiple of 30. A widget can be updated at a specified interval (**updateDuration**) or at the scheduled time (**scheduledUpdateTime**). If both are configured, **updateDuration** takes precedence.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.BundleManager.BundleFramework.FreeInstall

**System API:** This is a system API.

## updateEnabled

```TypeScript
readonly updateEnabled: boolean
```

Whether the widget supports periodic update. **true** if the widget supports periodic update, **false** otherwise.

**Type:** boolean

**Since:** 9

**System capability:** SystemCapability.BundleManager.BundleFramework.FreeInstall

**System API:** This is a system API.
