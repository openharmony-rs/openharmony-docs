# getAllLauncherAbilityInfos（系统接口）

## getAllLauncherAbilityInfos

```TypeScript
function getAllLauncherAbilityInfos(userId: number, callback: AsyncCallback<Array<LauncherAbilityInfo>>): void
```

获取所有的LauncherAbilityInfos，使用callback异步回调。

> **说明：**
>
> 从API version 8开始支持，从API version 9开始废弃，建议使用
> [getAllLauncherAbilityInfo](@ohos.bundle.launcherBundleManager:launcherBundleManager.getAllLauncherAbilityInfo(userId: int, callback: AsyncCallback<Array<LauncherAbilityInfo>>))
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getAllLauncherAbilityInfo(userId:

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 是 | 用户ID。取值范围：大于等于0。 |
| callback | AsyncCallback&lt;Array&lt;LauncherAbilityInfo&gt;&gt; | 是 | 程序启动作为入参的回调函数，返回程序信息。 |


## getAllLauncherAbilityInfos

```TypeScript
function getAllLauncherAbilityInfos(userId: number): Promise<Array<LauncherAbilityInfo>>
```

获取LauncherAbilityInfos，使用Promise异步回调。

> **说明：**
>
> 从API version 8开始支持，从API version 9开始废弃，建议使用
> [getAllLauncherAbilityInfo](@ohos.bundle.launcherBundleManager:launcherBundleManager.getAllLauncherAbilityInfo(userId: int, callback: AsyncCallback<Array<LauncherAbilityInfo>>))
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getAllLauncherAbilityInfo(userId:

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 是 | 用户ID。取值范围：大于等于0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;LauncherAbilityInfo&gt;&gt; | Promise形式返回程序信息。 |

