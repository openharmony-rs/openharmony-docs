# AbilityFormInfo（系统接口）

卡片信息。

**起始版本：** 9

<!--Device-unnamed-export interface AbilityFormInfo--><!--Device-unnamed-export interface AbilityFormInfo-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.FreeInstall

**系统接口：** 此接口为系统接口。

## defaultDimension

```TypeScript
readonly defaultDimension: string
```

表示卡片默认外观规格，取值必须在supportDimensions配置的列表中。

**类型：** string

**起始版本：** 9

<!--Device-AbilityFormInfo-readonly defaultDimension: string--><!--Device-AbilityFormInfo-readonly defaultDimension: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.FreeInstall

**系统接口：** 此接口为系统接口。

## name

```TypeScript
readonly name: string
```

表示forms的名称。

**类型：** string

**起始版本：** 9

<!--Device-AbilityFormInfo-readonly name: string--><!--Device-AbilityFormInfo-readonly name: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.FreeInstall

**系统接口：** 此接口为系统接口。

## scheduledUpdateTime

```TypeScript
readonly scheduledUpdateTime: string
```

表示卡片定点刷新的时间，采用24小时计数，精确到分钟。

**类型：** string

**起始版本：** 9

<!--Device-AbilityFormInfo-readonly scheduledUpdateTime: string--><!--Device-AbilityFormInfo-readonly scheduledUpdateTime: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.FreeInstall

**系统接口：** 此接口为系统接口。

## supportDimensions

```TypeScript
readonly supportDimensions: Array<string>
```

表示卡片外观规格，取值为“1*2”，“2*2”，“2*4”，“4*4”，定义卡片时至少要指定一个卡片规格。

**类型：** Array&lt;string&gt;

**起始版本：** 9

<!--Device-AbilityFormInfo-readonly supportDimensions: Array<string>--><!--Device-AbilityFormInfo-readonly supportDimensions: Array<string>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.FreeInstall

**系统接口：** 此接口为系统接口。

## type

```TypeScript
readonly type: string
```

表示forms的类型。

**类型：** string

**起始版本：** 9

<!--Device-AbilityFormInfo-readonly type: string--><!--Device-AbilityFormInfo-readonly type: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.FreeInstall

**系统接口：** 此接口为系统接口。

## updateDuration

```TypeScript
readonly updateDuration: number
```

表示卡片定时刷新的更新频率，单位：分钟，取值为30的倍数值。卡片的最高频率为每30分钟刷新一次，和定点刷新二选一，二者都配置的情况下，定时优先。

**类型：** number

**起始版本：** 9

<!--Device-AbilityFormInfo-readonly updateDuration: int--><!--Device-AbilityFormInfo-readonly updateDuration: int-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.FreeInstall

**系统接口：** 此接口为系统接口。

## updateEnabled

```TypeScript
readonly updateEnabled: boolean
```

表示该卡片是否支持定时刷新，true表示卡片支持定时刷新，false表示不支持。

**类型：** boolean

**起始版本：** 9

<!--Device-AbilityFormInfo-readonly updateEnabled: boolean--><!--Device-AbilityFormInfo-readonly updateEnabled: boolean-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.FreeInstall

**系统接口：** 此接口为系统接口。

