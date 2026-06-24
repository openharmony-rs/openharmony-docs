# getAllApplicationInfo

## getAllApplicationInfo

```TypeScript
function getAllApplicationInfo(bundleFlags: number,
    userId: number, callback: AsyncCallback<Array<ApplicationInfo>>): void
```

��ȡָ���û��������Ѱ�װ��Ӧ����Ϣ��ʹ��callback�첽�ص���

**起始版本：** 7

**废弃版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleFlags | number | 是 | ����ָ�����ص�Ӧ����Ϣ�����а�����Ϣ�ı�ǡ�ȡֵ��Χ���ο�[BundleFlag˵��](arkts-ability-bundle-bundleflag-e.md#BundleFlag)��Ӧ����Ϣ���flag�� |
| userId | number | 是 | �û�ID��Ĭ��ֵ�����÷������û���ȡֵ��Χ�����ڵ���0�� |
| callback | AsyncCallback&lt;Array&lt;ApplicationInfo&gt;&gt; | 是 | ����������Ϊ��εĻص�����������Ӧ����Ϣ�б��� |


## getAllApplicationInfo

```TypeScript
function getAllApplicationInfo(bundleFlags: number, callback: AsyncCallback<Array<ApplicationInfo>>): void
```

��ȡ���÷������û����Ѱ�װ��Ӧ����Ϣ��ʹ��callback�첽�ص���

**起始版本：** 7

**废弃版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleFlags | number | 是 | ����ָ�����ص�Ӧ����Ϣ�����а�����Ϣ�ı�ǡ�ȡֵ��Χ���ο�[BundleFlag˵��](arkts-ability-bundle-bundleflag-e.md#BundleFlag)��Ӧ����Ϣ���flag�� |
| callback | AsyncCallback&lt;Array&lt;ApplicationInfo&gt;&gt; | 是 | ����������Ϊ��εĻص�����������Ӧ����Ϣ�б��� |


## getAllApplicationInfo

```TypeScript
function getAllApplicationInfo(bundleFlags: number, userId?: number): Promise<Array<ApplicationInfo>>
```

��ȡָ���û��������Ѱ�װ��Ӧ����Ϣ��ʹ��promise�첽�ص���

**起始版本：** 7

**废弃版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleFlags | number | 是 | ����ָ�����ص�Ӧ����Ϣ�����а�����Ϣ�ı�ǡ�ȡֵ��Χ���ο�[BundleFlag˵��](arkts-ability-bundle-bundleflag-e.md#BundleFlag)��Ӧ����Ϣ���flag�� |
| userId | number | 否 | �û�ID��Ĭ��ֵ�����÷������û���ȡֵ��Χ�����ڵ���0�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;ApplicationInfo&gt;&gt; | Promise���󣬻�ȡ�ɹ�ʱ����Ӧ����Ϣ�б��� |

