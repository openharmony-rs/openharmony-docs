# ApplicationQuickFixInfo（系统接口）

应用级别的快速修复信息。

**起始版本：** 9

<!--Device-quickFixManager-export interface ApplicationQuickFixInfo--><!--Device-quickFixManager-export interface ApplicationQuickFixInfo-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.QuickFix

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { quickFixManager } from '@kit.AbilityKit';
```

## bundleName

```TypeScript
readonly bundleName: string
```

应用Bundle名称。

**类型：** string

**起始版本：** 9

<!--Device-ApplicationQuickFixInfo-readonly bundleName: string--><!--Device-ApplicationQuickFixInfo-readonly bundleName: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.QuickFix

**系统接口：** 此接口为系统接口。

## bundleVersionCode

```TypeScript
readonly bundleVersionCode: number
```

应用的版本号。

**类型：** number

**起始版本：** 9

<!--Device-ApplicationQuickFixInfo-readonly bundleVersionCode: long--><!--Device-ApplicationQuickFixInfo-readonly bundleVersionCode: long-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.QuickFix

**系统接口：** 此接口为系统接口。

## bundleVersionName

```TypeScript
readonly bundleVersionName: string
```

应用版本号的文字描述。

**类型：** string

**起始版本：** 9

<!--Device-ApplicationQuickFixInfo-readonly bundleVersionName: string--><!--Device-ApplicationQuickFixInfo-readonly bundleVersionName: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.QuickFix

**系统接口：** 此接口为系统接口。

## hapModuleQuickFixInfo

```TypeScript
readonly hapModuleQuickFixInfo: Array<HapModuleQuickFixInfo>
```

hap级别的快速修复信息。

**类型：** Array&lt;HapModuleQuickFixInfo&gt;

**起始版本：** 9

<!--Device-ApplicationQuickFixInfo-readonly hapModuleQuickFixInfo: Array<HapModuleQuickFixInfo>--><!--Device-ApplicationQuickFixInfo-readonly hapModuleQuickFixInfo: Array<HapModuleQuickFixInfo>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.QuickFix

**系统接口：** 此接口为系统接口。

## quickFixVersionCode

```TypeScript
readonly quickFixVersionCode: number
```

快速修复补丁包的版本号。

**类型：** number

**起始版本：** 9

<!--Device-ApplicationQuickFixInfo-readonly quickFixVersionCode: long--><!--Device-ApplicationQuickFixInfo-readonly quickFixVersionCode: long-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.QuickFix

**系统接口：** 此接口为系统接口。

## quickFixVersionName

```TypeScript
readonly quickFixVersionName: string
```

快速修复补丁包版本号的文字描述。

**类型：** string

**起始版本：** 9

<!--Device-ApplicationQuickFixInfo-readonly quickFixVersionName: string--><!--Device-ApplicationQuickFixInfo-readonly quickFixVersionName: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.QuickFix

**系统接口：** 此接口为系统接口。

