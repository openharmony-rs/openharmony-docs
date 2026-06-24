# getLauncherAbilityInfos（系统接口）

## getLauncherAbilityInfos

```TypeScript
function getLauncherAbilityInfos(bundleName: string,
    userId: number, callback: AsyncCallback<Array<LauncherAbilityInfo>>): void
```

���ݸ�����Bundle���ƻ�ȡLauncherAbilityInfos��ʹ��callback�첽�ص���

> **˵����**
>
> ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��
> [getLauncherAbilityInfo](@ohos.bundle.launcherBundleManager:launcherBundleManager.getLauncherAbilityInfo(bundleName: string, userId: int, callback: AsyncCallback<Array<LauncherAbilityInfo>>))
> �����

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getLauncherAbilityInfo(bundleName:

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Ҫ��ѯ��Ӧ��Bundle���ơ� |
| userId | number | 是 | �û�ID��ȡֵ��Χ�����ڵ���0�� |
| callback | AsyncCallback&lt;Array&lt;LauncherAbilityInfo&gt;&gt; | 是 | ����������Ϊ��εĻص����������س�����Ϣ�� |


## getLauncherAbilityInfos

```TypeScript
function getLauncherAbilityInfos(bundleName: string, userId: number): Promise<Array<LauncherAbilityInfo>>
```

���ݸ�����Bundle���ƻ�ȡLauncherAbilityInfos��ʹ��Promise�첽�ص���

> **˵����**
>
> ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��
> [getLauncherAbilityInfo](@ohos.bundle.launcherBundleManager:launcherBundleManager.getLauncherAbilityInfo(bundleName: string, userId: int, callback: AsyncCallback<Array<LauncherAbilityInfo>>))
> �����

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getLauncherAbilityInfo(bundleName:

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Ҫ��ѯ��Ӧ��Bundle���ơ� |
| userId | number | 是 | �û�ID��ȡֵ��Χ�����ڵ���0�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;LauncherAbilityInfo&gt;&gt; | Promise��ʽ���س�����Ϣ�� |

