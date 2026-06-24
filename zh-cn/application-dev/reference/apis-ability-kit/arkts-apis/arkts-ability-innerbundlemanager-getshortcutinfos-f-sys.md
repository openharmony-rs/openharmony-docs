# getShortcutInfos（系统接口）

## getShortcutInfos

```TypeScript
function getShortcutInfos(bundleName: string, callback: AsyncCallback<Array<ShortcutInfo>>): void
```

���ݸ�����Bundle���ƻ�ȡ��ݷ�ʽ��Ϣ��ʹ��callback�첽�ص���

> **˵����**
>
> ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��
> [getShortcutInfo](@ohos.bundle.launcherBundleManager:launcherBundleManager.getShortcutInfo(bundleName :string, callback: AsyncCallback<Array<ShortcutInfo>>))
> �����

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getShortcutInfo(bundleName

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Ҫ��ѯ��Ӧ��Bundle���ơ� |
| callback | AsyncCallback&lt;Array&lt;ShortcutInfo&gt;&gt; | 是 | ����������Ϊ��εĻص����������ؿ�ݷ�ʽ��Ϣ�� |


## getShortcutInfos

```TypeScript
function getShortcutInfos(bundleName: string): Promise<Array<ShortcutInfo>>
```

���ݸ�����Bundle���ƻ�ȡ��ݷ�ʽ��Ϣ��ʹ��Promise�첽�ص���

> **˵����**
>
> ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��
> [getShortcutInfo](@ohos.bundle.launcherBundleManager:launcherBundleManager.getShortcutInfo(bundleName :string, callback: AsyncCallback<Array<ShortcutInfo>>))
> �����

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getShortcutInfo(bundleName

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Ҫ��ѯ��Ӧ��Bundle���ơ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;ShortcutInfo&gt;&gt; | Promise��ʽ���ؿ�ݷ�ʽ��Ϣ�� |

