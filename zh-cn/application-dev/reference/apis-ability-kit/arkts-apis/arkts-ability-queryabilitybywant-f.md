# queryAbilityByWant

## queryAbilityByWant

```TypeScript
function queryAbilityByWant(want: Want,
    bundleFlags: number, userId: number, callback: AsyncCallback<Array<AbilityInfo>>): void
```

根据给定的意图获取指定用户下Ability信息，使用callback异步回调。

获取调用方自己的信息时不需要权限。

**起始版本：** 7

**废弃版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 指示包含要查询的应用Bundle名称的意图。 |
| bundleFlags | number | 是 | 用于指定返回abilityInfo信息。取值范围：参考[BundleFlag说明](arkts-ability-bundleflag-e.md)中Ability信息相关flag。 |
| userId | number | 是 | 用户ID。取值范围：大于等于0。 |
| callback | AsyncCallback&lt;Array&lt;AbilityInfo&gt;&gt; | 是 | 程序启动作为入参的回调函数，返回Ability信息。 |


## queryAbilityByWant

```TypeScript
function queryAbilityByWant(want: Want, bundleFlags: number, callback: AsyncCallback<Array<AbilityInfo>>): void
```

根据给定的意图获取Ability信息，使用callback异步回调。

获取调用方自己的信息时不需要权限。

**起始版本：** 7

**废弃版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 指示包含要查询的应用Bundle名称的意图。 |
| bundleFlags | number | 是 | 用于指定返回abilityInfo信息。取值范围：参考[BundleFlag说明](arkts-ability-bundleflag-e.md)中Ability信息相关flag。 |
| callback | AsyncCallback&lt;Array&lt;AbilityInfo&gt;&gt; | 是 | 程序启动作为入参的回调函数，返回Ability信息。 |


## queryAbilityByWant

```TypeScript
function queryAbilityByWant(want: Want, bundleFlags: number, userId?: number): Promise<Array<AbilityInfo>>
```

根据给定的意图获取Ability组件信息，使用Promise异步回调。

获取调用方自己的信息时不需要权限。

**起始版本：** 7

**废弃版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 包含要查询的应用Bundle名称的意图。 |
| bundleFlags | number | 是 | 用于指定返回abilityInfo信息。取值范围：参考[BundleFlag说明](arkts-ability-bundleflag-e.md)中Ability信息相关flag。 |
| userId | number | 否 | 用户ID。默认值：调用方所在用户，取值范围：大于等于0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;AbilityInfo&gt;&gt; | Promise形式返回Ability信息。 |

