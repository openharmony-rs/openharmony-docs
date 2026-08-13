# getLauncherAbilityInfos（系统接口）

## getLauncherAbilityInfos

```TypeScript
function getLauncherAbilityInfos(bundleName: string,
    userId: number, callback: AsyncCallback<Array<LauncherAbilityInfo>>): void
```

根据给定的Bundle名称获取LauncherAbilityInfos，使用callback异步回调。 > **说明：** > > 从API version 8开始支持，从API version 9开始废弃，建议使用 > [getLauncherAbilityInfo](arkts-ability-launcherbundlemanager-getlauncherabilityinfo-f-sys.md#getLauncherAbilityInfo（系统接口）) > 替代。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [getLauncherAbilityInfo](arkts-ability-launcherbundlemanager-getlauncherabilityinfo-f-sys.md#getLauncherAbilityInfo)(bundleName: string, userId: int, callback: AsyncCallback&lt;Array&lt;LauncherAbilityInfo&gt;&gt;)

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-innerBundleManager-function getLauncherAbilityInfos(bundleName: string,    userId: number, callback: AsyncCallback<Array<LauncherAbilityInfo>>): void--><!--Device-innerBundleManager-function getLauncherAbilityInfos(bundleName: string,    userId: number, callback: AsyncCallback<Array<LauncherAbilityInfo>>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 要查询的应用Bundle名称。 |
| userId | number | 是 | 用户ID。取值范围：大于等于0。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Array&lt;[LauncherAbilityInfo](arkts-ability-launcherabilityinfo-launcherabilityinfo-depr-i-sys.md)&gt;&gt; | 是 | 程序启动作为入参的回调函数，返回程序信息。 |


## getLauncherAbilityInfos

```TypeScript
function getLauncherAbilityInfos(bundleName: string, userId: number): Promise<Array<LauncherAbilityInfo>>
```

根据给定的Bundle名称获取LauncherAbilityInfos，使用Promise异步回调。 > **说明：** > > 从API version 8开始支持，从API version 9开始废弃，建议使用 > [getLauncherAbilityInfo](arkts-ability-launcherbundlemanager-getlauncherabilityinfo-f-sys.md#getLauncherAbilityInfo（系统接口）) > 替代。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [getLauncherAbilityInfo](arkts-ability-launcherbundlemanager-getlauncherabilityinfo-f-sys.md#getLauncherAbilityInfo)(bundleName: string, userId: int, callback: AsyncCallback&lt;Array&lt;LauncherAbilityInfo&gt;&gt;)

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-innerBundleManager-function getLauncherAbilityInfos(bundleName: string, userId: number): Promise<Array<LauncherAbilityInfo>>--><!--Device-innerBundleManager-function getLauncherAbilityInfos(bundleName: string, userId: number): Promise<Array<LauncherAbilityInfo>>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 要查询的应用Bundle名称。 |
| userId | number | 是 | 用户ID。取值范围：大于等于0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[LauncherAbilityInfo](arkts-ability-launcherabilityinfo-launcherabilityinfo-depr-i-sys.md)&gt;&gt; | Promise形式返回程序信息。 |

