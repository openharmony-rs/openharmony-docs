# ModuleAbilityInfo（系统接口）

module包含的ability组件信息。

**起始版本：** 9

<!--Device-unnamed-export interface ModuleAbilityInfo--><!--Device-unnamed-export interface ModuleAbilityInfo-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.FreeInstall

**系统接口：** 此接口为系统接口。

## exported

```TypeScript
readonly exported: boolean
```

表示ability是否可以被其它应用调用。true表示可以被其它应用调用，false表示不可以被其它应用调用。

**类型：** boolean

**起始版本：** 9

<!--Device-ModuleAbilityInfo-readonly exported: boolean--><!--Device-ModuleAbilityInfo-readonly exported: boolean-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.FreeInstall

**系统接口：** 此接口为系统接口。

## forms

```TypeScript
readonly forms: Array<AbilityFormInfo>
```

卡片信息。

**类型：** Array&lt;AbilityFormInfo&gt;

**起始版本：** 9

<!--Device-ModuleAbilityInfo-readonly forms: Array<AbilityFormInfo>--><!--Device-ModuleAbilityInfo-readonly forms: Array<AbilityFormInfo>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.FreeInstall

**系统接口：** 此接口为系统接口。

## label

```TypeScript
readonly label: string
```

表示ability对用户显示的名称，标签值配置为该名称的资源索引以支持多语言。

**类型：** string

**起始版本：** 9

<!--Device-ModuleAbilityInfo-readonly label: string--><!--Device-ModuleAbilityInfo-readonly label: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.FreeInstall

**系统接口：** 此接口为系统接口。

## name

```TypeScript
readonly name: string
```

表示当前ability的名称，该名称在整个应用要唯一。

**类型：** string

**起始版本：** 9

<!--Device-ModuleAbilityInfo-readonly name: string--><!--Device-ModuleAbilityInfo-readonly name: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.FreeInstall

**系统接口：** 此接口为系统接口。

